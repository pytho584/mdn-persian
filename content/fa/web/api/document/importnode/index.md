---
title: "Document: importNode() method"
short-title: importNode()
slug: Web/API/Document/importNode
page-type: web-api-instance-method
browser-compat: api.Document.importNode
---

{{APIRef("DOM")}}

متود **`importNode()`** از رابط {{domxref("Document")}} یک کپی از یک {{domxref("Node")}} یا {{domxref("DocumentFragment")}} از یک سند دیگر ایجاد می‌کند تا بعداً در سند جاری درج شود.

گره وارد شده هنوز در درخت سند قرار ندارد. برای قرار دادن آن، باید یک متود درج مانند {{domxref("Node.appendChild", "appendChild()")}} یا {{domxref("Node.insertBefore", "insertBefore()")}} را با گره‌ای که _در حال حاضر_ در درخت سند است فراخوانی کنید.

برخلاف {{domxref("document.adoptNode()")}}، گره اصلی از سند اصلی خود حذف نمی‌شود. گره وارد شده یک کلون از گره اصلی است.

متود {{domxref("Node.cloneNode()")}} نیز یک کپی از یک گره ایجاد می‌کند. تفاوت در این است که `importNode()` گره را در زمینه سند فراخواننده کلون می‌کند، در حالی که `cloneNode()` از سند گره‌ای که در حال کلون شدن است استفاده می‌کند. زمینه سند، {{domxref("CustomElementRegistry")}} را برای ساخت هر المان سفارشی تعیین می‌کند. به همین دلیل، برای کلون کردن گره‌هایی که در سند دیگری استفاده می‌شوند، از `importNode()` در سند مقصد استفاده کنید. {{domxref("HTMLTemplateElement.content")}} متعلق به یک سند مجزاست، بنابراین باید با استفاده از `document.importNode()` نیز کلون شود تا المان‌های سفارشی فرزند با استفاده از تعاریف موجود در سند جاری ساخته شوند. برای جزئیات بیشتر، مثال‌های صفحه {{domxref("Node.cloneNode()")}} را ببینید.

## Syntax

```js-nolint
importNode(externalNode)
importNode(externalNode, deep)
```

### Parameters

- `externalNode`
  - : {{domxref("Node")}} یا {{domxref("DocumentFragment")}} خارجی که باید به سند جاری وارد شود.
- `deep` {{optional_inline}}
  - : یک پرچم بولی که مقدار پیش‌فرض آن `false` است و مشخص می‌کند که آیا کل زیردرخت DOM `externalNode` در واردات گنجانده شود یا خیر.
    - اگر `deep` برابر `true` باشد، `externalNode` و تمام فرزندان آن کپی می‌شوند.
    - اگر `deep` برابر `false` باشد، فقط `externalNode` وارد می‌شود – گره جدید هیچ فرزندی ندارد.

### Return value

کپی `importedNode` در محدوده سند واردکننده.

> **نکته:** {{domxref("Node.parentNode")}} `importedNode` برابر `null` است، زیرا هنوز در درخت سند درج نشده است!

## Examples

### استفاده از importNode()

```js
const iframe = document.querySelector("iframe");
const oldNode = iframe.contentWindow.document.getElementById("myNode");
const newNode = document.importNode(oldNode, true);
document.getElementById("container").appendChild(newNode);
```

## Notes

گره‌های حاصل از اسناد خارجی، پیش از آنکه بتوانند در سند جاری درج شوند، باید یا:

- با استفاده از `document.importNode()` کلون شوند؛ یا
- با استفاده از {{domXref("document.adoptNode()")}} پذیرفته شوند.

> **نکته:** اگرچه فایرفاکس در حال حاضر این قانون را اعمال نمی‌کند، برای سازگاری بهتر در آینده توصیه می‌کنیم این قانون را رعایت کنید.

برای اطلاعات بیشتر درباره مسائل {{domXref("Node.ownerDocument")}}، به W3C DOM FAQ مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("document.adoptNode()")}} که رفتاری بسیار مشابه با این متود دارد
- {{domxref("Node.appendChild()")}}
- {{domxref("Node.insertBefore()")}}