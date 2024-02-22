# Advanced Strings

```
fruit = "cherry"
print(fruit[0]) # first letter
print(fruit[-1]) # last letter
```

You can not change strings. they are immutable

<pre><code><strong>#how to print certain characters in a string
</strong><strong>strings = "This is a string."
</strong>print(strings[:4]) #this prints the first 4 characters in the string
print(strings.split()) #delimeter #default delimiter is a space
strings_split = strings.split() #splits the string
strings_join = ' '.join(strings_split) # joins the string using spaces 
print(strings_join)
</code></pre>

<pre><code><strong>#how to store multiple quotes in a string
</strong><strong>quotes = "this is a list of quotes. 'Crazy!' 'You Dont Even Know'"
</strong>quotes = 'this is a list of quotes. \"Crazy!\" \"You Dont Even Know\"'

loads_of_space = "         yo     "
print(loads_of_space.strip())
</code></pre>

```
#searching in text to see if character is matching
print("B" in "Bus") #true
print("b" in "Bus") #false
```

```
text = "Hamburger"
letter = "H"

print(letter.lower() in text.lower()) #inproved

```

```
vegetable = "Carrot
print("My favorite vegetable is {}." .format(vegetable))
print("My favorite vegetable is %s" % vegetable)
print(f"My favorite vegetable is {vegetable}.")
```
