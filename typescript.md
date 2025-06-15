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
import type React from "react";

interface UserMessage {
  name: string;
  message: string;
}

const Message: React.FC<UserMessage> = ({ name, message }) => {
  return (
    <p>
      {name} , {message}
    </p>
  );
};

export default Message;

```
#### useState
```js
const [userName, setUserName] = useState<string>("User");
  const [userMessage, setUserMessage] = useState<string>(
    "This is the initial message"
  );
```

<img width="809" alt="image" src="https://github.com/user-attachments/assets/e7552e22-1070-416c-a752-c0ae8230d6c7" />

### useEffect
```js
const [userName, setUserName] = useState<string>("User");
  const [userMessage, setUserMessage] = useState<string>(
    "This is the initial message"
  );

  useEffect(() => {
    const timer = setTimeout(() => {
      setUserName("Basheer");
      setUserMessage("This is the updated message");
    }, 5000);
    return () => clearTimeout(timer);
  }, []);
```

### useContext
```js
const App: React.FC = () => {
 .....
  return (
    <UserContext.Provider value={{ name: userName, message: userMessage }}>
      <Message />
    </UserContext.Provider>
  );
};
```
userContext
```js
import React from "react";

interface UserMessageType {
  name: string;
  message: string;
}

export const UserContext = React.createContext<UserMessageType | undefined>(
  undefined
);
```
```js
import type React from "react";
import { UserContext } from "../context/user-context";
import { useContext } from "react";

const Message: React.FC = () => {
  const context = useContext(UserContext);
  if (!context) {
    throw new Error("User context must be used within UserProvider");
  }

  return (
    <p>
      {context.name} , {context.message}
    </p>
  );
};

export default Message;
```


