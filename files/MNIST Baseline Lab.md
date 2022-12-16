# MNIST Baseline

We have now built a nearest prototype baseline for an easy version of MNIST: 3 vs 7.

Your task: Adapt our code to build a nearest prototype for the full MNIST problem.


## 0. Make a new notebook
* File -> New Notebook
* Name the new notebook mnist_baseline.ipynb
* Save a copy of this notebook in your nb2 github repo. **Be sure to use the name mnist_baseline.ipynb** 
## 1. Open our old notebook
* Hopefully you remember how to do this

## 2. General process
* My recommended approach is to go through our old notebook *cell by cell
* For each cell, make sure you know what the cell is actually doing
* Once you know what a cell is doing, decide whether or not it can be directly copied, copied and modified, or whether we don't need it at all

### Downloading all of the data
* Early in the notebook there is a cell which uses `MNIST_SAMPLE` when downloading data. Change this to `MNIST` to obtain the full MNIST dataset

### Dealing with 10 things instead of 2
* Note that the 3 vs 7 case is easier than our new problem
* There were several places in the original code where we made a 3-version and a 7-version of a variable
* WE SHOULD NOT MAKE 10 DIFFERENT VERSIONS OF ALL THESE VARIABLES! DO NOT DO THIS! ***YOU WILL NOT GET CREDIT***
* "But but but...Mr. Donoghue, what else can we do?"
* In almost every case, we should make an ordinary python list with 10 elements (index 0 corresponding to 0 digits, index 1 corresponding to 1 digits, etc.)
* You might find it easiest to use a list comprehension
* Since we're only dealing with 10 things, you could also do it the "basic" way, using a standard for loop


## 3. Questions
* How do I combine a list of tensors into one tensor, not by stacking them, but by combining them?
  * use `torch.cat()` where you put the list into the parens
  * example:
    *  suppose we have a list, `l`, with 3 elements, each an order-3 tensor with shape `(5, 28, 28)`
    *  `torch.stack(l)` would produce a an order-4 tensor with shape `(3, 5, 28, 28)`
    *  `torch.cat(l)` would produce an order-3 tensor with shape `(15, 28, 28)`. The `15` is caused by adding `5 + 5 + 5`
* How can I get the distance from the mean for each of the many images to each of the 10 means?
  * Suppose we  have an order-3 tensor representing `N` images we want to find the distance from the 10 means
  * we might be tempted to rely on standard torch "broadcasting" (the thing that lets us subtract order-3 from order-2 and similar)
  * This will sadly not work. The shapes in questions would be `(N, 28, 28)` and `(10, 28, 28)`
  * Broadcasting rules says that we start matching the shape lists from the right and that the numbers must match (or one of the numbers must be 1 or non-existent)
  * E.g., `(28, 28)` and `(10, 28,28)` works, but  `(N, 28, 28)` and `(10, 28, 28)`
  * What would work though, is `(N, 1, 28, 28)` and `(10, 28, 28)`, producing a tensor with `(N, 10, 28, 28)`. 
  * After `mnist_distance` collapses the last 2 axes this gives us `(N, 10)`
  * We can do all this by "adding" an axis to our stacked image tensor.
  * if `foo` is the name of our `(N, 28, 28)` stacked tensor, `foo.unsqueeze(1)` adds an axis at axis-index `1` (in between the `N` and the first `28`)
* How can I find the index of the smallest distance for each image?
  * After doing what's hinted at in the previous question, we'd have a tensor of distances that is `(N, 10)`
  * We need a tensor that is `(N,)` where each element stores the index of the smallest of the 10 distances for that image
  * The mentioned index would also be the same as the digit our baseline would predict!
  * if `foo` is our `(N,10)` distance tensor, `foo.argmin(1)` would give us exactly what we want

## 4. Bonus
* Investigate the results!!
* Try to do nearest neighbor instead!



