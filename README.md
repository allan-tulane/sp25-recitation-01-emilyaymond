[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/tqM-lrvp)
# CMPS 2200  Recitation 01

**Name (Team Member 1):** __Emily Aymond________  
**Name (Team Member 2):** __Camden Yale_________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**

  In linear search, the worst case input value of key would be the last element in the list because it would have to go through all other elements in the list before it found the key or if the value is not an element in the list at all. In binary search, the worst case input value of key would be if the value were not in the list because it will keep splitting the list into halves until it has exhausted all possibilites but still has not found the key.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**

  In linear_search, the best case input value of key would be if it were the very first element in the list. In binary_search, the best case input value of key would be if the key were at the very middle of the list, meaning there would only have to be one comparison.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**

|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.003 |    0.004 |
|      100.000 |    0.005 |    0.002 |
|     1000.000 |    0.062 |    0.003 |
|    10000.000 |    0.482 |    0.005 |
|   100000.000 |    6.047 |    0.010 |
|  1000000.000 |   71.021 |    0.015 |
| 10000000.000 |  766.364 |    0.018 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here**

Yes, these run times do match the empirical results. It is possible to observe this because in the last two input sizes, n, in linear search, 10^6 takes 71 ms whereas 10^7 takes 766 ms, which is a 10x increase. In binary search, you can see that in the worst case scenario, the run time increases but not by much, which is consistent with logarithmic growth. This shows us that binary search is the more efficient option.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**
     
    The worst-case complexity using linear search is O(nk). This happens when the key is found in the very last position of the list or the value is not in the list at all.
    
  + For binary search? **TODO: your answer goes here**
    The worst-case complexity is $\Theta(n^2)$ + O(k log n). This happens when the value is not found in the list, so the list keeps getting split in half, leading to a logarithmic growth.
    
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: your answer goes here**
     
    It is more efficent when k is small to use linear search, but when the value of k is large, it is more efficent to use binary search.
