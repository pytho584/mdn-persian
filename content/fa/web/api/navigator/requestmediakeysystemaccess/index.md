---
title: "Navigator: requestMediaKeySystemAccess() method"
short-title: requestMediaKeySystemAccess()
slug: Web/API/Navigator/requestMediaKeySystemAccess
page-type: web-api-instance-method
browser-compat: api.Navigator.requestMediaKeySystemAccess
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد **`requestMediaKeySystemAccess()`** از رابط {{domxref("Navigator")}} یک {{jsxref('Promise')}} برمی‌گرداند که یک شیء {{domxref('MediaKeySystemAccess')}} را تحویل می‌دهد. از این شیء می‌توان برای دسترسی به یک سیستم کلید رسانه‌ای خاص استفاده کرد و به نوبه خود برای ایجاد کلیدهای رمزگشایی جریان رسانه‌ای به کار می‌رود.

این متد بخشی از [API افزونه‌های رسانه‌ای رمزگذاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) است که پشتیبانی از رسانه‌های رمزگذاری‌شده و ویدیوی محافظت‌شده با DRM را به وب می‌آورد.

این متد ممکن است اثرات قابل مشاهده برای کاربر داشته باشد، مانند درخواست مجوز برای دسترسی به یک یا چند منبع سیستم. هنگام تصمیم‌گیری درباره زمان فراخوانی `requestMediaKeySystemAccess()` این نکته را در نظر بگیرید؛ شما نمی‌خواهید این درخواست‌ها در زمان‌های نامناسب رخ دهند. به عنوان یک قاعده کلی، این تابع فقط زمانی باید فراخوانی شود که نزدیک به زمان ایجاد و استفاده از یک شیء {{domxref("MediaKeys")}} از طریق فراخوانی متد {{domxref("MediaKeySystemAccess.createMediaKeys", "createMediaKeys()")}} شیء {{domxref("MediaKeySystemAccess")}} برگشتی باشیم.

## Syntax

```js-nolint
requestMediaKeySystemAccess(keySystem, supportedConfigurations)
```

### Parameters

- `keySystem`
  - : رشته‌ای که سیستم کلید را شناسایی می‌کند.
    به عنوان مثال `com.example.some-system` یا `org.w3.clearkey`.
- `supportedConfigurations`
  - : یک {{jsxref('Array')}} غیر خالی از اشیایی که با شیء برگشتی از {{domxref("MediaKeySystemAccess.getConfiguration")}} مطابقت دارند.
    اولین عنصری که پیکربندی قابل قبولی داشته باشد استفاده خواهد شد.

    هر شیء ممکن است ویژگی‌های زیر را داشته باشد:

    > [!NOTE]
    > یا `videoCapabilities` یا `audioCapabilities` ممکن است خالی باشد، اما هر دو نه!
    - `label` {{optional_inline}}
      - : یک برچسب اختیاری برای پیکربندی که پیش‌فرض آن `""` است.
        این برچسب برای پیکربندی‌هایی که با استفاده از {{domxref("MediaKeySystemAccess.getConfiguration")}} واکشی می‌شوند حفظ می‌شود.
    - `initDataTypes`
      - : آرایه‌ای از رشته‌ها که نام نوع داده را برای فرمت‌های داده مقداردهی اولیه پشتیبانی‌شده نشان می‌دهد (پیش‌فرض یک آرایه خالی است).
        این نام‌ها نام‌هایی مانند `"cenc"`، `"keyids"` و `"webm"` هستند که در [رجیستری فرمت داده مقداردهی اولیه افزونه‌های رسانه‌ای رمزگذاری‌شده](https://w3c.github.io/encrypted-media/format-registry/initdata/) تعریف شده‌اند.
    - `audioCapabilities`
      - : آرایه‌ای از قابلیت‌های صوتی پشتیبانی‌شده.
        اگر آرایه خالی باشد، نوع محتوا از قابلیت‌های صوتی پشتیبانی نمی‌کند.

        هر شیء در آرایه ویژگی‌های زیر را دارد:
        - `contentType`
          - : رشته‌ای که نوع MIME رسانه منبع رسانه‌ای را نشان می‌دهد، مانند `"audio/mp4;codecs=\"mp4a.40.2\""`.
            توجه داشته باشید که رشته خالی نامعتبر است و اگر تعریف نوع MIME شامل پارامترهایی مانند `codecs` باشد، اینها نیز باید لحاظ شوند.
        - `encryptionScheme`
          - : طرح رمزگذاری مرتبط با نوع محتوا، مانند `cenc`، `cbcs`، `cbcs-1-9`.
            این مقدار باید توسط یک برنامه تنظیم شود (پیش‌فرض آن `null` است که نشان می‌دهد هر طرح رمزگذاری ممکن است استفاده شود).
        - `robustness`
          - : سطح استحکام مرتبط با نوع محتوا.
            رشته خالی نشان می‌دهد که هر توانایی برای رمزگشایی و دیکد کردن نوع محتوا قابل قبول است.

    - `videoCapabilities`
      - : آرایه‌ای از قابلیت‌های ویدیویی پشتیبانی‌شده.
        اشیاء موجود در آرایه همان شکل اشیاء موجود در `audioCapabilities` را دارند.

    - `distinctiveIdentifier`
      - : رشته‌ای که نشان می‌دهد آیا پیاده‌سازی ممکن است از «شناسه‌های متمایز» (یا شناسه‌های دائمی متمایز) برای هر عملیات مرتبط با هر شیء ایجاد شده از این پیکربندی استفاده کند یا خیر.
        مقادیر مجاز عبارتند از:
        - `required`
          - : شیء برگشتی باید از این ویژگی پشتیبانی کند.
        - `optional`
          - : شیء برگشتی ممکن است از این ویژگی پشتیبانی کند.
            این مقدار پیش‌فرض است.
        - `not-allowed`
          - : شیء برگشتی نباید از این ویژگی پشتیبانی کند یا از آن استفاده کند.

    - `persistentState`
      - : رشته‌ای که نشان می‌دهد آیا شیء برگشتی باید بتواند داده‌های نشست یا هر نوع وضعیت دیگری را ذخیره کند یا خیر.
        مقادیر همانند `distinctiveIdentifier` هستند و معنای یکسانی دارند: `required`، `optional` (پیش‌فرض)، `not-allowed`.
        وقتی حالت پایدار مجاز نیست، فقط نشست‌های «موقت» ممکن است ایجاد شوند.

    - `sessionTypes`
      - : آرایه‌ای از رشته‌ها که انواع نشست‌هایی که باید پشتیبانی شوند را نشان می‌دهد.
        مقادیر مجاز عبارتند از:
        - `temporary`
          - : نشستی که مجوز، کلید(ها) و رکورد یا داده‌های مرتبط با نشست در آن ذخیره نمی‌شوند.
            برنامه نیازی به مدیریت چنین فضای ذخیره‌سازی ندارد.
            پیاده‌سازی‌ها باید از این گزینه پشتیبانی کنند و این گزینه پیش‌فرض است.
        - `persistent-license`
          - : نشستی که مجوز (و احتمالاً داده‌های دیگر مرتبط با نشست) در آن ذخیره خواهد شد.
            رکوردی از مجوز و کلیدهای مرتبط حتی اگر مجوز از بین برود باقی می‌ماند و گواهی می‌دهد که مجوز و کلید(های) موجود در آن دیگر توسط کلاینت قابل استفاده نیستند.

### Return value

یک {{jsxref('Promise')}} که با یک شیء {{domxref('MediaKeySystemAccess')}} تکمیل می‌شود و پیکربندی سیستم کلید رسانه‌ای توصیف‌شده توسط `keySystem` و `supportedConfigurations` را نشان می‌دهد.

### Exceptions

در صورت بروز خطا، {{jsxref('Promise')}} برگشتی با یک {{domxref('DOMException')}} رد می‌شود که نام آن نشان می‌دهد چه نوع خطایی رخ داده است.

- `NotSupportedError` {{domxref("DOMException")}}
  - : یا `keySystem` مشخص‌شده توسط پلتفرم یا مرورگر پشتیبانی نمی‌شود، یا هیچ‌یک از پیکربندی‌های مشخص‌شده توسط `supportedConfigurations` قابل قبول نیستند (مثلاً اگر هیچ‌یک از `codec`های مشخص‌شده در `contentType` در دسترس نباشند).
- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [`Permissions-Policy: encrypted-media`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/encrypted-media) مسدود شده است.
- {{jsxref("TypeError")}}
  - : یا `keySystem` یک رشته خالی است یا آرایه `supportedConfigurations` خالی است.

## Examples

مثال زیر نشان می‌دهد که چگونه ممکن است از `requestMediaKeySystemAccess()` استفاده کنید، با مشخص کردن یک سیستم کلید و پیکربندی.

```js
const clearKeyOptions = [
  {
    initDataTypes: ["keyids", "webm"],
    audioCapabilities: [
      { contentType: 'audio/webm; codecs="opus"' },
      { contentType: 'audio/webm; codecs="vorbis"' },
    ],
    videoCapabilities: [
      { contentType: 'video/webm; codecs="vp9"' },
      { contentType: 'video/webm; codecs="vp8"' },
    ],
  },
];

navigator
  .requestMediaKeySystemAccess("org.w3.clearkey", clearKeyOptions)
  .then((keySystemAccess) => {
    /* use the access to get create keys */
  });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Encrypted Media Extensions API](/en-US/docs/Web/API/Encrypted_Media_Extensions_API)
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- {{domxref("MediaCapabilities.decodingInfo()")}}