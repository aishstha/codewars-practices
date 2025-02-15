## Description

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example:
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) => returns "(123) 456-7890"

The returned format must be correct in order to complete this challenge. 
Don't forget the space after the closing parenthese!

**Kata's link**: [Create Phone Number](http://www.codewars.com/kata/create-phone-number/)

## Best Practices

**First:**
```js
function createPhoneNumber(numbers){
  var format = "(xxx) xxx-xxxx";
  
  numbers.forEach(element => {
        format = format.replace('x', element);
  })
  
  return format;
}
```

**Second:**
```js
function createPhoneNumber(numbers){
  return numbers.join('').replace(/(...)(...)(.*)/, '($1) $2-$3');
}
```

**Third:**
```js
function createPhoneNumber(numbers){
  numbers = numbers.join('');
  return '(' + numbers.substring(0, 3) + ') ' 
      + numbers.substring(3, 6) 
      + '-' 
      + numbers.substring(6);
}
```

**Fourth:**
```js
function createPhoneNumber(numbers){
  numbers.unshift("(");
  numbers.splice(4, 0, ")", " ");
  numbers.splice(9, 0, "-");
  return numbers.join("");
}
```

**Fifth:**
```js
function createPhoneNumber(numbers){
  return numbers.join('').replace(/(\d{3})(\d{3})(\d{4})/,'($1) $2-$3');
}
```

## My solutions
```js
function createPhoneNumber(numbers){
  let checkPhone = /^\(\d{3}\)\s{1}\d{3}\-{1}\d{4}/;
  let phoneString;  
  let len = numbers.length;
  
  let first = '(';
  let second = '';
  let third = '';

  for(let f = 0; f < 3; f++){
    first += numbers[f];
  }

  first += ') ';

  for(let s = 3; s < 6; s++){
    second += numbers[s];
  }
  
  second += '-';

  for(let t = 6; t < 10; t++){
    third += numbers[t];
  }

  phoneString = first + second + third;
  
  if(checkPhone.test(phoneString)){
    return phoneString;
  } 
}
```
