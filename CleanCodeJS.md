# Clean code javascript

## **Variable**
### Use meaningful variable name:

**Not good:**
```javascript
const yyyymmdd = moment().format('YYYY/MM/DD');
```

**Good:**
```javascript
const currentDate = moment().format('YYYY/MM/DD');
```

### Use the same vocabulary for the same type of variable

**Not good:**
```javascript
getUserInfo();
getClientData();
getCustomerRecord();
```

**Good:**
```javascript
getUser();
```

### Use explanatory variables
**Not good:**
```javascript
setTimeout(pink, 6789); //what the heck is 6789?
```

**Good:**
```javascript
const TIME_TO_WAIT = 6789;
setTimeout(pink, TIME_TO_WAIT);
```

### Avoid mental mapping
**Not good:**
```javascript
localtions.forEach((l) => {
	doStuff();
	//...
	dispatch(l); // l is not good here	
})
```

**Good:**
```javascript
localtions.forEach((location) => {
	doStuff();
	//...
	dispatch(location); // l is not good here	
})
```

### Use default params
**Not Good:**
```javascript
const getName = (name) => {
	return name || 'Luu manh'
}
```

**Good:**
```javascript
const getName = (name = 'Luu manh') => {
	return name
}
```

## **Function**
### Use 2 or fewer params
Avoid pass too much params to function, it's hard to test and handle logic in function have >=3 params.
Limit params in function by use destructuring syntax in ES6.
ex: 
use 
```javascript
function createMenu({ title, body, buttonText, cancellable }) {
  // ...
}

createMenu({
  title: 'Foo',
  body: 'Bar',
  buttonText: 'Baz',
  cancellable: true
});
```
instead of
```javascript
function createMenu(title, body, buttonText, cancellable) {
  // ...
}
```

### Function should do one thing
This is the most important rule in software engineering.
**Not Good:**
```javascript
const emailClients = (clients) => {
	clients.forEach(client => {
		const clientRecord = ClientModel.find(client);
		if(clientRecord.isActive()){
			email(client);
		}
	})
} 
```

**Good:**
```javascript
const isActiveClient = (client) => {
	const clientRecord = ClientModel.find(client);
	return clientRecord.isActive();
}

const emailActiveClients = (clients) => {
	clients.filter(isActiveClient).forEach(email);
}
```

### Use meaningful func name and this name should say what func do
Same to variable's name

### Encapsule conditionals (Đóng gói các điều kiện)
**Not good:**
```javascript
if (fsm.state === 'fetching' && isEmpty(listNode)) {
  // ...
}
```

**Good:**
```javascript
function shouldShowSpinner(fsm, listNode) {
	return fsm.state === 'fetching' && isEmpty(listNode);
}

if(shouldShowSpinner(fsmInstance, listNodeInstance)) {
	// ...
}

### Use functional programming as much as possible
**Not good:**
```javascript
const programmerOutput = [
  {
    name: 'Uncle Bobby',
    linesOfCode: 500
  }, {
    name: 'Suzie Q',
    linesOfCode: 1500
  }, {
    name: 'Jimmy Gosling',
    linesOfCode: 150
  }, {
    name: 'Gracie Hopper',
    linesOfCode: 1000
  }
];

let totalOutput = 0;

for (let i = 0; i < programmerOutput.length; i++) {
  totalOutput += programmerOutput[i].linesOfCode;
```

**Good:**
```javascript
const programmerOutput = [
  {
    name: 'Uncle Bobby',
    linesOfCode: 500
  }, {
    name: 'Suzie Q',
    linesOfCode: 1500
  }, {
    name: 'Jimmy Gosling',
    linesOfCode: 150
  }, {
    name: 'Gracie Hopper',
    linesOfCode: 1000
  }
];

const INITIAL_VALUE = 0;

const totalOutput = programmerOutput
  .map((programmer) => programmer.linesOfCode)
  .reduce((acc, linesOfCode) => acc + linesOfCode, INITIAL_VALUE);
```

### Delete Dead code
**Not Good:**
```javascript
function oldF() {
	// ...
}

function newF() {
	// ...
}

newF()
// oldF() never use
```

**Good:**
```javascript
function newF() {
	// ...
}

newF()
```

