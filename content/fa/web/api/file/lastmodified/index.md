---
title: "File: lastModified property"
---

---
title: "File: lastModified property"
short-title: lastModified
slug: Web/API/File/lastModified
page-type: web-api-instance-property
browser-compat: api.File.lastModified
---

{{APIRef("File API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lastModified`** از رابط {{domxref("File")}} تاریخ آخرین تغییر فایل را به‌صورت تعداد میلی‌ثانیه از مبدأ Unix (نیمه‌شب اول ژانویه ۱۹۷۰) ارائه می‌دهد. فایل‌هایی که تاریخ آخرین تغییر مشخصی ندارند، تاریخ فعلی را برمی‌گردانند.

## مقدار

عددی که تعداد میلی‌ثانیه از مبدأ Unix را نشان می‌دهد.

## مثال‌ها

مثال زیر فایل‌هایی را که انتخاب می‌کنید حلقه می‌زند و مشخص می‌کند که آیا هر فایل در یک سال گذشته تغییر کرده است یا خیر.

### HTML

```html
<input type="file" id="file-picker" name="fileList" multiple />
<output id="output"></output>
```

```css hidden
output {
  display: block;
  white-space: pre-wrap;
}
```

### JavaScript

```js
const output = document.getElementById("output");
const filePicker = document.getElementById("file-picker");

filePicker.addEventListener("change", (event) => {
  const files = event.target.files;
  const now = new Date();
  output.textContent = "";

  for (const file of files) {
    const date = new Date(file.lastModified);
    // true اگر فایل بیش از 1 سال تغییر نکرده باشد
    const stale = now.getTime() - file.lastModified > 31_536_000_000;
    output.textContent += `${file.name} ${
      stale ? "کهنه" : "تازه"
    } است (${date}).\n`;
  }
});
```

### نتیجه

{{EmbedLiveSample('Examples')}}

### فایل‌های ساخته‌شده به‌صورت پویا

اگر یک فایل به‌صورت پویا ساخته شود، زمان آخرین تغییر را می‌توان در تابع سازنده {{domxref("File.File()", "File()")}} مشخص کرد. اگر این زمان ذکر نشود، `lastModified` زمان فعلی را از {{jsxref("Date.now()")}} در لحظه ایجاد شیء `File` به ارث می‌برد.

```js
const fileWithDate = new File([], "file.bin", {
  lastModified: new Date(2017, 1, 1),
});
console.log(fileWithDate.lastModified); // 1485903600000 را برمی‌گرداند

const fileWithoutDate = new File([], "file.bin");
console.log(fileWithoutDate.lastModified); // زمان فعلی را برمی‌گرداند
```

## کاهش دقت زمان

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت‌برداری](/en-US/docs/Glossary/Fingerprinting)، دقت `someFile.lastModified` ممکن است بسته به تنظیمات مرورگر گرد شود. در Firefox، اولویت `privacy.reduceTimerPrecision` به‌طور پیش‌فرض فعال است و مقدار پیش‌فرض آن ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید، که در این صورت دقت ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` (هر کدام بزرگ‌تر باشد) خواهد بود.

برای مثال، با کاهش دقت زمان، نتیجه `someFile.lastModified` همیشه مضربی از ۲ یا مضربی از ۱۰۰ (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) با فعال بودن `privacy.resistFingerprinting` خواهد بود.

```js
// کاهش دقت زمان (2ms) در Firefox 60
someFile.lastModified;
// ممکن است:
// 1519211809934
// 1519211810362
// 1519211811670
// …

// کاهش دقت زمان با فعال بودن `privacy.resistFingerprinting`
someFile.lastModified;
// ممکن است:
// 1519129853500
// 1519129858900
// 1519129864400
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("File")}}