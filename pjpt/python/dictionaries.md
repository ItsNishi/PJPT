# Dictionaries

key/value pairs {}



drinks = {"White Russian": 7, "Old Fashion": 10, "Lemon Drop": 8} #drink is key, price is value print(drinks)

employees = {"Finance": \["Bob", "Linda", "Tina"], "IT": \["Gene", "Louise", "Teddy"], "HR": \["Jimmy Jr.", "Mort"]} employees\['Legal'] = \["Mr. Frond"] #adds new key:value pair print(employees)

employees.update({"Sales": \["Andie", "Ollie"]}) #adds new key:value pair print(employees)

drinks\['White Russian'] = 8 print(drinks)

print(drinks.get("White Russian"))
