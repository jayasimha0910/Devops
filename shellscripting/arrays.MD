## Arrays
- If we want to represent a group of values with a single name then we should go for arrays concept.

## How to Create Arrays:
If we know elements at the beginning:
```
courses=(Java Python Linux Django)
```
If we don't know elements at the biginning:
```
courses[0]=Java 
courses[1]=Python 
courses[2]=Linux 
courses[3]=Django
```
The index values need not be consecutive.We can take randomly.
```
courses[10]=DataScience 
courses[20]=Devops
```
## How to Access Elements:
We can access array elements by using index which is zero based.i.e the index of first element is zero
```
${courses[0]} -> First element 
${courses[1]} -> Second element 
${courses[@]} -> All elements present inside array. 
${courses[*]} -> All elements present inside array into a single string separated by first character in IFS(Internal Field Separator) 
${!courses[@]} -> It returns all indexes where elements are available. 
${#courses[@]} -> It returns the number of elements present inside array. 
${#courses[0]} -> It returns the length of first element.
```

## Demo Script:
```
#! /bin/bash 
courses[0]=Java 
courses[1]=Python 
courses[2]=Linux 
courses[3]=Django 
courses[10]=DataScience
courses[20]=Devops 
echo "First Element : ${courses[0]}" 
echo "Second Element : ${courses[1]}" 
echo "All Elements with @ : ${courses[@]}" 
echo "All elements with * : ${courses[*]}" 
echo "The indices where elements are available : ${!courses[@]}" 
echo "The total number of elements : ${#courses[@]}" 
echo "The length of first element : ${#courses[0]}"
```

output:
```
durgasoft@durgasoft:~/scripts$ test.sh 
First Element : Java 
Second Element : Python 
All Elements with @ : Java Python Linux Django DataScience Devops 
All elements with * : Java Python Linux Django DataScience Devops 
The indices where elements are available : 0 1 2 3 10 20 
The total number of elements : 6 
The length of first element : 4
```
