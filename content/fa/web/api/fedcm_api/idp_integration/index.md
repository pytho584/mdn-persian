---
title: Identity provider integration with FedCM
slug: Web/API/FedCM_API/IDP_integration
page-type: guide
---

{{DefaultAPISidebar("FedCM API")}}

این مقاله تمام مراحلی را شرح می‌دهد که یک {{glossary("Identity provider", "ارائه‌دهنده هویت")}} (IdP) باید برای یکپارچه‌سازی با API مدیریت اعتبار فدرال (Federated Credential Management؛ به‌اختصار FedCM) انجام دهد.

## مراحل یکپارچه‌سازی IdP

برای یکپارچه‌سازی با FedCM، یک IdP باید کارهای زیر را انجام دهد:

1. [ارائه فایل well-known](#provide_a_well-known_file) برای شناسایی IdP.
2. [ارائه فایل پیکربندی و endpointها](#provide_a_config_file_and_endpoints) برای فهرست حساب‌ها و صدور توکن تأیید (و به‌صورت اختیاری فراداده کلاینت).
3. [به‌روزرسانی وضعیت ورود](#update_login_status_using_the_login_status_api) با استفاده از Login Status API.

## ارائه فایل well-known

یک مشکل بالقوه حریم خصوصی وجود دارد که در آن یک [IdP می‌تواند بدون رضایت صریح کاربر متوجه شود که آیا کاربر از یک relying party (RP) بازدید کرده است](https://github.com/w3c-fedid/FedCM/issues/230) یا نه. این موضوع پیامدهایی برای ردیابی کاربران دارد؛ بنابراین از IdP خواسته می‌شود فایل well-known را برای تأیید هویت خود ارائه دهد و این مشکل را کاهش دهد.

فایل well-known از طریق یک درخواست [`GET`](/en-US/docs/Web/HTTP/Reference/Methods/GET) بدون اعتبارنامه (uncredentialed) دریافت می‌شود که ریدایرکت‌ها را دنبال نمی‌کند. این کار عملاً مانع از آن می‌شود که IdP بفهمد چه کسی درخواست را ارسال کرده و کدام {{glossary("Relying party", "طرف اتکا")}} (RP) در تلاش برای اتصال است.

فایل well-known باید از {{glossary("registrable domain", "دامنه قابل ثبت")}} IdP در مسیر `/.well-known/web-identity` ارائه شود. برای مثال، اگر endpointهای IdP زیر نشانی `https://accounts.idp.example/` ارائه می‌شوند، باید فایل well-known را در `https://idp.example/.well-known/web-identity` قرار دهد. محتوای فایل well-known باید ساختار JSON زیر را داشته باشد:

```json
{
  "provider_urls": ["https://accounts.idp.example/config.json"]
}
```

عضو `provider_urls` باید آرایه‌ای از URLها باشد که به فایل‌های پیکربندی معتبر IdP اشاره می‌کنند و RPها می‌توانند برای تعامل با IdP از آن‌ها استفاده کنند. طول این آرایه در حال حاضر به یک مورد محدود است.

## هدر HTTP `Sec-Fetch-Dest`

همه درخواست‌های ارسال‌شده از طرف مرورگر از طریق FedCM شامل هدر `{{httpheader("Sec-Fetch-Dest")}}: webidentity` هستند. همه endpointهای IdP که درخواست‌های دارای اعتبارنامه دریافت می‌کنند (یعنی `accounts_endpoint` و `id_assertion_endpoint`) باید بررسی کنند که این هدر برای محافظت در برابر حملات {{glossary("CSRF")}} وجود دارد.

## ارائه فایل پیکربندی و endpointها

فایل پیکربندی IdP فهرستی از endpointهایی را ارائه می‌دهد که مرورگر برای پردازش جریان فدراسیون هویت و مدیریت ورودها به آن‌ها نیاز دارد. endpointها باید با پیکربندی هم‌منشأ (same-origin) باشند.

مرورگر درخواستی بدون اعتبارنامه برای دریافت فایل پیکربندی از طریق روش [`GET`](/en-US/docs/Web/HTTP/Reference/Methods/GET) ارسال می‌کند که ریدایرکت‌ها را دنبال نمی‌کند. این کار عملاً مانع از آن می‌شود که IdP بفهمد چه کسی درخواست را ارسال کرده و کدام RP در تلاش برای اتصال است.

فایل پیکربندی (که در مثال ما در `https://accounts.idp.example/config.json` میزبانی می‌شود) باید ساختار JSON زیر را داشته باشد:

```json
{
  "accounts_endpoint": "/accounts.php",
  "account_label": "developer",
  "supports_use_other_account": true,
  "client_metadata_endpoint": "/client_metadata.php",
  "disconnect_endpoint": "/disconnect.php",
  "id_assertion_endpoint": "/assertion.php",
  "login_url": "/login",
  "branding": {
    "background_color": "green",
    "color": "0xFFEEAA",
    "icons": [
      {
        "url": "https://idp.example/icon.ico",
        "size": 25
      }
    ]
  }
}
```

ویژگی‌ها به شرح زیر هستند:

- `accounts_endpoint`
  - : URL مربوط به endpoint فهرست حساب‌ها که فهرستی از حساب‌هایی را برمی‌گرداند که کاربر در حال حاضر روی IdP با آن‌ها وارد شده است. مرورگر از این فهرست برای ایجاد فهرستی از گزینه‌های ورود استفاده می‌کند که در رابط کاربری FedCM ارائه‌شده توسط مرورگر به کاربر نمایش داده می‌شود.
- `account_label` {{optional_inline}}
  - : یک رشته که اگر شامل شود، شناسه‌ای برای زیرمجموعه‌ای از حساب‌ها مشخص می‌کند که وقتی از این IdP برای احراز هویت فدرال استفاده می‌شود باید بازگردانده شوند. وقتی درخواست `get()` انجام می‌شود، فقط آن دسته از حساب‌ها از [endpoint فهرست حساب‌ها](#the_accounts_list_endpoint) بازگردانده می‌شوند که این رشته در پارامتر `label_hints` آن‌ها وجود داشته باشد.
- `supports_use_other_account` {{optional_inline}}
  - : یک مقدار بولین که پیش‌فرض آن `false` است؛ اگر روی `true` تنظیم شود، یعنی کاربران می‌توانند با حسابی غیر از حسابی که در حال حاضر با آن وارد شده‌اند وارد شوند (اگر IdP از چند حساب پشتیبانی کند). این فقط برای فراخوانی‌های `get()` که [حالت فعال (active mode)](/en-US/docs/Web/API/IdentityCredentialRequestOptions#active) را مشخص می‌کنند اعمال می‌شود.
    > [!NOTE]
    > در رابط کاربری ورود به سیستم مرورگر، این ویژگی به احتمال زیاد به‌صورت نوعی دکمه «انتخاب حساب دیگر» (Choose other account) ظاهر می‌شود.
- `client_metadata_endpoint` {{optional_inline}}
  - : URL مربوط به endpoint فراداده کلاینت که URLهای اشاره‌کننده به فراداده و صفحات شرایط استفاده از سرویس RP را برای استفاده در رابط کاربری FedCM فراهم می‌کند.
- `disconnect_endpoint` {{optional_inline}}
  - : URL مربوط به endpoint قطع اتصال که RP از طریق روش {{domxref("IdentityCredential.disconnect_static", "IdentityCredential.disconnect()")}} برای قطع اتصال از IdP استفاده می‌کند.
- `id_assertion_endpoint`
  - : URL مربوط به endpoint صدور توکن تأیید هویت؛ وقتی اعتبارنامه‌های معتبر کاربر به این endpoint ارسال شود، باید با یک توکن تأیید پاسخ دهد که RP می‌تواند برای تأیید اعتبار احراز هویت از آن استفاده کند.
- `login_url`
  - : URL صفحه ورود برای اینکه کاربر به IdP وارد شود.
- `branding` {{optional_inline}}
  - : شامل اطلاعات برندینگ است که در رابط کاربری FedCM ارائه‌شده توسط مرورگر برای سفارشی‌سازی ظاهر آن مطابق میل IdP استفاده می‌شود. اندازه آیکون ارائه‌شده در حالت غیرفعال (passive) باید بزرگ‌تر یا مساوی `25` (`25px`) و در حالت فعال (active) بزرگ‌تر یا مساوی `40` (`40px`) باشد (برای جزئیات بیشتر به [حالت فعال در برابر حالت غیرفعال](/en-US/docs/Web/API/FedCM_API/RP_sign-in#active_versus_passive_mode) مراجعه کنید).

جدول زیر خلاصه‌ای از درخواست‌های مختلف ارسال‌شده توسط FedCM API را نشان می‌دهد:

| Endpoint/منبع               | روش   | دارای اعتبارنامه (با کوکی‌ها) | شامل {{httpheader("Origin")}} |
| --------------------------- | ------ | ----------------------------- | ------------------------------ |
| `well-known`/`config.json`  | `GET`  | خیر                           | خیر                            |
| `accounts_endpoint`         | `GET`  | بله                           | خیر                            |
| `client_metadata_endpoint`  | `GET`  | خیر                           | بله                            |
| `disconnect_endpoint`       | `POST` | بله                           | بله                            |
| `id_assertion_endpoint`     | `POST` | بله                           | بله                            |

> [!NOTE]
> برای توضیح جریان FedCM که در آن به این endpointها دسترسی پیدا می‌شود، [جریان ورود FedCM](/en-US/docs/Web/API/FedCM_API/RP_sign-in#fedcm_sign-in_flow) را ببینید.

> [!NOTE]
> هیچ‌یک از درخواست‌های ارسال‌شده توسط FedCM API به endpointهای شرح‌داده‌شده در اینجا، به دلایل حریم خصوصی، اجازه پیروی از ریدایرکت‌ها را ندارند.

### endpoint فهرست حساب‌ها

مرورگر درخواست‌ها را با روش `GET` به این endpoint ارسال می‌کند. درخواست هیچ پارامتر `client_id`، هدر {{httpheader("Origin")}} یا هدر {{httpheader("Referer")}} ندارد. این کار عملاً مانع از آن می‌شود که IdP بفهمد کاربر در تلاش است به کدام RP وارد شود.

برای مثال:

```http
GET /accounts.php HTTP/1.1
Host: idp.example
Accept: application/json
Cookie: 0x23223
Sec-Fetch-Dest: webidentity
```

درخواست دارای اعتبارنامه است؛ یعنی کوکی‌های سایت IdP را شامل می‌شود و IdP می‌تواند از آن‌ها برای تشخیص اینکه کاربر با کدام حساب‌های IdP وارد شده است استفاده کند.

توجه داشته باشید که چون درخواست مرورگر به این endpoint یک درخواست میان‌سایتی (cross-site) است، کوکی‌ها فقط در صورتی شامل می‌شوند که مقدار ویژگی [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) آن‌ها `None` باشد. این یعنی IdPها نمی‌توانند از `SameSite` به‌عنوان بخشی از دفاع خود در برابر حملات [جعل درخواست میان‌سایتی (CSRF)](/en-US/docs/Web/Security/Attacks/CSRF) استفاده کنند، بنابراین باید روش‌های دفاعی جایگزین پیاده‌سازی کنند.

پاسخ، فهرستی از همه حساب‌های IdP را برمی‌گرداند که کاربر در حال حاضر با آن‌ها وارد شده است (مخصوص هیچ RP خاصی نیست)، با ساختار JSON زیر:

```json
{
  "accounts": [
    {
      "id": "elaina_maduro",
      "given_name": "Elaina",
      "name": "Elaina Maduro",
      "email": "elaina_maduro@idp.example",
      "tel": "+491234567890",
      "username": "elaina420",
      "picture": "https://idp.example/profile/123",
      "approved_clients": ["123", "456", "789"],
      "domain_hints": ["rp1.example.com", "rp3.example.com"],
      "label_hints": ["developer", "admin"],
      "login_hints": ["elaina_maduro", "elaina_maduro@idp.example"]
    },
    {
      "id": "elly",
      "given_name": "Elly",
      "username": "elly123",
      "email": "Elly@idp.example",
      "picture": "https://idp.example/profile/456",
      "approved_clients": ["abc", "def", "ghi"],
      "domain_hints": ["rp1.example.com", "rp2.example.com"],
      "label_hints": ["developer", "test"],
      "login_hints": ["elly", "elly@idp.example"]
    }
  ]
}
```

این اطلاعات موارد زیر را شامل می‌شود؛ `name`، `email`، `username` و `tel` اختیاری هستند، اما حداقل یکی از آن‌ها باید وجود داشته باشد و خالی نباشد.

- `id`
  - : شناسه یکتای کاربر.
- `name` {{optional_inline}}
  - : نام خانوادگی کاربر.
- `email` {{optional_inline}}
  - : نشانی ایمیل کاربر.
- `tel` {{optional_inline}}
  - : شماره تلفن کاربر. می‌تواند در هر قالبی باشد.
- `username` {{optional_inline}}
  - : نام کاربری کاربر.
- `given_name` {{optional_inline}}
  - : نام کوچک کاربر.
- `picture` {{optional_inline}}
  - : URL تصویر آواتار کاربر.
- `approved_clients` {{optional_inline}}
  - : آرایه‌ای از کلاینت‌های RP که کاربر با آن‌ها ثبت‌نام کرده است.
- `domain_hints` {{optional_inline}}
  - : آرایه‌ای از دامنه‌هایی که حساب با آن‌ها مرتبط است. RP می‌تواند فراخوانی `get()` انجام دهد که شامل ویژگی [`domainHint`](/en-US/docs/Web/API/IdentityCredentialRequestOptions#domainhint) است تا حساب‌های بازگشت‌داده‌شده را بر اساس دامنه فیلتر کند.
- `label_hints` {{optional_inline}}
  - : آرایه‌ای از رشته‌ها که برچسب‌هایی را مشخص می‌کنند که انواع حساب‌هایی را که حساب با آن‌ها شناسایی می‌شود تعریف می‌کنند. اگر فایل پیکربندی [`account_label`](#account_label) را مشخص کرده باشد، فقط آن دسته از حساب‌ها از endpoint فهرست حساب‌ها بازگردانده می‌شوند که آن برچسب را در `label_hints` خود داشته باشند.
- `login_hints` {{optional_inline}}
  - : آرایه‌ای از رشته‌ها که حساب را نشان می‌دهند. این رشته‌ها برای فیلتر کردن فهرست گزینه‌های حسابی که مرورگر برای ورود کاربر ارائه می‌دهد استفاده می‌شوند. این اتفاق زمانی رخ می‌دهد که ویژگی `loginHint` در [`identity.providers`](/en-US/docs/Web/API/IdentityCredentialRequestOptions#providers) در فراخوانی مربوط به `get()` ارائه شده باشد. هر حسابی که رشته‌ای در آرایه `login_hints` آن با `loginHint` ارائه‌شده مطابقت داشته باشد، در فهرست قرار می‌گیرد.

> [!NOTE]
> اگر کاربر به هیچ حسابی در IdP وارد نشده باشد، endpoint باید با [HTTP 401 (Unauthorized)](/en-US/docs/Web/HTTP/Reference/Status/401) پاسخ دهد.

### endpoint فراداده کلاینت

مرورگر درخواست‌های بدون اعتبارنامه را از طریق روش `GET` به این endpoint ارسال می‌کند و `clientId` که در فراخوانی `get()` به آن داده شده است را به‌عنوان پارامتر ارسال می‌کند.

برای مثال:

```http
GET /client_metadata.php?client_id=1234 HTTP/1.1
Host: idp.example
Origin: https://rp.example/
Accept: application/json
Sec-Fetch-Dest: webidentity
```

پاسخ به یک درخواست موفق شامل URLهایی است که به صفحات فراداده و شرایط استفاده از سرویس RP اشاره می‌کنند تا در رابط کاربری FedCM ارائه‌شده توسط مرورگر استفاده شوند. این پاسخ باید از ساختار JSON زیر پیروی کند:

```json
{
  "privacy_policy_url": "https://rp.example/privacy_policy.html",
  "terms_of_service_url": "https://rp.example/terms_of_service.html"
}
```

### endpoint قطع اتصال

با فراخوانی {{domxref("IdentityCredential.disconnect_static", "IdentityCredential.disconnect()")}}، مرورگر یک درخواست میان‌منشأ (cross-origin) {{httpmethod("POST")}} با کوکی‌ها و {{httpheader("Content-Type")}} از نوع `application/x-www-form-urlencoded` به endpoint قطع اتصال ارسال می‌کند که