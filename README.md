# subtree-host
Repository to evaluate the cost of usage gitsubtrees.
There is another repository subtree which will be hooked to the different paths of existing repository.

The questions I would like to get answer for here are:
1. How much of  host repository history inflation we will get in case we will use the feature.
1. What is the cost of the single release branch?


```
no subtrees:

git count-objects --human-readable  7 objects, 28.00 KiB
du -h . 144k

1 subtree:
git count-objects --human-readable
24 objects, 4.04 MiB


2 subtrees:
git count-objects --human-readable
34 objects, 4.08 MiB

both subtrees removed:

du -h 4.2 M
git count-objects --human-readable
15 objects, 60.00 KiB (after gc)

```
conclusion:
Git stores the histories of the repositories you have cloned, so pointing to the same repository doesn't increase ammount of data transmitted over network.
The size of files on your local files system will depend on how many files you will checkout.
Git effectively cleans removed branches.
