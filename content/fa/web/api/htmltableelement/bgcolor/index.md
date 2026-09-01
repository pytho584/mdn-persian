```markdown
---
title: "HTMLTableElement: bgColor property"
short-title: bgColor
slug: Web/API/HTMLTableElement/bgColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableElement.bgColor
---

{{APIRef("HTML DOM")}} {{Deprecated_Header}}

خاصیت **`bgcolor`** از {{domxref("HTMLTableElement")}} رنگ پس‌زمینه جدول را مشخص می‌کند.

> [!NOTE]
> دیگر از این ویژگی استفاده نکنید. در عوض، از ویژگی CSS {{cssxref("background-color")}} با تغییر ویژگی [`style`](/en-US/docs/Web/API/HTMLElement/style) عنصر یا با استفاده از یک قانون سبک استفاده کنید.

## مقدار

یک رشته (string) که یک مقدار رنگ را نمایش می‌دهد.

وقتی مقدار `null` تنظیم شود، آن مقدار `null` به رشته خالی (`""`) تبدیل می‌شود، بنابراین `elt.bgColor = null` معادل `elt.bgColor = ""` است.

## مثال‌ها

```js
// تنظیم رنگ پس‌زمینه جدول به آبی روشن
const t = document.getElementById("TableA");
t.bgColor = "lightblue";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("background-color")}}
```