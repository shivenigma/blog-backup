## A Deep Dive into Javascript Array Methods - Part 1

Javascript is great, it is single-threaded but fast enough for most use cases, it is easy to get started with but hard to master. 2019 has been great for Javascript and 2020 is not going to be any different. In this context, I am focusing more on writing beginner-friendly articles on Javascript this year.

In Javascript, we mainly use two data types arrays, and objects. Technically arrays are also objects in javascript, they have some prototype methods for traversing and mutating arrays (more on that is for another blog post). To work with arrays javascript has a lot of methods and sometimes it can be overwhelming to figure out which method does what and what arguments it takes, whether it modifies the original array or it creates and returns a new array. 

In this post, I am going to explain some of the most used array methods based on how I understood them. I have also seen people use different methods for different purposes, like using map/filter to loop over an array, it works but that's not it meant to be used for. Hopefully, after reading this series of posts you should be able to pick up any trivial use case and work with the right JS method for it.

I originally planned to write this as a single blog post but after seeing the amount of information need to be put for each array method, I split it into a series of blog posts, because too much information within a single blog post will be overwhelming. This is the first part of the series.

## 1) You want to loop over an array (forEach)
array.forEach is the semantically correct method for this purpose, I have seen many people use the map as well, both works. But map means that you're somehow modifying the original array and forEach means you don't.

When I say about modifying an array, I am not saying that it is not possible, I rather mean it should be avoided. To keep your code clean and to easily let other devs know your intention of a code block.

```
const names =["Javascript", "Python", "PHP", "Flutter"];
names.forEach(name => {
	console.log(name);
});

// OUTPUT
// > Javascript
// > Python
// > PHP
// > Flutter
``` 

The above code loop over an array and prints each element in the console. This is a very basic implementation of forEach.

### Method Signature


```
arr.forEach(callback, [, thisArg]);
// thisArg is optional for forEeach

// the callback has the following arguments in forEach.
callback(currentValue, [, index [, array]])
// index and array are optional
``` 


**callback -** The function which will be called once for each element in the array.

**currentValue** - The current element that is being iterated in the array

**index** (optional) - The index of the current element in the array

**array** (optional) - The array that is being traversed

**thisArg -** This is interesting before ES6 arrow functions. you can specify something that can be used as this inside the callback function. If you don't pass thisArg, the value of this will be determined similar to [how a function's this will be determined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this).

### Things to remember
- forEach does not mutate the array which is being traversed, but the callback can do it. (I recommend not doing it for obvious reasons mentioned down below).
- If the array is modified when forEach is running, some elements might be skipped as forEach doesn't make a copy of the array [(Example)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach#If_the_array_is_modified_during_iteration_other_elements_might_be_skipped.).
- Elements that are appended after the forEach has started will not be traversed.
- undefined, uninitialized values in the array will not be traversed in forEach.
- forEach is not chainable because it returns undefined.
- Early termination out of forEach is not possible, you can only throw an exception. If you need early termination, use for or for.. in loop.
- If callback is an arrow function, thisArg can be ignored as arrow functions lexically bind to this value.

## 2) You want to transform an array in some way
Transforming means that you're creating a new array by applying some sort of transformation to each element in the original array. let's add numbers to the languages array we used in our previous forEach example.


```
const names =["Javascript", "Python", "PHP", "Flutter"];
const newNames = names.map((name, index) => {
	return index.toString() + '. ' +name;
});
console.log(newNames);
// OUTPUT : Array ["0. Javascript", "1. Python", "2. PHP", "3. Flutter"]
``` 


In both cases above, you're probably trying to do something else for which, the map is the right way.

### Method Signature


```
let newArray = arr.map(callback, [, thisArg]); // thisArg is optional
callback(currentValue, [, index, [, array]]); // index and array are optional

// the callback must return an element for the new array after applying any transformation
``` 


**callback -** The function which will be called once for each element in the array.

**currentValue** - The current element that is being iterated in the array.

**index** (optional) - The index of the current element in the array.

**array** (optional) - The array that is being traversed.

**thisArg -** This is the same as we saw for forEach, used to refer this value inside the callback.

Map receives a function as the first argument and an optional index as the second argument, in the callback function you'll receive each item in the array as an argument and you must return the element after applying your transformation. 

### Things to remember
- You should not use the map in either case below,
    1. You're not using the newly created array that the map returns.
    2. You're not returning anything from the callback.
- the map does not mutate the array which is being traversed, but the callback can do it. (In short, don't do it to avoid unintended consequences).
- Elements that are appended after the map has started will not be traversed.
- The map is chainable with other array methods.
- Early termination out of the map is not possible. If you need early termination, you're using the map in the wrong place.
- The callback must return value otherwise the result array will be an array of undefined values.
- If callback is an arrow function, thisArg can be ignored as arrow functions lexically bind to this value.

These two are some of the frequent use cases I often come across in day to day work. I tried to write it simply as possible to my understanding and I hope you find this useful. If you think if something has to be added to the post feel free to let me know in the comments. Try to play with these two methods a little bit if you find them difficult or confusing. Remember, practice is what makes things stick in your memory not just reading.
