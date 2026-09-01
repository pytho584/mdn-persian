---
title: "FileReader: result property"
short-title: result
slug: Web/API/FileReader/result
page-type: web-api-instance-property
browser-compat: api.FileReader.result
---

{{APIRef("File API")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`result`** در رابط {{domxref("FileReader")}} محتوای فایل را برمی‌گرداند. این خاصیت فقط پس از اتمام عملیات خواندن معتبر است و قالب داده‌ها به روشی بستگی دارد که برای شروع عملیات خواندن استفاده شده است.

## مقدار

یک رشته (string) یا {{jsxref("ArrayBuffer")}} مناسب بر اساس اینکه کدام یک از روش‌های خواندن برای شروع عملیات استفاده شده است. اگر خواندن هنوز کامل نشده یا ناموفق باشد، مقدار `null` است.

انواع نتیجه در زیر توضیح داده شده‌اند.

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">متد</th>
      <th scope="col">توضیح</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        {{domxref("FileReader/readAsArrayBuffer", "readAsArrayBuffer()")}}
      </td>
      <td>
        <code>result</code> یک {{jsxref("Global_Objects/ArrayBuffer", "ArrayBuffer")}}
        جاوااسکریپت حاوی داده‌های باینری است.
      </td>
    </tr>
    <tr>
      <td>
        {{domxref("FileReader/readAsBinaryString", "readAsBinaryString()")}}
      </td>
      <td>
        <code>result</code> داده‌های باینری خام فایل را به صورت یک رشته
        شامل می‌شود.
      </td>
    </tr>
    <tr>
      <td>
        {{domxref("FileReader/readAsDataURL", "readAsDataURL()")}}
      </td>
      <td>
        <code>result</code> رشته‌ای با URL از نوع <code>data:</code>
        است که داده‌های فایل را نمایش می‌دهد.
      </td>
    </tr>
    <tr>
      <td>
        {{domxref("FileReader/readAsText", "readAsText()")}}
      </td>
      <td><code>result</code> متن در قالب یک رشته است.</td>
    </tr>
  </tbody>
</table>

## مثال‌ها

این مثال تابع `reader()` را ارائه می‌دهد که یک فایل را از یک [ورودی فایل](/en-US/docs/Web/HTML/Reference/Elements/input/file) می‌خواند. این تابع با ایجاد یک شیء {{domxref("FileReader")}} و افزودن یک شنونده برای رویدادهای {{domxref("FileReader/load_event", "load")}} کار می‌کند، به طوری که وقتی فایل خوانده می‌شود، `result` به دست آمده و به تابع بازخواست (callback) که به `reader()` ارائه شده ارسال می‌شود.

محتوای فایل به عنوان داده متنی خام پردازش می‌شود.

```js
// با توجه به این HTMLInputElement از نوع type="file":
// <input id="image" type="file" accept="image/*">

function reader(file, callback) {
  const fr = new FileReader();
  fr.onload = () => callback(null, fr.result);
  fr.onerror = (err) => callback(err);
  fr.readAsDataURL(file);
}

document.querySelector("#image").addEventListener("change", (evt) => {
  // اگر فایلی وجود نداشته باشد، کاری انجام نده.
  if (!evt.target.files) {
    return;
  }
  reader(evt.target.files[0], (err, res) => {
    console.log(res); // نتیجه رشته‌ای Base64 از نوع `data:image/...`
  });
});
```

با توجه به ماهیت ناهمگام {{domxref("FileReader")}}، می‌توانید از رویکرد مبتنی بر Promise استفاده کنید. در اینجا مثالی برای یک [ورودی فایل](/en-US/docs/Web/HTML/Reference/Elements/input/file) با ویژگی `multiple` آورده شده است که یک {{jsxref("Promise")}} برمی‌گرداند.

```js
// با توجه به این HTMLInputElement:
// <input id="images" type="file" accept="image/*" multiple>

const reader = (file) =>
  new Promise((resolve, reject) => {
    const fr = new FileReader();
    fr.onload = () => resolve(fr);
    fr.onerror = (err) => reject(err);
    fr.readAsDataURL(file);
  });

async function logImagesData(fileList) {
  let fileResults = [];
  const frPromises = fileList.map(reader);

  try {
    fileResults = await Promise.all(frPromises);
  } catch (err) {
    // در این مورد خاص، ممکن است Promise.all() ترجیح داده شود
    // زیرا تغییر یک FileList به زیرمجموعه‌ای از فایل‌های انتخاب شده
    // توسط کاربر کار ساده‌ای نیست. بنابراین، اجازه دهید کل عملیات
    // را متوقف کنیم.
    console.error(err);
    return;
  }

  fileResults.forEach((fr) => {
    console.log(fr.result); // نتیجه رشته‌ای Base64 از نوع `data:image/...`
  });
}

// مدیریت رویداد HTMLInputElement از نوع type="file":
document.querySelector("#images").addEventListener("change", (evt) => {
  // اگر فایلی وجود نداشته باشد، کاری انجام نده.
  if (!evt.target.files) {
    return;
  }
  logImagesData([...evt.target.files]);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("FileReader")}}