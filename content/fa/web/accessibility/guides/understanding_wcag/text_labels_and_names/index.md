---
title: "Text labels and names"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Text_labels_and_names"
translated_by: "n8n + AI"
---

---
title: Text labels and names
slug: Web/Accessibility/Guides/Understanding_WCAG/Text_labels_and_names
page-type: guide
sidebar: accessibilitysidebar
---

موقعیت‌های زیادی وجود دارد که در آن‌ها باید به یک کنترل، گفتگو یا سایر ویژگی‌های وب‌سایت، یک نام یا برچسب توصیفی داده شود تا کاربران فناوری‌های کمکی بتوانند هدف آن را درک کرده و نحوه استفاده صحیح از آن را بدانند. مشکلات مختلفی در این دسته وجود دارد که در بافت‌های متفاوتی یافت می‌شوند و هرکدام راه‌حل مخصوص به خود را دارند. مشکلات و راه‌حل‌های مختلف در بخش‌های زیر بحث شده‌اند.

## برای برچسب‌گذاری عناصر area که دارای ویژگی href هستند از ویژگی alt استفاده کنید

در نقشه‌های تصویری، به هر عنصر {{htmlelement("area")}} یک ویژگی `alt` حاوی نامی بدهید که توصیف می‌کند آن ناحیه به چه منابعی پیوند می‌دهد. انجام ندادن این کار، استفاده از نقشه تصویری را برای کاربران فناوری کمکی دشوار می‌کند — آن‌ها برای درک هدف یک تصویر به متن جایگزین نیاز دارند.

### مثال‌ها

مثال زیر یک نقشه تصویری را نشان می‌دهد (برگرفته از [H24: ارائه متن جایگزین برای عناصر area در نقشه‌های تصویری](https://www.w3.org/TR/WCAG20-TECHS/H24.html)):

```html
<img
  src="welcome.gif"
  usemap="#map1"
  alt="Areas in the library. Select an area for
more information on that area." />
<map id="map1" name="map1">
  <area shape="rect" coords="0,0,30,30" href="reference.html" alt="Reference" />
  <area
    shape="rect"
    coords="34,34,100,100"
    href="media.html"
    alt="Audio visual lab" />
</map>
```

برای مشاهده یک مثال تعاملی زنده، به [صفحه مرجع عنصر `<area>`](/en-US/docs/Web/HTML/Reference/Elements/area) مراجعه کنید.

### همچنین ببینید

- {{htmlelement("area")}}
- [H24: ارائه متن جایگزین برای عناصر area در نقشه‌های تصویری](https://www.w3.org/TR/WCAG20-TECHS/H24.html)

## گفتگوها باید برچسب‌گذاری شوند

برای هر ظرفی که محتویات آن به‌عنوان کادر گفتگو عمل می‌کند (مثلاً یک گفتگوی مُدال که از کاربر می‌خواهد انتخابی کند یا به اقدامی که انجام شده پاسخ دهد)، یک برچسب یا نام توصیفی به آن بدهید تا کاربران فناوری کمکی به‌راحتی بتوانند هدف آن را کشف کنند.

یک کادر گفتگو معمولاً با ARIA [`role="dialog"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) یا [`role="alertdialog"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role) نشان داده می‌شود؛ می‌توانید از ویژگی‌های [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای ارائه برچسب استفاده کنید.

### مثال‌ها

مثال زیر یک کادر گفتگو را نشان می‌دهد که با استفاده از `role="dialog"` تعریف شده و با `aria-labelledby` برچسب‌گذاری شده است.

```html
<div
  role="dialog"
  aria-labelledby="dialog1Title"
  aria-describedby="dialog1Desc">
  <h2 id="dialog1Title">Your personal details were successfully updated</h2>
  <p id="dialog1Desc">
    You can change your details at any time in the user account section.
  </p>
  <button>Close</button>
</div>
```

اگر کادر گفتگو سرتیتری ندارد، می‌توانید به‌جای آن از `aria-label` برای درج متن برچسب استفاده کنید:

```html
<div role="dialog" aria-label="Personal details updated confirmation">
  <p>
    Your personal details were successfully updated. You can change your details
    at any time in the user account section.
  </p>
  <button>Close</button>
</div>
```

### همچنین ببینید

- [`role="dialog"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)
- [`role="alertdialog"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role)
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- [روش‌های تألیف گفتگو](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/)

## اسناد باید دارای عنوان (title) باشند

در هر سند HTML مهم است که یک {{htmlelement("title")}} گنجانده شود که هدف صفحه را توصیف می‌کند. یک تکنیک رایج ناوبری برای کاربران فناوری کمکی این است که محتوای یک صفحه را با خواندن عنوان آن استنباط کنند. اگر عنوان در دسترس نباشد، آن‌ها باید در صفحه پیمایش کنند تا محتوای آن را تعیین کنند، که می‌تواند فرآیندی زمان‌بر و بالقوه گیج‌کننده باشد.

### مثال‌ها

عنوان مقاله مرجع درباره عنصر {{htmlelement("title")}} به این صورت است:

```html
<title>
  &lt;title&gt;: The Document Title element - HTML: Hypertext Markup Language |
  MDN
</title>
```

مثال دیگر می‌تواند به این شکل باشد:

```html
<title>Fill in your details to register — myGov services</title>
```

برای کمک به کاربر، می‌توانید مقدار عنوان صفحه را به‌روزرسانی کنید تا تغییرات مهم وضعیت صفحه (مانند مشکلات اعتبارسنجی فرم) را منعکس کند:

```html
<title>2 errors — Fill in your details to register — myGov services</title>
```

### همچنین ببینید

- {{htmlelement("title")}}

## محتوای تعبیه‌شده باید برچسب‌گذاری شود

اطمینان حاصل کنید که عناصری که محتوا را تعبیه می‌کنند دارای ویژگی [title](/en-US/docs/Web/HTML/Reference/Global_attributes/title) هستند که محتوای تعبیه‌شده را توصیف می‌کند. این شامل عناصر {{htmlelement("embed")}} و {{htmlelement("object")}} می‌شود. این عناصر اغلب برای محتوای گرافیکی استفاده می‌شوند، بسیار شبیه به عنصر {{HTMLelement("img")}}. یک عنوان توصیفی به کاربران فناوری کمکی کمک می‌کند تا بفهمند عنصر چه چیزی را نشان می‌دهد.

## شکل‌ها (Figures) با زیرنویس اختیاری باید برچسب‌گذاری شوند

برای بهترین دسترس‌پذیری، یک {{HTMLElement("figcaption")}} را در داخل عنصر {{HTMLElement("figure")}} قرار دهید، حتی اگر از نظر فنی اختیاری باشد. زیرنویس علاوه بر هر متن جایگزینی برای تصاویر داخل شکل است. زیرنویس هدف شکل را در سند توصیف می‌کند، که ممکن است با توصیف یک آیتم بصری، همان‌طور که توسط متن جایگزین ارائه می‌شود، متفاوت باشد.

### مثال

مثال زیر کدی برای یک شکل با زیرنویس نشان می‌دهد. ویژگی `alt` عنصر {{htmlelement("img")}} ظاهر تصویر را توصیف می‌کند؛ {{htmlelement("figcaption")}} آن را از دیدگاه عملکردی توصیف می‌کند (در این مورد، نام لاتین گل در تصویر).

```html
<figure>
  <img
    src="milkweed.jpg"
    alt="Black and white close-up photo of milkweed flowers" />
  <figcaption>Asclepias verticillata</figcaption>
</figure>
```

## عناصر Fieldset باید برچسب‌گذاری شوند

عناصر Fieldset باید مانند سایر عناصر فرم دارای توضیح متنی باشند. از عنصر {{htmlelement("legend")}} برای توصیف هدف یک fieldset استفاده کنید.

## برای برچسب‌گذاری یک fieldset از legend استفاده کنید

هنگامی که مجموعه‌ای از عناصر فرم را با یک عنصر {{htmlelement("fieldset")}} گروه‌بندی می‌کنید، باید یک عنصر تودرتوی {{htmlelement("legend")}} در داخل آن قرار دهید که شامل توضیح واضحی از گروه باشد.

کاربران فناوری کمکی این توضیح را هنگام تلاش برای درک هدف کلی گروه مفید می‌یابند. بدون legend، آن‌ها باید در میان کنترل‌های فرم منفرد در گروه پیمایش کنند تا ایده‌ای از هدف کلی به دست آورند، که می‌تواند منجر به سردرگمی شود.

### مثال‌ها

```html
<form>
  <fieldset>
    <legend>Choose your favorite monster</legend>

    <input type="radio" id="kraken" name="monster" value="K" />
    <label for="kraken">Kraken</label><br />

    <input type="radio" id="sasquatch" name="monster" value="S" />
    <label for="sasquatch">Sasquatch</label><br />

    <input type="radio" id="mothman" name="monster" value="M" />
    <label for="mothman">Mothman</label>
  </fieldset>
</form>
```

می‌توانید نسخه زنده و تعاملی این مثال را در [صفحه مرجع `<fieldset>`](/en-US/docs/Web/HTML/Reference/Elements/fieldset) مشاهده کنید.

### همچنین ببینید

- {{htmlelement("fieldset")}}
- {{htmlelement("legend")}}

## عناصر فرم باید برچسب‌گذاری شوند

همه عناصر درون یک فرم باید یک {{htmlelement("label")}} داشته باشند که هدف آن را مشخص کند. این برای همه انواع موارد {{htmlelement("input")}} و همچنین عناصر {{htmlelement("button")}}، {{htmlelement("output")}}، {{htmlelement("select")}}، {{htmlelement("textarea")}}، {{htmlelement("progress")}} و {{htmlelement("meter")}}، و همچنین هر عنصری با [نقش ARIA switch](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role) صدق می‌کند.

عنصر فرم را می‌توان در داخل {{htmlelement("label")}} قرار داد، در این صورت ارتباط بین عنصر فرم و برچسب از ساختار مشخص است. همچنین می‌توانید با تعیین مقدار `id` عنصر فرم به‌عنوان مقدار ویژگی `for` برچسب، ارتباطی بین {{htmlelement("label")}} و یک عنصر فرم ایجاد کنید.

### مثال

```html
<label
  >I agree to the terms and conditions.
  <input type="checkbox" id="terms" name="terms" />
</label>

<input type="checkbox" id="email-opt-in" name="opt-in" />
<label for="email-opt-in">Yes, please send me news about this product.</label>
```

## عناصر فرم باید دارای برچسب متنی قابل مشاهده باشند

علاوه بر داشتن {{htmlelement("label")}} برای هر عنصر فرم، این برچسب‌ها باید قابل مشاهده باشند، نه پنهان. برچسب‌های قابل مشاهده به _همه_ کاربران کمک می‌کنند تا هدف یک عنصر فرم را درک کنند. به متن placeholder (متن راهنما) تکیه نکنید، زیرا به محض شروع تایپ کاربر ناپدید می‌شود.

## عناصر قاب (Frame) باید برچسب‌گذاری شوند

عناصر قاب، هم {{htmlelement("iframe")}} و هم {{htmlelement("frame")}} قدیمی و منسوخ، باید دارای عنوانی برای توصیف محتویات قاب باشند. از ویژگی `title` برای برچسب‌گذاری یک عنصر قاب استفاده کنید. بدون عنوان، کاربران فناوری‌های کمکی باید برای درک محتوای قاب به داخل آن پیمایش کنند، که می‌تواند دشوار و گیج‌کننده باشد.

عنصر {{HTMLElement('frame')}} دیگر بخشی از مشخصات HTML نیست. پشتیبانی از آن ممکن است در آینده توسط مرورگرها حذف شود. علاوه بر این، برای صفحه‌خوان‌ها پیمایش صفحات دارای عناصر {{HTMLElement('frame')}} دشوار است. برای بهترین دسترس‌پذیری و نگهداری در آینده، هر صفحه‌ای که از قاب‌ها استفاده می‌کند را بازطراحی کنید تا با استفاده از CSS به چیدمان مشابهی دست یابید.

به‌عنوان یک بهترین روش، همچنین یک {{htmlelement("title")}} برای سندی که در قاب محصور شده است فراهم کنید، با محتوایی یکسان با ویژگی `title` قاب. (این فرض می‌کند که سند محصور تحت کنترل شماست؛ اگر نه، سعی کنید ویژگی `title` قاب را با عنوان سند مطابقت دهید.) برخی صفحه‌خوان‌ها محتویات ویژگی `title` را با محتویات {{htmlelement("title")}} سند محصور جایگزین می‌کنند. امن‌ترین و در دسترس‌ترین کار این است که عنوان یکسانی را در هر دو مکان ارائه دهید.

### مثال

```html
<iframe
  title="MDN Web docs"
  width="300"
  height="200"
  src="https://developer.mozilla.org">
</iframe>
```

## سرتیترها باید برچسب‌گذاری شوند

مطمئن شوید که سرتیترهای شما دارای محتوای متنی غیر خالی هستند و پنهان نیستند، مانند استفاده از CSS `display:none` یا `aria-hidden=true`. کاربران صفحه‌خوان برای درک ساختار و محتوای یک سند به سرتیترها تکیه می‌کنند.

همچنین، مطمئن شوید که از [عناصر سرتیتر](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) فقط برای سرتیترهای واقعی بخش‌ها استفاده می‌کنید، نه به‌عنوان یک راه میانبر برای برجسته کردن متن. کاربران صفحه‌خوان معمولاً سرتیترهای صفحه را «مرور» می‌کنند، بسیار شبیه به کاربران بینا؛ متنی که سرتیتر نیست اما با عناصر سرتیتر علامت‌گذاری شده باشد می‌تواند باعث سردرگمی شود.

## سرتیترها باید دارای محتوای متنی قابل مشاهده باشند

مطمئن شوید که سرتیترهای شما دارای محتوای متنی غیر خالی هستند و پنهان نیستند، مانند استفاده از CSS `display:none` یا `aria-hidden=true`. کاربران صفحه‌خوان برای درک ساختار و محتوای یک سند به سرتیترها تکیه می‌کنند. از عناصر سرتیتر برای علامت‌گذاری تصاویر یا سایر محتوای گرافیکی استفاده نکنید.

## برای توصیف محتوای `<iframe>` از ویژگی title استفاده کنید

مطمئن شوید که عناصر {{htmlelement("iframe")}} دارای ویژگی `title` برای توصیف محتویات قاب هستند. بدون عنوان، کاربران فناوری‌های کمکی باید برای درک محتوای قاب به داخل آن پیمایش کنند، که می‌تواند دشوار و گیج‌کننده باشد.

به‌عنوان یک بهترین روش، همچنین یک {{htmlelement("title")}} برای سندی که در قاب محصور شده است فراهم کنید، با محتوایی یکسان با ویژگی `title` قاب. (این فرض می‌کند که سند محصور تحت کنترل شماست؛ اگر نه، سعی کنید ویژگی `title` قاب را با عنوان سند مطابقت دهید.) برخی صفحه‌خوان‌ها محتویات ویژگی `title` را با محتویات {{htmlelement("title")}} سند محصور جایگزین می‌کنند. امن‌ترین و در دسترس‌ترین کار این است که عنوان یکسانی را در هر دو مکان ارائه دهید.

## محتوای دارای تصویر باید برچسب‌گذاری شود

برای همه تصاویر دارای محتوا (یعنی غیر تزئینی) و عناصر ش