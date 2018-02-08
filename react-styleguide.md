## Table of Contents
  1. [Do's](#do-s)
  2. [Don't](#don-t)
  3. [File Naming](#file-naming)
  4. [React Component](#react-component)

## Do's
* Use JSX syntax over React create methods.
* Use stateless component for dumb components `(no usage of setState)`
* Use [PureComponents](https://facebook.github.io/react/docs/react-api.html#react.purecomponent) wherever there is need of shallow rendering. 
* Use [Component Composition](https://reactjs.org/docs/components-and-props.html#composing-components) for scalability. This let's us use the same component abstraction for any level of detail.
* Use ternary operators over if/else blocks in conditional rendering.
* Use [Functional setState](https://x-team.com/blog/react-render-setstate/) over object merging.
* Use [Arrow Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) syntax to bind event handlers to avoid inconsistency between class and functional components.
* Use [shouldComponentUpdate()](https://reactjs.org/docs/react-component.html#shouldcomponentupdate) to avoid unnecessary component re-rendering. 
* Use [Controlled Components over Uncontrolled Components](https://goshakkk.name/controlled-vs-uncontrolled-inputs-react/).
* Use [lift state pattern](https://reactjs.org/docs/lifting-state-up.html) to transfer data between multiple child components before moving towards state containers like [Redux](https://redux.js.org/).

## Don't
* Do not use `React.createElement` unless you're initializing the app from a file that is not JSX.
* Do not create monolithic component, it is advisable to divide into stateless components and local render methods if render method exceeds `25` lines of code.
* Do not use `this.state` for local properties which will not be used to determine render logic.
```
render() {
    // Bad
    {
      (this.state.currentIndex === index && this.state.selectedIndices < MAX_LEN>)
      ? <WarningMessage />
      : <div>The queue is full!</div>
    }

    // Good
    {
      (this.state.currentIndex === index && this.selectedIndices < MAX_LEN>)
      ? <WarningMessage />
      : <div>The queue is full!</div>
    }
  }
```
* Avoid using DOM component attributes names as prop names.
* Don't replace [PureComponents](https://facebook.github.io/react/docs/react-api.html#react.purecomponent) in place for stateless components. PureComponents should only be used when there is a need of shallow comparison of the nextProps, this.props / prevState, this.state objects.

## File Naming

### File Extension
Use `.js` extension for React component file

### Casing Style
Use Pascalcasing `SampleComponent` for naming React Component files

## React Component

### Naming
* Use the filename as the component name.
For e.g -> `SampleComponent.js` => `SampleComponent`
* HOCs ([Higher-order-component](https://facebook.github.io/react/docs/higher-order-components.html)) should be prefixed with `with` keyword.
For e.g -> `withUser`
* Props Naming: Avoid using DOM component attributes names. Always use camelCase for prop names.
```javascript
<SampleComponent
  propName="test1"
/>
```

### Structure

* Class Component
```
// Import Statements
import React, { PropTypes } from "React";
import { Superhero } from "./Block";

class SuperheroList_ extends Component {
  static propTypes = {
    theme: PropTypes.string,
    SuperheroData: React.PropTypes.arrayOf(CustomPropTypes.Superhero)
  };

  constructor(props) {
    super(props);
    // State Initialization
    this.state = {
      showThumbnails: false
    };

    // Initialize local properties
    this.currentIndex = 0;

    // Function calls
    this._initializeSuperpowers();
  }

  _initializeSuperpowers() {
    // Local methods
  }

  addToCompareList(superhero) {
    // Outgoing methods - to be sent to child components
  }

  componentDidMount() {
    // Lifecycle methods
  }

  render() {
    // Render based logic
  }
}

// Export statement, allows wrapping them into hocs
export const SuperheroList = SuperheroList_;
```

* Functional Component (Stateless)

```
const SuperheroList_ = ({
  theme = "dark"
  SuperheroData = []
}) => {

  addToCompareList(superhero) {
    // Outgoing methods - to be sent to child components
  }

  return {
    // Render based logic
  }
}

SuperheroList_.propTypes = {
  theme: PropTypes.string,
  SuperheroData: React.PropTypes.arrayOf(CustomPropTypes.Superhero)
};

// Export statement, allows wrapping them into hocs
export const SuperheroList = SuperheroList_;
```
