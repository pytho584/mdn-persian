---
title: انتخاب و پیمایش در درخت DOM
slug: Web/API/Document_Object_Model/Selection_and_traversal_on_the_DOM_tree
page-type: guide
---

{{DefaultAPISidebar("DOM")}}

API انتخابگرها (Selectors API) روش‌هایی را فراهم می‌کند که بازیابی گره‌های {{domxref("Element")}} را از DOM با تطبیق دادن با مجموعه‌ای از [انتخابگرها](/en-US/docs/Web/CSS/Guides/Selectors) سریع و آسان می‌سازد. این روش بسیار سریع‌تر از تکنیک‌های قدیمی است که در آن‌ها برای مثال لازم بود از یک حلقه در کد جاوااسکریپت برای یافتن آیتم‌های موردنظر استفاده کنید.

## رابط NodeSelector

این مشخصات دو روش جدید به هر شیءای که رابط‌های {{domxref("Document")}}، {{domxref("DocumentFragment")}} یا {{domxref("Element")}} را پیاده‌سازی می‌کند اضافه می‌کند:

- {{domxref("Element.querySelector", "querySelector()")}}
  - : اولین گره {{domxref("Element")}} مطابق را در زیردرخت آن گره برمی‌گرداند. اگر گره‌ای مطابق یافت نشود، `null` برگردانده می‌شود.
- {{domxref("Element.querySelectorAll", "querySelectorAll()")}}
  - : یک {{domxref("NodeList")}} شامل همه گره‌های `Element` مطابق در زیردرخت آن گره برمی‌گرداند، یا اگر موردی یافت نشود، یک `NodeList` خالی.

> [!NOTE]
> {{domxref("NodeList")}} که توسط {{domxref("Element.querySelectorAll()", "querySelectorAll()")}} برگردانده می‌شود زنده (live) نیست؛ یعنی تغییرات DOM در این مجموعه منعکس نمی‌شود. این با سایر روش‌های جست‌وجوی DOM که فهرست گره‌های زنده برمی‌گردانند متفاوت است.

می‌توانید مثال‌ها و جزئیات را با مطالعه مستندات روش‌های {{domxref("Element.querySelector()")}} و {{domxref("Element.querySelectorAll()")}} بیابید.

## انتخابگرها

روش‌های انتخابگر، [انتخابگرها](/en-US/docs/Web/CSS/Guides/Selectors) را برای تعیین اینکه کدام عنصر یا عناصر باید برگردانده شوند می‌پذیرند. این شامل [فهرست انتخابگرها](/en-US/docs/Web/CSS/Reference/Selectors/Selector_list) نیز می‌شود، بنابراین می‌توانید چندین انتخابگر را در یک پرس‌وجوی واحد گروه‌بندی کنید.

برای محافظت از حریم خصوصی کاربر، برخی [شبه‌کلاس‌ها](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes) پشتیبانی نمی‌شوند یا رفتار متفاوتی دارند. برای مثال {{cssxref(":visited")}} هیچ موردی را برنمی‌گرداند و {{cssxref(":link")}} به‌عنوان {{cssxref(":any-link")}} در نظر گرفته می‌شود.

فقط عناصر قابل انتخاب هستند، بنابراین [شبه‌عنصرها](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) پشتیبانی نمی‌شوند.

## مثال‌ها

برای انتخاب همه عناصر پاراگراف (`p`) در یک سند که کلاس‌هایشان شامل `warning` یا `note` است، می‌توانید به این صورت عمل کنید:

```js
const special = document.querySelectorAll("p.warning, p.note");
```

همچنین می‌توانید با شناسه (ID) جست‌وجو کنید. برای مثال:

```js
const el = document.querySelector("#main, #basic, #exclamation");
```

پس از اجرای کد بالا، `el` شامل اولین عنصر در سند است که شناسه آن یکی از `main`، `basic` یا `exclamation` باشد.

## همچنین ببینید

- [مشخصات انتخابگرها](https://drafts.csswg.org/selectors/)
- [انتخابگرهای CSS](/en-US/docs/Web/CSS/Guides/Selectors)
- {{domxref("Element.querySelector()")}}
- {{domxref("Element.querySelectorAll()")}}
- {{domxref("Document.querySelector()")}}
- {{domxref("Document.querySelectorAll()")}}