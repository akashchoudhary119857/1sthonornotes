**Lab 1: Object Comparison in JavaScript**

**Objective:**

To develop a JavaScript program that compares two objects to determine if the first object contains equivalent property values to the second object.

**Scenario:**

In this lab exercise, you will write a JavaScript function to compare two objects. The function should check if all properties in the second object have equivalent values in the first object. This skill is essential for scenarios where object comparison is critical, such as validating data consistency, implementing deep equality checks, and performing quality assurance tests.
**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `objectComparison.js`.
        
    - Define two objects with similar and differing property values for testing.
        
2. **Function Development:**
    
    - Write a function `compareObjects(obj1, obj2)` that takes two parameters.
        
    - Use a loop to iterate over the properties of `obj2` and compare them with the properties in `obj1`.
        
    - Ensure that the function returns `true` if all properties and their values in `obj2` are present and equivalent in `obj1`, and `false` otherwise.
        
3. **Testing:**
    
    - Test your function with various objects to ensure accuracy.
        
    - Console log the results of your comparisons for validation.
**Outcome:**

By the end of this lab, you will have a functional JavaScript program capable of comparing two objects to check for equivalent property values. This exercise will enhance your understanding of object manipulation, property iteration, and conditional checks in JavaScript.

**Lab 2: Converting CSV String to 2D Array of Objects in JavaScript**

**Objective:**

To write a JavaScript program that converts a comma-separated value (CSV) string into a 2D array of objects, utilizing the first row of the CSV string as the title row.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that converts a given CSV string into a 2D array of objects. The first row of the CSV string will be used as the title row, providing the keys for each object in the array. This exercise will help you understand how to handle and manipulate CSV data in JavaScript, which is a common requirement in data processing and web applications.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `csvToArray.js`.
        
    - Define a sample CSV string to be used for testing your function.
        
2. **Function Development:**
    
    - Write a function `csvToArray(csvString)` that takes a single parameter `csvString`.
        
    - Split the CSV string by rows and columns to create a 2D array.
        
    - Use the first row as the title row to define keys for the objects.
        
    - Map the remaining rows to create an array of objects using the title row.
        
3. **Testing:**
    
    - Test your function with various CSV strings to ensure it converts the data accurately.
        
    - Console log the results of your conversion for validation.
**Outcome:**

By the end of this lab, you'll have a working JavaScript program capable of converting a CSV string into a 2D array of objects, with the first row of the string used as the title row. This will enhance your understanding of string manipulation, array methods, and object creation in JavaScript.

**Lab 3: Filtering Specified Values from an Array in JavaScript**

**Objective:**

To develop a JavaScript program that filters out specified values from a given array and returns the original array without the filtered values.

**Scenario:**

In this lab exercise, you'll write a JavaScript function to remove specified values from an array. This is a common task in data processing, allowing for the cleanup of datasets by removing unwanted or irrelevant values. The exercise will help you understand array manipulation, the use of higher-order functions, and the importance of data sanitization in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `filterArray.js`.
        
    - Define a sample array and a list of values to be filtered out for testing your function.
        
2. **Function Development:**
    
    - Write a function `filterArray(arr, valuesToFilter)` that takes two parameters: `arr` (the original array) and `valuesToFilter` (an array of values to be removed from the original array).
        
    - Use array methods such as `filter` and `includes` to remove the specified values from the original array.
        
    - Ensure the function returns a new array with the filtered values removed.
        
3. **Testing:**
    
    - Test your function with various arrays and sets of values to filter out, ensuring it behaves as expected.
        
    - Console log the results of your filtering operation for validation.
**Outcome:**

By the end of this lab, you'll have a working JavaScript program capable of filtering out specified values from an array and returning the original array without those values. This exercise will strengthen your understanding of array manipulation, higher-order functions, and data sanitization in JavaScript.

**Lab 4: Combining Numbers into All Combinations in JavaScript**

**Objective:**

To create a JavaScript program that takes a given array of numbers and returns an array containing all possible combinations of those numbers.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that generates all possible combinations of numbers from a given array. This task is vital for understanding how to approach problems related to permutations and combinations, which are common in algorithm design and data processing.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `combinations.js`.
        
    - Define a sample array of numbers to be used for testing your function.
        
2. **Function Development:**
    
    - Write a function `getCombinations(arr)` that takes an array of numbers as a parameter.
        
    - Use recursion to generate all possible combinations of the numbers in the array.
        
    - Ensure the function returns an array containing all combinations of the input array.
        
3. **Testing:**
    
    - Test your function with different arrays to ensure it generates the correct combinations.

**Lab 5 : Finding Minimum-Maximum Values in an Array Using a Comparing Rule in JavaScript**

**Objective:**

To write a JavaScript program that returns the minimum and maximum values of an array after applying a provided function to set a comparing rule.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that determines the minimum and maximum values of an array based on a specified comparing rule. This task is crucial for data analysis and custom sorting operations where a specific rule is applied to determine the order or range of data points.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `minMaxArray.js`.
        
    - Define a sample array of numbers to be used for testing your function.
        
    - Define a custom comparing function that will set the rule for comparison.
        
2. **Function Development:**
    
    - Write a function `minMaxBy(arr, fn)` that takes two parameters: `arr` (the array of numbers) and `fn` (the function to set the comparing rule).
        
    - Use array methods such as `reduce` to iterate through the array and determine the minimum and maximum values based on the comparing rule provided by `fn`.
        
    - Ensure the function returns an object containing both the minimum and maximum values.
        
3. **Testing:**
    
    - Test your function with different arrays and comparing functions to ensure it behaves as expected.
        
    - Console log the results of your comparisons for validation.
**Outcome:**

By the end of this lab, you'll have a working JavaScript program capable of finding the minimum and maximum values in an array based on a provided comparing rule. This exercise will enhance your understanding of higher-order functions, array manipulation, and the application of custom comparison logic in JavaScript.

**Lab 6: Splitting Array Values into Two Groups in JavaScript**

**Objective:**

To write a JavaScript program that splits the values of two given arrays into two groups. If an element in the filter array is true, the corresponding element in the collection array belongs to the first group; otherwise, it belongs to the second group.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that separates values from an array into two different groups based on the values of a filter array. This task is essential for understanding array manipulation and conditional logic in JavaScript, providing a foundation for more complex data processing and filtering operations.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `splitArray.js`.
        
    - Define two sample arrays: one for the collection of values and one for the filter criteria.
        
2. **Function Development:**
    
    - Write a function `splitByFilter(collection, filter)` that takes two parameters: `collection` (the array of values) and `filter` (the array of boolean values).
        
    - Use array methods such as `reduce` to iterate through the collection and split the values into two groups based on the filter array.
        
    - Ensure the function returns an object with two properties: `group1` and `group2`, representing the two groups of values.
        
3. **Testing:**
    
    - Test your function with different arrays to ensure it correctly splits the values based on the filter criteria.
        
    - Console log the results of your splitting operation for validation.

**Outcome:**

By the end of this lab, you'll have a working JavaScript program capable of splitting the values of two arrays into two groups based on a filter array. This exercise will enhance your understanding of array manipulation and conditional logic in JavaScript.

**Lab 7: Getting the Current Date in JavaScript**

**Objective:**

To write a JavaScript program that retrieves the current date and formats it in different ways: `mm-dd-yyyy`, `mm/dd/yyyy`, `dd-mm-yyyy`, and `dd/mm/yyyy`.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function to get the current date and format it in various common date formats. This task is essential for understanding how to work with dates and times in JavaScript, and how to manipulate string formats to achieve the desired output.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `formatDate.js`.
        
    - Use the built-in `Date` object to get the current date.
        
2. **Function Development:**
    
    - Write a function `getFormattedDate()` that retrieves the current date.
        
    - Create sub-functions or use methods to format the date into `mm-dd-yyyy`, `mm/dd/yyyy`, `dd-mm-yyyy`, and `dd/mm/yyyy`.
        
    - Ensure the function returns the date in the specified formats.
        
3. **Testing:**
    
    - Test your function to make sure it returns the current date in all the required formats.
        
    - Console log the results to verify correctness.

**Lab 8: Splitting Values into Two Groups in JavaScript**

**Objective:**

To develop a JavaScript program that splits values into two groups based on a filter array. If an element in the filter is true, the corresponding element in the collection belongs to the first group; otherwise, it belongs to the second group.

**Scenario:**

In this lab exercise, you'll write a JavaScript function that separates values from an array into two groups using a filter array. This task is vital for data processing, allowing you to classify or segregate data based on specific criteria. The exercise will improve your understanding of array manipulation, conditional logic, and the use of higher-order functions in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `splitValues.js`.
        
    - Define two sample arrays: one for the collection of values and one for the filter criteria.
        
2. **Function Development:**
    
    - Write a function `splitByFilter(collection, filter)` that takes two parameters: `collection` (the array of values) and `filter` (the array of boolean values).
        
    - Use array methods such as `reduce` to iterate through the collection and separate values into two groups based on the filter array.
        
    - Ensure the function returns an object with two properties: `group1` and `group2`, representing the two groups of values.
        
3. **Testing:**
    
    - Test your function with different arrays to ensure it correctly splits the values based on the filter criteria.
        
    - Console log the results to verify correctness.

**Lab 9: Computing Absolute Difference with Conditional Multiplication in JavaScript**

**Objective:**

To write a JavaScript program that computes the absolute difference between a specified number and 19. The program should return triple the absolute difference if the specified number is greater than 19.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that calculates the absolute difference between a given number and 19. If the given number is greater than 19, the function should return three times the absolute difference. This task is fundamental for understanding conditional statements and mathematical operations in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `absoluteDifference.js`.
        
    - Define a sample number for testing your function.
        
2. **Function Development:**
    
    - Write a function `computeDifference(num)` that takes a single parameter `num`.
        
    - Calculate the absolute difference between `num` and 19.
        
    - Use an if-else statement to check if `num` is greater than 19. If true, return triple the absolute difference; otherwise, return the absolute difference.
        
3. **Testing:**
    
    - Test your function with various numbers to ensure it returns the correct value.
        
    - Console log the results to verify correctness.

**Lab 10: Checking for Substring Presence and Modification in JavaScript**

**Objective:**

To write a JavaScript program that checks whether the substring "Script" appears at the 5th (index 4) position in a given string. If "Script" appears in the specified position, the program should return the string without "Script"; otherwise, return the original string.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that examines a string to see if "Script" appears at the 5th position. If it does, the function will return the string without "Script". This task is fundamental for understanding string manipulation, conditional logic, and indexing in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `checkSubstring.js`.
        
    - Define a sample string for testing your function.
        
2. **Function Development:**
    
    - Write a function `checkAndRemoveScript(str)` that takes a single parameter `str`.
        
    - Use the `substring` or `slice` methods to check if "Script" appears at the 5th position (index 4) of `str`.
        
    - Use an if-else statement to return the modified string without "Script" if the condition is met, otherwise return the original string.
        
3. **Testing:**
    
    - Test your function with various strings to ensure it behaves as expected.
        
    - Console log the results to verify correctness.

**Lab 11: Determining the Sign of the Product of Three Numbers in JavaScript**

**Objective:**

To write a JavaScript program that uses a conditional statement to determine the sign of the product of three given numbers. The program should display an alert box with the specified sign.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that determines whether the product of three numbers is positive or negative. This task helps reinforce your understanding of conditional statements, logical operators, and the importance of handling numeric data in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `productSign.js`.
        
    - Define three sample numbers for testing your function.
        
2. **Function Development:**
    
    - Write a function `findProductSign(num1, num2, num3)` that takes three parameters.
        
    - Use a conditional statement to check the signs of the numbers and determine the sign of their product.
        
    - Display an alert box with the sign of the product.
        
3. **Testing:**
    
    - Test your function with different sets of numbers to ensure it correctly identifies the sign of the product.
        
    - Verify that the alert box displays the correct sign.

**Lab 12: Finding the Closest Value to 100 in JavaScript**

**Objective:**

To write a JavaScript program that compares two numerical values and determines which one is closest to 100.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that takes two numerical values as inputs and returns the value that is closest to 100. This task will help you understand conditional statements, absolute value calculations, and basic comparison operations in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `closestTo100.js`.
        
    - Define two sample numbers for testing your function.
        
2. **Function Development:**
    
    - Write a function `findClosestTo100(num1, num2)` that takes two parameters: `num1` and `num2`.
        
    - Calculate the absolute difference between each number and 100.
        
    - Use a conditional statement to compare the differences and determine which number is closer to 100.
        
    - Ensure the function returns the number that is closest to 100.
        
3. **Testing:**
    
    - Test your function with different sets of numbers to ensure it behaves as expected.
        
    - Console log the results to verify correctness.

**Lab 12: Evaluating Student Grades Based on Examination Marks in JavaScript**

**Objective:**

To write a JavaScript program that evaluates a student's total marks across various examinations and determines their grade based on specific criteria. The program should return `true` if the student achieves an A+ grade, otherwise it should return `false`.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function that evaluates a student's total marks and determines their grade. The grading criteria are as follows:

1. If the total marks fall within the range of 89 to 100 (inclusive), the student receives an A+ grade.
    
2. If the examination is labeled as "Final-exam," the student will receive an A+ grade only if their total marks are 90 or greater.
    

You will assume that the "Final-exam" is indicated by passing `true` as the second parameter to the function; otherwise, the second parameter will be `false`.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `evaluateGrade.js`.
        
    - Define a function that takes the student's total marks and a boolean indicating if it's the final exam.
        
2. **Function Development:**
    
    - Write a function `evaluateGrade(totalMarks, isFinalExam)` that takes two parameters: `totalMarks` (the student's total marks) and `isFinalExam` (a boolean indicating if it's the final exam).
        
    - Implement the grading criteria using conditional statements.
        
    - Ensure the function returns `true` if the student receives an A+ grade, otherwise return `false`.
        
3. **Testing:**
    
    - Test your function with various total marks and final exam indicators to ensure it behaves as expected.
        
    - Console log the results to verify correctness.

**Lab 13: Checking Number Sequences for Increasing Order in JavaScript**

**Objective:**

To write a JavaScript program that checks whether three given numbers are increasing in strict mode or in soft mode.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function to determine whether a sequence of three numbers is increasing strictly or softly. The function will help you understand conditional statements and comparative logic, essential for data validation and sorting algorithms.

- **Strict Mode:** Numbers must be in a strictly increasing order (e.g., 10, 15, 31).
    
- **Soft Mode:** Numbers can be equal or in any increasing order (e.g., 24, 22, 31 or 22, 22, 31).
    

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `checkNumberSequence.js`.
        
    - Define three sample numbers for testing your function.
        
2. **Function Development:**
    
    - Write a function `checkSequence(num1, num2, num3)` that takes three parameters.
        
    - Implement conditional logic to check if the numbers are in strict or soft increasing order.
        
    - Return 'Strict Mode' if the numbers are in strict order, 'Soft Mode' if they are in soft order, or 'Neither' if none of the conditions are met.
        
3. **Testing:**
    
    - Test your function with different sets of numbers to ensure it behaves as expected.
        
    - Console log the results to verify correctness.

**Lab 14: Checking Whether a Given Number is an Adam Number in JavaScript**

**Objective:**

To write a JavaScript program that checks whether a given number is an Adam number.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function to determine whether a given number is an Adam number. An Adam number is a number that, when squared, the reverse of the resulting square is the square of the reverse of the original number. This task will help you understand number manipulation, reversing strings and numbers, and using conditional statements in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `checkAdamNumber.js`.
        
    - Define a sample number for testing your function.
        
2. **Function Development:**
    
    - Write a function `isAdamNumber(num)` that takes a single parameter `num`.
        
    - Implement logic to square the number, reverse the squared number, and check if this reversed number is equal to the square of the reversed original number.
        
    - Ensure the function returns `true` if the number is an Adam number, otherwise return `false`.
        
3. **Testing:**
    
    - Test your function with various numbers to ensure it behaves as expected.
        
    - Console log the results to verify correctness.

**Lab 15: Moving the Last Three Characters to the Start of a String in JavaScript**

**Objective:**

To write a JavaScript program that moves the last three characters of a given string to the start. The string length must be greater than or equal to three.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function to rearrange the last three characters of a string to the beginning of the string. This task will help you understand string manipulation, substring extraction, and concatenation in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `moveLastThreeChars.js`.
        
    - Define a sample string for testing your function.
        
2. **Function Development:**
    
    - Write a function `moveLastThreeChars(str)` that takes a single parameter `str`.
        
    - Check if the length of the string is greater than or equal to three.
        
    - Extract the last three characters and the remaining part of the string.
        
    - Concatenate the last three characters at the start of the remaining string and return the result.
        
3. **Testing:**
    
    - Test your function with various strings to ensure it behaves as expected.
        
    - Console log the results to verify correctness.

**Lab 16: Finding the First 5 Happy Numbers in JavaScript**

**Objective:**

To write a JavaScript program that finds and prints the first five happy numbers. A happy number is defined as a number that eventually equals 1 when replaced repeatedly by the sum of the squares of its digits. If the process loops endlessly without reaching 1, the number is considered an unhappy (or sad) number.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function to determine whether a number is a happy number and to find the first five happy numbers. This task will help you understand loops, conditionals, and digit manipulation in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `happyNumbers.js`.
        
    - Define a function to check whether a number is happy.
        
2. **Function Development:**
    
    - Write a function `isHappyNumber(num)` that takes a single parameter `num`.
        
    - Implement the logic to repeatedly replace the number by the sum of the squares of its digits.
        
    - Check for cycles to determine if the number is unhappy.
        
    - Write a function `findFirstNHappyNumbers(n)` to find and print the first `n` happy numbers.
        
3. **Testing:**
    
    - Test your function by finding the first five happy numbers.
        
    - Console log the results to verify correctness.

**Lab 17: Sorting Letters in a String Alphabetically Using JavaScript**

**Objective:**

To write a JavaScript function that returns a string with its letters sorted in alphabetical order. Punctuation, numbers, and symbols are not included in the passed string.

**Scenario:**

In this lab exercise, you'll develop a JavaScript function to take a string and return a new string where the letters are sorted alphabetically. This task will enhance your understanding of string manipulation, array methods, and sorting algorithms in JavaScript.

**Procedure:**

1. **Setup:**
    
    - Create a new JavaScript file named `alphabeticalOrder.js`.
        
    - Define a sample string for testing your function.
        
2. **Function Development:**
    
    - Write a function `sortStringAlphabetically(str)` that takes a single parameter `str`.
        
    - Convert the string to an array of characters.
        
    - Use the array's `sort` method to sort the characters alphabetically.
        
    - Join the sorted array back into a string and return the result.
        
3. **Testing:**
    
    - Test your function with various strings to ensure it returns the expected output.
        
    - Console log the results to verify correctness.