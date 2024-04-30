# JavaScript-interview-codes
1. **Convert integer to Roman number**
```javascript
  function convertToRoman(num) {
  const romanNumerals = [
    { value: 100, symbol: 'C' },
    { value: 90, symbol: 'XC' },
    { value: 50, symbol: 'L' },
    { value: 40, symbol: 'XL' },
    { value: 10, symbol: 'X' },
    { value: 9, symbol: 'IX' },
    { value: 5, symbol: 'V' },
    { value: 4, symbol: 'IV' },
    { value: 1, symbol: 'I' },
  ];

  let result = '';

  for (let i = 0; i < romanNumerals.length; i++) {
    while (num >= romanNumerals[i].value) {
      result += romanNumerals[i].symbol;
      num -= romanNumerals[i].value;
    }
  }

  return result;
}

// Example usage:
console.log(convertToRoman(34)); // Output: XXXIV
console.log(convertToRoman(88)); // Output: LXXXVIII

```

2. **Check Number is floating or Integer**
```js
  function checkNumberType(num) {
  console.log(Math.round(num), 'de');
  if (Math.round(num) === num) {
    return 'Integer';
  } else {
    return 'Floating-point';
  }
}
 ```
