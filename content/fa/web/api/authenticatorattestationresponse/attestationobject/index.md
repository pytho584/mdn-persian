---
title: "AuthenticatorAttestationResponse: attestationObject property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAttestationResponse/attestationObject"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAttestationResponse: attestationObject property"
short-title: attestationObject
slug: Web/API/AuthenticatorAttestationResponse/attestationObject
page-type: web-api-instance-property
browser-compat: api.AuthenticatorAttestationResponse.attestationObject
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی **`attestationObject`** از رابط {{domxref("AuthenticatorAttestationResponse")}} یک {{jsxref("ArrayBuffer")}} را بازمی‌گرداند که شامل کلید عمومی جدید و همچنین امضایی بر روی کل `attestationObject` با یک کلید خصوصی است که در هنگام ساخته شدن در احراز هویت‌کننده ذخیره می‌شود.

به عنوان بخشی از فراخوانی {{domxref("CredentialsContainer.create()")}}، یک احراز هویت‌کننده یک جفت کلید جدید و همچنین یک `attestationObject` برای آن جفت کلید ایجاد می‌کند. کلید عمومی که با کلید خصوصی ایجادکننده امضای تأییدیه (attestation signature) مطابقت دارد، به خوبی شناخته شده است؛ با این حال، زنجیره‌های کلید عمومی تأییدیه شناخته شده مختلفی برای اکوسیستم‌های گوناگون (مانند تأییدیه‌های Android یا TPM) وجود دارد.

## مقدار

پس از رمزگشایی `ArrayBuffer` رمزگذاری‌شده با [CBOR](https://datatracker.ietf.org/doc/html/rfc8949)، شیء جاوااسکریپت حاصل شامل ویژگی‌های زیر خواهد بود:

- `authData`
  - : [داده‌های احراز هویت](/en-US/docs/Web/API/Web_Authentication_API/Authenticator_data) برای عملیات. توجه داشته باشید که در {{domxref("AuthenticatorAssertionResponse")}}، `authenticatorData` به عنوان یک ویژگی در یک شیء جاوااسکریپت نمایش داده می‌شود (به {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} مراجعه کنید) در حالی که در {{domxref("AuthenticatorAttestationResponse")}}، `authenticatorData` یک ویژگی در یک نقشه [CBOR](https://datatracker.ietf.org/doc/html/rfc8949) است.

    فیلد {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} یکسان توسط هر دو `AuthenticatorAttestationResponse` و `AuthenticatorAssertionResponse` استفاده می‌شود. هنگامی که در تأییدیه استفاده می‌شود، شامل یک فیلد اختیاری به نام `attestedCredentialData` است. این فیلد هنگام استفاده در `AuthenticatorAssertionResponse` گنجانده نمی‌شود. فیلد attestedCredentialData شامل `credentialId` و `credentialPublicKey` است.

- `fmt`
  - : یک رشته متنی که قالب attStmt را نشان می‌دهد. [مشخصات WebAuthn تعدادی قالب را تعریف می‌کند](https://w3c.github.io/webauthn/#sctn-defined-attestation-formats)؛ با این حال، قالب‌ها ممکن است در مشخصات دیگر نیز تعریف شده و در یک [ثبت IANA](https://w3c.github.io/webauthn/#sctn-att-fmt-reg) ثبت شوند. قالب‌های تعریف‌شده توسط WebAuthn عبارتند از:
    - `"packed"`
    - `"tpm"`
    - `"android-key"`
    - `"android-safetynet"`
    - `"fido-u2f"`
    - `"none"`

- `attStmt`
  - : یک عبارت تأییدیه (attestation statement) که در قالب تعریف‌شده توسط `"fmt"` است. در حال حاضر، [برای جزئیات هر قالب به مشخصات WebAuthn مراجعه کنید](https://w3c.github.io/webauthn/#sctn-defined-attestation-formats).

## مثال‌ها

برای یک مثال دقیق، [ایجاد یک اعتبارنامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/create#creating_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CredentialsContainer.create()")}}: روشی که برای ایجاد یک عبارت با یک `challenge` رمزنگاری استفاده می‌شود که امضای آن توسط احراز هویت‌کننده در `attStmt` موجود است، با گزینه انتقال `attestation` مشخص‌شده.