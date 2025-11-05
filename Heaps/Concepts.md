## Heaps
- Priority Queue is an abstract data type similar to queue or stack, each element has a priority attached to it and element wil high priority is served before an element with low priority.
- Heap is a data structure used to implement the priority queue (other ways to implement PQ are array and linked list that take O(1) time complexity either for insertion or deletion and other being O(N))
- Implementing PQ with heap take O(logN) for both insertion and deletion
- Heap is a complete Binary Tree and the value of each node must be no greater than (or no less than) the value of its child nodes
- Max Heap and Min Heap are the 2 types, max heap has the largest value as its root node and min heap has the smallest value as its root node
- Implementation of heap: https://leetcode.com/playground/XcTweQ9Q

## Convert Min Heap to Max Heap
```cpp
// O(n) complexity
void MaxHeapify(int arr[], int i, int N)
{
    int largest = i;
    int l = 2*i + 1;
    int r = 2*i + 2;
    
    if (l < N && arr[l] > arr[largest]) largest = l;
    if (r < N && arr[r] > arr[largest]) largest = r;
    
    if (largest != i) {
        swap(arr[largest], arr[i]);
        MaxHeapify(arr, largest, N);
    }      
}

// We begin with the last internal node and check its children
void convertMaxHeap(int arr[], int N)
{
    for (int i = (N-2)/2; i >= 0; i--) {
        MaxHeapify(arr, i, N);
    }
}
```

## Heapsort: TC - O(N * logN), SC - O(1)
```cpp
// Function to heapify a subtree rooted at index i
void MaxHeapify(int arr[], int N, int i) {
    int largest = i;        // Initialize largest as root
    int l = 2*i + 1;        // left child
    int r = 2*i + 2;        // right child

    // If left child is larger than root
    if (l < N && arr[l] > arr[largest])
        largest = l;

    // If right child is larger than largest so far
    if (r < N && arr[r] > arr[largest])
        largest = r;

    // If largest is not root
    if (largest != i) {
        swap(arr[i], arr[largest]);
        // Recursively heapify the affected subtree
        MaxHeapify(arr, N, largest);
    }
}

// Function to build a max heap
void BuildMaxHeap(int arr[], int N) {
    for (int i = (N-2)/2; i >= 0; i--) {
        MaxHeapify(arr, N, i);
    }
}

// HeapSort function
void HeapSort(int arr[], int N) {
    BuildMaxHeap(arr, N);

    // One by one extract elements from heap
    for (int i = N-1; i > 0; i--) {
        // Move current root to end
        swap(arr[0], arr[i]);
        // call max heapify on the reduced heap
        MaxHeapify(arr, i, 0);
    }
}
```
