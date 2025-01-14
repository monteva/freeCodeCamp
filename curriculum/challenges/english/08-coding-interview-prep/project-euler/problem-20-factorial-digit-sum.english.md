---
id: 5900f3801000cf542c50fe93
challengeType: 5
title: 'Problem 20: Factorial digit sum'
forumTopicId: 301839
---

## Description
<section id='description'>
<var>n</var>! means <var>n</var> × (<var>n</var> − 1) × ... × 3 × 2 × 1
For example, 10! = 10 × 9 × ... × 3 × 2 × 1 = 3628800,<br>and the sum of the digits in the number 10! is 3 + 6 + 2 + 8 + 8 + 0 + 0 = 27.
Find the sum of the digits <var>n</var>!
</section>

## Instructions
<section id='instructions'>

</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>sumFactorialDigits(10)</code> should return 27.
    testString: assert.strictEqual(sumFactorialDigits(10), 27);
  - text: <code>sumFactorialDigits(25)</code> should return 72.
    testString: assert.strictEqual(sumFactorialDigits(25), 72);
  - text: <code>sumFactorialDigits(50)</code> should return 216.
    testString: assert.strictEqual(sumFactorialDigits(50), 216);
  - text: <code>sumFactorialDigits(75)</code> should return 432.
    testString: assert.strictEqual(sumFactorialDigits(75), 432);
  - text: <code>sumFactorialDigits(100)</code> should return 648.
    testString: assert.strictEqual(sumFactorialDigits(100), 648);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function sumFactorialDigits(n) {
  // Good luck!
  return n;
}

sumFactorialDigits(100);
```

</div>



</section>

## Solution
<section id='solution'>

```js
const sumFactorialDigits = (n) => {
  if(n === 0) {
    return [1]
  }
  const result = sumFactorialDigits(n - 1)
  let overflow = [0]
  const limit = result.length
  for(let i = 0; i <= limit; i++) {
    const digit = (result[i] || 0) * n + overflow.pop()
    if(digit > 9) {
      let newOverflow = parseInt(digit / 10).toString().split('').map((x, index, arr) => parseInt(x) + (overflow[arr.length - index - 1] || 0))
      overflow = newOverflow
      for(let j = 0;j < Math.max(newOverflow.length, overflow.length); j++) {

      }
      result[i] = digit % 10
    } else {
      result[i] = digit
      overflow = [0]
    }
  }

  return result
}

sumFactorialDigits(100);
```

</section>
