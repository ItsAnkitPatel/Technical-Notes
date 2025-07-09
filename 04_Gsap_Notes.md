### GSAP(GreenSock Animation Platform) - A JavaScript library for creating high-performance animations.

GSAP is a powerful JavaScript library that allows developers to create high-performance animations for web applications. It is widely used for its ease of use, flexibility, and performance.

It wasn't free until 2020, but now it is free for most use cases, with a commercial license available for advanced features and support.

**What is emotional design**

Emotional design is the practice of creating products that evoke specific emotions in users. It focuses on the user's feelings and experiences, aiming to create a connection between the user and the product. Emotional design can enhance user engagement, satisfaction, and loyalty. It involves understanding the user's needs, preferences, and emotions to create a product that resonates with them.

American psychologist **Donald Norman**, in his book "Emotional Design: Why We Love (or Hate) Everyday Things," emphasizes the importance of emotional design in creating products that people love. He argues that products should not only be functional but also evoke positive emotions in users.

He discussed three levels of design:

1. **Visceral Design(Wow, that looks amazing)**: This level focuses on the immediate emotional response to a product's appearance and feel. It involves the initial attraction to a product based on its aesthetics, such as color, shape, and texture. Visceral design aims to create a strong first impression and evoke positive emotions through visual appeal.
2. **Behavioral Design(This feels intuitive)**: This level focuses on the usability and functionality of a product. It involves creating products that are easy to use, efficient, and effective in meeting the user's needs. Behavioral design aims to create a seamless user experience that enhances satisfaction and reduces frustration.
3. **Reflective Design**: This level focuses on the user's long-term emotional connection to a product. It involves creating products that resonate with the user's values, beliefs, and identity. Reflective design aims to create a lasting emotional bond between the user and the product, fostering loyalty and advocacy.

<hr />

### GSAP Starter

Either use cdn links or install GSAP via npm:

cdn:

```html
<script src="https://cdn.jsdelivr.net/npm/gsap@3.13.0/dist/gsap.min.js"></script>
```

or install via npm:

```bash
npm install gsap
```

[Official GSAP installation guide 🔗](https://gsap.com/docs/v3/Installation/)

<br />
<br />

**Gsap general structure**

```javascript
gsap.to(target, vars);
```

- `fn`: The function to be executed, such as `gsap.to()`, `gsap.from()`, or `gsap.fromTo()`.
- `target`: The target element(DOM element) to animate. This can be a single element, an array of elements, or a CSS selector string.
- `vars`: An object containing the animation properties and values. This object can include properties such as `duration`, `ease`, `x`, `y`, `opacity`, and more. It can also include callbacks like `onComplete`, `onStart`, and `onUpdate` to execute functions at specific points during the animation.

Example:

```javascript
gsap.to(".card", {
  opacity: 1,
  scale: 1,
  duration: 2, // 2 seconds
  onComplete: () => {
    gsap.to(".card", {
      y: -20, // Move the element 20px up; negative values move up, positive move down
      repeat: -1, // Repeat infinitely; -1 is the special value for endless looping
      yoyo: true, // Reverse the animation direction on every alternate repeat; creates a "back and forth" effect
      duration: 0.5, // Each up/down cycle lasts 0.5 seconds; short durations can look abrupt if too fast
    });
  },
});
```
