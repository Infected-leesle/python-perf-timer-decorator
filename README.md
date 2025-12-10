``` python
from time import perf_counter
from functools import wraps

def timer(func):
    fname = func.__name__
    pc = perf_counter

    @wraps(func)
    def wrapper(*args, **kwargs):
        start = pc()
        result = func(*args, **kwargs)
        duration = pc() - start
        print(fname, "→", f"{duration:.6f}", "sec")
        return result

    return wrapper
```
