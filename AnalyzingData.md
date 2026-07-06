# Analyzing Data 1 and 2
Using python coding methods to simplify mathematical data analysis 
```python
import numpy
```

```python
# Data from loaded file will print once read
numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```


    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])






```python
# Applying a variable name to the function will prevent data from being printed after being read
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```

```python
# Print data using print() function
print(data)
```
    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]




```python
# Print the area of data cells
print(data.shape)
```
    (60, 40)




```python
print('first value in data:', data[0,0])
```
    first value in data: 0.0




```python
print('middle value in data:', data[29, 19])
```
    middle value in data: 16.0




```python
# Print 4 rows and 10 columns
print(data[0:4, 0:10])
```
    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]




```python
# Print 5 rows and 10 columns
print(data[5:10, 0:10])
```
    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]




```python
# Isolated the first 3 rows and last 4 columns of the dataset
small = data[:3, 36:]
```

```python
print('small is')
```
    small is




```python
print(small)
```
    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]




```python
# Use a numpy function
print(numpy.mean(data))
```
    6.14875




```python
#Assign names to multiple values in one function
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```

```python
print(maxval)
print(minval)
print(stdval)
```
    20.0
    0.0
    4.613833197118566




```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)
```

```python
print(maxval)
print(minval)
print(stdval)
```
    20.0
    0.0
    4.613833197118566




```python
print('maximum inflammation:', maxval)
print('minimum inflammation:', minval)
print('standard deviation:', stdval)
```
    maximum inflammation: 20.0
    minimum inflammation: 0.0
    standard deviation: 4.613833197118566




```python
# Sometimes we want to look at variation in statistical values
patient_0 = data[0, :] # 0 on the first row, everything on the columns
print('maximum inflammation for patient 0:', numpy.amax(patient_0))
```
    maximum inflammation for patient 0: 18.0




```python
print('maximum inflammation for patient 2:', numpy.amax(data[2, :]))
```
    maximum inflammation for patient 2: 19.0




```python
print(numpy.mean(data, axis = 0))
```
    [ 0.          0.45        1.11666667  1.75        2.43333333  3.15
      3.8         3.88333333  5.23333333  5.51666667  5.95        5.9
      8.35        7.73333333  8.36666667  9.5         9.58333333 10.63333333
     11.56666667 12.35       13.25       11.96666667 11.03333333 10.16666667
     10.          8.66666667  9.15        7.25        7.33333333  6.58333333
      6.06666667  5.95        5.11666667  3.6         3.3         3.56666667
      2.48333333  1.5         1.13333333  0.56666667]




```python
print(numpy.mean(data, axis = 0).shape)
```
    (40,)




```python
print(numpy.mean(data, axis = 1))
```
    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]

# Analyzing Data 3
Using python to create a visual representation for data analysis
```python
import numpy
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```

```python
# Heat map of inflammation over time
import matplotlib.pyplot
image = matplotlib.pyplot.imshow(data)
matplotlib.pyplot.show()
```

<img width="178" height="251" alt="output_1_0" src="https://github.com/user-attachments/assets/3ad9b9ed-c28e-40e5-85a3-f4dd5b4ea99e" />


```python
# Average inflammation over time
ave_inflammation = numpy.mean(data, axis = 0)
ave_plot = matplotlib.pyplot.plot(ave_inflammation)
matplotlib.pyplot.show()
```

<img width="368" height="248" alt="output_2_0" src="https://github.com/user-attachments/assets/5e4fa3cc-a62f-491d-9066-6cbb94896b5d" />

```python
# Max inflammation over time
max_plot = matplotlib.pyplot.plot(numpy.amax(data, axis = 0))
matplotlib.pyplot.show()
```

<img width="378" height="248" alt="output_3_0" src="https://github.com/user-attachments/assets/3eba0d01-fda2-42b5-9b28-1cc861ad6c74" />

```python
# Min inflammation over time
min_plot = matplotlib.pyplot.plot(numpy.amin(data, axis = 0))
matplotlib.pyplot.show()
```

<img width="362" height="248" alt="output_4_0" src="https://github.com/user-attachments/assets/e70de3ce-003e-441b-8233-2014b767a10a" />

```python
# Plot all three figures at once
fig = matplotlib.pyplot.figure(figsize =(10.0, 3.0))

axes1 = fig.add_subplot(1, 3, 1)
axes2 = fig.add_subplot(1, 3, 2)
axes3 = fig.add_subplot(1, 3, 3)

axes1.set_ylabel('average')
axes1.plot(numpy.mean(data, axis = 0))

axes2.set_ylabel('max')
axes2.plot(numpy.amax(data, axis = 0))

axes3.set_ylabel('min')
axes3.plot(numpy.amin(data, axis = 0))

fig.tight_layout()
matplotlib.pyplot.savefig('inflammation.png')
matplotlib.pyplot.show()
```

<img width="712" height="208" alt="output_5_0" src="https://github.com/user-attachments/assets/c5a8b922-c9bd-4cd7-8c86-a76955b8724a" />
