---
title: "MediaKeys"
---

---
title: MediaKeys
slug: Web/API/MediaKeys
page-type: web-api-interface
browser-compat: api.MediaKeys
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

رابطهٔ **`MediaKeys`** در [API افزونههای رسانهٔ رمزنگاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) مجموعه‌ای از کلیدها را نشان می‌دهد که یک {{domxref("HTMLMediaElement")}} مرتبط می‌تواند برای رمزگشایی داده‌های رسانه‌ای در حین پخش از آن استفاده کند.

## ویژگی‌های نمونه

هیچ‌کدام.

## روش‌های نمونه

- {{domxref("MediaKeys.createSession()")}}
  - : یک شیء جدید {{domxref("MediaKeySession")}} برمی‌گرداند که زمینه‌ای برای تبادل پیام با ماژول رمزگشایی محتوا (CDM) را نشان می‌دهد.
- {{domxref("MediaKeys.getStatusForPolicy()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به یک رشتهٔ وضعیت resolve می‌شود و نشان می‌دهد که آیا CDM بر اساس الزامات خط‌مشی مشخص‌شده، نمایش داده‌های رسانه‌ای رمزنگاری‌شده با استفاده از کلیدها را مجاز می‌داند یا خیر.
- {{domxref("MediaKeys.setServerCertificate()")}}
  - : یک {{jsxref("Promise")}} به گواهی سرور برمی‌گرداند که برای رمزنگاری پیام‌ها به سرور مجوز استفاده می‌شود.

## مثال‌ها

### بررسی قابل‌استفاده بودن کلیدها با محدودیت HDCP

این مثال نشان می‌دهد که چگونه می‌توان از `getStatusForPolicy()` برای بررسی اینکه آیا کلیدها می‌توانند یک فرمت ویدیویی خاص را در محیطی که حداقل نسخهٔ HDCP آن `2.2` است رمزگشایی کنند، استفاده کرد.
برای اطلاعات بیشتر، مستندات [روش MediaKeys: getStatusForPolicy()](/en-US/docs/Web/API/MediaKeys/getStatusForPolicy) را ببینید.

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

    // دریافت محتوا یا بازگشت به گزینهٔ جایگزین اگر
    // کلیدها قابل استفاده نیستند
    if (mediaStatus === "usable") {
      console.log("HDCP 2.2 can be enforced.");
      // دریافت محتوای محافظت‌شده با کیفیت بالا
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

## سازگاری مرورگر

{{Compat}}