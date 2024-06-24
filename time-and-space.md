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
