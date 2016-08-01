---
title       : Insert the chapter title here
description : Insert the chapter description here
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:50 skills:1 key:666730c56f
## The np.random module and Bernoulli trials

You can think of a Bernoulli trial as a flip of a possibly biased coin. Specifically, each coin flip has a probability $p$ of landing heads (success) and probability $1-p$ of landing tails (failure). To make it concrete in our finance example, let $p$ be the probability that a home buyer will pay off the loan (success). In this exercise, you will write a function to perform a Bernoulli trail, `bernoulli_trial(p)`, which returns `True` for a success. To do this, use the `np.random.rand()` function, which returns a random number between zero and one.  Run this function 100,000 times for `p = 0.95` to check to see if you get the number of successes you expect.

*** =instructions
- Seed the random number generator
- Write the function `bernoulli_trial(p)`. Within this function:
    * Choose a random number between zero and one.
    * If the number you chose is less than `p`, return `True`.
    * Otherwise, return `False`.
- Initialize the counter of `True`s, which are Bernoulli trial successes (buyer pays off his or her mortgage), to zero.
- Write a `for` loop to count the number of successes in 100,000 trials with `p=0.95`.
- Count the fraction of trials that were successes.
- Print the result.

*** =hint
hint comes here

*** =pre_exercise_code
```{python}
import numpy as np
```

*** =sample_code
```{python}
# Seed the random number generator
np.random.seed(42)

def bernoulli_trial(p):
    """Perform Bernoulli trial with success probability p."""
    # Choose random number between zero and one
    random_number = np.random.random()

    # Check to see if it is less than p and return True, else return False
    if random_number < p:
        return True
    return False

# Initialize counter
n_success = 0

# Perform Bernoulli trials
for _ in range(100000):
    n_success += bernoulli_trial(0.95)

# Print fraction of successes
print('fraction success:', n_success/100000)

```

*** =solution
```{python}
# Seed the random number generator
np.random.seed(42)

def bernoulli_trial(p):
    """Perform Bernoulli trial with success probability p."""
    # Choose random number between zero and one
    random_number = np.random.random()

    # Check to see if it is less than p and return True, else return False
    if random_number < p:
        return True
    return False

# Initialize counter
n_success = 0

# Perform Bernoulli trials
for _ in range(100000):
    n_success += bernoulli_trial(0.95)

# Print fraction of successes
print('fraction success:', n_success/100000)
```

*** =sct
```{python}
#test_function_definition("bernoulli_trial", results=[(0.3),(0.5),(0.8)])

def test_for_iter():
    msg = "Make sure you iterate over 100,000 trials."
    test_function("range", incorrect_msg=msg)
test_for_loop(index=1,
              for_iter=test_for_iter)

test_object("n_success", incorrect_msg="Did you initiate and update `n_success` correctly?")

test_function("print")

success_msg("The fraction success is close to our expected value of 0.95.")
```
--- type:NormalExercise lang:python xp:100 skills:1 key:4e6305dc0e
## Plot the movies yourself

Do you remember the plot of the last exercise? Let's make an even cooler plot!

A dataset of movies, `movies`, is available in the workspace.

*** =instructions
- The first function, `np.unique()`, uses the `unique()` function of the `numpy` package to get integer values for the movie genres. You don't have to change this code, just have a look!
- Import `pyplot` in the `matplotlib` package. Set an alias for this import: `plt`.
- Use `plt.scatter()` to plot `movies.runtime` onto the x-axis, `movies.rating` onto the y-axis and use `ints` for the color of the dots. You should use the first and second positional argument, and the `c` keyword.
- Show the plot using `plt.show()`.

*** =hint
- You don't have to program anything for the first instruction, just take a look at the first line of code.
- Use `import ___ as ___` to import `matplotlib.pyplot` as `plt`.
- Use `plt.scatter(___, ___, c = ___)` for the third instruction.
- You'll always have to type in `plt.show()` to show the plot you created.

*** =pre_exercise_code
```{python}
import pandas as pd
movies = pd.read_csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

import numpy as np
```

*** =sample_code
```{python}
# Get integer values for genres
_, ints = np.unique(movies.genre, return_inverse = True)

# Import matplotlib.pyplot


# Make a scatter plot: runtime on  x-axis, rating on y-axis and set c to ints


# Show the plot

```

*** =solution
```{python}
# Get integer values for genres
_, ints = np.unique(movies.genre, return_inverse = True)

# Import matplotlib.pyplot
import matplotlib.pyplot as plt

# Make a scatter plot: runtime on  x-axis, rating on y-axis and set c to ints
plt.scatter(movies.runtime, movies.rating, c=ints)

# Show the plot
plt.show()
```

*** =sct
```{python}
# SCT written with pythonwhat: https://github.com/datacamp/pythonwhat/wiki

test_function("numpy.unique",
              not_called_msg = "Don't remove the call of `np.unique` to define `ints`.",
              incorrect_msg = "Don't change the call of `np.unique` to define `ints`.")

test_object("ints",
            undefined_msg = "Don't remove the definition of the predefined `ints` object.",
            incorrect_msg = "Don't change the definition of the predefined `ints` object.")

test_import("matplotlib.pyplot", same_as = True)

test_function("matplotlib.pyplot.scatter",
              incorrect_msg = "You didn't use `plt.scatter()` correctly, have another look at the instructions.")

test_function("matplotlib.pyplot.show")

success_msg("Great work!")
```
