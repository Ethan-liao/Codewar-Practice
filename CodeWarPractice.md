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
#### Refactored solution
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


## Solution
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
## Question
In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

Example:

highAndLow("1 2 3 4 5"); // return "5 1"
highAndLow("1 2 -3 4 5"); // return "5 -3"
highAndLow("1 9 3 4 -5"); // return "9 -5"
## Solution
```
function highAndLow(numbers){\
 //refactored
let arr = numbers.split(' ').map(Number);

 return Math.max.apply(null,arr) +" " + Math.min.apply(null,arr);


//   let num = numbers.split(" ").map(Number);
//   let low = 1;
//   let high = 1;
//   console.log(num)
//    for (var i=0; i<num.length; i++){
//     if (num[i] > high)
//      high=num[i];
//     if (num[i]< low)
//      low=num[i];
//    }   

//  return high +" "+ low;
}
```
## Question
You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). You know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).
## Solution
```
let isValidWalk = (walk) => {
	let start=0;
	let counter =0;
  walk.forEach((x)=>{
  	 switch(x){
  	 	case 'n':
  	 					start+=1;
  	 					counter++;
  	 					break;
  	 	case 's':
  	 					start-=1;
  	 					counter++;
  	 					break;
  	 	case 'e':
  	 					start+=1;
  	 					counter++;
  	 					break;
  	 	case 'w':
  	 					start-=1;
  	 					counter++;
  	 					break;
  	 }
  })
  return start == 0 && counter == 10 ? true : false;
}
```

## Question
You will be given a number and you will need to return it as a string in Expanded Form. For example:

expandedForm(12); // Should return '10 + 2'
expandedForm(42); // Should return '40 + 2'
expandedForm(70304); // Should return '70000 + 300 + 4'
## Solution


```
let expandedForm = (num)=>{
  let newNum = num.toString().split('');
	let length = newNum.length;
	let result=[];
	for(i=0;i<newNum.length;i++ ){
		if(newNum[i]==='0'){
			length--
		} else {
			length--
			result.push(newNum[i]*Math.pow(10,length))
		}
	}
	return result.join(' + ')
}
```

## Question
Given an array, find the int that appears an odd number of times.

There will always be only one integer that appears an odd number of times.
## Solution
```
let findOdd = (arr)=> {
  let counter1=0;
  for(i=0;i<=arr.length;i++){
  	for(j=0;j<=arr.length;j++){
  		if(arr[i]==arr[j]){
  			counter1++
  		}
  	}
  	if(counter1%2 != 0){
  		return arr[i]
  	}
  }
}
```
## Question
square every digit of a number.

For example, if we run 9119 through the function, 811181 will come out.
## Solution

```
let squareDigits=(num)=>{
  let newNum = num.toString().split('')
  return parseInt(newNum.map((x)=>{
  	return Math.pow(x,2)
  }).join(''))
}
```

## Question
You need to swap the head and the tail of the specified array:

the head (the first half) of array moves to the end, the tail (the second half) moves to the start. The middle element (if it exists) leaves on the same position.

Return new array.

For example:

    [ 1, 2, 3, 4, 5 ]   =>  [ 4, 5, 3, 1, 2 ]
     \----/   \----/         
      head     tail
## Solution
```
let swapHeadAndTail=(arr)=>{
 let midPoint = Math.floor(arr.length/2);
 let tail = arr.slice(midPoint+1,arr.length);
 let head = arr.slice(0,midPoint);
 let result =[];
 if(arr.length<=2){
   return arr.reverse();
 } else if (arr.length%2==0){
 	 tail = arr.slice(midPoint,arr.length);
 	 return tail.concat(head)
 }
 else if(arr.length%2!==0){
   return tail.concat(arr[midPoint],head)
 }
}

#### Refactored solution
```
let swapHeadAndTail=(arr)=>{
 let midPoint =arr.length/2;
 let tail = arr.slice(-midPoint);
 let head = arr.slice(0,midPoint);
 return [...tail, ...arr.slice(midPoint,-midPoint), ...head]

}

## Question
A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence "The quick brown fox jumps over the lazy dog" is a pangram, because it uses the letters A-Z at least once (case is irrelevant).

Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.

## Solution
```
let alphabet =()=>{
	let abc = 'abcdefghijklmnopqrstuvwxyz'
	return abc.split('')
}

let checkArr=(letter,alphArr)=>{
	alphArr.map((el)=>{
		if(el === letter){
			alphArr.splice(alphArr.indexOf(el),1)
		}
	})
}

let isPangram=(string)=>{
  let strToBeCompared = string.toLowerCase().replace(/\s/g,'').split('')
  let abc=alphabet();
  for(i=0;i<strToBeCompared.length;i++){
  checkArr(strToBeCompared[i],abc)
  // console.log(strToBeCompared[i])
  }
  return abc.length == 0 ? true:false;
}

let str = "The quick brown fox jumps over the lazy dog."
let str = "This is not a pangram."
let str = 'abcdefeT'
isPangram(str)
```

## Question
here is an array with some numbers. All numbers are equal except for one. Try to find it!
```
findUniq([ 1, 1, 1, 2, 1, 1 ]) === 2
findUniq([ 0, 0, 0.55, 0, 0 ]) === 0.55
It’s guaranteed that array contains more than 3 numbers.
```
The tests contain some very huge arrays, so think about performance.

## Refactored Solution
```
let findUniq = (arr) => {
 arr.sort((a,b)=> a-b);
 return arr[0] == arr[1]?arr.pop():arr[0]
 }
```

## Solution
```
let findUniq = (arr) => {
  for(i=1;i<=arr.length;i++){
		if(arr[i] != arr[i-1] && arr[i] == arr[i+1] ){
		 	return arr[i-1];
		} else if(arr[i] == arr[i+1] && arr[i] != arr[i-1]){
			return arr[i+1]
		} else if(arr[i] != arr[i-1] && arr[i] != arr[i+1]){
      return arr[i]
      }
  }
}
```

## Question
You are having a BBQ, after the BBQ you are left with the rubbish. You have 3 recycling boxes:

Red: Plastics, Green: Glass, Blue: Card.

You will need to sort the rubbish according to the material and return the number of items in each box in the form of an array i.e [2,3,4] where 2 is the number of plastic items, 3 is the number of glass items and 4 is the number of card items. assume:

Plastics > 0, Glass < 0, Card = 0

## Solution
```
function recycleMe(recycle){
	let positive = 0,
			negative = 0,
			zero = 0;

	recycle.forEach((num) => {
			num > 0 ? positive++ : (num<0 ? negative++:zero++);
		})
	return [positive, negative, zero]
}

recycleMe([5,-9,0,6,-84,-95,15])
solution(3,3,1)
```

## Question
Convert number to roman numerals

## Solution

```
function convertToRoman(num) {
	let ones = ['I','II','III','IV','V','VI','VII','VIII','IX'];
	let tenth = ['X','XX','XXX','XL','L','LX','LXX','LXXX','XC'];
	let hundredth = ['C','CC','CCC','CD','D','DC','DCC','DCCC','CM'];
	let thousandth = ['M','MM','MMM','MMMM','MMMMM'];

	num = num.toString();
	let arr = num.split('');

	function checkTenth(value) {
		 return value[1] == '0'? tenth[value[0]-1] : tenth[arr[0]-1] + ones[arr[1]-1];
	}

	function checkHundredth(value) {
		for(i=1; i < value.length; i++) {
			return (value[i] == '0' && value[i+1] == '0') ? hundredth[value[0]-1] : value[i] == '0' ? hundredth[arr[0]-1] + ones[arr[2]-1] : hundredth[arr[0]-1] + tenth[arr[1]-1] + ones[arr[2]-1]
			}
		}


	function checkThousandth(value) {
		for(i=1; i < value.length; i++){
			if(value[i] == '0' && value[i+1] == '0' && value[i+2] == '0') {
				return thousandth[arr[0]-1]
			} else if(value[i] == '0' && value[i+1] == '0') {
					return thousandth[arr[0]-1]+ ones[arr[3]-1]
			} else if(value[i] == '0'){
					return thousandth[arr[0]-1] + tenth[arr[2]-1] + ones[arr[3]-1]
			} else if(value[i] !== '0'){
				return thousandth[arr[0]-1] + hundredth[arr[1]-1] + tenth[arr[2]-1] + ones[arr[3]-1]
			}
		}
	}


	function checkPlace(el) {
		let length = num.length;

		if(length == 1) {
			return ones[arr-1]
		} else if (length == 2) {
				return checkTenth(arr)
		}	else if (length == 3) {
				return checkHundredth(arr)
		} else if (length == 4) {
				return checkThousandth(arr)
		}
	}
	return checkPlace(num)
}

convertToRoman(3999)
// only up to 5999
```
