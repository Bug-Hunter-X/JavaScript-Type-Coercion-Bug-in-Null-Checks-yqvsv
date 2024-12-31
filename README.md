# JavaScript Type Coercion Bug
This repository demonstrates a subtle bug in JavaScript related to type coercion within null checks. The function `foo` aims to return `null` if either `a` or `b` is `null`, otherwise it returns their sum.  However, the strict equality (`===`) operator can lead to unexpected results if the inputs are not strictly null but are coercible to nullish values (e.g., 0, '' ).

## Bug Description
The core issue stems from the limitations of type coercion in JavaScript.  The strict equality (`===`) operator doesn't perform any type conversion before comparison. This is good for strict comparisons but can fail in certain cases with unexpected nullish values. 

## How to Reproduce
1. Clone this repository.
2. Run `bug.js` using a JavaScript interpreter like Node.js.
3. Observe the unexpected behavior when supplying inputs that would ideally coerce to null in a loose equality setting, but are not strictly null. 

## Solution
The solution utilizes loose equality (`==`) to handle these unexpected values correctly. This is less precise but gives more leeway for type coercion which can improve the outcome in handling unexpected input cases in production.  In production, a more robust way to handle unexpected inputs is to use explicit type checking and validation to ensure the inputs meet the expected type and format before proceeding with the operation.