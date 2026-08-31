---
title: "AuthenticatorAttestationResponse"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAttestationResponse"
translated_by: "n8n + AI"
---

---
title: AuthenticatorAttestationResponse
slug: Web/API/AuthenticatorAttestationResponse
page-type: web-api-interface
browser-compat: api.AuthenticatorAttestationResponse
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

**`AuthenticatorAttestationResponse`** رابطهای از [Web Authentication API](/en-US/docs/Web/API/Web_Authentication_API) است که نتیجه ثبت اعتبارنامه WebAuthn میباشد. این رابط شامل اطلاعاتی درباره اعتبارنامه است که سرور برای انجام تأییدیههای WebAuthn به آن نیاز دارد، مانند شناسه اعتبارنامه و کلید عمومی.

یک نمونه از شیء `AuthenticatorAttestationResponse` در ویژگی {{domxref("PublicKeyCredential.response", "response")}} از یک شیء {{domxref("PublicKeyCredential")}} موجود است که توسط یک فراخوانی موفق {{domxref("CredentialsContainer.create()")}} برگردانده میشود.

این رابط از {{domxref("AuthenticatorResponse")}} ارث میبرد.

{{InheritanceDiagram}}

> [!NOTE]
> این رابط به زمینههای سطح بالا محدود است. استفاده از ویژگیهای آن در داخل یک عنصر {{HTMLElement("iframe")}} هیچ تأثیری نخواهد داشت.

## ویژگیهای نمونه

_همچنین ویژگیهایی را از والد خود، {{domxref("AuthenticatorResponse")}}، به ارث میبرد._

- {{domxref("AuthenticatorAttestationResponse.attestationObject")}} {{ReadOnlyInline}}
  - : یک {{jsxref("ArrayBuffer")}} حاوی دادههای احراز هویت و یک بیانیه گواهی برای یک جفت کلید جدید که توسط احراز هویتکننده تولید شده است.

- {{domxref("AuthenticatorResponse.clientDataJSON")}} {{ReadOnlyInline}}
  - : این ویژگی که از {{domxref("AuthenticatorResponse")}} به ارث رسیده، شامل سریالسازی سازگار با JSON از دادههایی است که از مرورگر به احراز هویتکننده برای تولید این اعتبارنامه ارسال شده است — یعنی زمانی که {{domxref("CredentialsContainer.create()")}} با گزینه `publicKey` فراخوانی میشود. این داده شامل برخی اطلاعات از گزینههای ارسالشده به فراخوانی `create()` و برخی اطلاعات کنترلشده توسط مرورگر است.

## روشهای نمونه

- {{domxref("AuthenticatorAttestationResponse.getAuthenticatorData()")}}
  - : یک {{jsxref("ArrayBuffer")}} حاوی دادههای احراز هویت موجود در ویژگی {{domxref("AuthenticatorAttestationResponse.attestationObject")}} را برمیگرداند.
- {{domxref("AuthenticatorAttestationResponse.getPublicKey()")}}
  - : یک {{jsxref("ArrayBuffer")}} حاوی `SubjectPublicKeyInfo` به فرمت DER از اعتبارنامه جدید (به [Subject Public Key Info](https://www.rfc-editor.org/info/rfc5280/#section-4.1.2.7) مراجعه کنید) را برمیگرداند، یا اگر در دسترس نباشد، `null` را برمیگرداند.
- {{domxref("AuthenticatorAttestationResponse.getPublicKeyAlgorithm()")}}
  - : عددی برابر با [شناسه الگوریتم COSE](https://www.iana.org/assignments/cose/cose.xhtml#algorithms) را برمیگرداند که الگوریتم رمزنگاری استفادهشده برای اعتبارنامه جدید را نشان میدهد.
- {{domxref("AuthenticatorAttestationResponse.getTransports()")}}
  - : آرایهای از رشتهها را برمیگرداند که توصیف میکند کدام روشهای انتقال (مانند `usb`، `nfc`) با احراز هویتکننده پشتیبانی میشوند. اگر این اطلاعات در دسترس نباشد، آرایه ممکن است خالی باشد.

## مثالها

برای یک مثال دقیق، به [ایجاد یک اعتبارنامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/create#creating_a_public_key_credential) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AuthenticatorAssertionResponse")}}: رابط برای نوع پاسخی که هنگام بازیابی یک اعتبارنامه موجود داده میشود.
- {{domxref("AuthenticatorResponse")}}: رابط والد.