# Fast BSP-Tree Generation Using Binary Searches

## A note from the author

Note: The document's preface states that this idea is in concept stages. This was because, at the time, I hadn't implemented it in production code. Since the writing of this document, I've used this technique a few times and it has proven quite powerful for fast BSP-tree generation.

## Original description

When building a BSP tree, it is most often necessary to find a reasonable balance between "fewest splits" (i.e. smallest tree) and "least depth" (i.e. best balance of nodes.) In most applications fewest splits tend to be more important, unfortunately, this is a most time consuming task.

Many applications that require BSP trees use a heuristic to determine a balance between "fewest splits" and "least depth". It is in this balance, that we find hope for an efficient solution.

It can be said, that because we're searching for a balance between depth and splits, there are a certain number of potential polygons (acting as splitters) that will result in the deepest tree, and should not be considered, even if they result in nearly no splits.

Given these criteria, we can find a range of the top contenders for least depth, and from them find the contender that results in the fewest splits. As long as we have enough "least depth" polygons to choose from, we'll find our target balance.

By doing this, we avoid the computationally expensive (and exhaustive) search for the fewest splits, and focus our energy on the least depth. From this reduced set, we find fewest splits, reducing our computation time.
