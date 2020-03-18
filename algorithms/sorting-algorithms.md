---
title: "Sorting algorithms"
tags: ""
---
### Bubble sort

This is the simplest sorting algorithm.$\\$
Algorithm:

-   First input the array.
-   Next, consider two elements at a time and check if the first element is smaller than the second then swap otherwise move to the next pair.
-   As soon as the largest number is bubbled to the end, repeat the process by reducing the array size.

Code in C:

```C
void bubble sort(int arr[], int n)
{
    for(int i=0;i<n;i++)
    {
        for(int j=0;j<n-i-1;j++)
        {
            if(a[j]>a[j+1])
            {
                swap(a[j],a[j+1]);
            }
        }
    }
}
```

-   Time complexity and space complexity:
    -   Time complexity: 
        -   worst case is O(n$^2$)
        -   Best case is O(n$^2$) (for traditional bubble sort)
        -   Best case for optimal bubble sort is O(n)
    -   Space complexity:
        -   Total space complexity is O(n)


-   We can implement _bubble sort recursively_ because we pass address first index but recursively so it is calling function by reference.
    -   We do the same thing as iterative version but call the function after one iteration with array size being one less than the initial one.
    -   But the main problem is time and recursion is hell slow due the need for allocation of stack and assigning variables again.
    -   If you observe the function will be called around 'n' times and will depend on size of array.
    -   If you calculate the time complexity of recursion algorithms it comes to be O($n^2$) which is same in case of iterative case.
    -   The space complexity is going to hit you hard as _extra space_ would be _O(n)_.

* * *

### Insertion sort

This is similar to arranging your playing cards.

-   Inserting lower values at the beginning.$\\$
    Algorithm:
-   Input the array
    -   A marker is used to keep track of the sorted sequence.
    -   considering the first element in sorted sequence.
-   Now consider first element of the unsorted sequence, push the elements in sorted sequence to the right which are greater than the selected number and insert the number in the right spot.
    -   After this update the marker.
-   Repeat the above step until the unsorted part in empty. (check if marker has reached the end).

Code in C:

```C
void insertionSort(int arr[], int n)
{
    int key,j; // val selected to be inserted in the right place
    for(int i=1;i<n;i++) // this loop is for assigning
    {
        key=arr[i];
        j=i-1; // selecting the last in sorted seq
        while(j>=0 && arr[j]>key) // traversing sorting seq and check
        {
            arr[j+1]=arr[j]; //push this 'j' element to 'j+1'
            j=j-1;
        }
        arr[j+1]=key;
    }
}
```

-   Time complexity and space complexity:
    -   Time complexity:
        -   Worst-case time complexity is O(n$^2$)
        -   Best-case time complexity is O(n)
    -   Space complexity:
        -   Space complexity is known as O(n)

* * *

### Selection sort

```C
int selectionSort(int arr[],int n)
{
    int min_index=0,temp; //for the minimum val min_index
    for(int i=0;i<n-1;i++) // iteration
    {
        min_index=i;
        for(int j=i+1;j<n;j++)
        {
             if(arr[j]<arr[min_index])
             {
                 min_index=j;
             }
        }
        if(arr[i]>arr[min_index])
        {
            temp=arr[i];
            arr[i]=arr[min_index];
            arr[min_index]=temp;
        }
    }
}
```

-   Time complexity and space complexity:
    -   Time complexity:
        -   The worst-case time complexity is O(n$^2$)
        -   The best-case time complexity is also O(n$^2$)
    -   Space complexity:
        -   It is O(n) which only depends on the main array, no auxillary array is used.

* * *

### Merge sort

It is a divide and conquer algorithm
Algorithm:

-   First input the array
-   Now find the mid point of the array by $\\frac{l+r}{2}$.
-   Now divide the array into two parts left and right part.
-   Do this recursively till you divide the array into size of 1, then start merging the elements from left side first(because of recursion)
-   Before merging compare the elements and then merge them into the array and continue so on till you get the sorted form of the array.

```C
void merge(int arr[], int low, int mid, int high)
{
    int n1=mid-low+1, n2=high-mid;
    int left[n1], right[n2]; // temp arrays
    
    for(int i=0;i<n1;i++)
    {
        left[i]=arr[low+i];
    }
    for(int j=0;j<n2;j++)
    {
        right[j]=arr[mid+1+j];
    }
    
    int a=0,b=0,k=low;
    while(a<n1 && b<n2)
    {
        if(left[a]<=right[b])
        {
            arr[low]=left[a];
            a++;
        }
        else
        {
            arr[low]=right[b];
            b++;
        }
        low++;
    }
    
    while(a<n1) // if a>b, so copy left
    {
        arr[low]=left[a];
        a++;
        low++;
    }
    
    while(b<n2) // b>a, so copy right
    {
        arr[low]=right[b];
        b++;
        low++;
    }
    
}

void mergesort(int arr[], int low, int high)
{
    if(low<high)
    {
        int mid=(low+high)/2;
        // printf("up\n");
        mergesort(arr,low,mid);
        // printf("mid\n");
        mergesort(arr,mid+1,high);
        // printf("down\n");
        merge(arr,low,mid,high);
    }
}
```

-   Time complexity and space complexity:
    -   Time complexity:
        -   Best, average and worst-case time complexity is O(nlog(n))
    -   Space complexity:
        -   As this a recursive type of algorithm the space occupied by is alot and will be not feasible as alot of memory will be utilized if the input array will be big
        -   Space complexity $\\alpha$ n

* * *

### Quick sort

It is a divide and conquer algorithm

-   So basic idea is we pick a pivot and sort the array around this pivot.
-   The pivot can be picked based on implementation, can be 1st, last, random or middle element.
-   The main role is played by the partition function, it does:
    -   Pick pivot
    -   Group smaller values before pivot and larger after pivot
    -   Make sure pivot is in the right place of the array (as lower on left and larger on right so logically pivot is in its right place)

Algorithm:

-   Input the array
-   Consider a pivot, and force lower elements before pivot and larger elements after pivot which forces pivot to be in right place.
-   To group those elements in partition function, start from left with two indicies:
    -   if element > pivot then don't do anything
    -   if element &lt; pivot then swap current index value with the element.

```C
int partition(int arr[], int left, int right)
{
     int pivot=arr[right],temp;
     int i=left-1,j=left;
     while(j<=right-1)
     {
         if(arr[j]<pivot)
         {
             ++i;
             temp=arr[j];
             arr[j]=arr[i];
             arr[i]=temp;
         }
         if(arr[j]==pivot)
            break;
         j++;
     }
     temp=arr[i+1];
     arr[i+1]=pivot;
     arr[j]=temp;
    //  for(int i=0;i<6;i++)
    // {
    //     printf("%d  ",arr[i]);
    // }
     return i+1;
}

void quicksort(int arr[],int left, int right)
{
    if(left<right)
    {
        int pindex=partition(arr,left,right);
        // printf("\n%d",pindex);
        quicksort(arr,left,pindex-1);
        quicksort(arr,pindex+1,right);
    }
}
```

-   Time complexity and space complexity:
    -   Time complexity:
        -   The best and average case is O(nlog(n))
        -   The worst-case is O(n$^2$) which is when array is sorted in reverse order.
    -   Space complexity:
        -   space complexity $\\alpha$ n+log(n) ( log(n) is for recursive calls) so finally its O(n)

* * *

### Heap sort

In this sorting algorithm we consider a max heap or a min heap (for descending order).

-   Main role is played by Heapify.

Algorithm:

-   Consider an array.
-   MaxHeapify the array
-   Then swap the root element (which contains the maximum value) with the last element 
-   Reduce the size of the array and repeat from step 2 till array is sorted.

Code in C:

```C
void heapify(int arr[], int x, int n)
{
    int left=2*x+1, right=2*x+2, max_i=x;
    
    if(left<n && arr[left]>arr[max_i])
    {
        max_i=left;        
    }
    
    if(right<n && arr[right]>arr[max_i])
    {
        max_i=right;
    }
    
    if(max_i!=x)
    {
        arr[x]=arr[x]+arr[max_i];
        arr[max_i]=arr[x]-arr[max_i];
        arr[x]=arr[x]-arr[max_i];
        heapify(arr,max_i,n);
    }
}

void maxHeapify(int arr[],int n)
{
    for(int i=n/2 - 1;i>=0;i--)
    {
        heapify(arr,i,n);
    }
}

void heapsort(int arr[], int n)
{
    for(int i=n;i>1;i--)
    {
        maxHeapify(arr,i);
        int temp;
        temp=arr[0];
        arr[0]=arr[i-1];
        arr[i-1]=temp;
    }
}
```

-   Time complexity and space complexity:
    -   Time complexity
        -   Best case is when 
        -   Worst case is when 
    -   Space complexity

* * *

### Hash sort

In this we use hashing technique, basically consider an auxillary array and sort the array but here we do use extra space.
Algorithm:

-   Consider the array
-   Traverse the main array, the value in the array consider it to be an index in the auxillary array (of size $10^7$) and at that index make the value one.
-   Finally to get the sorted sequence, traverse the auxillary array from start and wherever you have value one, store that index in another array.

Code in C:

```C
int hashSort(int arr[], int n)
{
    int aux[10000000]={0},narr[n];
    for(int i=0;i<n;i++)
    {
        aux[arr[i]]=1;
    }
    int j=0;
    for(int i=0;i<10000000;i++)
    {
        if(aux[i]==1 && j<n)
        {
            narr[j]=i;
            j++;
        }
    }
}
```

-   Time Complexity and space complexity:
    -   Time complexity:
        -   Worst-case time complexity is O($10^7$), this uses an auxillary of max. size $10^7$.
        -   The best-case complexity is O($10^7$) if n&lt;$10^7$
    -   Space complexity:
        -   The space complexity is O($10^7$) when n&lt;$10^7$
-   Main limitation:
    -   The _size of each integer can't be greater than $10^7$_ as these numbers will be used as indices in auxillary array and max. size of array in a normal computer is $10^7$.
