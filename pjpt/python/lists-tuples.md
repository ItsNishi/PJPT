# Lists/ Tuples

```
vehicles = ["car", "truck", "van", "semi", "suv"] 
```

```
print(vehicles[1]) #returns the second item in the list - index / indices
print(vehicles[0]) #returns the first item in the list
print(vehicles[1:3]) #returns the first number given until right before last number given
print(vehicles[1:4]) #returns all 
print(vehicles[1:]) #returns everything from number to end of list
print(vehicles[:1]) #everything before 1
print(vehicles[:2])
print(vehicles[-1]) #grabs last item
```

<pre><code>print(len(vehicles)) #counts items in list
<strong>vehicles.append("boat")
</strong>print(vehicles)
</code></pre>

```
vehicles.insert(2, "airplane") #inserts into 3 spot
print(vehicles)

vehicles.pop() #removes last item
print(vehicles)

vehicles.pop(0) #removes first item 
print(vehicles)
```

```
vehicles_brands = ['porsche', '50 First Dates']
our_favorite_movies = movies + amber_movies
print(our_favorite_movies)
```

Tuples are immutable, meaning you cannot modify their elements. Once a tuple is created, its values cannot be changed.
