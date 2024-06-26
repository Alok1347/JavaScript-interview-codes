# JavaScript-interview-codes
### Table of Contents

| No. | Questions                                                                                                                                                     |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [Convert integer to Roman numbers upto 100](#convert-integer-to-roman-numbers-upto-100)                                                                       |
| 2   | [Check wheather number is integer or Floating number](#check-wheather-number-is-integer-or-floating-number)                                                   |
| 3   | [Convert Underscore variable name to camelCase](#convert-underscore-variable-name-to-camelcase)                                                               |
| 4   | [Magereta teacher result declartion problem for calculating students average problem (Nagarro interview)](#magereta-teacher-result-declartion-problem-for-calculating-students-average-problem-nagarro-interview)                                                                                                                                    |      
| 5   | [count the occurance of the each and show in the object.](#count-the-occurance-of-the-each-and-show-in-the-object)                                            |
| 6   | [Use recurssion to do deep copy js Object](#use-recurssion-to-do-deep-copy-js-object)                                                                         |
| 7   | [Write a function to remove duplicate elements from array.](#write-a-function-to-remove-duplicate-elements-from-array)                                        |
| 8   | [Find the largest two values of array.](#find-the-largest-two-values-of-array)                                                                                |
| 9   | [Write a program to print message after 1 sec delay](#write-a-program-to-print-message-after-1-sec-delay)                                                     |
| 10   | [Output 1](#output-1)                                                                                                                                        |
| 11   | [Output 2](#output-2 )                                                                                                                                       |

                                                                                                                                                                  

1. ### Convert integer to Roman numbers upto 100
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
 **[⬆ Back to Top](#table-of-contents)**
---

2. ### Check wheather number is integer or Floating number
```js
  function checkNumberType(num) {
  if (Math.round(num) === num) {
    return 'Integer';
  } else {
    return 'Floating-point';
  }
}
 ```
 **[⬆ Back to Top](#table-of-contents)**
---
3. ### Convert Underscore variable name to camelCase,
Example: input= alok_singh_developer => alokSinghDeveloper
```js
let result = [];
function converter(input) {
  result = input.split('_');
  const temp = result.map(el =>
    el.replace(el.charAt(0), el.charAt(0).toUpperCase())
  );

  const res = temp.join('');
  return res.replace(res.charAt(0), res.charAt(0).toLowerCase());
}

console.log(converter('my_new_array'));
console.log(converter('alok_singh_developer'));
```
 **[⬆ Back to Top](#table-of-contents)**
---
4. ### Magereta teacher result declartion problem for calculating students average problem (Nagarro interview)
Statement:- Given a list of N students, every student is marked for M subjects. Each student is denoted by an index value. Their teacher Ms. Margaret must ignore the marks of any 1 subject for every student. For this she decides to ignore the subject which has the lowest class average. Your task is to help her find that subject, calculate the total marks of each student in all the other subjects and then finally return the array of the total marks scored by each student.
Input Specification: input1: An integer value N denoting number of students
input2: An integer value M denoting number of subjects
input3: A 2-D integer array of size N'M containing the marks of all students in each subject.
Output Specification:
Return an integer array of size N containing the total marks of each student after deducting the score for that one subject.
```js
const marks = [
  [23, 45, 87, 21, 33], // [59, 115, 200 ,139 ]
  [23, 25, 86, 21, 53],
  [13, 45, 27, 31, 53],
];
let totalMarks = [];
const averageMarks = marks => {
  for (let i = 0; i < marks[0].length; i++) {
    let sum = 0;
    for (let j = 0; j < marks.length; j++) {
      sum = sum + marks[j][i];
    }
    totalMarks.push(sum);
  }
  return totalMarks;
};
const avgMarks = averageMarks(marks);
let minValue = Math.min(...avgMarks);
const indexValue = avgMarks.indexOf(minValue);
const newMarks = marks.map(mark => mark.filter((data, i) => i !== indexValue));
console.log(newMarks);
const reducedArray = newMarks.map(mark =>
  mark.reduce((acc, curr) => acc + curr, 0)
);
console.log(reducedArray, 'Final Marks');
```
 **[⬆ Back to Top](#table-of-contents)**

---
5. ### count the occurance of the each and show in the object.
```js
const dataArray = ["rat", "cat", "dog", "cat", "cat", "cat", "rat"];
function counter(elements) {
  const number = {};
  for (ele of elements) {
    if (number[ele]) {
      number[ele] += 1;
    } else {
      number[ele] = 1;
    }
  }
  return console.log(number);
}

counter(dataArray); //  {rat: 2, cat: 4, dog: 1}
```
 **[⬆ Back to Top](#table-of-contents)**

---

6. ### Use recurssion to do deep copy js Object
```js
const message = [
  {
    name: 'alok',
    age: 20,
    Foods: [
      {
        breakfast: 'Poha',
        dinner: 'Khichdi',
        sleep: [
          {
            napping: 'short',
            deep: 'long',
          },
        ],
      },
    ],
  },
  {
    name: 'Subham',
    age: 22,
    Foods: [
      {
        breakfast: 'Maggie',
        dinner: 'Pizaa',
        sleep: [
          {
            napping: 'short only',
            deep: 'long only',
          },
        ],
      },
    ],
  },
];

function flaten(arr) {
  let dataArr = [];
  let hasNestedArray = false;

  arr.forEach(item => {
    const newItem = {};
    for (const key in item) {
      if (Array.isArray(item[key])) {
        item[key].forEach(food => {
          Object.assign(newItem, food); // Merge each food object into newItem
        });
        hasNestedArray = true;
      } else {
        newItem[key] = item[key];
      }
    }
    dataArr.push(newItem);
  });

  if (hasNestedArray) {
    return flaten(dataArr); // If there was a nested array, recursively flatten again
  } else {
    return dataArr; // Otherwise, return the flattened array
  }
}

console.log(flaten(message));
```
 **[⬆ Back to Top](#table-of-contents)**
---
7. ### Write a function to remove duplicate elements from array.
 ```js
let arr = [1, 2, 3, 4, 5, 3, 2, 3, 1, 4, 2];

function removeDuplicates(arr) {
  const sorted = arr.sort();
  for (let i = 0; i < sorted.length; i++) {
    if (arr[i] == arr[i + 1]) {
      sorted.splice(arr[i], 1);
      i--;
    }
  }
  return sorted;
}

console.log(removeDuplicates(arr)); // Output: [ 1, 2, 3, 4, 5 ]

```
---
 **[⬆ Back to Top](#table-of-contents)**
 
8. ### Find the largest two values of array.
```js
const arr = ['20','120','111','215','54','78'];

function largest(arr){
  const mutate = [...arr];
  const largestarr = [];
  
  while(largestarr.length < 2){
    let largestNum = mutate[0];
    let largestIndex = 0;
    
    for(let i = 1; i < mutate.length; i++){
      if(parseInt(mutate[i],10) > parseInt(largestNum,10)){
        largestNum = mutate[i];
        largestIndex = i;
      }
    }
    
    mutate.splice(largestIndex, 1);
    largestarr.push(largestNum);
  }
  
  return largestarr;
}

console.log(largest(arr));
```

 **[⬆ Back to Top](#table-of-contents)**
---
9. ### Write a program to print message after 1 sec delay
```js
function printMessagesWithDelay(messages) {
  messages.forEach((message, index) => {
    setTimeout(() => {
      console.log(message);
    }, index * 1000); // Delay increases with each message
  });
}

const messages = [
  "Message 1",
  "Message 2",
  "Message 3",
  "Message 4",
  "Message 5"
];

printMessagesWithDelay(messages);
```
 **[⬆ Back to Top](#table-of-contents)**
---
10. ### Output 1
 ```js
   getProjects().then(() => console.log('hi'));
      console.log('hello');
   ```
   The console.log('hello') statement will be executed first, followed by the .then() callback function (console.log('hi')).
This is because getProjects() is an asynchronous function that returns a Promise. When you call getProjects().then(), it schedules the execution of the callback function to be executed asynchronously after the promise returned by getProjects() resolves. Meanwhile, the console.log('hello') statement is synchronous and will be executed immediately.

**[⬆ Back to Top](#table-of-contents)**
---
11. ### Output 2
```js
await getProjects();
console.log('hello');
```
In JavaScript, when you use the await keyword, it pauses the execution of the code until the promise returned by the asynchronous function getProjects() resolves. This means that the code inside getProjects() will be executed first, and only after it completes will the console.log('hello') statement be executed. The output will be the result of getProjects() (assuming it returns something), followed by 'hello'

**[⬆ Back to Top](#table-of-contents)**
---
https://timesheet.synechron.com/submitTimesheet
