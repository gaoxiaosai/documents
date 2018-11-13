## 第1章 算法简介

#### 1.1 引言

**算法:** 算法是一组完成任务的指令.

#### 1.2 二分查找

**特点:** 每次排除列表中的一半元素.

**前提条件:** 列表有序.

**运行时间:** 对数时间.

**代码实现:**

```python
#二分查找,成功返回下标,失败返回None
def binary_search(lst, item):
    low = 0
    high = len(lst) - 1
    
    while low <= high:
        mid = (low + high) // 2
        guess = lst[mid]
        if guess == item:
            return mid
        if guess > item:
            high = mid - 1
        else:
            low = mid + 1
     return None
```

#### 1.3 大O表示法

**大O表示法:** 表示执行的操作数.

#### 1.4 小结

- 二分查找的速度比简单查找快的多.
- O(log n) 比 O(n) 快, 需要搜索的元素越多,前者比后者就快的越多
- 算法运行时间并不以秒为单位
- 算法运行时间是从其增速的角度度量的
- 算法运行时间用大O表示法表示

## 第 2 章 选择排序

 #### 2.1数组和链表

- **数组**
  - 元素地址是连续的
- **链表**
  - 元素地址是不连续的

#### 2.2 数组与链表基本操作运行时间比较

|      | 数组 | 链表 |
| :--: | :--: | ---- |
| 读取 | O(1) | O(n) |
| 插入 | O(n) | O(1) |
| 删除 | O(n) | O(1) |

**访问**

- 随机访问
- 顺序访问

#### 2.3 选择排序

**代码实现**

```python
def find_smallest(arr):
    smallest = arr[0]
    smallest_index = 0
    for i in range(1, len(arr)):
        if arr[i] < smallest:
            smallest = arr[i]
            smallest_index = i
    return smallest_index


def selection_sort(arr):
    newArr = []
    for i in range(len(arr)):
        smallest = find_smallest(arr)
        newArr.append(arr.pop(smallest))
    return newArr


print(selection_sort([5,3,6,2,10]))
```

#### 2.4 小结

- 计算机内存犹如一大堆抽屉
- 需要存储多个元素时,可使用数组或链表
- 数组的元素都在一起
- 链表的元素是分开的,其中每个元素都存储了下一个元素的地址
- 数组的读取速度很快
- 链表的插入和删除速度很快
- 在同一数组中,所有元素的类型都必须相同(都为int, double等)
## 3 递归

#### 3.1小结

- **递归指的是调用自己的函数。**
- **每个递归函数都有两个条件：基线条件和递归条件。**
- **栈有两种操作：压入和弹出。**
- **所有函数调用都进入调用栈。**
- **调用栈可能很长，这将占用大量的内存。**

---

## 第 4 章 快速排序

#### 4.1 分而治之

- **找出简单的基线条件；**
- **确定如何缩小问题的规模，使其符合基线条件。**

#### 4.2 快速排序

**步骤：**

- 选择基准值。
- 将数组分成两个子数组：小于基准值的元素和大于基准值的元素。
- 对这两个子数组进行快速排序。

**代码**

```python
def quick_sort(array):
    if len(array) < 2:
        return array
    else:
        pivot = array[0]
        less = [i for i in array[1:] if i <= pivot]
        greater = [i for i in array[1:] if i > pivot]
        return quick_sort(less) + [pivot] + quick_sort(greater)
 
print(quick_sort([10, 5, 2, 3]))
```

#### 4.4 小结

- **D&C将问题逐步分解。使用D&C处理列表时，基线条件很可能是空数组或只包含一个元素的数组。**
- **实现快速排序时，请随机的选择用作基准值的元素。快速排序的平均运行时间为O(n log n)。**
- **大O表示法中的常量有时候事关重大，这就是快速排序比合并排序快的原因所在。**
- **比较简单查找和二分查找时，常量几乎无关紧要，因为列表很长时，O(log n) 的速度比O(n)快得多。**

---

## 第 5 章 散列表

