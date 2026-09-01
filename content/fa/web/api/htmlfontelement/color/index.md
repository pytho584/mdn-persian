---
title: "HTMLFontElement: color property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLFontElement/color"
---

---
title: "HTMLFontElement: color property"
short-title: color
slug: Web/API/HTMLFontElement/color
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLFontElement.color
---

{{deprecated_header}}{{APIRef("HTML DOM")}}

ویژگی منسوخ‌شدهٔ
**`HTMLFontElement.color`**
یک رشته است که مشخصهٔ HTML
[`color`](/en-US/docs/Web/HTML/Reference/Elements/font#color)
را بازتاب می‌دهد؛ این رشته یا شامل یک نام رنگ است یا رنگی که در قالب هگزادسیمال
#RRGGBB
مشخص شده است.

قالب این رشته باید مطابق یکی از Microsyntax های زیر در HTML باشد (به {{cssxref("&lt;color&gt;")}} مراجعه کنید):

| Microsyntax              | توضیحات                         | مثال‌ها                  |
| ------------------------ | -------------------------------- | ------------------------- |
| رشتهٔ نام رنگ معتبر      | _نام رنگ (بدون حساسیت به بزرگی/کوچکی حروف)_ | `Green`، `green`، `GREEN` |
| رشتهٔ هگزادسیمال معتبر   | _#RRGGBB_                        | `#008000`                 |
| RGB با مقادیر اعشاری     | _rgb(x x x) (x در بازهٔ ۰ تا ۲۵۵-)_  | `rgb(0 128 0)`            |

## مقدار

یک رشته.

وقتی مقدار `null` به آن اختصاص داده شود، آن مقدار `null` به رشتهٔ خالی (`""`) تبدیل می‌شود؛ بنابراین `elt.color = null` معادل `elt.color = ""` است.

## مثال‌ها

```js
// فرض بر این است که عنصر <font id="f"> در HTML وجود دارد

const f = document.getElementById("f");
f.color = "green";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("HTMLFontElement")}} که این ویژگی به آن تعلق دارد.