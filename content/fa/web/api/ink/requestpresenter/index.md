---
title: "Ink: requestPresenter() method"
---

---
title: "Ink: requestPresenter() method"
short-title: requestPresenter()
slug: Web/API/Ink/requestPresenter
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Ink.requestPresenter
---

{{APIRef("Ink API")}}{{SeeCompatTable}}

متد **`requestPresenter()`** از رابط {{domxref("Ink")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("DelegatedInkTrailPresenter")}} تکمیل می‌شود. این شیء برای مدیریت رندر ضربه‌های قلم به کار می‌رود.

## نحو

```js-nolint
requestPresenter(param)
```

### پارامترها

- `param` {{optional_inline}}
  - : یک شیء که ویژگی زیر را دارد:
    - `presentationArea` {{optional_inline}}
      - : یک {{domxref("Element")}} که رندر ضربه‌های قلم به داخل آن محدود می‌شود (به‌طور دقیق‌تر، جعبهٔ مرزی (border box) عنصر). اگر `param` ارسال نشود یا مقدار `presentationArea` برابر با `null` باشد، رندر جوهر به‌صورت پیش‌فرض به viewport دربرگیرنده محدود می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک نمونه از شیء {{domxref("DelegatedInkTrailPresenter")}} resolve می‌شود.

### استثناها

- `Error` {{domxref("DOMException")}}
  - : اگر `presentationArea` یک {{domxref("Element")}} معتبر نباشد یا در همان سند (document) شیء {{domxref("Ink")}} مرتبط نباشد، یک خطا پرتاب شده و عملیات لغو می‌شود.

## مثال

```js
async function inkInit() {
  const ink = navigator.ink;
  let presenter = await ink.requestPresenter({ presentationArea: canvas });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}