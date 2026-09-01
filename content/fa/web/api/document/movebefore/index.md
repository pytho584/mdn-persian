---
title: "Document: moveBefore() method"
short-title: moveBefore()
slug: Web/API/Document/moveBefore
page-type: web-api-instance-method
browser-compat: api.Document.moveBefore
---

{{APIRef("DOM")}}

متد **`moveBefore()`** از رابط {{domxref("Document")}} یک {{domxref("Node")}} معین را به‌عنوان فرزند مستقیم، درون گره DOM سند، قبل از یک گره مرجع معین جابه‌جا می‌کند.

## سینتکس

```js-nolint
moveBefore(movedNode, referenceNode)
```

### پارامترها

- `movedNode`
  - : یک {{domxref("Node")}} که نشان‌دهنده گره موردنظر برای جابه‌جایی است. توجه داشته باشید که این گره باید یک {{domxref("Element")}} یا {{domxref("CharacterData")}} باشد.
- `referenceNode`
  - : یک {{domxref("Node")}} که `movedNode` قبل از آن جابه‌جا می‌شود، یا `null`. اگر مقدار `null` باشد، `movedNode` در انتهای گره‌های فرزند سند درج می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر پرتاب می‌شود:
    - `movedNode` مشخص‌شده بخشی از این سند نیست.
    - `movedNode` مشخص‌شده یک {{domxref("Element")}} یا {{domxref("CharacterData")}} نیست.
    - در حال تلاش برای جابه‌جایی `movedNode` قبل از document type سند (که با یک شیء {{domxref("DocumentType")}} نمایش داده می‌شود) هستید.
- `NotFoundError` {{jsxref("TypeError")}}
  - : `referenceNode` مشخص‌شده فرزند گرهی نیست که روی آن `moveBefore()` را فراخوانی کرده‌اید؛ به عبارت دیگر، گرهی که می‌خواهید `movedNode` را در داخل آن جابه‌جا کنید.
- `TypeError` {{jsxref("TypeError")}}
  - : آرگومان دوم ارائه نشده است.

## توضیحات

متد `moveBefore()` یک گره معین را به مکان جدیدی در DOM منتقل می‌کند. این متد عملکردی مشابه متد {{domxref("Node.insertBefore()")}} ارائه می‌دهد، با این تفاوت که گره را حذف و سپس دوباره درج نمی‌کند. این بدان معناست که وضعیت گره (که اگر با `insertBefore()` و سازوکارهای مشابه جابه‌جا می‌شد بازنشانی می‌شد) پس از جابه‌جایی حفظ می‌شود. این وضعیت‌ها شامل موارد زیر است:

- وضعیت [انیمیشن](/en-US/docs/Web/CSS/Guides/Animations) و [ترانزیشن](/en-US/docs/Web/CSS/Guides/Transitions).
- وضعیت بارگذاری {{htmlelement("iframe")}}.
- وضعیت‌های تعاملی (برای مثال {{cssxref(":focus")}} و {{cssxref(":active")}}).
- وضعیت عنصر [تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API).
- وضعیت باز/بسته بودن [پاپ‌اورها](/en-US/docs/Web/API/Popover_API).
- وضعیت مودال عناصر {{htmlelement("dialog")}} (دیالوگ‌های مودال بسته نخواهند شد).

وضعیت پخش عناصر {{htmlelement("video")}} و {{htmlelement("audio")}} در فهرست بالا گنجانده نشده است، زیرا این عناصر هنگام حذف و درج مجدد، صرف‌نظر از سازوکار مورد استفاده، وضعیت خود را حفظ می‌کنند.

هنگام مشاهده تغییرات DOM با استفاده از یک {{domxref("MutationObserver")}}، گره‌هایی که با `moveBefore()` جابه‌جا شده‌اند به‌صورت یک [گره حذف‌شده](/en-US/docs/Web/API/MutationRecord/removedNodes) و یک [گره افزوده‌شده](/en-US/docs/Web/API/MutationRecord/addedNodes) ثبت خواهند شد.

متد `moveBefore()` زمانی که روی گره `Document` فراخوانی شود کاربرد چندانی ندارد. برخی کاربردهای غیرعنصری برای آن وجود دارد؛ برای مثال می‌توانید از `moveBefore()` برای جابه‌جایی گره‌های دیدگاه (comment) در اطراف ریشه `Document` استفاده کنید. با این حال، بسیار محتمل‌تر است که استفاده از آن روی یک `DocumentFragment` یا `Element` خاص برای شما مفید باشد — به {{domxref("DocumentFragment.moveBefore()")}} و {{domxref("Element.moveBefore()")}} مراجعه کنید.

### محدودیت‌های `moveBefore()`

هنگام استفاده از `moveBefore()` باید از چند محدودیت آگاه باشید:

- فقط زمانی کار می‌کند که یک گره را در همان سند جابه‌جا کنید.
- اگر بخواهید گرهی را که به DOM متصل نیست به یک والد متصل منتقل کنید، یا برعکس، کار نخواهد کرد.

در چنین مواردی، `moveBefore()` با استثنای `HierarchyRequestError` شکست می‌خورد. اگر محدودیت‌های بالا برای مورد استفاده خاص شما الزامی هستند، به‌جای آن از {{domxref("Node.insertBefore()")}} استفاده کنید یا از [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) برای مدیریت خطاهای ناشی از این موارد بهره ببرید.

## مثال‌ها

### جابه‌جایی یک گره دیدگاه با `moveBefore()`

در این نمایش، نشان می‌دهیم که چگونه می‌توان از `document.moveBefore()` برای جابه‌جایی یک گره دیدگاه در DOM استفاده کرد.

#### HTML

اچ‌تی‌ام‌ال یک الگوی حداقلی است که یک دیدگاه را داخل {{htmlelement("body")}} دارد.

```html live-sample___movebefore-comment
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>document.moveBefore() example</title>
  </head>
  <body>
    <!-- This comment should be at the end of the document -->
    <p>Some content</p>
  </body>
</html>
```

#### JavaScript

در اسکریپت خود، از میان تمام {{domxref("Node.childNodes", "childNodes")}} عنصر `<body>` حلقه می‌زنیم. وقتی گرهی با مقدار {{domxref("Node.nodeType", "nodeType")}} برابر با `8` پیدا می‌کنیم (که نشان‌دهنده یک گره دیدگاه است)، ارجاع به آن را در متغیری به نام `commentNode` ذخیره می‌کنیم. سپس `document.moveBefore()` را فراخوانی می‌کنیم و مشخص می‌کنیم که می‌خواهیم گره دیدگاه را جابه‌جا کنیم و آرگومان دوم را `null` قرار می‌دهیم تا دیدگاه را در انتهای گره‌های فرزند `Document` درج کنیم.

```js live-sample___movebefore-comment
let commentNode;

for (node of document.querySelector("body").childNodes) {
  if (node.nodeType === 8) {
    commentNode = node;
  }
}

document.moveBefore(commentNode, null);
```

#### نتیجه

نمونه رندر شده به این صورت است:

{{EmbedLiveSample("movebefore-comment", "100%", "60px")}}

اگر مثال را با ابزار توسعه‌دهنده مرورگر خود بررسی کنید، متوجه می‌شوید که دیدگاه به انتهای سند، پس از تگ بسته‌شونده `</html>` منتقل شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DocumentFragment.moveBefore()")}}
- {{domxref("Element.moveBefore()")}}
- {{domxref("Node.insertBefore()")}}