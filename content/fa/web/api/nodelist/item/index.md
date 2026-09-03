---
title: "NodeList: item() method"
---

---
title: "NodeList: item() method"
short-title: item()
slug: Web/API/NodeList/item
page-type: web-api-instance-method
browser-compat: api.NodeList.item
---

{{APIRef("DOM")}}

این متد یک گره را از یک [`NodeList`](/en-US/docs/Web/API/NodeList) بر اساس ایندکس برمی‌گرداند. تا زمانی که آرگومان ارائه کنید، هیچ استثنایی پرتاب نمی‌کند. اگر ایندکس خارج از محدوده باشد، مقدار `null` برگردانده می‌شود و اگر هیچ آرگومانی ارائه نشود، یک {{jsxref("TypeError")}} پرتاب می‌شود.

در JavaScript، به جای فراخوانی `nodeList.item(index)`، می‌توانید مستقیماً به `index` دسترسی داشته باشید؛ مانند `nodeList[index]`.

## سینتکس

```js-nolint
item(index)
```

### پارامترها

- `index`
  - : ایندکس گرهی که باید بازیابی شود. ایندکس از صفر شروع می‌شود.

### مقدار بازگشتی

گره واقع در ایندکس `index` در `nodeList` که توسط متد `item` برگردانده می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر هیچ آرگومانی ارائه نشود، پرتاب می‌شود.

## مثال‌ها

```js
const tables = document.getElementsByTagName("table");
const firstTable = tables.item(1); // or tables[1] - returns the second table in the DOM
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}