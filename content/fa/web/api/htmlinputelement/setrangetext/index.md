---
title: "HTMLInputElement: setRangeText() method"
short-title: setRangeText()
slug: Web/API/HTMLInputElement/setRangeText
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.setRangeText
---

{{APIRef("HTML DOM")}}

متد **`HTMLInputElement.setRangeText()`** یک محدوده از متن را در یک عنصر {{HTMLElement("input")}} یا {{HTMLElement("textarea")}} با یک رشته جدید جایگزین می‌کند.

## نحو

```js-nolint
setRangeText(replacement)
setRangeText(replacement, start)
setRangeText(replacement, start, end)
setRangeText(replacement, start, end, selectMode)
```

### پارامترها

- `replacement`
  - : رشته‌ای که قرار است درج شود.
- `start` {{optional_inline}}
  - : شاخص مبتنی بر صفر اولین کاراکتری که باید جایگزین شود. پیش‌فرض مقدار فعلی `selectionStart` (آغاز انتخاب فعلی کاربر) است.
- `end` {{optional_inline}}
  - : شاخص مبتنی بر صفر کاراکتر _بعد از_ آخرین کاراکتری که باید جایگزین شود. پیش‌فرض مقدار فعلی `selectionEnd` (پایان انتخاب فعلی کاربر) است.
- `selectMode` {{optional_inline}}
  - : رشته‌ای که نحوه تنظیم انتخاب پس از جایگزینی متن را مشخص می‌کند. مقادیر ممکن:
    - `"select"` متن تازه درج شده را انتخاب می‌کند.
    - `"start"` انتخاب را به درست قبل از متن درج شده منتقل می‌کند.
    - `"end"` انتخاب را به درست بعد از متن درج شده منتقل می‌کند.
    - `"preserve"` سعی می‌کند انتخاب را حفظ کند. این مقدار پیش‌فرض است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

برای جایگزینی بخشی از متن در جعبه متن، دکمه این مثال را کلیک کنید. متن تازه درج شده پس از آن برجسته (انتخاب) می‌شود.

### HTML

```html
<input
  type="text"
  id="text-box"
  size="30"
  value="This text has NOT been updated." />
<button>Update text</button>
```

### JavaScript

```js
function selectText() {
  const input = document.getElementById("text-box");
  input.focus();
  input.setRangeText("ALREADY", 14, 17, "select");
}

document.querySelector("button").addEventListener("click", selectText);
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{HTMLElement("textarea")}}
- {{domxref("HTMLInputElement")}}
- {{domxref("Selection")}}