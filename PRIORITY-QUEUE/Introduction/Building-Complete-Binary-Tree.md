# Building Complete Binary Tree

#### Building Complete Binary Tree from an array

For a parent at index i(root of the tree is of index 0), What are its children?

**Children-1**: Index ***2*i + 1**

**Children-2**: Index ***2*i + 2**

Also, for the indices of a children let's say i, **Parent** index will be: *floor((i-1)/2)*.

So, we can add edges from those children to its parent. For each node we have to perform this operation until for any node, one or more children are available.

------------------------------------------------------------------------------
