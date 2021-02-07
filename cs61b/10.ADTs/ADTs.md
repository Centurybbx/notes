## ADTs

## Intro to ADTs

​	ADT就是Abstract Data Type，通常来说只关注它的operations，而不关注它的implementations(非常类似于Java中的Interface的定义)。

比如在Java中，有很多ADT：

- Stacks：FILO的DS
  - `push(int x)`: puts x on the top of the stack
  - `int pop()`: takes the element on the top of the stack
- **Lists**：按序排列元素的DS
  - `add(int i)`: adds an element
  - `int get(int i)`: gets element at index i
- **Sets**：没有重复元素的DS
  - `add(int i)`: adds an element
  - `contains(int i)`: returns a boolean for whether or not the set contains the value
- **Maps**：含有键值对的DS
  - `put(K key, V value)`: puts a key value pair into the map
  - `V get(K key)`: gets the value corresponding to the key

> 上述中加粗的ADTs他们同属于一个更大ADT`Collections`。

​	ADT很有用，在之后的过程中会使用的越来越多。