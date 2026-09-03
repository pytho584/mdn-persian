---
title: "Node: firstChild property"
short-title: firstChild
slug: Web/API/Node/firstChild
page-type: web-api-instance-property
browser-compat: api.Node.firstChild
---

{{APIRef("DOM")}}

خاصیت فقط-خواندنی **`firstChild`** از رابط {{domxref("Node")}}
نخستین فرزند گره را در درخت برمی‌گرداند،
یا اگر گره فرزندی نداشته باشد `null` را.

اگر گره یک {{domxref("Document")}} باشد،
این خاصیت اولین گره در لیست فرزندان مستقیم آن را برمی‌گرداند.

> [!NOTE]
> این خاصیت هر نوع گره‌ای که نخستین فرزند این گره باشد را برمی‌گرداند.
> ممکن است یک گره {{domxref("Text")}} یا {{domxref("Comment")}} باشد.
> اگر می‌خواهید اولین {{domxref("Element")}} که فرزند یک عنصر دیگر است را به دست آورید،
> از {{domxref("Element.firstElementChild")}} استفاده کنید.

## مقدار

یک {{domxref("Node")}}، یا اگر هیچ‌کدام نباشد `null`.

## مثال

این مثال کاربرد `firstChild` و چگونگی تداخل گره‌های فضای خالی با این خاصیت را نشان می‌دهد.

```html
<p id="para-01">
  <span>First span</span>
</p>
```

```js
const p01 = document.getElementById("para-01");
console.log(p01.firstChild.nodeName);
```

در کد بالا، کنسول '#text' را نمایش می‌دهد
زیرا یک گره متنی برای حفظ فضای خالی بین انتهای تگ‌های
`<p>` و `<span>` درج شده است. **هر**
[فضای خالی](/en-US/docs/Web/CSS/Guides/Text/Whitespace#working_with_whitespace_in_the_dom)
یک گره `#text` ایجاد می‌کند، از یک فاصله تا چند فاصله، بازگشت به خط، تب و غیره.

یک گره `#text` دیگر بین تگ‌های بسته `</span>`
و `</p>` درج می‌شود.

اگر این فاصله‌های خالی از کد منبع حذف شوند، گره‌های #text درج نمی‌شوند و
عنصر span به نخستین فرزند پاراگراف تبدیل می‌شود.

```html
<p id="para-01"><span>First span</span></p>
```

```js
const p01 = document.getElementById("para-01");
console.log(p01.firstChild.nodeName);
```

اکنون کنسول 'SPAN' را نمایش می‌دهد.

برای جلوگیری از مشکل بازگشت `#text` یا
`#comment` توسط `node.firstChild`، می‌توان از {{domxref("Element.firstElementChild")}} استفاده کرد
تا فقط اولین گره عنصر را برگرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.firstElementChild")}}
- {{domxref("Node.lastChild")}}