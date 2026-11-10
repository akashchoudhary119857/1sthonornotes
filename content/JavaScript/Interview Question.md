let num = "5";
let numNew = 2;
console.log(num + numNew)
console.log(num - numNew)


let num = false;
let numNew = !num;
console.log(numNew)


console.log([]==[]);


let num = 0.1 + 0.2;
let numNew = 0.3 ;
console.log(num == numNew);

console.log(undefined + 1)
console.log(true + false)
console.log(false + false)
console.log(true + true)
console.log(true + true + true)
console.log("5" + 2);
console.log("5" - 2);
console.log("5" + 2+"5");
console.log(5 + 2+"5");
console.log(5 + "2"+"5");
console.log(1 + +"2" + "2");
console.log(1 + -"1" + "2");
console.log(+"1" + "1" + "2");
console.log("A" - "B" + "2");
1. **“A” - “B”**:
    
    - In JavaScript, the `-` operator tries to convert the operands to numbers.
    - Since “A” and “B” are strings and not numbers, the conversion fails, resulting in `NaN` (Not-a-Number).
2. **NaN + “2”**:
    
    - Now, we have `NaN` (from the previous step) and the string `"2"`.
    - When you use the `+` operator with a `NaN` and a string, JavaScript converts `NaN` to a string and concatenates it with `"2"`.
    - Therefore, `NaN + "2"` results in the string `"NaN2"`.
console.log("A" - "B" + 2);
1. **“A” - “B”**:
    
    - The `-` operator tries to convert the operands to numbers.
    - Since “A” and “B” are strings and not numbers, the conversion fails, resulting in `NaN` (Not-a-Number).
2. **NaN + 2**:
    
    - Now, we have `NaN` (from the previous step) and the number `2`.
    - When you use the `+` operator with `NaN` and a number, the result is still `NaN` because any arithmetic operation with `NaN` results in `NaN`.
console.log(null + 1);
console.log("A" + "B" + "2");
1. **“A” + “B”**:
    
    - The `+` operator, when used with strings, concatenates them.
    - So, `"A" + "B"` results in the string `"AB"`.
2. **“AB” + “2”**:
    
    - Again, the `+` operator concatenates the strings.
    - So, `"AB" + "2"` results in the string `"AB2"`.

Therefore, the output of `console.log("A" + "B" + "2");` is `"AB2"`.

