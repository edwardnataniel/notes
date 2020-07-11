# NumPy Cheat Sheet

## NumPy Array creation
* np.array(my_list)  
list can be 1D, 2D (e.g. [[1,2,3],[4,5,6],[7,8,9]]), etc.

* np.arange(0, 10)  
similar to range. right exclusive

* np.zeros(3)
np.zeros((5,5))

* np.ones(4)

* np.linspace(0, 5, 10)  
10 evenly space points from 0 to 5 (inclusive)

* np.eye(4)

## Random Numbers
* np.random.rand(5)  
Uniformly distributed from 0 to 1  
np.random.rand(5,5). 5x5 array

* np.random.randn(2)  
standard normal  
np.random.randn(4,4)

* np.random.randint(1,100, 10)  
10 random numbers from 1 to 100 (exclusive)
* np.random.seed(101)  
from numpy.random import randint
* randint(2,10)

 ## Functions
* arr.reshape(5,5)
* arr.shape
* arr.dtype
* arr.max()
* arr.min()
* arr.mean()
* arr.argmax() #returns the index
* arr.argmin()

## Subsetting
* arr[1:5]  
index 1 to 5 (exclusive)  
slice of array. reference only  
dog = arr[1:5] – change in dog will reflect in arr  

* arr_copy = arr.copy()
* arr_2d[0][0] #double-bracket notation
* arr_2d[0,0]  #single-bracket
* arr_2d[1:3,1:6]
* arr[arr > 5]

## Operations
* arr + arr, arr-arr, arr*arr, arr/arr – element-wise operations
* arr**2
* np.sqrt(arr)
* np.exp(arr)
* np.max(arr)
* np.min(arr)
* np.sin(arr)
* np.log(arr)

 ## Errors
* 1/0  ZeroDivisionError
* arr/arr # 0 over 0 (nan)
* 1 / arr # 1 over 0 (inf)
