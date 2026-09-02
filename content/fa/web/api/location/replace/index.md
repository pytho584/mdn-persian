---
title: "Location: replace() method"
short-title: replace()
slug: Web/API/Location/replace
page-type: web-api-instance-method
browser-compat: api.Location.replace
---

{{ APIRef("HTML DOM") }}

متد **`replace()`** از رابط {{DOMXref("Location")}}، منبع فعلی را با منبع موجود در URL داده‌شده جایگزین می‌کند. تفاوت آن با متد {{domxref("Location.assign","assign()")}} در این است که پس از استفاده از `replace()`، صفحهٔ فعلی در تاریخچهٔ جلسه ({{domxref("History")}}) ذخیره نمی‌شود؛ بنابراین کاربر نمی‌تواند با دکمهٔ _بازگشت_ به آن بازگردد. این متد نباید با متد {{jsxref("String")}} یعنی {{jsxref("String.prototype.replace()")}} اشتباه گرفته شود.

## نحو

```js-nolint
replace(url)
```

### پارامترها

- `url`
  - : یک رشته یا هر شیء دیگری که دارای {{Glossary("stringifier")}} باشد، مانند یک شیء {{domxref("URL")}}، که URL صفحهٔ موردنظر برای پیمایش را شامل می‌شود.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : مرورگرها پیمایش‌ها را محدود می‌کنند و اگر این متد بیش از حد مکرر فراخوانی شود، ممکن است این خطا را صادر کنند، هشدار تولید کنند، یا فراخوانی را نادیده بگیرند.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر پارامتر `url` ارائه‌شده یک URL معتبر نباشد، این خطا صادر می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
// Navigate to the Location.reload article by replacing this page
window.location.replace(
  "https://developer.mozilla.org/en-US/docs/Web/API/Location.reload",
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("Location")}} که این متد به آن تعلق دارد.
- متدهای مشابه: {{domxref("Location.assign()")}} و {{domxref("Location.reload()")}}.