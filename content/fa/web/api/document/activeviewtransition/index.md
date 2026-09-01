---
title: "Document: activeViewTransition property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Document/activeViewTransition"
---

---
title: "Document: activeViewTransition property"
short-title: activeViewTransition
slug: Web/API/Document/activeViewTransition
page-type: web-api-instance-property
browser-compat: api.Document.activeViewTransition
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`activeViewTransition`** در رابط {{domxref("Document")}}، یک نمونه از {{domxref("ViewTransition")}} را برمی‌گرداند که نمایانگر [انتقال نما](/en-US/docs/Web/API/View_Transition_API) فعالِ فعلی روی سند است.

{{domxref("ViewTransition")}} فعلی را می‌توان از راه‌های دیگری نیز به دست آورد:

- مقدار بازگشتی {{domxref("Document.startViewTransition()")}} در مورد انتقال‌های نمای هم‌سند (same-document).
- ویژگی `viewTransition` در اشیاء رویداد {{domxref("Window.pagereveal_event", "pagereveal")}} و {{domxref("Window.pageswap_event", "pageswap")}} در مورد انتقال‌های نمای بین‌سندی (cross-document).

با این حال، ویژگی `activeViewTransition` روشی سازگار برای دسترسی به انتقال نمای فعال در هر زمینه‌ای فراهم می‌کند، بدون آنکه نگران ذخیره‌سازی ارجاعی به آن برای استفاده بعدی باشید.

## مقدار

یک {{domxref("ViewTransition")}} یا `null` در صورتی که هیچ انتقال نمای فعالی وجود نداشته باشد.

## مثال‌ها

```js
// شروع یک انتقال نما
document.startViewTransition(() => {
  // به‌روزرسانی رابط کاربری برای نمایش وضعیت جدید
  updateUI();
});

// بررسی اینکه آیا انتقال نمایی در حال حاضر فعال است
if (document.activeViewTransition) {
  console.log("یک انتقال نما در حال حاضر فعال است");
}

// واکنش به پایان یافتن انتقال نما
document.activeViewTransition.finished.then(() => {
  console.log("انتقال نما پایان یافت");
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.startViewTransition()")}}
- {{domxref("Element.activeViewTransition")}}
- رویداد {{domxref("Window.pagereveal_event", "pagereveal")}}
- رویداد {{domxref("Window.pageswap_event", "pageswap")}}
- [View Transition API](/en-US/docs/Web/API/View_Transition_API)
- {{domxref("ViewTransition")}}