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


Reference: http://es5.github.io/#x11.6.1
