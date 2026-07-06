# Using Multiple Files
Using the glob command to find files with common names and call upon multiple files without the use of a 'for' loop.
```python
import glob
```

```python
print(glob.glob('inflammation*.csv'))
```
    ['inflammation-10.csv', 'inflammation-09.csv', 'inflammation-11.csv', 'inflammation-06.csv', 'inflammation-05.csv', 'inflammation-08.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-04.csv', 'inflammation-03.csv', 'inflammation-02.csv', 'inflammation-12.csv']




```python
# Use glob to apply a graphing function to multiple files
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]

for filename in filenames:
    print(filename)
    
    data = numpy.loadtxt(fname=filename, delimiter = ',')
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
    inflammation-01.csv




<img width="712" height="208" alt="output_2_1" src="https://github.com/user-attachments/assets/887289a4-4d76-4fc3-ad83-e2eb1a73a5f9" />


    inflammation-02.csv




<img width="712" height="208" alt="output_2_3" src="https://github.com/user-attachments/assets/dbf477b9-5f41-43d2-8a89-4cbcd3096619" />

    inflammation-03.csv




<img width="712" height="208" alt="output_2_5" src="https://github.com/user-attachments/assets/97c9585d-4ec7-41af-aa2e-1a02eba289cd" />
