
 # Independent Study Project - Bubble Sort


 # Introduction
 Sorting algorithms plays a crucial role in computer science, thus allowing us to organize and retrieve data efficiently. Among the varied sorting algorithms, bubble sort stands out for its simplicity and intuitive nature. In this article, we will take a look into bubble sort, explore its principles, its implementation, performance characteristics, and real-world applications.


 ## Learning Objectives

  By the end of this lesson, you should be familiar with how to:

-  Describe what Bubble Sort is,
-  How to perform Bubble Sort on lists and arrays
-  Bubble Sort Syntax and JS code
-  Bubble Sort Strengths and Constraints
-  Time and Space complexity
-  Edge Cases


## What is Bubble Sort?

Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping  adjacent elements 'IF' they are in the wrong order. If the algorithm is in the correct order, then bubble sort fails. This sorting technique compares two adjacent elements in an array and swaps them if they are in the wrong order. It keeps repeating this process until the array is sorted. 


![diagram](https://miro.medium.com/v2/resize:fit:802/format:webp/0*l6PC-ARdWVQL0a-q.gif)

## How to perform Bubble Sort on an list & Array?

The bubble sort algorithm follows a simple step-by-step process. Starting from the beginning of the list, it compares adjacent elements and swaps them 'if' they are in the wrong order. This process continues iteratively until the entire list is sorted. During each iteration, the largest unsorted element gradually “bubbles” to the end of the list.


## Let's illustrate with an unsorted list: [7, 2, 9, 5, 1]


- In the first iteration, 7 and 2 are compared. Since 7 is greater than 2, they are swapped.
  - Iteration 1: [7, 2, 9, 5, 1] ----> [2, 7, 9, 5, 1]
- The next comparison is between 7 and 9. As they are in the correct order, no swapping occurs.
  -  Iteration 2: [2, 7, 9, 5, 1] ----> [2, 7, 9, 5, 1]
- The next comparison is between 9 and 5. Since 9 is greater than 5, they are swapped.
  - Iteration 3: [2, 7, 9, 5, 1] ----> [2, 7, 5, 9, 1]
- The next iteration comparison is between 7 and 5. Since 7 is greater than 5, they are swapped.
  - Iteration 4: [2, 7, 5, 9, 1] ----> [2, 5, 7, 9, 1]
-  By now you get the gist of it- The process continues, comparing and swapping adjacent elements until the largest element, 9, reaches its correct position at the end of the list.
 - After the last iterations, the list becomes sorted: [1, 2, 5, 7, 9].


## Picturally: Let's illustrate with the array [6, 3, 0, 5]


 
![diagram](https://media.geeksforgeeks.org/wp-content/uploads/20230526103842/1.webp)



## Let's see how this works in code - but first syntax:

### Step 1: Create a boolean variable
Let's track whether any swap has been made in the current iteration of the array. To do this, create a boolean variable named "swapped" for this purpose but do not assign it yet.
    let swapped; 

### Step 2: Create a "do-while" loop to iterate until the array is sorted
Let's use the "do-while" loop to iterate through the array until it is sorted. This loop executes at least once, even if the array is already sorted — which is why it’s best used for this. We will also use the "swapped" variable to check whether any swap has been made in the current iteration.

       do {
         // code to be executed
       } while (swapped);

### Step 3: Set the boolean variable to false at the start of each iteration
At the start of each iteration, we have to set the "swapped" variable to false. This is because we have not made any swap yet in the current iteration.

       do {
         swapped = false;
         // code to be executed
        } while (swapped);

### Step 4: Use a "for" loop to compare adjacent elements
Within the "do-while" loop, we use a "for" loop to compare each array element with the element next to it. 
- If the current element is greater than the next element, they are swapped. If true, we  declare a temporary variable  with the keyword "temp" and assign the value of arr[i] to it. This is done to temporarily store the value of the current element before the swap and ensures a correct swap.
- we then assigns the value of the next element (arr[i + 1]) to the current element (arr[i]), effectively swapping their positions.
- By doing this, we have assigned  the temporary value (temp) to the next element, completing the swap. 
- "swapped" variable is set to true to indicate that a swap occurred during this iteration.
- The 'do-while' loop continues to execute as long as swapped is true. If a swap occurred in the previous iteration, the loop continues. If no swap occurred, the loop exits.

        for (let i = 0; i < arr.length - 1; i++) {
           if (arr[i] > arr[i + 1]) {
             let temp = arr[i];
             arr[i] = arr[i + 1];
             arr[i + 1] = temp;
               swapped = true;
            }
        }
    } while (swapped);  


### Step 5: Repeat the loop until no more swaps are made
If no swap is made in the current iteration, the "swapped" variable remains false. This means the array is sorted, and we can exit the loop.
If elements have been swapped, the "swapped" variable is set to true, and the loop continues to iterate until the array is sorted.

     const bubbleSort = (arr) => {
           let swapped;
         do {
             swapped = false;
            for (let i = 0; i < arr.length - 1; i++) {
                if (arr[i] > arr[i + 1]) {
                  let temp = arr[i];
                 arr[i] = arr[i + 1];
                 arr[i + 1] = temp;
                  swapped = true;
               }
            }    
        } while (swapped);
            return arr;
     }; 


  Now let's see how it works in JS code:

            const bubbleSort = (arr) => {
                let swapped;
                do {
                    swapped = false;
                    for (let i = 0; i < arr.length - 1; i++) {
                      if (arr[i] > arr[i + 1]) {
                         [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]];
                         swapped = true;
                        }
                    }
                } while (swapped);
                  return arr;
            };

        let myArray = [45, 19, 3, 7, 100];
       console.log(bubbleSort(myArray)); // returns [3, 7, 19, 45, 100]


## Big O Evaluation

### Bubble Sort Strengths
A significant strength of bubble sort is in its simplicity. It is quite easy to understand, implement, and debug, thereby making it a great choice for small-scale sorting tasks. 
### Bubble Sort Constraints
From our illustration above you may have noticed that bubble sort considers one element at a time. As such, this is time consuming and inefficient. Due to this inefficiency, bubble sort is constrained on how much it is used in coding and production.  It has huge limitations performing on large data sets. The algorithm's time complexity makes it inefficient for sorting extensive lists, as it requires extensive comparisons and swaps. 

### Use Cases
It is best suited for small datasets or situations where simplicity and ease of implementation are prioritized over performance.


### Time and Space Complexity

Bubble sort has an average-case and worst-case time complexity of O(n²), making it less efficient compared to other sorting algorithms like quicksort or mergeSort. In the best-case, when the list is already sorted, bubble sort achieves a time complexity of O(n). Regarding space complexity, bubble sort requires only a constant amount of additional memory, resulting in O(1) space complexity.

### Edge Cases

Although bubble sort may not be the most efficient algorithm as-is, it can be optimized in certain ways. One optimization is early termination, where the algorithm halts if no swaps are made during an iteration, indicating that the list is already sorted. Additionally, variations of bubble sort, such as bidirectional bubble sort or recursive bubble sort, offer slight improvements in performance or functionality.Bubble Sort is best used when the data set is few, for large data set, bubble sort 


### Citations

<a href= "https://www.geeksforgeeks.org/bubble-sort" > Geek for geeks- Bubble Sort</a> 

<a href="https://www.freecodecamp.org/news/how-to-implement-bubble-sort-algorithm-with-javascript/">FreeCodeCamp - How To Implement Bubble Sort</a> 

 <a href="https://medium.com/@prashantblogs/understanding-bubble-sort-a-simple-yet-powerful-sorting-algorithm-c4803a6bb4ed">Understanding Bubble Sort</a> 

<a href="https://flexiple.com/javascript/bubble-sort-javascript">Bubble Sort in Javascript</a> 




