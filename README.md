# Code Wars Challenges

### 1. Stop gninnipS My sdroW! **6 kyu**

Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

*Examples: *

    spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" spinWords( "This is a test") => returns "This is a test" spinWords( "This is another test" )=> returns "This is rehtona test"

*My solution:*
```javascript
    function spinWords(word) {
        return word.split(' ').map(word => {
        if (word.length >= 5) {
            return word.split('').reverse().join('')
        }
        return word;
    }).join(' ')
}
```
---
### 2. Sum of Digits / Digital Root **6 kyu**
Digital root is the recursive sum of all the digits in a number.

Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.
 
*Examples:*

    16  -->  1 + 6 = 7
    942  -->  9 + 4 + 2 = 15  -->  1 + 5 = 6
    132189  -->  1 + 3 + 2 + 1 + 8 + 9 = 24  -->  2 + 4 = 6
    493193  -->  4 + 9 + 3 + 1 + 9 + 3 = 29  -->  2 + 9 = 11  -->  1 + 1 = 2

*My solution:*
```javascript
    function digital_root(num) {
    const toStrSplit = num.toString().split('').reduce((a, b) => parseInt(a) + parseInt(b));
    if (toStrSplit.toString().length > 1) {
        const secondCalc = toStrSplit.toString().split('').reduce((a, b) => parseInt(a) + parseInt(b));
        if (secondCalc.toString().length > 1) {
            return secondCalc.toString().split('').reduce((a, b) => parseInt(a) + parseInt(b))
        } else {
            return secondCalc;
        }
    } else {
        return parseInt(toStrSplit);
    }
}
```
___
## 3. Mumbling **7 kyu**
This time no story, no theory. The examples below show you how to write function accum:

*Examples:*

    accum("abcd") -> "A-Bb-Ccc-Dddd"
    accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
    accum("cwAt") -> "C-Ww-Aaa-Tttt"

The parameter of accum is a string which includes only letters from a..z and A..Z.

*My solution:*
```javascript
function accum(str) {
    const repeated = str.split('').map((char, i) => char = char.repeat(i + 1))

    return repeated.map(char => char.charAt(0).toUpperCase() + char.slice(1).toLowerCase()).join('-')
}
```
---

## 4.Disemvowel Trolls **7 kyu**

Trolls are attacking your comment section!

A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

Note: for this kata **y** isn't considered a vowel.

*My solution:*
```javascript
function disemvowel(str) {
   return str.replace(/[a|e|i|o|u]/gi, '')
}
```

---
## 5.List Filtering **7 kyu**
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

*Example:*

    filter_list([1,2,'a','b']) == [1,2]
    filter_list([1,'a','b',0,15]) == [1,0,15]
    filter_list([1,2,'aasf','1','123',123]) == [1,2,123]

*My solution:*
```javascript
function filter_list(list) {
    const arr = [];
    return list.filter(l => {
        if (typeof l != 'number') {
            return
        }
        arr.push(l)
        return arr
    })
}
```

---

## 6. Highest and Lowest **7 kyu**
In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

*Example:*

    highAndLow("1 2 3 4 5");  // return "5 1"
    highAndLow("1 2 -3 4 5"); // return "5 -3"
    highAndLow("1 9 3 4 -5"); // return "9 -5"

*Notes:*

All numbers are valid Int32, no need to validate them.
There will always be at least one number in the input string.
Output string must be two numbers separated by a single space, and highest number is first.

*My solution:*
```javascript
function highAndLow(numbers) {
    const intigers = [];
    if (numbers.split(' ').length != 1) {

        numbers.split(' ').forEach(num => intigers.push(+num));
        const sort = intigers.sort((a, b) => a - b)
        // console.log(sort);
        const maxNum = sort.splice(-1)
        const minNum = sort[0]
        // console.log('max: ' + maxNum);
        // console.log('min: ' + minNum);
        return maxNum + ' ' + minNum
    } else {
        return +numbers.split(' ') + ' ' + numbers.split(' ')
    }
}
```
---

## 7. Persistent Bugger **6 kyu**

Write a function, *persistence*, that takes in a positive parameter num and returns its multiplicative persistence, which is the number of times you must multiply the digits in num until you reach a single digit.

*For example:*

    persistence(39) === 3 // because 3*9 = 27, 2*7 = 14, 1*4=4
                        // and 4 has only one digit

    persistence(999) === 4 // because 9*9*9 = 729, 7*2*9 = 126,
                            // 1*2*6 = 12, and finally 1*2 = 2

    persistence(4) === 0 // because 4 is already a one-digit number

*My solution:*

```javascript
let count = 0;
function persistence(num) {
    if (num.toString().length > 1) {
        persistence(num.toString().split('').map(Number).reduce((a, b) => a * b))
        count++;
        return count;
    } else {
      count = 0;
        return count;
    }
}
```
---

## 8. Your order, please **6 kyu**

Your task is to sort a given string. Each word in the string will contain a single number. This number is the position the word should have in the result.

Note: Numbers can be from 1 to 9. So 1 will be the first word (not 0).

If the input string is empty, return an empty string. The words in the input String will only contain valid consecutive numbers.

*Examples:*

    "is2 Thi1s T4est 3a"  -->  "Thi1s is2 3a T4est"
    "4of Fo1r pe6ople g3ood th5e the2"  -->  "Fo1r the2 g3ood 4of th5e pe6ople"
    ""  -->  ""

*My solution:*
```javascript
function order(words) {
    if (words === '') return words;

    const arr = [];

    const splitedWords = words.split(' ');

    splitedWords.forEach(word => {
        const obj = {
            text: word,
            place: word.match(/[0-9]/g).join('')
        };
        arr.push(obj);
        return arr;
    });

    arr.forEach(word => {
        return splitedWords[word.place - 1] = word.text;
    });

    return splitedWords.join(' ');
}
```
---

## 9. RGB To Hex Conversion **5 kyu**
The rgb function is incomplete. Complete it so that passing in RGB decimal values will result in a hexadecimal representation being returned. Valid decimal values for RGB are 0 - 255. Any values that fall out of that range must be rounded to the closest valid value.

Note: Your answer should always be 6 characters long, the shorthand with 3 will not work here.

The following are examples of expected output values:

    rgb(255, 255, 255) // returns FFFFFF
    rgb(255, 255, 300) // returns FFFFFF
    rgb(0,0,0) // returns 000000
    rgb(148, 0, 211) // returns 9400D3

*My solution:*

``` javascript
function rgb(r, g, b) {
    return [convertToHex(r), convertToHex(g), convertToHex(b)].join('')
}
function convertToHex(num) {
    if (num < 0 || num === 0) {
        num = 0;
        return num.toString(16) + '0'
    } else if (num > 255) {
        num = 255;
        return num.toString(16).toUpperCase()
    } else {
        if (num.toString(16).length === 1) {
            return '0' + num.toString(16).toUpperCase()
        }
        return num.toString(16).toUpperCase()
    }
}
```
---

## 10. Bit Counting **6 kyu**

Write a function that takes an integer as input, and returns the number of bits that are equal to one in the binary representation of that number. You can guarantee that input is non-negative.

Example: The binary representation of *1234* is *10011010010*, so the function should return *5* in this case

*My solution:*

```javascript
var countBits = function(n) {
  if (n === 0) return 0;
  return n.toString(2).match(/[1]/g).length;
};
```
---

## 11. Highest Scoring Word **6 kyu**

Given a string of words, you need to find the highest scoring word.

Each letter of a word scores points according to its position in the alphabet: *a = 1, b = 2, c = 3* etc.

You need to return the highest scoring word as a string.

If two words score the same, return the word that appears earliest in the original string.

All letters will be lowercase and all inputs will be valid.

*My solution:*
```javascript
function high(x) {
    const words = x.split(' ');
    const arr = [];
    let longestWord;

    words.forEach(word => {
        let eachWordSplit = word.split('');
        const eachWordScore = eachWordSplit.map(w => {
            return w.charCodeAt() - 97 + 1;
        })
        const obj = {
            value: eachWordScore.reduce((a, b) => a + b),
            text: word
        }
        return arr.push(obj);

    });

    const values = arr.map(a => {
        return a.value;
    })

    const sortedVal = values.sort((a, b) => a - b);
    const longestInArray = sortedVal.slice(-1).toString();

     arr.forEach(array => {
        if (array.value.toString() != longestInArray) return;
        longestWord = array.text;
        return longestWord;
    })
    return longestWord;
}
```
---

## 12. Convert A Hex String To RGB **5 kyu**

When working with color values it can sometimes be useful to extract the individual red, green, and blue (RGB) component values for a color. Implement a function that meets these requirements:

    Accepts a case-insensitive hexadecimal color string as its parameter (ex. *"#FF9933"* or *"#ff9933"*)

    Returns an object with the structure *{r: 255, g: 153, b: 51}* where r, g, and b range from 0 through 255

Note: your implementation does not need to support the shorthand form of hexadecimal notation (ie *"#FFF"*)

*Example:*

    "#FF9933" --> {r: 255, g: 153, b: 51}


``` javascript
function hexStringToRGB(hexString) {
    const hex = hexString.match(/[a-z0-9]/gi);
    const arr = [];


    let i = 0;
    while (i < hex.length) {
        arr.push(hex.slice(i, i + 2))
        i += 2
    }

    const joinedArr = arr.map(val => val.join('').toLowerCase());

    const endObj = {
        r: rgbVal(joinedArr[0]),
        g: rgbVal(joinedArr[1]),
        b: rgbVal(joinedArr[2])
    }
    return endObj;
}
function rgbVal(hex) {
    if (hex === '00') return hex = 0;
    for (let i = 0; i <= 255; i++) {
        if (i.toString(16) === hex) {
            return i;
        }
    }
}
```
---

## 13. The Hashtag Generator **5 kyu**
The marketing team is spending way too much time typing in hashtags.
Let's help them with our own Hashtag Generator!

*Here's the deal:*

    It must start with a hashtag (#).

    All words must have their first letter capitalized.

    If the final result is longer than 140 chars it must return false.

    If the input or the result is an empty string it must return false.

*Examples:*

    " Hello there thanks for trying my Kata"  =>  "#HelloThereThanksForTryingMyKata"
    "    Hello     World   "                  =>  "#HelloWorld"
    ""                                        =>  false


*My solution:*

```javascript
function generateHashtag(str) {
    if (str === ' ' || str === '') return false;

    const joined = str.split(' ').map(word => word.charAt(0).toUpperCase() + word.slice(1).toLowerCase()).join('');

    if (joined.length >= 140 || joined === '') {
        return false
    } else {
        return '#' + joined
    }
}
```
---

## 14. Regex Password Validation **5 kyu**

*Description:*

You need to write regex that will validate a password to make sure it meets the following criteria:

At least six characters long
contains a lowercase letter
contains an uppercase letter
contains a number
Valid passwords will only be alphanumeric characters.

*My Solution:*

```javascript
function validate(password) {
    if (password.length < 6) return false;

    const validateLowercase = (password.search(/[a-z]/) > -1);
    const validateUpperCase = (password.search(/[A-Z]/) > -1);
    const validateNum = (password.search(/[0-9]/) > -1);
    const noSymOrEmpty = (password.search(/[.; | ^\s+$]/)) > -1;

    if (validateLowercase === true && validateUpperCase === true && validateNum === true && noSymOrEmpty === false) {
        return true;

    } else {
        return false;
    }
}
```
---

## 15. Validate my Password **6 kyu**

I will give you a string. You respond with "VALID" if the string meets the requirements or "INVALID" if it does not.

Passwords must abide by the following requirements:

    More than 3 characters but less than 20.

    Must contain only alphanumeric characters.

    Must contain letters and numbers.

*My solution:*

``` javascript
function validPass(password) {
    const validation = /^[A-Za-z0-9]{3,20}$/.test(password) && /[a-z]+/gi.test(password) && /[0-9]+/.test(password)

    return validation ? 'VALID' : 'INVALID';
}
```
---

## 16. Regex validate PIN code **7 kyu**

*Description:*

ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.

If the function is passed a valid PIN string, return true, else return false.

*Examples*

    "1234"   -->  true
    "12345"  -->  false
    "a234"   -->  false

*My solution:*

```javascript
function validatePIN (pin) {
  return /^[\d]{4,4}$/.test(pin) || /^[\d]{6,6}$/.test(pin);
}
```
---

## 17.Sort Numbers **7 kyu**


Finish the solution so that it sorts the passed in array of numbers. If the function passes in an empty array or null/nil value then it should return an empty array.

*For example:*

    solution([1, 2, 10, 50, 5]); // should return [1,2,5,10,50]
    solution(null); // should return []

*My solution:*

``` javascript
function solution(nums){
  if(nums === null) return [];
  return nums.sort((a,b)=> a-b);
}
```
---

## 18. Reversed Words **8 kyu**

Complete the solution so that it reverses all of the words within the string passed in.

*Example:*

    reverseWords("The greatest victory is that which requires no battle")
    // should return "battle no requires which that is victory greatest The"


*My Solution:*

``` javascript
function reverseWords(str){
  return str.split(' ').reverse().join(' ');
}
```
---
## 19. Vowel Count **7 kyu**

Return the number (count) of vowels in the given string.

We will consider *a, e, i, o, u* as vowels for this Kata (but not *y*).

The input string will only consist of lower case letters and/or spaces.

*My Solution:*

``` javascript
function getCount(str) {
  const vowels = str.match((/[aeiou]/gi));
    return vowels != null ? vowels.length : 0;
}
```
---
## 20. Multiples of 3 or 5 **6 kyu**

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

    Note: If the number is a multiple of both 3 and 5, only count it once. Also, if a number is negative, return 0(for languages that do have them)


*My Solution:*

``` javascript
function solution(number){
  if (number <= 0) return 0;
    const arr = [];
    for (let i = 0; i < number; i++) {
        if (i % 3 === 0) {
            arr.push(i)
        } else if (i % 5 === 0) {
            arr.push(i)
        }
    }
    return arr.reduce((a, b) => a + b);
}
```
---

## 21. Get the Middle Character **7 kyu**

You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.

*Examples:*

    Kata.getMiddle("test") should return "es"

    Kata.getMiddle("testing") should return "t"

    Kata.getMiddle("middle") should return "dd"

    Kata.getMiddle("A") should return "A"

*Input*

A word (string) of length 0 < str < 1000 (In javascript you may get slightly more than 1000 in some test cases due to an error in the test cases). You do not need to test for this. This is only here to tell you that you do not need to worry about your solution timing out.

*Output*

The middle character(s) of the word represented as a string.

*My Solution:*

``` javascript
function getMiddle(s) {
    const strLeng = s.length;
    let middleIndex;
    if (strLeng % 2 === 0) {
        middleIndex = Math.floor(strLeng / 2)
       return s[middleIndex - 1] + s[middleIndex]
    } else {
        middleIndex = Math.floor(strLeng / 2)
        return s[middleIndex]
    }
}
```
---

## 22. Who likes it? **6 kyu**

You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:

    likes [] -- must be "no one likes this"
    likes ["Peter"] -- must be "Peter likes this"
    likes ["Jacob", "Alex"] -- must be "Jacob and Alex like this"
    likes ["Max", "John", "Mark"] -- must be "Max, John and Mark like this"
    likes ["Alex", "Jacob", "Mark", "Max"] -- must be "Alex, Jacob and 2 others like this"

For 4 or more names, the number in and 2 others simply increases.

*My Solution:*

``` javascript
function likes(str) {
    if (str.length === 0) return 'no one likes this';

    let arrLikes = [];
    if (str.length === 2) {
        return `${str[0]} and ${str[1]} like this`
    } else if (str.length <= 3) {
        for (let i = 0; i < str.length; i++) {
            arrLikes.push(str[i])
        }
    } else if (str.length >= 4) {
        return `${str[0]}, ${str[1]} and ${str.length - 2} others like this`
    }
    if (arrLikes.length > 1) {
        arrLikes.splice(arrLikes.length - 1, 0, 'and')
    }
    return (arrLikes.length === 1 ? `${arrLikes.join('')} likes this` : `${arrLikes.join(', ')} like this`).replace('and,', 'and').replace(', and', ' and');
}
```
---

## 23. Square Every Digit **7 kyu**

Welcome. In this kata, you are asked to square every digit of a number and concatenate them.

For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

    Note: The function accepts an integer and returns an integer


*My Solution:*

``` javascript
function squareDigits(num) {
    return +num.toString().split('').map(num => {
        return Math.pow(num, 2)
    }).join('')
}
```
---

## 24. Find The Parity Outlier **6 kyu**

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.

*Examples*

    [2, 4, 0, 100, 4, 11, 2602, 36]
    Should return: 11 (the only odd number)

    [160, 3, 1719, 19, 11, 13, -21]
    Should return: 160 (the only even number)

*My Solution:*

``` javascript
function findOutlier(integers) {
    const even = [];
    const odd = [];
    integers.forEach(num => {
        if (num % 2 === 0) {
            even.push(num);
        } else {
            odd.push(num);
        }
    })
    return even.length === 1 ? +even : +odd
}
```
---

## 25. Replace With Alphabet Position **6 kyu**

Welcome.

In this kata you are required to, given a string, replace every letter with its position in the alphabet.

If anything in the text isn't a letter, ignore it and don't return it.

"a" = 1, "b" = 2, etc.

*Example*

    alphabetPosition("The sunset sets at twelve o' clock.")
    Should return "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11" (as a string)

*My Solution:*

``` javascript
function alphabetPosition(text) {
  if (text.toLowerCase().match(/[a-z]/gi) === null) { 
    return '' ;
  } else {
        return text.toLowerCase().match(/[a-z]/gi).map(char => char.charCodeAt() - 97 + 1).join(' ');
    }
}
```
---

## 26. Dubstep **6 kyu**

Polycarpus works as a DJ in the best Berland nightclub, and he often uses dubstep music in his performance. Recently, he has decided to take a couple of old songs and make dubstep remixes from them.

Let's assume that a song consists of some number of words (that don't contain WUB). To make the dubstep remix of this song, Polycarpus inserts a certain number of words "WUB" before the first word of the song (the number may be zero), after the last word (the number may be zero), and between words (at least one between any pair of neighbouring words), and then the boy glues together all the words, including "WUB", in one string and plays the song at the club.

For example, a song with words "I AM X" can transform into a dubstep remix as "WUBWUBIWUBAMWUBWUBX" and cannot transform into "WUBWUBIAMWUBX".

Recently, Jonny has heard Polycarpus's new dubstep track, but since he isn't into modern music, he decided to find out what was the initial song that Polycarpus remixed. Help Jonny restore the original song.

*Input*

The input consists of a single non-empty string, consisting only of uppercase English letters, the string's length doesn't exceed 200 characters

*Output*

Return the words of the initial song that Polycarpus used to make a dubsteb remix. Separate the words with a space.

*Examples*

    songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB")
    // =>  WE ARE THE CHAMPIONS MY FRIEND

*My Solution:*

``` javascript
function songDecoder(song){
   const songName = song.replace((/WUB/gi), ' ').split('')
    return songName.join('').replace((/\s\s+/g), ' ').replace(/^\s+/g, '').replace(/\s+$/, '')
}
```
---

## 27. Unique In Order **6 kyu**

Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.

*For example:*

    uniqueInOrder('AAAABBBCCDAABBB') == ['A', 'B', 'C', 'D', 'A', 'B']
    uniqueInOrder('ABBCcAD')         == ['A', 'B', 'C', 'c', 'A', 'D']
    uniqueInOrder([1,2,2,3,3])       == [1,2,3]

*My Solution:*

``` javascript
function uniqueInOrder(str) {
    const arr = [];
    for (let i = 0; i < str.length; i++) {
        if (str[i] !== str[i + 1]) {
            arr.push(str[i])
        }
    }
    return arr
}
```
---

## 28. Credit Card Mask **7 kyu**

Usually when you buy something, you're asked whether your credit card number, phone number or answer to your most secret question is still correct. However, since someone could look over your shoulder, you don't want that shown on your screen. Instead, we mask it.

Your task is to write a function maskify, which changes all but the last four characters into '#'.

*Examples*

    maskify("4556364607935616") == "############5616"
    maskify(     "64607935616") ==      "#######5616"
    maskify(               "1") ==                "1"
    maskify(                "") ==                 ""

    // "What was the name of your first pet?"
    maskify("Skippy")                                   == "##ippy"
    maskify("Nananananananananananananananana Batman!") == "####################################man!"

*My Solution:*

``` javascript
function maskify(cc) {
    const xxx = cc.replace(/[\w\d\s]/gi, '#').split('')
    xxx[xxx.length - 1] = cc[cc.length - 1]
    xxx[xxx.length - 2] = cc[cc.length - 2]
    xxx[xxx.length - 3] = cc[cc.length - 3]
    xxx[xxx.length - 4] = cc[cc.length - 4]
    return xxx.join('')
}
```
---

## 29. Counting Duplicates **6 kyu**

Count the number of Duplicates
Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

*Example*

    "abcde" -> 0 # no characters repeats more than once
    "aabbcde" -> 2 # 'a' and 'b'
    "aabBcde" -> 2 # 'a' occurs twice and 'b' twice (`b` and `B`)
    "indivisibility" -> 1 # 'i' occurs six times
    "Indivisibilities" -> 2 # 'i' occurs seven times and 's' occurs twice
    "aA11" -> 2 # 'a' and '1'
    "ABBA" -> 2 # 'A' and 'B' each occur twice

*My Solution:*

``` javascript
function duplicateCount(text) {
    const arr = [];
    const arr2 = [];

    const sortedStr = text.toLowerCase().split('').sort();


    for (let i = 0; i < sortedStr.length; i++) {
        if (sortedStr[i] === sortedStr[i + 1]) {
            arr.push(sortedStr[i]);
        }
    }

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== arr[i + 1]) {
            arr2.push(arr[i]);
        }
    }
    return arr2.length;
}
```
---

## 30. You're a square! **7 kyu**

*A square of squares*

You like building blocks. You especially like building blocks that are squares. And what you even like more, is to arrange them into a square of square building blocks!

However, sometimes, you can't arrange them into a square. Instead, you end up with an ordinary rectangle! Those blasted things! If you just had a way to know, whether you're currently working in vain… Wait! That's it! You just have to check if your number of building blocks is a perfect square.

*Task*

Given an integral number, determine if it's a square number:

    In mathematics, a square number or perfect square is an integer that is the square of an integer; in other words, it is the product of some integer with itself.

The tests will always use some integral number, so don't worry about that in dynamic typed languages.

*Examples*

    -1  =>  false
    0  =>  true
    3  =>  false
    4  =>  true
    25  =>  true
    26  =>  false

*My Solution:*

``` javascript
var isSquare = function(n){
  return Math.sqrt(n) % 1 === 0 ? true : false
}
```
---

## 31. Array.diff **6 kyu**

Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

It should remove all values from list a, which are present in list b.

    arrayDiff([1,2],[1]) == [2]
    If a value is present in b, all of its occurrences must be removed from the other:

    arrayDiff([1,2,2,2,3],[2]) == [1,3]

*My Solution:*

``` javascript
function arrayDiff(a, b) {
   return a.filter(char => {
        return !b.includes(char)
})}
```
---

## 32. IQ Test **6 kyu**

Bob is preparing to pass IQ test. The most frequent task in this test is to find out which one of the given numbers differs from the others. Bob observed that one number usually differs from the others in evenness. Help Bob — to check his answers, he needs a program that among the given numbers finds one that is different in evenness, and return a position of this number.

 Keep in mind that your task is to help Bob solve a real IQ test, which means indexes of the elements start from 1 (not 0)

*Examples:*

    iqTest("2 4 7 8 10") => 3 // Third number is odd, while the rest of the numbers are even

    iqTest("1 2 1 1") => 2 // Second number is even, while the rest of the numbers are odd


*My Solution:*

``` javascript
function iqTest(nums) {
    const arr = [];
    const arrEven = [];
    const arrOdd = [];

    const numArr = nums.split(' ').map(Number);
    
    numArr.forEach(num => {
        if (num % 2 === 0) {
            arr.push(true);
            arrEven.push(num);
        } else {
            arr.push(false);
            arrOdd.push(num);
        }
        return arr
    })

    if (arrEven.length > arrOdd.length) {
        return arr.indexOf(false) + 1
    } else {
        return arr.indexOf(true) + 1
    }
}
```
---

## 33. Find the unique number **6 kyu**

There is an array with some numbers. All numbers are equal except for one. Try to find it!

    findUniq([ 1, 1, 1, 2, 1, 1 ]) === 2
    findUniq([ 0, 0, 0.55, 0, 0 ]) === 0.55

It’s guaranteed that array contains at least 3 numbers.

The tests contain some very huge arrays, so think about performance.


*My Solution:*

``` javascript
function findUniq(arr) {
    const sorted = arr.sort((a, b) => a - b)
    if (sorted[0] === sorted[1]) {
        return sorted[sorted.length - 1]
    } else {
        return sorted[0]
    }
}
```
---

## 34. Sum of positive **8 kyu**

You get an array of numbers, return the sum of all of the positives ones.

*Example* 

    [1,-4,7,12] => 1 + 7 + 12 = 20

Note: if there is nothing to sum, the sum is default to 0.

*My Solution:*

``` javascript
function positiveSum(arr) {
    if (arr.length === 0) return 0;

    const positiveNums = arr.filter(num => {
        if (num > 0) {
            return num
        }
    })

    if (positiveNums.length !== 0) {
        return positiveNums.reduce((a, b) => a + b)
    } else {
        return 0
    }
}
```
---

## 35. Remove First and Last Character **8 kyu**

It's pretty straightforward. Your goal is to create a function that removes the first and last characters of a string. You're given one parameter, the original string. You don't have to worry with strings with less than two characters.

*My Solution:*

``` javascript
function removeChar(str){
return str.split('').slice(1, -1).join('');
};
```
---

## 36. Remove String Spaces **8 kyu**

Simple, remove the spaces from the string, then return the resultant string.

*My Solution:*

``` javascript
function noSpace(x){
  return x.replace(/\s+/g, '').trim()
}
```
---

## 37. Convert string to camel case **6 kyu**

Complete the method/function so that it converts dash/underscore delimited words into camel casing. The first word within the output should be capitalized only if the original word was capitalized (known as Upper Camel Case, also often referred to as Pascal case).

*Examples*

    toCamelCase("the-stealth-warrior") // returns "theStealthWarrior"

    toCamelCase("The_Stealth_Warrior") // returns "TheStealthWarrior"

*My Solution:*

``` javascript
function toCamelCase(str) {
    const splited = str.split('');

    for (let i = 0; i < splited.length; i++) {
        if (splited[i] === '-' || splited[i] === '_') {
            splited[i + 1] = splited[i + 1].toUpperCase();
            splited.splice(i, 1)
        }
    }

    return splited.join('')
}
```
---

## 40. Sort the odd **6 kyu**

You have an array of numbers.
Your task is to sort ascending odd numbers but even numbers must be on their places.

Zero isn't an odd number and you don't need to move it. If you have an empty array, you need to return it.

*Example*

    sortArray([5, 3, 2, 8, 1, 4]) == [1, 3, 2, 8, 5, 4]

*My Solution:*

``` javascript
function sortArray(nums) {
    
    const evenArr = [];
    const oddArr = [];

    nums.forEach((num, index) => {
        let objData = {
            'index': index,
            'value': num,
        }
        
        if (num % 2 !== 0) {
            oddArr.push(num)
        } else {
            evenArr.push(objData)
        }
    })

    const sortedOdd = oddArr.sort((a, b) => a - b)

    evenArr.forEach(even => {
        return sortedOdd.splice(even.index, 0, even.value)
    })
    return sortedOdd
}
```
---

## 41. Format a string of names like 'Bart, Lisa & Maggie'. **6 kyu**

Given: an array containing hashes of names

Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

*Example:*

    list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])
    // returns 'Bart, Lisa & Maggie'

    list([ {name: 'Bart'}, {name: 'Lisa'} ])
    // returns 'Bart & Lisa'

    list([ {name: 'Bart'} ])
    // returns 'Bart'

    list([])
    // returns ''

Note: all the hashes are pre-validated and will only contain A-Z, a-z, '-' and '.'.

*My Solution:*

``` javascript
function list(namesArr) {
    if (namesArr.length === 0) return ''
    if (namesArr.length === 1) {
        return namesArr[0].name
    } else if (namesArr.length === 2) {
        return namesArr[0].name + ' & ' + namesArr[1].name
    } else {
        const names = namesArr.map(n => n.name).join(', ');
        const reversed = names.split(' ').reverse().join(' ')
        
        const addAnd = reversed.replace(/[\s]/, ' & ').replace(/(,\s)/, ' ')
        const revAgain = addAnd.split(' ').reverse().join(' ')
        return revAgain;
    }
}
```
---

## 42. Simple validation of a username with regex **8 kyu**

Write a simple regex to validate a username. Allowed characters are:

    lowercase letters,
    numbers,
    underscore

    Length should be between 4 and 16 characters (both included).

*My Solution:*

``` javascript
function validateUsr(username) {
    const validate = /^[a-z\d_]{4,16}$/g;
    return validate.test(username)
}
```
---

## 43. Regex count lowercase letters **8 kyu**

Your task is simply to count the total number of lowercase letters in a string.

*Examples*

    lowercaseCount("abc"); ===> 3

    lowercaseCount("abcABC123"); ===> 3

    lowercaseCount("abcABC123!@€£#$%^&*()_-+=}{[]|\':;?/>.<,~"); ===> 3

    lowercaseCount(""); ===> 0;

    lowercaseCount("ABC123!@€£#$%^&*()_-+=}{[]|\':;?/>.<,~"); ===> 0

    lowercaseCount("abcdefghijklmnopqrstuvwxyz"); ===> 26

*My Solution:*

``` javascript
function lowercaseCount(str) {
    const count = str.match(/[a-z]/g)
    if (count === null) return 0
    return count.length
}

```
---

## 44. Complementary DNA **7 kyu**

Deoxyribonucleic acid (DNA) is a chemical found in the nucleus of cells and carries the "instructions" for the development and functioning of living organisms.

If you want to know more http://en.wikipedia.org/wiki/DNA

In DNA strings, symbols *"A"* and *"T"* are complements of each other, as *"C"* and *"G"*. You have function with one side of the DNA (string, except for Haskell); you need to get the other complementary side. DNA strand is never empty or there is no DNA at all (again, except for Haskell).

More similar exercise are found here http://rosalind.info/problems/list-view/ (source)

    DNAStrand ("ATTGC") // return "TAACG"

    DNAStrand ("GTAT") // return "CATA" 

*My Solution:*

``` javascript
function DNAStrand(dna) {
    return dna.split('').map(char => {
        if (char === 'A') {
            return char = 'T'
        }
        if (char === 'T') {
            return char = 'A'
        }
        if (char === 'C') {
            return char = 'G'
        }
        if (char === 'G') {
            return char = 'C'
        }
    }).join('');
}
```
---

## 45. String repeat **8 kyu**

Write a function called repeat_str which repeats the given string src exactly count times.

    repeatStr(6, "I") // "IIIIII"
    repeatStr(5, "Hello") // "HelloHelloHelloHelloHello"

*My Solution:*

``` javascript
function repeatStr (n, s) {
  return s.repeat(n);
}
```
---

## 46. Find the next perfect square! **7 kyu**

You might know some pretty large perfect squares. But what about the NEXT one?

Complete the findNextSquare method that finds the next integral perfect square after the one passed as a parameter. Recall that an integral perfect square is an integer n such that sqrt(n) is also an integer.

If the parameter is itself not a perfect square then -1 should be returned. You may assume the parameter is positive.

*Examples:*

    findNextSquare(121) --> returns 144
    findNextSquare(625) --> returns 676
    findNextSquare(114) --> returns -1 since 114 is not a perfect

*My Solution:*

``` javascript
function findNextSquare(sq) {
    if (Math.sqrt(sq) % 1 !== 0) return -1;

    const nextNum = Math.sqrt(sq) + 1

    return Math.pow(nextNum, 2)
}
```
---

## 47. Isograms **7 kyu**

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

    isIsogram("Dermatoglyphics") == true
    isIsogram("aba") == false
    isIsogram("moOse") == false // -- ignore letter case

*My Solution:*

``` javascript
function isIsogram(str) {
    const arr = [];
    const sorted = str.toLowerCase().split('').sort();
    sorted.forEach((char, index) => {
        if (sorted[index] === sorted[index + 1]) {
            arr.push(char)
        }
    })
    return arr.length === 0
}
```
---

## 48. Sum of two lowest positive integers **7 kyu**

Create a function that returns the sum of the two lowest positive numbers given an array of minimum 4 positive integers. No floats or non-positive integers will be passed.

For example, when an array is passed like [*19, 5, 42, 2, 77]*, the output should be *7*.

    [10, 343445353, 3453445, 3453545353453] should return 3453455.

*My Solution:*

``` javascript
function sumTwoSmallestNumbers(numbers) {
    const sorted = numbers.sort((a, b) => a - b);

    return sorted[0] + sorted[1]
}

```
---

## 49. Descending Order **7 kyu**

Your task is to make a function that can take any non-negative integer as an argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

*Examples:*

    Input: 42145 Output: 54421

    Input: 145263 Output: 654321

    Input: 123456789 Output: 987654321

*My Solution:*

``` javascript
function descendingOrder(n) {
    return +n.toString()
        .split('')
        .sort((a, b) => b - a)
        .join('')
}
```
---

## 50. Detect Pangram **6 kyu**

A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence "The quick brown fox jumps over the lazy dog" is a pangram, because it uses the letters A-Z at least once (case is irrelevant).

Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.

*My Solution:*

``` javascript
function isPangram(string) {
    const arr = [];
    const sorted = string.toLowerCase().match(/[a-z]/gi).sort();

    sorted.forEach((char, i) => {
        if (sorted[i] !== sorted[i + 1]) {
            arr.push(char)
        }
    });
    return arr.length === 26
}
```
---

## 51. Two to One **7 kyu**

Take 2 strings s1 and s2 including only letters from ato z. Return a new sorted string, the longest possible, containing distinct letters,
each taken only once - coming from s1 or s2.

*Examples:*

    a = "xyaabbbccccdefww"
    b = "xxxxyyyyabklmopq"
    longest(a, b) -> "abcdefklmopqwxy"

    a = "abcdefghijklmnopqrstuvwxyz"
    longest(a, a) -> "abcdefghijklmnopqrstuvwxyz"

*My Solution:*

``` javascript
function longest(s1, s2) {
    const joined = s1.concat(s2).split('').sort();
    const matched = joined.join('').match(/[a-zA-Z]/gi);

    return matched.map((char, index) => {
        if (matched[index] !== matched[index + 1]) {
            return char
        }
    }).join('');
}
```
---

## 52. Friend or Foe? **7 kyu**

Make a program that filters a list of strings and returns a list with only your friends name in it.

If a name has exactly 4 letters in it, you can be sure that it has to be a friend of yours! Otherwise, you can be sure he's not...

*Examples:*

     Input = ["Ryan", "Kieran", "Jason", "Yous"], Output = ["Ryan", "Yous"]

    i.e.

    friend ["Ryan", "Kieran", "Mark"] `shouldBe` ["Ryan", "Mark"]

*My Solution:*

``` javascript
function friend(friends) {
    return friends.filter(name => {
        if (name.length === 4) {
            return name
        }
    })
}
```
---

## 53. String ends with? **7 kyu**

Complete the solution so that it returns true if the first argument(string) passed in ends with the 2nd argument (also a string).

*Examples:*

    solution('abc', 'bc') // returns true
    solution('abc', 'd') // returns false

*My Solution:*

``` javascript
function solution(str, ending) {
    if (ending.length === 0) return true;
    
    const endLength = -ending.length;

    const lastCharStr = str.slice(endLength);

    return lastCharStr === ending;
}

```
---

## 54. Reverse words **7 kyu**

Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.

*Examples:*

    "This is an example!" ==> "sihT si na !elpmaxe"
    "double  spaces"      ==> "elbuod  secaps"

*My Solution:*

``` javascript
function reverseWords(str) {
    return str.split(' ').map(char => char.split('').reverse().join('')).join(' ')
}
```
---

## 55. Count of positives / sum of negatives **8 kyu**

Given an array of integers.

Return an array, where the first element is the count of positives numbers and the second element is sum of negative numbers.

If the input array is empty or null, return an empty array.

*Example:*

    For input [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, -11, -12, -13, -14, -15], you should return [10, -65].

*My Solution:*

``` javascript
function countPositivesSumNegatives(input) {
  
  if (input === null || input.length === 0) {
        return [];
    } else {
        const arrPos = [];
        const arrNeg = [];

        input.forEach(num => {
            if (num > 0) {
                arrPos.push(num);
            } else {
                arrNeg.push(num);
            }
        })
      
        if (arrNeg.length !== 0) {
            const sumNeg = arrNeg.reduce((a, b) => a + b);

            return [arrPos.length, sumNeg]
        } else {
            return [arrPos.length, 0]
        }
    }
}
```
---

## 56. Reverse every other word in the string **6 kyu**

Reverse every other word in a given string, then return the string. Throw away any leading or trailing whitespace, while ensuring there is exactly one space between each word. Punctuation marks should be treated as if they are a part of the word in this kata.

*My Solution:*

``` javascript
function reverse(str) {
  
 const match = str.match(/\S\w+[.,!?]*/gi);
  
    if (match === null) {
        return ''
    } else {
        const splited = str.split(' ');
        for (let i = 0; i < splited.length; i++) {
            if (i % 2 !== 0) {
                splited[i] = splited[i].split('').reverse().join('')
            }
        }
        return splited.join(' ')
    }
}
```
---

## 57. Time-like string format **6 kyu**

Build up a method that takes an integer and formats it to a 'time - like' format.

The method must raise an exception if its hour length is less than 3 digits and greater than 4.

*Example:*

    solution(800); // should return '8:00'
    solution(1000); // should return '10:00'
    solution(1451); // should return '14:51'
    solution(3351); // should return '33:51'


*My Solution:*

``` javascript
function solutionTimeLike(hour) {
    const regex = /^[\d]{3,4}$/
    if (regex.test(hour)) {
        const toStr = hour.toString();
        const splited = toStr.split('');

        if (splited.length === 3) {
            splited.splice(1, 0, ':')
            return splited.join('')
        } else {
            splited.splice(2, 0, ':')
            return splited.join('')
        }
    } else {
        throw 'Must enter a number that has 3 or 4 digits';
    }
}
```
---

## 58. Mumbling **7 kyu**

This time no story, no theory. The examples below show you how to write function accum:

*Examples:*

    accum("abcd") -> "A-Bb-Ccc-Dddd"
    accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
    accum("cwAt") -> "C-Ww-Aaa-Tttt"

The parameter of accum is a string which includes only letters from a..z and A..Z.

*My Solution:*

``` javascript
function accum(str) {
    const repeated = str.split('').map((char, i) => char = char.repeat(i + 1))

    return repeated.map(char => char.charAt(0).toUpperCase() + char.slice(1).toLowerCase()).join('-')
}
```
---

## 59. Exes and Ohs **7 kyu**

Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

*Examples input/output:*

    XO("ooxx") => true
    XO("xooxx") => false
    XO("ooxXm") => true
    XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
    XO("zzoo") => false

*My Solution:*

``` javascript
function XO(str) {
    if(str.length === 0) return true;

    const os = str.match(/[o+]/gi);
    const xs = str.match(/[x+]/gi);
    
    if (os === null || xs === null) return false
    return os.length === xs.length;
}
```
---

## 60. Hungarian Vowel Harmony (easy) **7 kyu**

Vowel harmony is a phenomenon in some languages. It means that "A vowel or vowels in a word are changed to sound the same (thus "in harmony.")" (wikipedia). This kata is based on vowel harmony in Hungarian.

Task:

Your goal is to create a function *dative()* (Dative() in C#) which returns the valid form of a valid Hungarian word *w* in dative case i. e. append the correct suffix *nek* or *nak* to the word w based on vowel harmony rules.

*Vowel Harmony Rules (simplified)*

    When the last vowel in the word is

    a front vowel (e, é, i, í, ö, ő, ü, ű) the suffix is -nek

    a back vowel (a, á, o, ó, u, ú) the suffix is -nak

*Examples:*

    dative("ablak") == "ablaknak"
    dative("szék") == "széknek"
    dative("otthon") == "otthonnak"

*Preconditions:*

To keep it simple: All words end with a consonant :)
All strings are unicode strings.
There are no grammatical exceptions in the tests.

*My Solution:*

``` javascript
function dative(word) {
    const nek = word.search(/e|é|i|í|ö|ő|ü|ű/gi)
    const nak = word.search(/a|á|o|ó|u|ú/gi)

    return nek > nak ? word + 'nek' : word + 'nak'
}
```
---

## 61. Hungarian Vowel Harmony (harder) **6 kyu**

Vowel harmony is a phenomenon in some languages. It means that "A vowel or vowels in a word are changed to sound the same (thus "in harmony.")" (wikipedia). This kata is based on vowel harmony in Hungarian.

*Task:*

Your goal is to create a function *instrumental()* which returns the valid form of a valid Hungarian word *w* in instrumental case i. e. append the correct suffix *-vel* or *-val* to the word *w* based on vowel harmony rules.

*Vowel Harmony Rules (simplified)*

    Front vowels: e, é, i, í, ö, ő, ü, ű

    Back vowels: a, á, o, ó, u, ú


    Vowel pairs (short -> long): a -> á, e -> é, i -> í, o -> ó, u -> ú, ö -> ő, ü -> ű

    Digraphs: sz, zs, cs

*Word ends with a vowel*

1. Change the ending vowel from short to long form.

1. Append the suffix:

    1. vel if the ending vowel is a front vowel

    1. val if the ending vowel is a back vowel


*Word ends with a consonant*

Step one

1. Default case: Double the ending consonant and continue with step two.
1. Special case: If the word ends with a digraph then double the first letter (e. g. sz -> ssz)

Step two

*Append the suffix:*

1. el if the last vowel is a front vowel
1. al if the last vowel is a back vowel

*Examples:*

    instrumental("fa") === "fával"
    instrumental("teve") === "tevével"
    instrumental("betű") === "betűvel"
    instrumental("ablak") === "ablakkal"
    instrumental("szék") === "székkel"
    instrumental("otthon") === "otthonnal"
    instrumental("kar") === "karral"
    instrumental("rács") === "ráccsal"
    instrumental("kosz") === "kosszal"

*Preconditions:*

1. All strings are unicode strings.
1. The tests don't contain:
    1. exceptional cases like kávé -> kávéval
    1. words ending with doubled consonants (e. g. tett)
    1. words ending with y
    1. words ending with u, i

*My Solution:*

``` javascript
function instrumental(word) {

    const replaced = word.replace(/a$|e$|i$|u$|ö$|ü$/gi, ($0) => {
        if ($0 === 'a') {
            return 'á';
        } else if ($0 === 'e') {
            return 'é';
        } else if ($0 === 'i') {
            return 'í';
        } else if ($0 === 'o') {
            return 'ó';
        } else if ($0 === 'u') {
            return 'ú';
        } else if ($0 === 'ö') {
            return 'ő';
        } else if ($0 === 'ü') {
            return 'ű';
        } else {
            return
        }
    })
    const lastTwo = replaced.replace(/sz$|zs$|cs$/g, ($0) => {
        if ($0 === 'sz') {
            return 'ssz'
        } else if ($0 === 'zs') {
            return 'zzs'
        } else if ($0 === 'cs') {
            return 'ccs'
        } else {
            return
        }
    })

    let addV;
    switch (lastTwo.slice(-1)) {
        case 'é':
        case 'é':
        case 'i':
        case 'í':
        case 'ö':
        case 'ő':
        case 'ü':
        case 'ű':
            addV = lastTwo + 'vel'
            break
        case 'a':
        case 'á':
        case 'o':
        case 'ó':
        case 'u':
        case 'ú':
            addV = lastTwo + 'val'
            break
        default:
            addV = lastTwo
    }

    const searchIfValVelAdded = addV.search(/val$|vel$/g)
    if (searchIfValVelAdded < 0) {
        
        if (addV.slice(-3) === 'ssz' || addV.slice(-3) === 'zzs' || addV.slice(-3) === 'ccs') {
            const el = addV.search(/e|é|i|í|ö|ő|ü|ű/gi)
            const al = addV.search(/a|á|o|ó|u|ú/gi)
            return el > al ? addV + 'el' : addV + 'al'
        }

        if (addV.slice(-1) !== 'e' || addV.slice(-1) !== 'é' || addV.slice(-1) !== 'i' || addV.slice(-1) !== 'í' || addV.slice(-1) !== 'ö' || addV.slice(-1) !== 'ő' || addV.slice(-1) !== 'ü' || addV.slice(-1) !== 'ű' || addV.slice(-1) !== 'a' || addV.slice(-1) !== 'á' || addV.slice(-1) !== 'o' || addV.slice(-1) !== 'ó' || addV.slice(-1) !== 'u' || addV.slice(-1) !== 'ú' && addV.slice(-3) !== 'ssz' && addV.slice(-3) !== 'zzs' && addV.slice(-3) !== 'ccs') {
            const el = addV.search(/e|é|i|í|ö|ő|ü|ű/gi)
            const al = addV.search(/a|á|o|ó|u|ú/gi)
            return el > al ? addV + addV.slice(-1) + 'el' : addV + addV.slice(-1) + 'al'
        }
    } else {
        return addV
    }
}
```
---

## 62. Char Code Calculation **7 kyu**

Given a string, turn each letter into its ASCII character code and join them together to create a number - let's call this number total1:

    'ABC' --> 'A' = 65, 'B' = 66, 'C' = 67 --> 656667

Then replace any incidence of the number 7 with the number 1, and call this number 'total2':

total1 = 656667
            ^
total2 = 656661
            ^
            
Then return the difference between the sum of the digits in total1 and total2:

    (6 + 5 + 6 + 6 + 6 + 7)
    - (6 + 5 + 6 + 6 + 6 + 1)
    -------------------------
                        6

*My Solution:*

``` javascript
function calc(x) {
    const total1 = x.split('').map(char => char.charCodeAt()).join('');
    const total2 = total1.replace(/7/g, '1');

    const sum1 = total1.split('').map(Number).reduce((a, b) => a + b);
    const sum2 = total2.split('').map(Number).reduce((a, b) => a + b);

    return sum1 - sum2;
}
```
---
