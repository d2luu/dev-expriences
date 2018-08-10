### Use stateless component
** The Stateless functional components will benefit from future React performance optimizations specific to these components. **
```javascript
const App = () => {
  return (
    <div>
      <h2 id="heading">Hello ReactJS </h2>
      <header />
    </div>
  );
};

export default App;
```

If want to write component in ES6 style, still can do but in this case the eslint error need to be removed (if using eslint). The following change in .eslintrc file:
```bash
"rules": {
    "react/prefer-stateless-function": "off"
}
```