# react-functional

Add life cycle methods to stateless functional components,
without the class noise. 

## functional(component)

### Adding life cycle methods to function component

```javascript
import { React } from 'react'
import functional from 'react-functional'

function ComponentA(props) {
  return <div>{ props.name }</div>
}

ComponentA.shouldComponentUpdate = (props, nextProps) =>
  props.name !== nextProps.name

export default functional(ComponentA)
```

### Compose component from an object

```javascript
import { React } from 'react'
import functional from 'react-functional'

function shouldComponentUpdate(props, nextProps) {
  return props.name !== nextProps.name
}

function render(props) {
  return <div>{ props.name }</div>
}

export default functional({shouldComponentUpdate, render})
```

### Supported properties

- `propTypes`
- `defaultProps`
- `displayName` (auto-detected from function names)

### Supported methods

- `componentWillMount(props)`
- `componentDidMount(props, refs)`
- `componentWillReceiveProps(props, nextProps, refs)`
- `shouldComponentUpdate(props, nextProps, refs)`
- `componentWillUpdate(props, nextProps, refs)`
- `componentDidUpdate(props, prevProps, refs)`
- `componentWillUnmount(props, refs)`

## Test Coverage

```sh
npm run cov
```

| File      |  % Stmts | % Branch |  % Funcs |  % Lines |
|-----------|----------|----------|----------|----------|
| All files |      100 |      100 |      100 |      100 |

```sh
npm test
```

```sh
test/index.js
  function
    ✓ componentWillMount called
    ✓ render function called
    ✓ div element rendered
    ✓ prop passed through

  object
    ✓ componentWillMount called
    ✓ render function called
    ✓ div element rendered
    ✓ prop passed through


  8 passing (1s)
```

## Thanks

* [react-stateless](http://npmjs.com/react-stateless) for inspiration and code
* [nearForm](http://nearform.com) for sponsoring
