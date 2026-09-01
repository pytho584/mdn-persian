```
---
title: "Element: role property"
---

---
title: "Element: role property"
short-title: role
slug: Web/API/Element/role
page-type: web-api-instance-property
browser-compat: api.Element.role
---

{{ ApiRef("DOM") }}

ویژگی **`role`** در رابط {{domxref("Element")}}، نقش [WAI-ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) را که به‌صورت صریح برای عنصر تعیین شده است، بازمی‌گرداند.

همه عناصر HTML یک نقش ARIA ضمنی دارند، حتی اگر آن نقش [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) باشد. این ارتباط معنایی به ابزارها امکان می‌دهد تا شیء را به شکلی ارائه و تعامل با آن را پشتیبانی کنند که با انتظارات کاربران از سایر اشیاء هم‌نوع سازگار باشد. ویژگی `role` برای تعیین صریح نقش ARIA عنصر استفاده می‌شود و نقش ضمنی را بازنویسی می‌کند. برای مثال، یک {{htmlelement("ul")}} که نقش ضمنی [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role) را دارد، ممکن است ویژگی `role="treegrid"` به‌صورت صریح برای آن تنظیم شده باشد. ویژگی `role` مقدار صریحاً تنظیم‌شده ویژگی `role` را بازتاب می‌دهد — در این مورد `treegrid`؛ و نقش ضمنی `list` عنصر را بازنمی‌گرداند مگر اینکه به‌صورت صریح تنظیم شده باشد.

فهرست کامل نقش‌های تعریف‌شده ARIA را می‌توانید در صفحه مرجع [نقش‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) مشاهده کنید.

## مقدار

یک رشته (string)؛ مقدار ویژگی `role` یا اگر به‌صورت صریح تنظیم نشده باشد، `null`.

## مثال‌ها

در این مثال، به تصاویری که ویژگی `alt` آن‌ها خالی یا وجود ندارد، نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) داده می‌شود:

```js
const images = document.querySelectorAll("img");
images.forEach((image) => {
  if (!image.alt) {
    image.role = "presentation";
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ElementInternals.role")}}
- [ویژگی‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes)
```