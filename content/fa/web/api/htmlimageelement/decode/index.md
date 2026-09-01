---
title: "HTMLImageElement: decode() method"
short-title: decode()
slug: Web/API/HTMLImageElement/decode
page-type: web-api-instance-method
browser-compat: api.HTMLImageElement.decode
---

{{APIRef("HTML DOM")}}

متد **`decode()`** از رابط {{domxref("HTMLImageElement")}} یک {{jsxref("Promise")}} برمی‌گرداند که پس از رمزگشایی تصویر و آماده بودن آن برای افزودن به DOM، حل می‌شود.

از این متد می‌توان برای شروع بارگذاری تصویر قبل از الصاق آن به یک عنصر در DOM (یا افزودن آن به عنوان یک عنصر جدید به DOM) استفاده کرد، به طوری که تصویر بلافاصله پس از افزوده شدن به DOM قابل رندر شدن باشد. این کار به نوبه خود از تأخیر در رندر فریم بعدی پس از افزودن تصویر به DOM که در اثر بارگذاری تصویر رخ می‌دهد، جلوگیری می‌کند.

## نحو

```js-nolint
decode()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که پس از آماده شدن داده‌های تصویر برای استفاده، با مقدار `undefined` fulfillment می‌شود.

### استثناها

- `EncodingError` {{domxref("DOMException")}}
  - : در حین رمزگشایی تصویر خطایی رخ داده است. این اتفاق می‌تواند در موارد زیر رخ دهد:
    - درخواست با شکست مواجه شود
    - درخواست تصویر پس از فراخوانی `decode()` تغییر کند (مثلاً با تغییر `src` آن)
    - داده‌های تصویر خراب باشند

## مثال‌ها

### استفاده پایه

مثال زیر نحوه استفاده از متد `decode()` را برای کنترل زمان افزودن تصویر به DOM نشان می‌دهد.

```js
const img = new Image();
img.src = "nebula.jpg";
img
  .decode()
  .then(() => {
    document.body.appendChild(img);
  })
  .catch((encodingError) => {
    // با خطا کاری انجام دهید.
  });
```

> [!NOTE]
> بدون یک متد بازگرداننده {{jsxref('Promise')}}، شما تصویر را در یک مدیریت‌کننده رویداد {{domxref("Window/load_event", "load")}} به DOM اضافه می‌کردید و خطا را در مدیریت‌کننده رویداد {{domxref("HTMLElement/error_event", "error")}} مدیریت می‌کردید.

### جلوگیری از تصاویر خالی

در مثال زیر، احتمالاً یک تصویر خالی در صفحه نمایش داده می‌شود زیرا تصویر در حال دانلود است:

```js
const img = new Image();
img.src = "img/logo.png";
document.body.appendChild(img);
```

استفاده از `decode()` باعث می‌شود که درج تصویر در DOM تا زمانی که کاملاً دانلود و رمزگشایی نشده، به تأخیر بیفتد و در نتیجه از مشکل تصویر خالی جلوگیری شود:

```js
async function getImage() {
  const img = new Image();
  img.src = "img/logo.png";
  await img.decode();
  document.body.appendChild(img);
  const p = document.createElement("p");
  p.textContent = "تصویر کاملاً بارگذاری شد!";
  document.body.appendChild(p);
}
```

این کار به ویژه زمانی مفید است که به صورت پویا یک تصویر موجود را با یک تصویر جدید جایگزین می‌کنید، و همچنین از نگه داشته شدن paint‌های نامرتبط خارج از این کد در حین رمزگشایی تصویر جلوگیری می‌کند. به عنوان مثال، در یک آلبوم عکس آنلاین، می‌توانید ابتدا یک تصویر بندانگشتی با وضوح پایین نمایش دهید و سپس آن تصویر را با تصویر با وضوح کامل جایگزین کنید، با نمونه‌سازی یک {{domxref("HTMLImageElement")}} جدید، تنظیم منبع آن بر روی URL تصویر با وضوح کامل، و سپس استفاده از `decode()` برای دریافت یک promise که پس از آماده شدن تصویر با وضوح کامل برای استفاده، حل می‌شود. در آن زمان، می‌توانید تصویر با وضوح پایین را با تصویر با وضوح کامل که اکنون در دسترس است جایگزین کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ویژگی decoding تصویر واقعاً چه کاری انجام می‌دهد؟](https://www.tunetheweb.com/blog/what-does-the-image-decoding-attribute-actually-do/) در tunetheweb.com (2023)
- ویژگی {{domxref("HTMLImageElement.decoding")}}