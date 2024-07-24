# Input Component with Imperative Focus Handling

This project demonstrates a basic React component that uses `useImperativeHandle` to expose a custom imperative method for focusing an input field.

## Project Structure

The project consists of a single React component:

- **Input Component (`Input.js`)**: This component encapsulates an `<input>` element and uses `useImperativeHandle` to expose a `focus()` method.

## Input Component Details

### File: `Input.js`

```javascript
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const Input = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
      console.log('Input is in focus');
    }
  }));

  return <input ref={inputRef} {...props} placeholder="Type here" />;
});

export default Input;
```

### Explanation:

- **`useRef`**: Used to create a reference (`inputRef`) that will be attached to the `<input>` element.
- **`useImperativeHandle`**: Hook that allows the component to expose certain functions or properties to parent components when using `ref`.
  - Here, it exposes a `focus()` method that triggers focus on the `<input>` element and logs a message to the console.

## App Component Details

### File: `App.js`

```javascript
import React, { useRef } from 'react';
import Input from './Input';

const App = () => {
  const inputRef = useRef(null);

  return (
    <div>
      <Input ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
};

export default App;
```

### Explanation:

- **`useRef`**: Creates a reference (`inputRef`) that will be used to call the `focus()` method of the `<Input>` component.
- **`onClick` Handler**: Triggers the `focus()` method of the `<Input>` component when the button is clicked.

## How to Run

To run the project:

1. Clone the repository.
2. Navigate to the project directory.
3. Install dependencies: `npm install` or `yarn install`.
4. Start the development server: `npm start` or `yarn start`.
5. Open your browser and go to `http://localhost:3000` to view the app.

## Notes

- This project demonstrates how to use `useImperativeHandle` to control child components imperatively from parent components.
- The `Input` component encapsulates an `<input>` element and exposes a `focus()` method to focus the input programmatically.
- This setup is useful when you need to manage focus or other imperative actions from a parent component without exposing the internal implementation details of the child component.

## What you will experience

<img width="1436" alt="Captura de pantalla 2024-07-24 a la(s) 12 49 18" src="https://github.com/user-attachments/assets/0f7bdfcb-c3f3-4314-845f-e12af2763b79">
