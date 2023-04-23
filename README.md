# Solution

### Name: - Shiv Shnakar Singh<br/>
### Registration No: - 12018635<br/>
### College: - Lovely professional University<br/>
### Assignment Domain: - Frontend Assignment<br/>

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

Fixed code can be found in `App.js` file in `src` folder.

```
import React, { useState, useEffect, memo } from "react";
import PropTypes from "prop-types";

// Single List Item
const WrappedSingleListItem = ({ index, isSelected, onClickHandler, text }) => {
  return (
    <li
      style={{ backgroundColor: isSelected ? "green" : "red" }}
      onClick={() => onClickHandler(index)}
    >
      {text}
    </li>
  );
};

WrappedSingleListItem.propTypes = {
  index: PropTypes.number,
  isSelected: PropTypes.bool,
  onClickHandler: PropTypes.func.isRequired,
  text: PropTypes.string.isRequired,
};

const SingleListItem = memo(WrappedSingleListItem);

// List Component
const WrappedListComponent = ({ items }) => {
  const [selectedIndex, setSelectedIndex] = useState();

  useEffect(() => {
    setSelectedIndex(null);
  }, [items]);

  const handleClick = (index) => {
    setSelectedIndex(index);
  };

  return (
    <ul style={{ textAlign: "left" }}>
      {items ? (
        items.map((item, index) => (
          <SingleListItem
            key={index}
            onClickHandler={() => handleClick(index)}
            text={item.text}
            index={index}
            isSelected={selectedIndex === index}
          />
        ))
      ) : (
        <div>Welcome</div>
      )}
    </ul>
  );
};

WrappedListComponent.propTypes = {
  items: PropTypes.arrayOf(
    PropTypes.shape({
      text: PropTypes.string.isRequired,
    })
  ),
};

WrappedListComponent.defaultProps = {
  items: [
    { text: "BMW" },
    { text: "Audi is red" },
    { text: "Thank You Mercedes" },
    { text: "There you go Porsche" },
  ],
};

const List = memo(WrappedListComponent);

export default List;
```


