# Solution

### `Single List component`
The Single List Component is a functional React component that renders a single item in a list. It takes in props including the item's index, whether or not it is currently selected, a function to handle click events, and the text content of the item. The component renders a `<li>` element with a background color of green if it is selected and red if it is not, and it calls the click event handler function passed in via props when it is clicked.

This component is often used as a child component within a larger list component where it can be reused multiple times to render each item in the list. By making this component reusable and encapsulating the logic for rendering and handling click events within it, we can create more modular and maintainable code.

### `Warning and Errors in code`
There is a warning and an error found in code.

Warning: 

Line 31:6:  React Hook useEffect has a missing dependency: `setSelectedIndex`. in variable `selectedIndex` under `WrappedListComponent` it must be `useState(null)` instead of `useState()`

In `SingleListItem` component, the `isSelected` prop type should be `PropTypes.bool.isRequired` instead of `PropTypes.bool`. This is because the prop is required and its value should always be a boolean.

Error:

there is an error in Line 54 under `WrappedListComponent.propTypes` it shoud be corrected as `PropTypes.shape` instead of `PropTypes.shapeOf` as property `shapeOf` does not exist in type `propType`

### `Fixed code`

Fixed code can be found in `index.js` file and the original one is saved in `problem.js` file in `src` folder.


