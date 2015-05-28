# Storyous guide to Can.JS() {

## Table of Contents

1. [Common pitfails](#common-pitfails)
2. [Communication between components](#communication-between-components)

## Common pitfails

  - [1.1](#1.1) <a name='1.1'></a> **Use .attr() to set properties**: When you don't use attr method to set properties, events will not work.

    ```javascript
    // bad
    obj.property = 'value';

    // good
    obj.attr('property', 'value');

    // reading without .attr() is ok
    var foo = object.property;
    ```

  - [1.2](#1.2) <a name='1.2'></a> **Always pass an object between components/templates**: Two way binding is lost, when you're passing a scalar.

    ```javascript
    obj.attr('prop', 'foo');

    // bad
    <my-component data-some-value="{obj.prop}"></my-component>

    // when the value is changed inside component, object is not affected
    scope.attr('someValue', 'some'); 
    console.log(obj.prop); // foo

    // good
    <my-component data-obj="{obj.prop}"></my-component>

    // when the value is changed, object is not affected
    scope.attr('obj.prop', 'some'); 
    console.log(obj.prop); // some
    ```

**[⬆ back to top](#table-of-contents)**

## Communication between components

  - [2.1] **Best page which explains passing data/events between components**: [Improving communication and message passing between components](https://github.com/bitovi/canjs/issues/1209). It's a feature request but it sumarizes all current ways to use can.Components.

**[⬆ back to top](#table-of-contents)**

# }