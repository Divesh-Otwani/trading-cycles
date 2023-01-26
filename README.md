# trading-cycles

## Description

This daml package implements a class trading application in which college students
can do cyclical trades of classes.

By using DAML and a backing blockchain, we ensure the following.

 * A swap (giving up a course A for a course B) adheres to graduation
   requirements and fair-play because a student's advisor, the current class's
   professor, and the registrar have to sign off on the swap.
 * Any valid cycle consists of a loop of valid swaps. Students provide a
   witness that the swap they want to make is pre-approved.
 * The cyclic trade is atomic so students don't need to trust each other.
   Students do have to trust the registrar, however.
 * Students cannot trade a class they have traded to get; that is, no class
   can be used as an asset.
 * Students cannot see the enrollment of classes they are not in. Thus, trades
   cannot be based off of taking classes with friends (unless this is done
   off-chain).
 * The state of the classes is kept consistent with lots of trades occurring
   without sacrificing performance. This is mainly because (1) a student need
   only interact with a few parties to pre-approve a swap (so it doesn't have
   to synchronize with a giant database), (2) students independently form
   (pending) cycles (without centralized synchronization), and (3) executing a
   cycle only touches a few classes.

The workflow is illustrated in `Main.daml` and documented throughout.

## Docs

The documentation is available [here][1] taken from `/docs`. It is rather
sparse and a few pieces of intended documentation are not created and this
needs to be fixed.

## Comments

This problem generalizes to trading resources with approvals for those
resources, but for now I limited the scope.

[1]: https://divesh-otwani.github.io/trading-cycles/ 
