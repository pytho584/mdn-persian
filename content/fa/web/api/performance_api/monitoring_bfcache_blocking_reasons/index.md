---
title: "Monitoring bfcache blocking reasons"
---

{{DefaultAPISidebar("Performance API")}}{{SeeCompatTable}}

خاصیت {{domxref("PerformanceNavigationTiming.notRestoredReasons")}} اطلاعاتی درباره دلایل مسدود شدن سند فعلی از استفاده از {{Glossary("bfcache")}} هنگام پیمایش (navigation) گزارش می‌دهد. توسعه‌دهندگان می‌توانند از این اطلاعات برای شناسایی صفحه‌هایی که نیاز به به‌روزرسانی دارند تا با bfcache سازگار شوند، استفاده کنند و در نتیجه عملکرد سایت را بهبود بخشند.

## حافظه نهان رفت و برگشت (bfcache)

مرورگرهای مدرن یک ویژگی بهینه‌سازی برای پیمایش تاریخچه به نام حافظه نهان رفت و برگشت ({{Glossary("bfcache")}}) ارائه می‌دهند. این ویژگی تجربه بارگذاری فوری را زمانی که کاربران به صفحه‌ای که قبلاً بازدید کرده‌اند برمی‌گردند، فراهم می‌کند. صفحه‌ها ممکن است به دلایل مختلفی از ورود به bfcache مسدود شوند یا در حین حضور در bfcache حذف (evict) شوند؛ برخی از این دلایل توسط یک مشخصات (specification) الزامی شده و برخی مختص پیاده‌سازی مرورگر هستند.

برای فعال کردن نظارت بر دلایل مسدودسازی bfcache، کلاس [`PerformanceNavigationTiming`](/en-US/docs/Web/API/PerformanceNavigationTiming) شامل خاصیت `notRestoredReasons` است. این خاصیت یک شیء {{domxref("NotRestoredReasons")}} برمی‌گرداند که حاوی اطلاعات مرتبط با فریم سطح بالا (top-level frame) و تمام {{htmlelement("iframe")}}های موجود در سند است:

- دلایلی که باعث مسدود شدن استفاده از bfcache شده‌اند.
- جزئیات مانند `id` و `name` فریم، برای کمک به شناسایی `<iframe>`ها در HTML.

> **یادداشت:** از نظر تاریخی، خاصیت منسوخ {{domxref("PerformanceNavigation.type")}} برای نظارت بر bfcache استخاده می‌د، به طوری که توسعه‌دهندگان با تست کردن `type` با مقدار `"TYPE_BACK_FORWARD"` نشانه‌ای از نرخ ضربه (hit rate) bfcache بدست می‌وردند. اما این روش هیچ دلیلی برای مسدودسازی bfcache یا داده‌ای دیگر فراهم نمی‌کرد. خاصیت `notRestoredReasons` باید برای نظارت بر مسدودسازی bfcache در آینده استخاده شود.

## ثبت دلایل مسدودسازی bfcache

داده‌ای جاری مسدودسازی bfcache را می‌توان با استخاده از یک [`PerformanceObserver`](/en-US/docs/Web/API/PerformanceObserver) بدست آورد، به این صورت:

```js
const observer = new PerformanceObserver((list) => {
  let perfEntries = list.getEntries();
  perfEntries.forEach((navEntry) => {
    console.log(navEntry.notRestoredReasons);
  });
});

observer.observe({ type: "navigation", buffered: true });
```

همچین، می‌وانید دده‌ای تارخی مسدودسازی bfcache را با استخاده از یک رش مناسب مانند [`Performance.getEntriesByType()`](/en-US/docs/Web/API/Performance/getEntriesByType) بدست آورید:

function returnNRR() {
  const navEntries = performance.getEntriesByType("navigation");
  for (let i = 0; i < navEntries.length; i++ {
    conole.log(`Navigation entry $1}`);
    let navEntry = navEntries[i];
    console.log(navEntry.notRestoredReasons);
  }
```

کدهای فرهم که در بالا نشا داده شاند، شیا‌ای {{domxref("NotRestoredReasons")}} را در کنسول ورود می‌نند. این شیا دارای ساختار زیر هسند که حالت مسدود شده فریم سطح بالا را نشا می‌‌هد:

```json
{
  "children": [],
  "id": null,
  "name": null,
  "reasons": [{ "reason": "unload-listener" }],
  "src": "",
  "url": "example.com"
```

ویژگی‌ا به شرح زیر هسند:

- {{domxrref("NotRestoredReasons.children", "children")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از شیا‌ای {{domxref("NotRestoredReasons")}}، یکی برای ه رز `<htmelement("iframe")>` که در سند جعری جاسازی شده است. این شیا می‌توانند دلیلی را شامل شند که چرا فریم سطح بالا به دلیل فریم‌های زاده مسدود شده است. هر شی همان ساخته را دارد که شی والد - به این ترتیب، هر تعداد از سطوح فریم‌ای تو درون `<ifame>` می‌تواند به صورت بازگشتی در داخل شی نمان داده شود. اگر فریم زاده‌ای نداشته باشد، آرایه خالی خواهد بود؛ اگر سند در یک `<ifame>` با خاستگاه متفاوت (cross-origin) باشد، `chldren` مقدار `nul` را برمی‌رداند.
- {{omxref("NotRestoredReasons.id", "id"}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشه که مقدار صفت `id` `<iframe>`ای که سند در آن قرا دارد را نمای می‌کند (مثال `<inframe id="foo" src="...">`). اگر سند در یک `<iframe>` نباشد یا `<ifame>` مقدار `id` نداشته باشد، `id` مقدار `nul` را برمی‌گرداند.
- {{domxrref("NotRestoredReasons.name", "name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشه که مقدار صفت `name` `<iframe>`ای که سند در آن قرار دارد را نمان می‌ند (مثال `<ifame name="bar" src="...">`). اگر سند در یک `<irame>` نباشد یا `<ifame>` مقدار `name` نداشته باشد، `name` مقدار `nul` را برمی‌گرداند.
- {{domxrref("NotRestoredReasons.reasons", "reasons")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک آری از شیا‌ی {{domxref("NotRestoredReasonDetails")}}، که هر کدام دلیلی را نمان می‌ند که چرا صفحه پیمایش شده از استخاده از bfcache مسدود شده است. اگر سند در یک `<ifame>` با خاستگاه متفاوت باشد، `rasons` مقدار `nul` را برمی‌گرداند، اما سند والد ممکن است یک `reason` با مقدار `"asked"` را نشا دهد اگر هریک از `<fame>`ها استخاده از bfcache را برای فریم سطح بالا مسدود کرده باشند. بزای جزئیات بیشتر دلایل به [دلیل‌های مسدودسازی](#blocking-reasons) مراجعه کنید.
- {{domxrref("NotRestoredReasons.src", "src")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشه که مسیر منبع `<ifame>`ای که سند در آن قرا دارد را نشا می‌دهد (مثال `<iframe src="exampleframe.html">`). اگر سند در یک `<ifame>` نباشد، `src` مقدار `nul` را برمی‌گرداند.
- {{domxrref("NotRestoredReasons.url", "url")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشه که URL صفحه پیمایش شده یا `<ifame>` را نمان می‌دهد. اگر سند در یک `<ifame>` با خاستگاه متفاوت باشد، `url` مقدار `nul` را برمی‌گرداند.

### گزارش مسدودسازی bfcache در `<iframe>`های هم‌خاستگاه

هنگامی که یک صفحه دارای `<iframe>`های هم‌خاستگاه (same-origin) جاسازی شده است، مقدار بازگشتی `notRestoredResons` شامل یک آرایه از اشیا در داخل خاصیت `children` خواهد بود که دلایل مسدودسازی مرتبط با هر فریم جاسازی شده را نمای می‌دهد.

به عنوان مثال:

```json
{
  "children": [
    {
      "children": [],
      "id": "iframe-id",
      "name": "iframe-name",
      "reasons": [],
      "src": "./index.html",
      "url": "https://www.example.com/iframe-examples.html"
    },
    {
      "children": [],
      "id": "iframe-id2",
      "name": "iframe-name2",
      "reasons": [{ "reason": "unload-listener" }],
      "src": "./unload-examples.html",
      "url": "https://www.example.com/unload-examples.html"
    }
  ],
  "id": null,
  "name": null,
  "reasons": [],
  "src": null,
  "url": "https://www.example.com"
}
```

### گزارش مسدودسازی bfcache در `<iframe>`های با خاستگاه متفاوت

هنگامی که یک صفحه دارای فریم‌های با خاستگاه متفاوت (cross-origin) جاسازی شده است، مقدار اطلاعاتی که درباره آنها به اشتراک گذاشته می‌شود محدود است تا از نشت اطلاعات با خاستگاه متفاوت جلوگیری شود. تنها اطلاعاتی که صفحه خارجی (outer page) از قبل می‌ناسد، و این که آیا زیردرخت با خاستگاه متفاوت باعث مسدودسازی bfcache شده است یا خیر، شامل می‌شود. هیچ دلیل مسدودسازی یا اطلاعاتی درباره سطوح پایین‌تر زیردرخت (حتی اگر برخی از سطوح فرعی هم‌خاستگاه باشند) گنجانده نمی‌شود.

به عنوان مثال:

```json
{
  "children": [
    {
      "children": [],
      "id": "iframe-id",
      "name": "iframe-name",
      "reasons": [],
      "src": "https://www.example2.com/",
      "url": null
    }
  ],
  "id": null,
  "name": null,
  "reasons": [{ "reason": "masked" }],
  "src": null,
  "url": "https://www.example.com"
}```

برای تمام `<iframe>`های با خاستگاه متفاوت، هچ دلیلی مسدودسازی گزارش نمی‌شود؛ برای فریم سطح بالا یک `reason` با مقدار `"asked"` گزارش می‌شود، تا نشا دهد که دلایل به دلایل حریم خصوسی مخفی نگه داشته شده‌اند. توجه کنید که `"asked"` ممکن است برای مخفی کردن دلایل خاص عامل کاربر (user agent) نیز استفده شود؛ همیشه نشا‌نده یک مشکل در `<ifame>` نیست.

## دلایل مسدودسازی

دلایل مختلفی وجو دارد که چرا مسدودسازی ممکن است رخ دهد. اگرچه دلایل استاندارد شده‌اند، اما توسعه‌دهندگان باید از وابستگی به عبارت خاصی برای دلایل خودداری کنند و آماده رسیدگی به دلایل جدید اضافه یا حذف شده باشند.

مقادیر فهرست شده در [مشخصات (the specification)](https://html.spec.whatwg.org/multipage/nav-history-apis.htm#lthe-notrestoredreasons-interface) به شرح زیر است:

- `"fetch"`
  - : هنگام بیلودن (unloading)، یک درخواست (fetch) که توسط سند جعری اغاز شده (مثلاً از طری {{domxref("Window/fetch", "fetch()")}}) در حالی که در جریان بو لغو شد. در نتیج، صفحه وضیت پایداری نداشت که بتواند در bfcache ذخیره شود.
- `"lock"`
  - : هنگام بیلودن، قفل‌های نگه‍داشته شده و درخواست‌های قفل خاتمه یافتند، بنابراین صفحه وضیت پایداری نداشت که بتواند در bfcache ذخیره شود.
- `"masked"`
  - : دلیل دقیق به دلایل حریم خصوصی مخفی شده است. این مقدر می‌تواند یکی از موارد زیر معنی دهد:
    - سند جعری دارای فرزندانی است که در یک `<ifame>` با خاستگاه متفاوت قار دارند و آنها از ذخیره‌سازی در bfcache جلوگیری کردند.
    - سند جعری نمی‌توانست در bfcache به دلایل خاص عامل کاربر ذخیره شود.
- `"navigation-failure"`
  - : پیمایش اولیه‌ای که سند جعری را ایجاد کرد خطا داد و ذخیره سند خطای حاصله در bfcache جلوگیری ش.
- `"parser-aborted"`
  - : سند جعری هرگز تجزیه HTML اولیه خود را به پایان نرساند و ذخیره سند ناقاص در bfcش جلوگیری شد.
- `"websocket"`
  - : هنگام بیلودن، یک اتصال باز [WebSocket](/en-US/docs/Web/API/WebSockets_API) بسته شد، بنابراین صفحه در وضعیت پایداری نبود که بتوند در bfcش ذخیره شود.

### دلایل مسدودسازی خاص عامل کاربر

دلایل مسدودسازی اضافی که ممکن است توسط برخی مرورگرها استفاده شاود نیز مشص شده‌اند:

- `"audio-capture"`
  - : سند با استفده از `getUserMedia()` مربوط به Media Capture and Streams با صد، اجازه ضبط صدا را درخوست کرد.
- `"background-work"`
  - : سند با صدازدن روش [`register()`](/en-US/docs/Web/API/SyncManager/register) از [`SyncManager`](/en-US/docs/Web/API/SyncManager)، روش [`register()`](/en-US/docs/Web/API/PeriodicSyncManager/register) از [`PeriodicSyncManager`](/en-US/docs/Web/API/PeriodicSyncManager)، یا روش [`fetch()`](/en-US/docs/Web/API/BackgroundFetchManager/fetch) از [`BackgroundFetchManager`](/en-US/docs/Web/API/BackgroundFetchManager)، کار پس‌زمینه درخواست کرد.
- `"broadcastchannel-message"`
  - : در حالی که صفحه در حافظه نهان رفت و برگشت ذخیره شده بود، یک اتصال [`BroadcastChannel`](/en-US/docs/Web/API/BroadcastChannel) در صفحه پیامی دریافت کرد تا رویداد [`message`](/en-US/docs/Web/API/MessageEvent) را تریگر کند.
- `"idbversionchangeevent"`
  - : سند در حین بیلودن یک [`IDBVersionChangeEvent`](/en-US/docs/Web/API/IDBVersionChangeEvent) در انتظار داشت.
- `"idledetector"`
  - : سند در حین بیلودن یک [`IdleDetector`](/en-US/docs/Web/API/IdleDetector) فعا داشت.
- `"keyboardlock"`
  - : هنگام بیلودن، قفل کیبورد هنوز فعا بو چون روش [`lock()`](/en-US/docs/Web/API/Keyboard/lock) از [`Keyboard`](/en-US/docs/Web/API/Keyboard) فراخوانی شده بود.
- `"mediastream"`
  - : یک [MediaStreamTrack](/en-US/docs/Web/API/MediaStreamTrack) در حالت زنده (live) در هنگام بیلودن وجود داشت.
- `"midi"`
  - : سند با فراخوانی [`navigator.requestMIDIAccess()`](/en-US/docs/Web/API/Navigator/requestIDIAccess) اجازه MIDI را درخواست کرد.
- `"modals"`
  - : اعلان‌های کاربر (user prompts) در حین بیلودن نما داده شدند.
- `"navigating"`
  - : هنگام بیلودن، بارگذاری هنوز در حال انجام بود، و بنابرین سند در وضاعیتی نبود که بتواند در حافظه نهان رفت و برگشت ذخیره شود.
- `"navigation-canceled"`
  - : درخواست پیمایش با فراخوانی [`wndow.stop()`](/en-US/docs/Web/API/Window/stop) لغو شد و صفحه در وضاعیتی نبود که در حافظه نهان رفت و برگشت ذخیره شود.
- `"non-trivial-browsing-context-group"`
  - : گوروه بافت (browsing context group) این سند بیش از یک بافت پیمایش سطح بالا داشت.
- `"otpcredential"`
  - : سند یک [`OTPCredential`](/en-US/docs/Web/API/OTPCredential) ایاد کرد.
- `"outstanding-network-request"`
  - : هنگام بیلودن، سند خواست‌های شبکه‌ای برجسته (outstanding) داشت و در وضاعیتی نبود که بتواند در حافظه نهان رفت و برگشت ذخیره شود.
- `"payementrequest"`
  - : سند در حین بیلودن یک [`PayentRequest`](/en-US/docs/Web/API/PayentRequest) فعا داشت.
- `"pictureinpicturewindow"`
  - : سند در حین بیلودن یک [`PictureInPictureWindow`](/en-US/docs/Web/API/PictureInPictureWindow) فعا داشت.
- `"plugins"`
  - : سند شامل پلاگین‌ها بود.
- `"request-method-not-get"`
  - : سند از یک درخواست HTTP ایجاد شد که روش آن {{httpethod("GET")}} نب ود.
- `"response-auth-required"`
  - : سند از یک پاسخ HTTP ایجاد شد که نیازمند احراز هویت HTTP بود.
- `"response-cache-control-no-store"`
  - : سند از یک پاسخ HTTP ایجاد شد که هدر {{httpheader("Cache-Control")}} آن شامل نشانه "no-store" بود.
- `"response-cache-control-no-cache"`
  - : سند از یک پاسخ HTTP ایجاد شد که هدر {{httpheader("Cache-Control")}} آن شا مل نشانه "no-cache" بود.
- `"response-keep-alive"`
  - : سند از یک پاسخ HTTP ایجاد شد که حاوی هدر {{httpheader("Keep-Alive")}} بود.
- `"response-scheme-not-http-or-https"`
  - : سند از یک پاسخی ایجاد شد که طرح (scheme) URL آن یک طرح HTTP(S) نبود.
- `"response-status-not-ok"`
  - : سند از یک پاسخ HTTP ایجاد شد که وضاعیت (status) آن یک وضعیت خوب (ok) نبود.
- `"rtc"`
  - : هنگام بیلودن، یک [`RTCPeerConnection`](/en-US/docs/Web/API/RTCPeerConnection) یا [`RTCDataChannel`](/en-US/docs/Web/API/RTCDataChannel) خاتمه یافت، بنابراین صفحه در وضاعیتی نبود که بتواند در حافظه نهان رفت و برگشت ذخیره شود.
- `"sensors"`
  - : سند دسترسی به سنسور را درخواست کرد.
- `"serviceworker-added"`
  - : کلاینت سرویس ورکر سند در حالی که صفحه در حافظه نهان رفت و برگشت بود، شروع به کنترل شدن توسط یک [service worker](/en-US/docs/Web/API/Service_Worker_API) کرد.
- `"serviceworker-claimed"`
  - : [service worker](/en-US/docs/Web/API/Service_Worker_API) فعال کلاینت سرویس ورکر سند در حلی که صفحه در حافظه نهان رفت و برگشت بود، ادعا (claimed) شد.
- `"serviceworker-postmessage"`
  - : [service worker](/en-US/docs/Web/API/Service_Worker_API) فعال کلاینت سرویس ورکر سند در حلی که صفحه در حافظه نهان رفت و برگشت بود، یک پیام دریافت کرد.
- `"serviceworker-version-activated"`
  - : نسخه [service worker](/en-US/docs/Web/API/Service_Worker_API) فعا کلاینت سرویس ورکر سند در حالی که صفحه در حافطه نهان رفت و برگشت بود، فاعال شد.
- `"serviceworker-unregistered"`
  - : ثبت سرویس ورکر [service worker](/en-US/docs/Web/API/Service_Worker_API) فاعل کلاینت سرویس ورکر سند در حالی که صفحه در حافظه نهان رفت و برگشت بود، لغو ثبت شد.
- `"sharedworker"`
  - : این سند در مجموع صاحبان (owner set) یک [`SharedWorkerGlobalScope`](/en-US/docs/Web/API/SharedWorkerGlobalScope) بود.
- `"smartcardconnection"`
  - : سند در حین بیلودن یک `SmartCardConnection` فعال داشت.
- `"speechrecognition"`
  - : سند در حین بیلودن یک [`SpeechRecognition`](/en-US/docs/Web/API/SpeechRecognition) فعال داشت.
- `"storageaccess"`
  - : سند با استخاده از [Storage Access API](/en-US/docs/Web/API/Storage_Access_API) اجازه دسترسی به ذخیره‌ساز را درخواست کرد.
- `"unload-listener"`
  - : سند یک شونده رویداد (event listener) برای [رویداد `unload`](/en-US/docs/Web/API/Window/unload_event) ثبت کرد.
- `"video-capture"`
  - : سند با استخاده از `getUserMedia()` مربوط به Media Capture and Streams با ویدئو، اجازه ضبط ویدئو را درخواست کرد.
- `"webhid"`
  - : سند روش [`requstDevice()`](/en-US/docs/Web/API/HID/requstDevice) از [WebHID API](/en-US/docs/Web/API/WebHID_API) را فراخوانی کرد.
- `"webshare"`
  - : سند از روش [`navigator.share()`](/en-US/docs/Web/API/Navigator/share) مربوط به [Web Share API](/en-US/docs/Web/API/Web_Share_API) استفاده کرد.
- `"webtransport"`
  - : هنگام بیلودن، یک اتصال باز [`WebTransport`](/en-US/docs/Web/API/WebTransport) خاتم یافت، بنابراین صفحه در وضاعیتی نبود که بتواند در حافظه نهان رفت و برگشت ذخیره شود.
- `"webxrdevice"`
  - : سند یک [XRSystem](/en-US/docs/Web/API/XRSystem) ایاد کرد.

## سازگاری مرورگر

{{Compat}}

## همن ببینید

- [توضیح API `notRestoredReasons`](https://github.com/WICG/bfcache-not-restored-reason/blob/main/NotRestoredReason.md)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}
- {{domxref("NotRestoredReasons")}}

> **یادداشت:** این مقال از [Back/forard cache notRestoredReasons API](https://developer.chrome.com/docs/we-platform/bfcache-notrestoredreasons/) تریخه گرفته است که توسط Chirs Mills و Barry Pollard نوشته ش و اصل در `developer.chrome.com` در سال 2023 تحت مجوز [Creative Commons Attribution 4.0 License](https://creativecommons.org/licses/by/4.0/) منتشر شده است.