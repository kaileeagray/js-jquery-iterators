# jQuery Iterators

## Objectives
+ use `$.each` to iterate over a collection of objects
+ use `.each` to iterate over jQuery objects
+ use `$.map` to iterate over a collection of objects
+ use `.map` to iterate over jQuery objects

## Intro

Just like Ruby and JavaScript, jQuery also has iterators. They work in much the same way as the iterators we've already studied, but jQuery's let us manipulate the DOM. Feel free to copy and paste the examples below into `index.html` and `script.js` to try them out!

## `$.each`

Let's say we have an array of names, and we want to iterate over them to say hello:

```js
var names = ["Carleton", "Avi", "Azat", "Ann"]
```

jQuery has a built in iterator that lets us iterate over **plain JavaScript arrays**:

```js
$.each(names, function(index, name){
  console.log("hey " + name);
});
```

`$.each` accepts two parameters, the array to iterate over and a function that contains the actions to be taken with each item in the array. This anonymous function accepts two parameters: the index of the array and a variable placeholder to represent each item individually.

The first time iterating over the `names` array, `index` is storing 0 and `name` is storing `"Carleton"`.

## `.each`

`.each` is only different from `$.each` because it works on a collection of jQuery objects instead of a plain JavaScript array.

Let's say we have three divs on a page, and we want to print the div number inside each div using jQuery.

HTML:
```html
<div>
</div>
<div>
</div>
<div>
</div>
<div>
</div>
```
We can use the jQuery selector `$('div')` which will return us an array of jQuery objects.

We can iterate over this array using `.each` and use it to append the div number to the body of the div:

```js
$('div').each(function(index, div){
  $(this).append("this is div number " + (index + 1));
});
```

The `.each` function accepts a function as a parameter. The function accepts two parameters, a variable to represent the index of the array and a variable to represent each individual jQuery object in the array. Once inside the body of the  function, `this` represents the element of the array.


## `$.map`

Just like `$.each`, `$.map` only works on plain JavaScript arrays. Just like in Ruby, `map` in JavaScript creates a new array with the results of calling a provided function.

Let's take our first example of an array of names:

```js
var names = ["Carleton", "Avi", "Azat", "Ann"];
```

Using `$.map`, we can iterate over the names to add their programming language of choice:

```js
$.map(names, function(name, index){
   return name + " loves JavaScript"; 
});
```

You'll notice the order of the parameters in the anonymous functions are reversed. This is done to match the order of parameters in the plain JavaScript `map` function.

## `.map`

Let's say we have a list on a page, and we want to grab all the text snippets from the list to manipulate them:

```html
<ol>
  <li>Chocolate</li>
  <li>Fried Chicken</li>
  <li>Dumplings</li>
  <li>Pizza</li>
</ol>
```

We can use `.map` to iterate over the list and return an array of the text:

```js
function listIterate(){
  return $('li').map(function(index, item){
      return item.innerHTML;
  });
}
``` 

We defined a `listIterate` function. The body of the function calls `.map` on `$("li")`, which returns an array of jQuery objects representing all the list items. The important thing to note is that we have `return` in this method twice. The first `return` sets the new array as the return value of the `listIterate` function. The second `return` tells `.map` to add the text of the list item to the new array and move on to the next element in the array.

## Resources
+ [jQuery Docs](https://api.jquery.com/)

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/js-jquery-iterators'>jQuery Iterators</a> on Learn.co and start learning to code for free.</p>

<p class='util--hide'>View <a href='https://learn.co/lessons/js-jquery-iterators'>jQuery Iterators</a> on Learn.co and start learning to code for free.</p>
