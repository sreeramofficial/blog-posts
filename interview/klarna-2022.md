# Klarna 2022

&nbsp;
## Problem

Evaluate the value of an arithmetic expression in Reverse Polish Notation.

Valid operators are +, -, \*, and /. Each operand may be an integer or another expression.

Note that division between two integers should truncate toward zero.

It is guaranteed that the given RPN expression is always valid. That means the expression would always evaluate to a result, and there will not be any division by zero operation.

Leetcode - [150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

&nbsp;

## Solution

```js
/**
 * @param {string[]} tokens
 * @return {number}
 */

const operators = {
  "+": (a, b) => +a + +b,
  "-": (a, b) => +a - +b,
  "*": (a, b) => +a * +b,
  "/": (a, b) => (+a / +b) | 0,
};

var evalRPN = function (tokens) {
  return tokens.reduce((acc, item) => {
    if (item in operators) {
      const [a, b] = acc.splice(-2);
      const res = operators[item](a, b);
      return [...acc, res];
    }
    return [...acc, item];
  }, [])[0];
};
```
