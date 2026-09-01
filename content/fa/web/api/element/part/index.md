---
title: "Element: part property"
---

---
title: "Element: part property"
short-title: part
slug: Web/API/Element/part
page-type: web-api-instance-property
browser-compat: api.Element.part
---

{{ ApiRef("DOM") }}

ویژگی فقط‌خواندنی **`part`** در رابط {{domxref("Element")}} شامل یک شیء {{domxref("DOMTokenList")}} است که شناسه‌(های) part عنصر را نشان می‌دهد. این ویژگی، ویژگی محتوایی [`part`](/en-US/docs/Web/HTML/Reference/Global_attributes/part) عنصر را بازتاب می‌دهد. از این شناسه‌ها می‌توان برای استایل‌دهی به بخش‌های یک shadow DOM از طریق شبه‌عنصر {{cssxref("::part")}} استفاده کرد.

## مقدار

یک شیء {{domxref("DOMTokenList")}}. اگر ویژگی `part` تنظیم نشده باشد یا خالی باشد، یک `DOMTokenList` خالی برمی‌گرداند؛ یعنی یک `DOMTokenList` که ویژگی `length` آن برابر با `0` است.

اگرچه ویژگی `part` به خودی خود فقط‌خواندنی است، به این معنا که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `part` مقداردهی کنید، که معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از متدهای {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## نمونه‌ها

نمونه زیر برگرفته از مثال [shadow-part](https://mdn.github.io/web-components-examples/shadow-part/) ما است. در اینجا از ویژگی `part` برای یافتن بخش‌های shadow استفاده می‌شود و سپس از ویژگی `part` برای تغییر شناسه‌های part هر زبانه استفاده می‌شود تا هنگام کلیک روی زبانه‌ها، استایل صحیح به زبانه فعال اعمال شود.

```js
const tabs = [];
const children = this.shadowRoot.children;

for (const elem of children) {
  if (elem.getAttribute("part")) {
    tabs.push(elem);
  }
}

tabs.forEach((tab) => {
  tab.addEventListener("click", (e) => {
    tabs.forEach((tab) => {
      tab.part = "tab";
    });
    e.target.part = "tab active";
  });

  console.log(tab.part);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("::part")}}
- [part](/en-US/docs/Web/HTML/Reference/Global_attributes/part)