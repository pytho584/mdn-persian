---
title: "HTMLTableElement: cellSpacing property"
short-title: cellSpacing
slug: Web/API/HTMLTableElement/cellSpacing
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableElement.cellSpacing
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

اگرچه باید به جای آن از ویژگی CSS {{cssxref("border-spacing")}} استفاده کنید، ویژگی **`cellSpacing`** در رابط منسوخ {{domxref("HTMLTableElement")}} فاصلهٔ اطراف عناصر {{HTMLElement("th")}} و {{HTMLElement("td")}} را که نشان‌دهندهٔ سلول‌های یک جدول هستند، مشخص می‌کند. هر دو سلول با مجموع `cellSpacing` هر یک از آن دو سلول از یکدیگر جدا می‌شوند.

## مقدار

یک رشته (string) که یا یک عدد بر حسب پیکسل (مانند `"10"`) است یا یک مقدار درصدی (مانند `"10%"`).

هنگامی که روی مقدار `null` تنظیم شود، آن مقدار `null` به رشتهٔ خالی (`""`) تبدیل می‌شود، بنابراین `elt.cellSpacing = null` معادل `elt.cellSpacing = ""` است.

## مثال‌ها

این مثال فاصله سلول‌ها را برای یک جدول مشخص به ۱۰ پیکسل تنظیم می‌کند.

```js
const t = document.getElementById("TableA");
t.cellSpacing = "10";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}