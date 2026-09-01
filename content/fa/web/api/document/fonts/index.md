---
title: "Document: fonts property"
---

---
title: "Document: fonts property"
short-title: fonts
slug: Web/API/Document/fonts
page-type: web-api-instance-property
browser-compat: api.Document.fonts
---

{{APIRef("DOM")}}

ویژگی **`fonts`** در رابط {{domxref("Document")}}، رابط {{domxref("FontFaceSet")}} سند را برمی‌گرداند.

این قابلیت بخشی از [CSS Font Loading API](/en-US/docs/Web/API/CSS_Font_Loading_API) است.

## مقدار

مقدار بازگشتی، رابط {{domxref("FontFaceSet")}} سند است. رابط `FontFaceSet` برای بارگذاری فونت‌های جدید، بررسی وضعیت فونت‌های بارگذاری‌شدهٔ قبلی و موارد مشابه مفید است.

## مثال‌ها

### انجام عملیات پس از بارگذاری فونت‌ها

```js
document.fonts.ready.then((fontFaceSet) => {
  // Any operation that needs to be done only after all used fonts
  // have finished loading can go here.
  const fontFaces = [...fontFaceSet];
  console.log(fontFaces);
  // some fonts may still be unloaded if they aren't used on the site
  console.log(fontFaces.map((f) => f.status));
});
```

این Promise زمانی برآورده می‌شود که عملیات بارگذاری و چیدمان همهٔ فونت‌های استفاده‌شده به پایان رسیده باشد. مجموعهٔ فونت‌های استفاده‌شده می‌تواند با مجموعهٔ فونت‌های _اعلام‌شده_ متفاوت باشد؛ برای مثال، اگر فونت‌های اختیاری (یعنی فونت‌هایی که از طریق `font-display: optional` اعلام شده‌اند) نتوانسته باشند به‌موقع بارگذاری شوند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("FontFaceSet")}}
- {{domxref("FontFace")}}