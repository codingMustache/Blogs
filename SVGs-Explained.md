Table of Contents
- [A SVG is..](#a-svg-is)
- [The History of SVGs](#the-history-of-svgs)
- [Parts of an SVG](#parts-of-an-svg)
- [How to make a SVG](#how-to-make-a-svg)
- [Advance SVG Uses](#advance-svg-uses)
- [Conclusion](#conclusion)

## A SVG is..
SVG stands for scalable vector graphic. As exactly as is sounds these are scalable images that are great for responsive design. Being scalable is great because you can zoom on an SVG image and you will not get any degradation. Usually much smaller than a JPEG or a PNG. SVGs are written in XML code to produce the desired image. If you are not great with plotting points you could use Adobe creative suite to create one or an open source options are GIMP, Inkscape or Krita. Some other great use cases are they are great for creating a mask for images.
## The History of SVGs
The history of SVGs go back to the early days of the internet. Created by the World Wide Wed Consortium (W3C) in the late 90s. It was developed to create a way for developers to have vector based imaged that could be scalable and allow for responsive design. Adoption of the svg was initially very slow but when realized by developers and designers how useful an svg can be it took off.
## Parts of an SVG
An example of a SVG:
```html
<svg
     viewBox='0 0 100 100'>
     <circle
          cx='50'
          cy='50'
          r='50'
          fill='red'
     />
</svg>
```
This will render a red circle, one of the basics shapes to make an without using a drawing application. The first part of the svg is `viewBox`, which defines `min-x`, `min-y`, `width` and `height` respectively.  Moving the circle outside of the `viewBox` will cut that portion out. Since the drawing is completely scalable I find using 100 and using that a reference to percentages with plotting the rest of the numbers. Next is `cx` and `cy`, which is center x and center y plots for the circle. Then there is `r` which refers to radius of the circle. Finally, `fill` allows you to color with a few spelt out color and any hex code color.
## How to make a SVG
```html
<svg viewBox='0 0 100 100'>
    <path
        stroke='white'
        fill='none'
        d="
            M 10 10
            H 90
            V 90
            H 10
            V 10
         "
     />
</svg>
```
Thought a complex looking element this is a simple white outline of a square. The most powerful properties for SVGs is path, anything can be drawn with it. The structure of the SVG path is followed by the `d` property that defines the path to be drawn. The structure for the drawing is defining the kind of line or the starting point which is defined by `M`. The numbers are followed by `x, y` plot points. `H` and `V` or horizontal and vertical points are followed by one number moving to the next plot point. The default fill is black setting a fill to `none` will make the area transparent. To find more properties I would suggest taking a look at the [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/d) for the `d` properties such as drawing arcs and other lines/points.
## Advance SVG Uses
Some cool tricks you can use SVG with is using the `path` property in your CSS to add changes to your SVG when you hover. An example of this would be:

index.html
```html
<svg id="svg_css" viewBox="0 0 100 100">
     <path
          fill="none"
          stroke="red"
          d="
               M 100, 100
               m -100, -50
               a 50,50 0 1,0 100,0
               a 50,50 0 1,0 -100,0
          "/>
</svg>
```

stye.css
```CSS
html, body {
  height: 100%;
  width: 100%;
}
#svg_css:hover path {
  d: path(
    "M 10,10 H 90 V 90 H 10 V 10"
  );
}
```
The HTML renders a red circle, and the CSS sets a rule on the hover to change the path of the SVG to a square. This is changing the path of the object but you could potentially change or add CSS rules the any of the properties including stroke or fill color.

Another very cool thing you can do is masking. Masking is filling the background of the SVG with an image. This effect can really add a new dimension to you SVGs.
```html
<svg width="600" height="400">
     <mask id="svgmask1">
          <polygon
               fill="#ffffff"
               points="200 0, 400 400, 0 400"
          />
    </mask>
    <image
          xlink:href="cat.jpeg"
          mask="url(#svgmask1)"
     />
</svg>
```
This will render a triangle with the `cat.jpeg` being masked out by the triangle. Potentially you could add multiple shapes by the and multiple images within one SVG. This has really deep and has a endless possibility of creativity.

## Conclusion
This is just the basics of SVGs and techniques to use them to get a deeper understanding you should take a deeper dive into the [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/SVG) on SVGs; there is so much more that delved into. There is such a wide set of use cases for SVGs that solve so many developer problems and open the door for being creative. For more complex images that you might want to develop I would suggest using am art application such as Inkscape or Gimp and it will convert your vector image into an SVG.