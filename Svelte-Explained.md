Svelte is a framework like no other, and according to Stack Overflow it’s the world’s most loved framework in 2021 [[1]](https://insights.stackoverflow.com/survey/2021#most-loved-dreaded-and-wanted-webframe-love-dread). The documentation Svelte is absolutely so well written, and there is even a interactive IDE that can help you get started on understanding Svelte. The framework’s main focus is on letting you write less code while still being very versatile, lightweight and letting the compiler, Svelte Kit, do the heavy lifting. It is a component driven framework that uses HTML templates that that you write javascript or typescript directly into the `.svelte` file.

You can have access to writing Svelte by either using the CDN link or the or installing the project though node. The easiest way to install svelte is by running the commands:
```
npm create svelte@latest my-app
cd my-app
npm install
npm run dev -- --open
```
This will get you a template to start your 1st project. Building a simple “Hello World” is as simple as writing regular HTML and boom you have written your 1st svelte. It handles javascript in the in script tags and passes the variable to the the HTML by wrapping the variable name in `{}`.
```
<script>
const name = "Jorge"
</script>
<p>Hello {name}!</p>
```
As simple as that your page will now have "Hello Jorge". Styles are written a inside a style tag and it is not affected by other imports that might share the same tags. This helps with modularity of Svelte. All on the same svelte file. To understand how to to add event handlers [here](https://svelte.dev/repl/f9e5429cd9d343179a44478587a11747?version=3.49.0) is a link to something I made in a Svelte REPL. The action `on:click` with the name of the function will call that function when the click is made. Svelte also has special syntax to write directly in your HTML that can use logic like IF blocks that looks like this:
```
<script>
	let toggler = { on: false };

	function toggle() {
		toggler.on = !toggler.on;
	}
</script>

{#if toggler.on}
	<button on:click={toggle}>
		ON
	</button>
{/if}

{#if !toggler.on}
	<button on:click={toggle}>
		OFF
	</button>
{/if}
```
This code has a two buttons that toggle each other when on is clicked it switches to off using the if block logic in the code.


Svelte components are just separate svelte files that are exported from the file into others. When exporting just use the export keyword and you now have access to the exported svelte file to the the file you import it at. The imported file also has access to variables that you might want to use in your code. That looks something like [this](https://svelte.dev/tutorial/declaring-props). This can leads to a very modular design process similar to React. 

This is just a brief introduction into Svelte but there is so much more and all can be learned with ease. [Wes Bos](https://twitter.com/wesbos) is such a great resource on the topic and I encourage you to check out his podcast [Syntax](https://syntax.fm/) and his [tutorials](https://leveluptutorials.com/) page as well. Svelte also has a [Discord](https://discord.com/invite/yy75DKs) with a great community. I hope this article launches you to take a deeper dive into the framework. 


Some Useful Links:
[Svelte's Official Website](https://svelte.dev/)
[SvelteKit's Website](https://kit.svelte.dev/)
[MDN Docs](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_getting_started)