```yaml
---
title: "Node: appendChild() method"
short-title: appendChild()
slug: Web/API/Node/appendChild
page-type: web-api-instance-method
browser-compat: api.Node.appendChild
---

{{APIRef("DOM")}}

متد **`appendChild()`** از رابط {{domxref("Node")}} یک گره را به انتهای فهرست فرزندان یک گره والد مشخص اضافه می‌کند.

> [!NOTE]
> اگر فرزند داده شده ارجاعی به یک گره موجود در سند باشد، `appendChild()` آن را از موقعیت فعلی خود به موقعیت جدید منتقل می‌کند.

اگر فرزند داده شده یک {{domxref("DocumentFragment")}} باشد، کل محتویات {{domxref("DocumentFragment")}} به لیست فرزندان گره والد مشخص منتقل می‌شود.

`appendChild()` گره تازه اضافه شده را برمی‌گرداند، یا اگر فرزند یک {{domxref("DocumentFragment")}} باشد، قطعه خالی را برمی‌گرداند.

> [!NOTE]
> بر خلاف این متد، متد {{domxref("Element.append()")}} از چندین آرگومان و اضافه کردن رشته‌ها پشتیبانی می‌کند. اگر گره شما یک عنصر است، می‌توانید استفاده از آن را ترجیح دهید.

## نحو

```js-nolint
appendChild(child)
```

### پارامترها

- `child`
  - : گره‌ای که باید به گره والد مشخص شده (معمولاً یک عنصر) اضافه شود.

### مقدار بازگشتی

یک {{domxref("Node")}} که همان فرزند اضافه شده (`child`) است، به جز زمانی که `child` یک {{domxref("DocumentFragment")}} باشد، که در آن صورت {{domxref("DocumentFragment")}} خالی برگردانده می‌شود.

### استثناها

- `HierarchyRequestError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که محدودیت‌های درخت DOM نقض شود، یعنی اگر یکی از موارد زیر رخ دهد:
    - اگر والد `child` یک {{domxref("Document")}}، {{domxref("DocumentFragment")}} یا {{domxref("Element")}} نباشد.
    - اگر درج `child` منجر به یک چرخه شود، یعنی `child` جد گره باشد.
    - اگر `child` یک {{domxref("DocumentFragment")}}، {{domxref("DocumentType")}}، {{domxref("Element")}} یا {{domxref("CharacterData")}} نباشد.
    - اگر گره جاری یک {{domxref("Text")}} باشد و والد آن یک {{domxref("Document")}} باشد.
    - اگر گره جاری یک {{domxref("DocumentType")}} باشد و والد آن _نه_ یک {{domxref("Document")}} باشد، زیرا یک _doctype_ باید همیشه فرزند مستقیم یک _document_ باشد.
    - اگر والد گره یک {{domxref("Document")}} باشد و `child` یک {{domxref("DocumentFragment")}} با بیش از یک فرزند {{domxref("Element")}} باشد، یا یک فرزند {{domxref("Text")}} داشته باشد.
    - اگر درج `child` منجر به {{domxref("Document")}} با بیش از یک {{domxref("Element")}} به عنوان فرزند شود.

## توضیحات

اگر فرزند داده شده ارجاعی به یک گره موجود در سند باشد، `appendChild()` آن را از موقعیت فعلی خود به موقعیت جدید منتقل می‌کند — نیازی به حذف گره از والد خود قبل از اضافه کردن آن به گره دیگر نیست. این بدان معناست که یک گره نمی‌تواند همزمان در دو نقطه از سند باشد. از متد {{domxref("Node.cloneNode()")}} می‌توان برای تهیه یک کپی از گره قبل از اضافه کردن آن به والد جدید استفاده کرد. کپی‌های ساخته شده با `cloneNode` به طور خودکار همگام نگه داشته نمی‌شوند.

`appendChild()` به جای گره والد، گره تازه اضافه شده را برمی‌گرداند. این بدان معناست که می‌توانید بلافاصله پس از ایجاد گره جدید، آن را اضافه کنید بدون اینکه مرجع آن را از دست بدهید:

```js
const paragraph = document.body.appendChild(document.createElement("p"));
// می‌توانید بعداً عناصر بیشتری به پاراگراف اضافه کنید
```

از طرف دیگر، نمی‌توانید از `appendChild()` به صورت یک [API روان](https://en.wikipedia.org/wiki/Fluent_interface) (مانند jQuery) استفاده کنید.

```js example-bad
// این کار سه پاراگراف اضافه نمی‌کند:
// سه عنصر به جای خواهر و برادر، تو در تو می‌شوند
document.body
  .appendChild(document.createElement("p"))
  .appendChild(document.createElement("p"))
  .appendChild(document.createElement("p"));
```

## مثال

### اضافه کردن یک پاراگراف به بدنه

```js
// یک عنصر پاراگراف جدید ایجاد کنید و آن را به انتهای بدنه سند اضافه کنید
const p = document.createElement("p");
document.body.appendChild(p);
```

### ایجاد یک ساختار DOM تو در تو

در این مثال، سعی می‌کنیم یک ساختار DOM تو در تو را با استفاده از حداقل متغیرهای موقت ایجاد کنیم.

```js
const fragment = document.createDocumentFragment();
const li = fragment
  .appendChild(document.createElement("section"))
  .appendChild(document.createElement("ul"))
  .appendChild(document.createElement("li"));
li.textContent = "hello world";

document.body.appendChild(fragment);
```

این درخت DOM زیر را تولید می‌کند:

```html
<section>
  <ul>
    <li>hello world</li>
  </ul>
</section>
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.removeChild()")}}
- {{domxref("Node.replaceChild()")}}
- {{domxref("Node.insertBefore()")}}
- {{domxref("Node.hasChildNodes()")}}
- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("Element.append()")}}
```