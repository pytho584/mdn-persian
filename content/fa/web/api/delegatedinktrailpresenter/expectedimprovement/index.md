---
title: "DelegatedInkTrailPresenter: expectedImprovement property"
---

---
title: "DelegatedInkTrailPresenter: expectedImprovement property"
short-title: expectedImprovement
slug: Web/API/DelegatedInkTrailPresenter/expectedImprovement
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.DelegatedInkTrailPresenter.expectedImprovement
---

{{APIRef("Ink API")}}{{Deprecated_header}}{{Non-Standard_Header}}

ویژگی فقط‌خواندنی **`expectedImprovement`** در رابط {{domxref("DelegatedInkTrailPresenter")}} مقداری را بر حسب میلی‌ثانیه بازمی‌گرداند که نشان‌دهندهٔ بهبود تأخیری است که با استفاده از این ارائه‌دهنده می‌توان انتظار داشت.

مقدار

یک عدد.

مثال

```js
async function inkInit() {
  const ink = navigator.ink;
  const presenter = await ink.requestPresenter({ presentationArea: canvas });
  console.log(presenter.expectedImprovement);

  // …
}
```

مشخصات

این ویژگی دیگر بخشی از مشخصات نیست.

سازگاری مرورگر

{{Compat}}