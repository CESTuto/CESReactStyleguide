## Table of Contents
  1. [File Naming](#file-naming)
  2. [React Component](#react-component)

## File Naming

### Extension
Use `.js` extension for React component file

### PascalCasing
Use Pascalcasing - `SampleComponent` for React Component files

## React Component

### General
* Always use JSX syntax.
* Use stateless component for dumb components `(no usage of setState)`
* Use [PureComponents](https://facebook.github.io/react/docs/react-api.html#react.purecomponent) wherever there is need of shallow rendering.
* Do not use `React.createElement` unless you're initializing the app from a file that is not JSX.

### Naming
* Use the filename as the component name.
For e.g -> `SampleComponent.js` => `SampleComponent`
* HOCs ([Higher-order-component](https://facebook.github.io/react/docs/higher-order-components.html)) should be prefixed with `with` keyword.
For e.g -> `withUser`
* Props Naming: Avoid using DOM component prop names for different purposes. Always use camelCase for prop names.
For e.g =>
```javascript
<SampleComponent
  propName="test1"
/>
```
* Local Variables: Should be prefixed with an underscore `_`.
For e.g -> `_sampleLocalVariable` 
