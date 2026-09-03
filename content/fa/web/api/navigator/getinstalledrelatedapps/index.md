---
title: "Navigator: getInstalledRelatedApps() method"
short-title: getInstalledRelatedApps()
slug: Web/API/Navigator/getInstalledRelatedApps
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Navigator.getInstalledRelatedApps
---

{{APIRef}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`getInstalledRelatedApps()`** یک Promise برمی‌گرداند که در صورت موفقیت با آرایه‌ای از اشیاء نمایانگر هر برنامهٔ مرتبط مخصوص پلتفرم یا [برنامهٔ وب پیشرونده](/en-US/docs/Web/Progressive_web_apps) که کاربر نصب کرده است، مقداردهی می‌شود. می‌توان از این روش برای شخصی‌سازی محتوا استفاده کرد؛ برای مثال اگر برنامهٔ مخصوص پلتفرم و/یا PWA از قبل نصب شده باشد، بنرهای «برنامهٔ ما را نصب کنید» از برنامهٔ وب حذف می‌شوند.

> [!NOTE]
> این روش باید در یک [زمینهٔ امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) سطح بالا فراخوانی شود؛ یعنی نباید داخل یک {{htmlelement("iframe")}} تعبیه شده باشد.

## توضیحات

`getInstalledRelatedApps()` را می‌توان برای بررسی نصب بودن برنامه‌های Universal Windows Platform (UWP)، برنامه‌های اندروید و PWAهایی که با برنامهٔ وب فراخوانندهٔ این روش مرتبط هستند استفاده کرد.

برای مرتبط کردن برنامهٔ وب فراخواننده با یک برنامهٔ مخصوص پلتفرم یا PWA، دو کار باید انجام شود:

1. برنامهٔ وب فراخواننده باید در عضو [`related_applications`](/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/related_applications) از [فایل مانیفست](/en-US/docs/Web/Progressive_web_apps/Manifest) آن مشخص شده باشد.
2. رابطهٔ برنامهٔ مخصوص پلتفرم یا PWA با برنامهٔ فراخواننده باید تعریف شده باشد.

تعریف این رابطه بسته به نوع برنامه به روش‌های متفاوتی انجام می‌شود:

- یک برنامهٔ اندروید این کار را از طریق [سیستم Digital Asset Links](https://developers.google.com/digital-asset-links/v1/getting-started) انجام می‌دهد.
- یک برنامهٔ Windows UWP این کار را از طریق [گرداننده‌های URI (URI Handlers)](https://learn.microsoft.com/en-us/windows/apps/develop/launch/web-to-app-linking) انجام می‌دهد.
- یک PWA این کار را از طریق موارد زیر انجام می‌دهد:
  - یک ورودی خودتعریف‌شده در عضو `related_applications` مانیفست خودش، با مشخص کردن ویژگی‌های `platform` و `id`؛ در موردی که یک PWA در همان محدوده (scope) بررسی می‌کند که آیا روی پلتفرم زیرین نصب شده است.
  - یک فایل `assetlinks.json` در پوشهٔ [`/.well-known/`](https://datatracker.ietf.org/doc/html/rfc5785) آن؛ در موردی که برنامه‌ای خارج از محدودهٔ آن PWA بررسی می‌کند که آیا روی اندروید نصب شده است.

برای جزئیات بیشتر دربارهٔ نحوهٔ برخورد با هر یک از این موارد، به [آیا برنامهٔ شما نصب است؟ getInstalledRelatedApps() به شما خواهد گفت!](https://developer.chrome.com/docs/capabilities/get-installed-related-apps) مراجعه کنید.

> [!NOTE]
> بیشتر مرورگرهای پشتیبان، هنگام شناسایی یک PWA قابل نصب، رابط کاربری نصب خودشان را ارائه می‌دهند؛ اگر آن PWA از قبل نصب شده باشد این رابط ظاهر نمی‌شود — به [قابل نصب کردن PWAها > نصب از وب](/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable#installation_from_the_web) مراجعه کنید. می‌توان با رویداد {{domxref("Window.beforeinstallprompt_event", "beforeinstallprompt")}} از نمایش این رابط جلوگیری کرد. همچنین می‌توان این رویداد را با `getInstalledRelatedApps()` ترکیب کرد تا بر اساس در دسترس بودن یک برنامهٔ مخصوص پلتفرم، رابط نصب نمایش داده نشود. برای اطلاعات مفید بیشتر به [راه‌اندازی نصب از PWA خود](/en-US/docs/Web/Progressive_web_apps/How_to/Trigger_install_prompt#responding_to_platform-specific_apps_being_installed) مراجعه کنید.

## نحو

```js-nolint
getInstalledRelatedApps()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{JSxRef("Promise")}} که با آرایه‌ای از اشیاء نمایانگر هر برنامهٔ مرتبط نصب‌شده مقداردهی می‌شود. هر شیء می‌تواند ویژگی‌های زیر را داشته باشد:

- `id` {{optional_inline}}
  - : یک رشته که شناسهٔ استفاده‌شده برای نمایش برنامه در پلتفرم مشخص‌شده را نشان می‌دهد. شکل دقیق این رشته بسته به پلتفرم متفاوت خواهد بود.
- `platform`
  - : یک رشته که [پلتفرم](https://github.com/w3c/manifest/wiki/Platforms) (اکوسیستم یا سیستم‌عامل) مرتبط با برنامه را نشان می‌دهد. این مقدار می‌تواند یکی از موارد زیر باشد:
    - `"chrome_web_store"`: یک برنامه از [Google Chrome Web Store](https://chromewebstore.google.com/).
    - `"play"`: یک برنامه از [Google Play Store](https://play.google.com/store/games).
    - `"chromeos_play"`: یک برنامه از [ChromeOS Play](https://support.google.com/googleplay/answer/7021273).
    - `"webapp"`: یک [برنامهٔ وب پیشرونده](/en-US/docs/Web/Progressive_web_apps).
    - `"windows"`: یک برنامه از [Windows Store](https://apps.microsoft.com/?rtc=1&hl=en-US&gl=US).
    - `"f-droid"`: یک برنامه از [F-Droid](https://f-droid.org/).
    - `"amazon"`: یک برنامه از [Amazon App Store](https://www.amazon.com/gp/browse.html?node=2350149011).
- `url` {{optional_inline}}
  - : یک رشته که URL مرتبط با برنامه را نشان می‌دهد. این معمولاً جایی است که می‌توانید اطلاعاتی دربارهٔ آن برنامه بخوانید و آن را نصب کنید.
- `version` {{optional_inline}}
  - : یک رشته که نسخهٔ برنامهٔ مرتبط را نشان می‌دهد.

اطلاعات برنامهٔ مرتبط باید قبلاً در عضو [`related_applications`](/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/related_applications) از [فایل مانیفست](/en-US/docs/Web/Progressive_web_apps/Manifest) برنامهٔ وب فراخواننده مشخص شده باشد.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : این روش در یک بافت مرور (browsing context) سطح بالا فراخوانی نشده است.

## مثال‌ها

```js
const relatedApps = await navigator.getInstalledRelatedApps();

// Dump all the returned related apps into a table in the console
console.table(relatedApps);

// Search for a specific installed platform-specific app
const psApp = relatedApps.find((app) => app.id === "com.example.myapp");

if (psApp && doesVersionSendPushMessages(psApp.version)) {
  // There's an installed platform-specific app that handles sending push messages
  // No need to handle this via the web app
  return;
}
```

> [!NOTE]
> در این مثال، `doesVersionSendPushMessages()` یک تابع فرضی تعریف‌شده توسط توسعه‌دهنده است؛ این تابع توسط مرورگر ارائه نمی‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [آیا برنامهٔ شما نصب است؟ getInstalledRelatedApps() به شما خواهد گفت!](https://developer.chrome.com/docs/capabilities/get-installed-related-apps)