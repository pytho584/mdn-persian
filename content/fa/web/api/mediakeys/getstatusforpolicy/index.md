```markdown
---
title: "MediaKeys: getStatusForPolicy() method"
short-title: getStatusForPolicy()
slug: Web/API/MediaKeys/getStatusForPolicy
page-type: web-api-instance-method
browser-compat: api.MediaKeys.getStatusForPolicy
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد `getStatusForPolicy()` از رابط {{domxref("MediaKeys")}} برای بررسی اینکه آیا ماژول رمزگشایی محتوا (CDM) اجازه نمایش داده‌های رسانه‌ای رمزگذاری‌شده را با استفاده از کلیدها، بر اساس الزامات خط مشی مشخص‌شده، می‌دهد یا خیر، استفاده می‌شود.

این متد یک {{jsxref("Promise")}} برمی‌گرداند که با یک رشته (string) که وضعیت کلید را نسبت به تمام الزامات خط مشی مشخص‌شده نشان می‌دهد، حل می‌شود.
اگر مقدار به `"usable"` حل شود، محتوا قابل رمزگشایی و نمایش با کیفیت ایده‌آل است.
مقادیر دیگر دلایلی را نشان می‌دهند که چرا نمی‌توان از کلیدها برای نمایش محتوا استفاده کرد؛ در برخی موارد به گزینه‌های جایگزین اشاره دارند، مانند پخش محتوا با کیفیت پایین‌تر.

محدودیت‌های خط مشی در حال حاضر فقط شامل محدودیتی بر روی حداقل نسخه HDCP پشتیبانی‌شده است.

توجه داشته باشید که این متد یک "کلید فرضی" را در برابر محدودیت‌ها بررسی می‌کند.
برنامه نیازی ندارد ابتدا یک کلید واقعی ایجاد کند و یک مجوز واقعی را با استفاده از {{domxref("MediaKeySession")}} دریافت کند، و حتی {{domxref("MediaKeys")}} نیازی به اتصال به عناصر صوتی یا تصویری ندارد.

## Syntax

```js-nolint
getStatusForPolicy(policy)
```

### پارامترها

- `policy` {{optional_inline}}
  - : یک شیء با ویژگی‌های اختیاری زیر:
    - `minHdcpVersion` {{optional_inline}}
      - : یک رشته که نسخه معنایی (semantic version) حداقل نسخه HDCP را برای بررسی قابلیت استفاده نشان می‌دهد، مانند `1.0`، `1.4`، `2.2`، `2.3`.

> [!NOTE]
> حداقل یک محدودیت خط مشی باید مشخص شود، بنابراین `minHdcpVersion` فقط "از نظر فنی" اختیاری است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک رشته حل می‌شود و نشان می‌دهد آیا کلید با توجه به خط مشی مشخص‌شده قابل استفاده برای رمزگشایی است یا خیر.

رشته می‌تواند یکی از مقادیر زیر را داشته باشد:

- `usable`
  - : کلید در حال حاضر برای رمزگشایی قابل استفاده است.
- `expired`
  - : کلید دیگر به دلیل گذشتن زمان انقضا برای رمزگشایی قابل استفاده نیست.
- `released`
  - : کلید آزاد شده و دیگر در دسترس CDM نیست. با این حال اطلاعاتی در مورد کلید موجود است، مانند رکوردی از تخریب مجوز.
- `output-restricted`
  - : محدودیت‌های خروجی مرتبط با کلید بر اساس خط مشی مشخص‌شده وجود دارد. داده‌های رسانه‌ای رمزگشایی‌شده با این کلید ممکن است از نمایش مسدود شوند. وضعیت نشان می‌دهد که اتصال بین منبع و خروجی (مثلاً کامپیوتر شما و یک نمایشگر خارجی) مورد اعتماد نیست. این ممکن است نشان‌دهنده عدم تطابق نسخه HDCP بین منبع، دستگاه‌های میانی و خروجی باشد، یا اینکه دستگاه‌های اتصال میانی مانند کابل‌های HDMI یا تقسیم‌کننده‌های ویدیو آسیب دیده یا ناسازگار هستند. یک برنامه ممکن است انتخاب کند از نسخه HDCP بالاتری استفاده کند، یا محتوایی که به چنین نسخه بالایی نیاز ندارد. همچنین باید بررسی کنید که دستگاه‌ها و کابل‌های میانی از HDCP پشتیبانی می‌کنند، محکم متصل شده‌اند و آسیب ندیده‌اند.
- `output-downscaled`
  - : محدودیت‌های خروجی مرتبط با کلید بر اساس خط مشی مشخص‌شده وجود دارد، اما این محدودیت‌ها ممکن است در صورت پخش محتوا با کیفیت پایین‌تر کاهش یابند. اگر این مقدار برگردانده شود، یک برنامه ممکن است محتوا را با وضوح پایین‌تر پخش کند، یا می‌تواند از نسخه HDCP بالاتری استفاده کند، یا از محتوای دیگری که به چنین نسخه HDCP بالایی نیاز ندارد استفاده کند.
- `usable-in-future`
  - : کلید در آینده، پس از رسیدن زمان شروع آن، برای رمزگشایی قابل استفاده خواهد شد.
- `status-pending`
  - : وضعیت کلید هنوز مشخص نیست و در حال تعیین است.
- `internal-error`
  - : کلید در حال حاضر به دلیل خطایی در CDM برای رمزگشایی قابل استفاده نیست. برنامه نمی‌تواند برای مدیریت این حالت کاری انجام دهد.

### استثناها

- `TypeError`
  - : `policy` هیچ ویژگی تعریف‌شده‌ای (محدودیت‌های خط مشی) ندارد، یا یک کلید ویژگی معتبر نیست.

- `NotSupportedError`
  - : CDM نمی‌تواند وضعیت را برای برخی یا تمام محدودیت‌های خط مشی تعیین کند.

## مثال‌ها

### بررسی قابلیت استفاده کلیدها با محدودیت HDCP

این مثال بررسی می‌کند که آیا کلیدها برای رمزگشایی یک فرمت ویدیویی خاص در هنگام استفاده از حداقل نسخه HDCP `2.2` قابل استفاده هستند یا خیر.

> [!NOTE]
> وضعیت `output-restricted` زمانی که از نمایشگر خارجی استفاده می‌کنید می‌تواند ناشی از مشکلات ناسازگاری سخت‌افزاری HDCP باشد. اگر از لپ‌تاپ استفاده می‌کنید، ممکن است با قطع کردن نمایشگر خارجی بتوانید این مشکل را "رفع" کنید.

#### HTML

```html
<pre id="log"></pre>
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const config = [
  {
    videoCapabilities: [
      {
        contentType: 'video/mp4; codecs="avc1.640028"',
        encryptionScheme: "cenc",
        robustness: "SW_SECURE_DECODE", // Widevine L3
      },
    ],
  },
];

getMediaStatus(config);

async function getMediaStatus(config) {
  try {
    const mediaKeySystemAccess = await navigator.requestMediaKeySystemAccess(
      "com.widevine.alpha",
      config,
    );
    const mediaKeys = await mediaKeySystemAccess.createMediaKeys();
    const mediaStatus = await mediaKeys.getStatusForPolicy({
      minHdcpVersion: "2.2",
    });
    log(mediaStatus);

    // دریافت محتوا یا بازگشت به یک گزینه جایگزین اگر
    // کلیدها قابل استفاده نیستند
    if (mediaStatus === "usable") {
      console.log("HDCP 2.2 can be enforced.");
      // دریافت محتوای محافظت‌شده با وضوح بالا
    } else {
      log("HDCP 2.2 cannot be enforced");
      // بازگشت به محتوای دیگر، دریافت مجوز و غیره
    }
  } catch (error) {
    log(error);
  }
}
```

#### نتایج

{{EmbedLiveSample("Check if keys are usable with HDCP restriction")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaKeyStatusMap.get()")}}
```