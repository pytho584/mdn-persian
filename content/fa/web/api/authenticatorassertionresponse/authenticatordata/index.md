---
title: "AuthenticatorAssertionResponse: authenticatorData property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAssertionResponse/authenticatorData"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAssertionResponse: authenticatorData property"
short-title: authenticatorData
slug: Web/API/AuthenticatorAssertionResponse/authenticatorData
page-type: web-api-instance-property
browser-compat: api.AuthenticatorAssertionResponse.authenticatorData
---

{{securecontext_header}}{{APIRef("Web Authentication API")}}

خصوصیت **`authenticatorData`** از رابط {{domxref("AuthenticatorAssertionResponse")}} یک {{jsxref("ArrayBuffer")}} برمی‌گرداند که شامل اطلاعاتی از احرازکننده است؛ مانند هش شناسهٔ طرف اعتماد (rpIdHash)، شمارندهٔ امضا، تست حضور کاربر، پرچم‌های تأیید هویت کاربر و هر افزونه‌ای که توسط احرازکننده پردازش شده است.

## مقدار

یک {{jsxref("ArrayBuffer")}} با {{jsxref("ArrayBuffer.byteLength", "byteLength")}} حداقل ۳۷ بایت، که شامل ساختار داده‌ای است که در [داده‌های احرازکننده](/en-US/docs/Web/API/Web_Authentication_API/Authenticator_data) توضیح داده شده است.

## مثال‌ها

برای یک مثال دقیق، [بازیابی یک گواهینامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/get#retrieving_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}