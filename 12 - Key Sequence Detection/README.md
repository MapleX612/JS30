# 12 - Key Sequence Detection

**[Live Demo](https://maplex612.github.io/JS30/12%20-%20Key%20Sequence%20Detection/index-MAPLE.html)**  

## 1. `Array.splice()`

With this challenge, I got more familiar with the `splice()` method. Here are some recaps on it.  

- It **changes** the original array and returns an array of deleted items (empty array if no items are deleted).  
On the other hand, `map()`, `filter()` and `slice()` will not alter the original array.  

- It has 3 parameters: 1st param is required while the other two are optional.  
    ```
    deletedItems = arr.splice(start, deleteCount, item(s) to be added);
    ```
  - 1st param `start`  

    If `start > arr.length`, no item will be deleted. If 3rd param are assigned, `splice()` will add items to the array.  

    If `start < 0`, then the array changes from the index `arr.length + start`. If `arr.length + start` is negative, then the array will change from index 0.
    ```
    const arr = ['a','b','c','d'];

    arr.splice(6, 0, 'e','f'); //arr is now ['a','b','c','d','e','f']

    arr.splice(-2, 1); //change from index 6-2 (the 2nd last item). arr is now ['a','b','c','d','f']  

    arr.splice(-6, 2); //arr.length + start < 0, thus change from index 0. arr is now ['c','d','f']
    ```  

  - 2nd param `deleteCount`  
  
    If `deleteCount` is ommited, or `deleteCount` >= the number of left items starting at `start`, then **all** items from `start` to the end (inclusive) are deleted.  

    If `deleteCount <= 0`, no items will be deleted.