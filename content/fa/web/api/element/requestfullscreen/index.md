---
title: "Element: requestFullscreen() method"
short-title: requestFullscreen()
slug: Web/API/Element/requestFullscreen
page-type: web-api-instance-method
browser-compat: api.Element.requestFullscreen
---

{{APIRef("Fullscreen API")}}

متد **`requestFullscreen()`** از رابط {{domxref("Element")}} یک درخواست ناهمگام (asynchronous) برای نمایش عنصر در حالت تمام‌صفحه (fullscreen) صادر می‌کند.

## نحو (Syntax)

```js-nolint
requestFullscreen()
requestFullscreen(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء (object) که رفتار انتقال به حالت تمام‌صفحه را کنترل می‌کند.
    گزینه‌های موجود عبارتند از:
    - `keyboardLock` {{optional_inline}}
      - : حالت قفل صفحه‌کلید (keyboard lock) را کنترل می‌کند.
        - `"none"`
          - : هیچ قفل صفحه‌کلیدی اعمال نمی‌شود.
            این حالت پیش‌فرض است.
        - `"browser"`
          - : حالت قفل صفحه‌کلید مرورگر اعمال می‌شود.
            در این حالت، مرورگر رویدادهای صفحه‌کلید را به برنامه‌ای که معمولاً توسط کدهای مرورگر یا سیستم مدیریت می‌شود، ارسال می‌کند.
            برنامه‌ها باید رویدادهای کلیدها و ترکیب‌کلیدهایی را که می‌خواهند استفاده کنند، رهگیری (intercept) کرده و با فراخوانی [`preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) هر اقدام پیش‌فرضی را لغو کنند.

            توجه داشته باشید که برخی مرورگرها ممکن است اقدام پیش‌فرض برای برخی کلیدها مانند کلیدی که معمولاً برای خروج از حالت تمام‌صفحه استفاده می‌شود را غیرفعال کنند؛ این تضمین شده نیست، بنابراین همیشه باید `preventDefault()` را فراخوانی کنید.
            همچنین تشویق می‌شود که مرورگرها مکانیزمی برای خروج از حالت تمام‌صفحه با قفل صفحه‌کلید ارائه دهند.

            برای اطلاعات بیشتر به بخش [قفل صفحه‌کلید](#keyboard_locking) در زیر مراجعه کنید.

    - `navigationUI` {{optional_inline}}
      - : مشخص می‌کند که آیا هنگام تمام‌صفحه بودن عنصر، رابط ناوبری (navigation UI) نشان داده شود یا خیر.
        مقدار پیش‌فرض `"auto"` است که نشان می‌دهد مرورگر باید تصمیم بگیرد.
        - `"hide"`
          - : رابط ناوبری مرورگر پنهان می‌شود و تمام ابعاد صفحه به نمایش عنصر اختصاص می‌یابد.
        - `"show"`
          - : مرورگر کنترل‌های ناوبری صفحه و احتمالاً سایر رابط‌های کاربری را نمایش می‌دهد؛ ابعاد عنصر (و اندازه درک‌شده صفحه) برای جا دادن به این رابط کاربری محدود می‌شود.
        - `"auto"`
          - : مرورگر انتخاب می‌کند کدام یک از تنظیمات بالا اعمال شود.
            این مقدار پیش‌فرض است.
    - `screen` {{optional_inline}} {{experimental_inline}}
      - : صفحه‌ای را مشخص می‌کند که می‌خواهید عنصر را در آن به حالت تمام‌صفحه درآورید.
        این یک شیء {{domxref("ScreenDetailed")}} را به عنوان مقدار می‌پذیرد که نمایانگر صفحه انتخاب‌شده است.

### مقدار بازگشتی

یک {{JSxRef("Promise")}} که با مقدار `undefined` زمانی که انتقال به حالت تمام‌صفحه کامل شود، حل (resolve) می‌شود، یا با یک استثنا (exception) رد (reject) می‌شود.

### استثناها (Exceptions)

در صورت خطا، `Promise` بازگشتی با یکی از مقادیر زیر رد می‌شود:

- {{jsxref("TypeError")}}
  - : استثنای `TypeError` ممکن است در هر یک از شرایط زیر رخ دهد:
    - سند (document) حاوی عنصر کاملاً فعال نیست؛ یعنی سند جاری فعال نیست.
    - عنصر درون یک سند قرار ندارد.
    - عنصر مجاز به استفاده از ویژگی `fullscreen` نیست، چه به دلیل تنظیمات [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) یا سایر ویژگی‌های کنترل دسترسی.
    - عنصر و سند آن یک گره (node) واحد هستند.
    - عنصر یک [پاپ‌اور (popover)](/en-US/docs/Web/API/Popover_API) است که قبلاً از طریق {{domxref("HTMLElement.showPopover()")}} نمایش داده شده است.

- `NotSupportedError` {{domxref("DOMException")}}
  - : پارامتر `options.keyboardLock` ارسال‌شده توسط مرورگر پشتیبانی نمی‌شود.

## توضیحات (Description)

متد **`requestFullscreen()`** یک درخواست ناهمگام برای نمایش عنصر در حالت تمام‌صفحه صادر می‌کند.

این متد نیاز به مجوز (permission) دارد.

- اگر مجوز ورود به حالت تمام‌صفحه اعطا شود، {{JSxRef("Promise")}} بازگشتی حل می‌شود و عنصر یک رویداد {{domxref("Element/fullscreenchange_event", "fullscreenchange")}} دریافت می‌کند تا از قرار گرفتن در حالت تمام‌صفحه مطلع شود.
- اگر مجوز رد شود، promise رد می‌شود و عنصر به جای آن یک رویداد {{domxref("Element/fullscreenerror_event", "fullscreenerror")}} دریافت می‌کند.

اگر عنصر از سند اصلی جدا شده باشد، سند این رویدادها را دریافت می‌کند.

### عناصر سازگار (Compatible elements)

عنصری که می‌خواهید در حالت تمام‌صفحه قرار دهید باید چند الزام ساده را برآورده کند:

- باید یکی از عناصر HTML استاندارد یا {{SVGElement("svg")}} یا {{MathMLElement("math")}} باشد.
- یک عنصر {{HTMLElement("dialog")}} _نباشد_.
- باید یا درون سند سطح بالا (top-level document) قرار داشته باشد یا در یک {{HTMLElement("iframe")}} که ویژگی [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen) به آن اعمال شده است.

علاوه بر این، هر {{httpheader("Permissions-Policy")}} تنظیم‌شده باید استفاده از ویژگی `fullscreen` را مجاز کند.

### تشخیص فعال‌سازی تمام‌صفحه

می‌توانید با استفاده از {{jsxref("Promise")}} بازگشتی از `requestFullscreen()` تشخیص دهید که آیا تلاش شما برای تغییر به حالت تمام‌صفحه موفق بوده است یا خیر، همانطور که در [مثال‌ها](#examples) در زیر مشاهده می‌کنید.

برای اطلاع از زمانی که کد دیگری حالت تمام‌صفحه را روشن یا خاموش می‌کند، باید شنونده‌هایی (listeners) برای رویداد {{domxref("Document/fullscreenchange_event", "fullscreenchange")}} روی {{domxref("Document")}} تنظیم کنید.
همچنین مهم است که به `fullscreenchange` گوش دهید تا از زمانی که مثلاً کاربر به صورت دستی حالت تمام‌صفحه را تغییر می‌دهد یا زمانی که کاربر برنامه‌ها را جابجا می‌کند و باعث خروج موقت برنامه شما از حالت تمام‌صفحه می‌شود، مطلع شوید.

### قفل صفحه‌کلید (Keyboard locking)

قفل صفحه‌کلید به یک برنامه تمام‌صفحه اجازه می‌دهد برخی کلیدها و ترکیب‌کلیدهایی را که در غیر این صورت منحصراً توسط مرورگر یا سیستم‌عامل مدیریت می‌شوند، رهگیری و مدیریت کند.
این می‌تواند تجربه کاربری را برای بازی‌ها بهبود بخشد، مثلاً با اجازه دادن به استفاده از کلید <kbd>Esc</kbd> به عنوان کلید منو به جای خروج از حالت تمام‌صفحه.
همچنین می‌تواند برای برنامه‌هایی مانند کنترل از راه دور دسکتاپ مفید باشد، جایی که می‌خواهید تقریباً تمام رویدادهای کلید به رایانه راه دور ارسال شوند.

قفل صفحه‌کلید با ارسال یک مقدار حالت قفل صفحه‌کلید `"browser"` به پارامتر [`options.keyboardLock`](#keyboardlock) هنگام فعال‌سازی حالت تمام‌صفحه فعال می‌شود.
هنگامی که قفل صفحه‌کلید در حالت تمام‌صفحه فعال است، مرورگر «بسیاری بیشتر» از رویدادهای صفحه‌کلید را به برنامه هدایت می‌کند — مجموعه دقیق کلیدها به مرورگر بستگی دارد.
برنامه وب باید رویداد را با فراخوانی [`preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) برای لغو اقدام پیش‌فرض آن مدیریت کند.
برخی ترکیب‌کلیدها برای کنترل سیستم یا دارای ریسک حریم خصوصی هستند و بنابراین نمی‌توان با این مکانیزم رهگیری و غیرفعال کرد (مثلاً <kbd>Ctrl+Alt+Delete</kbd> در ویندوز).

توجه داشته باشید که برخی مرورگرها همیشه اقدام پیش‌فرض کلید <kbd>Esc</kbd> را در هنگام قفل صفحه‌کلید غیرفعال می‌کنند، به طوری که فشار دادن آن به طور خودکار از حالت تمام‌صفحه خارج نمی‌شود.
با این حال، از آنجایی که این تضمین نشده است، همچنان باید `preventDefault()` را فراخوانی کنید تا از خروج از حالت تمام‌صفحه با فشار دادن <kbd>Esc</kbd> جلوگیری کنید.
به طور کلی، نمی‌توانید فرض کنید که اقدام پیش‌فرض برای هر رویداد صفحه‌کلید به طور پیش‌فرض غیرفعال است.

انتظار می‌رود مرورگرها یک مکانیزم جایگزین برای خروج از حالت تمام‌صفحه در زمانی که قفل صفحه‌کلید فعال است، ارائه دهند.
اکثر مرورگرها از کلید <kbd>Esc</kbd> برای خروج از حالت تمام‌صفحه معمولی و از فشار طولانی <kbd>Esc</kbd> برای خروج از قفل صفحه‌کلید استفاده می‌کنند.
قفل صفحه‌کلید زمانی که مرورگر از حالت تمام‌صفحه خارج می‌شود، غیرفعال می‌شود.

### ملاحظات امنیتی (Security considerations)

[فعال‌سازی موقت کاربر (Transient user activation)](/en-US/docs/Web/Security/Defenses/User_activation) مورد نیاز است.
کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند.

حالت تمام‌صفحه توسط دستورالعمل [Permissions-Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) {{HTTPHeader("Permissions-Policy/fullscreen","fullscreen")}} کنترل می‌شود.

لیست سفید پیش‌فرض برای `screen-wake-lock` مقدار `self` است.
این اجازه استفاده از تمام‌صفحه را در فریم‌های تو در تو با همان منبع (same-origin) می‌دهد اما از آن در محتوای شخص ثالث جلوگیری می‌کند.
استفاده شخص ثالث را می‌توان با تنظیم سربرگ `Permissions-Policy` برای اعطای مجوز به یک منبع خاص شخص ثالث فعال کرد.

```http
Permissions-Policy: fullscreen=(self b.example.com)
```

سپس ویژگی `allow="fullscreen"` باید به عنصر کانتینر فریم برای منابع آن منبع اضافه شود:

```html
<iframe src="https://b.example.com" allow="fullscreen"></iframe>
```

می‌توان از مجوز `fullscreen` [Permissions API](/en-US/docs/Web/API/Permissions_API) برای آزمایش اینکه آیا دسترسی به استفاده از حالت `granted` (اعطا شده)، `denied` (رد شده) یا `prompt` (نیاز به تأیید کاربر با یک اعلان) است استفاده کرد.

## مثال‌ها (Examples)

### درخواست حالت تمام‌صفحه

این مثال عنصر {{HTMLElement("video")}} را با فشار دادن کلیدهای <kbd>Enter</kbd> یا <kbd>Shift</kbd> + <kbd>F</kbd> به حالت تمام‌صفحه و خارج از آن تغییر می‌دهد.
اسکریپت با استفاده از {{domxref("document.fullscreenElement")}} بررسی می‌کند که آیا سند در حال حاضر در حالت تمام‌صفحه است یا خیر.
اگر سند در حالت تمام‌صفحه است، {{domxref("document.exitFullscreen()")}} را فراخوانی می‌کند تا خارج شود.
در غیر این صورت، `requestFullscreen()` را روی عنصر `<video>` فراخوانی می‌کند:

```js
const video = document.querySelector("video");

document.addEventListener("keydown", (event) => {
  // توجه کنید که "F" به حروف بزرگ و کوچک حساس است (بزرگ):
  if (event.key === "Enter" || event.key === "F") {
    // بررسی کنید که آیا در حالت تمام‌صفحه هستیم
    if (document.fullscreenElement) {
      document.exitFullscreen();
      return;
    }
    // در غیر این صورت وارد حالت تمام‌صفحه شوید
    video.requestFullscreen().catch((err) => {
      console.error(`خطا در فعال‌سازی تمام‌صفحه: ${err.message}`);
    });
  }
});
```

```html
<p>
  عنصر ویدیوی زیر یک تایم‌لپس از شکوفه‌زدن یک گل را نشان می‌دهد. می‌توانید با
  <kbd>Enter</kbd> یا <kbd>Shift</kbd> + <kbd>F</kbd> ("F" بزرگ) حالت تمام‌صفحه
  را روشن و خاموش کنید. سند جاسازی‌شده باید
  <a href="https://developer.mozilla.org/en-US/docs/Web/API/Element/focus_event">
    focus
  </a>
  داشته باشد تا مثال کار کند.
</p>

<video controls loop src="/shared-assets/videos/flower.mp4" width="420"></video>
```

```css hidden
body {
  font-family:
    "Benton Sans", "Helvetica Neue", "Helvetica", "Arial", sans-serif;
  margin: 2em;
}

video::backdrop {
  background-color: #444488;
}
button {
  display: block;
}
kbd {
  border: 2px solid #cdcdcd;
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 0 #cdcdcd;
  font-size: 0.825rem;
  padding: 0.25rem;
}
```

{{embedlivesample("requesting_fullscreen_mode", , "400", "", "", "", "fullscreen")}}

### استفاده از قفل صفحه‌کلید

این مثال تقریباً مشابه مثال قبلی است، با این تفاوت که درخواست می‌دهیم تمام‌صفحه با قفل صفحه‌کلید باز شود.

#### JavaScript

```js hidden
const video = document.querySelector("video");
```

کد تغییر یافته شنونده رویداد کلید در زیر نشان داده شده است.

تفاوت اول این است که ما رویداد کلید <kbd>Esc</kbd> را در حالت تمام‌صفحه مدیریت می‌کنیم، با فراخوانی `event.preventDefault()` برای غیرفعال کردن اقدام پیش‌فرض (که خروج از حالت تمام‌صفحه است).

مانند قبل، اگر <kbd>Enter</kbd> یا <kbd>Shift+F</kbd> در زمانی که در حالت تمام‌صفحه نیستیم فشار داده شود، `requestFullscreen()` را فراخوانی می‌کنیم.
با این حال در این مورد گزینه `keyboardLock` را با مقدار `"browser"` ارسال می‌کنیم.

```js
document.addEventListener("keydown", (event) => {
  // بررسی کنید که آیا در حالت تمام‌صفحه هستیم
  if (document.fullscreenElement) {
    // لغو خروج از طریق کلید Escape
    if (event.key === "Escape") {
      event.preventDefault();
      // هر کار دیگری که ممکن است بخواهید هنگام فشار دادن escape انجام دهید
    }
  } else if (event.key === "Enter" || event.key === "F") {
    // اگر Enter یا F فشار داده شده و در حالت تمام‌صفحه نیستیم، تمام‌صفحه را باز کنید.
    // توجه کنید که "F" به حروف بزرگ و کوچک حساس است (بزرگ).
    video.requestFullscreen({ keyboardLock: "browser" }).catch((err) => {
      console.error(`خطا در فعال‌سازی تمام‌صفحه: ${err.message}`);
    });
  }
});
```

```html hidden
<p>
  عنصر ویدیوی زیر یک تایم‌لپس از شکوفه‌زدن یک گل را نشان می‌دهد. می‌توانید با
  <kbd>Enter</kbd> یا <kbd>Shift+F</kbd> ("F" بزرگ) حالت تمام‌صفحه را روشن و
  خاموش کنید. سند جاسازی‌شده باید
  <a href="https://developer.mozilla.org/en-US/docs/Web/API/Element/focus_event">
    focus
  </a>
  داشته باشد تا مثال کار کند.
</p>

<video controls loop src="/shared-assets/videos/flower.mp4" width="420"></video>
```

```css hidden
body {
  font-family:
    "Benton Sans", "Helvetica Neue", "Helvetica", "Arial", sans-serif;
  margin: 2em;
}

video::backdrop {
  background-color: #444488;
}
button {
  display: block;
}
kbd {
  border: 2px solid #cdcdcd;
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 0 #cdcdcd;
  font-size: 0.825rem;
  padding: 0.25rem;
}
```

#### نتایج

فریم را انتخاب کنید و <kbd>Shift+F</kbd> را فشار دهید.
هنگامی که صفحه به صورت تمام‌فریم نمایش داده می‌شود، به اعلان موقت در بالای صفحه که نحوه خروج از حالت تمام‌صفحه را توضیح می‌دهد توجه کنید.

{{embedlivesample("Using keyboard lock", , "400", "", "", "", "fullscreen")}}

### استفاده از navigationUI

در این مثال، کل سند با فراخوانی `requestFullscreen()` روی {{DOMxRef("Document.documentElement")}} که عنصر ریشه {{HTMLElement("html")}} سند است، در حالت تمام‌صفحه قرار می‌گیرد.

```js
let elem = document.documentElement;

elem
  .requestFullscreen({ navigationUI: "show" })
  .then(() => {})
  .catch((err) => {
    alert(
      `خطایی در تلاش برای تغییر به حالت تمام‌صفحه رخ داد: ${err.message} (${err.name})`,
    );
  });
```

مدیریت حل promise هیچ کاری انجام نمی‌دهد، اما اگر promise رد شود، یک پیام خطا با فراخوانی {{DOMxRef("Window.alert", "alert()")}} نمایش داده می‌شود.

### استفاده از گزینه screen

اگر می‌خواهید عنصر را در صفحه اصلی سیستم‌عامل به حالت تمام‌صفحه درآورید، می‌توانید از کدی مانند زیر استفاده کنید:

```js
try {
  const primaryScreen = (await getScreenDetails()).screens.find(
    (screen) => screen.isPrimary,
  );
  await document.body.requestFullscreen({ screen: primaryScreen });
} catch (err) {
  console.error(err.name, err.message);
}
```

متد {{domxref("Window.getScreenDetails()")}} برای بازیابی شیء {{domxref("ScreenDetails")}} برای دستگاه جاری استفاده می‌شود که شامل اشیاء {{domxref("ScreenDetailed")}} نمایانگر صفحه‌های مختلف موجود است.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- {{DOMxRef("Document.exitFullscreen()")}}
- {{DOMxRef("Document.fullscreen")}}
- {{DOMxRef("Document.fullscreenElement")}}
- {{CSSxRef(":fullscreen")}}
- [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen)