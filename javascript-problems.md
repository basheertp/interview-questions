```js

const input = "23R3q32e 3E#(&h 7s@A(B) 97d78e^^&%";

const inputArr = input.split(" ");
let outputArr = []
for(let word of inputArr) {
    const wordArr = [...word].filter(char => /[a-zA-Z]/.test(char));
    outputArr.push(wordArr.reverse());
       
}
 console.log(outputArr.join(","));

```
