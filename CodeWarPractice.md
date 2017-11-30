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
