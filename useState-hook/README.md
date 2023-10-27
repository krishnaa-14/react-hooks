

1. **useState Hook**: It's a React hook that allows you to add state to functional components.

```jsx
import React, { useState } from 'react';

function MyComponent() {
  const [state, setState] = useState(initialValue);
  // ...
}
```

2. **State Initialization**: `useState` returns an array with two elements. The first element (`state`) is the current state value, and the second element (`setState`) is a function you use to update the state. `initialValue` is the initial value of the state.

3. **State Updating**: When you call `setState`, React will re-render the component with the updated state. If you do this multiple times in a single render, React may batch the updates and apply them together.

   ```jsx
   // Incorrect way - It may not work as expected
   setState(newState);
   setState(newState);

   // Correct way - Ensures each update is based on the latest state
   setState(prevState => newState);
   setState(prevState => newState);
   ```

4. **Accessing Previous State**: If your state update depends on the current state, it's better to use the function form of `setState`. This way, you'll get the previous state value and can safely compute the next state based on it.

   ```jsx
   setState(prevState => prevState + 1);
   ```

5. **Avoiding Conditionals**: Do not put `useState` inside conditional blocks. Always use it at the top level of your component.

   ```jsx
   // Incorrect
   if (condition) {
     const [val, setVal] = useState(0);
   }

   // Correct
   const [val, setVal] = useState(0);
   ```

6. **Hooks Inside Components**: Always use hooks inside functional components, not inside other functions or conditions.

