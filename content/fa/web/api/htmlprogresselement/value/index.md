---
title: "HTMLProgressElement: value property"
short-title: value
slug: Web/API/HTMLProgressElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLProgressElement.value
---

{{APIRef("HTML DOM")}}

ویژگی **`value`** در رابط {{DOMxRef("HTMLProgressElement")}}، پیشرفت فعلی عنصر {{HTMLElement("progress")}} را نمایش می‌دهد.

## مقدار

یک عدد اعشاری. اگر مقدار {{DOMxRef("HTMLProgressElement.max", "max")}} روی نوار پیشرفت تنظیم نشده باشد، مقدار `value` بین ۰٫۰ و ۱٫۰ خواهد بود. اگر مقدار `max` تنظیم شده باشد، `value` بین `0` و مقدار `max` خواهد بود.

اگر ویژگی `value` بر روی شیء {{DOMxRef("HTMLProgressElement")}} تنظیم نشده باشد، نوار پیشرفت نامعین (indeterminate) باقی می‌ماند.

### مثال‌ها

### HTML

```html
Determinate Progress bar: <progress id="pBar"></progress> <span>0</span>%
<br />
Indeterminate Progress bar: <progress></progress>
```

### JavaScript

```js
const pBar = document.getElementById("pBar");
const span = document.getElementsByTagName("span")[0];

pBar.max = 100;
pBar.value = 0;

setInterval(() => {
  pBar.value = pBar.value < pBar.max ? pBar.value + 1 : 0;

  span.textContent = Math.trunc(pBar.position * 100);
}, 100);
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}