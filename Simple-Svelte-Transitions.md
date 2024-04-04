
Table of Contents:
- [Fade](#fade)
- [Blur](#blur)
- [Fly](#fly)
- [Slide](#slide)
- [Scale](#scale)
- [Draw](#draw)


&nbsp; &nbsp; Svelte has its own built in transitions that are very easy to use. The transitions are very customizable, they have a couple parameters in common, `delay`, `durarion` and `easing`. All have default values that can be used with out out. Transions are a great way to give your website/app some pazza. The general way to get most of these working just to see what works for you can be something like this: 
```html
<script>
import { fade, blur, fly, slide, scale} from 'svelte/transition';

let i = 0 

const handleClick = () => { i++ };

</script>

<div>
  <button on:click='{handleClick}'> ADD </button>
  {#key i }
    <div transition:TRANSITION_NAME="{{duration: 300}}">
      { i }
    </div>
  {/key}
</div>
```
To test this you would change `TRANSITION_NAME` to one of the imported transitions. This would render a number and add to `i`, the change would show the transition. Adding some CSS rules to keep the `fixed` would make some transitions look better, such as scale and blur. This example is a simple property change that trigger the rerendering of the element, but you could do this with components as well.

<a name='fade'>
#Fade
</a>

&nbsp; &nbsp; Fade can take in parameter of `delay`, `duration`, and `easing`. The delay is how many milliseconds that before the transition starts, the default is set at 0. Duration is how long the transition last for in milliseconds. The easing takes in a svelte easing function more information can be seen [here](https://svelte.dev/docs#run-time-svelte-easing). An example of fade looks like this:


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/d3z7c42536kqqn3polak.gif)

[Tutorial](https://svelte.dev/tutorial/transition)

[Docs](https://svelte.dev/docs#run-time-svelte-transition-fade)

<a name='blur'>
#Blur
</a>

&nbsp; &nbsp; Blur blurs in/out the element that is being rendered. This are some more paramters that blur takes in, `delay`, `durarion` and `easing` just like fade but the other 2 are `opacity` and `amount`. The opacity is the will animate in and out of, and amount is the size of the blur.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1kh8edzprhelwjyvao36.gif)

[Docs](https://svelte.dev/docs#run-time-svelte-transition-blur)

<a name='fly'>
#Fly
</a>
&nbsp; &nbsp; The Fly transition moves one element from an x and y position into frame over last element. This can take a `in:fly` and an `out:fly` with parameters passed in. `delay`, `duration`,`easing` `opacity` and adding a `x` and `y`. X and Y move newly rendered element from and into the position using the axis. You can make it look like this: 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/22llekorka1cmvg3h6x7.gif)  

[Tutorial](https://svelte.dev/tutorial/adding-parameters-to-transitions)

[Docs](https://svelte.dev/docs#run-time-svelte-transition-fly)

<a name='Slide'>
#Slide
</a>
&nbsp; &nbsp; &nbsp; Slide renders element in and out of the frame. Like Blur it takes in `delay`, `duration` and an `easing` function. This is a very simple transition to implement and simple looking animation. An example looks like this: 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/z9ilar30b1d656qu63zo.gif) 

[Docs](https://svelte.dev/docs#run-time-svelte-transition-slide)

<a name='scale'>
#Scale
</a>
&nbsp; &nbsp; Scale renders element in and out from the z index and grows. It takes in `delay`, `duration`, an `easing` function, `start` and `opacity`. Start scales the element initial size. An example looks like this: 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tpsgwqzxktw7o2o1v63z.gif)

[Docs](https://svelte.dev/docs#run-time-svelte-transition-scale)

<a name='draw'>
#Draw
</a>
&nbsp; &nbsp; The draw animation is a one a little more complex but can be very fun to implement. This is used for drawing out SVG in a path. It can be used in something like an icon or an image on the page that you would would to give more of a fancy and fun look. Parameters that it takes in are `delay`, `speed`, `duration` and an `easing` function. You Svg needs a path and not just a drawn on shape or icon. The transition is invoked in the path parameter in the SVG. A simple implementation looks like this:


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tsodjj6acf7ze5dzndl9.gif)  

[Docs](https://svelte.dev/docs#run-time-svelte-transition-draw)

&nbsp; &nbsp; This is just a simple introduction in svelte transitions. To urge you take take a deeper dive into the tutorials that svelte has to offer. The REPL that they have to show you how to use the transition is an easy way to test a transition before implementation. Playing with Animations and getting a feel for them and understanding how to use it and really getting a feel for what it looks like is important.