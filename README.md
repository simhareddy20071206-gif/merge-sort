# merge-sort
Alright — let’s go through **Merge Sort** step-by-step 👇

---

## 🧩 **What is Merge Sort?**

**Merge Sort** is a **divide and conquer** sorting algorithm.
It splits the array into halves, sorts each half **recursively**, and then **merges** them back in sorted order.

---

## ⚙️ **Algorithm Steps**

1. **Divide:** Split the array into two halves.
2. **Conquer:** Recursively sort the two halves.
3. **Combine:** Merge the two sorted halves into one sorted array.

---

## 💻 **C++ Code Example**

```cpp
#include <iostream>
#include <vector>
using namespace std;

void merge(vector<int>& arr, int left, int mid, int right) {
    vector<int> temp;
    int i = left, j = mid + 1;

    // Merge both halves
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j])
            temp.push_back(arr[i++]);
        else
            temp.push_back(arr[j++]);
    }

    // Add remaining elements
    while (i <= mid) temp.push_back(arr[i++]);
    while (j <= right) temp.push_back(arr[j++]);

    // Copy back to original array
    for (int k = left; k <= right; ++k)
        arr[k] = temp[k - left];
}

void mergeSort(vector<int>& arr, int left, int right) {
    if (left >= right) return;

    int mid = left + (right - left) / 2;
    mergeSort(arr, left, mid);
    mergeSort(arr, mid + 1, right);
    merge(arr, left, mid, right);
}

int main() {
    vector<int> arr = {38, 27, 43, 3, 9, 82, 10};
    mergeSort(arr, 0, arr.size() - 1);

    cout << "Sorted array: ";
    for (int x : arr) cout << x << " ";
    cout << endl;
}
```

---

## 🧠 **Key Points**

| Concept              | Explanation                                                                |
| -------------------- | -------------------------------------------------------------------------- |
| **Time Complexity**  | O(n log n) — because array is divided log n times, and merging takes O(n). |
| **Space Complexity** | O(n) — needs temporary arrays for merging.                                 |
| **Stable Sort**      | ✅ Yes                                                                      |
| **In-place Sort**    | ❌ No (uses extra memory)                                                   |

---

## 🧩 **Pattern (for DSA practice)**

The **pattern** of merge sort is:

> Recursively divide → process left and right → merge results

It’s often used in:

* Sorting algorithms
* Counting inversions
* Merging k sorted lists
* Problems where combining sorted parts helps (e.g., divide and conquer type questions)

---

Would you like me to show the **recursive tree / dry run** of merge sort on an example like `{5, 2, 4, 6, 1, 3}` to visualize it?
