
### Remove numbers and special charactors from the string and print each word in reverse order
```js
const input = "$y%M%{} #%32E4&*(m5A4$n$ }s3i# #R%E$%e}h2S$a$b$";

const inputArr = input.split(" ");
let filteredWord = "";
for(let word of inputArr) {
    const filteredChar = [...word].filter(char => /[a-zA-Z]/.test(char));
    filteredWord += filteredChar.reverse().join("") + " ";
}
console.log(filteredWord);
// My nAmE is baSheER
```

### get highest number from the given array, if it has duplicate return an array
const numbers  = [1,2,3,3,2,1,3,4,4,4,3,2];

```js
  const getRepeatedNums = (numbers) => {
    let freq = [];
    let maxValue = 0;
    for (num of numbers) {
      freq[num] = freq.hasOwnProperty(num) ? freq[num] + 1 : 1;
      maxValue = Math.max(maxValue, freq[num]);
    }
    let freqNums = [];
    freq.map((num, index) => {
      if (num === maxValue) {
        freqNums.push(index);
      }
    });
    return freqNums;
  };
  const numbers = [1, 2, 3, 3, 2, 1, 3, 4, 4, 4, 3, 2];
  getRepeatedNums(numbers);
```


### Write a program to find all permutations from a string using JavaScript

```js
const input = "abc";

const getCombinations = (str) => {
    const results = [];
    if(str.length === 0 || str.length === 1) return str;
    for (let i=0; i<str.length;i++) {
        
    const currentChar = str[i];
    const remainingChar = str.slice(0,i) + str.slice(i+1);
    const remainPerms = getCombinations(remainingChar);

    for(let perms of remainPerms) {
        results.push(currentChar + perms)
    }
    }
    return results;
    
}

console.log(getCombinations(input));
```
### Find the first non-repeating charactor in a given string

### function to accept any number of chained parameters and multiple
multiply(2)(3)(4)
```js
function multiply(a) {
  let product = a;

  function inner(b) {
    product *= b;
    return inner;
  }

  inner.valueOf = () => product; // for numeric coercion
  inner.toString = () => product; // fallback
  return inner;
}
```
### find the best day to buy and best day to sell to maximize profit from stock prices (buy low, sell high after the buy day).
const prices = [9, 8, 4, 2, 5, 11, 1];
```js
function getBestBuySellDays(prices) {
  let minPrice = prices[0];
  let minDay = 0;
  let maxProfit = 0;
  let buyDay = 0;
  let sellDay = 0;

  for (let i = 1; i < prices.length; i++) {
    const profit = prices[i] - minPrice;

    if (profit > maxProfit) {
      maxProfit = profit;
      buyDay = minDay;
      sellDay = i;
    }

    if (prices[i] < minPrice) {
      minPrice = prices[i];
      minDay = i;
    }
  }

  return maxProfit > 0
    ? { buyDay, sellDay, buyPrice: prices[buyDay], sellPrice: prices[sellDay], profit: maxProfit }
    : 'No profitable trade possible';
}

// Example:
const prices = [9, 8, 4, 2, 5, 11, 1];
console.log(getBestBuySellDays(prices));
```
