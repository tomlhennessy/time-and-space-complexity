# Timing Benchmarks

* Measuring Code Efficiency
    • Run a function and measure how long it takes to complete
    • Use results to benchmark performance with various inputs

* Computer Safety
    • Running experiments in JavaScript is safe
    • You can't damage your computer by playing with code in Node.js

* Stopping Long-Running Code
    • Ctrl + C: Halts code execution if it runs too long
    • Useful for stopping infinite loops or very large computations

* Memory Crashes
    • Modern computers isolate processes, preventing crashes from code
    • Example: Adding 1 trillion integers to an array results in a memory error without harming the computer

* Modifying the Filesystem
    • Be cautious: Modifying or deleting important files can cause damage
    • Always understand code befroe running it, especially from untrusted sources

* Timing Your Code
    1. __`console.time()`__ Method
        • Measures how long an operation takes

        • Usage:
        ```js
        console.time("Timer");
        // Your code here
        console.timeEnd("Timer");
        ```

        • Example:
        ```js
        console.time("addNums")
        addNums(1000000);
        console.timeEnd("addNums")
        ```

    2. __`Date.now()`__ Method
        • Provides a timestamp in milliseconds since the Unix Epoch
        • Calculate runtime by storing start and end times

        • Usage:
        ```js
        let startTime = Date.now();
        // Your code here
        let endTime = Date.now();
        console.log(`Runtime: ${endTime - startTime}ms`);
        ```

        • Example:
        ```js
        startTime = Date.now();
        addNums(1000000);
        endTime = Date.now();
        console.log(`Runtime: ${endTime - startTime}ms`);
        ```

* Visualising Performance

    1. Google Sheets
    • Collect timing data by incrementing inputs
    • Example Code:
    ```js
    let increment = 1000000;
    for (let n = increment; n <= 10 * increment; n += increment) {
        startTime = Date.now();
        addNums(n);
        endTime = Date.now();
        console.log(`${endTime - startTime}`);
    }
    ```
    • Copy results into Google Sheets and use the Chart feature to visualise

* Summary
    • Use `console.time()` and `Date.now()` to measure and compare code performance
    • Visualise data using Google Sheets for better insights



# Intro to Big-O

* What is Big-0?
    Big-O notation is a way to describe the efficiency of algorithms, focusing on their growth rates as the input size increases. Instead of measuring exact runtimes, Big-O allows us to understand how an algorithm's performance scales.

* Types of Growth
    1. Constant Growth (O(1)): The runtime does not change with the input size
    2. Linear Growth (O(n)): The runtime increases directly proportional to the input size
    3. Quadratic Growth (O(n^2)): The runtime increases proportionally to the square of the input size

* Key Concepts
    • Large ns: Big-O is concerned with the behaviour of algorithms for very large input sizes
    • Ignoring Coefficients and Lower-order Terms: Focus on the term with the highest growth rate and ignore constants and less significant terms

* Examples of Big-O

    1. Linear Growth (O(n)):

        ```js
        function addNums(n) {
            let total = 0;
            for (let i = 1; i <= n; i++) {
                total += i;
            }
            return total;
        }
        ```
        • The loop runs 'n' times, so the time complexity O(n)

    2. Constant Growth (O(1)):

        ```js
        function addFirstAndLast(nums) {
            const firstNum = nums[0];
            const lastNum = nums[nums.length - 1];
            return firstNum + lastNum;
        }
        ```
        • The operations are constant and do not depend on the input size

    3. Quadratic Growth (O(n^2)):

        ```js
        function printPairSums(n) {
            for (let i = 0; i < n; i++) {
                for (let j = 0; j < n; j++) {
                    console.log(`${i} + ${j} = ${i + j}`)
                }
            }
        }
        ```
        • Two nested loops each run `n` times, resulting in O(n^2)


* Best, Worst, and Average Case Analysis
    • Best Case: The most optimal scenario (least work)
    • Worst Case: The least optimal scenario (most work)
    • Average Case: An average scenario over all possible inputs

For practical purposes, Big-O usually refers to the worse-case scenario

* Practical Examples

    • Array Search:
    ```js
    function arraySearch(arr, target) {
        for (let i = 0; i < arr.length; i++) {
            if (arr[i] === target) return true;
        }
        return false;
    }
    ```
    • Best Case: O(1) if the target is the first element
    • Worst Case: O(n) if the target is not present
    • Average Case: O(n) if the target is somewhere in the array


* Important Patterns

    1. Nested Loops:
        • Example: `O(n^2)` if each loop runs `n` times
        • More loops lead to higher polynomial growth

    2. Adjacent Loops:
        • Example: `O(n) + O(n) = O(2n) = O(n)`
        • Sequential loops add up but are simplified to the dominant term

    3. Composite Functions:
        • Example: `O(n^2 + n) = O(n^2)`
        • Ignore less significant terms to determine overall complexity


* Summary
    • Constant Time (O(1)): Time does not depend on the input size
    • Linear Time (O(n)): Time increases proportionally with input size
    • Quadratic Time (O(n^2)): Time increases with the square of the input size

Understanding Big-O helps in optimising code and is crucial for technical interviews, especially for large-scale applications
