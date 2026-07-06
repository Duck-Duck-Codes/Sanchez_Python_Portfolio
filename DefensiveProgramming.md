# Defensive Programming
Purposefully cause an error code to become familiar with troubleshoot messages. Create a defined user function and include a personal error code that appears for the correct instance.
```python
# Trigger simple error message
numbers = [1.5, 2.3, 0.7, -0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive values'
    total += num
print('total is:', total)
```

    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-1-13c7d5640ddd> in <module>
          2 total = 0.0
          3 for num in numbers:
    ----> 4     assert num > 0.0, 'Data should only contain positive values'
          5     total += num
          6 print('total is:', total)


    AssertionError: Data should only contain positive values




```python
# Create a user defined function that contains a message that explains how to use the command when asked,
# as well as error messages that only appear when the corresponding error is committed
def normalize_rectangle(rect):
    """Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis.
    input format is (x0, y0, x1, y1).
    (x0, y0) and (x1, y1) define the lower left and upper right corners of the rectangle respectively."""
    assert len(rect) == 4, 'Rectangle must contain 4 coordinates'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'
    
    dx = x1 - x0
    dy = y1 - y0
    if dx > dy:
        scaled = dx / dy
        upper_x, upper_y = 1.0, scaled
    else:
        scaled = dx / dy
        upper_x, upper_y = scaled, 1.0
        
    assert 0 < upper_x <= 1.0, 'Calculated upper x coordinated invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper y coordinated invalid'
    
    return(0, 0, upper_x, upper_y)
```

```python
# Trigger the error message 'Rectangle must contain 4 coordinates'
print(normalize_rectangle((0.0, 1.0, 2.0)))
```

    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-3-a81b6ed7619a> in <module>
    ----> 1 print(normalize_rectangle((0.0, 1.0, 2.0)))
    

    <ipython-input-2-deb91e022f48> in normalize_rectangle(rect)
          3     input format is (x0, y0, x1, y1).
          4     (x0, y0) and (x1, y1) define the lower left and upper right corners of the rectangle respectively."""
    ----> 5     assert len(rect) == 4, 'Rectangle must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
          7     assert x0 < x1, 'Invalid X coordinates'


    AssertionError: Rectangle must contain 4 coordinates




```python
# Trigger the error message 'Invalid X coordinates'
print(normalize_rectangle((4.0, 2.0, 1.0, 5.0)))
```

    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-4-5e28a32bada1> in <module>
    ----> 1 print(normalize_rectangle((4.0, 2.0, 1.0, 5.0)))
    

    <ipython-input-2-deb91e022f48> in normalize_rectangle(rect)
          5     assert len(rect) == 4, 'Rectangle must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
    ----> 7     assert x0 < x1, 'Invalid X coordinates'
          8     assert y0 < y1, 'Invalid Y coordinates'
          9 


    AssertionError: Invalid X coordinates




```python
# Correct usage of function
print(normalize_rectangle((0.0, 0.0, 1.0, 5.0)))
```
    (0, 0, 0.2, 1.0)




```python
# Trigger the error message 'Calculated upper y coordinated invalid'
print(normalize_rectangle((0.0, 0.0, 5.0, 1.0)))
```

    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-6-1337bef8f4bf> in <module>
    ----> 1 print(normalize_rectangle((0.0, 0.0, 5.0, 1.0)))
    

    <ipython-input-2-deb91e022f48> in normalize_rectangle(rect)
         18 
         19     assert 0 < upper_x <= 1.0, 'Calculated upper x coordinated invalid'
    ---> 20     assert 0 < upper_y <= 1.0, 'Calculated upper y coordinated invalid'
         21 
         22     return(0, 0, upper_x, upper_y)


    AssertionError: Calculated upper y coordinated invalid
