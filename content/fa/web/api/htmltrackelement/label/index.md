---
title: "HTMLTrackElement: label property"
---

---
title: "HTMLTrackElement: label property"
short-title: label
slug: Web/API/HTMLTrackElement/label
page-type: web-api-instance-property
browser-compat: api.HTMLTrackElement.label
---

{{ApiRef("HTML DOM")}}

ویژگی **`label`** از {{domxref("HTMLTrackElement")}} عنوان قابل‌خواندن برای کاربر را نشان می‌دهد که هنگام فهرست‌کردن زیرنویس‌ها، شرح‌ها و توصیف‌های صوتی برای یک track نمایش داده می‌شود. این ویژگی بازتاب‌دهندهٔ ویژگی [`label`](/en-US/docs/Web/HTML/Reference/Elements/track#label) عنصر {{htmlelement("track")}} است.

## مقدار

یک رشته.

## مثال

```js
const trackElement = document.getElementById("exampleTrack");
console.log(`Track's label: ${trackElement.label}`);
trackElement.label = "Updated label";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTrackElement.track")}}
- {{domxref("HTMLTrackElement.kind")}}