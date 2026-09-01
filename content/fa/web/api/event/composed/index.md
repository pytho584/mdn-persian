---
title: "Event: composed property"
short-title: composed
slug: Web/API/Event/composed
page-type: web-api-instance-property
browser-compat: api.Event.composed
---

{{APIRef("Shadow DOM")}}{{AvailableInWorkers}}

خاصیت فقط خواندنی **`composed`** از رابط {{domxref("Event")}} یک مقدار بولی بازمی‌گرداند که نشان می‌دهد آیا رویداد از مرز Shadow DOM به DOM استاندارد منتشر می‌شود یا خیر.

همه رویدادهای رابط کاربری (UI) که توسط عامل کاربر (UA) ارسال می‌شوند، composed هستند (مانند کلیک، لمس، موس‌رو، کپی، چسباندن و غیره). بیشتر انواع دیگر رویدادها composed نیستند و بنابراین `false` برمی‌گردانند. به عنوان مثال، این شامل رویدادهای مصنوعی (synthetic) می‌شود که بدون تنظیم گزینه `composed` آنها به `true` ایجاد شده‌اند.

انتشار (Propagation) فقط زمانی رخ می‌دهد که خاصیت {{domxref("Event.bubbles", "bubbles")}} نیز `true` باشد. با این حال، رویدادهای composed در فاز capturing نیز در میزبان (host) به گونه‌ای مدیریت می‌شوند که گویی در فاز `AT_TARGET` هستند. شما می‌توانید مسیری را که رویداد از طریق ریشه سایه (shadow root) به ریشه DOM دنبال می‌کند، با فراخوانی {{domxref("Event.composedPath", "composedPath()")}} تعیین کنید.

## مقدار

یک مقدار بولی که اگر رویداد پس از رسیدن به ریشه سایه (shadow root) از Shadow DOM به DOM استاندارد عبور کند، `true` است. (یعنی اولین گره در Shadow DOM که رویداد انتشار را از آنجا آغاز کرد.) اگر این مقدار `false` باشد، ریشه سایه آخرین گره‌ای خواهد بود که رویداد به آن ارائه می‌شود.

## مثال‌ها

در این [مثال](https://mdn.github.io/web-components-examples/composed-composed-path/)، دو عنصر سفارشی ساده به نام‌های `<open-shadow>` و `<closed-shadow>` تعریف می‌کنیم. هر دو محتوای ویژگی text خود را گرفته و آن را به عنوان محتوای متنی یک عنصر `<p>` در Shadow DOM خود قرار می‌دهند. تنها تفاوت بین این دو این است که ریشه‌های سایه (shadow roots) آن‌ها به ترتیب با حالت‌های `open` و `closed` متصل شده‌اند.

دو تعریف به این صورت هستند:

```js
customElements.define(
  "open-shadow",
  class extends HTMLElement {
    constructor() {
      super();

      const pElem = document.createElement("p");
      pElem.textContent = this.getAttribute("text");

      const shadowRoot = this.attachShadow({
        mode: "open",
      });

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

      const shadowRoot = this.attachShadow({
        mode: "closed",
      });

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

سپس یک شنونده رویداد کلیک روی عنصر `<html>` قرار می‌دهیم:

```js
document.querySelector("html").addEventListener("click", (e) => {
  console.log(e.composed);
  console.log(e.composedPath());
});
```

وقتی روی عنصر `<open-shadow>` و سپس روی عنصر `<closed-shadow>` کلیک می‌کنید، دو چیز را متوجه خواهید شد.

1. خاصیت `composed` مقدار `true` را برمی‌گرداند، زیرا رویداد `click` همیشه قادر به انتشار در سراسر مرزهای سایه است.
2. تفاوت در مقدار `composedPath` برای دو عنصر.

مسیر composed عنصر `<open-shadow>` به این صورت است:

```plain
Array [ p, ShadowRoot, open-shadow, body, html, HTMLDocument https://mdn.github.io/web-components-examples/composed-composed-path/, Window ]
```

در حالی که مسیر composed عنصر `<closed-shadow>` به صورت زیر است:

```plain
Array [ closed-shadow, body, html, HTMLDocument https://mdn.github.io/web-components-examples/composed-composed-path/, Window ]
```

در حالت دوم، شنونده‌های رویداد فقط تا خود عنصر `<closed-shadow>` انتشار می‌یابند، اما به گره‌های داخل مرز سایه نمی‌رسند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}