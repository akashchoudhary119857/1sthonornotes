
# **Strings in JavaScript: '', "", and ``**


In JavaScript, you can define strings in **three ways**:

1. **Single quotes `' '`**
    
2. **Double quotes `" "`**
    
3. **Backticks `` ` ` `` (Template literals)**
	1.  Power of interpolation/ Decrypting variable name using interpolate signature ${})
       String Constructor
    

---

## **1. Single Quotes `' '`**

`let name = 'John'; console.log(name); // John`

 **Use cases:**

- Standard string declaration.
    
- Works fine for most strings.
    

 **Limitation:**

- Can’t easily include single quotes inside the string without escaping:
    

`let text = 'It\'s sunny'; // Need backslash to escape '`

---

## **2. Double Quotes `" "`**

`let name = "John"; console.log(name); // John`

 **Use cases:**

- Same as single quotes.
    
- Useful if the string itself contains single quotes:
    

`let text = "It's sunny"; // No need to escape '`

**Limitation:**

- Can’t include double quotes inside without escaping:
    

`let text = "He said \"Hello\""; // Must escape "`

---

## **3. Backticks `` ` ` `` — Template Literals**

``let name = `John`; console.log(name); // John``

**Advantages over '' and "":**

1. **Multi-line strings:**
    

``let poem = `Roses are red, Violets are blue, CodeWithAahi is fun, And so are you!`; 
console.log(poem);

2. **String interpolation (embedding expressions):**
    

let a = 5; 
let b = 10; 
console.log(`Sum of ${a} + ${b} = ${a + b}`);           // Sum of 5 + 10 = 15``

3. **Easier to include quotes without escaping:**
    

let text = `He said "It's sunny!"`; 
console.log(text);      // He said "It's sunny!"``

---

## **Summary Table**

|Feature|`' '` Single Quote|`" "` Double Quote|`` ` Backticks (Template Literals)|
|---|---|---|---|
|Basic string|✅|✅|✅|
|Multi-line|❌|❌|✅|
|Expression interpolation|❌|❌|✅ `${expression}`|
|Easier quotes inside string|Partial (needs escaping)|Partial (needs escaping)|✅|
|Use case|Simple strings|Simple strings with single quotes|Dynamic strings, multi-line, embedding expressions|
**Example comparing all three:**
let name = 'Alice';
let greeting1 = 'Hello ' + name + '!';       // Using single quote + concatenation
let greeting2 = "Hello " + name + "!";       // Using double quote + concatenation
let greeting3 = `Hello ${name}!`;            // Using template literal  easier
console.log(greeting1, greeting2, greeting3);

## Here are the list of string functions in java script

1. **charAt(index)**: Returns the character at the specified index.
2. **charCodeAt(index)**: Returns the Unicode of the character at the specified index.
3. **at(index)**: Returns the character at the specified index, allowing for negative indexing.
4. **concat(string2, string3, …, stringN)**: Joins two or more strings and returns a new string.
5. **includes(searchString, position)**: Checks if a string contains the specified string/characters.
6. **indexOf(searchValue, fromIndex)**: Returns the index of the first occurrence of the specified value.
7. **lastIndexOf(searchValue, fromIndex)**: Returns the index of the last occurrence of the specified value.
8. **match(regex)**: Searches a string for a match against a regular expression and returns the matches.
9. **matchAll(regex)**: Returns an iterator of all results matching a string against a regular expression.
10. **repeat(count)**: Returns a new string with a specified number of copies of an existing string.
11. **replace(searchValue, newValue)**: Replaces a specified value with another value in a string.
12. **replaceAll(searchValue, newValue)**: Replaces all occurrences of a specified value with another value in a string.
13. **search(regex)**: Searches a string for a specified value and returns the position of the match.
14. **slice(start, end)**: Extracts a part of a string and returns a new string.
15. **split(separator, limit)**: Splits a string into an array of substrings.
16. **substring(start, end)**: Extracts characters from a string between two specified indices.
17. **toLowerCase()**: Converts a string to lowercase letters.
18. **toUpperCase()**: Converts a string to uppercase letters.
19. **trim()**: Removes whitespace from both ends of a string.
20. **trimStart()**: Removes whitespace from the beginning of a string.
21. **trimEnd()**: Removes whitespace from the end of a string.
22. **padStart(targetLength, padString)**: Pads the current string with another string (multiple times, if needed) until the resulting string reaches the given length.
23. **padEnd(targetLength, padString)**: Pads the current string with another string (multiple times, if needed) until the resulting string reaches the given length.
24. **valueOf()**: Returns the primitive value of a String object.
25. **localeCompare(compareString, locales, options)**: Returns a number indicating whether a reference string comes before, after, or is the same as the given string in sort order.
26. **startsWith(searchString, position)**: Determines whether a string begins with the characters of a specified string.
27. **endsWith(searchString, length)**: Determines whether a string ends with the characters of a specified string.
28. **normalize(form)**: Returns the Unicode Normalization Form of the string.
29. **codePointAt(pos)**: Returns a non-negative integer that is the Unicode code point value at the given position.
30. **fromCharCode(num1, …, numN)**: Returns a string created from the specified sequence of UTF-16 code units.
31. **fromCodePoint(num1, …, numN)**: Returns a string created from the specified sequence of code points.
32. **raw(callSite, …substitutions)**: Returns a string created from a raw template string.
