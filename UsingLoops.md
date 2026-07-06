# Using Loops
Using 'for' loops to facilitate repetitive tasks.
```python
odds = [1, 3, 5, 7]
```

```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```
    1
    3
    5
    7




```python
# Usage to print multiple values
odds = [1, 3, 5, 7, 9, 11]

for num in odds:
    print(num)
```
    1
    3
    5
    7
    9
    11




```python
# Usage to count values
length = 0
names = ['Curie', 'Darwin', 'Turing']

for value in names:
    length = length + 1
print('There are', length, 'names in the list.')
```
    There are 3 names in the list.




```python
name = "Rosalind"
for name in ['Curie', 'Darwin', 'Turing']:
    print(name)
print('after the loop, name is', name)
```
    Curie
    Darwin
    Turing
    after the loop, name is Turing




```python
print(len([0, 1, 2, 3]))
```
    4




```python
name = ['Curie', 'Darwin', 'Turing']

print(len(name))
```
    3
