colors = ["R", "G", "B", "Y"]
countries = ["Germany", "Poland", "Czech", "Austria", "Italy"]

for i in range(len(countries)):
    print(countries[i], ":", colors[i % 4])
