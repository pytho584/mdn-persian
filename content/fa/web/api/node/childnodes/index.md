---
title: "Node: childNodes property"
short-title: childNodes
slug: Web/API/Node/childNodes
page-type: web-api-instance-property
browser-compat: api.Node.childNodes
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`childNodes`** در رابط {{domxref("Node")}} یک {{domxref("NodeList")}} زنده از {{domxref("Node","گره‌های")}} فرزند عنصر داده‌شده را برمی‌گرداند، به‌طوری‌که اولین گره فرزند ایندکس `0` را می‌گیرد. گره‌های فرزند شامل عناصر، متن و کامنت‌ها هستند.

> [!NOTE]
> زنده بودن {{domxref("NodeList")}} به این معناست که محتوای آن با هر بار افزوده‌شدن یا حذف‌شدن فرزندان جدید تغییر می‌کند.
>
> مرورگرها برای نمایش فاصله‌های خالی (whitespace) در نشانه‌گذاری منبع، گره‌های متنی را در سند وارد می‌کنند. بنابراین، گره‌ای که مثلاً با `Node.childNodes[0]` به دست می‌آید ممکن است به یک گره متنی حاوی فاصله اشاره کند، نه عنصر واقعی‌ای که نویسنده قصد دریافت آن را داشته است.
>
> برای اطلاعات بیشتر به [کار با فاصله‌های خالی در DOM](/en-US/docs/Web/CSS/Guides/Text/Whitespace#working_with_whitespace_in_the_dom) مراجعه کنید.

آیتم‌های موجود در مجموعه گره‌ها، آبجکت هستند نه رشته. برای دریافت داده از گره‌ها، از ویژگی‌های آن‌ها استفاده کنید. مثلاً برای دریافت نام اولین گره فرزند، می‌توانید از `elementNodeReference.childNodes[0].nodeName` استفاده کنید.

خود شیء {{domxref("document")}} دو فرزند دارد: اعلان Doctype و عنصر ریشه که معمولاً با نام `documentElement` شناخته می‌شود. در اسناد HTML، دومی عنصر {{HTMLElement("html")}} است.

مهم است به خاطر داشته باشید که `childNodes` شامل _همه_ گره‌های فرزند می‌شود، از جمله گره‌های غیرعنصری مانند متن و کامنت. برای دریافت مجموعه‌ای که فقط عناصر را شامل می‌شود، از {{domxref("Element.children")}} استفاده کنید.

## مقدار

یک {{domxref("NodeList")}} زنده شامل فرزندان آن گره.

> [!NOTE]
> چند بار فراخوانی `childNodes` همان {{domxref("NodeList")}} را برمی‌گرداند.

## مثال‌ها

### استفاده ساده

```js
// توجه کنید که para یک ارجاع به یک عنصر <p> است

// ابتدا بررسی کنید که عنصر گره فرزند دارد
if (para.hasChildNodes()) {
  let children = para.childNodes;

  for (const node of children) {
    // با هر فرزند به عنوان children[i] کاری انجام دهید
    // توجه: لیست زنده است! افزودن یا حذف فرزندان، `length` لیست را تغییر می‌دهد
  }
}
```

### حذف همه فرزندان از یک گره

```js
// این یکی از راه‌های حذف همه فرزندان از یک گره است
// box یک ارجاع به یک عنصر است
while (box.firstChild) {
  // لیست زنده است، بنابراین هر بار فراخوانی، ایندکس‌ها دوباره محاسبه می‌شوند
  box.removeChild(box.firstChild);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.firstChild")}}
- {{domxref("Node.lastChild")}}
- {{domxref("Node.nextSibling")}}
- {{domxref("Node.previousSibling")}}
- {{domxref("Element.children")}}