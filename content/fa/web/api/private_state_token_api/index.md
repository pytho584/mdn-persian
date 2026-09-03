---
title: Private State Token API
slug: Web/API/Private_State_Token_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.fetch.init_privateToken_parameter
spec-urls: https://wicg.github.io/trust-token-api/
---

{{DefaultAPISidebar("Private State Token API")}}{{SeeCompatTable}}

**Private State Token API** سازوکاری برای انتقال اعتماد به اصالت یک کاربر از یک بافت مرور (browsing context) به بافتی دیگر فراهم می‌کند، بدون آنکه هویت کاربر فاش شود یا فعالیت‌های او در وب‌سایت‌های مختلف قابل ردیابی باشد.

## مفاهیم و کاربرد

برای جلوگیری از کلاهبرداری در وب، وب‌سایت‌ها و سرویس‌ها باید سیگنال‌های اعتمادی ایجاد و منتقل کنند که اثبات کند کاربر همان کسی است که ادعا می‌کند و نه یک ربات که وانمود می‌کند انسان است و نه طرف سوم مخربی که از یک شخص یا سرویس واقعی کلاهبرداری می‌کند.

- اعتماد با استفاده از سازوکارهایی مانند [کپچا](https://en.wikipedia.org/wiki/CAPTCHA)، تأیید آدرس ایمیل یا انجام خرید ایجاد می‌شود.
- اعتماد به‌طور سنتی بین مبدأهای مختلف با سازوکارهایی مانند [کوکی‌های طرف سوم](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) منتقل می‌شود.

متأسفانه، فنون مبتنی بر کوکی فعلی برای انتقال چنین اطلاعاتی امن نیستند و می‌توانند برای {{glossary("fingerprinting")}} و ردیابی کاربران استفاده شوند که برای حریم خصوصی کاربر مشکل‌ساز است.

توکن‌های حالت خصوصی این مشکل را حل می‌کنند و اجازه می‌دهند سیگنال‌های اعتماد بدون ردیابی غیرفعال، با استفاده از [پروتکل Privacy Pass](https://privacypass.github.io/) در پس‌زمینه، بین مبدأها منتقل شوند.

> [!NOTE]
> توکن‌های حالت خصوصی جایگزینی برای کپچا یا سایر سازوکارهای ایجاد اعتماد نیستند. توکن‌های حالت خصوصی راهی برای _انتقالِ_ اعتماد به یک کاربر فراهم می‌کنند، نه _ایجادِ_ اعتماد در یک کاربر.

### توکن‌های حالت خصوصی چگونه کار می‌کنند؟

1. هنگامی که یک وب‌سایت به اعتماد کاربر دست یافته است (مثلاً از طریق کپچا)، می‌تواند یک توکن رمزنگاری‌شده صادر کند که توسط مرورگر کاربر به‌طور امن ذخیره می‌شود. به این وب‌سایت **صادرکننده (issuer)** می‌گویند.
2. وب‌سایت دیگری می‌تواند با بررسی اینکه آیا مرورگر کاربر توکنی را که توسط صادرکننده‌ای مورد اعتمادِ آن وب‌سایت صادر شده است ذخیره کرده، تأیید کند که همان کاربر قابل اعتماد است. اگر چنین بود، می‌تواند آن توکن را بازخرید کند تا یک **رکورد بازخرید (redemption record)** به دست آورد. به این وب‌سایت **بازخریدکننده (redeemer)** می‌گویند.
3. سپس از رکورد بازخرید برای دادن دسترسی کاربر به سرویس‌ها استفاده می‌شود، گویی کاربر مستقیماً با آن وب‌سایت احراز هویت شده است؛ همچنین می‌توان آن را برای انتقال اعتماد به طرف‌های دیگر ارسال کرد.

توکن‌های حالت خصوصی رمزنگاری شده‌اند، بنابراین شناسایی یک فرد یا اتصال نمونه‌های معتمد و غیرمعتمد برای کشف هویت کاربر ممکن نیست.

راهنمای استفاده از توکن‌های حالت خصوصی را در [استفاده از Private State Token API](/en-US/docs/Web/API/Private_State_Token_API/Using) ببینید.

## رابط‌ها (Interfaces)

Private State Token API هیچ رابط مجزای خود را ندارد.

### افزوده‌شده‌ها به رابط‌های دیگر

- {{domxref("Document.hasPrivateToken()")}}
  - : یک promise برمی‌گرداند که با یک مقدار بولین تکمیل می‌شود و نشان می‌دهد که آیا مرورگر یک توکن حالت خصوصی ذخیره‌شده از یک صادرکنندهٔ خاص دارد یا نه.
- {{domxref("Document.hasRedemptionRecord()")}}
  - : یک promise برمی‌گرداند که با یک مقدار بولین تکمیل می‌شود و نشان می‌دهد که آیا مرورگر یک رکورد بازخرید متعلق به یک صادرکنندهٔ خاص دارد یا نه.
- {{domxref("HTMLIFrameElement.privateToken")}}
  - : مقدار ویژگیِ `privateToken` عنصر `<iframe>` را منعکس می‌کند.
- {{domxref("Window.fetch", "fetch()")}} / {{domxref("Request.Request", "Request()")}}، گزینهٔ [`privateToken`](/en-US/docs/Web/API/RequestInit#privatetoken)
  - : شیئی که یک عملیات توکن حالت خصوصی را نمایش می‌دهد. فراخوانی‌های fetch با گزینهٔ `privateToken` عملیاتی مانند صدور یا بازخرید توکن‌ها را آغاز می‌کنند.
- {{domxref("XMLHttpRequest.setPrivateToken()")}}
  - : اطلاعات توکن حالت خصوصی را به یک فراخوانی `XMLHttpRequest` اضافه می‌کند تا عملیات توکن حالت خصوصی آغاز شود.

## عناصر HTML

- {{htmlelement("iframe")}}، ویژگی [`privateToken`](/en-US/docs/Web/HTML/Reference/Elements/iframe#privatetoken)
  - : شامل یک نمایش رشته‌ای از یک شیء گزینه‌ها است که یک عملیات توکن حالت خصوصی را نشان می‌دهد. iframeهای دارای این ویژگی می‌توانند برای آغاز عملیاتی مانند صدور یا بازخرید توکن‌ها استفاده شوند.

## هدرهای HTTP

- {{httpheader("Permissions-Policy")}}؛ دستور {{httpheader('Permissions-Policy/private-state-token-issuance','private-state-token-issuance')}}
  - : استفاده از عملیات `token-request` را کنترل می‌کند.
- {{httpheader("Permissions-Policy")}}؛ دستور {{httpheader('Permissions-Policy/private-state-token-redemption','private-state-token-redemption')}}
  - : استفاده از عملیات `token-redemption` و `send-redemption-record` را کنترل می‌کند.
- {{httpheader("Sec-Redemption-Record")}}
  - : یک هدر درخواست که هنگام انجام درخواست fetch از نوع `send-redemption-record`، یک رکورد بازخرید را برای انتقال اعتماد به طرف دیگر ارسال می‌کند.
- {{httpheader("Sec-Private-State-Token")}}
  - : هم به‌صورت هدر درخواست و هم به‌صورت هدر پاسخ وجود دارد؛ در درخواست‌های صدور و بازخرید برای انتقال داده‌های درخواست (مانند nonceهای کور (blinded nonce) که برای تولید توکن‌ها استفاده می‌شوند) و داده‌های پاسخ (مانند توکن‌ها و رکوردهای بازخرید) به‌کار می‌رود.
- {{httpheader("Sec-Private-State-Token-Crypto-Version")}}
  - : یک هدر درخواست که به سرور صادرکننده ارسال می‌شود و مشخص می‌کند هنگام تولید توکن‌ها از کدام نسخهٔ پروتکل رمزنگاری برای امضای nonceهای کور استفاده شود.
- {{httpheader("Sec-Private-State-Token-Lifetime")}}
  - : یک هدر پاسخ که توسط سرور بازخریدکننده ارسال می‌شود تا به مرورگر بگوید یک رکورد بازخرید خاص را برای چه مدتی در حافظهٔ نهان نگه دارد.

## ملاحظات امنیتی

عملیات `token-request` توکن حالت خصوصی توسط دستور {{httpheader('Permissions-Policy/private-state-token-issuance','private-state-token-issuance')}} هدر {{httpheader("Permissions-Policy")}} کنترل می‌شود؛ در حالی که عملیات `token-redemption` و `send-redemption-record` توسط دستور {{httpheader('Permissions-Policy/private-state-token-redemption','private-state-token-redemption')}} کنترل می‌شوند.

به‌طور خاص، هر جا که یک خط‌مشی تعریف‌شده استفاده را مسدود کند، هر تلاش برای آغاز عملیات توکن حالت خصوصی از طریق درخواست‌های fetch ناموفق خواهد بود.

## مثال‌ها

برای یک نمونه پیاده‌سازی، به [صادرکنندهٔ نمونهٔ Private State Token](https://privatetokens.dev/) مراجعه کنید.

## مشخصات

{{specifications}}

## سازگاری مرورگر

{{Compat}}