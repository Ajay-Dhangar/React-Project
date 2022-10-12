# REACT-PROJECTS 

1. [Calculator](https://ajay-dhangar.github.io/Calculator/)

2. 

### 1. How to create Calculator       
       
   - Create `index.html` file and put tis code.   
 ```   
    <div id="root"></div>
    
 ```
   - create `style.css` file and put tis code.
   ```
   .app-container {
  width: 400px;
  height: 400px;
}

.calculator {
  display: grid;
  grid-template-columns: repeat(4, 50px);
}

.display {
  grid-column-start: 1;
  grid-column-end: 5;
  height: 40px;
  font-size: 30px;
  text-align: right;
  border: 1px solid black;
  padding-right: 10px;
  padding-top: 5px;
}

button {
  height: 50px;
  background-color: white;
  border: 1px solid lightgray;
}

button.operator {
  background-color: lightgray;
}
   ```
   - create `main.js` file and put tis code.
```
const Calculator = function (props) {
  const [calc, setCalc] = React.useState({
    current: "0",
    total: "0",
    isInitial: true,
    preOp: ""
  });

  const handleNumber = function (value) {
    let newValue = value;
    if (!calc.isInitial) {
      newValue = calc.current + value;
    }
    setCalc({
      current: newValue,
      total: calc.total,
      isInitial: false,
      preOp: calc.preOp
    });
  };

  const handleOperator = function (value) {
    const total = doCalculation();

    setCalc({
      current: total.toString(),
      total: total.toString(),
      isInitial: true,
      preOp: value
    });
  };

  const handleClear = function () {
    setCalc({ current: "0", total: "0", isInitial: true, op: "" });
  };

  const doCalculation = function () {
    debugger;
    let total = parseInt(calc.total);

    switch (calc.preOp) {
      case "+":
        total += parseInt(calc.current);
        break;
      case "-":
        total -= parseInt(calc.current);
        break;
      case "*":
        total *= parseInt(calc.current);
        break;
      case "/":
        total /= parseInt(calc.current);
        break;
      default:
        total = parseInt(calc.current);
    }
    return total;
  };

  const handleEquals = function () {
    doCalculation();
  };

  const renderDisplay = function () {
    return calc.current;
  };

  return (
    <div className="calculator">
      <div className="display">{renderDisplay()}</div>
      <CalcButton value="7" onClick={handleNumber} />
      <CalcButton value="8" onClick={handleNumber} />
      <CalcButton value="9" onClick={handleNumber} />
      <CalcButton className="operator" value="/" onClick={handleOperator} />

      <CalcButton value="4" onClick={handleNumber} />
      <CalcButton value="5" onClick={handleNumber} />
      <CalcButton value="6" onClick={handleNumber} />
      <CalcButton className="operator" value="*" onClick={handleOperator} />

      <CalcButton value="1" onClick={handleNumber} />
      <CalcButton value="2" onClick={handleNumber} />
      <CalcButton value="3" onClick={handleNumber} />
      <CalcButton className="operator" value="-" onClick={handleOperator} />

      <CalcButton value="C" onClick={handleClear} />
      <CalcButton value="0" onClick={handleNumber} />
      <CalcButton value="=" onClick={handleOperator} />

      <CalcButton className="operator" value="+" onClick={handleOperator} />
    </div>
  );
};

const CalcButton = (props) => (
  <button
    className={props.className}
    onClick={() => props.onClick(props.value)}
  >
    {props.value}
  </button>
);

ReactDOM.render(
  <div className="app-container">
    <Calculator />
  </div>,
  document.getElementById("root")
);
```

**OUTPUT**
![image](https://user-images.githubusercontent.com/99037494/195266894-c17add7b-239c-4c03-9aa7-f2f858da2b71.png)




