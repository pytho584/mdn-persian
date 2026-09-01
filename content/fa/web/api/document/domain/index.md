---
title: "Document: domain property"
---

---
title: "Document: domain property"
short-title: domain
slug: Web/API/Document/domain
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.domain
---

{{APIRef("DOM")}}{{Deprecated_Header}}

ویژگی **`domain`** در رابط {{domxref("Document")}}، بخش دامنهٔ {{glossary("origin")}} سند فعلی را دریافت یا تنظیم می‌کند، همان‌طور که توسط [سیاست همان-ریشه](/en-US/docs/Web/Security/Defenses/Same-origin_policy) استفاده می‌شود.

## مقدار

یک رشته.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : سند از تنظیم دامنهٔ خود منع شده است، مثلاً در حالت sandboxed (جعبه شنی) یا با مبدأ ناشفاف قرار دارد. برای جزئیات به [بخش خطاها](#failures) مراجعه کنید.

## مثال‌ها

### دریافت دامنه

برای کدی که در نشانی `https://developer.mozilla.org/en-US/docs/Web` اجرا می‌شود، این مثال `currentDomain` را روی رشتهٔ `"developer.mozilla.org"` تنظیم می‌کند.

```js
const currentDomain = document.domain;
```

گیرنده (getter) این ویژگی، بخش دامنه از مبدأ سند فعلی را برمی‌گرداند. در بیشتر موارد، این همان بخش hostname از نشانی سند است. با این حال، استثناهایی وجود دارد:

- اگر صفحه دارای {{glossary("origin")}} ناشفاف باشد، مثلاً برای صفحه‌ای با [نشانی داده (data URL)](/en-US/docs/Web/URI/Reference/Schemes/data)، رشتهٔ خالی برمی‌گرداند.
- اگر [تنظیم‌کننده (setter) `document.domain`](#setting_the_domain) استفاده شده باشد، مقدار تنظیم‌شده را برمی‌گرداند.

اگرچه گیرنده به اندازهٔ تنظیم‌کننده خطرناک نیست، اما احتمالاً ساده‌تر و کاربردی‌تر است که به جای آن از ویژگی {{domxref("Location.hostname")}} استفاده کنید. به این ترتیب می‌توانید به‌طور کامل از `document.domain` اجتناب کنید:

```js
const currentHostname = location.hostname;
```

برای نشانی `https://developer.mozilla.org/en-US/docs/Web`، `currentHostname` نیز رشتهٔ `"developer.mozilla.org"` است. جایگزین‌های دیگری که اطلاعات کمی متفاوت ارائه می‌دهند عبارت‌اند از {{domxref("Location.host")}} که شامل پورت است، و {{domxref("Window.origin")}} که مبدأ کامل را ارائه می‌دهد.

### تنظیم دامنه

```js
document.domain = domainString;
```

تنظیم‌کنندهٔ این ویژگی می‌تواند برای _تغییر_ {{glossary("origin")}} یک صفحه استفاده شود و بدین ترتیب نحوهٔ انجام برخی بررسی‌های امنیتی را تغییر دهد. این ویژگی فقط می‌تواند روی همان دامنه یا دامنهٔ والد تنظیم شود. برای مثال، اگر هر دو `https://a.example.com` و `https://b.example.com` از کد زیر استفاده کنند:

```js
document.domain = "example.com";
```

آنگاه هر دو مبدأ خود را طوری تغییر داده‌اند که دامنهٔ یکسانی داشته باشند، و اکنون می‌توانند مستقیماً به DOM یکدیگر دسترسی پیدا کنند — علیرغم اینکه cross-origin هستند، که معمولاً چنین دسترسی را مسدود می‌کند.

توجه داشته باشید که تنظیم `document.domain` روی مقدار فعلی آن یک عملیات بی‌اثر (no-op) نیست. همچنان مبدأ را تغییر می‌دهد. برای مثال، اگر صفحه‌ای کد زیر را اجرا کند:

```js
document.domain = document.domain;
```

آنگاه آن صفحه نسبت به هر صفحهٔ دیگری که به‌طور عادی same-origin است و چنین کاری نکرده است، به عنوان cross-origin در نظر گرفته می‌شود.

#### منسوخ شدن

تنظیم‌کنندهٔ `document.domain` منسوخ شده است. این ویژگی محافظت‌های امنیتی فراهم‌شده توسط [سیاست همان-ریشه](/en-US/docs/Web/Security/Defenses/Same-origin_policy) را تضعیف می‌کند و مدل مبدأ را در مرورگرها پیچیده می‌کند و در نتیجه مشکلات تعامل‌پذیری و باگ‌های امنیتی ایجاد می‌شود.

اقدام به تنظیم `document.domain` خطرناک است. این کار دسترسی کامل به DOM یک صفحه را از _همهٔ_ زیردامنه‌ها باز می‌کند، که احتمالاً مورد نظر نیست. همچنین مؤلفهٔ پورت را از مبدأ حذف می‌کند، بنابراین اکنون صفحات دیگری که همان آدرس IP یا همان مؤلفهٔ host را دارند، می‌توانند به صفحهٔ شما دسترسی پیدا کنند، حتی روی پورتی متفاوت.

این موضوع به‌ویژه در میزبانی اشتراکی (shared hosting) ناامن است. برای مثال، مشتری دیگری در همان میزبان اشتراکی می‌تواند سایتی را روی همان آدرس IP اما روی پورتی متفاوت میزبانی کند؛ سپس تنظیم `document.domain` حفاظت همان-ریشه را که به‌طور عادی از شما در برابر دسترسی آن سایتِ مشتری دیگر به داده‌های سایت شما محافظت می‌کند، از بین می‌برد.

مشکلات مشابهی برای سایت‌های میزبانی اشتراکی که به هر مشتری یک زیردامنهٔ متفاوت می‌دهند، رخ می‌دهد. اگر سایتی `document.domain` را تنظیم کند، هر مشتری دیگری در یک زیردامنهٔ متفاوت می‌تواند همین کار را انجام دهد و به داده‌های سایت اصلی دسترسی یابد.

به جای استفاده از `document.domain` برای تسهیل ارتباط cross-origin، باید از {{domxref("Window.postMessage")}} برای ارسال یک پیام ناهمگام به مبدأ دیگر استفاده کنید. این دسترسی کنترل‌شده از طریق ارسال پیام، بسیار امن‌تر از افشای کامل تمام داده‌هایی است که توسط `document.domain` ایجاد می‌شود.

#### خطاها

تنظیم‌کننده در چند مورد یک `SecurityError` {{domxref("DOMException")}} پرتاب می‌کند:

- سند داخل یک {{htmlelement("iframe")}} جعبه‌ای (sandboxed) قرار دارد.
- سند هیچ {{glossary("browsing context")}} ندارد.
- [دامنهٔ مؤثر](https://html.spec.whatwg.org/multipage/origin.html#concept-origin-effective-domain) سند برابر `null` است.
- مقدار داده‌شده نه با hostname فعلی صفحه یکسان است و نه دامنهٔ والد آن.

به عنوان مثال از این مورد آخر، تلاش برای تنظیم `document.domain` روی `"example.org"` زمانی که در `https://example.com/` هستید، خطا پرتاب می‌کند.

علاوه بر این، به عنوان بخشی از فرایند منسوخ شدن، در ترکیب با برخی ویژگی‌های مدرن ایزوله‌سازی، هیچ کاری انجام نمی‌دهد:

- اگر در صفحه‌ای با ایزوله‌سازی cross-origin استفاده شود، یعنی صفحه‌ای که از مقادیر مناسب برای هدرهای HTTP {{httpheader("Cross-Origin-Opener-Policy")}} و {{httpheader("Cross-Origin-Embedder-Policy")}} استفاده می‌کند.
- اگر در صفحه‌ای با ایزوله‌سازی مبدأ استفاده شود، یعنی صفحه‌ای که از هدر HTTP {{httpheader("Origin-Agent-Cluster")}} {{experimental_inline}} استفاده می‌کند.

در نهایت، تنظیم `document.domain` مبدأ مورد استفاده برای بررسی‌های مبدأ توسط برخی APIهای وب را تغییر نمی‌دهد و بدین ترتیب دسترسی زیردامنه از طریق این مکانیزم را مسدود می‌کند. APIهای تحت تأثیر شامل (اما نه محدود به) این موارد هستند: {{domxref("Window.localStorage")}}, [API IndexDB](/en-US/docs/Web/API/IndexedDB_API), {{domxref("BroadcastChannel")}}, {{domxref("SharedWorker")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [سیاست همان-ریشه](/en-US/docs/Web/Security/Defenses/Same-origin_policy)
- {{domxref("Location.hostname")}}
- {{domxref("Location.host")}}
- {{domxref("Window.origin")}}