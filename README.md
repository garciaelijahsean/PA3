# Pandas Practice Problems - PA #3

This repository contains solutions to practice problems using Pandas. Just like in NumPys, we need to access the pandas library that can be written as: 

```python
    import pandas as pd 
```

Things to take note of:<br>
- `import` -> just lets you use external libraries
- `pandas` -> the library to access and use for codes that involves high-performance and easy to use data structures
- `as pd` -> just an alias to shorten "pandas"

Before we get onto the problems, we have to download the following file and save it to our default user folder: `cars.csv`. The format for this README.md file is going to be code with explanation as there as sub-objectives per problems that requires different outputs. 

### Now onto the problems:
---
### PROBLEM 1:<br>
For problem 1, it is asking for 2 outputs: (a) load the corresponding .csv file into ta data frame named cars using pandas and (b) display the first five and last five rwos of the resulting cars. After we're done, we save the file as `Surname_Pandas_P1.py` and create a new file for the next problem. 

### Code with explanation:<br>
#### Part A:<br>
```python
    cars = pd.read_csv('cars.csv') 
    cars
```

- We load the file using `pd.read_csv('cars.csv')` into a pandas DataFrame. Then in the next line, input `cars` to display the Dataframe

#### Part B:<br>
```python
    cars.head()
```

- We use `cars.head()` to display the first five rows of the dataset. Execute the code and it should output the first five rows of the dataset. 

```python
    cars.tail()
```

- Same thing goes for the last five rows, instead of `cars.head()`, we use `cars.tail()`. Execute the code and it should output the last five rows of the dataset
---
### PROBLEM 2: 
For problem 2, it is asking for 4 outputs: (a) display the first five rows with odd-numbered columns of cars, (b) display the row that contains the 'Model' of Mazda RX4', (c) How many cylinders (‘cyl’) does the car model ‘Camaro Z28’ have?, and (d) Determine how many cylinders (‘cyl’) and what gear type (‘gear’) do the car models ‘Mazda RX4 Wag’, ‘Ford Pantera L’ and ‘Honda Civic’ have. Afterwards, we save the file as `Surname_Pandas_P2.py`.

### Code with explanation:<br>
Before anything else, since this is a new file, we have to import the pandas library again using `import pandas as pd`
```python
cars = pd.read_csv('cars.csv')
cars
```

- Load the dataset into a pandas DataFrame.

#### Part A:
```python
cars.iloc[:5, 1::2] 
```

- We use `cars.iloc[:5, 1::2]` to display the first five rows with odd-numered columns of cars. `iloc` is the index location and used to select rows and columns by their integer position (not by labels like .loc). For the rows, we use `:5` to locate the first five. `:5` just means everything from the beginning until index 5. For the columns, we use Python slicing. As such, we use `1::2` to get the odd-numbered columns. `1:` means it starts from index 1 then a colon next to it, refering to go until the end. `:2` means it takes every second column. 


#### Part B:
```python
cars.loc[cars['Model'] == 'Mazda RX4'] 
```

- We used `.loc` this time as we're going to select by labels. We use `cars['Model'] == 'Mazda RX4'` to display the row that contains the 'Model' of Mazda RX4'. 

#### Part C:
```python
cars.loc[(cars['Model']=='Camaro Z28'), ['cyl']]
```

- Same as Part B, we used `.loc` since we are dealing with labels. Then, we use `cars.loc[(cars['Model']=='Camaro Z28'), ['cyl']]`. It features a row selector again like Part B but for this part, `cars['Model']=='Camaro Z28'` is a boolean series and if the condition is true, it returns the cyl column of Camaro Z28. 

#### Part D:
```python
cars.loc[cars['Model'].isin(['Mazda RX4 Wag', 'Ford Pantera L', 'Honda Civic']), ['cyl', 'gear']]
```

- It uses `.loc` so it deals with labels. Similar to the previous problem, this line of code is a boolean series. `.isin` checks each row's 'Model' (basically when you want to check multiple labels). And from the matching rows, we select the `cyl` and `gear` values as that's what the problem is asking for. 
