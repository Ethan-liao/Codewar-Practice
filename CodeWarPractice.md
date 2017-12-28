## Question
This time no story, no theory. The examples below show you how to write function accum:

 Examples:

accum("abcd");    // "A-Bb-Ccc-Dddd"

accum("RqaEzty"); // "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"

accum("cwAt");    // "C-Ww-Aaa-Tttt"

## Solution
```
function accum(s) {
 let newText=[];
 for(i=0;i<s.length;i++){
  newText.push(s[i].repeat((i+1)).toLowerCase());
 }
 return newText
 .map((x) => x[0].toUpperCase() + x.substring(1))
 .join('-');
}
```

## Question
Given two arrays, a1 and a2, sort the elements of a2 based on the first letters of elements in a1.

Example 1

var a1 = ['giraffe', 'orangutan', 'impala', 'elephant', 'rhino'];
var a2 = ['rattlesnake', 'eagle', 'geko', 'iguana', 'octopus'];

returns ['geko', 'octopus', 'iguana', 'eagle', 'rattlesnake']

## Solution
#### Solution 1
```
function getMiddle(s){
let length = s.length;
 	let center = (length/2);
  let nextText = center+1;
  if (length % 2 == 0){
  	return s.slice(center-1,nextText);
  	}
	else {
		return s.slice(center,center+1);		

	}
}
```
#### Refactored solution
```
function getMiddle(s)
{  
  let center = (s.length)/2;
  let odd =  s.slice(center, center+1);
  let even =  s.slice(center-1, center+1);
  return (s.length % 2) ? odd : even;
}
```

## Question

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

Note: for this kata y isn't considered a vowel.

## Solution

function disemvowel(str){
   return str.replace(/[aeiou]/gi,'')
}

disemvowel("This website is for losers LOL!");



## Question
Implement the method isSortedAndHow, which accepts an array of integers, and returns one of the following:

'yes, ascending' - if the numbers in the array are sorted in an ascending way
'yes, descending' - if the numbers in the array are sorted in a descending way
'no'
You can assume the array will always be valid, and there will always be one correct answer.

## Solution
```
function isSortedAndHow(array) {
	let ascCount = 0;
	let descCount = 0;
	if (array.length < 2) {
		return 'Error, there needs to be more than one digit';
	}
	for (i = 0; i <= array.length-1; i++) {
		if (array[i] <= array[i + 1] ) {
			ascCount++;
			if (ascCount == array.length-1) {
				return 'yes, ascending';
			}
		} else if (array[i] >= array[i + 1] ) {
			descCount++;
			console.log(array[i]);
			if (descCount == array.length-1) {
				return 'yes, descending';

			}
		} else {
			return 'no';
		}
	}
}
// isSortedAndHow([4])
// isSortedAndHow([3, 4, 5]);
// isSortedAndHow([15, 7, 3, -8])
// isSortedAndHow([4, 2, 30])
```
## Question
As a part of this Kata, you need to create a function that when provided with a triplet, returns the index of the numerical element that lies between the other two elements.

## Solution
```
let gimme =  (inputArray) => {
	let sorted = inputArray.concat().sort((a,b)=>{return a-b})[1];
		return inputArray.indexOf(sorted);
};

// gimme([5, 1, 22])
// gimme([5,10,14])

```

## Question
In mathematics, the factorial of a non-negative integer n, denoted by n!, is the product of all positive integers less than or equal to n. For example: 5! = 5 * 4 * 3 * 2 * 1 = 120. By convention the value of 0! is 1.

Write a function to calculate factorial for a given input. If input is below 0 or above 12 throw an exception of type RangeError (JavaScript).
## Solution
```
let factorial=(n) => {
	if(n<0 || n>12){
		throw new RangeError("Parameter must be between 0 and 12")
	}
 return n ? n*factorial(n-1):1;
}
```
## Question
Write a reverseWords function that accepts a string a parameter, and reverses each word in the string. Any spaces in the string should be retained.
## Solution
```
let reverseWords = (str)=>{
  let arr= str.split(' ');
  return  arr.map((x)=>{
  	return x.split('').reverse().join('');
   }).join(' ')
}
```
reverseWords("This is an example!")

## Question
ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.
If the function is passed a valid PIN string, return true, else return false.
## Solution
```
let validatePIN = (pin)=>{
  if (isNaN(pin) == true || pin.match(/\D+/g)!=null)
   return false;
  else if (pin.length == 4 || pin.length == 6)
   return true;
  else return false;
}
```
Refactored
```
let validatePIN = (pin)=>{
  return (/^(\d{4}|\d{6})$/).test(pin);
}
```

## Question
Write a function named sumDigits which takes a number as input and returns the sum of the absolute value of each of the number's decimal digits.

## Solution
```
let sumDigits = (number) => {
		let arr = number.toString().split('');
		let sum=0;
		arr.map((x) => {
			if( (/\d/g).test(x) ){
				sum +=parseInt(x)
			}})
		return sum;
}
```
## Question
We will be given the sale price (discounted price), and the sale percentage, our job is to figure out the original price.

## Solution
```
let discoverOriginalPrice = (discountedPrice, salePercentage)=>{
 return parseFloat((discountedPrice/((100- salePercentage)/100)).toFixed(2));
}
```
## Question
Given a string and an array of integers representing indices, capitalize all letters at the given indices.

For example:

capitalize("abcdef",[1,2,5]) = "aBCdeF"
capitalize("abcdef",[1,2,5,100]) = "aBCdeF". There is no index 100.
The input will be a lowercase string with no spaces and an array of digits.
## Solution
```
let capitalize = (str,arr) =>{
	  let newString = str.split('');
	  	for(i=0;i<arr.length; i++){
	  		if (arr[i] <= newString.length){
	  				newString.splice(arr[i],1, newString[arr[i]].toUpperCase())
	  		}
	  	} return newString.join('')
};
```
## Question
Given two numbers and an arithmetic operator (the name of it, as a string), return the result of the two numbers having that operator used on them.

a and b will both be positive integers, and a will always be the first number in the operation, and b always the second.

The four operators are "add", "subtract", "divide", "multiply".


## Sollution
```
let arithmetic = (a, b, operator) => {
	let result ={
		'add': (x,y) => {return x+y},
		'subtract': (x,y) => {return x-y},
		'divide': (x,y) => {return x/y},
		'multiply': (x,y) => {return x*y},
	} ;
	return result[operator](a,b)
}
```
