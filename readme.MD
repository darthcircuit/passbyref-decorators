# Assignment:

Write a decorator function that will convert any and all args passed to a function into a copy of the argument, rather than a reference to the object.

```
def pass_by_value(func):
    @functools.wraps(func)
    def wrapper_func(*args, **kwargs):
        # Your code goes here
        # For every argument in args, copy it and replace the original with the copy in args
        # Don't forget that args is an immutable tuple, so you
        # will need to create a new list instead and then pass that
        # to the function call itself
        return (
            func( *args, **kwargs)
        )
    return wrapper_func
```

## Use the following as test code:

```
@pass_by_value
def reverse(list_of_values, another_list, yet_another_list):
    list_of_values.sort(reverse=True)
    return list_of_values


values_list = [1,2,3,4,5,6,7,8,9]

print(values_list)
new_values_list = reverse(values_list)
print(new_values_list)
print(values_list)
```

## If it is working correctly, it should print:

```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
[9, 8, 7, 6, 5, 4, 3, 2, 1]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```
