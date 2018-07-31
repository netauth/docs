# group-expansions

Modify the expansion rules on a group.  The expansion rules of NetAuth
are incredibly complex.  Here's a brief introduction to how they work
pulled from the development log, but keep in mind that its easy to get
in way over your head with expansion rules, and so use them in
moderation.

### Include Expansions

The first type of expansion that NetAuth supports is very
straightforward.  You can tell a group to include another group.  This
directly includes the other group's memberships and is transparent to
a client looking up members.  The difference between this system and
the nested groups described above is that the client is not aware an
expansion took place.  The client just asked for the members of 'foo'
and got all of them, even those who have indirect membership in 'foo'
via 'bar'.

These exapansions can be nested arbitrarily deep and can include
arbitrarily many groups at each inclusion level, though for sanity of
the systems administrator, care should be taken not to create overly
complex membership graphs.

### Exclude Expansions

Exclude expansions are the second type of expansion that NetAuth
supports and are a bit more involved to understand.  These expansions
work by 'pruning' members of a group if they are also members of a
subgroup.  Take for example the directory structure shown below:

```
ALL
 |
 |-group1
 |   |
 |   \-foo
 |
 \-group2
     |
     \-foo
```

If you were to query the membership of group1 with no expansion rules,
then as you would expect the members list would contain 'foo'.

```
ALL
 |
 |-group1
 |   |
 |   |-EXCLUDE:group2
 |   \-foo
 |
 \-group2
     |
     \-foo
```

Now if we add an exclude expansion to group1 to exclude the members of
group2 and run the same request, something interesting happens: group1
has no members anymore!  Ok, to clear up what's happening here, lets
modify the directory a little bit so that it now looks like this:

```
ALL
 |
 |-group1
 |   |
 |   |-EXCLUDE:group2
 |   |-foo
 |   \-bar
 |
 \-group2
     |
     \-foo
```

Now if we query the membership of group1 again we have one member
'bar'.  What is happening here?  When the exclude relation was added
to group1 this instructed NetAuth to filter out anyone who was a
member of group2 when returning the membership of group1.  But, and
this is the important bit, the members are still in group1.

```
ALL
 |
 |-group1
 |   |
 |   |-foo
 |   \-bar
 |
 \-group2
     |
     \-foo
```

If we remove the exclude rule and query the membership of group1 again
it now contains 'bar' *and* 'foo'.  The 'foo' entity was never
removed, so they still maintain membership.  Here's a real-world
example that might spark thoughts of how this can be used:

```
ALL
 |
 |-PermitLogin
 |   |
 |   |-INCLUDE:Users
 |   \-EXCLUDE:Restricted
 |
 |-Users
 |   |
 |   |-Alice
 |   |-Bob
 |   |-Eve
 |   |-<Many More Entities>
 |
 \-Restricted
     |
     \-Eve
```

In this example, we have entities that are permitted to log in to a
system as members of the PermitLogin group via an include rule
targeting the Users group (all users are permitted to log in).  Not
surprisingly Eve was caught trying to install a keylogger on Bob's
computer, so Eve is restricted from logging in now.  But this is
temporary as we expect Eve will learn from this experience, so we
don't really want to remove Eve from the Users group, since that's
going to require noting down somewhere and some rules to put back
later.

Instead we can have another group called 'Restricted' and this group's
members shall be excluded from PermitLogin.  By putting Eve in this
group, PermitLogin no longer will return Eve as a member since the
EXCLUDE rule has filtered her out.

### Expansions All The Way Down

You can actually nest includes and excludes as deep as you like to
compose arbitrarily complex logical membership graphs based on the
include and exclude rules.  Do be careful though, as each rule has a
non-trivial cost to calculate and the mental cost of maintaining a
large tree like this is also quite high.

## Help Text

```
group-expansions --parent <parent> --child <child> --mode <INCLUDE|EXCLUDE|DROP>

Modify group expansions.  INCLUDE will include the children of the
named group in the parent, EXCLUDE will exclude the children of the
named group from the parent, and DROP will remove rules of either
type.  -child string
        Child Group
  -mode string
        Mode, must be one of INCLUDE, EXCLUDE, or DROP (default "INCLUDE")
  -parent string
        Parent Group
```

## Usage

The parent group is the group that the expansion will expand into, the
child is the group whose members will either be included or excluded.

If you no longer wish to have an expansion, use the `DROP` mode to
remove it.

Expansion application is idempotent, and expansions are checked for
cycles, but still exercise caution when modifying large or nested
expansion rules.

Modifying expansion rules requires the `MODIFY_GROUP_META` capability.


## Example

```shell
$ netauth list-members --group child
ID: demo
Number: 7
GECOS: Demonstration Entity
$ netauth list-members --group parent
$ netauth group-expansions --mode INCLUDE --parent parent --child child
$ netauth list-members --group parent
ID: demo
Number: 7
GECOS: Demonstration Entity
```
