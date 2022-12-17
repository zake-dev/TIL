# Improve Accessibility : `sr-only class` and `<del>`

How do you handle texts in html document usually? We can put titles as heading tags like `<h1>`, `<h2>`, paragraphs with `<p>` tag, some specific text decorations with `<span>`.

<img src="../images/improve-accessibility-example-component.png" />

How about above image? How can you style prices part? The simplest way is just putting them in a `<p>` tag with separate `<span>` tags. However, this approach will break accessibility of your website. If you style them without specific tags or accessibility improvements, **screen readers will not be able to describe it properly**.

## Describe Your Deleted Texts

To improve your website in terms of accessibility, you can use `<del>` tag for `line-through` text. Compared to normal `<span>` tag with css decoration, now screen readers will describe the content it is **deleted**.

Another improvement is using a `<span>` tag with `sr-only class`. This class is for the contents that should be provided to _screen readers only_ without visibility. For the example above, you can provide **"The previous price was $169.99 ..."** text with `sr-only class` so screen readers can describe the content more precisely without visibility interruption.

However, `sr-only class` is not a native implemented CSS class. This is kind of convention for frontend developers to make a website has more accessibility. This class uses absolute position with no visible area. Here is the example code lines:

```css
.sr-only {
  position: absolute; /* Give position: relative to parent class to place child properly */
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  border: 0;
  clip: rect(0, 0, 0, 0);
}
```
