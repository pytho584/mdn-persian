---
title: "HTMLFencedFrameElement: allow property"
short-title: allow
slug: Web/API/HTMLFencedFrameElement/allow
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLFencedFrameElement.allow
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

ویژگی **`allow`** در {{domxref("HTMLFencedFrameElement")}} مقدار ویژگی `allow` عنصر متناظر {{htmlelement("fencedframe")}} را می‌خواند و تنظیم می‌کند. این ویژگی یک [خط‌مشی مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) را نشان می‌دهد که هنگام نخستین بار تعبیه‌شدن محتوا روی آن اعمال می‌شود.

همهٔ خط‌مشی‌های مجوز در قاب‌های حصاردار مجاز نیستند. مجوزهای مجاز در [خط‌مشی‌های مجوز موجود برای قاب‌های حصاردار](/en-US/docs/Web/HTML/Reference/Elements/fencedframe#permissions_policies_available_to_fenced_frames) فهرست شده‌اند؛ این مجوزها برای بارگذاری محتوای قاب حصاردار که از APIهای مشخص‌شده می‌آید الزامی هستند. اگر ویژگی `allow` را تنظیم نکنید، آن مجوزها به‌طور پیش‌فرض مجاز خواهند بود. اگر می‌خواهید مجموعهٔ مجوزها را محدودتر کنید، باید مطمئن شوید که همهٔ مجوزهای لازم برای APIهایی که استفاده می‌کنید در ویژگی `allow` تنظیم شده باشند.

## مقدار

یک رشته که نمایانگر یک [خط‌مشی مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) است.

## مثال‌ها

```js
const frame = document.createElement("fencedframe");
console.log(frame.allow);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [قاب‌های حصاردار (Fenced frames)](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com
