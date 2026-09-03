```yaml
---
title: "Navigator: canShare() method"
short-title: canShare()
slug: Web/API/Navigator/canShare
page-type: web-api-instance-method
browser-compat: api.Navigator.canShare
---

{{APIRef("Web Share API")}}{{securecontext_header}}

متد **`canShare()`** از رابط {{domxref("Navigator")}} اگر فراخوانی معادل {{domxref("navigator.share()")}} موفقیت‌آمیز باشد، مقدار `true` را برمی‌گرداند.

این متد اگر داده‌ها قابل _اعتبارسنجی_ نباشند، مقدار `false` برمی‌گرداند. دلایل نامعتبر بودن داده‌ها عبارتند از:

- پارامتر `data` حذف شده باشد یا فقط شامل ویژگی‌هایی با مقادیر ناشناخته باشد. توجه داشته باشید که هر ویژگی‌ای که توسط عامل کاربر (user agent) شناسایی نشود، نادیده گرفته می‌شود.
- یک URL بد فرمت باشد.
- فایل‌هایی مشخص شده باشند اما پیاده‌سازی از اشتراک‌گذاری فایل پشتیبانی نکند.
- اشتراک‌گذاری داده‌های مشخص شده توسط عامل کاربر «اشتراک‌گذاری خصمانه» تلقی شود.

[Web Share API](/en-US/docs/Web/API/Web_Share_API) توسط خط مشی مجوز [web-share](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/web-share) کنترل می‌شود.
متد `canShare()` اگر مجوز پشتیبانی شود اما اعطا نشده باشد، مقدار `false` برمی‌گرداند.

## نحو (Syntax)

```js-nolint
canShare()
canShare(data)
```

### پارامترها

- `data` {{optional_inline}}
  - : یک شیء که داده‌های اشتراک‌گذاری را برای آزمایش تعریف می‌کند.
    معمولاً یک شیء با همان ویژگی‌ها به {{domxref("navigator.share()")}} ارسال می‌شود اگر این فراخوانی `true` برگرداند.

    ویژگی‌هایی که برای عامل کاربر ناشناخته هستند نادیده گرفته می‌شوند؛ داده‌های اشتراک‌گذاری فقط بر اساس ویژگی‌هایی که عامل کاربر درک می‌کند ارزیابی می‌شوند.
    همه ویژگی‌ها اختیاری هستند اما حداقل باید یک ویژگی داده شناخته شده مشخص شود در غیر این صورت متد `false` برمی‌گرداند.

    مقادیر ممکن عبارتند از:
    - `url` {{optional_inline}}
      - : یک رشته که یک URL را برای اشتراک‌گذاری نشان می‌دهد.
    - `text` {{optional_inline}}
      - : یک رشته که متنی را برای اشتراک‌گذاری نشان می‌دهد.
    - `title` {{optional_inline}}
      - : یک رشته که عنوانی را برای اشتراک‌گذاری نشان می‌دهد.
    - `files` {{optional_inline}}
      - : آرایه‌ای از اشیاء {{domxref("File")}} که فایل‌هایی را برای اشتراک‌گذاری نشان می‌دهد.

### مقدار بازگشتی

اگر `data` مشخص شده بتواند با {{domxref("Navigator.share()")}} به اشتراک گذاشته شود `true` را برمی‌گرداند، در غیر این صورت `false`.

## مثال‌ها

### ارسال URL MDN

این مثال از `navigator.canShare()` برای بررسی اینکه آیا `navigator.share()` می‌تواند داده‌های مشخص شده را به اشتراک بگذارد استفاده می‌کند.

#### HTML

HTML فقط یک پاراگراف برای نمایش نتیجه آزمایش ایجاد می‌کند.

```html
<p class="result"></p>
```

#### JavaScript

```js
let shareData = {
  title: "MDN",
  text: "Learn web development on MDN!",
  url: "https://developer.mozilla.org",
};

const resultPara = document.querySelector(".result");

if (!navigator.canShare) {
  resultPara.textContent = "navigator.canShare() not supported.";
} else if (navigator.canShare(shareData)) {
  resultPara.textContent =
    "navigator.canShare() supported. We can use navigator.share() to send the data.";
} else {
  resultPara.textContent = "Specified data cannot be shared.";
}
```

#### نتیجه

کادر زیر باید نشان دهد که آیا `navigator.canShare()` در این مرورگر پشتیبانی می‌شود یا خیر، و اگر بله، آیا می‌توانیم از `navigator.share()` برای اشتراک‌گذاری داده‌های مشخص شده استفاده کنیم:

{{EmbedLiveSample('Sending_the_MDN_URL')}}

### مثال بررسی ویژگی

این متد ویژگی (feature) را آزمایش می‌کند که آیا یک ویژگی داده خاص معتبر و قابل اشتراک‌گذاری است یا خیر.
اگر با یک ویژگی داده `data` تکی استفاده شود، تنها در صورتی `true` برمی‌گرداند که آن ویژگی معتبر و در پلتفرم قابل اشتراک‌گذاری باشد.

کد زیر نحوه تأیید پشتیبانی از یک ویژگی داده را نشان می‌دهد.

```js
// ویژگی‌ای که ممکن است پشتیبانی نشود
let testShare = { someNewProperty: "Data to share" };

// داده‌های پیچیده که از کلید جدید استفاده می‌کنند
const shareData = {
  title: "MDN",
  text: "Learn web development on MDN!",
  url: "https://developer.mozilla.org",
  someNewProperty: "Data to share",
};

// آزمایش معتبر و پشتیبانی‌شده بودن کلید قبل از اشتراک‌گذاری
if (navigator.canShare(testShare)) {
  // از navigator.share() برای اشتراک‌گذاری 'shareData' استفاده کنید
} else {
  // موردی که ویژگی داده جدید قابل اشتراک‌گذاری نیست را مدیریت کنید
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("navigator.share()")}}
```