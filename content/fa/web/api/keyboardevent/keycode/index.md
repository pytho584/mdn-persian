---
title: "KeyboardEvent: keyCode property"
---

---
title: "KeyboardEvent: keyCode property"
short-title: keyCode
slug: Web/API/KeyboardEvent/keyCode
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.KeyboardEvent.keyCode
---

{{APIRef("UI Events")}}{{Deprecated_Header}}

ویژگی فقط‌خواندنیِ منسوخ‌شدهٔ **`KeyboardEvent.keyCode`** یک کد عددی وابسته به سیستم و پیاده‌سازی را نشان می‌دهد که مقدار بدونِ‌تغییر کلید فشرده‌شده را شناسایی می‌کند.

این مقدار معمولاً کد دهدهی ASCII ({{RFC(20)}}) یا Windows 1252 متناظر با آن کلید است. اگر کلید قابل شناسایی نباشد، این مقدار `0` خواهد بود.

در صورت امکان باید از استفاده از این ویژگی خودداری کنید؛ مدتی است که منسوخ اعلام شده است. در عوض، باید از {{domxref("KeyboardEvent.code")}} (برای کلید فیزیکی فشرده‌شده) یا {{domxref("KeyboardEvent.key")}} (برای نویسه‌ای که کلید به آن نگاشت می‌شود) استفاده کنید. اگر مرورگرهای بسیار قدیمی را هدف گرفته‌اید، سازگاری هر یک از این دو ویژگی را بررسی کنید.

> [!NOTE]
> توسعه‌دهندگان وب هنگام مدیریت رویدادهای `keydown` و `keyup` نباید از ویژگی `keyCode` برای نویسه‌های قابل چاپ استفاده کنند. همان‌طور که در بالا توضیح داده شد، ویژگی `keyCode` برای نویسه‌های قابل چاپ، به‌ویژه آن‌هایی که با فشردن کلید <kbd>Shift</kbd> یا <kbd>Alt</kbd> وارد می‌شوند، مفید نیست.

## مقدار `keyCode`

### کلیدهای قابل چاپ در موقعیت استاندارد

مقدار رویدادهای کلیدی که در اثر فشردن یا رها کردن کلیدهای قابل چاپ در موقعیت استاندارد ایجاد می‌شوند، بین مرورگرها سازگار نیست.

IE فقط مقدار کد کلید مجازی بومی را به‌صورت `KeyboardEvent.keyCode` در معرض دید قرار می‌دهد.

Google Chrome، Chromium و Safari باید مقدار را بر اساس نویسهٔ ورودی تعیین کنند. اگر بتوان نویسهٔ ورودی را با چیدمان صفحه‌کلید US وارد کرد، آن‌ها از مقدار `keyCode` در چیدمان صفحه‌کلید US استفاده می‌کنند.

Firefox مقادیر `keyCode` را از نویسه‌های {{Glossary("ASCII")}} که با آن کلید قابل ورود هستند به دست می‌آورد — حتی با اصلاح‌کننده‌های Shift یا چیدمان صفحه‌کلید سازگار با ASCII. برای جزئیات، قوانین زیر را ببینید:

1. اگر سیستم ویندوز باشد و کد کلید بومیِ کلید فشرده‌شده نشان دهد که کلید a-z یا 0-9 است، از یک keycode برای آن استفاده کنید.
2. اگر سیستم مک باشد و کد کلید بومیِ کلید فشرده‌شده نشان دهد که کلید 0-9 است، از یک keycode برای آن استفاده کنید.
3. اگر کلید فشرده‌شده بدون کلید اصلاح‌کننده، یک نویسهٔ الفبایی یا عددی ASCII وارد کند، از یک keycode برای آن استفاده کنید.
4. اگر کلید فشرده‌شده با کلید اصلاح‌کنندهٔ Shift، یک نویسهٔ الفبایی یا عددی ASCII وارد کند، از یک keycode برای آن استفاده کنید.
5. اگر کلید فشرده‌شده بدون کلید اصلاح‌کننده، یک نویسهٔ ASCII دیگر وارد کند، از یک keycode برای آن استفاده کنید.
6. اگر کلید فشرده‌شده با کلید اصلاح‌کنندهٔ Shift، یک نویسهٔ ASCII دیگر وارد کند، از یک keycode برای آن استفاده کنید.
7. در غیر این صورت، یعنی کلید فشرده‌شده یک نویسهٔ یونیکد وارد می‌کند:
   1. اگر چیدمان صفحه‌کلید سازگار با ASCII است (یعنی می‌تواند حروف ASCII وارد کند)، از 0 استفاده کنید یا طبق قوانین تکمیلی زیر محاسبه کنید.
   2. در غیر این صورت، یعنی چیدمان صفحه‌کلید سازگار با ASCII نیست، از چیدمان صفحه‌کلید سازگار با ASCII استفاده کنید که با بالاترین اولویت در محیط نصب شده است:
      1. اگر کلید فشرده‌شده در چیدمان جایگزین، یک نویسهٔ الفبایی یا عددی ASCII وارد کند، از یک keycode برای آن استفاده کنید.
      2. در غیر این صورت، از 0 استفاده کنید یا طبق قوانین تکمیلی زیر محاسبه کنید.

Gecko مقادیر `keyCode` کلیدهای نقطه‌گذاری را تا حد امکان (زمانی که به بندهای ۷.۱ یا ۷.۲ در فهرست بالا می‌رسیم) طبق قوانین زیر تنظیم می‌کند:

> [!WARNING]
> هدف از این قوانین تکمیلی جدید این است که کاربرانی که چیدمان صفحه‌کلیدشان نویسه‌های یونیکد را به کلیدهای نقطه‌گذاری در چیدمان صفحه‌کلید US نگاشت می‌کند، بتوانند از برنامه‌های وب استفاده کنند که فقط با چیدمان‌های سازگار با ASCII یا فقط با چیدمان صفحه‌کلید US از Firefox پشتیبانی می‌کنند. در غیر این صورت، مقادیر `keyCode` تازه‌نگاشت‌شده ممکن است با کلیدهای دیگر تداخل کنند. برای مثال، اگر چیدمان صفحه‌کلید فعال روسی باشد، مقدار `keyCode` برای **هر دو** کلید `"Period"` و `"Slash"` برابر `190` (`KeyEvent.DOM_VK_PERIOD`) است. اگر باید این کلیدها را از هم تشخیص دهید اما نمی‌خواهید خودتان از همهٔ چیدمان‌های صفحه‌کلید دنیا پشتیبانی کنید، احتمالاً باید از {{domxref("KeyboardEvent.code")}} استفاده کنید.

1. اگر در macOS یا لینوکس اجرا می‌شود:
   1. اگر چیدمان صفحه‌کلید فعال سازگار با ASCII نیست و یک چیدمان جایگزین سازگار با ASCII در دسترس است.
      1. اگر چیدمان جایگزین سازگار با ASCII فقط با خود کلید (بدون اصلاح‌کننده) یک نویسهٔ ASCII تولید کند، از یک `keyCode` برای آن نویسه استفاده کنید.
      2. اگر چیدمان جایگزین سازگار با ASCII با کلید اصلاح‌کنندهٔ Shift یک نویسهٔ ASCII تولید کند، از یک `keyCode` برای نویسهٔ حاصل از Shift استفاده کنید.
      3. در غیر این صورت، از یک `keyCode` برای نویسهٔ ASCII تولیدشده توسط آن کلید استفاده کنید، زمانی که چیدمان صفحه‌کلید US فعال است.
   2. در غیر این صورت، از یک `keyCode` برای نویسهٔ ASCII تولیدشده توسط آن کلید استفاده کنید، زمانی که چیدمان صفحه‌کلید US فعال است.
2. اگر در ویندوز اجرا می‌شود:
   1. از یک مقدار `keyCode` برای نویسهٔ ASCII تولیدشده توسط کلیدی استفاده کنید که هنگام فعال بودن چیدمان صفحه‌کلید US به همان کد کلید مجازی ویندوز نگاشت می‌شود.

<table class="no-markdown">
  <caption>
    مقادیر keyCode رویداد keydown هر مرورگر ناشی از کلیدهای قابل چاپ در موقعیت استاندارد
  </caption>
  <thead>
    <tr>
      <th scope="row">{{domxref("KeyboardEvent.code")}}</th>
      <th colspan="3" scope="col">IE 11</th>
      <th colspan="6" scope="col">Google Chrome 34</th>
      <th colspan="3" scope="col">Chromium 34</th>
      <th colspan="3" scope="col">Safari 7</th>
      <th colspan="9" scope="col">Gecko 29</th>
    </tr>
    <tr>
      <th></th>
      <th colspan="3" scope="col">Windows</th>
      <th colspan="3" scope="col">Windows</th>
      <th colspan="3" scope="col">Mac (10.9)</th>
      <th colspan="3" scope="col">Linux (Ubuntu 14.04)</th>
      <th colspan="3" scope="col">Mac (10.9)</th>
      <th colspan="3" scope="col">Windows</th>
      <th colspan="3" scope="col">Mac (10.9)</th>
      <th colspan="3" scope="col">Linux (Ubuntu 14.04)</th>
    </tr>
    <tr>
      <th></th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
      <th scope="col">US</th>
      <th scope="col">Japanese</th>
      <th scope="col">Greek</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row"><code>"Digit1"</code></th>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
      <td colspan="3"><code>0x31 (49)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit2"</code></th>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
      <td colspan="3"><code>0x32 (50)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit3"</code></th>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
      <td colspan="3"><code>0x33 (51)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit4"</code></th>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
      <td colspan="3"><code>0x34 (52)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit5"</code></th>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
      <td colspan="3"><code>0x35 (53)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit6"</code></th>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
      <td colspan="3"><code>0x36 (54)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit7"</code></th>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
      <td colspan="3"><code>0x37 (55)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit8"</code></th>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
      <td colspan="3"><code>0x38 (56)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit9"</code></th>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
      <td colspan="3"><code>0x39 (57)</code></td>
    </tr>
    <tr>
      <th scope="row"><code>"Digit0"</code></th>
      <td colspan="3"><code>0x30 (48)</code></td>
      <td colspan="3"><code>0x30 (48)</