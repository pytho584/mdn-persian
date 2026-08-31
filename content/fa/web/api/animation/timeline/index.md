---
title: "Animation: timeline property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/timeline"
translated_by: "n8n + AI"
---

---
title: "Animation: timeline property"
short-title: timeline
slug: Web/API/Animation/timeline
page-type: web-api-instance-property
browser-compat: api.Animation.timeline
---

{{ APIRef("Web Animations") }}

ویژگی **`Animation.timeline`** در رابط {{domxref("Animation")}}، {{domxref("AnimationTimeline", "timeline")}} مرتبط با این انیمیشن را برمی‌گرداند یا تنظیم می‌کند. یک timeline منبعی از مقادیر زمانی برای اهداف همگام‌سازی است و یک شیء مبتنی بر {{domxref("AnimationTimeline")}} است. به‌طور پیش‌فرض، timeline انیمیشن و timeline سند {{domxref("Document")}} یکسان هستند.

## مقدار

یک {{domxref("AnimationTimeline", "شیء timeline", "", 1)}} که به عنوان منبع زمان‌بندی برای انیمیشن استفاده می‌شود، یا `null` برای استفاده از حالت پیش‌فرض، که همان timeline سند {{domxref("Document")}} است.

## مثال‌ها

در اینجا ما timeline انیمیشن را همانند timeline سند تنظیم می‌کنیم (به هر حال، این timeline پیش‌فرض برای همه انیمیشن‌ها است):

```js
animation.timeline = document.timeline;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}
- {{domxref("AnimationTimeline")}} شیء والد که همه timelineها از آن ارث می‌برند.
- {{domxref("DocumentTimeline")}} تنها نوع شیء timeline که در حال حاضر موجود است.
- {{domxref("Document.timeline")}} timeline پیش‌فرضی است که همه انیمیشن‌ها به آن اختصاص می‌یابند.