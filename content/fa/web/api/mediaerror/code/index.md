---
title: "MediaError: code property"
---

---
title: "MediaError: code property"
short-title: code
slug: Web/API/MediaError/code
page-type: web-api-instance-property
browser-compat: api.MediaError.code
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`MediaError.code`** یک مقدار عددی برمی‌گرداند که نوع خطای رخ‌داده در یک عنصر رسانه‌ای را نشان می‌دهد. برای دریافت یک رشته متنی حاوی اطلاعات تشخیصی خاص، {{domxref("MediaError.message")}} را ببینید.

## مقدار

یک مقدار عددی که نوع کلی خطای رخ‌داده را نشان می‌دهد. مقادیر احتمالی در بخش [ثابت‌های کد خطای رسانه](#media_error_code_constants) در زیر توضیح داده شده‌اند.

### ثابت‌های کد خطای رسانه

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">نام</th>
      <th scope="col">مقدار</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>MEDIA_ERR_ABORTED</code></td>
      <td><code>1</code></td>
      <td>
        دریافت منبع مرتبط به درخواست کاربر لغو شده است.
      </td>
    </tr>
    <tr>
      <td><code>MEDIA_ERR_NETWORK</code></td>
      <td><code>2</code></td>
      <td>
        نوعی خطای شبکه رخ داده است که با وجود در دسترس بودن قبلی، از دریافت موفق رسانه جلوگیری کرده است.
      </td>
    </tr>
    <tr>
      <td><code>MEDIA_ERR_DECODE</code></td>
      <td><code>3</code></td>
      <td>
        با وجود اینکه قبلاً قابل استفاده تشخیص داده شده بود، هنگام تلاش برای رمزگشایی منبع رسانه خطایی رخ داد و در نتیجه خطا ایجاد شد.
      </td>
    </tr>
    <tr>
      <td><code>MEDIA_ERR_SRC_NOT_SUPPORTED</code></td>
      <td><code>4</code></td>
      <td>
        منبع مرتبط یا شیء ارائه‌دهنده رسانه (مانند {{domxref("MediaStream")}}) نامناسب تشخیص داده شده است.
      </td>
    </tr>
  </tbody>
</table>

## مثال‌ها

این مثال یک عنصر {{HTMLElement("video")}} ایجاد می‌کند، یک مدیریت خطا برای آن تنظیم می‌کند و سپس ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/video#src) عنصر را روی منبع ویدیویی که باید در عنصر نمایش داده شود قرار می‌دهد. مدیریت خطا یک پیام خروجی می‌دهد:

```js
const obj = document.createElement("video");
obj.onerror = () => {
  console.error(`Error with media: ${obj.error.code}`);
};
obj.src = "https://example.com/blahblah.mp4";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaError")}}: رابطی که برای تعریف ویژگی `MediaError.code` استفاده می‌شود.