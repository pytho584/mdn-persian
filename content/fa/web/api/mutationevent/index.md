---
title: MutationEvent
slug: Web/API/MutationEvent
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent
---

{{APIRef("UI Events")}}{{Deprecated_Header}}{{non-standard_header}}

رابطهٔ **`MutationEvent`** ویژگیهای رویدادی را فراهم میکند که مخصوص تغییرات در سلسلهمراتب و گرههای مدل شیء سند (DOM) هستند.

> [!NOTE]
> استفاده از _رویدادهای تغییر (mutation events)_ مشکلآفرین است:
>
> - طراحی آنها [ناقص](https://lists.w3.org/Archives/Public/public-webapps/2011JulSep/0779.html) است.
> - افزودن شنوندههای تغییر DOM به یک سند، [بهشدت کارایی](https://groups.google.com/g/mozilla.dev.platform/c/L0Lx11u5Bvs?pli=1) تغییرات بعدی DOM در آن سند را کاهش میدهد (۱٫۵ تا ۷ برابر کندتر!). علاوه بر این، حذف شنوندهها نیز آسیب را جبران نمیکند.
> - سازگاری ضعیفی با مرورگرهای مختلف دارند: سافاری از `DOMAttrModified` پشتیبانی نمیکند (به [باگ 8191 وبکیت](https://webkit.org/b/8191) مراجعه کنید) و فایرفاکس از _رویدادهای نام تغییر (mutation name events)_ مانند `DOMElementNameChanged` و `DOMAttributeNameChanged` پشتیبانی نمیکند.
>
> این رویدادها به نفع [mutation observers](/en-US/docs/Web/API/MutationObserver) منسوخ شدهاند. **بهجای آنها از این موارد استفاده کنید.**

{{InheritanceDiagram}}

## ویژگیهای نمونه

_این رابط همچنین ویژگیهای والد خود {{domxref("UIEvent")}} و بهطور غیرمستقیم {{domxref("Event")}} را به ارث میبرد._

- {{domxref("MutationEvent.attrChange")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : مشخص میکند چه نوع تغییری باعث رویداد `DOMAttrModified` شده است. میتواند `MODIFICATION` (`1`)، `ADDITION` (`2`) یا `REMOVAL` (`3`) باشد. برای سایر رویدادها معنایی ندارد و برابر `0` قرار میگیرد.
- {{domxref("MutationEvent.attrName")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : نام گرهٔ متأثر از رویداد `DOMAttrModified` را مشخص میکند. برای سایر رویدادها معنایی ندارد و برابر رشتهٔ خالی (`""`) قرار میگیرد.
- {{domxref("MutationEvent.newValue")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : در رویدادهای `DOMAttrModified`، مقدار جدید گرهٔ {{domxref("Attr")}} تغییریافته را شامل میشود. در رویدادهای `DOMCharacterDataModified`، مقدار جدید گرهٔ {{domxref("CharacterData")}} تغییریافته را شامل میشود. در سایر موارد، رشتهٔ خالی (`""`) را برمیگرداند.
- {{domxref("MutationEvent.prevValue")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : در رویدادهای `DOMAttrModified`، مقدار قبلی گرهٔ {{domxref("Attr")}} تغییریافته را شامل میشود. در رویدادهای `DOMCharacterDataModified`، مقدار قبلی گرهٔ {{domxref("CharacterData")}} تغییریافته را شامل میشود. در سایر موارد، رشتهٔ خالی (`""`) را برمیگرداند.
- {{domxref("MutationEvent.relatedNode")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : گرهٔ مرتبط با رویداد را مشخص میکند، مانند گرهٔ تغییریافته در زیردرخت برای `DOMSubtreeModified`.

## روشهای نمونه

- {{domxref("MutationEvent.initMutationEvent()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : روش سازندهای که یک `MutationEvent` جدید پیکربندیشده با پارامترهای دادهشده برمیگرداند.

## فهرست رویدادهای تغییر

در ادامه فهرست همهٔ رویدادهای تغییر آمده است:

- `DOMAttrModified` (توسط سافاری پشتیبانی نمیشود)
- `DOMAttributeNameChanged` (توسط فایرفاکس پشتیبانی نمیشود)
- `DOMCharacterDataModified`
- `DOMElementNameChanged` (توسط فایرفاکس پشتیبانی نمیشود)
- `DOMNodeInserted`
- `DOMNodeInsertedIntoDocument`
- `DOMNodeRemoved`
- `DOMNodeRemovedFromDocument`
- `DOMSubtreeModified`

## مثالها

میتوانید یک شنونده برای رویدادهای تغییر با استفاده از {{DOMxRef("EventTarget.addEventListener()")}} به صورت زیر ثبت کنید:

```js
element.addEventListener("DOMNodeInserted", (event) => {
  // …
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMxRef("MutationObserver")}}