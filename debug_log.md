# Debug Log

**Explain how you used the VSCode debugger tools to uncover the bugs in Exercise 7. Be specific. What breakpoints did you set? Where did you step to? What made you realize the error?**

_Example: I set a breakpoint on line 5 and stepped until line 12. There, I discovered that the `x` variable had a value of `-3`, whereas it should have had a value of `7`. That made me realize that we should be adding the two numbers `x` and `y`, instead of subtracting._

## Exercise 1: Step Through Code
I initiated the debugging steps in Exercise 1 by setting a breakpoint on line 5 within the `calculate_average` function. This breakpoint served as a pause point, allowing me to look at the program at that particular line. Using the `Step Over` button, I navigated through the code line by line, closely observing the changes in variables.

The Variables tab displayed all variables at the breakpoint on line 5, allowing me to track the values of variables like `total` and `num` as I stepped through the function.

## Exercise 2: Step Over, Step Into, Step Out

For exercise 2, I set a breakpoint on line 13 at the beginning of the `calculate_average` function. This served as the starting point. I ran the debugger and used the `Step Into` button to delve into the `calculate_sum` function.

While stepping through the `calculate_sum` function, I used both the `Step Over` and `Step Into` buttons. The distinction between these controls allowed me to navigate through the code, by either advancing to the next line or diving into helper functions.

The `Step Out` functionality became valuable when I wanted to skip the remainder of the `calculate_sum` function and return to the calling function (`calculate_average`). 

## Exercise 3

For Exercise 3, I set a breakpoint on line 16 at the beginning of the `find_most_common_word` function. This breakpoint allowed me to pause the code's execution and look at the state of the variables at that specific line.

While stepping through the code, I created watch expressions to gain real-time insights into the values of specific expressions. I added a watch expression for `1 + 2`, displaying both the expression and its result in the Variables tab. Additionally, I added watch expressions for `len(list_of_words)` and `word_to_count['fish']` to look at the changes in the number of words and the count of the word 'fish' as the program executed.

The watch expressions provided important information about the behavior of these expressions at different points in the code. By setting watch expressions for variables like 'word', 'count', 'most_common_word', and 'highest_count' within the loop, I can look at their values as the loop iterates through the words. This can be helpful for understanding how the algorithm works and identifying any unexpected behavior.

## Exercise 4
For Exercise 4, I set a breakpoint at the beginning of the `fibonacci()` function on line 6 and ran the debugger, using the `Continue` button to step through the code. By looking at the call stack during the recursive calls, I could see how it grew longer with each iteration and then shortened as the recursive calls reached the base case. This visualization provided valuable insights into the sequence of function calls and their relationships. The debugger allowed me to click into each stack, looking at the variables within specific function calls, heling my understanding of the recursive process in the `fibonacci()` function.

## Exercise 5

For Exercise 5, I didn't set any breakpoints. I ran the debugger without setting a breakpoint, allowing it to stop when encountering an uncaught exception. It stopped right away and resulted in a "List index out of range" error. By examining the `Variables` list in the debug tab, I identified the and noticed that the error was due to the comparison `list_of_nums[i] > list_of_nums[i+1]` in the inner loop, where `i+1` went out of bounds for the last element. I fixed this by adjusting the loop range to `range(len(list_of_nums)-1)` to prevent accessing an index beyond the list's length. After the fix, running the code resulted in the sorted list being printed to the console.

Output: `[2, 3, 4, 6, 7, 12]`

## Exercise 6

For Exercise 6, I set a breakpoint on line 22 at the beginning of the `compare_to` method. Using the Step Over button, I stepped through the next few lines, looking at the "Variables" list to inspect the variables for Amy and Mike. I saw their names and ages nested inside the variables list.

## Exercise 7

I ran the code and the actual output was: `fantastic` and the expected output is supposed to be `fantastic, I guess programming is fantastic.` 

**Debugging Steps:**
- I set a breakpoint at the beginning of the `replace_substring()` function on line 3.
- I ran the debugger and stepped through the code using the `Step Over` button.
- While stepping through the recursive calls, I looked at the "Variables" list to track the values of relevant variables.
- I noticed in the `replace_substring` function, the parameter `start_str` was intended to represent the substring we want to replace in the sentence. But, as the function was recursively calling itself, the intention was to shorten the sentence by removing the matched portion. The problem was that instead of modifying the sentence, the function was unintentionally modifying the start_str.
- When the code reached lines 10 and 13, the original intention was to create the `remainder_of_sentence` by removing the matched portion (`start_str`) from the sentence. However, due to the recursive calls, the variable `start_str` didn't represent the original starting substring but more of a modified version of it.
- By changing the parameter name from `start_str` to `sentence` on lines 10 and 13, we made the code match what it was supposed to do. This little change made sure that we are correctly working with the original sentence and shortening it as we recursively replace the substring. The correction prevents unintended modifications to the `start_str` variable, resolving the bug in the code.
- After making this fix, I reran the code, and the output was: `'fantastic, I guess programming is fantastic.'`.