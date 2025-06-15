### Typescript

Javascript is a dynamically typed language

```js
sudo npm i -g typescript
```

```js
tsc --init
```


```js
tsc
```

<img width="898" alt="image" src="https://github.com/user-attachments/assets/873b239e-64a1-4873-988b-b939ad7eb682" />

#### Tuple

```js
let user: [number, string] = [1, "bash"];
```

#### ENUM
```js
const enum Size {
  Small = 1,
  Medium = 2,
  Large = 3,
}

let mysize: Size = Size.Medium;

console.log(mysize);

```

#### Funtions

```js
const calculateTax = (income: number): string => {
  return "Hi";
};
```
```js
const calculateTax = (income: number): number => {
  if (income < 50) return income * 5;
  return income * 7;
};

```
For function settings changes in tsconfig
```
"noUnusedLocals": true 
"noUnusedParameters": true          
"noImplicitReturns": true

### Objects
<img width="1045" alt="image" src="https://github.com/user-attachments/assets/3bd5aa1c-fc97-463a-8d3f-0ba4053fa54e" />

```js
let employee: { id: number; name?: string } = { id: 1 };

employee.name = "Bash";
```
? - optional
```js
let employee: { id: number; name: string } = { id: 1, name: "bash" };
```

```js
let employee: { readonly id: number; name: string } = { id: 1, name: "bash" };

employee.id = 2; // Error
```

```js
let employee: {
  readonly id: number;
  name: string;
  retire: (date: Date) => void;
} = { id: 1, name: "bash", retire: (date: Date) => console.log(date) };

let user = "basheer";
```

### Advanced 
```js
type Employee = {
  readonly id: number;
  name: string;
  retire: (date: Date) => void;
};

let employee: Employee = {
  id: 1,
  name: "bash",
  retire: (date: Date) => console.log(date),
};

let user = "basheer";
```

#### Union type 
```js
function kgTolbs(weight: number | string): number {
  if (typeof weight === "number") {
    return weight * 2.2;
  } else {
    return parseInt(weight) * 2.2;
  }
}

kgTolbs(10);
kgTolbs("10kg");
```

### Intersection type
```js
type Draggable = {
  drage: () => void;
};

type Resizableable = {
  resize: () => void;
};

type UIWidget = Draggable & Resizableable;

let textBox: UIWidget = {
  drage: () => {},
  resize: () => {},
};

```
### Literal(Exact, specific)
```js
type Quantity = 50 | 100;

let quantity: Quantity;

quantity = 50;

type Metric = "cm" | "inch";
```

<img width="1102" alt="image" src="https://github.com/user-attachments/assets/3fd5b826-c7df-4e21-a1ce-b81065ca9b04" />

### React
```js
  let firstValue: string = "Basheer";
  let amount: number = 120;
  let isPublished: boolean = true;
  const numbers: number[] = [1, 2, 3, 4, 5, 6];
  const employees: Array<string> = ["basheer", "john", "joe"];
  let aTuple: [string, number] = ["basheer", 3]; // tuple
  enum Cars {
    first = "Audi",
    second = "Benz",
  }
```

#### Component
```js
import Message from "./components/message";
import "./App.css";

function App() {
  return (
    <>
      <Message name="Basheer" message="Hello world" />
    </>
  );
}

export default App;
```

```js
function App() {
  return (
    <>
      <Message name="Basheer" message="Hello world" />
    </>
  );
}
```

