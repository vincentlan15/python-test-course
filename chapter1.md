---
title       : Insert the chapter title here
description : Insert the chapter description here
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:50 skills:1 key:666730c56f
## Do Frog A and Frog B come from the same distribution?

Now you'll put your `permutation_sample()` function to work. You will use the difference of means as the test statistic. You need to write a function that computes the difference in the mean of two data sets to pass into `permutation_sample()`. Then call `permutation_sample()` to get your samples. Finally, the p-value is the fraction of your samples where the difference in means was less than the observed difference in means, 0.29 N.

The two data sets are stored in the arrays `force_a` and `force_b`.

*** =instructions
- Write a function, `diff_of_means(data_1, data_2)`, to compute the difference of the means of two data sets.
- Compute the value of the difference in mean impact force between the two frogs from the data.
- Take 10,000 permutaiton samples.
- Compute the p-value as the fraction of samples with the difference in mean impact force that is greater than the observed value.
- Print the p-value.

*** =hint
hint comes here

*** =pre_exercise_code
```{python}
import numpy as np
import pandas as pd

# Pull out data
df = pd.read_csv('https://s3.amazonaws.com/assets.datacamp.com/production/course_1397/datasets/frog_tongue.csv', comment='#')

force_a = df.loc[df['ID']=='II', 'impact force (mN)'].values / 1000
force_b = df.loc[df['ID']=='IV', 'impact force (mN)'].values / 1000

def ecdf(data):
    """Compute ECDF for a one-dimensional array of measurements."""
    x = np.sort(data)
    y = np.arange(1, len(data) + 1) / len(data)
    return x, y

def bootstrap_sample_1d(data, func, n_samples):
    """Take bootstrap samples of array of data."""
    # Initialize samples
    samples = np.empty(n_samples)

    # Take samples
    for i in range(n_samples):
        samples[i] = func(np.random.choice(data, len(data)))

    return samples

def permutation_sample(data_1, data_2, func, n_samples):
    """Generate samples for a permutation test."""
    # Concatenate the data sets together
    data = np.concatenate((data_1, data_2))

    # Initialize the array containing samples
    samples = np.empty(n_samples)

    for i in range(n_samples):
        # Permute the data
        data_perm = np.random.permutation(data)

        # Partition the permuted data into two data sets
        data_a = data_perm[:len(data_1)]
        data_b = data_perm[len(data_1):]

        # Compute the test statistic
        samples[i] = func(data_a, data_b)

    return samples
```

*** =sample_code
```{python}
# Seed random number generator
np.random.seed(42)

def diff_of_means(data_1, data_2):
    return np.mean(data_1) - np.mean(data_2)

# Compute difference of mean impact force from experiment
empirical_diff_means = diff_of_means(force_a, force_b)

# Draw 10,000 permutation samples
samples = permutation_sample(force_a, force_b, diff_of_means, 10000)

# Compute p-value
p = np.sum(samples > empirical_diff_means) / len(samples)

# Print the result
print('p-value =', p)
```

*** =solution
```{python}
# Seed random number generator
np.random.seed(42)

def diff_of_means(data_1, data_2):
    return np.mean(data_1) - np.mean(data_2)

# Compute difference of mean impact force from experiment
empirical_diff_means = diff_of_means(force_a, force_b)

# Draw 10,000 permutation samples
samples = permutation_sample(force_a, force_b, diff_of_means, 10000)

# Compute p-value
p = np.sum(samples > empirical_diff_means) / len(samples)

# Print the result
print('p-value =', p)
```

*** =sct
```{python}
test_function_definition("diff_of_means", results=[([3,2],[5,6]),([2,2],[8,5])], wrong_result_msg="Did you define diff_of_means?")

test_function("diff_of_means")
test_object("empirical_diff_means")

test_function("permutation_sample", do_eval=False)
test_object("samples", do_eval=False)

test_function("numpy.sum")
test_object("p")

test_function("print")

success_msg("""The p-value of 0.006 tells you that there is about a 0.6% chance that you would get the difference of means observed in the experiment if frogs were exactly the same. A p-value below 0.01 is typically said to be "statistically significant,", but: warning! warning! warning! You have computed a p-value; it is a number. I encourage you not to distill it to a yes-or-no phrase. p = 0.006 and p = 0.000000006 are both said to be "statistically significant," but they are definitely not the same!""")
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
