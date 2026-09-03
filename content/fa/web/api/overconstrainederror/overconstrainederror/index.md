---
title: "OverconstrainedError: OverconstrainedError() constructor"
short-title: OverconstrainedError()
slug: Web/API/OverconstrainedError/OverconstrainedError
page-type: web-api-constructor
browser-compat: api.OverconstrainedError.OverconstrainedError
---

{{APIRef("Media Capture and Streams")}}

سازنده **`OverconstrainedError()`** یک شیء جدید از نوع {{domxref("OverconstrainedError")}} می‌سازد که نشان می‌دهد مجموعه قابلیت‌های مورد نظر برای {{domxref("MediaStreamTrack")}} جاری در حال حاضر قابل برآورده شدن نیست. هنگامی که این رویداد روی یک `MediaStreamTrack` پرتاب می‌شود، آن `MediaStreamTrack` بی‌صدا می‌شود تا زمانی که یا محدودیت‌های جاری قابل اعمال باشند یا محدودیت‌های قابل قبولی اعمال شوند.

## نحو (Syntax)

```js-nolint
new OverconstrainedError()
```

### پارامترها

- `constraint`
  - : محدودیتی که برآورده نشده است.
- `message` {{optional_inline}}
  - : متنی برای ویژگی `message` خطا. مقدار پیش‌فرض یک رشته خالی است.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگرها (Browser compatibility)

{{Compat}}