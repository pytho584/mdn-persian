---
title: "Node: removeChild() method"
short-title: removeChild()
slug: Web/API/Node/removeChild
page-type: web-api-instance-method
browser-compat: api.Node.removeChild
---

{{APIRef("DOM")}}

متد **`removeChild()`** از رابط {{domxref("Node")}} یک گرهٔ فرزند را از DOM حذف می‌کند و گرهٔ حذف‌شده را بازمی‌گرداند.

> [!NOTE]
> تا زمانی که یک ارجاع (reference) به گرهٔ حذف‌شده نگه داشته شود،
> آن گره همچنان در حافظه وجود دارد، اما دیگر بخشی از DOM نیست.
> همچنان می‌توان بعداً در کد از آن استفاده کرد.
>
> اگر مقدار بازگشتیِ `removeChild()` ذخیره نشود و هیچ ارجاع دیگری نیز نگه داشته نشود،
> پس از مدت کوتاهی به‌طور خودکار از حافظه [حذف خواهد شد](/en-US/docs/Web/JavaScript/Guide/Memory_management).

برخلاف {{domxref("Node.cloneNode()")}}، مقدار بازگشتی، اشیاء `EventListener` مرتبط با خود را حفظ می‌کند.

## Syntax

```js-nolint
removeChild(child)
```

### پارامترها

- `child`
  - : یک {{domxref("Node")}} که گرهٔ فرزند موردنظر برای حذف از DOM است.

### مقدار بازگشتی

گرهٔ فرزند حذف‌شده (`child`).

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `child` فرزند آن گره نباشد پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `child` برابر با `null` باشد پرتاب می‌شود.

## مثال‌ها

### مثال‌های ساده

با توجه به HTML زیر:

```html
<div id="parent">
  <div id="child"></div>
</div>
```

برای حذف یک عنصر مشخص وقتی گرهٔ والد آن را می‌دانیم:

```js
const parent = document.getElementById("parent");
const child = document.getElementById("child");
const throwawayNode = parent.removeChild(child);
```

برای حذف یک عنصر مشخص بدون نیاز به مشخص کردن گرهٔ والد آن:

```js
const node = document.getElementById("child");
if (node.parentNode) {
  node.parentNode.removeChild(node);
}
```

برای حذف همهٔ فرزندان یک عنصر:

```js
const element = document.getElementById("idOfParent");
while (element.firstChild) {
  element.removeChild(element.firstChild);
}
```

### ایجاد TypeError

```html
<!--نمونه کد HTML-->
<div id="parent"></div>
```

```js
const parent = document.getElementById("parent");
const child = document.getElementById("child");

// پرتاب خطای Uncaught TypeError
const garbage = parent.removeChild(child);
```

### ایجاد NotFoundError

```html
<!--نمونه کد HTML-->
<div id="parent">
  <div id="child"></div>
</div>
```

```js
const parent = document.getElementById("parent");
const child = document.getElementById("child");

// این فراخوانی اول به‌درستی گره را حذف می‌کند
const garbage = parent.removeChild(child);

// فراخوانی دوم باعث ایجاد NotFoundError می‌شود
parent.removeChild(child);
```

## Specifications

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.replaceChild()")}}
- {{domxref("Node.parentNode")}}
- {{domxref("Element.remove()")}}
- {{domxref("Node.cloneNode()")}}