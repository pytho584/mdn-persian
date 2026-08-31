---
title: "Barcode Detection API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Barcode_Detection_API"
translated_by: "n8n + AI"
---

---
title: Barcode Detection API
slug: Web/API/Barcode_Detection_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.BarcodeDetector
---

{{securecontext_header}}{{DefaultAPISidebar("Barcode Detection API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

API شناسایی بارکد، بارکدهای خطی و دوبعدی را در تصاویر شناسایی می‌کند.

## مفاهیم و کاربرد

پشتیبانی از تشخیص بارکد در برنامه‌های وب، از طریق قالب‌های بارکد پشتیبانی‌شده، طیف وسیعی از موارد استفاده را فراهم می‌کند. کدهای QR می‌توانند برای پرداخت‌های آنلاین، پیمایش وب یا برقراری ارتباط در شبکه‌های اجتماعی استفاده شوند، کدهای آزتک می‌توانند برای اسکن کارت‌های پرواز استفاده شوند و برنامه‌های خرید می‌توانند از بارکدهای EAN یا UPC برای مقایسه قیمت کالاهای فیزیکی استفاده کنند.

تشخیص از طریق متد {{domxref('BarcodeDetector.detect()','detect()')}} انجام می‌شود که یک شیء تصویر دریافت می‌کند؛ این شیء می‌تواند یکی از این اشیاء باشد:
یک {{domxref("HTMLImageElement")}}،
یک {{domxref("SVGImageElement")}}،
یک {{domxref("HTMLVideoElement")}}،
یک {{domxref("HTMLCanvasElement")}}،
یک {{domxref("ImageBitmap")}}،
یک {{domxref("OffscreenCanvas")}}،
یک {{domxref("VideoFrame")}}،
یک {{domxref('Blob')}}،
یا یک {{domxref('ImageData')}}.
پارامترهای اختیاری می‌توانند به سازندهٔ {{domxref('BarcodeDetector')}} ارسال شوند تا راهنمایی‌هایی دربارهٔ اینکه کدام قالب‌های بارکد شناسایی شوند ارائه دهند.

### قالب‌های بارکد پشتیبانی‌شده

API شناسایی بارکد از قالب‌های بارکد زیر پشتیبانی می‌کند:

<table class="no-markdown">
  <thead>
    <tr>
      <th>قالب</th>
      <th>توضیحات</th>
      <th>تصویر</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>aztec</td>
      <td>
        یک ماتریس دوبعدی مربعی که از iso24778 پیروی می‌کند و در مرکز آن یک الگوی هدف مربعی وجود دارد، بنابراین شبیه یک هرم آزتک است. به ناحیه خالی اطراف نیازی ندارد.
      </td>
      <td>
        <img
          alt="A sample image of an Aztec barcode. A square with smaller black and white squares inside"
          src="aztec.gif"
        />
      </td>
    </tr>
    <tr>
      <td>code_128</td>
      <td>
        یک بارکد خطی (تک‌بعدی)، قابل رمزگشایی دوسویه و خودبررسی که از iso15417 پیروی می‌کند و قادر است هر ۱۲۸ نویسه {{Glossary("ASCII")}} را رمزگذاری کند (از این رو نامگذاری شده است).
      </td>
      <td>
        <img
          alt="An image of a code-128 barcode. A horizontal distribution of vertical black and white lines"
          src="code-128.gif"
        />
      </td>
    </tr>
    <tr>
      <td>code_39</td>
      <td>
        یک بارکد خطی (تک‌بعدی)، خودبررسی که از iso16388 پیروی می‌کند. این یک نوع بارکد گسسته با طول متغیر است.
      </td>
      <td>
        <img
          alt="An image of a code-39 barcode. A horizontal distribution of vertical black and white lines"
          src="code-39.png"
        />
      </td>
    </tr>
    <tr>
      <td>code_93</td>
      <td>
        یک نماد خطی پیوسته با طول متغیر که از bc5 پیروی می‌کند. تراکم اطلاعات بیشتری نسبت به Code 128 و Code 39 که از نظر ظاهری مشابه است ارائه می‌دهد. Code 93 عمدتاً توسط پست کانادا برای رمزگذاری اطلاعات تکمیلی تحویل استفاده می‌شود.
      </td>
      <td>
        <img
          alt="An image of a code 93 format barcode. A horizontal distribution of white and black horizontal lines"
          src="code-93.png"
        />
      </td>
    </tr>
    <tr>
      <td>codabar</td>
      <td>
        یک بارکد خطی که نویسه‌های 0-9، A-D و نمادهای - . $ / + را نمایش می‌دهد.
      </td>
      <td>
        <img
          alt="An image of a codabar format barcode. A horizontal distribution of black and white vertical lines"
          src="codabar.png"
        />
      </td>
    </tr>
    <tr>
      <td>data_matrix</td>
      <td>
        یک بارکد دوبعدی مستقل از جهت که از ماژول‌های سیاه و سفید تشکیل شده و در الگوی مربعی یا مستطیلی مطابق با iso16022 چیده شده است.
      </td>
      <td>
        <img
          alt="An example of a data matrix barcode. A square filled with smaller black and white squares"
          src="data-matrix.png"
        />
      </td>
    </tr>
    <tr>
      <td>ean_13</td>
      <td>
        یک بارکد خطی مبتنی بر استاندارد UPC-A که در iso15420 تعریف شده است.
      </td>
      <td>
        <img
          alt="An image of an EAN-13 format barcode. A horizontal distribution of white and black lines"
          src="ean-13.png"
        />
      </td>
    </tr>
    <tr>
      <td>ean_8</td>
      <td>یک بارکد خطی تعریف‌شده در iso15420 که از EAN-13 مشتق شده است.</td>
      <td>
        <img
          alt="An image of an EAN-8 format barcode. A horizontal distribution of vertical black and white lines"
          src="ean-8.png"
        />
      </td>
    </tr>
    <tr>
      <td>itf</td>
      <td>
        یک بارکد پیوسته، خودبررسی و قابل رمزگشایی دوسویه. همیشه ۱۴ رقم را رمزگذاری می‌کند.
      </td>
      <td>
        <img
          alt="An image of an ITF Barcode. A horizontal distribution of white and black lines"
          src="ift.png"
        />
      </td>
    </tr>
    <tr>
      <td>pdf417</td>
      <td>
        یک قالب نماد بارکد دوبعدی پیوسته با چندین ردیف و ستون. به صورت دوسویه قابل رمزگشایی است و از استاندارد iso15438 استفاده می‌کند.
      </td>
      <td>
        <img
          alt="An example of a pdf417 barcode format. A rectangle of smaller black and white squares"
          src="pdf417.png"
        />
      </td>
    </tr>
    <tr>
      <td>qr_code</td>
      <td>
        یک بارکد دوبعدی که از استاندارد iso18004 استفاده می‌کند. اطلاعات رمزگذاری‌شده می‌تواند متن، URL یا داده‌های دیگر باشد.
      </td>
      <td>
        <img
          alt="An example of a QR code. A square of smaller black and white squares"
          src="qr-code.png"
        />
      </td>
    </tr>
    <tr>
      <td>upc_a</td>
      <td>
        یکی از رایج‌ترین انواع بارکد خطی است و به طور گسترده در خرده‌فروشی در ایالات متحده استفاده می‌شود. در iso15420 تعریف شده است و ارقام را با نوارهایی از میله‌ها و فاصله‌ها نمایش می‌دهد، به طوری که هر رقم با الگوی منحصربه‌فردی از ۲ میله و ۲ فاصله با عرض متغیر مرتبط است. UPC-A می‌تواند ۱۲ رقم را رمزگذاری کند که به صورت یکتا به هر قلم تجاری اختصاص می‌یابد و از نظر فنی زیرمجموعه‌ای از EAN-13 است (کدهای UPC-A در EAN-13 با اولین نویسه که روی ۰ تنظیم شده است نمایش داده می‌شوند).
      </td>
      <td>
        <img
          alt="An image of a upc-a barcode. A rectangle of black and white vertical lines with numbers underneath"
          src="upc-a.png"
        />
      </td>
    </tr>
    <tr>
      <td>upc_e</td>
      <td>
        تغییری از UPC-A که در iso15420 تعریف شده است و صفرهای غیرضروری را برای بارکد فشرده‌تر حذف می‌کند.
      </td>
      <td>
        <img
          alt="An image of a upc-e barcode. A rectangle of black and white vertical lines"
          src="upc-e.png"
        />
      </td>
    </tr>
    <tr>
      <td>unknown</td>
      <td>
        این مقدار توسط پلتفرم استفاده می‌شود تا نشان دهد که نمی‌داند یا مشخص نمی‌کند کدام قالب بارکد در حال شناسایی یا پشتیبانی است.
      </td>
      <td></td>
    </tr>
  </tbody>
</table>

می‌توانید قالب‌های پشتیبانی‌شده توسط عامل کاربر را از طریق متد {{domxref('BarcodeDetector/getSupportedFormats_static','getSupportedFormats()')}} بررسی کنید.

## رابط‌ها

- {{domxref("BarcodeDetector")}} {{Experimental_Inline}}
  - : رابط `BarcodeDetector` در API شناسایی بارکد، امکان شناسایی بارکدهای خطی و دوبعدی را در تصاویر فراهم می‌کند.

## مثال‌ها

### ایجاد یک شناساگر

این مثال سازگاری مرورگر را بررسی می‌کند و یک شیء شناساگر بارکد جدید با قالب‌های پشتیبانی‌شدهٔ مشخص ایجاد می‌کند.

```js
// check compatibility
if (!("BarcodeDetector" in globalThis)) {
  console.log("Barcode Detector is not supported by this browser.");
} else {
  console.log("Barcode Detector supported!");

  // create new detector
  const barcodeDetector = new BarcodeDetector({
    formats: ["code_39", "codabar", "ean_13"],
  });
}
```

### دریافت قالب‌های پشتیبانی‌شده

مثال زیر متد `getSupportedFormats()` را فراخوانی می‌کند و نتایج را در کنسول ثبت می‌کند.

```js
// check supported types
BarcodeDetector.getSupportedFormats().then((supportedFormats) => {
  supportedFormats.forEach((format) => console.log(format));
});
```

### شناسایی بارکدها

این مثال از متد `detect()` برای شناسایی بارکدهای موجود در تصویر داده‌شده استفاده می‌کند. روی این بارکدها پیمایش می‌شود و داده‌های بارکد در کنسول ثبت می‌شوند.

```js
barcodeDetector
  .detect(imageEl)
  .then((barcodes) => {
    barcodes.forEach((barcode) => console.log(barcode.rawValue));
  })
  .catch((err) => {
    console.log(err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [barcodefaq.com: وب‌سایتی با اطلاعات درباره بارکدهای مختلف و نمونه‌هایی از انواع مختلف.](https://www.barcodefaq.com/)
- [Shape Detection API: یک تصویر ارزش هزار کلمه، چهره‌ها و بارکدها را دارد](https://developer.chrome.com/docs/capabilities/shape-detection#barcodedetector)