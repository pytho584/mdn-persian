---
title: "CSSStyleDeclaration: getPropertyValue() method"
---

---
title: "CSSStyleDeclaration: getPropertyValue() method"
short-title: getPropertyValue()
slug: Web/API/CSSStyleDeclaration/getPropertyValue
page-type: web-api-instance-method
browser-compat: api.CSSStyleDeclaration.getPropertyValue
---

{{ APIRef("CSSOM") }}

متد **CSSStyleDeclaration.getPropertyValue()** رشته‌ای شامل مقدار یک ویژگی CSS مشخص را برمی‌گرداند.

## Syntax

```js-nolint
getPropertyValue(property)
```

### Parameters

- `property`
  - : رشته‌ای است که نام ویژگی مورد بررسی (به صورت hyphen case) را نشان می‌دهد.

### Return value

رشته‌ای شامل مقدار ویژگی. اگر تنظیم نشده باشد، رشته خالی بازگردانده می‌شود.

مقدار ویژگی به‌صورت پویا محاسبه می‌شود، نه مقداری که در ابتدا در اعلان (declaration) ذکر شده بود. سریال‌سازی به شکل زیر انجام می‌شود:

- اگر `property` یک ویژگی کوتاه‌نویس (shorthand property) باشد، همه ویژگی‌های بلندنویس (longhand properties) متناظر با آن در نظر گرفته می‌شوند. توجه داشته باشید که ویژگی‌های کوتاه‌نویسی که در برگه سبک اصلی مشخص شده بودند، هنگام تجزیه (parse) از قبل به ویژگی‌های بلندنویس بسط داده شده‌اند. اگر دست‌کم یکی از آن ویژگی‌های بلندنویس اعلام‌نشده باشد یا وضعیت `!important` آن‌ها با هم متفاوت باشد، نتیجه رشته خالی خواهد بود. در غیر این صورت، یک مقدار ویژگی که به همان فهرست مقادیر ویژگی‌های بلندنویس بسط می‌یابد بازگردانده می‌شود و این مقدار کوتاه‌نویس تا حد امکان مؤلفه‌های کمتری را شامل می‌شود و در صورت امکان به ترتیبی بازچینی می‌شود که با ترتیب متعارف در تعریف رسمی مطابقت داشته باشد. اگر هر یک از تبدیل‌های نحوی بالا سازگاری با عقب (backwards-compatible) را کاهش دهد، آن‌ها را انجام ندهید.
- در غیر این صورت، ویژگی بر اساس نوع داده‌اش سریال‌سازی می‌شود. هر نوع داده یک نمایش متعارف دارد؛ برای مثال، مقادیر `<color>` همیشه از `rgb(R, G, B)` یا `rgba(R, G, B, A)` استفاده می‌کنند.

در اصل، مقدار ویژگی _متعارف‌شده (canonicalized)_ می‌شود و این تضمین را ایجاد می‌کند که دو مقدار ویژگی با اثر رندر یکسان، حتی اگر به شکل متفاوتی اعلام شده باشند، به صورت رشته‌ای با هم برابر مقایسه شوند.

## Examples

کد جاوااسکریپت زیر مقدار ویژگی `margin` را در یک قانون انتخابگر CSS پرس‌وجو می‌کند:

```js
const declaration = document.styleSheets[0].cssRules[0].style;
const value = declaration.getPropertyValue("margin"); // "1px 2px"
```

رشته بازگردانده‌شده ممکن است با مقداری که در مشخصات استایل عنصر ذکر شده تفاوت داشته باشد. برای مثال این استایل‌دهی:

```css
p#blueish {
  color: hsl(250 90 50);
}
```

```js
const declaration = document.styleSheets[0].cssRules[0].style;
const value = declaration.getPropertyValue("color");
```

یک مقدار `rgb(51, 13, 242);` را تنظیم می‌کند. این موضوع هنگام مقایسه استایل‌ها به صورت رشته‌ای اهمیت دارد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}