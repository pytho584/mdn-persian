```
---
title: "MediaTrackSupportedConstraints: groupId property"
short-title: groupId
slug: Web/API/MediaTrackSupportedConstraints/groupId
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.groupId_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`groupId`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است. این ویژگی در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و روی `true` تنظیم می‌شود) اگر و تنها اگر {{Glossary("user agent")}} (عامل کاربر) از محدودیت `groupId` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود؛ بنابراین مقدار این ویژگی هرگز `false` نخواهد بود.

برای دسترسی به دیکشنری محدودیت‌های پشتیبانی‌شده، کافی است `navigator.mediaDevices.getSupportedConstraints()` را فراخوانی کنید.

## مقدار

اگر عامل کاربر از محدودیت `groupId` پشتیبانی کند، این ویژگی در دیکشنری وجود دارد (و مقدار آن همیشه `true` است). در غیر این صورت، این ویژگی در دیکشنری محدودیت‌های پشتیبانی‌شده وجود نخواهد داشت و اگر تلاش کنید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

## Examples

```html hidden
<div id="result"></div>
```

```css hidden
#result {
  font:
    14px "Arial",
    sans-serif;
}
```

```js
const result = document.getElementById("result");
const supported = navigator.mediaDevices.getSupportedConstraints().groupId;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### Result

{{ EmbedLiveSample('Examples', 600, 80) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}
```