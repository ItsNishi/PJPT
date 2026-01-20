# Variables and Methods

## Variables

```python
quote = "this is a string variable"    # String
age = 30                               # Integer
gpa = 3.7                              # Float (decimal)

print(quote)
```

## String Methods

```python
quote = "hello world"

print(quote.upper())    # HELLO WORLD
print(quote.lower())    # hello world
print(quote.title())    # Hello World
print(len(quote))       # 11 (character count)
```

## Type Conversion

```python
print(int(age))         # 30
print(int(30.1))        # 30
print(int(30.9))        # 30 (truncates, doesn't round)
print(str(age))         # "30" (string)
```

## String Concatenation with Variables

```python
# Must convert non-strings with str()
print("My quote: " + quote + " and my age is " + str(age))
```

## Variable Modification

```python
age = 30
age += 1        # age is now 31

birthday = 1
age += birthday # age is now 32
```
