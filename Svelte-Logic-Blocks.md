## Table Of Contents
 * [Intro to Logic](#chapter-1)
 * [If/ Else/ Else IF Blocks](#chapter-2)
 * [Each Blocks](#chapter-3)
 * [Key Blocks](#chapter-4)
 * [Await Blocks](#chapter-5)
 * [Conclusion](#chapter-6)


###<a name="chapter-1">Intro To Svelte Logic</a>
HTML lacks the ability to express any logic when rendering elements to the DOM. Svelte is a templating language it adds the power of Javascript and the capacity of logic right in your HTML to render the DOM in a much more sleek way. This really relieves a huge amount of code that would have to be written in other frameworks. There are 4 types of logic blocks that, if/ else/ else if, each, key and await blocks. All have a different use case. The general syntax for this would look something similar to this:
```svelte
{#logic block}
<html-element/>
{/logic block}
```

###<a name="chapter-2">If/ Else/ Else IF Blocks</a>
If you know this form of logic block from knowing JavaScript, the idea is not much different. You can use a conditional to render and element on a page. Similarly to JS you can chain conditionals together to render corresponding elements to the page. 
```svelte
{#if temp < 60}
<p>Grab a Jacket</p>
{:else if temp < 70}
<p>Perfect Weather</p>
{:else}
<p>Wear some Shorts</p>
{/if}
```
The example above is a simple lesson on how the logic blocks are constructed within the html. These logic blocks can be chained together with as many `else if` blocks as you like. 
 
###<a name="chapter-3">Each Blocks</a>
The Each block is used to to iterate over an arrays or objects within an array to render your elements based on the values. This can create many elements with the same template. The each block will pas the values from the array into the Dom element, and alike to `.map()` you can also provide you with an index in the rendering if you choose to use it. An example use looks like this:
```Javascript
 let names = [
   { id: '123', name: 'Jorge' },
   { id: '456', name: 'Clare' },
   { id: '789', name: 'John' }
 ];
```
```html
<ul>
 {#each names as ppl , i}
  <li>
   num: {i}
   Id: {ppl.id}
   Name: {ppl.name}
  </li>
 {/each}
</ul>
```
Which renders: 
```
num: 0 Id: 123 Name: Jorge
num: 1 Id: 456 Name: Clare
num: 2 Id: 789 Name: John
```
###<a name="chapter-4">Key Blocks</a>
Key blocks are a relatively new feature in svelte and arguably one of the more elegant logic blocks. This logic can re-render your DOM element based on a value changes. It also works naturally with transition animations in svelte. So something like this:
```javascript
import { fade } from 'svelte/transition'
let i = 0;
function count(){
  i++
  setTimeout(count, 1000)
}
count()
```
```html
{#key i}
<p transition:fade> {i} </p>
{/key}
```
Will add a fade in animation that uses the count function in the javascript that endlessly counts at one second intervals.

###<a name="chapter-5">Await Blocks</a>
The Await block works with promises and with that there are three expressions that are used: promise, then and catch. This is great for server side rendering. This really is one of the more complex items to implement in other frame works and Svelte makes this so easy. The syntax for this looks like this:
```html
{#await promise}
 <p>waiting...</p>
{:then value}
 <p>The value is {value}</p>
{:catch error}
 <p>{error.message}</p>
{/await}
```
###<a name="chapter-6">Conclusion</a>
This is a basic summary of the way the logic blocks work in svelte I implore you to look at the documentation over at [Svelte](https://svelte.dev/docs) to get an even deeper understanding on how they work and how to use them. They are a critical part of why I believe svelte is such a great framework.

####Links to the Docs
#####[IF/ Else/ Else If](https://svelte.dev/docs#template-syntax-if)
#####[Each](https://svelte.dev/docs#template-syntax-each)
#####[Key](https://svelte.dev/docs#template-syntax-key)
#####[Await](https://svelte.dev/docs#template-syntax-await)