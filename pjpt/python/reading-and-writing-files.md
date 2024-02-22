# Reading and Writing Files

Read a file

```
# Open the file in read mode
file = open("example.txt", "r")


# Read the entire content
content = file.read()
print(content)


# Read a single line
line = file.readline()
print(line)


# Read all lines
lines = file.readlines()
print(lines)


# Close the file
file.close()
```

Write to a file. Will overwrite file

```
# Open the file in write mode
file = open("example.txt", "w")


# Write content to the file
file.write("Hello, World!\n")
file.write("This is a new line.")


# Close the file
file.close()
```

Append a file

```
# Open the file in append mode
file = open("example.txt", "a")


# Append content to the file
file.write("\nThis is appended content.")


# Close the file
file.close()
```

Recommendations

```
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```
