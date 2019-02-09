# Creating and Inserting DOM Nodes

## Problem Statement

We can find and select nodes in the DOM. But now we want to do more. What if we
need to create or insert a new element, or remove one? We need a box of
JavaScript tools that will help us out.

## Objectives

1. Create DOM elements programmatically
2. Append elements in the DOM
3. Remove elements from the DOM

## Create DOM Elements Programmatically

### `document.createElement()`

Creating an element in JavaScript couldn't be easier. Simply call
`document.createElement(tagName)`, where `tagName` is the string representation
of any valid HTML tag (e.g., `'p'`, `'div'`, `'span'`, etc.).

Open this lesson's `index.html` file in your browser and open up the browser's
console. In the console, enter

``` javascript
let element = document.createElement('div');
```

Type `element.` (or whatever you named your new element). It's an existing DOM element, but it doesn't yet appear in the DOM.

We can set properties on it:

``` javascript
element.innerHTML = 'Hello, DOM!';
element.style.backgroundColor = '#f9f9f9';
```

Feel free to set as many properties as you'd like — this is a good chance to
look around and explore different properties of DOM elements!

But notice that no matter what properties we add, the element doesn't show up on
the page. What gives?

## Append Elements into the DOM

To get an element to appear in the DOM, we have to append it to an existing DOM
node. To go back to our tree metaphor, we have to glue our new leaf onto a
branch that's already there. We can start as high up on the tree as
`document.body`, or we can find a more specific element using any of the
techniques we've learned for traversing the DOM.

### `appendChild()`

Let's append `element` to `body` to start:

``` javascript
document.body.appendChild(element);
```

If you've been following along, you should see `"Hello, DOM!"` on the page now
(and it should have a light gray background).

We can continue to update `element`, since we have a reference to it:

``` javascript
element.style.textAlign = 'center';
```

And now our element's text is centered.

We can append elements to that element:

``` javascript
let ul = document.createElement('ul');

for (let i = 0; i < 3; i++) {
  let li = document.createElement('li');
  li.innerHTML = (i + 1).toString();
  ul.appendChild(li);
}

element.appendChild(ul);
```

Hm, that looks a bit ugly. Let's fix it

``` javascript
ul.style.textAlign = 'left';
```

That's better.

## Remove Elements from the DOM

Now let's remove one of those `li`s.

### `removeChild()`

``` javascript
ul.removeChild(ul.querySelector('li:nth-child(2)'));
```

Boom. Second element is gone.

What if we want to remove the whole unordered list (`ul`)?

### `element.remove()`

We can just call `remove()` on the element itself:

``` javascript
ul.remove();
```

And it's gone!

## Resources

- [document.createElement()](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
- [appendChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)
- [removeChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild)
- [element.remove()](https://developer.mozilla.org/en-US/docs/Web/API/ChildNode/remove)

## Conclusion

We learned how to create, append and remove elements in the DOM with JavaScript.

<p class='util--hide'>View <a href='https://learn.co/lessons/creating-and-inserting-dom-nodes'>Creating And Inserting Nodes</a> on Learn.co and start learning to code for free.</p>
