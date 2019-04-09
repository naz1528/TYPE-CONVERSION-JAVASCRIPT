# TYPE-CONVERSION-JAVASCRIPT
                                      TYPE CONVERSION JAVASCRIPT DOCUMENT


                                  Applying the Additive Operators to Numbers # Ⓣ 
The + operator performs addition when applied to two operands of numeric type, producing the sum of the operands. The - operator performs subtraction, producing the difference of two numeric operands.

   Addition is a commutative operation, but not always associative.

   The result of an addition is determined using the rules of IEEE 754 binary double-precision arithmetic:

                 If either operand is NaN, the result is NaN.

                 The sum of two infinities of opposite sign is NaN.

                  The sum of two infinities of the same sign is the infinity of that sign.

                  The sum of an infinity and a finite value is equal to the infinite operand.

                  The sum of two negative zeros is −0. The sum of two positive zeros, or of two zeros of opposite sign, is +0.

                  The sum of a zero and a nonzero finite value is equal to the nonzero operand.

                  The sum of two nonzero finite values of the same magnitude and opposite sign is +0.

                  In the remaining cases, where neither an infinity, nor a zero, nor NaN is involved, and the operands have the same sign or have different magnitudes, the sum is computed and rounded to the nearest representable value using IEEE 754 round-to-nearest mode. If the magnitude is too large to represent, the operation overflows and the result is then an infinity of appropriate sign. The ECMAScript language requires support of gradual underflow as defined by IEEE 754.

                  The - operator performs subtraction when applied to two operands of numeric type, producing the difference of its operands; the left operand is the minuend and the right operand is the subtrahend. Given numeric operands a and b, it is always the case that a–b produces the same result as a +(–b).
                  
                  Type Conversion: Number and String
One of the most common things you find yourself doing in JavaScript is using arithmetic operators: +, -, *, /. These operators expect operands that are numbers. So when any of the operands is not a number, JavaScript implicitly coerces it into a number. But there are times when you may not get the result you may be expecting, especially when you are using the + operator. This is majorly because the + operator is also used for string concatenation. See the following snippet:

                                              console.log(100 + 50); // 150
                                              console.log(100 - 50); // 50

                                              console.log('100' + 50); // "10050"
                                              console.log('100' - 50); // 50

                                              console.log(null + 50); // 50
                                              console.log(null - 50); // -50

                                              console.log(void 0 + 50); // NaN
                                              console.log(void 0 - 50); // NaN

                                              console.log(true + 50); // 51
                                              console.log(true - 50); // -49

                                              console.log(false + 50); // 50
                                              console.log(false - 50); // -50

                                              console.log([] + 50); // "50"
                                              console.log([] - 50); // -50

                                              console.log([100] + 50); // "10050"
                                              console.log([100] - 50); // 50

                                              console.log({} + 50); // "[object Object]50"
                                              console.log({} - 50); // NaN

                                              console.log(new Date + 1000); // "Thu May 31 2018 18:27:51 GMT+0100 (WAT)1000"
                                              console.log(new Date - 1000); // 1527787670595
                                              
        Explanation:
        
              Based on your response, here are two expressions:

                               [] + 50 === '50'
                               [] — 50 === -50

The results of the expressions on the LHS of the === operator are clearly an indication of how JavaScript implicitly coerces data types for certain operations.

                 Case 1
The + operator does one of these two operations:

number addition — if both operands are numbers,
string concatenation—otherwise.
Hence, in (1) above, the + operator does string concatenation instead of number addition, since both operands are not numbers. In order to do string concatenation, the operands are first converted to strings.

               [] converted to a string becomes ''.
Note that, conversion of an array to string is equivalent to calling .join(',') on the array — using a comma (,) as the separator.
                // Array.toString()
                [1, 2, 3, 4, 5].toString(); // "1,2,3,4,5"

                // is equivalent to
                // Array.join(',')
                [1, 2, 3, 4, 5].join(','); // "1,2,3,4,5"
                50 converted to a string becomes '50'
                Therefore,

                [] + 50
                becomes (after the implicit type coercion):

                '' + '50'
                which results to:

                '50'
                        
                        Case 2
In (2) above, the — operator always does number subtraction. Hence, the operands are first converted to numbers.

[] converted to a number becomes 0.
Note that if the array contains exactly one item, then the result of converting the array to a number is the same as the result of converting the only item in the array to a number.
However, if the array contains more than one item, then converting to a number returns NaN.
50 is already a number so it stays the same.
Therefore,

                        [] - 50
                        becomes (after the implicit type coercion):

                        0 - 50
                        which results to:

                        -50


Using the unary + operator on a value is functionally equivalent to casting the value using the Number() function.

              +new Date === Number(new Date); // true
              
              
              String Concatenation
              
The + operator can also be used to convert values to string. Concatenate an empty string('') to any value using the + operator to convert the value to a string.

                                console.log(100 + ''); // "100"

                                console.log(null + ''); // "null"
                                console.log(void 0 + ''); // "undefined"

                                console.log(true + ''); // "true"
                                console.log(false + ''); // "false"

                                console.log([] + ''); // ""
                                console.log([100] + ''); // "100"
                                console.log([100, 50] + ''); // "100,50"

                                console.log({} + ''); // "[object Object]"

                                console.log(new Date + ''); // "Thu May 31 2018 19:28:09 GMT+0100 (WAT)"
                                
                                 Short-Circuiting
When working with the (|| and &&) logical operators, you may have noticed an interesting behavior called short-circuiting. Here is how it works:

The logical && operator returns the first operand if it is falsy, otherwise it returns the second operand.

The logical && short-circuiting is commonly used as a replacement for very simple if statements as shown in the following snippet:


                                   // METHOD 1: Using if statement
                                    if (person) {
                                      fetchProfile(person);
                                    }

                                    // METHOD 2: Using short-circuiting
                                    person && fetchProfile(person);

Note that using short-circuiting actually returns a value since it is a JavaScript expression. Hence, the result of a short-circuiting operation can be stored in a variable or used anywhere JavaScript expects a value.

var personProfile = person && fetchProfile(person);
However, using if statement does not return a value because it is a JavaScript statement.

The logical || operator returns the first operand if it is truthy, otherwise it returns the second operand.

                                                 // METHOD 1: Using if/else statements
                                                  let requestAnimFrame = null;

                                                  if (window.requestAnimationFrame) {
                                                 requestAnimFrame = window.requestAnimationFrame;
                                                  }

                                                  else if (window.webkitRequestAnimationFrame) {
                                                    requestAnimFrame = window.webkitRequestAnimationFrame;
                                                  }

                                                  else if (window.mozRequestAnimationFrame) {
                                                    requestAnimFrame = window.mozRequestAnimationFrame;
                                                  }

                                                  // METHOD 2: Using short-circuiting
                                                  const requestAnimFrame2 = (
                                                    window.requestAnimationFrame ||
                                                    window.webkitRequestAnimationFrame ||
                                                    window.mozRequestAnimationFrame ||
                                                    null
                                                  );
Reference: http://es5.github.io/#x11.6.1
