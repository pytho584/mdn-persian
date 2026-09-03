---
title: "Navigator"
---

---
title: Navigator
slug: Web/API/Navigator
page-type: web-api-interface
browser-compat: api.Navigator
---

{{APIRef("DOM")}}

رابط **`Navigator`** نمایانگر وضعیت و هویت عامل کاربر (user agent) است. این رابط به اسکریپت‌ها امکان می‌دهد که از آن پرس‌وجو کنند و خود را برای انجام برخی فعالیت‌ها ثبت کنند.

یک شیء `Navigator` را می‌توان با استفاده از ویژگی فقط‌خواندنی {{domxref("window.navigator")}} به دست آورد.

## ویژگی‌های نمونه

هیچ ویژگی‌ای را به ارث نمی‌برد.

### ویژگی‌های استاندارد

- {{domxref("Navigator.audioSession")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("AudioSession")}} برمی‌گرداند که می‌توان از آن برای کنترل نحوه تعامل صدای برنامه وب با سایر صداهای در حال پخش روی دستگاه استفاده کرد.
- {{domxref("Navigator.bluetooth")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("Bluetooth")}} برای سند جاری برمی‌گرداند که دسترسی به قابلیت‌های [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) را فراهم می‌کند.
- {{domxref("Navigator.clipboard")}} {{ReadOnlyInline}} {{securecontext_inline}}
  - : یک شیء {{domxref("Clipboard")}} برمی‌گرداند که دسترسی خواندن و نوشتن به کلیپ‌بورد سیستم را فراهم می‌کند.
- {{domxref("Navigator.connection")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NetworkInformation")}} حاوی اطلاعاتی درباره اتصال شبکه دستگاه برمی‌گرداند.
- {{domxref("Navigator.contacts")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : رابط {{domxref('ContactsManager')}} را برمی‌گرداند که به کاربران اجازه می‌دهد ورودی‌هایی از فهرست مخاطبان خود انتخاب کرده و جزئیات محدودی از ورودی‌های انتخاب‌شده را با یک وب‌سایت یا برنامه به اشتراک بگذارند.
- {{domxref("Navigator.cookieEnabled")}} {{ReadOnlyInline}}
  - : اگر تنظیم یک کوکی نادیده گرفته شود `false` و در غیر این صورت `true` برمی‌گرداند.
- {{domxref("Navigator.credentials")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : رابط {{domxref("CredentialsContainer")}} را برمی‌گرداند که متدهایی برای درخواست اعتبارنامه و اطلاع‌دادن به عامل کاربر هنگام وقوع رویدادهای جالب مانند ورود یا خروج موفق را در معرض دید قرار می‌دهد.
- {{domxref("Navigator.deviceMemory")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : مقدار حافظه دستگاه را بر حسب گیگابایت برمی‌گرداند. این مقدار یک تقریب است که با گرد کردن به نزدیک‌ترین توان ۲ و تقسیم آن عدد بر ۱۰۲۴ به دست می‌آید.
- {{domxref("Navigator.devicePosture")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شیء {{domxref("DevicePosture")}} مرورگر را برمی‌گرداند که به توسعه‌دهندگان اجازه می‌دهد وضعیت فعلی دستگاه (یعنی اینکه viewport در حالت صاف یا تا شده است) را پرس‌وجو کرده و در پاسخ به تغییرات وضعیت، کد اجرا کنند.
- {{domxref("Navigator.geolocation")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("Geolocation")}} برمی‌گرداند که امکان دسترسی به موقعیت دستگاه را فراهم می‌کند.
- {{domxref("Navigator.gpu")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : شیء {{domxref("GPU")}} را برای بافت مرورگر جاری برمی‌گرداند. نقطه ورود به {{domxref("WebGPU_API", "WebGPU API", "", "nocode")}}.
- {{domxref("Navigator.hardwareConcurrency")}} {{ReadOnlyInline}}
  - : تعداد هسته‌های پردازنده منطقی موجود را برمی‌گرداند.
- {{domxref("Navigator.hid")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("HID")}} برمی‌گرداند که متدهایی برای اتصال به دستگاه‌های HID، فهرست‌کردن دستگاه‌های HID متصل شده، و رویدادگردان‌هایی برای دستگاه‌های HID متصل شده فراهم می‌کند.
- {{domxref("Navigator.ink")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("Ink")}} برای سند جاری برمی‌گرداند که دسترسی به قابلیت‌های [Ink API](/en-US/docs/Web/API/Ink_API) را فراهم می‌کند.
- {{domxref('Navigator.keyboard')}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref('Keyboard')}} برمی‌گرداند که دسترسی به توابعی برای دریافت نقشه‌های طرح‌بندی صفحه‌کلید و فعال‌سازی ضبط فشارهای کلید از صفحه‌کلید فیزیکی را فراهم می‌کند.
- {{domxref("Navigator.language")}} {{ReadOnlyInline}}
  - : یک رشته (string) نمایانگر زبان ترجیحی کاربر، معمولاً زبان رابط کاربری مرورگر، برمی‌گرداند. وقتی این مقدار ناشناخته باشد، مقدار `null` برگردانده می‌شود.
- {{domxref("Navigator.languages")}} {{ReadOnlyInline}}
  - : یک آرایه از رشته‌ها نمایانگر زبان‌های شناخته‌شده برای کاربر، به ترتیب اولویت، برمی‌گرداند.
- {{domxref("Navigator.locks")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("LockManager")}} برمی‌گرداند که متدهایی برای درخواست یک شیء {{domxref('Lock')}} جدید و پرس‌وجو برای یک شیء {{domxref('Lock')}} موجود فراهم می‌کند.
- {{domxref("Navigator.login")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : دسترسی به شیء {{domxref("NavigatorLogin")}} مرورگر را فراهم می‌کند که یک ارائه‌دهنده هویت فدرال (IdP) می‌تواند از آن برای تنظیم وضعیت ورود کاربر هنگام ورود یا خروج از IdP استفاده کند. برای جزئیات بیشتر به [Federated Credential Management (FedCM) API](/en-US/docs/Web/API/FedCM_API) مراجعه کنید.
- {{domxref("Navigator.maxTouchPoints")}} {{ReadOnlyInline}}
  - : حداکثر تعداد نقاط تماس لمسی همزمان را که توسط دستگاه جاری پشتیبانی می‌شود، برمی‌گرداند.
- {{domxref("Navigator.mediaCapabilities")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("MediaCapabilities")}} برمی‌گرداند که می‌تواند اطلاعاتی درباره قابلیت‌های رمزگشایی و رمزگذاری برای یک قالب مشخص و قابلیت‌های خروجی در معرض دید قرار دهد.
- {{domxref("Navigator.mediaDevices")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک ارجاع به یک شیء {{domxref("MediaDevices")}} برمی‌گرداند که سپس می‌تواند برای دریافت اطلاعات درباره دستگاه‌های رسانه‌ای موجود ({{domxref("MediaDevices.enumerateDevices()")}})، یافتن ویژگی‌های محدودکننده پشتیبانی‌شده برای رسانه در رایانه کاربر و عامل کاربر ({{domxref("MediaDevices.getSupportedConstraints()")}})، و درخواست دسترسی به رسانه با استفاده از {{domxref("MediaDevices.getUserMedia()")}} استفاده شود.
- {{domxref("Navigator.mediaSession")}} {{ReadOnlyInline}}
  - : شیء {{domxref("MediaSession")}} را برمی‌گرداند که می‌تواند برای ارائه فراداده‌ای استفاده شود که مرورگر می‌تواند از آن برای نمایش اطلاعات درباره رسانه‌ای که در حال پخش است به کاربر استفاده کند، مانند در یک رابط کاربری کنترل رسانه سراسری.
- {{domxref("Navigator.onLine")}} {{ReadOnlyInline}}
  - : یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا مرورگر به صورت آنلاین کار می‌کند یا خیر.
- {{domxref("Navigator.pdfViewerEnabled")}} {{ReadOnlyInline}}
  - : اگر مرورگر بتواند فایل‌های PDF را هنگام پیمایش به آنها به صورت درون‌خطی نمایش دهد `true`، و در غیر این صورت `false` برمی‌گرداند.
- {{domxref("Navigator.permissions")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("Permissions")}} برمی‌گرداند که می‌تواند برای پرس‌وجو و به‌روزرسانی وضعیت مجوز API‌های تحت پوشش [Permissions API](/en-US/docs/Web/API/Permissions_API) استفاده شود.
- {{domxref("Navigator.preferences")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : شیء {{domxref("PreferenceManager")}} جاری سند را برمی‌گرداند که دسترسی به اطلاعات [ترجیحات کاربر](/en-US/docs/Web/API/User_Preferences_API) را فراهم می‌کند.
- {{domxref("Navigator.presentation")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک ارجاع به API {{domxref("Presentation")}} برمی‌گرداند.
- {{domxref("Navigator.scheduling")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("Scheduling")}} برای سند جاری برمی‌گرداند.
- {{domxref("Navigator.serial")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("Serial")}} برمی‌گرداند که نقطه ورود به [Web Serial API](/en-US/docs/Web/API/Web_Serial_API) را برای فعال‌سازی کنترل پورت‌های سریال نشان می‌دهد.
- {{domxref("Navigator.serviceWorker")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("ServiceWorkerContainer")}} برمی‌گرداند که دسترسی به ثبت، حذف، ارتقا و ارتباط با اشیاء {{domxref("ServiceWorker")}} را برای [سند مرتبط](https://html.spec.whatwg.org/multipage/browsers.html#concept-document-window) فراهم می‌کند.
- {{domxref("Navigator.storage")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : شیء تکی {{domxref('StorageManager')}} را برمی‌گرداند که برای مدیریت مجوزهای ماندگاری و تخمین فضای ذخیره‌سازی موجود به صورت سایت‌به‌سایت/برنامه‌به‌برنامه استفاده می‌شود.
- {{domxref("Navigator.usb")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("USB")}} برای سند جاری برمی‌گرداند که دسترسی به قابلیت‌های [WebUSB API](/en-US/docs/Web/API/WebUSB_API) را فراهم می‌کند.
- {{domxref("Navigator.userActivation")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("UserActivation")}} حاوی اطلاعاتی درباره وضعیت فعال‌سازی کاربر پنجره جاری برمی‌گرداند.
- {{domxref("Navigator.userAgent")}} {{ReadOnlyInline}}
  - : رشته عامل کاربر (user agent string) را برای مرورگر جاری برمی‌گرداند.
- {{domxref("Navigator.userAgentData")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("NavigatorUAData")}} برمی‌گرداند که دسترسی به اطلاعاتی درباره مرورگر و سیستم عامل کاربر را فراهم می‌کند.
- {{domxref("Navigator.virtualKeyboard")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : یک ارجاع به API {{domxref("VirtualKeyboard")}} برمی‌گرداند تا کنترل صفحه‌کلید مجازی روی صفحه را به دست گیرد.
- {{domxref("Navigator.wakeLock")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک رابط {{domxref("WakeLock")}} برمی‌گرداند که می‌توانید از آن برای درخواست قفل بیدارماندن صفحه استفاده کرده و از کم‌نورشدن، خاموش‌شدن یا نمایش محافظ صفحه جلوگیری کنید.
- {{domxref("Navigator.webdriver")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا عامل کاربر توسط اتوماسیون کنترل می‌شود یا خیر.
- {{domxref("Navigator.windowControlsOverlay")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : رابط {{domxref("WindowControlsOverlay")}} را برمی‌گرداند که اطلاعاتی درباره هندسه نوار عنوان در برنامه‌های وب پیشرفته (Progressive Web Apps) دسکتاپ و یک رویداد برای اطلاع از تغییرات آن را در معرض دید قرار می‌دهد.
- {{domxref("Navigator.xr")}} {{ReadOnlyInline}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : شیء {{domxref("XRSystem")}} را برمی‌گرداند که نقطه ورود به [WebXR API](/en-US/docs/Web/API/WebXR_Device_API) را نشان می‌دهد.

### ویژگی‌های غیراستاندارد

- {{domxref("Navigator.buildID")}} {{ReadOnlyInline}} {{Non-standard_Inline}}
  - : شناسه ساخت (build identifier) مرورگر را برمی‌گرداند. در مرورگرهای مدرن، این ویژگی به عنوان یک اقدام حفظ حریم خصوصی، یک مهر زمانی ثابت برمی‌گرداند، مثلاً در Firefox 64 به بعد `20181001000000`.
- {{domxref("Navigator.globalPrivacyControl")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار بولی برمی‌گرداند که نشان‌دهنده رضایت کاربر برای به اشتراک‌گذاری یا فروش اطلاعاتش است.
- {{domxref("Navigator.standalone")}} {{Non-standard_Inline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد مرورگر در حالت مستقل (standalone) اجرا می‌شود یا خیر. فقط در Safari iOS اپل در دسترس است.

### ویژگی‌های منسوخ‌شده

- {{domxref("Navigator.activeVRDisplays")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک آرایه شامل هر شیء {{domxref("VRDisplay")}} که در حال حاضر ارائه می‌دهد ({{domxref("VRDisplay.isPresenting")}} `true` است) برمی‌گرداند.
- {{domxref("Navigator.appCodeName")}} {{ReadOnlyInline}}
  - : همیشه `'Mozilla'` را در هر مرورگری برمی‌گرداند.
- {{domxref("Navigator.appName")}} {{ReadOnlyInline}}
  - : همیشه `'Netscape'` را در هر مرورگری برمی‌گرداند.
- {{domxref("Navigator.appVersion")}} {{ReadOnlyInline}}
  - : نسخه مرورگر را به صورت یک رشته برمی‌گرداند. برای دریافت مقدار صحیح به این ویژگی تکیه نکنید.
- {{domxref("Navigator.doNotTrack")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : مقدار ترجیح «دنبال نکن» (do-not-track) کاربر را گزارش می‌دهد. وقتی این مقدار "1" باشد، وب‌سایت یا برنامه شما نباید کاربر را ردیابی کند.
- {{domxref("Navigator.mimeTypes")}} {{ReadOnlyInline}}
  - : یک {{domxref("MimeTypeArray")}} شامل انواع MIME پشتیبانی‌شده توسط مرورگر برمی‌گرداند.
- {{domxref("Navigator.oscpu")}} {{ReadOnlyInline}}
  - : یک رشته نمایانگر سیستم عامل جاری برمی‌گرداند.
- {{domxref("Navigator.platform")}} {{ReadOnlyInline}}
  - : یک رشته نمایانگر پلتفرم مرورگر برمی‌گرداند. برای دریافت یک مقدار معنی‌دار به این تابع تکیه نکنید.
- {{domxref("Navigator.plugins")}} {{ReadOnlyInline}}
  - : یک {{domxref("PluginArray")}} شامل افزونه‌های نصب‌شده در مرورگر برمی‌گرداند.
- {{domxref("Navigator.product")}} {{ReadOnlyInline}}
  - : همیشه `'Gecko'` را در هر مرورگری برمی‌گرداند.
- {{domxref("Navigator.productSub")}} {{ReadOnlyInline}}
  - : یا رشته `'20030107'` یا `'20100101'` را برمی‌گرداند.
- {{domxref("Navigator.vendor")}} {{ReadOnlyInline}}
  - : یا رشته خالی، یا `'Apple Computer Inc.'`، یا `'Google Inc.'` را برمی‌گرداند.
- {{domxref("Navigator.vendorSub")}} {{ReadOnlyInline}}
  - : همیشه رشته خالی را برمی‌گرداند.

## روش‌های نمونه

هیچ روشی را به ارث نمی‌برد.

- {{domxref("Navigator.canShare()")}} {{SecureContext_Inline}}
  - : اگر فراخوانی `Navigator.share()` موفقیت‌آمیز باشد `true` برمی‌گرداند.
- {{domxref("Navigator.clearAppBadge()")}} {{SecureContext_Inline}}
  - : یک نشان (badge) را از روی آیکون برنامه جاری پاک کرده و یک {{jsxref("Promise")}} برمی‌گرداند که با {{jsxref("undefined")}} حل می‌شود.
- {{domxref("Navigator.deprecatedReplaceInURN()")}} {{Experimental_Inline}}
  - : رشته‌های مشخص شده را در داخل URL نگاشت‌شده متناظر با یک URN مبهم یا خاصیت `url` داخلی `FencedFrameConfig` جایگزین می‌کند. این روش به عنوان یک اقدام موقت (از این رو «منسوخ‌شده») در دسترس قرار گرفته است تا آن جایگزینی را برای URL‌های فریم حصاردار (fenced frame) امکان‌پذیر کند و به ارائه‌دهندگان فناوری تبلیغات کمک کند تا پیاده‌سازی‌های موجود را به API‌های [privacy sandbox](https://privacysandbox.google.com/) منتقل کنند.
- {{domxref("Navigator.getAutoplayPolicy()")}} {{Experimental_Inline}}
  - : یک مقدار برمی‌گرداند که نشان می‌دهد آیا عنصر رسانه‌ای، زمینه صوتی (audio context) یا «نوع» ویژگی رسانه‌ای مشخص شده مجاز به پخش خودکار (autoplay) است یا خیر.
- {{domxref("Navigator.getBattery()")}} {{SecureContext_Inline}}
  - : یک promise برمی‌گرداند که با یک شیء {{domxref("BatteryManager")}} حل می‌شود که اطلاعاتی درباره وضعیت شارژ باتری را برمی‌گرداند.
- {{domxref("Navigator.getGamepads()")}}
  - : یک آرایه از اشیاء {{domxref("Gamepad")}} برمی‌گرداند، یکی برای هر گیم‌پد متصل به دستگاه.
- {{domxref("Navigator.getInstalledRelatedApps()")}} {{Experimental_Inline}} {{SecureContext_Inline}}
  - : یک promise برمی‌گرداند که با یک آرایه از اشیاء نمایانگر هر برنامه بومی یا [برنامه وب پیشرفته](/en-US/docs/Web/Progressive_web_apps) مرتبطی که کاربر نصب کرده است، حل می‌شود.
- {{domxref("Navigator.registerProtocolHandler()")}} {{SecureContext_Inline}}
  - : به وب‌سایت‌ها اجازه می‌دهد خود را به عنوان یک handler احتمالی برای یک پروتکل خاص ثبت کنند.
- {{domxref("Navigator.requestMediaKeySystemAccess()")}} {{SecureContext_Inline}}
  - : یک {{jsxref("Promise")}} برای یک شیء MediaKeySystemAccess برمی‌گرداند.
- {{domxref("Navigator.requestMIDIAccess()")}} {{SecureContext_Inline}}
  - : یک {{jsxref('Promise')}} نمایانگر درخواست دسترسی به دستگاه‌های MIDI روی سیستم کاربر برمی‌گرداند.
- {{domxref("Navigator.sendBeacon()")}}
  - : برای انتقال ناهمزمان مقدار کمی داده با استفاده از {{Glossary("HTTP")}} از عامل کاربر به یک وب سرور استفاده می‌شود.
- {{domxref("Navigator.setAppBadge()")}} {{SecureContext_Inline}}
  - : یک نشان روی آیکون مرتبط با این برنامه تنظیم می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که با {{jsxref("undefined")}} حل می‌شود.
- {{domxref("Navigator.share()")}} {{SecureContext_Inline}}
  - : مکانیزم اشتراک‌گذاری بومی پلتفرم جاری را فراخوانی می‌کند.
- {{domxref("Navigator.vibrate()")}}
  - : باعث لرزش در دستگاه‌هایی که از آن پشتیبانی می‌کنند می‌شود. اگر پشتیبانی از لرزش موجود نباشد، هیچ کاری انجام نمی‌دهد.
- {{domxref("Navigator.unregisterProtocolHandler()")}} {{SecureContext_Inline}}
  - : یک وب‌سایت که handler برای یک پروتکل مشخص است را لغو ثبت می‌کند.

### روش‌های منسوخ‌شده

- {{domxref("Navigator.getUserMedia()")}} {{Deprecated_Inline}} {{SecureContext_Inline}}
  - : پس از درخواست اجازه از کاربر، جریان صوتی یا تصویری مرتبط با یک دوربین یا میکروفون روی رایانه محلی را برمی‌گرداند.
- {{domxref("Navigator.getVRDisplays()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک promise برمی‌گرداند که به یک آرایه از اشیاء {{domxref("VRDisplay")}} نمایانگر هر دستگاه VR موجود متصل به رایانه حل می‌شود.
- {{domxref("Navigator.javaEnabled()")}}
  - : همیشه false برمی‌گرداند.
- {{domxref("Navigator.taintEnabled()")}}
  - : `false` برمی‌گرداند. توابع taint/untaint جاوااسکریپت در جاوااسکریپت 1.2 حذف شدند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}