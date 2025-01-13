```haskell
%% concatenate lists %%
[1, 2, 3] ++ [4, 5, 6]
1:[2, 3, 4]
1:2:3:[]
```
When using the `++` opearator haskell has to step through all entries in the left list to append to the end. But using the `cons (:)`  on a single element is instantaneus.
Comparing strings looks at the first one and if they are equal, the next one and so on.

#### Operations
```
[1, 2, 3] !! 0 :[2, 3] 

[3, 2, 1] > [2, 1, 0]
True

[3, 0, 0] > [2, 100, 100]
True

[2, 3, 4] < [2, 1, 0]
False
```

#### Functions
```
head [1,2,3]
1

tail [1,2,3]
[2,3]

last [1,2,3]
3

init [1,2,3]
[1,2]

length [1,2,3,4,5]
5

null []
True

null [1,2,3]
False

reverse [1,2,3]
[3,2,1]

take 3 [1,2,3,4,5]
[1,2,3]

take 0 [1,2,3]
[]

take 10 [1,2]
[1,2]

drop 3 [1,2,3,4,5,6]
[4,5,6]
```