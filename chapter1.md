---
title       : Insert the chapter title here
description : Insert the chapter description here
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

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
