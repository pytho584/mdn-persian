---
title: "ARIA: slider role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: slider role"
short-title: slider
slug: Web/Accessibility/ARIA/Reference/Roles/slider_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#slider
sidebar: accessibilitysidebar
---

نقش `slider` یک ورودی را تعریف می‌کند که کاربر در آن مقداری را از میان یک بازهٔ مشخص انتخاب می‌کند.

## توضیحات

نقش `slider` برای ویجت‌های ورودی بازه‌ای است که کاربر در آن‌ها مقداری را از میان حداقل و حداکثر مشخص‌شده انتخاب می‌کند.

### نقش `slider` در مقایسه با سایر گزینه‌های بازه‌ای

ARIA شش [نقش ویجت](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#2._widget_roles) بازه‌ای مختلف را در اختیار توسعه‌دهندگان قرار می‌دهد، از جمله `progressbar`، `meter` و `slider`.

نقش [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)، مشابه عنصر {{HTMLElement('progress')}} در HTML، یک بازهٔ فقط‌خواندنی است که بخش تکمیل‌شدهٔ یک کار را نشان می‌دهد و در یک جهت واحد پیشرفت می‌کند؛ مانند نوار پیشرفت بارگذاری یک فایل که با تکمیل بارگذاری، در نهایت به ۱۰۰٪ می‌رسد.

نقش [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)، مشابه عنصر {{HTMLElement('meter')}} در HTML، یک نشانگر فقط‌خواندنی است که مقدار چیزی را در یک بازهٔ مشخص نشان می‌دهد؛ مانند نشانگر باتری رایانه یا نشانگر سوخت خودرو.

نقش `slider`، مشابه `input` از نوع `range` در HTML یعنی [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، یک ورودی بازه‌ای خواندنی-نوشتنی است. اسلایدرها به کاربران امکان می‌دهند مقداری را بین حداقل و حداکثر مشخص‌شده انتخاب کنند. کاربر با حرکت دادن دستگیرهٔ اسلایدر در طول یک اسلایدر افقی یا عمودی، مقدار موردنظر را انتخاب می‌کند.

اگرچه هر سه این بازه‌ها دارای حالت‌ها و خصوصیت‌های ARIA یکسانی هستند، نقش `slider` تنها بازهٔ خواندنی-نوشتنی است: تنها بازه‌ای است که مقدار آن از طریق تعامل کاربر تغییر می‌کند. بنابراین، باید بتواند فوکوس دریافت کند. علاوه بر این، تعامل با صفحه‌کلید، کلیک ماوس و تعامل لمسی باید پشتیبانی شوند.

> [!WARNING]
> برای تغییر مقدار اسلایدر، فناوری‌های کمکی مبتنی بر لمس باید با شبیه‌سازی رویدادهای کلید، به ژست‌های کاربر برای افزایش و کاهش مقدار پاسخ دهند.
> پیش از استفاده از نقش `slider` (و همهٔ ویجت‌های بازه‌ای)، ویجت‌های اسلایدر را با استفاده از فناوری‌های کمکی روی دستگاه‌هایی که لمس سازوکار ورودی اصلی آن‌هاست، به‌طور کامل آزمایش کنید.

### ویژگی‌های رایج

ویژگی [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) مقدار حداقل را تعیین می‌کند. اگر حذف شده باشد یا عدد نباشد، به‌صورت پیش‌فرض `0` (صفر) در نظر گرفته می‌شود.

ویژگی [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) مقدار حداکثر را تعریف می‌کند. اگر وجود نداشته باشد یا عدد نباشد، به‌صورت پیش‌فرض ۱۰۰ در نظر گرفته می‌شود.

مقدار ویژگی [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) باید بین حداقل و حداکثر مقدار، به‌صورت شامل، قرار داشته باشد. این ویژگی برای `slider` و `meter` الزامی و برای `progressbar` اختیاری است.

برای `slider`، مگر در صورت استفاده از عنصر [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، مقدار `aria-valuenow` باید هنگام به‌روزرسانی مقدار توسط کاربر، به‌صورت برنامه‌نویسی‌شده به‌روزرسانی شود.

ویژگی اختیاری [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) زمانی اضافه می‌شود که مقدار عددی `aria-valuenow` بیانگر مقدار موردنظر اسلایدر نباشد. از آنجا که حداقل، حداکثر و مقادیر فعلی همگی عددی هستند، وقتی مقادیری که این اعداد نشان می‌دهند عددی نیستند، باید ویژگی `aria-valuetext` با یک مقدار رشته‌ای که معنای مقدار عددی را تعریف می‌کند ارائه شود. برای مثال، اگر از اسلایدر برای اندازه‌های تیشرت استفاده شود، وقتی `aria-valuenow` افزایش می‌یابد، ویژگی `aria-valuetext` باید از xx-small تا XX-large تغییر کند.

مقدار `aria-valuetext` باید همگام با به‌روزرسانی `value` یا `aria-valuenow` به‌روزرسانی شود. اگرچه معادل HTML برای `<input type="range">` وجود ندارد، می‌توانید `aria-valuetext` را روی هر نوع {{htmlelement('input')}} قرار دهید. ویژگی‌های ARIA روی عناصر معنایی HTML پشتیبانی می‌شوند.

هنگامی که `aria-valuetext` برای یک اسلایدر ویژگی مهمی است، به‌جای آن استفاده از {{HTMLElement('select')}} با عناصر {{HTMLElement('option')}} را در نظر بگیرید. اگرچه از نظر ظاهری بازه نیست، مقدار هر گزینه برای همهٔ کاربران، نه فقط کاربران فناوری کمکی، در دسترس‌تر است.

یک نام قابل‌دسترس **الزامی** است. اگر نقش بازه روی یک عنصر HTML {{HTMLElement('input')}} (یا عنصر `<meter>` یا `<progress>`) اعمال شود، نام قابل‌دسترس می‌تواند از {{HTMLElement('label')}} مرتبط گرفته شود. در غیر این صورت، اگر برچسب قابل مشاهده وجود دارد از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) و اگر برچسب قابل مشاهده وجود ندارد از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید.

هنگامی که از عنصر HTML {{HTMLElement('input')}} برای ایجاد اسلایدر خود استفاده نمی‌کنید، ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) را برای قابل فوکوس کردن اسلایدر اضافه کنید. از میان سه نوع بازه، فقط `slider` تعاملی است و بنابراین تنها نوعی است که باید بتواند فوکوس دریافت کند. فوکوس باید روی دستگیرهٔ اسلایدر قرار گیرد.

اسلایدرها به‌صورت ضمنی مقدار [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) برابر با `horizontal` دارند. این ویژگی با `meter` یا `progressbar` پشتیبانی نمی‌شود.

### تعاملات کاربر

برخلاف نقش‌های فقط‌خواندنی `meter` و `progressbar`، `slider` یک ورودی است و تعامل کاربر را می‌پذیرد. علاوه بر افزودن ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) برای فعال کردن فوکوس اسلایدر، باید پشتیبانی از صفحه‌کلید و دستگاه‌های اشاره‌گر نیز پیاده‌سازی شود.

اسلایدر بازهٔ مقادیر ممکن را نشان می‌دهد. موقعیت دستگیرهٔ اسلایدر در طول آن، مقدار فعلی را نشان می‌دهد. کنش‌های کاربر که باید پشتیبانی شوند عبارت‌اند از تغییر مقدار با کشیدن دستگیره یا کلیک روی اسلایدر برای دستگاه‌های اشاره‌گر و استفاده از کلیدهای جهت‌دار مانند کلیدهای جهت‌نما برای کاربران صفحه‌کلید. به [تعاملات صفحه‌کلید](#keyboard_interactions) در ادامه مراجعه کنید.

> [!NOTE]
> توصیه می‌شود به‌جای نقش `slider` از عناصر بومی [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range) استفاده کنید. عامل‌های کاربر (User agents) یک ویجت استایل‌سازیشده برای عنصر ورودی بازه‌ای ارائه می‌دهند که بر اساس `value` فعلی و رابطهٔ آن با مقادیر حداقل و حداکثر ساخته می‌شود. هنگام استفاده از عناصر غیرمعنایی، همهٔ ویژگی‌های عنصر معنایی بومی باید با ویژگی‌های ARIA، جاوااسکریپت و CSS بازآفرینی شوند.

### بازه با چند دستگیره

اسلایدر چنددستگیره (multi-thumb) اسلایدری است که دو یا چند دستگیره دارد و هرکدام مقداری را در یک گروه از مقادیر مرتبط تعیین می‌کنند. برای مثال، در جستجوی محصولات، می‌توان از یک اسلایدر دو دستگیره استفاده کرد تا کاربران بتوانند حداقل و حداکثر قیمت جستجو را تعیین کنند.

در بسیاری از اسلایدرهای دو دستگیره، دستگیره‌ها اجازه ندارند از یکدیگر عبور کنند؛ مانند زمانی که اسلایدر مقادیر حداقل و حداکثر یک بازه را تعیین می‌کند. برای مثال، در یک انتخابگر محدودهٔ قیمت، حداکثر مقدار دستگیره‌ای که حد پایینی بازه را تعیین می‌کند، به مقدار فعلی دستگیره‌ای که حد بالایی بازه را تعیین می‌کند محدود می‌شود. همچنین حداقل مقدار دستگیرهٔ حد بالایی به مقدار فعلی دستگیرهٔ حد پایینی محدود می‌شود.

الزامی نیست که دستگیره‌های اسلایدرهای چنددستگیره به مقادیر سایر دستگیره‌ها وابسته باشند، اما تجربهٔ کاربری شهودی یک الزام است؛ بنابراین توصیه می‌شود از این ضدالگو اجتناب کنید.

### همهٔ عناصر فرزند نمایشی هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `slider` ندارند. برای مقابله با این محدودیت، مرورگرها به‌طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را روی همهٔ عناصر فرزند هر عنصر `slider` اعمال می‌کنند، زیرا این نقش از فرزندان معنایی پشتیبانی نمی‌کند.

برای مثال، عنصر `slider` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="slider"><h3>Temperature in Celsius</h3></div>
```

از آنجا که فرزندان `slider` نمایشی هستند، کد زیر معادل است با:

```html
<div role="slider"><h3 role="presentation">Temperature in Celsius</h3></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه‌کدهای قبلی با کد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="slider">Temperature in Celsius</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) (الزامی)
  - : روی یک مقدار اعشاری بین `aria-valuemin` و `aria-valuemax` تنظیم می‌شود و مقدار فعلی اسلایدر را نشان می‌دهد.
- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
  - : فناوری‌های کمکی اغلب مقدار `aria-valuenow` را به‌صورت عدد نمایش می‌دهند. اگر این نمایش دقیق نباشد، از `aria-valuetext` استفاده کنید تا مقدار قابل‌فهم‌تری برای اسلایدر فراهم شود.
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
  - : روی یک مقدار اعشاری تنظیم می‌شود که مقدار حداقل را نشان می‌دهد و از `aria-valuemax` کمتر است. اگر وجود نداشته باشد، مقدار پیش‌فرض ۰ است.
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
  - : روی یک مقدار اعشاری تنظیم می‌شود که مقدار حداکثر را نشان می‌دهد و از `aria-valuemin` بیشتر است. اگر وجود نداشته باشد، مقدار پیش‌فرض ۱۰۰ است.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : مقدار رشته‌ای را تعریف می‌کند یا عنصر (یا عناصری) را که عنصر اسلایدر را برچسب‌گذاری می‌کنند مشخص می‌کند و نام قابل‌دسترس را فراهم می‌سازد. نام قابل‌دسترس الزامی است.
- [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation)
  - : نشان می‌دهد که جهت عنصر افقی، عمودی یا ناشناخته/مبهم است. برای اسلایدر، مقدار ضمنی `horizontal` است، اما می‌توان آن را روی `vertical` تنظیم کرد. از آنجا که این ویژگی مقدار ضمنی دارد، جهت اسلایدر هرگز مبهم نیست.

### تعاملات صفحه‌کلید

| کلید(ها) | عملکرد |
| -------------------- | ------------------------------------------------------------------- |
| کلیدهای جهت‌نمای راست و بالا | افزایش مقدار انتخاب‌شده به اندازهٔ یک گام |
| کلیدهای جهت‌نمای چپ و پایین | کاهش مقدار انتخاب‌شده به اندازهٔ یک گام |
| Page Up | (اختیاری) افزایش مقدار به اندازهٔ مقداری معین، بیشتر از یک گام |
| Page Down | (اختیاری) کاهش مقدار به اندازهٔ مقداری معین، بیشتر از یک گام |
| Home | تنظیم اسلایدر روی حداقل مقدار. |
| End | تنظیم اسلایدر روی حداکثر مقدار. |

برای کلیدهای اختیاری <kbd>Page Up</kbd> و <kbd>Page Down</kbd>، تغییر مقدار اسلایدر باید اندازه‌ای بزرگ‌تر از تغییرات گامی باشد که با کلیدهای جهت‌نمای بالا و پایین انجام می‌شود.

## مثال‌ها

در مثال زیر، یک دماسنج عمودی ایجاد می‌کنیم که کاربر می‌تواند دمای اتاق را با آن تنظیم کند:

```html
<div>
  <div id="temperatureLabel">Temperature</div>
  <div id="temperatureValue">20°C</div>
  <div id="temperatureSlider">
    <div
      id="temperatureSliderThumb"
      role="slider"
      aria-labelledby="temperatureLabel"
      aria-orientation="vertical"
      tabindex="0"
      aria-valuemin="15.0"
      aria-valuemax="25.0"
      aria-valuenow="20.0"
      aria-valuetext="20 degrees Celsius"
      style="top: calc((25 - 20)*2rem - 0.5rem)"></div>
  </div>
</div>
```

موقعیت دستگیره برابر است با حداکثر مقدار منهای مقدار فعلی، ضرب در ارتفاع یک درجه، منهای نصف ارتفاع دستگیره برای وسط‌چین کردن آن. بقیهٔ استایل‌ها ثابت هستند.

```css
[id="temperatureSlider"] {
  position: relative;
  height: 20rem;
  width: 1rem;
  outline: 1px solid;
  margin: 3rem;
}

[id="temperatureSliderThumb"] {
  position: absolute;
  height: 1rem;
  width: 2rem;
  background-color: currentColor;
  left: -0.5rem;
}
```

برای اینکه این مثال کار کند، باید یک اسکریپت بنویسیم که همهٔ رویدادهای صفحه‌کلید و رویدادهای اشاره‌گر را مدیریت کند، از جمله شنونده‌های رویداد برای `pointermove`، `pointerup`، `focus`، `blur` و `keydown`، و استایل‌هایی برای حالت پیش‌فرض و زمانی که دستگیره و اسلایدر فوکوس دریافت می‌کنند فراهم کند. موقعیت دستگیره، مقادیر `aria-valuenow` و `aria-valuetext` و متن داخلی عنصری با [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) برابر با "temperatureValue" باید هر بار که کلیدهای <kbd>ArrowLeft</kbd>، <kbd>ArrowDown</kbd>، <kbd>ArrowRight</kbd>، <kbd>ArrowUp</kbd>، <kbd>Home</kbd>، <kbd>End</kbd> و به‌صورت اختیاری <kbd>PageDown</kbd> و <kbd>PageUp</kbd> رها می‌شوند و همچنین زمانی که کاربر دستگیره را می‌کشد یا روی اسلایدر دما کلیک می‌کند، به‌روزرسانی شوند.

با استفاده از HTML معنایی، این مثال می‌توانست به شکل زیر نوشته شود:

```html
<label for="temperature"> Temperature </label>
<output id="temperatureValue">20°C</output>
<input
  type="range"
  id="temperatureSlider"
  min="15"
  max="25"
  step="0.1"
  value="20"
  aria-valuetext="20 degrees celsius" />
```

```css
#temperatureSlider {
  transform: rotate(-90deg);
}
```

با استفاده از {{HTMLElement('input')}}، یک ویجت ورودی بازه‌ای از پیش استایل‌سازیشده با فوکوس صفحه‌کلید، استایل فوکوس، تعاملات صفحه‌کلید و `value` که در تعامل با کاربر به‌روزرسانی می‌شود، به‌صورت رایگان دریافت می‌کنیم. همچنان باید از جاوااسکریپت برای تغییر `aria-valuetext` و مقدار عنصر {{HTMLElement('output')}} استفاده کنیم.

روش‌های مختلفی برای عمودی کردن یک ورودی بازه‌ای وجود دارد. در این مثال، از [تبدیل‌های CSS](/en-US/docs/Web/CSS/Reference/Properties/transform) استفاده کردیم.

## بهترین روش‌ها

اگر اسلایدر پیشرفت بارگذاری یک ناحیهٔ خاص از صفحه را توصیف می‌کند، ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) را برای ارجاع به وضعیت اسلایدر اضافه کنید و ویژگی [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) را روی آن ناحیه به `true` تنظیم کنید تا بارگذاری آن به پایان برسد.

`<input type="range">` در HTML به‌صورت ضمنی دارای `role` برابر با `slider` است. از ویژگی‌های `aria-valuemax` یا `aria-valuemin` روی عناصر `<input type="range">` استفاده نکنید؛ به‌جای آن‌ها از `min` و `max` استفاده کنید. در غیر این صورت، می‌توان از هر ویژگی سراسری `aria-*` و هر ویژگی `aria-*` دیگری که برای نقش `slider` قابل اعمال است استفاده کرد.

### اولویت با HTML

توصیه می‌شود به‌جای نقش `slider` از یک {{HTMLElement("input")}} بومی از نوع `range`، یعنی [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range)، استفاده کنید.

## مشخصات

{{Specifications}}

## بیشتر ببینید

- [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range)،
- عنصر HTML {{HTMLElement('progress')}}
- عنصر HTML {{HTMLElement('meter')}}
- سایر ویجت‌های بازه‌ای عبارت‌اند از:
  - [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
  - [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
  - [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) (در صورت قابل فوکوس بودن)
  - [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)
  - [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- نمونه‌های W3C WAI-ARIA practices:
  - [Horizontal Multi-Thumb Slider](https://www.w3.org/WAI/ARIA/apg/patterns/slider-multithumb/examples/slider-multithumb/)
  - [Color Viewer Slider](https://www.w3.org/WAI/ARIA/apg/patterns/slider/examples/slider-color-viewer/)
  - [Rating Slider](https://www.w3.org/WAI/ARIA/apg/patterns/slider/examples/slider-rating/)
  - [Media Seek Slider](https://www.w3.org/WAI/ARIA/apg/patterns/slider/examples/slider-seek/)
  - [Vertical Temperature Slider](https://www.w3.org/WAI/ARIA/apg/patterns/slider/examples/slider-temperature/)