---
title: "KeyframeEffect: pseudoElement property"
short-title: pseudoElement
slug: Web/API/KeyframeEffect/pseudoElement
page-type: web-api-instance-property
browser-compat: api.KeyframeEffect.pseudoElement
---

{{ APIRef("Web Animations") }}

ویژگی **`pseudoElement`** از رابط {{domxref("KeyframeEffect")}} یک رشته است که شبه‌عنصری (pseudo-element) را که در حال انیمیشن است، نشان می‌دهد. برای انیمیشن‌هایی که شبه‌عنصری را هدف قرار نمی‌دهند، می‌تواند `null` باشد. این ویژگی هم به عنوان گیرنده (getter) و هم به عنوان تنظیم‌کننده (setter) عمل می‌کند، به جز برای انیمیشن‌ها و transitionهای تولیدشده توسط CSS.

> [!NOTE]
> اگر این ویژگی با استفاده از نحو قدیمی تک‌خط تیره (single-colon) از {{cssxref("::before", ":before")}}, {{cssxref("::after", ":after")}}, {{cssxref("::first-letter", ":first-letter")}} یا {{cssxref("::first-line", ":first-line")}} تنظیم شود، رشته به نسخه مدرن دو-خط تیره (double-colon) به ترتیب {{cssxref("::before")}}, {{cssxref("::after")}}, {{cssxref("::first-letter")}} و {{cssxref("::first-line")}} تبدیل می‌شود.

## مقدار

یک رشته یا `null`.

## استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : هنگامی که تلاش شود این ویژگی روی یک عنصر یا یک شبه‌عنصر نامعتبر (غیرموجود یا نادرست نوشته شده) تنظیم شود، این استثنا پرتاب می‌شود. در این صورت ویژگی بدون تغییر باقی می‌ماند.

## مثال‌ها

```html
<div id="text">Some text</div>
<pre id="log"></pre>
```

```css
#text::after {
  content: "👹";
  display: inline-block; /* Needed as the `transform` property does not apply to inline elements */
  font-size: 2rem;
}
#text::before {
  content: "🤠";
  display: inline-block;
  font-size: 2rem;
}
```

```js
const log = document.getElementById("log");
const text = document.getElementById("text");

// Create the keyframe and launch the animation
const animation = text.animate([{ transform: "rotate(360deg)" }], {
  duration: 3000,
  iterations: Infinity,
  pseudoElement: "::after",
});

// Get the value of KeyframeEffect.pseudoElement
function logPseudoElement() {
  const keyframeEffect = animation.effect;
  log.textContent = `Value of pseudoElement animated: ${keyframeEffect.pseudoElement}`;
  requestAnimationFrame(logPseudoElement);
}

// Every 6 seconds, switch the pseudo-element animated
function switchPseudoElement() {
  const keyframeEffect = animation.effect;
  keyframeEffect.pseudoElement =
    keyframeEffect.pseudoElement === "::after" ? "::before" : "::after";
  setTimeout(switchPseudoElement, 6000);
}

switchPseudoElement();
logPseudoElement();
```

{{EmbedLiveSample("Examples", "100", "90")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- رابط {{domxref("KeyframeEffect")}}
- سازنده {{domxref("KeyframeEffect.KeyframeEfect", "KeyframeEffect()")}}
- ویژگی {{domxref("KeyframeEffect.target", "target")}}