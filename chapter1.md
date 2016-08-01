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
# Seed the random number generator
np.random.seed(42)
```

*** =sample_code
```{python}
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
--- type:NormalExercise lang:python xp:50 skills:1 key:666730c56f
## Testing having random.seed in PEC

Testing random.seed in PEC as opposed to in Sample Code/Solution Code.

*** =instructions
- Click "Submit Answer" and see result. `random.seed` is in PEC.

*** =hint
hint comes here

*** =pre_exercise_code
```{python}
import numpy as np

# Seed the random number generator
np.random.seed(42)
```

*** =sample_code
```{python}
x = np.random.randn(50)
print(x)
```

*** =solution
```{python}
x = np.random.randn(50)
print(x)
```

*** =sct
```{python}
test_function("numpy.random.randn")
test_object("x")
test_function("print")
```
--- type:NormalExercise lang:python xp:100 skills:1 key:4e6305dc0e
## Testing having random.seed in Sample Code/Solution Code

Testing random.seed in PEC in Sample Code/Solution Code as a comparison.


*** =instructions
- Click "Submit Answer".

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

x = np.random.randn(50)
print(x)

```

*** =solution
```{python}
# Seed the random number generator
np.random.seed(42)

x = np.random.randn(50)
print(x)

```

*** =sct
```{python}
test_function("numpy.random.randn")
test_object("x")
test_function("print")
```
