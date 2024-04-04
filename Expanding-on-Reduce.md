#### How 'Reduce', a high order function, works in Javascript
Javascript’s reduce function is is a helpful tool to execute useful tasks. From adding an array, to finding averages of an array, to creating a well formatted object from an array, to even flattening an array --it can really be the Swiss army knife of javascript functions. The key to using reduce is truly understanding how it works. This article will go over how to dissect the reduce method, how to use reduce, as well as how to use cases for the reduce method.

### Recreating Reduce
The first thing to know is that reduce takes in a user passed callback function that loops over elements in an array. The callback function takes in an accumulator, a current value, index, and the collection.To build reduce you also need to know that it takes in a ‘seed’ value that can be a starting value of the loop or even set to an output datatype. The example below shows how reduce works

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zqobkj6xcny62h6n6ad2.png)

### How reduce works
The call back function is a key part of how reduce works. In the example below is a simple addition of all the values in the array. Like in any method, the correct syntax for using reduce involves putting the array that you would like to pass through, followed by a period and the call back function. After that, if you'd like, you can include the seed. For example, in the case below, the seed is zero, however, without it you would get the same result.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ibw33ekha49fganyjs0t.png)

The call back function has 4 parameters that can be used to execute the action you are trying to execute:

- Accumulator: Always starts off with the value of the seed. 
- CurrentValue: Is the 1st value in the array
- Index: The index of the current value that is being passed 
- Array: The entire collection

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5f96l9h2p2wck9vow3l2.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s39f6u7gw3amgz7ueah3.png)

### Use Cases for Reduce
Above we learned how to use the reduce method to find the sum of an array. However, that is only one way to use reduce. In fact, the reduce method can serve many purposes. For example, it can find an average, return objects from an array, return odd numbers from an array, and even flatten or filter.

#### Creating an Object

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wl8di5byzwzbpjbnovyw.png)

Sometimes passing your array through reduce into an object can be a very useful way to use reduce. The result variable takes the array pets and reduces it into an object with the amount of time that the element is repeated in the array. Since the accumulator takes the value of seed at the first iteration of the callback function and then passes the key plus one in the key and property in the accumulator. At each iteration it will check for the key and add one if the key is not there.

#### Average

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/guizs5ot377k4s4ijkau.png)

Finding the average of the array is a great example of using all the parameters in the callback function. Using array.length can help you find the end of the array and the index can signify what index reduce is on in its loop. In an if loop you execute the accumulator divided by the amount of elements in the array and the return of that would give you an average.

#### Flatten

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eux1tltasprn2heboyro.png)

Though there is a flatten function, reduce can also accomplish flattening nested sub-arrays by using concat and taking the elements in the sub-array into the accumulator. Assigning the seed to an empty array is not necessary to run the reduce as intended in this case because if you leave out it will pass the elements into the first array. 

#### Filter

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l8ormwxe8eeczz6kh4aq.png)

By creating a conditional it will pass the true current values into the accumulator recreating a filter function. Using the other argument, index or array, you can also use it to pass certain indexes, like odd or even placements, an nth  place in the array or a combination of conditionals. 


### Conclusion
The reduce method can be one of the more versatile functions in your javascript arsenal. However, while you can use it to replace other functions in Javascript, it can also make your code less clean, so it's important to know the aforementioned functions. At the same time, if you are in a pinch, the multi-tool functions can come in very handy.