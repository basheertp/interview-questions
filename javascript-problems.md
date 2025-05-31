
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
