---
title: "Event: composedPath() method"
short-title: composedPath()
slug: Web/API/Event/composedPath
page-type: web-api-instance-method
browser-compat: api.Event.composedPath
---

{{APIRef("Shadow DOM")}}{{AvailableInWorkers}}

متد **`composedPath()`** در رابط {{domxref("Event")}} مسیر رویداد را برمی‌گرداند؛ آرایه‌ای از اشیایی که شنونده‌های رویداد روی آن‌ها فراخوانی خواهند شد. اگر ریشه سایه (shadow root) با {{domxref("ShadowRoot.mode")}} برابر با `closed` ساخته شده باشد، این مسیر شامل گره‌های داخل درخت سایه نمی‌شود.

## نحو (Syntax)

```js-nolint
composedPath()
```

### پارامترها

هیچ.

### مقدار بازگشتی

آرایه‌ای از اشیاء {{domxref("EventTarget")}} که اشیایی را نشان می‌دهد که شنونده رویداد روی آن‌ها فراخوانی خواهد شد.

## مثال‌ها

در مثال زیر، که می‌توانید آن را در [https://mdn.github.io/web-components-examples/composed-composed-path/](https://mdn.github.io/web-components-examples/composed-composed-path/) امتحان کنید، دو عنصر سفارشی ساده تعریف کرده‌ایم: `<open-shadow>` و `<closed-shadow>`. هر دوی این عناصر محتوای ویژگی text خود را می‌گیرند و آن را به‌عنوان محتوای متنی یک عنصر `<p>` در DOM سایه خود وارد می‌کنند. تنها تفاوت بین این دو این است که ریشه‌های سایه آن‌ها به ترتیب با حالت `open` و `closed` متصل شده‌اند.

```js
customElements.define(
  "open-shadow",
  class extends HTMLElement {
    constructor() {
      super();

      const pElem = document.createElement("p");
      pElem.textContent = this.getAttribute("text");

      const shadowRoot = this.attachShadow({ mode: "open" });
      shadowRoot.appendChild(pElem);
    }
  },
);

customElements.define(
  "closed-shadow",
  class extends HTMLElement {
    constructor() {
      super();

      const pElem = document.createElement("p");
      pElem.textContent = this.getAttribute("text");

      const shadowRoot = this.attachShadow({ mode: "closed" });
      shadowRoot.appendChild(pElem);
    }
  },
);
```

سپس یکی از هر عنصر را در صفحه خود قرار می‌دهیم:

```html
<open-shadow text="I have an open shadow root"></open-shadow>
<closed-shadow text="I have a closed shadow root"></closed-shadow>
```

و یک شنونده رویداد کلیک روی عنصر `<html>` اضافه می‌کنیم:

```js
document.querySelector("html").addEventListener("click", (e) => {
  console.log(e.composed);
  console.log(e.composedPath());
});
```

وقتی روی عنصر `<open-shadow>` و سپس روی عنصر `<closed-shadow>` کلیک کنید، دو نکته را متوجه خواهید شد. اول اینکه ویژگی `composed` مقدار `true` را برمی‌گرداند، زیرا رویداد `click` همیشه می‌تواند از مرزهای سایه عبور کند. دوم اینکه تفاوتی در مقدار `composedPath` برای این دو عنصر مشاهده می‌کنید. مسیر ترکیبی عنصر `<open-shadow>` به این صورت است:

```plain
Array [ p, ShadowRoot, open-shadow, body, html, HTMLDocument https://mdn.github.io/web-components-examples/composed-composed-path/, Window ]
```

در حالی که مسیر ترکیبی عنصر `<closed-shadow>` به این صورت است:

```plain
Array [ closed-shadow, body, html, HTMLDocument https://mdn.github.io/web-components-examples/composed-composed-path/, Window ]
```

در حالت دوم، شنونده‌های رویداد فقط تا خود عنصر `<closed-shadow>` propagate می‌شوند و به گره‌های داخل مرز سایه نمی‌رسند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}