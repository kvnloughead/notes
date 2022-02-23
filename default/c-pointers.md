---
Title: c-pointers
Category: default
Author: Kevin Loughead
Date: 2022-02-22
Tags:
---

Working with pointers and references is tricky. And array slices. Example (with my less than great understanding in comments)

```c++
// This function returns a pointer (*) of type int.
// Also note the second argument `const int *arr`. It's a constant integer
// pointer to the first element in the arr that gets past as an argument.
int *binary_search(int value, const int *arr, size_t length) {
  if (length == 0) return NULL;
  if (length == 1) {
    // To return an pointer with type int that points to the correct array
    // element, you need to take the address of the array element with
    // &arr[index] and then cast that to an int pointer.
    return value == arr[0] ? (int *) &arr[0] : NULL;
  }
  unsigned int mid = length / 2;
  if (value == arr[mid]) {
    return (int *) &arr[mid];
  } else if (value > arr[mid]) {
    // You can't really slice an array in C, but we can pretend to do so
    // by passing a pointer to a different array element. In this example,
    // instead of working with arr[0..] we will be working with arr[mid+1..].
    return binary_search(value, (int *) &arr[mid + 1], length / 2);
  } else {
    // In this example we are working with arr[0..length/2].
    return binary_search(value, (int *) &arr[0], length / 2);
  }
}


```
