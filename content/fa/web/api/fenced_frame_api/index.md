---
title: "Fenced Frame API"
---

---
title: Fenced Frame API
slug: Web/API/Fenced_frame_API
page-type: web-api-overview
status:
  - experimental
browser-compat: html.elements.fencedframe
---

{{SeeCompatTable}}{{DefaultAPISidebar("Fenced Frame API")}}

> [!WARNING]
> این ویژگی در حال حاضر توسط یکی از فروشندگان مرورگر مخالفت شده است.
> برای جزئیات، بخش [مواضع استانداردها](#standards_positions) را در پایین ببینید.

**Fenced Frame API** قابلیت‌هایی برای کنترل محتوای تعبیه‌شده در عناصر {{htmlelement("fencedframe")}} فراهم می‌کند.

## مفاهیم و کاربرد

یکی از منابع اصلی مشکلات [حریم خصوصی](/en-US/docs/Web/Privacy) و [امنیت](/en-US/docs/Web/Security) در وب، محتوایی است که در عناصر {{htmlelement("iframe")}} تعبیه می‌شود. در گذشته از `<iframe>`ها برای قرار دادن کوکی‌های شخص ثالث استفاده می‌شد که می‌توانستند برای به اشتراک‌گذاری اطلاعات و ردیابی کاربران در بین سایت‌ها مورد استفاده قرار گیرند. علاوه بر این، محتوای تعبیه‌شده در یک `<iframe>` می‌تواند با سند میزبان خود ارتباط برقرار کند (مثلاً با استفاده از {{domxref("Window.postMessage()")}}).

سند میزبان نیز می‌تواند با استفاده از اسکریپت‌نویسی اشکال مختلفی از اطلاعات را از `<iframe>` بخواند — برای مثال، به‌طور بالقوه می‌توانید داده‌های قابل توجهی برای ردیابی/اثر انگشت (fingerprinting) از خواندن URL تعبیه‌شده از طریق ویژگی `src` به دست آورید، به‌ویژه اگر شامل [پارامترهای URL](/en-US/docs/Web/URI/Reference/Query) باشد. همچنین `<iframe>` می‌تواند به DOM زمینه میزبان دسترسی داشته باشد و برعکس.

اکثر مرورگرهای مدرن در حال کار بر روی سازوکارهایی برای پارتیشن‌بندی فضای ذخیره‌سازی هستند تا داده‌های کوکی دیگر برای ردیابی قابل استفاده نباشند (به عنوان مثال [کوکی‌های دارای وضعیت پارتیشن‌بندی مستقل (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) یا [پارتیشن‌بندی وضعیت در فایرفاکس](/en-US/docs/Web/Privacy/Guides/State_Partitioning) را ببینید).

عناصر `<fencedframe>` در نظر دارند بخش دیگری از این معما را حل کنند — آن‌ها از نظر شکل و عملکرد بسیار شبیه به `<iframe>`ها هستند، با این تفاوت که:

- ارتباطات نمی‌تواند بین محتوای `<fencedframe>` و سایت میزبان آن به اشتراک گذاشته شود.
- یک `<fencedframe>` می‌تواند به داده‌های بین‌سایتی دسترسی داشته باشد، اما فقط در مجموعه‌ای بسیار خاص از شرایط کنترل‌شده که حریم خصوصی کاربر را حفظ می‌کند.
- نمی‌توان یک `<fencedframe>` را آزادانه دستکاری کرد یا از طریق اسکریپت‌نویسی معمولی به داده‌های آن دسترسی داشت (مثلاً خواندن یا تنظیم URL منبع). محتوای `<fencedframe>` فقط از طریق [APIهای خاص](#use_cases) قابل تعبیه است.
- یک `<fencedframe>` نمی‌تواند به DOM زمینه میزبان دسترسی داشته باشد و همچنین زمینه میزبان نیز نمی‌تواند به DOM `<fencedframe>` دسترسی داشته باشد.

برای اطلاعات بیشتر در مورد مدل ارتباطی fenced frameها، راهنمای [ارتباط با فریم‌های تعبیه‌شده](/en-US/docs/Web/API/Fenced_frame_API/Communication_with_embedded_frames) را بخوانید.

### موارد استفاده

از `<fencedframe>`ها توسط APIهای دیگر برای تعبیه انواع مختلف محتوای بین‌سایتی یا جمع‌آوری داده استفاده می‌شود و موارد استفاده مختلف را به شیوه‌ای حفظ‌کننده حریم خصوصی برآورده می‌کنند. بسیاری از این موارد قبلاً به کوکی‌های شخص ثالث یا سایر سازوکارهایی که برای حریم خصوصی مضر بودند متکی بودند.

- [API Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage) دسترسی به داده‌های بین‌سایتی پارتیشن‌بندی‌نشده را در یک محیط امن فراهم می‌کند و نتایج را در یک `<fencedframe>` محاسبه و/یا نمایش می‌دهد. برای مثال:
  - تبلیغ‌کنندگان می‌توانند میزان دسترسی یک آگهی را اندازه‌گیری کنند یا بر اساس آگهی‌هایی که کاربران قبلاً در سایر سایت‌ها دیده‌اند، آگهی‌های بعدی را ارائه دهند.
  - توسعه‌دهندگان می‌توانند آزمایش A/B انجام دهند و بر اساس گروهی که کاربر به آن اختصاص داده شده است، یا بر اساس تعداد کاربرانی که قبلاً هر نوع را دیده‌اند، انواع مختلفی را به کاربر نشان دهند.
  - کسب‌وکارها می‌توانند تجربه کاربر را بر اساس آنچه در سایت‌های دیگر دیده است سفارشی‌سازی کنند. برای مثال، اگر کاربر قبلاً عضویت خریداری کرده است، ممکن است نخواهید آگهی‌های ثبت‌نام عضویت را در سایر ویژگی‌های خود به او نشان دهید.
- [API Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience) به توسعه‌دهندگان اجازه می‌دهد تبلیغات مبتنی بر گروه‌های علاقه‌مندی (interest groups) را پیاده‌سازی کنند، یعنی موارد استفاده بازاریابی مجدد و مخاطبان سفارشی. این API می‌تواند پیشنهادهای متعدد برای فضای تبلیغاتی را ارزیابی کند و آگهی برنده را در یک `<fencedframe>` نمایش دهد.
- [API Private Aggregation](https://privacysandbox.google.com/private-advertising/private-aggregation) می‌تواند داده‌ها را از `<fencedframe>`ها (که از shared storage یا Protected Audience API منشأ می‌گیرند) جمع‌آوری کند و گزارش‌های تجمیعی ایجاد کند.

## `<fencedframe>`ها چگونه کار می‌کنند؟

همانطور که در بالا ذکر شد، شما محتوای تعبیه‌شده در یک {{htmlelement("fencedframe")}} را مستقیماً از طریق اسکریپت معمولی کنترل نمی‌کنید.

برای تعیین اینکه چه محتوایی در یک `<fencedframe>` نمایش داده شود، یک API استفاده‌کننده (مانند [Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience) یا [Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage)) یک شیء {{domxref("FencedFrameConfig")}} تولید می‌کند که سپس از طریق جاوااسکریپت به عنوان مقدار ویژگی {{domxref("HTMLFencedFrameElement.config")}} عنصر `<fencedframe>` تنظیم می‌شود.

مثال زیر یک `FencedFrameConfig` از حراج آگهی API Protected Audience دریافت می‌کند که سپس برای نمایش آگهی برنده در یک `<fencedframe>` استفاده می‌شود:

```js
const frameConfig = await navigator.runAdAuction({
  // … auction configuration
  resolveToConfig: true,
});

const frame = document.createElement("fencedframe");
frame.config = frameConfig;
```

برای دریافت یک شیء `FencedFrameConfig` باید `resolveToConfig: true` به فراخوانی `runAdAuction()` ارسال شود. اگر `resolveToConfig` روی `false` تنظیم شود، {{jsxref("Promise")}} حاصل به یک [URN](/en-US/docs/Web/URI/Reference/Schemes/urn) مبهم (مثلاً `urn:uuid:c36973b5-e5d9-de59-e4c4-364f137b3c7a`) که فقط در یک `<iframe>` قابل استفاده است، حل خواهد شد.

در هر صورت، مرورگر یک URL حاوی مکان هدف محتوایی که قرار است تعبیه شود را ذخیره می‌کند — که به URN مبهم یا ویژگی داخلی `url` در `FencedFrameConfig` نگاشت می‌شود. مقدار URL توسط جاوااسکریپت در حال اجرا در زمینه میزبان قابل خواندن نیست.

> [!NOTE]
> پشتیبانی از URNهای مبهم در `<iframe>`ها برای تسهیل انتقال پیاده‌سازی‌های موجود به [APIهای Privacy Sandbox](https://privacysandbox.google.com/) فراهم شده است. این پشتیبانی موقت در نظر گرفته شده است و با رشد پذیرش، در آینده حذف خواهد شد.

> [!NOTE]
> `FencedFrameConfig` دارای یک متد {{domxref("FencedFrameConfig.setSharedStorageContext", "setSharedStorageContext()")}} است که برای ارسال داده از سند میزبان به فضای ذخیره‌سازی مشترک `<fencedframe>` استفاده می‌شود. برای مثال، می‌توان از طریق `<fencedframe>` در یک {{domxref("Worklet")}} به آن دسترسی داشت و برای تولید گزارش از آن استفاده کرد. برای جزئیات بیشتر، [API Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage) را ببینید.

### دسترسی به قابلیت‌های fenced frame در شیء `Fence`

در داخل اسنادی که در `<fencedframe>`ها تعبیه شده‌اند، جاوااسکریپت به ویژگی {{domxref("Window.fence")}} دسترسی دارد که یک نمونه {{domxref("Fence")}} را برای آن سند برمی‌گرداند. این شیء شامل چند تابع است که به‌طور خاص به قابلیت‌های API fenced frame مرتبط هستند.
به عنوان مثال، {{domxref("Fence.reportEvent()")}} راهی برای آغاز ارسال داده‌های گزارش از طریق یک [beacon](/en-US/docs/Web/API/Beacon_API) به یک یا چند URL مشخص فراهم می‌کند تا بازدیدها و کلیک‌های آگهی گزارش شوند.

### سیاست مجوزها (Permissions policy)

فقط ویژگی‌های خاصی که برای استفاده در `<fencedframe>`ها طراحی شده‌اند می‌توانند از طریق سیاست‌های مجوز (permissions policies) تنظیم‌شده روی آن‌ها فعال شوند؛ سایر ویژگی‌های کنترل‌شده توسط سیاست در این زمینه در دسترس نیستند. برای جزئیات بیشتر، [سیاست‌های مجوز موجود برای fenced frameها](/en-US/docs/Web/HTML/Reference/Elements/fencedframe#permissions_policies_available_to_fenced_frames) را ببینید.

### هدرهای HTTP

یک هدر {{httpheader("Sec-Fetch-Dest")}} با مقدار `fencedframe` برای هر درخواستی که از داخل یک `<fencedframe>` ارسال می‌شود، از جمله `<iframe>`های فرزند تعبیه‌شده در یک `<fencedframe>`، تنظیم خواهد شد.

```http
Sec-Fetch-Dest: fencedframe
```

سرور باید برای هر سندی که قرار است در یک `<fencedframe>` یا `<iframe>` تعبیه‌شده در یک `<fencedframe>` بارگذاری شود، یک هدر پاسخ {{httpheader("Supports-Loading-Mode")}} با مقدار `fenced-frame` تنظیم کند.

```http
Supports-Loading-Mode: fenced-frame
```

سایر اثرات fenced frameها بر هدرهای HTTP به شرح زیر است:

- [نشانه‌های مشتری عامل کاربر (User-Agent Client Hints)](/en-US/docs/Web/HTTP/Guides/Client_hints#user_agent_client_hints) در داخل fenced frameها در دسترس نیستند، زیرا آن‌ها به واگذاری [سیاست مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) متکی هستند که می‌تواند برای نشت داده مورد سوءاستفاده قرار گیرد.
- تنظیمات سخت‌گیرانه [`Cross-Origin-Opener-Policy`](/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Opener-Policy) در زمینه‌های مرور جدیدی که از داخل fenced frameها باز می‌شوند اعمال می‌شود، در غیر این صورت می‌توان از آن‌ها برای نشت اطلاعات به مبدأهای دیگر استفاده کرد. هر پنجره جدیدی که از داخل یک fenced frame باز شود، [`rel="noopener"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noopener) و `Cross-Origin-Opener-Policy: same-origin` را تنظیم می‌کند تا اطمینان حاصل شود که {{domxref("Window.opener")}} مقدار `null` برمی‌گرداند و آن را در گروه زمینه مرور خودش قرار می‌دهد.
- [`Content-Security-Policy: fenced-frame-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/fenced-frame-src) برای مشخص کردن منابع معتبر برای زمینه‌های مرور تودرتو که در عناصر `<fencedframe>` بارگذاری می‌شوند، اضافه شده است.
- تنظیمات سفارشی [`Content-Security-Policy: sandbox`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/sandbox) نمی‌توانند توسط fenced frameها به ارث برده شوند تا مشکلات حریم خصوصی کاهش یابد. برای بارگذاری یک fenced frame، باید هیچ CSP سندباکس (sandbox) مشخص نکنید (که مقادیر زیر را به صورت ضمنی شامل می‌شود)، یا مقادیر سندباکس زیر را مشخص کنید:
  - `allow-same-origin`
  - `allow-forms`
  - `allow-scripts`
  - `allow-popups`
  - `allow-popups-to-escape-sandbox`
  - `allow-top-navigation-by-user-activation`

### رویدادهای `beforeunload` و `unload`

رویدادهای [`beforeunload`](/en-US/docs/Web/API/Window/beforeunload_event) و [`unload`](/en-US/docs/Web/API/Window/unload_event) در fenced frameها فعال نمی‌شوند، زیرا آن‌ها می‌توانند اطلاعاتی را به شکل برچسب زمانی حذف صفحه (deletion timestamp) نشت دهند. پیاده‌سازی‌ها در تلاشند تا حد امکان نشت‌های بالقوه را از بین ببرند.

## رابط‌ها (Interfaces)

- {{domxref("FencedFrameConfig")}}
  - : نماینده ناوبری یک {{htmlelement("fencedframe")}} است، یعنی اینکه چه محتوایی در آن نمایش داده خواهد شد. یک `FencedFrameConfig` از منبعی مانند [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) بازگردانده می‌شود و به عنوان مقدار {{domxref("HTMLFencedFrameElement.config")}} تنظیم می‌شود.
- {{domxref("Fence")}}
  - : شامل چند تابع مرتبط با قابلیت‌های fenced frame است. فقط برای اسنادی که در داخل یک `<fencedframe>` تعبیه شده‌اند در دسترس است.
- {{domxref("HTMLFencedFrameElement")}}
  - : نماینده یک عنصر `<fencedframe>` در جاوااسکریپت است و ویژگی‌هایی برای پیکربندی آن فراهم می‌کند.

### افزونه‌هایی بر سایر رابط‌ها

- {{domxref("Navigator.deprecatedReplaceInURN()")}}
  - : رشته‌های مشخص‌شده را در داخل URL نگاشت‌شده‌ای که مربوط به یک URN مبهم یا ویژگی داخلی `url` در `FencedFrameConfig` است، جایگزین می‌کند.
- {{domxref("Window.fence")}}
  - : یک نمونه از شیء {{domxref("Fence")}} را برای زمینه سند فعلی برمی‌گرداند. فقط برای اسنادی که در داخل یک `<fencedframe>` تعبیه شده‌اند در دسترس است.

## ثبت‌نام و تست محلی

برخی از ویژگی‌های API که {{domxref("FencedFrameConfig")}} ایجاد می‌کنند، مانند {{domxref("Navigator.runAdAuction()")}} ([Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience)) و {{domxref("WindowSharedStorage.selectURL()")}} ([Shared Storage API](/en-US/docs/Web/API/Shared_Storage_API))، و همچنین سایر ویژگی‌ها مانند {{domxref("Fence.reportEvent()")}}، از شما می‌خواهند که سایت خود را در یک [فرآیند ثبت‌نام Privacy Sandbox](/en-US/docs/Web/Privacy/Guides/Privacy_sandbox#enrollment) ثبت کنید. اگر این کار را انجام ندهید، فراخوانی‌های API با یک هشدار در کنسول شکست خواهند خورد.

> [!NOTE]
> در Chrome، همچنان می‌توانید کد fenced frame خود را بدون ثبت‌نام به صورت محلی آزمایش کنید. برای امکان تست محلی، پرچم توسعه‌دهنده Chrome زیر را فعال کنید:
>
> `chrome://flags/#privacy-sandbox-enrollment-overrides`

## مثال‌ها

دموهای زیر همگی از `<fencedframe>`ها استفاده می‌کنند:

- [دموهای Shared Storage API](https://shared-storage-demo.web.app/) (که شامل چند مثال Private Aggregation API نیز می‌شود)
- [دموی Protected Audience API](https://protected-audience-demo-advertiser.web.app/)

## مشخصات

{{Specifications}}

### مواضع استانداردها

یک فروشنده مرورگر با این [مشخصات مخالفت](/en-US/docs/Glossary/Web_standards#opposing_standards) کرده است.
مواضع شناخته‌شده استانداردها به شرح زیر است:

- Mozilla (Firefox): [Negative](https://github.com/mozilla/standards-positions/issues/781)

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com