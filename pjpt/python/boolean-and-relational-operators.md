# Boolean and Relational Operators

## Boolean Values

```python
bool1 = True
bool2 = 3 * 3 == 9    # True (expression evaluates)
bool3 = False
bool4 = 3 * 3 != 9    # False

print(type(bool1))    # <class 'bool'>

bool5 = "True"
print(type(bool5))    # <class 'str'> - string, not boolean
```

## Relational Operators

```python
greater_than = 7 > 5           # True
less_than = 5 < 7              # True
greater_than_equal = 7 >= 7    # True
less_than_equal = 7 <= 7       # True
```

## Boolean Operators

| Expression | Result |
|------------|--------|
| `True and True` | True |
| `True and False` | False |
| `True or True` | True |
| `True or False` | True |
| `not True` | False |

```python
test_and = True and True      # True
test_and2 = True and False    # False
test_or = True or True        # True
test_or2 = True or False      # True
test_not = not True           # False
```
