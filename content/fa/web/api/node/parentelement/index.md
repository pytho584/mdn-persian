---
title: "Node: parentElement property"
short-title: parentElement
slug: Web/API/Node/parentElement
page-type: web-api-instance-property
browser-compat: api.Node.parentElement
---

{{APIRef("DOM")}}

خاصیت فقط خواندنی **`parentElement`** در رابط {{domxref("Node")}}، عنصر والد ({{DOMxRef("Element")}}) گره DOM را برمی‌گرداند، یا اگر گره والد نداشته باشد یا والد آن یک {{DOMxRef("Element")}} نباشد، `null` را برمی‌گرداند. در مقابل، {{domxref("Node.parentNode")}} هر نوع والدی را بدون توجه به نوع آن برمی‌گرداند.

## مقدار

یک {{domxref("Element")}} که عنصر والد گره جاری است، یا اگر وجود نداشته باشد `null`.

## مثال

### استفاده از parentElement

این مثال، والد `node` را طوری تنظیم می‌کند که رنگ متن قرمز داشته باشد.

```js
if (node.parentElement) {
  node.parentElement.style.color = "red";
}
```

### null بودن parentElement

`parentElement` می‌تواند `null` باشد اگر گره والد نداشته باشد (مثلاً چون به درخت متصل نیست) یا والد آن یک `Element` نباشد. از سوی دیگر، {{domxref("Node.parentNode")}} همیشه گره والد را برمی‌گرداند که ممکن است یک {{domxref("Document")}} یا انواع دیگر گره باشد.

```html
<!doctype html>
<html lang="en-US">
  <body>
    <script>
      const html = document.querySelector("html");
      console.log(html.parentElement); // null
      console.log(html.parentNode); // document
    </script>
  </body>
</html>
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.parentNode")}}