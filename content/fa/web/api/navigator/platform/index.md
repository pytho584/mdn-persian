---
title: "Navigator: platform property"
---

---
title: "Navigator: platform property"
short-title: platform
slug: Web/API/Navigator/platform
page-type: web-api-instance-property
browser-compat: api.Navigator.platform
---

{{APIRef("HTML DOM")}}

ویژگی **`platform`** که یک ویژگی فقط‌خواندنیِ رابط {{domxref("Navigator")}} است، رشته‌ای را برمی‌گرداند که پلتفرمِ در حال اجرای مرورگر کاربر را شناسایی می‌کند.

## مقدار

رشته‌ای که یک پلتفرم را نشان می‌دهد، برای مثال:

- `"MacIntel"`
- `"Win32"`
- `"Linux x86_64"`

> [!NOTE]
> در ویندوز، مرورگرهای مدرن حتی اگر روی نسخهٔ ۶۴ بیتی ویندوز اجرا شوند، مقدار `"Win32"` را برمی‌گردانند.

## توضیحات

ویژگی `platform` پلتفرم/سیستم‌عاملی را که مرورگر روی آن اجرا می‌شود، نشان می‌دهد.

از نظر تئوری، این اطلاعات برای تشخیص مرورگر و ارائهٔ کدی برای دور زدن باگ‌های خاص مرورگر یا نبودِ پشتیبانی از قابلیت‌ها مفید است. با این حال، این روش **غیرقابل اعتماد** است و **توصیه نمی‌شود**؛ به دلایلی که در [کاهش User-Agent](/en-US/docs/Web/HTTP/Guides/User-agent_reduction) و [تشخیص مرورگر با استفاده از user agent](/en-US/docs/Web/HTTP/Guides/Browser_detection_using_the_user_agent) آمده است.

[تشخیص قابلیت (Feature detection)](/en-US/docs/Learn_web_development/Extensions/Testing/Feature_detection) راهبرد بسیار قابل اعتمادتری است.

## مثال‌ها

### تعیین کلید اصلاح‌گر (modifier key) برای پلتفرم کاربر

یک مورد استفاده که `navigator.platform` می‌تواند مفید باشد، زمانی است که نیاز دارید به کاربران راهنمایی نشان دهید که آیا کلید اصلاح‌گر میانبرهای صفحه‌کلید، کلید فرمان `⌘` (در سیستم‌های اپل) است یا کلید کنترل `Ctrl` (در سیستم‌های غیر اپل):

```js
const modifierKeyPrefix =
  navigator.platform.startsWith("Mac") || navigator.platform === "iPhone"
    ? "⌘" // command key
    : "Ctrl"; // control key
```

این کد بررسی می‌کند که آیا `navigator.platform` با `"Mac"` شروع می‌شود یا دقیقاً با `"iPhone"` برابر است، و سپس بر اساس درست بودن هر یک از این دو شرط، متغیر `modifierKeyPrefix` را به کلید اصلاح‌گر مناسبِ پلتفرم کاربر تنظیم می‌کند. این کار می‌تواند در رابط کاربری وب برای نشان دادنِ این که کاربران هنگام استفاده از میانبرهای صفحه‌کلید به کدام کلید اصلاح‌گر نیاز دارند، به کار رود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Navigator.userAgent")}}
- {{HTTPHeader("User-agent")}} هدر HTTP