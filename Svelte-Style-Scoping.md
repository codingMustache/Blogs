## Table of Contents

- [How Svelte Styling Works](#works)
- [Component based Styling](#components)
- [Global Tag](#global)
- [External Sylesheet](#sheet)
- [Sources & Resources](#source)

&nbsp; &nbsp; Svelte is a relatively new framework/templating language that has a particular way of styling components. This blog was written at the time Svelte version 3.x and SvelteKit was being used. Things have changed from alpha and I'm sure will change with newer versions. Before you continue reading you should have a basic understanding of components, javascript, html and css. If you need some deeper understanding about Svelte check out my other blog post about Svelte. Styling is in Svelte is really fun and interesting. I learned a lot just getting into it on my first personal project with it and I realized there is a lot to understanding on how it works.


<a name='works'>
## How Svelte Styling Works
</a>

&nbsp; &nbsp; Understanding what Svelte is doing on the backend is key to understanding how to style your components. Svelte components styles are scoped per component and this is because svelte takes advantage of the way styling works. There are three ways to apply styling rules into your svelte code:

- Component
- Global
- Style Sheet

&nbsp; &nbsp; Each of these have there own set of rules they follow. To style an element in CSS, the specificity will always override the style rules from the parent object or less explicit style rule. Svelte does styled components by attaching a hash to the class name and passing the styles written per component to the elements. So an example of a svelte made html elements would look like this:


```html
<ul class="s-V0aBpCfzfs-B">
	<li class="s-V0aBpCfzfs-B">1</li>
	<li class="s-V0aBpCfzfs-B">2</li>
	<li class="s-V0aBpCfzfs-B">3</li>
</ul>
```

&nbsp; &nbsp; This `<ul>` element is in the same component but I made two `<ul>` components exactly the same with different styling, the components would maintain their individual styles. This is because in the back-end Svelte is adding the hashed class into the styling rules. Understanding what Svelte does on the back-end will help you understand on how to apply style rules that best work for you. I will go from the most specific to the to the most general ways of styling a svelte component. Starting with the Component based styling.


<a name='components'>
### Component based Styling
</a>

&nbsp; &nbsp; This style option it what gives svelte its pizazz. A svelte component has three major parts the first is the script which is where the javascript lives, then the html is and then theres the styling. So a typical component looks like this:

```html
<script>

	let i = 'Hello World!'

</script>

<p> { i } </p>

<style>

	p{
		color: green;
	}

</style>
```

This will render:
```html
<p style='color: green'>Hello World!</p>
```
&nbsp; &nbsp; Then this component is imported into another the styling will be unaffected. This is because the backend of svelte is creating a hash class name and making a style rule based on the hash class name. This is utilizing the CSS specificity that overrides the general CSS rules. This is great if your component needs some rules that you don't need applied to other similar elements. Rules made here are for the most specific rules that you need applied to your html.
Another interesting thing you could do with your styling is use your javascript variables in your style tag by adding `var( --i)`. This add some dynamics to your svelte styling. An example of that looks like this that would render the same component as above looks like this:

```html
<script>

	export let color = 'green!'

</script>

<p style='--passed: {color}'>Hello World!</p>

<style>

	p{
		color: var(--passed);
	}

</style>
```

<a name='global'>
### The Global Tag
</a>

&nbsp; &nbsp; An amazing tool in your svelte arsenal is applying `:global()` rules. As said above rules made in a component override any other styling rules. The global tag is used to apply rules to elements that may not carry a certain rule for for that specific element. In other words `:global()` will not override rules applied to a component. This is helpful to know when styling. A great use case for the global tag is CSS reseting or setting general style to your page, such as fonts. To use it you would do something like this:

```css
:global(*){
	margin: 0px;
	font-family: 'comic-sans':
}
```

<a name='sheet'>
### Using a Style Sheet
</a>

&nbsp; &nbsp; Using an external stylesheet is the last way to apply styling rules to your svelte. This is done just as you would add an external stylesheet to most frameworks. To have them applied you have to import the `style.css` in your component. Similarly to `:global()`, these rules are applied globally when imported to the root svelte file. The import is added like so:

```javascript
import "/path/to/style.css";
```

&nbsp; &nbsp; Conclusively, this blog gives you better tools to build a take a deeper dive into svelte. Understanding how style scoping in svelte works is key to understanding how to build a better more dynamic web application. There is component based styling, using the global tag and using an external style sheet. These three styling method have their own use case. A tip I would give after build my first project is style from furtherest scope to the most specific component styling. This method helps to not build clashing rules, and understanding where rules come from.

<a name='source'>
## Sources & Resources:
</a>

&nbsp; https://svelte.dev/docs

&nbsp; https://svelte.dev/tutorial/style-directive

&nbsp; https://issuecloser.com/blog/how-svelte-scopes-component-styles

&nbsp; https://css-tricks.com/what-i-like-about-writing-styles-with-svelte/

&nbsp; https://progressivewebninja.com/a-guide-to-css-in-svelte-and-conditional-styling/