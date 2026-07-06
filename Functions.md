# Functions
[Part One](https://github.com/Duck-Duck-Codes/Python_Portfolio/blob/main/Functions.md#functions-1)

[Part Two](https://github.com/Duck-Duck-Codes/Python_Portfolio/blob/main/Functions.md#functions-2)

[Part Three](https://github.com/Duck-Duck-Codes/Python_Portfolio/blob/main/Functions.md#functions-3)

[Part Four](https://github.com/Duck-Duck-Codes/Python_Portfolio/blob/main/Functions.md#functions-4)
## Functions 1
Simple use of defining functions
```python
fahrenheit_val = 99
celsius_val = ((fahrenheit_val - 32) * (5/9))

print(celsius_val)
```
    37.22222222222222




```python
fahrenheit_val2 = 43
celsius_val2 = ((fahrenheit_val2 - 32) * (5/9))

print(celsius_val2)
```
    6.111111111111112




```python
def explicit_fahr_to_celsius(temp):
    # Assign the converted value to a variable
    converted = ((temp - 32) * (5/9))
    # Return the values of the new variable
    return converted
```

```python
def fahr_to_celsius(temp):
    # Return converted value more efficiently using the return function without
    # creating a new variable. This code does the same as the previous function but it 
    # is more explicit in explaining how the return command works.
    return ((temp - 32) * (5/9))
```

```python
fahr_to_celsius(32)
```


    0.0






```python
print('Freezing point of water:', fahr_to_celsius(32), 'C')
print('Boiling point of water:', fahr_to_celsius(212), 'C')
```
    Freezing point of water: 0.0 C
    Boiling point of water: 100.0 C




```python
def celsius_to_kelvin(temp_c):
    return temp_c + 273.15

print('freezing point of water in Kelvin:', celsius_to_kelvin(0.))
```
    freezing point of water in Kelvin: 273.15




```python
def fahr_to_kelvin(temp_f):
    temp_c = fahr_to_celsius(temp_f)
    temp_k = celsius_to_kelvin(temp_c)
    return temp_k

print('freezing point of water in Kelvin:', fahr_to_kelvin(212.0))
```
    freezing point of water in Kelvin: 373.15




```python
temp_kelvin = fahr_to_kelvin(212.0)
print('Temperature in Kelvin was:', temp_kelvin)
```
    Temperature in Kelvin was: 373.15




```python
def print_temperatures():
    print('Temperature in Fahrenheit was:', temp_fahr)
    print('Temperature in Kelvin was:', temp_kelvin)
    
temp_fahr = 212.0
temp_kelvin = fahr_to_kelvin(temp_fahr)

print_temperatures()
```
    Temperature in Fahrenheit was: 212.0
    Temperature in Kelvin was: 373.15
## Functions 2
Using a defined variable to simplify repetitive tasks as well as including an error message when neccessary.
```python
import numpy
import glob
import matplotlib
import matplotlib.pyplot
```

```python
# Define a variable that can generate a plot for average, max, and min for a patient file
def visualize(filename):
    
    data = numpy.loadtxt(fname = filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))
    
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
    matplotlib.pyplot.show()
```

```python
# Create a variable that detects inflammation levels and prints report based on data
def detect_problems(filename):
    
    data = numpy.loadtxt(fname = filename, delimiter = ',')
    
    if numpy.amax(data, axis = 0)[0] == 0 and numpy.amax(data, axis = 0)[20] == 20:
        print('Suspicious looking maxima!')
    elif numpy.sum(numpy.amin(data, axis = 0)) == 0:
        print('Minima add up to zero!')
    else:
        print('Seems OK!')
```

```python
# Print the name of the file, visualize function and, report message
filenames = sorted(glob.glob('inflammation*.csv'))

for filename in filenames[:3]:
    print(filename)
    visualize(filename)
    detect_problems(filename)
```
    inflammation-01.csv




<img width="712" height="208" alt="output_3_1" src="https://github.com/user-attachments/assets/17056bd0-333b-4bc4-9128-b2e33ba03395" />

    Suspicious looking maxima!
    inflammation-02.csv




<img width="712" height="208" alt="output_3_3" src="https://github.com/user-attachments/assets/bd90c5cc-5489-47b4-948b-5a61228bcba2" />

    Suspicious looking maxima!
    inflammation-03.csv




<img width="712" height="208" alt="output_3_5" src="https://github.com/user-attachments/assets/524ea810-4806-49b9-ad5f-a591987c04ea" />

    Minima add up to zero!



## Functions 3
```python
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```

```python
z = numpy.zeros((2, 2))
print(offset_mean(z, 3))
```
    [[3. 3.]
     [3. 3.]]




```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')

print(offset_mean(data, 0))
```
    [[-6.14875 -6.14875 -5.14875 ... -3.14875 -6.14875 -6.14875]
     [-6.14875 -5.14875 -4.14875 ... -5.14875 -6.14875 -5.14875]
     [-6.14875 -5.14875 -5.14875 ... -4.14875 -5.14875 -5.14875]
     ...
     [-6.14875 -5.14875 -5.14875 ... -5.14875 -5.14875 -5.14875]
     [-6.14875 -6.14875 -6.14875 ... -6.14875 -4.14875 -6.14875]
     [-6.14875 -6.14875 -5.14875 ... -5.14875 -5.14875 -6.14875]]




```python
print('original min, mean and max are:', numpy.amin(data), numpy.mean(data), numpy.amax(data))
offset_data = offset_mean(data, 0)
print('min, mean, and max of offset data are:',
     numpy.amin(offset_data),
     numpy.mean(offset_data),
     numpy.amax(offset_data))
```
    original min, mean and max are: 0.0 6.14875 20.0
    min, mean, and max of offset data are: -6.14875 2.842170943040401e-16 13.85125




```python
print('std dev before and after:', numpy.std(data), numpy.std(offset_data))
```
    std dev before and after: 4.613833197118566 4.613833197118566




```python
print('difference in standard deviation before and after:',
     numpy.std(data) - numpy.std(offset_data))
```
    difference in standard deviation before and after: 0.0




```python
# offset_mean(data, target_mean_value):
# return a new array containing the original data with its mean offset to match the desired value.
# This data should be imputed as a measurements in columns and samples in rows

def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```

```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data with its mean offset to match the desired value"""
    return (data - numpy.mean(data)) + target_mean_value
```

```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data 
    with its mean offset to match the desired value
    
    Examples
    ------------
    
    >>> offset_mean([1,2,3], 0)
    array([-1., 0., 1.])"""
    return (data - numpy.mean(data)) + target_mean_value
```

```python
help(offset_mean)
```
    Help on function offset_mean in module __main__:
    
    offset_mean(data, target_mean_value)
        Return a new array containing the original data 
        with its mean offset to match the desired value
        
        Examples
        ------------
        
        >>> offset_mean([1,2,3], 0)
        array([-1., 0., 1.])
    




## Functions 4
```python
numpy.loadtxt('inflammation-01.csv', delimiter = ',')
```


    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])






```python
def offset_mean(data, target_mean_value = 0.0):
    """Return a new array containing the original data 
    with its mean offset to match the desired value, (0 by default).
    
    Examples
    ------------
    
    >>> offset_mean([1,2,3], 0)
    array([-1., 0., 1.])"""
    return (data - numpy.mean(data)) + target_mean_value
```

```python
test_data = numpy.zeros((2, 2))
print(offset_mean(test_data, 3))
```
    [[3. 3.]
     [3. 3.]]




```python
print(offset_mean(test_data))
```
    [[0. 0.]
     [0. 0.]]




```python
def display(a=1, b=2, c=3):
    print('a:', a, 'b:', b, 'c:', c)
    
print('no parameters:')
display()
print('one parameter:')
display(55)
print('two parameters:')
display(55, 66)
```
    no parameters:
    a: 1 b: 2 c: 3
    one parameter:
    a: 55 b: 2 c: 3
    two parameters:
    a: 55 b: 66 c: 3




```python
print('only setting the value of c')
display(c = 77)
```
    only setting the value of c
    a: 1 b: 2 c: 77




```python
numpy.loadtxt('inflammation-01.csv', delimiter = ',')
```


    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])

