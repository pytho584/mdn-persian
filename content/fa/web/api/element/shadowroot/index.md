---
title: "Element: shadowRoot property"
---

{{APIRef("Shadow DOM")}}

خاصیت فقط خواندنی `Element.shadowRoot` نشان‌دهنده shadow root (ریشه سایه) میزبانی شده توسط عنصر است.

برای افزودن یک shadow root به یک عنصر موجود از {{DOMxRef("Element.attachShadow()")}} استفاده کنید.

## مقدار

یک نمونه از شیء {{DOMxRef("ShadowRoot")}}، یا `null` اگر shadow root مرتبط با {{DOMxRef("ShadowRoot.mode", "mode")}} آن برابر با `closed` متصل شده باشد. (برای جزئیات بیشتر به {{DOMxRef("Element.attachShadow()")}} مراجعه کنید).

برخی عناصر داخلی، مانند {{HTMLElement("input")}} و {{HTMLElement("img")}}، دارای shadow roots عامل کاربر (user-agent) هستند که برای اسکریپت بسته هستند. بنابراین، خاصیت `shadowRoot` آن‌ها همیشه `null` است.

## مثال‌ها

قطعه کدهای زیر از مثال [life-cycle-callbacks](https://github.com/mdn/web-components-examples/tree/main/life-cycle-callbacks) گرفته شده‌اند ([همچنین به صورت زنده ببینید](https://mdn.github.io/web-components-examples/life-cycle-callbacks/))، که یک عنصر ایجاد می‌کند یک مربع با اندازه و رنگی که در ویژگی‌های عنصر مشخص شده است نمایش می‌دهد.

درون تعریف کلاس عنصر `<custom-square>`، ما چندین فراخوان چرخه عمر (life cycle callbacks) قرار می‌دهیم که یک تابع خارجی به نام `updateStyle()` را فراخوانی می‌کنند، که در واقع اندازه و رنگ را به عنصر اعمال می‌کند. مشاهده می‌کنید که ما `this` (خود عنصر سفارشی) را به عنوان پارامتر به آن ارسال می‌کنیم.

```js
class Square extends HTMLElement {
  connectedCallback() {
    console.log("Custom square element added to page.");
    updateStyle(this);
  }

  attributeChangedCallback(name, oldValue, newValue) {
    console.log("Custom square element attributes changed.");
    updateStyle(this);
  }
}
```

در خود تابع `updateStyle()`، ما با استفاده از `Element.shadowRoot` یک ارجاع به shadow DOM دریافت می‌کنیم. از اینجا از تکنیک‌های استاندارد پیمایش DOM برای یافتن عنصر {{htmlelement("style")}} درون shadow DOM و سپس به‌روزرسانی CSS درون آن استفاده می‌کنیم:

```js
function updateStyle(elem) {
  const shadow = elem.shadowRoot;
  const childNodes = Array.from(shadow.childNodes);

  childNodes.forEach((childNode) => {
    if (childNode.nodeName === "STYLE") {
      childNode.textContent = `
        div {
          width: ${elem.getAttribute("l")}px;
          height: ${elem.getAttribute("l")}px;
          background-color: ${elem.getAttribute("c")};
        }
      `;
    }
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}