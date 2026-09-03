---
title: "PublicKeyCredential: authenticatorAttachment property"
short-title: authenticatorAttachment
slug: Web/API/PublicKeyCredential/authenticatorAttachment
page-type: web-api-instance-property
browser-compat: api.PublicKeyCredential.authenticatorAttachment
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`authenticatorAttachment`** در رابط {{domxref("PublicKeyCredential")}} یک رشته است که دسته‌بندی کلی احرازگر (authenticator) مورد استفاده در فراخوانی متناظر {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} یا {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}} را نشان می‌دهد.

## مقدار

یک رشته که یکی از مقادیر زیر خواهد بود:

- `"platform"`
  - : احرازگر بخشی از دستگاهی است که WebAuthn روی آن اجرا می‌شود (به آن **احرازگر پلتفرمی** گفته می‌شود)؛ بنابراین WebAuthn با استفاده از یک کانال ارتباطی موجود برای آن پلتفرم، مانند یک API مختص آن پلتفرم، با آن ارتباط برقرار می‌کند. اعتبارنامه کلید عمومی متصل به یک احرازگر پلتفرمی **اعتبارنامه پلتفرمی** نامیده می‌شود.
- `"cross-platform"`
  - : احرازگر بخشی از دستگاهی نیست که WebAuthn روی آن اجرا می‌شود (به دلیل امکان جابه‌جایی بین دستگاه‌های مختلف، **احرازگر سیار** نیز نامیده می‌شود)؛ بنابراین WebAuthn با استفاده از یک پروتکل ارتباطی بین‌پلتفرمی مانند بلوتوث یا NFC با آن ارتباط برقرار می‌کند. اعتبارنامه کلید عمومی متصل به یک احرازگر سیار **اعتبارنامه سیار** نامیده می‌شود.

## مثال‌ها

```js
const options = {
  challenge: new Uint8Array(26) /* from the server */,
  rp: {
    name: "Example CORP",
    id: "login.example.com",
  },
  user: {
    id: new Uint8Array(26) /* To be changed for each user */,
    name: "canand@example.com",
    displayName: "Carina Anand",
  },
  pubKeyCredParams: [
    {
      type: "public-key",
      alg: -7,
    },
  ],
};

navigator.credentials
  .create({ publicKey: options })
  .then((pubKeyCredential) => {
    const attachment = pubKeyCredential.authenticatorAttachment;
    // Do something with authenticatorAttachment
  })
  .catch((err) => {
    // Deal with any error
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}