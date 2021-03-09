<h1 class="capitalize">COMD2451</h1>
<h2 class="capitalize center">Creating a Basic Sticky Footer with CSS</h2>

---

<section class="section">
    <h2 class="sentence">What is a Sticky Footer?</h2>

***According*** to `CSS Tricks`,

> The ***purpose*** of a `sticky footer` is that it `"sticks"` to the ***bottom*** of the `browser window`. But ***not*** `always`, if there is ***enough*** `content` on the `page` to ***push*** the `footer` ***lower***, it ***still*** does that. But ***if*** the `content` on the `page` is ***short***, a `sticky footer` will ***still*** `hang` to the ***bottom*** of the `browser window`.
> <cite>-- [Sticky Footer, Five Ways](https://css-tricks.com/couple-takes-sticky-footer/) -- CSS Tricks</cite>

***No matter*** `how much` or `little` ***content*** `populates` the ***page***, the `sticky footer` will ***still*** `stick` to the ***bottom*** of the ***page***.

</section>

---

<section class="section">
    <h2 class="sentence">Creating a Sticky Footer with Flexbox</h2>

One `should` ***really*** `try` to ***avoid*** `using techniques` for ***creating*** `sticky footers` ***with*** `fixed heights`. `Fixed heights` ***usually*** are ***not*** a ***good*** thing to ***implement*** in `Web Design`. ***Fixed anything***, for ***that matter*** (though ***there are*** `exceptions` to ***rule***!).

Using `Flexbox` for a `sticky footer` ***not only*** does ***not*** `require` ***extra*** `elements`, but it ***also*** `allows` ***for*** a `footer` ***with*** a `variable height`.

We can ***set up*** the ***following*** `HTML markup` in our `index.html` and `CSS code` in our `main.css` to ***see*** **how** the ***following*** works:

The `HTML markup`:

```html
<body>
    <main class="Site-content">

    </main>
    <footer class="site-credits">© 2021 Maria D. Campbell</footer>
</body>
```

The `CSS`:

```css
html, body {
    height: 100%;
}

body {
    display: flex;
    flex-direction: column;
}

.Site-content {
    flex: 1 0 auto;
}

.site-credits {
    flex-shrink: 0;
}
```

Now let's ***add*** some ***more*** `HTML markup` to ***make for*** a ***more*** `structured`, ***realistic*** `page`:

```html
<body>
    <main class="Site-content">
        <h1>This is the main heading</h1>
        <section>
            <article>
                <h2>This is an article heading</h2>
                <p>This is some article content.</p>
            </article>
        </section>
    </main>
    <footer class="site-credits">
		<p>© 2021 Maria D. Campbell</p>
	</footer>
</body>
```

<aside>
    Note: I'll take the students into the browser to show them what this markup and associated CSS looks like as a result of the change.
</aside>

***Even though*** there is ***very little*** `content` on the ***page***, the `footer` ***still sticks*** to the ***bottom***.
</section>

---

<section class="section">
    <h2 class="sentence">Breaking down the sticky footer: the body and html elements</h2>

In the `CSS`, ***first*** we ***use*** a `grouping selector` and ***add*** the `height property declaration` ***to it***:

```css
html, body {
    height: 100%;
}
```

***Above***, we are ***making sure*** that ***both*** the `html element` and the `body element` have a `height` of `100%` ***relative*** to the `browser window` (`viewport`). We ***have*** to ***target*** those ***two*** `elements` ***with*** the `property declaration` of `height: 100%`, ***otherwise*** the `Flexbox sticky footer` ***styling*** will ***not*** `work`!

***Next***, we ***add*** a `body element selector rule set` ***containing*** the ***following*** `CSS property declarations` ***inside***:

```css
body {
    display: flex;
    flex-direction: column;
}
```

***Here***, we ***give*** the `display property` the `value` of `flex`. ***Whenever*** one ***wants*** to ***apply*** `Flexbox` to a `CSS selector`, the `display property declaration` of `display: flex` ***has*** to `be applied` ***first*** to the ***parent container***. ***Here***, the `body` is the ***parent container***.

We ***also*** `apply` the `flex-direction: column property declaration`, ***because*** we ***don't want*** the `Flexbox` ***default*** `behavior` of `row`. We ***want*** the `content` to be `displayed` ***vertically***. The `column property value` ***displays*** the `content` ***within*** the `body element` as a `column` ***instead*** of a `row`. If we ***removed*** this `property declaration`, the `content` ***would*** be ***displayed*** as a `row`.

<aside class="notes">
    Note: I will show the difference between adding flex-direction: column and removing it to the students.
</aside>

</section>

---

<section class="section">
    <h2 class="sentence">Sticky Footer and the flex shorthand property declaration</h2>

```css
.Site-content {
    flex: 1 0 auto;
}
```

The `flex property` is the ***shorthand*** for the ***following*** `CSS properties`:

+ flex-grow
+ flex-shrink
+ flex-basis

</section>

---

<section class="section">
    <h2 class="sentence">The flex-grow property</h2>

+ [flex-grow](https://cssreference.io/property/flex-grow/): ***this*** `CSS property` ***defines*** `how much` a `flexbox item` ***should grow*** if there's ***space available***. The ***default*** `value` for `flex-grow` is `0`. With a ***value*** of `0`, the `element` will ***not grow*** if there ***is*** `space` ***available***. It will ***only use*** the `space` it ***needs***.

`flex-grow` ***accepts*** a ***unitless*** `value` that ***serves*** as a `proportion`. It ***dictates*** the ***amount*** of `available space` ***inside*** the `flex container` the `item` ***should take up***.

If ***all*** `items` have a `flex-grow` ***set*** to `1,` the ***remaining space*** in the `container` will be `distributed equally` to ***all*** `children`. If ***one child*** `has` a `value` of `2`, for ***example***, the ***behavior*** of the `child` ***depends*** on the `value` of the `flexbox item` ***siblings*** (`items` ***alongside*** the ***targeted*** `flexbox item`).

If ***only one*** `Flexbox item` is ***being targeted*** with `flex-grow: 2`, and `there are` ***two*** `other items` in the ***parent*** `flexbox container`, the ***remaining space*** is `divided` in `3`. We can ***take*** a ***look*** at an [example of flex-grow on CSSReference](https://cssreference.io/property/flex-grow/) to ***better understand*** ***what*** this ***means***.

***Negative*** `numbers` are ***invalid***.

</section>

---

<section class="section">
    <h2 class="sentence">The flex-shrink property</h2>

[flex-shrink](https://css-tricks.com/snippets/css/a-guide-to-flexbox/): `flex-shrink` ***defines*** `how much` a `flexbox item` ***should shrink*** if there is ***not*** `enough space` ***available***. The ***default*** `value` for `flex-shrink` is `1`.

In our `flex` ***shorthand*** `property declaration`, the `flex-shrink` ***property value*** is `0`. This ***means*** that the ***targeted*** `flex-item` (`main element`) ***does not*** `shrink`. It will ***retain*** the `width` it ***needs***, and ***not wrap*** its `content` (which is ***what*** it ***does*** when it ***shrinks***). Its ***siblings*** (if there were ***any*** in ***our case***) will ***shrink*** to ***give space*** to the `target element` (***here*** it is the `main element`).

***Because*** the `target element` will ***not wrap*** its ***content***, there is ***also*** a ***chance*** for the `flexbox container`'s `content` to ***overflow*** (***here*** it is the `body element`).

***Negative*** `numbers` are ***invalid***.

<aside class="notes">
    Note: Show the visual example of [flex-shrink](https://cssreference.io/property/flex-shrink/) on CSSReference to the students.
</aside>

</section>

---

<section class="section">
    <h2 class="sentence">The flex-basis property</h2>

[flex-basis](https://css-tricks.com/snippets/css/a-guide-to-flexbox/): ***sets*** the ***initial*** `main size` of a `flex item`.  This ***means*** that it ***defines*** the ***default*** `size` of the `flex-item` ***before*** the `remaining space` is ***distributed***. It ***can*** be ***represented*** by a (***relative***) `length` ( ***such as*** `50%`, `3rem`, etc) ***or*** a `keyword`. The ***default*** (`keyword`) ***value*** is `auto`.

The `flex-basis property` is ***specified*** as ***either*** the `keyword` ***content*** or a `"width"`. In ***our*** `example`, we are ***specifying/targeting*** a `"width"` ***with*** the `auto keyword`.

The `auto` ***keyword*** (which is ***what*** is `being used` in the `value` of our `flex-basis property` of the `flex` ***shorthand*** `property value`), ***means*** that the `size` of the ***targeted*** `flex-item`(s) is ***determined*** `relative` to the `flex-grow` ***and*** the `flex-shrink` ***values*** `set upon` the `flex-item`(s).

If we ***set*** the ***following*** `flex shorthand` on ***two*** `flex items` ***within*** the `flex container`, for ***example***:

The `HTML` ***markup***:

```html
<ul class="flex-container">
  <li class="flex-item flex1">1</li>
  <li class="flex-item flex2">2</li>
</ul>
```
The `CSS` ***code***:

```css
.flex1 {
    flex: 1 1 auto;
}

.flex2 {
    flex: 2 2 auto;
}
```

***Initially***, ***before*** any `re-sizing` ***occurs***, the `flex-item` ***with*** the`.flex2` ***class*** is ***approximately*** `half` the `size` of the `flex-item` ***with*** the `.flex1` ***class***, ***taking*** into ***account*** any `margins` or `padding`. Its `size` is ***automatically adjusted*** by the `browser`. As the `viewport` ***increases*** in `width`, for ***example***, the `flex-item` ***with*** the `.flex2` ***class*** becomes ***relatively*** `twice` as `big` as the `flex-item` ***with*** the `.flex1` ***class***. ***That*** is ***thanks*** to the ***first value*** of `2`, ***which represents*** the `flex-grow` ***property***.

***But*** as the `viewport` ***decreases*** in `width`, the `flex-item` ***with*** the ***class*** of `.flex2` ***shrinks*** to ***approximately*** `half` the `size` of the `flex-item` ***with*** the ***class*** of `.flex1`. This is ***thanks*** to the `flex-shrink` ***value*** of `2`.

We ***shall*** `see better` ***how*** this all ***works*** when we ***start working*** with `columns`, ***primarily*** for the `portfolio` ***page***.

<aside class="notes">
    Note: show the students how auto works vs other values of flex-basis so that they understand it in the context of the sticky footer CSS. Also go to the [example from CSS Tricks on CodePen](https://codepen.io/chriscoyier/pen/PoPwPbE) so they can see the basic flex shorthand property syntax with different values and how it affects the layout on the page simply and clearly. The other CSS Trick CodePen example which is very good to show and play with in the Developer Tools Device Mode is the [flex-basis example](https://codepen.io/HugoGiraudel/pen/58ccdf09053da058e85c442cb93b0c6c).
</aside>

</section>

---

<section class="section">
    <h2 class="sentence">flex-basis: 0 <code>vs</code> flex-basis: auto</h2>

As ***mentioned earlier***, `numeric values` of the `flex` ***shorthand*** `property` are ***interpreted*** as ***specific*** `widths`, so `0` ***would*** be the ***same*** as ***specifying*** `width: 0` (and ***would collapse*** the `element` to its ***smallest possible*** `width` ***given*** its ***content***, or to `0` ***itself*** if the `content` is ***hidden***).

A `property declaration` of `flex-basis: auto` ***does not*** `define` any ***specific starting*** `width` ***for*** the `flex-item`. It is ***also*** the ***default*** `value` of the `flex-basis` ***property***.

A `value` of `auto` ***means*** that the `length` is ***equal*** to the `length` of the `flexible item`. If the `item` ***itself*** has `no length` ***specified***, the `length` will be ***according*** to its ***content***. This `concept` is ***similar*** in a way to ***using*** the `auto `***keyword*** as the `value` of the `margin` ***properties***. ***Like*** `margin-right: auto` or `margin-left: auto`.

</section>

---

<section class="section">
    <h2 class="sentence">Making the footer "prettier"</h2>

***Now*** that we ***have made*** the `footer` ***stick*** to the `bottom` of the `page` no matter ***how much*** or ***little content*** `populates` the ***page***, we can ***apply*** a ***bit*** of `styling` to it to ***make it*** `"prettier"`.

```css
.site-credits {
	color: inherit;
	flex-shrink: 0;
    font-size: 1.2rem;
    text-align: center;
}
```

***Here***, the `inherit value` for the `color property` will ***simply*** be the `default color` ***set*** by the `user-agent` (`browser`), ***because*** I did ***not apply*** the `color property` on the `body element selector` (***which is*** the `parent` of the `footer element`). ***That*** `color` is `black`.

***Next***, I ***applied*** the `font-size: 1.2rem;` ***property declaration*** to ***increase*** the `size` of the `footer font`, ***because*** the ***default*** was ***too small***. ***Using*** `rem` ***instead*** of `px` (***pixels***) ***means that*** the `font size` of the `footer` will `adapt` ***relative*** to the `viewport size`.

In my ***final*** `CSS` for the `footer` ***itself***, I ***don't add*** the `color: inherit;` ***property declaration***. This was ***just*** for the ***purpose*** of the `demo` so that you ***better understand*** what the `inherit property value` ***does***.

<aside class="notes">
	Note: Show the students what I mean by the `footer font` adapting ***relative*** to the `viewport size` by demonstrating what it looks like on **various devices** in `Chrome Developer Tools`.
</aside>

</section>

---

<section class="section">
    <h2 class="sentence">Related Resources</h2>

+ [What is a sticky footer?: stackoverflow](https://stackoverflow.com/questions/4520505/what-is-a-sticky-footer)

+ [Sticky footers: MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Sticky_footers)

+ [A Complete Guide to Flexbox: CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

+ [flex: CSS Tricks](https://css-tricks.com/almanac/properties/f/flex/)

+ [flex-basis: MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis)

+ [The difference between flex-basis auto and 0 (zero) [duplicate]: stackoverflow](https://stackoverflow.com/questions/47578958/the-difference-between-flex-basis-auto-and-0-zero/47579078)

+ [flex-basis: CSS Tricks](https://css-tricks.com/almanac/properties/f/flex-basis/)

+ [flex-shrink: cssreference](https://cssreference.io/property/flex-shrink/)

+ [CSS Flexible Box Layout Module Level 1: W3C](https://www.w3.org/TR/css-flexbox/#main-size)

</section>
