---
title: "Background Fetch API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Background_Fetch_API"
translated_by: "n8n + AI"
---

---
title: Background Fetch API
slug: Web/API/Background_Fetch_API
page-type: web-api-overview
status:
  - experimental
browser-compat:
  - api.BackgroundFetchManager
  - api.BackgroundFetchRegistration
  - api.BackgroundFetchRecord
spec-urls: https://wicg.github.io/background-fetch/
---

{{DefaultAPISidebar("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

**Background Fetch API** روشی برای مدیریت دانلودهایی فراهم میکند که ممکن است زمان قابل توجهی طول بکشند، مانند فیلمها، فایلهای صوتی و نرمافزارها.

## مفهوم و کاربرد

هنگامی که یک برنامهٔ وب نیاز به دانلود فایل‌های بزرگ توسط کاربر دارد، این اغلب مشکلی ایجاد می‌کند: کاربر باید برای تکمیل دانلود، به صفحه متصل بماند. اگر اتصال را از دست بدهد، برگه را ببندد یا از صفحه خارج شود، دانلود متوقف می‌شود.

{{domxref("Background Synchronization API", "", "", "nocode")}} روشی برای سرویس‌ورکرها فراهم می‌کند تا پردازش را تا زمانی که کاربر متصل است به تأخیر بیندازند؛ با این حال نمی‌توان از آن برای کارهای طولانی‌مدت مانند دانلود یک فایل بزرگ استفاده کرد. Background Sync مستلزم آن است که سرویس‌ورکر تا تکمیل واکشی زنده بماند و برای صرفه‌جویی در عمر باتری و جلوگیری از کارهای ناخواسته در پس‌زمینه، مرورگر در نقطه‌ای کار را خاتمه خواهد داد.

Background Fetch API این مشکل را حل می‌کند. این API روشی ایجاد می‌کند که توسعه‌دهندهٔ وب بتواند به مرورگر بگوید برخی واکشی‌ها را در پس‌زمینه انجام دهد، مثلاً وقتی کاربر دکمه‌ای برای دانلود یک فایل ویدیویی کلیک می‌کند. مرورگر سپس واکشی‌ها را به شکلی قابل مشاهده برای کاربر انجام می‌دهد، پیشرفت را به کاربر نمایش می‌دهد و روشی برای لغو دانلود در اختیار او قرار می‌دهد. پس از تکمیل دانلود، مرورگر سرویس‌ورکر را باز می‌کند و در آن نقطه، برنامهٔ شما در صورت نیاز می‌تواند با پاسخ کاری انجام دهد.

Background Fetch API امکان انجام واکشی را فراهم می‌کند حتی اگر کاربر فرآیند را در حالت آفلاین شروع کند. به محض اتصال، عملیات آغاز می‌شود. اگر کاربر آفلاین شود، فرآیند تا زمانی که کاربر دوباره آنلاین شود متوقف می‌ماند.

## رابط‌ها

- {{domxref("BackgroundFetchManager")}} {{Experimental_Inline}}
  - : یک نگاشت که در آن کلیدها شناسه‌های واکشی پس‌زمینه و مقادیر اشیاء {{domxref("BackgroundFetchRegistration")}} هستند.
- {{domxref("BackgroundFetchRegistration")}} {{Experimental_Inline}}
  - : یک واکشی پس‌زمینه را نشان می‌دهد.
- {{domxref("BackgroundFetchRecord")}} {{Experimental_Inline}}
  - : یک درخواست و پاسخ واکشی تکی را نشان می‌دهد.
- {{domxref("BackgroundFetchEvent")}} {{Experimental_Inline}}
  - : نوع رویداد برای رویدادهای {{domxref("ServiceWorkerGlobalScope.backgroundfetchabort_event", "backgroundfetchabort")}} و {{domxref("ServiceWorkerGlobalScope.backgroundfetchclick_event", "backgroundfetchclick")}}
- {{domxref("BackgroundFetchUpdateUIEvent")}} {{Experimental_Inline}}
  - : نوع رویداد برای رویدادهای {{domxref("ServiceWorkerGlobalScope.backgroundfetchsuccess_event", "backgroundfetchsuccess")}} و {{domxref("ServiceWorkerGlobalScope.backgroundfetchfail_event", "backgroundfetchfail")}}

### افزونه‌های سایر رابط‌ها

- {{domxref("ServiceWorkerRegistration.backgroundFetch")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک ارجاع به شیء {{domxref("BackgroundFetchManager")}} برمی‌گرداند که عملیات واکشی پس‌زمینه را مدیریت می‌کند.
- رویداد {{domxref("ServiceWorkerGlobalScope/backgroundfetchabort_event", "backgroundfetchabort")}} {{Experimental_Inline}}
  - : هنگامی که یک عملیات واکشی پس‌زمینه توسط کاربر یا برنامه لغو شود، فعال می‌شود.
- رویداد {{domxref("ServiceWorkerGlobalScope/backgroundfetchclick_event", "backgroundfetchclick")}} {{Experimental_Inline}}
  - : هنگامی که کاربر روی رابط کاربری برای یک عملیات واکشی پس‌زمینه کلیک کرده باشد، فعال می‌شود.
- رویداد {{domxref("ServiceWorkerGlobalScope/backgroundfetchfail_event", "backgroundfetchfail")}} {{Experimental_Inline}}
  - : هنگامی که حداقل یکی از درخواست‌ها در یک عملیات واکشی پس‌زمینه ناموفق باشد، فعال می‌شود.
- رویداد {{domxref("ServiceWorkerGlobalScope/backgroundfetchsuccess_event", "backgroundfetchsuccess")}} {{Experimental_Inline}}
  - : هنگامی که همهٔ درخواست‌ها در یک عملیات واکشی پس‌زمینه موفق باشند، فعال می‌شود.

## نمونه‌ها

قبل از استفاده از Background Fetch، پشتیبانی مرورگر را بررسی کنید.

```js
if (!("BackgroundFetchManager" in self)) {
  // Provide fallback downloading.
}
```

استفاده از Background Fetch نیاز به یک سرویس‌ورکر ثبت‌شده دارد. سپس برای انجام واکشی، `backgroundFetch.fetch()` را فراخوانی کنید. این یک promise برمی‌گرداند که با یک {{domxref("BackgroundFetchRegistration")}} حل می‌شود.

یک واکشی پس‌زمینه ممکن است چند فایل را واکشی کند. در مثال ما، واکشی یک MP3 و یک JPEG را درخواست می‌کند. این امکان را فراهم می‌کند که یک بسته از فایل‌ها که کاربر آن را به عنوان یک مورد می‌بیند (مثلاً یک پادکست و جلد آن) یکجا دانلود شود.

```js
navigator.serviceWorker.ready.then(async (swReg) => {
  const bgFetch = await swReg.backgroundFetch.fetch(
    "my-fetch",
    ["/ep-5.mp3", "ep-5-artwork.jpg"],
    {
      title: "Episode 5: Interesting things.",
      icons: [
        {
          sizes: "300x300",
          src: "/ep-5-icon.png",
          type: "image/png",
        },
      ],
      downloadTotal: 60 * 1024 * 1024,
    },
  );
});
```

می‌توانید نمونه‌های کد بیشتر و یک نسخهٔ نمایشی را در [معرفی Background Fetch](https://developer.chrome.com/blog/background-fetch/) بیابید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [معرفی Background Fetch](https://developer.chrome.com/blog/background-fetch/)
- [Background Fetch - HTTP 203](https://www.youtube.com/watch?v=cElAoxhQz6w)