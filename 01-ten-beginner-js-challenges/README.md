# Question 1
#### Create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

```js
function filter_list(arr) {
    return arr.filter((item) => typeof item === 'number' );
}
```

Or:
```js
const filter_list = (arr) => arr.filter(item => typeof item === 'number');
```

# Question 2
#### Implement a difference function, which subtracts one list from another and returns the result. It should remove all values from list a, which are present in list b keeping their order.
```js
function arrayDiff(arr1, arr2) {
    function findIndexes (array, value){
        let indexes = []
        for (let i = 0; i < array.length; i++){ 
            if (array[i] === value) {
                indexes.push(i)
            }
        }
        return indexes
    }

    arr2.forEach((element) => {
            if (arr1.includes(element)) {
                indexOfelement = findIndexes (arr1, element)
                arr1 = arr1.filter((_, index) => !indexOfelement.includes(index))
            } 
    });
    return arr1
}
```

# Question 3
#### Given: an array containing hashes of names.
#### Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.
```js
function getNames(arr3) {
    if (arr3.length === 0) {
        result = "''"
    } else {
        lastName = arr3.pop()
        names = []
        arr3.forEach((element) => {names.push(element.name)})
        result = "'" + names.join(", ") + " & " + lastName.name + "'" 
    }
    return result
}
```

# Question 4
####  You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. 
#### The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). 
#### You always walk only a single block for each letter (direction) and you know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.
#### Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).
```js
function isValidWalk(walk){
    if (walk.length != 10) {
        return false
    }
    let nOffset = 0
    let sOffset = 0
    let wOffset = 0
    let eOffset = 0

    walk.forEach(direction => {
        switch (direction) {
            case 'n':
                nOffset += 1
                break
            case 's':
                sOffset += 1
                break
            case 'w':
                wOffset += 1
                break
            case 'e':
                eOffset += 1
                break            
        }
    });
    return (nOffset - sOffset === 0 && wOffset -eOffset ===0)
}
```

# Question 5
#### ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits. If the function is passed a valid PIN string, return true, else return false.
```js
function validatePIN(pin) {
    if (pin.length === 4 || pin.length === 6 ) {
        result = /^\d+$/.test(pin)
    } else {
        return false
    }
    return result
}
```
Or:
```js
function validatePIN(pin) {
    result = /^(\d{4}|\d{6})$/.test(pin)
    return result
}
```

# Question 6
#### Create a function, which counts the total number of lowercase letters in a string.
```js
function lowercaseCount (str) {
    result =  str.match(/[a-z]/g)
    return result ? result.length : 0
}
```

# Question 7
#### Write a simple function that takes a Date as a parameter and returns a Boolean representing whether the date is today or not. 
#### Make sure that your function does not return a false positive by only checking the day.
```js
function isToday(date) {
    result = new Date().toDateString() === date.toDateString()
    return result
  }
```

# Question 8
#### Create a function that given a string, capitalizes the letters that occupy even indexes and odd indexes separately, and returns as shown below. 
#### For example, capitalize("abcdef") = ['AbCdEf', 'aBcDeF'].
#### Index 0 will be considered even. The input will be a lowercase string with no spaces.
```js
function capitalize(str){
    strToArray1 = str.split("")
    strToArray2 = str.split("")

    strToArray1.forEach((element,index, originalArray) => {
        if (index % 2 === 0) {
            originalArray[index] = element.toUpperCase()
        }
    })

    strToArray2.forEach((element,index, originalArray) => {
        if (index % 2 !== 0) {
            originalArray[index] = element.toUpperCase()
        }
    })

    result =  [strToArray1.join(""), strToArray2.join("")]
    return result
  };
```

# Question 9
#### Create a function that given a number , returns the Maximum number  could be formed from the digits of the number given.
#### Only Natural numbers passed to the function , numbers Contain digits [0:9] inclusive. 
#### Digit Duplications could occur , So also consider it when forming the Largest.
```js
function maxNumber(num){
    result = num.toString().split("").sort((first,second) => second-first)
    return result.join("")
}
```

# Question 10
#### Write a function, persistence, that takes in a positive parameter num and returns its multiplicative persistence, which is the number of times you must multiply the digits in num until you reach a single digit.
```js
 function persistence(num) {
    
    function multiply(n){
        return n.reduce(function(a,b){return a*b;});
    }
    var count =0; 
    while(num > 9) {
        num= num.toString().split("");
        num = multiply(num);
        count++;
     }
     return count;
 }
```