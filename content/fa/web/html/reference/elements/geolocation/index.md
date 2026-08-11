---
title: "<geolocation> HTML geolocation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/geolocation"
translated_by: "n8n + AI"
---

المان **`<geolocation>`** یک کنترل تعاملی در [HTML](/en-US/docs/Web/HTML) است که به کاربر امکان می‌دهد موقعیت مکانی خود را با صفحه به اشتراک بگذارد.

این المان این موارد را فراهم می‌کند:

- یک رابط کاربری شهودی (تعریف‌شده توسط مرورگر)
- فرآیندی برای مدیریت مجوزهای مورد نیاز قابلیت `geolocation`
- امکانات API برای دسترسی به داده‌های موقعیت و واکنش به داده‌های دریافتی و تغییرات مجوز

## ویژگی‌ها (Attributes)

این المان از [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `autolocate` {{experimental_inline}}
  - یک ویژگی بولی (boolean) که اگر `true` باشد، مرورگر بلافاصله پس از رندر شدن المان `<geolocation>` (در صورت اعطای مجوز قبلی) داده‌های موقعیت را دریافت می‌کند. اگر `false` باشد، داده‌ها تا زمانی که کاربر کنترل را فعال نکند دریافت نمی‌شوند. مقدار پیش‌فرض `false` است.

    اگر مجوز قبلاً داده نشده باشد، این ویژگی تأثیری ندارد.

- `watch` {{experimental_inline}}
  - یک ویژگی بولی که اگر `true` باشد، مرورگر هر بار که موقعیت دستگاه کاربر تغییر می‌کند، داده‌های موقعیت را دریافت می‌کند. اگر `false` باشد، داده‌ها فقط یک بار دریافت می‌شوند. مقدار پیش‌فرض `false` است.

## توضیحات

المان `<geolocation>` یک کنترل اعلامی (declarative) و تعریف‌شده توسط مرورگر برای اشتراک‌گذاری داده‌های موقعیت ارائه می‌دهد. مثلاً در مرورگر Chrome، دکمه شامل یک آیکون «پین نقشه» و متن شهودی (مانند «استفاده از موقعیت» در محتوای انگلیسی) است.

این المان همچنین مدیریت آسان مجوزهای کاربر را امکان‌پذیر می‌کند.
به‌عنوان مثال، در Chrome اگر کاربر قبلاً اجازه دسترسی به موقعیت را رد کرده باشد یا پنجره مجوز را بدون انتخاب بسته باشد، می‌تواند دوباره دکمه را فشار دهد تا انتخاب خود را تغییر دهد. در مواردی که قبلاً مجوز را رد کرده است، دیالوگ‌های بعدی به او اطلاع می‌دهند که قبلاً اجازه اشتراک‌گذاری موقعیت را نداده و از او می‌پرسند که آیا می‌خواهد همچنان اجازه ندهد یا اجازه دهد.

یک نکته کلیدی درباره `<geolocation>` این است که انتخاب آگاهانه کاربر را منعکس می‌کند و از استفاده‌های احتمالی که کاربر را فریب دهد تا ناآگاهانه موقعیت خود را فاش کند جلوگیری می‌کند (برای اطلاعات بیشتر به بخش [مسدودسازی توسط `<geolocation>`](#geolocation_blocking) مراجعه کنید).

رابط DOM این المان، یعنی {{domxref("HTMLGeolocationElement")}}، امکاناتی برای دسترسی به داده‌های موقعیت برگشتی، وضعیت مجوز فعلی و خطاها (در صورت ناموفق بودن دریافت داده) فراهم می‌کند و نیاز به نوشتن منطق جاوااسکریپت را کاهش می‌دهد. همچنین رویدادهایی در دسترس هستند که می‌توان در پاسخ به دریافت داده‌های موقعیت، تغییر وضعیت مجوز و تعامل کاربر با دیالوگ مجوز، کد اجرا کرد.

> **نکته:** به دلایل عملکردی، حداکثر سه المان `<geolocation>` در یک صفحه مجاز است. اگر این سهمیه بیش‌تر شود، عملکرد تمام المان‌های `<geolocation>` غیرفعال می‌شود.

### ارتباط با Geolocation API

[Geolocation API](/en-US/docs/Web/API/Geolocation_API) یک جایگزین قدیمی‌تر برای مدیریت داده‌های موقعیت ارائه می‌دهد. این API کاستی‌هایی دارد که `<geolocation>` سعی در رفع آن‌ها دارد: مهم‌ترین آن‌ها این است که رابط کاربری و منطق پایه برای درخواست داده‌ها هر بار باید از صفر پیاده‌سازی شود و مدیریت مجوزها می‌تواند غیرشهودی باشد.

المان `<geolocation>` در پس‌زمینه از ویژگی‌های Geolocation API استفاده می‌کند. به طور پیش‌فرض، مرورگر یک بار داده‌های موقعیت را درخواست می‌کند (مثل فراخوانی {{domxref("Geolocation.getCurrentPosition()")}}). اما اگر ویژگی `watch` روی `true` تنظیم شود، مرورگر هر بار که موقعیت دستگاه تغییر می‌کند داده‌ها را به‌روزرسانی می‌کند (مثل فراخوانی {{domxref("Geolocation.watchPosition()")}}).

اگر داده‌ها با موفقیت بازیابی شوند، در property با نام {{domxref("HTMLGeolocationElement.position")}} در دسترس خواهند بود که حاوی یک شیء {{domxref("GeolocationPosition")}} است. اگر بازیابی داده‌ها ناموفق باشد، اطلاعات خطا در property با نام {{domxref("HTMLGeolocationElement.error")}} قرار می‌گیرد که شامل یک شیء {{domxref("GeolocationPositionError")}} است.

### تنظیم زبان دکمه

اتریبیوت سراسری `lang` توسط عنصر `<geolocation>` برای انتخاب زبان متن رندر‌شده استفاده می‌شود. یعنی می‌توانید یک اتریبیوت `lang` را مستقیماً روی عنصر `<geolocation>` یا روی یکی از اجداد آن قرار دهید تا به browser بگویید برچسب دکمه از چه زبانی استفاده کند.

اگر هیچ اتریبیوت `lang` مناسبی تنظیم نشده باشد، از زبان ترجیحی browser استفاده می‌شود.

### گنجاندن محتوای جایگزین

می‌توانید محتوای جایگزین را بین تگ‌های باز و بسته عنصر `<geolocation>` قرار دهید که در صورت پشتیبانی‌نشدن نمایش داده شود. برای مثال، می‌توانید پیام «پشتیبانی نمی‌شود» را قرار دهید:

```html
<geolocation>
  <p>Your browser doesn't support the Geolocation element.</p>
</geolocation>
```

با این حال، راه‌حل عملی‌تر این است که یک عنصر {{htmlelement("button")}} معمولی قرار دهید که از Geolocation API برای دریافت داده‌های موقعیت استفاده می‌کند:

```html
<geolocation>
  <button id="fallback">Use location</button>
</geolocation>
```

### مسدودسازی `<geolocation>`

ایده کلیدی پشت طراحی عنصر `<geolocation>` این است که انتخاب آگاهانه کاربر برای افشای اطلاعات موقعیت را منعکس کند و از فریب کاربران توسط عوامل مخرب برای فعال‌سازی آن جلوگیری کند، مثلاً از طریق [clickjacking](/en-US/docs/Web/Security/Attacks/Clickjacking). به همین دلیل، browser برای هر عنصر رندر‌شده، فهرستی از به‌اصطلاح **blocker reasons** را نگه می‌دارد.

وقتی یک blocker روی عنصر `<geolocation>` فعال باشد، عنصر از کار کردن باز می‌ماند (مسدود می‌شود)، به‌صورت موقت یا دائم، بسته به دلیل. وقتی یک عنصر `<geolocation>` مسدود می‌شود، به‌اصطلاح invalid محسوب می‌شود. می‌توانید با بررسی property با نام {{domxref("HTMLGeolocationElement.isValid")}} متوجه شوید که آیا invalid است یا نه. همچنین می‌توانید دلیل invalid بودن را از طریق property با نام {{domxref("HTMLGeolocationElement.invalidReason")}} دریافت کنید — برای فهرست کامل دلایل ممکن به آن صفحه مراجعه کنید.

### محدودیت‌های استایل‌دهی

عنصر `<geolocation>` محدودیت‌های متعددی بر روی استایل‌های CSS دارد که می‌توان روی آن اعمال کرد. برخی از این محدودیت‌ها برای تضمین دسترس‌پذیری (accessibility) اساسی طراحی شده‌اند و اگر رعایت نشوند، دکمه غیرفعال می‌شود. برخی دیگر مقادیر یا بازه‌های مشخصی را برای property های مختلف اعمال می‌کنند.

هر property که در زیربخش‌های زیر فهرست نشده باشد، یا معادل منطقی یک property فیزیکی ذکر شده در زیربخش‌های زیر باشد، هنگام تنظیم روی عنصر `<geolocation>` نادیده گرفته می‌شود.

#### محدودیت‌های دسترس‌پذیری

دکمه رندر‌شده `<geolocation>` در صورت رعایت‌نکردن محدودیت‌های زیر غیرفعال می‌شود (یعنی فشار دادن آن اثری نخواهد داشت):

- نسبت [کنتراست رنگ](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast) بین {{cssxref("color")}} و {{cssxref("background-color")}} باید حداقل ۳:۱ باشد.
- مقدار {{cssxref("font-size")}} نباید کوچک‌تر از مقدار `small` باشد (در مورد مقادیر کلیدواژه‌ای)، یا از مقدار محاسبه‌شده آن (در مورد سایر انواع مقادیر).

#### محدودیت‌های مقدار

محدودیت‌های مقدار زیر برای property های CSS روی عنصر `<geolocation>` اعمال می‌شوند. اگر تلاش شود این property ها روی عنصر `<geolocation>` به مقادیری خارج از محدودیت‌های ذکر شده تنظیم شوند، مقدار طوری تنظیم می‌شود که با محدودیت برابر شود (در مورد محدودیت مقدار دقیق) یا به نزدیک‌ترین کران بالا یا پایین مقدار محاسبه‌شده برسد (در مورد محدودیت بازه‌ای).

- `opacity`
  - : `1.0`
- `line-height`
  - : `normal`
- `white-space`
  - : `nowrap`
- `user-select`
  - : `none`
- `appearance`
  - : `auto`
- `box-sizing`
  - : `content-box`
- `vertical-align`
  - : `middle`
- `text-emphasis`
  - : `initial`
- `text-shadow`
  - : `initial`
- `outline-offset`
  - : `0` یا بیشتر.
- `font-weight`
  - : `200` یا بیشتر.
- `word-spacing`
  - : بین `0` و `0.5em`، شامل هر دو مقدار.
- `letter-spacing`
  - : بین `0.05em-` و `0.2em`، شامل هر دو مقدار.
- `letter-spacing`
  - : بین `0.05em-` و `0.2em`، شامل هر دو مقدار.
- `min-height`
  - : `1em` یا بیشتر.
- `max-height`
  - : `3em` یا کمتر. مقدار `none` نیز پذیرفته می‌شود.
- `min-width`
  - : مقدار محاسبه‌شده‌ی `fit-content` یا کمتر.
- `border-width`
  - : `1em` یا کمتر.

#### محدودیت‌های پیچیده

محدودیت‌های زیر پیچیده‌تر از محدودیت‌های مقدار ساده هستند:

- Padding در جهت بلوک (Block direction)
  - : اگر `block-size` برابر `auto` تنظیم شده باشد، `padding-block-start` و `padding-block-end` (و ویژگی‌های فیزیکی معادل برای [حالت نوشتار](/en-US/docs/Web/CSS/Reference/Properties/writing-mode) فعلی) به حداکثر `1em` محدود می‌شوند و باید برابر باشند.
- Padding در جهت خط (Inline direction)
  - : اگر `inline-size` برابر `auto` تنظیم شده باشد، `padding-inline-start` و `padding-inline-end` (و ویژگی‌های فیزیکی معادل برای [حالت نوشتار](/en-US/docs/Web/CSS/Reference/Properties/writing-mode) فعلی) به حداکثر `5em` محدود می‌شوند و باید برابر باشند.

#### ویژگی‌هایی که می‌توانند به‌صورت عادی تنظیم شوند

- `font-kerning`
- `font-optical-sizing`
- `font-stretch`
- `font-synthesis-weight`
- `font-synthesis-style`
- `font-synthesis-small-caps`
- `font-feature-settings`
- `forced-color-adjust`
- `text-rendering`
- `align-self`
- `anchor-name`
- `aspect-ratio`
- `border`، `border-top`، `border-right`، `border-bottom` و `border-left`
- `clear`
- `color-scheme`
- `contain-intrinsic-width`
- `contain-intrinsic-height`
- `container-name`
- `container-type`
- `counter-reset`، `counter-increment` و `counter-set`
- `flex`، `flex-grow`، `flex-shrink` و `flex-basis`
- `float`
- `height`
- `isolation`
- `justify-self`
- `left`
- `order`
- `orphans`
- `outline`، `outline-color` و `outline-style`
- `overflow-anchor`
- `overscroll-behavior`، `overscroll-behavior-inline`، `overscroll-behavior-block`، `overscroll-behavior-x` و `overscroll-behavior-y`
- `page`
- `position`
- `position-anchor`
- `right`
- `scroll-margin`، `scroll-margin-top`، `scroll-margin-right`، `scroll-margin-bottom` و `scroll-margin-left`
- `scroll-padding`، `scroll-padding-top`، `scroll-padding-right`، `scroll-padding-bottom`، `scroll-padding-left`، `scroll-padding-inline-start`، `scroll-padding-block-start`، `scroll-padding-block-start`، `scroll-padding-inline-end` و `scroll-padding-block-end`
- `text-spacing-trim`
- `text-transform`
- `top`
- `visibility`
- `x`
- `y`
- `ruby-position`
- `user-select`
- `width`
- `will-change`
- `z-index`

## دسترس‌پذیری

المان `<geolocation>` یک نام دسترس‌پذیر دارد که به [زبانی که روی آن تنظیم شده](#setting_the_button_language) نوشته می‌شود. همچنین دارای [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) برابر با [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) است تا صفحه‌خوان‌ها آن را به‌عنوان یک دکمه بشناسند.

علاوه بر این، المان `<geolocation>` به‌صورت پیش‌فرض مقدار [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) برابر با `0` دارد؛ بنابراین از نظر فوکوس صفحه‌کلید مانند یک `<button>` واقعی رفتار می‌کند.

در نهایت، برای اطلاع از محدودیت‌های استایل‌دهی اعمال‌شده روی المان `<geolocation>` برای رعایت الزامات اساسی دسترس‌پذیری، به بخش [محدودیت‌های دسترس‌پذیری](#accessibility_restrictions) مراجعه کنید.

## مثال‌ها

### مثال استفادهٔ پایه

در این مثال، از المان `<geolocation>` برای دریافت موقعیت فعلی شما استفاده می‌شود و نتیجه در یک المان `<p>` در زیر دکمه نمایش داده می‌شود. در این مثال همچنین از یک `<button>` معمولی به‌عنوان جایگزین برای دریافت اطلاعات موقعیت در مرورگرهایی که از `<geolocation>` پشتیبانی نمی‌کنند استفاده شده است.

#### HTML

ما یک المان `<geolocation>` به همراه یک `<button>` جایگزین که داخل آن قرار گرفته است اضافه می‌کنیم تا در مرورگرهایی که `<geolocation>` را پشتیبانی نمی‌کنند نمایش داده شود. همچنین یک `<p>` برای خروجی گرفتن اطلاعات موقعیت و خطاها در نظر می‌گیریم.

```html
<geolocation>
  <button id="fallback">Use location</button>
</geolocation>
<p id="output"></p>
```

#### JavaScript

در اسکریپت خود، ابتدا به element `<p>` خروجی ارجاع می‌دهیم. سپس با بررسی اینکه آیا `typeof HTMLGeolocationElement === "function"` است، تشخیص می‌دهیم که element `<geolocation>` پشتیبانی می‌شود یا نه:

- اگر پشتیبانی می‌شود، ابتدا به element `<geolocation>` ارجاع می‌گیریم و سپس یک شنونده رویداد به نام `location` به آن اضافه می‌کنیم.
  وقتی دکمه فشرده می‌شود و داده‌ها دریافت می‌شوند، شنونده مختصات (lat, long) را در `<p>` خروجی چاپ می‌کند (داده‌ها از طریق property `position` دریافت می‌شوند)، یا اگر دریافت داده ناموفق باشد، یک پیام خطا چاپ می‌کند (که از طریق property `error` دریافت می‌شود).
- اگر پشتیبانی نمی‌شود، به element `<button>` جایگزین ارجاع می‌گیریم و همان داده‌ها را دریافت و چاپ می‌کنیم؛ با این تفاوت که این بار از یک شنونده رویداد `click` روی دکمه و یک فراخوانی `Geolocation.getCurrentPosition()` برای دریافت داده‌ها استفاده می‌کنیم.

```js
const outputElem = document.querySelector("#output");

if (typeof HTMLGeolocationElement === "function") {
  const geo = document.querySelector("geolocation");
  geo.addEventListener("location", () => {
    if (geo.position) {
      outputElem.textContent += `(${geo.position.coords.latitude},${geo.position.coords.longitude}), `;
    } else if (geo.error) {
      outputElem.textContent += `${geo.error.message}, `;
    }
  });
} else {
  const fallback = document.querySelector("#fallback");
  fallback.addEventListener("click", () => {
    navigator.geolocation.getCurrentPosition(
      (position) => {
        outputElem.textContent += `(${position.coords.latitude}, ${position.coords.longitude}), `;
      },
      (error) => {
        outputElem.textContent += `${error.message}, `;
      },
    );
  });
}
```

#### نتیجه

این کد را به صورت [اجرای زنده](https://mdn.github.io/dom-examples/geolocation-element/basic-example/) ببینید ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/basic-example)). همچنین نسخه‌ای از این مثال را می‌توانید پیدا کنید که شامل attribute `watch` روی element `<geolocation>` است و بنابراین هر بار که موقعیت دستگاه کاربر تغییر می‌کند، داده‌های مکان را دریافت می‌کند (آن را به صورت [اجرای زنده](https://mdn.github.io/dom-examples/geolocation-element/basic-watch-example/) و [کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/basic-watch-example) ببینید).

سعی کنید دموها را در یک browser پشتیبانی‌کننده و در صورت امکان در یک browser غیرپشتیبان ببینید و به تفاوت روند دیالوگ مجوزها وقتی اجازه استفاده از `geolocation` را می‌دهید یا رد می‌کنید توجه کنید.

برای آشنایی با یک مثال کامل‌تر که از داده‌های مکان برای ساخت نقشهٔ منطقهٔ شما استفاده می‌کند، به صفحهٔ مرجع `HTMLGeolocationElement` مراجعه کنید.

## خلاصه فنی

| ویژگی | مقدار |
| --- | --- |
| دسته‌بندی محتوا | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content), محتوای تعاملی, محتوای قابل لمس |
| محتوای مجاز | هر محتوای بازگشتی شفاف مناسب. |
| حذف تگ | هیچ‌کدام. هر دو تگ شروع و پایان اجباری هستند. |
| والدهای مجاز | هر المانی که محتوای عبارتی (phrasing content) را بپذیرد. |
| نقش ARIA ضمنی | [نقش متناظر ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) |
| رابط DOM | `HTMLGeolocationElement` |

## همچنین ببینید

- `HTMLGeolocationElement`
- The `geolocation` [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)
- [Geolocation API](/en-US/docs/Web/API/Geolocation_API)
- [Permissions API](/en-US/docs/Web/API/Permissions_API)
- [Introducing the `<geolocation>` HTML element](https://developer.chrome.com/blog/geolocation-html-element) on developer.chrome.com (2026)