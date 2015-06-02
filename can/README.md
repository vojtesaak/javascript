# Storyous guide to Can.JS() {

## Table of Contents

1. [Common pitfails](#common-pitfails)
2. [Communication between components](#communication-between-components)
3. [Component lifecycle](#component-lifecycle)

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

  - [1.3](#1.3) <a name='1.3'></a> **Dont set can objects as default values at prototypes**: Objects are shared between instances, so it can have unexpected side effects. When you need to use this 'feature', please comment a parameter. [Or check this fiddle](http://jsfiddle.net/sb8smx9L/)

    ```javascript
    
    can.Component.extend({
        tag: "my-comp",
        viewModel: {

            // will be shared
            someObject: new can.Map(),

            // will work as default
            anotherObject: {},
        }
    });

    ```

**[⬆ back to top](#table-of-contents)**

## Communication between components

  - [2.1](#2.1) <a name='2.1'></a>  **Best page which explains passing data/events between components**: [Improving communication and message passing between components](https://github.com/bitovi/canjs/issues/1209). It's a feature request but it sumarizes all current ways to use can.Components.

**[⬆ back to top](#table-of-contents)**

## Component lifecycle

  - [3.1](#3.1) <a name='3.1'></a>  **It's good to know the call order of init methods**: [Or check this fiddle](http://jsfiddle.net/sb8smx9L/)

    1. Init at ViewModel
    2. Init at Events
    3. --render--
    4. Init at Component

    ```javascript


    var Component = can.Component.extend({
        tag: 'click-counter',
        template: '<a href="javascript://" can-click="updateCount">' 
                    + 'Click Me</a>'
                    + '<p id="msg">Clicked{{countCompute}} times'
                    + '</p>',
        init: function(element, options) {
            // called third
            console.log('Component init', element, options);
        },
        viewModel: {
            count: 0,
     
            init: function(inputData) {
                // called first
                console.log('Scope init', inputData);
            },
            updateCount: function() {
                this.attr('count', this.count + 1);
                this.attr('anotherShare.shared', this.anotherShare.shared + 1);
                this.attr('sharedMap.shared', this.sharedMap.shared + 1);
            }
        },
        events: {
            init: function(arrayOfElements, scope) {
                // called second
                console.log('Events init', arrayOfElements, scope);
            }
        }
    });

    ```

# }