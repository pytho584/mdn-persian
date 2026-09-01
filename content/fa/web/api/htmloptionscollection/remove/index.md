---
title: "HTMLOptionsCollection: remove() method"
short-title: remove()
slug: Web/API/HTMLOptionsCollection/remove
page-type: web-api-instance-method
browser-compat: api.HTMLOptionsCollection.remove
---

{{ APIRef("HTML DOM") }}

متد **`remove()`** از رابط {{DOMxRef("HTMLOptionsCollection")}}، عنصر {{HTMLElement("option")}} مشخص‌شده با ایندکس را از این مجموعه حذف می‌کند.

## سینتکس

```js-nolint
remove(index)
```

### پارامترها

- `index`
  - : یک عدد صحیح مبتنی بر صفر برای ایندکس {{ domxref("HTMLOptionElement") }} در {{DOMxRef("HTMLOptionsCollection")}}. اگر ایندکس یافت نشود، متد هیچ تأثیری ندارد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const optionList = document.querySelector("select").options;
const listLength = optionList.length;
optionList.remove(listLength - 1); // removes the last item
optionList.remove(0); // removes the first item
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLOptionsCollection.add()")}}
- {{DOMxRef("HTMLOptionsCollection.length")}}
- {{DOMxRef("HTMLOptionsCollection.selectedIndex")}}
- {{domxref("HTMLOptionsCollection")}}
- {{domxref("Element.remove")}}