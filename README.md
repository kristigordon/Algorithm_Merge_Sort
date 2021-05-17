# Algorithm_Merge_Sort

![image](https://user-images.githubusercontent.com/66803124/118539316-239a5080-b704-11eb-8b31-3e413955bde6.png)

As you can see from the graphic above, Merge Sort works by finding the middle-most index in the array and cutting it 
into two halves until each array is only 1 number in length, then taking each of those halves and sorting them. 

![image](https://user-images.githubusercontent.com/66803124/118541515-a15f5b80-b706-11eb-98db-e599baba64d4.png)

At the end, the halved arrays will merge back together, sort, merge, sort until they finally form one fully sorted array. 

![image](https://user-images.githubusercontent.com/66803124/118541803-fbf8b780-b706-11eb-9f70-cbc61beec1a2.png)

The time complexity here will be a Log N since each time we combine two blocks, we need to look at up to (n) items to determine their relative location.

In other words, we are using an outer loop log N times as our sorted array doubles in size on each iteration.
Then our inner loop is looking at up to (n) items to determine their relative order in the increasing size blocks.

# Psuedo Code:
```
If array size 1, return 

Else, split left and right 

Then, merge sorted sub arrays by: 

Set L and R Pointers 

While L and R pointers have room, 

	Add lesser value and advance 

Dump items from unfinished array 
```

# Coding Question

```
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

The number of elements initialized in nums1 and nums2 are m and n respectively. You may assume that nums1 has a size equal to m + n such that it has enough space to hold additional elements from nums2.

 

Example 1:

Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Example 2:

Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]
 

Constraints:

nums1.length == m + n
nums2.length == n
0 <= m, n <= 200
1 <= m + n <= 200
-109 <= nums1[i], nums2[i] <= 109
```

# Solution 
```
def merge_sort(unsorted_array):
    if len(unsorted_array) > 1:
        mid = len(unsorted_array) // 2  # Finding the mid of the array
        left = unsorted_array[:mid]  # Dividing the array elements
        right = unsorted_array[mid:]  # into 2 halves

        merge_sort(left)
        merge_sort(right)

        i = j = k = 0

        #  data to temp arrays L[] and R[]
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                unsorted_array[k] = left[i]
                i += 1
            else:
                unsorted_array[k] = right[j]
                j += 1
            k += 1

        # Checking if any element was left
        while i < len(left):
            unsorted_array[k] = left[i]
            i += 1
            k += 1

        while j < len(right):
            unsorted_array[k] = right[j]
            j += 1
            k += 1


# Code to print the list
def print_list(array1):
    for i in range(len(array1)):
        print(array1[i], end=" ")
    print()


# driver code to test the above code
if __name__ == '__main__':
    array = [12, 11, 13, 5, 6, 7]
    print("Given array is", end="\n")
    print_list(array)
    merge_sort(array)
    print("Sorted array is: ", end="\n")
    print_list(array)
```
