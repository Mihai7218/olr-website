+++
title = "Demo Page"
+++

# Demo Page

{% alert(note=true) %}
This is a demo of most of the components, but some of them are only accessible on specific pages. If you wish to see them, follow one of these:

- [Blog Demo](@/blog/_index.md)
- [Post Demo](@/blog/the-quill-of-duck/index.md)
{% end %}

## Markdown

Text can be **bold**, *italic*, ~~strikethrough~~, and ***~~all at the same time~~***.

[Link to another page](@/demo/page.md).

There should be whitespace between paragraphs[^1].

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6

This is a normal paragraph[^2] following a header.

😭😂🥺🤣❤️✨🙏😍🥰😊

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

> "Original content is original only for a few seconds before getting old"
> > Rule #21 of the internet

- Item 1
- Item 2
  - Item 2.1
  - Item 2.2
- Item 3
- `Item 4`

1. Perform step #1
2. Proceed to step #2
3. Conclude with step #3

- [ ] Milk
- [x] Eggs
- [x] Flour
- [ ] Coffee
- [x] Combustible lemons

![Male mallard duck](https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Male_mallard_duck_2.jpg/800px-Male_mallard_duck_2.jpg)

| Mare         | Rating            | Additional info  |
| :----------- | :---------------- | :---------------  |
| Fluttershy   | Best pone         | Shy and adorable |
| Apple Jack   | Good pone         | Honest and nice  |
| Pinkie Pie   | Fun pone          | Party horn!      |
| Twilight     | Decent pone       | Neeerd           |
| Rainbow Dash | Annoying pone     | Looks badass     |
| Rarity       | Fancy pone        | Sometimes nice   |

```rust
let highlight = true;
```

```scss, linenos, linenostart=10, hl_lines=3-4 8-9, hide_lines=2 7
pre mark {
  // If you want your highlights to take the full width
  display: block;
  color: currentcolor;
}
pre table td:nth-of-type(1) {
  // Select a colour matching your theme
  color: #6b6b6b;
  font-style: italic;
}
```

***

## Extra

### Shortcodes

Duckquill provides a few useful [shortcodes](https://www.getzola.org/documentation/content/shortcodes/) that simplify some tasks. The can be used on all pages.

#### Alerts

[GitHub-style](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts) alerts. Simply wrap the text of desired alert inside the shortcode to get the desired look.

Available alert types:

- `note`: Useful information that users should know, even when skimming content.
- `tip`: Helpful advice for doing things better or more easily.
- `important`: Key information users need to know to achieve their goal.
- `warning`: Urgent info that needs immediate user attention to avoid problems.
- `caution`: Advises about risks or negative outcomes of certain actions.

```jinja2
{%/* alert(note=true) */%}
-> Alert text <-
{%/* end */%}
```

{% alert(note=true) %}
Useful information that users should know, even when skimming content.
{% end %}

{% alert(tip=true) %}
Helpful advice for doing things better or more easily.
{% end %}

{% alert(important=true) %}
Key information users need to know to achieve their goal.
{% end %}

{% alert(warning=true) %}
Urgent info that needs immediate user attention to avoid problems.
{% end %}

{% alert(caution=true) %}
Advises about risks or negative outcomes of certain actions.
{% end %}

#### Images and Videos

By default images and videos come with some generic styling, such as rounded corners and shadow. To fine-tune these, you can use shortcodes with different variable combinations.

Available variables are:

- `url`: URL to an image.
- `url_min`: URL to compressed version of an image, original can be opened by clicking on the image.
- `alt`: Alt text, same as if the text were inside square brackets in Markdown.
- `full`: Forces image to be full-width.
- `full_bleed`: Forces image to fill all the available screen width. Removes shadow, rounded corners and zoom on hover.
- `start`: Float image to the start of paragraph and scale it down.
- `end`: Float image to the end of paragraph and scale it down.
- `pixels`: Uses nearest neighbor algorithm for scaling, useful for keeping pixel-art sharp.
- `transparent`: Removes rounded corners and shadow, useful for transparent images.
- `no_hover`: Removes zoom on hover.

```jinja2
{{/* image(url="image.png", alt="This is an image" no_hover=true) */}}
```

<figure>
{{ image(url="https://i1.theportalwiki.net/img/2/23/Ashpd_blueprint.jpg", alt="Portal Gun blueprint", no_hover=true) }}
<figcaption>Image with an alt text and without zoom on hover</figcaption>
</figure>

<figure>
{{ image(url="https://upload.wikimedia.org/wikipedia/commons/b/b4/JPEG_example_JPG_RIP_100.jpg", url_min="https://upload.wikimedia.org/wikipedia/commons/3/38/JPEG_example_JPG_RIP_010.jpg", alt="The gravestone of J.P.G.", no_hover=true) }}
<figcaption>Image with compressed version, an alt text, and without zoom on hover</figcaption>
</figure>

Alternatively, you can append the following URL anchors. It can be more handy in some cases, e.g such images will render normally in any Markdown editor, opposed to the Zola shortcodes.

- `#full`: Forces image to be full-width.
- `#full-bleed`: Forces image to fill all the available screen width. Removes shadow, rounded corners and zoom on hover.
- `#start`: Float image to the start of paragraph and scale it down.
- `#end`: Float image to the end of paragraph and scale it down.
- `#pixels`: Uses nearest neighbor algorithm for scaling, useful for keeping pixel-art sharp.
- `#transparent`: Removes rounded corners and shadow, useful for transparent images.
- `#no-hover`: Removes zoom on hover.

<br />
<figure>

![Toolbx header image](https://containertoolbx.org/assets/toolbx.gif#full#pixels#transparent#no-hover)
<figcaption>Full-width image with an alt text, pixel-art rendering, no shadow and rounded corners, and no zoom on hover</figcaption>
</figure>

<br />

![1966 Ford Mustang coupe white](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/1966_Ford_Mustang_coupe_white_003.jpg/320px-1966_Ford_Mustang_coupe_white_003.jpg#start)
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim aeque doleamus animo, cum corpore dolemus, fieri tamen permagna accessio potest, si aliquod aeternum et infinitum impendere malum nobis opinemur.

\
[![Picture of the magnificent lej da staz just before sunrise in october](https://images.unsplash.com/photo-1635410773896-da585e1fe138?q=80&w=2063&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D#full-bleed)](https://unsplash.com/photos/a-mountain-lake-surrounded-by-trees-and-snow-CqTOTZh5vrs)

For videos it's all the same except for a few differences: `no_hover` and `url_min` variables are not available.

```jinja2
{{/* video(url="video.webm", alt="This is a video") */}}
```

<figure>
{{ video(url="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.webm", alt="Red flower wakes up") }}
<figcaption>WebM video example from MDN</figcaption>
</figure>

<figure>
{{ video(url="https://upload.wikimedia.org/wikipedia/commons/transcoded/0/0e/Duckling_preening_%2881313%29.webm/Duckling_preening_%2881313%29.webm.720p.vp9.webm", alt="Duckling preening", full_bleed=true) }}
<figcaption>Duckling preening</figcaption>
</figure>

#### CRT

Alright, this one doesn't simplify anything, it just adds a CRT-like effect around Markdown code blocks.

```jinja2
{%/* crt() */%}
-> Markdown code block <-
{%/* end */%}
```

{% crt() %}

```
 _____________________________________________
|.'',        Public_Library_Halls         ,''.|
|.'.'',                                 ,''.'.|
|.'.'.'',                             ,''.'.'.|
|.'.'.'.'',                         ,''.'.'.'.|
|.'.'.'.'.|                         |.'.'.'.'.|
|.'.'.'.'.|===;                 ;===|.'.'.'.'.|
|.'.'.'.'.|:::|',             ,'|:::|.'.'.'.'.|
|.'.'.'.'.|---|'.|, _______ ,|.'|---|.'.'.'.'.|
|.'.'.'.'.|:::|'.|'|???????|'|.'|:::|.'.'.'.'.|
|,',',',',|---|',|'|???????|'|,'|---|,',',',',|
|.'.'.'.'.|:::|'.|'|???????|'|.'|:::|.'.'.'.'.|
|.'.'.'.'.|---|','   /%%%\   ','|---|.'.'.'.'.|
|.'.'.'.'.|===:'    /%%%%%\    ':===|.'.'.'.'.|
|.'.'.'.'.|%%%%%%%%%%%%%%%%%%%%%%%%%|.'.'.'.'.|
|.'.'.'.','       /%%%%%%%%%\       ','.'.'.'.|
|.'.'.','        /%%%%%%%%%%%\        ','.'.'.|
|.'.','         /%%%%%%%%%%%%%\         ','.'.|
|.','          /%%%%%%%%%%%%%%%\          ','.|
|;____________/%%%%%Spicer%%%%%%\____________;|
```

{% end %}

There's also a `cursor` class that you can add to a span with e.g. `█` character to simulate the terminal cursor. It doesn't work from inside Markdown code blocks though.

### Description List (`<dl>`)

```html
<dl>
<dt>Something</dt>
<dd>And its description</dd>
</dl>
```

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

### Form Input (`<input>`)

```html
<input type="checkbox" />
<label>Checkbox</label>
```

<ul>
  <li>
    <input type="checkbox" />
    <label>&nbsp;Milk</label>
  </li>
  <li>
    <input type="checkbox" />
    <label>&nbsp;Eggs</label>
  </li>
  <li>
    <input type="checkbox" />
    <label>&nbsp;Flour</label>
  </li>
  <li>
    <input type="checkbox" checked />
    <label>&nbsp;Coffee</label>
  </li>
  <li>
    <input type="checkbox" disabled />
    <label>&nbsp;Combustible lemons</label>
  </li>
</ul>

With `radio` type:

```html
<input type="radio" name="test" />
<label>Radio</label>
```

<ul>
  <li>
    <input type="radio" name="test" />
    <label>&nbsp;Milk</label>
  </li>
  <li>
    <input type="radio" name="test" />
    <label>&nbsp;Eggs</label>
  </li>
  <li>
    <input type="radio" name="test" />
    <label>&nbsp;Flour</label>
  </li>
  <li>
    <input type="radio" name="test" checked />
    <label>&nbsp;Coffee</label>
  </li>
  <li>
    <input type="radio" name="test" disabled />
    <label>&nbsp;Combustible lemons</label>
  </li>
</ul>

With `color` type:

```html
<label>Color:</label>
<input type="color" value="#000000" />
```

<label for="color">Color:</label>
<input id="color" type="color" value="#b57edc" />

<label for="color">Disabled:</label>
<input id="color" type="color" value="#b57edc" disabled />

With `range` type:

```html
<input type="range" max="100" value="33">
```

<input type="range" max="100" value="33" id="range">
<!-- For the demo purposes only -->
<small id="range-value"></small>

<script type="text/javascript">
  var slider = document.getElementById("range");
  var output = document.getElementById("range-value");
  output.innerHTML = slider.value;

  slider.oninput = function() {
    output.innerHTML = this.value;
  }
</script>
<!-- End -->

### Figure Captions (`<figcaption>`)

```markdown
<figure>
  -> Whatever content <-
  <figcaption>Caption of content above</figcaption>
</figure>
```

<figure>

  ![The Office](https://i.ibb.co/MPDJRsT/ImMAXM3.png)
  <figcaption>The Office where Stanley works, it has yellow floor and beige walls</figcaption>
</figure>

### Accordion (`<details>`)

```markdown
<details>
  <summary>Accordion title</summary>
  -> Contents here <-
</details>
```

<details>
  <summary>Reveal accordion</summary>

  Get it? I know, it's an awful pun.
  ![Piano Accordion](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/PianoAccordeon.jpg/916px-PianoAccordeon.jpg#transparent#no-hover)

</details>

### Side Comment (`<small>`)

```html
<small>Small, cute text that doesn't catch attention.</small>
```

<small>Small, cute text that doesn't catch attention.</small>

### Abbreviation (`<abbr>`)

```html
<abbr title="American Standard Code for Information Interchange">ASCII</abbr>
```

The <abbr title="American Standard Code for Information Interchange">ASCII</abbr> art are awesome!

### Aside (`<aside>`)

```html
<aside>
-> Contents here <-
</aside>
```

<aside>
Quill and a parchment
<img class="transparent no-hover" style="margin-bottom: 0; border-radius: 0;" alt="Quill and a parchment" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/%D7%A7%D7%9C%D7%A3%2C_%D7%A0%D7%95%D7%A6%D7%94_%D7%95%D7%93%D7%99%D7%95.jpg/326px-%D7%A7%D7%9C%D7%A3%2C_%D7%A0%D7%95%D7%A6%D7%94_%D7%95%D7%93%D7%99%D7%95.jpg" />
</aside>

A quill is a writing tool made from a moulted flight feather (preferably a primary wing-feather) of a large bird. Quills were used for writing with ink before the invention of the dip pen, the metal-nibbed pen, the fountain pen, and, eventually, the ballpoint pen.

As with the earlier reed pen (and later dip pen), a quill has no internal ink reservoir and therefore needs to periodically be dipped into an inkwell during writing. The hand-cut goose quill is rarely used as a calligraphy tool anymore because many papers are now derived from wood pulp and would quickly wear a quill down. However it is still the tool of choice for a few scribes who have noted that quills provide an unmatched sharp stroke as well as greater flexibility than a steel pen.

### Keyboard Input (`<kbd>`)

```html
<kbd>⌘ Command</kbd>.
```

To switch the keyboard layout, press <kbd>⌘ Super</kbd> + <kbd>Space</kbd>.

### Mark Text (`<mark>`)

```html
<mark>Marked text</mark>
```

You know what? I'm gonna say some <mark>very important</mark> stuff, so <mark>important</mark> that even **bold** is not enough.

### Deleted and Inserted Text (`<del>` and `<ins>`)

```html
<del>Something deleted</del> <ins>Something added</ins>
```

<del>Text deleted</del> <ins>Text added</ins>

### Progress Indicator (`<progress>`)

```html
<progress></progress>
<progress value="33" max="100"></progress>
```

<progress></progress>
<progress value="33" max="100"></progress>

### Sample Output (`<samp>`)

```html
<samp>Sample Output</samp>
```

<samp>Sample Output</samp>

### Inline Quotation (`<q>`)

```html
<q>Someone said something</q>
```

Blah blah <q>Inline Quote</q> hmm.

### Unarticulated Annotation (`<u>`)

```html
<u>Gmarrar mitsakes</u>
```

<u>Yeet</u> the <u>sus</u> drip while <u>vibing</u> with the <u>TikTok</u> <u>fam</u> on a cap-free boomerang.

### External Links

```html
<a class="external" href="https://example.org">External link</a>
```

<a class="external" href="https://example.org">Link to site</a>

### Buttons Dialog

```html.j2
<div class="dialog-buttons">
  <a class="inline-button" href="#top">Go to Top</a>
  <a class="inline-button colored external" href="https://example.org">Example</a>
</div>
```

<div class="dialog-buttons">
  <a class="inline-button" href="#top">Go to Top</a>
  <a class="inline-button colored external" href="https://example.org">Example</a>
</div>

[^1]: Footnote
[^2]: [Footnote (link)](https://example.org)

<!-- For the demo purposes only -->
<div id="color-picker-container">
<label for="color-picker">Primary color:</label>
<input id="color-picker" type="color" />
</div>

<style>
  #color-picker-container {
    -webkit-backdrop-filter: var(--blur);
    position: fixed;
    bottom: 1rem;
    left: 0;
    transform: translateX(calc(-100% + 1rem));
    z-index: 1;
    backdrop-filter: var(--blur);
    transition: var(--transition);
    box-shadow: var(--edge-highlight);
    border-start-end-radius: var(--rounded-corner);
    border-end-end-radius: var(--rounded-corner);
    background-color: var(--nav-bg);
    padding: 0.5rem;
  }

  #color-picker-container:hover {
    transform: none;
  }

  #color-picker-container label {
    margin-inline-end: 0.25rem;
    color: var(--fg-muted-4);
    font-weight: bold;
  }

  :root[dir*="rtl"] #color-picker-container {
    right: 0;
    left: unset;
    transform: translateX(calc(100% - 1rem));
  }

  :root[dir*="rtl"] #color-picker-container:hover {
    transform: none;
  }
</style>

<script type="text/javascript">
  let colorPicker;
  const defaultColor = window.getComputedStyle(document.documentElement).getPropertyValue("--primary-color");
  console.log(defaultColor);

  window.addEventListener("load", startup, false);

  function hexToRGB(hex, alpha) {
    var r = parseInt(hex.slice(1, 3), 16),
      g = parseInt(hex.slice(3, 5), 16),
      b = parseInt(hex.slice(5, 7), 16);

    if (alpha) {
      return "rgba(" + r + ", " + g + ", " + b + ", " + alpha + ")";
    } else {
      return "rgb(" + r + ", " + g + ", " + b + ")";
    }
  }

  function startup() {
    colorPicker = document.querySelector("#color-picker");
    colorPicker.value = defaultColor;
    colorPicker.addEventListener("input", update, false);
    colorPicker.select();
  }

  function update(event) {
    document.documentElement.style.setProperty('--primary-color', event.target.value);
    document.documentElement.style.setProperty('--primary-color-alpha', hexToRGB(event.target.value, 0.2));
  }
</script>
<!-- End -->
