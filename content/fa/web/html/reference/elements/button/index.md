---
title: "<button> HTML button element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button"
translated_by: "n8n + AI"
---

عنصر `<button>` در HTML یک عنصر تعاملی است که کاربر می‌تواند با ماوس، صفحه‌کلید، لمس، فرمان صوتی یا هر فناوری کمکی دیگر آن را فعال کند. پس از فعال‌شدن، یک عمل مانند ارسال یک فرم (form) یا باز کردن یک دیالوگ (dialog) انجام می‌دهد.

به‌طور پیش‌فرض، دکمه‌های HTML به شکلی نمایش داده می‌شوند که شبیه پلتفرم عامل user agent است، اما می‌توانید با استفاده از CSS ظاهر آن‌ها را تغییر دهید.

```html interactive-example
<button class="favorite styled" type="button">Add to favorites</button>
```

```css interactive-example
.styled {
  border: 0;
  line-height: 2.5;
  padding: 0 20px;
  font-size: 1rem;
  text-align: center;
  color: white;
  text-shadow: 1px 1px 1px black;
  border-radius: 10px;
  background-color: tomato;
  background-image: linear-gradient(
    to top left,
    rgb(0 0 0 / 0.2),
    rgb(0 0 0 / 0.2) 30%,
    transparent
  );
  box-shadow:
    inset 2px 2px 3px rgb(255 255 255 / 0.6),
    inset -2px -2px 3px rgb(0 0 0 / 0.6);
}

.styled:hover {
  background-color: red;
}

.styled:active {
  box-shadow:
    inset -2px -2px 3px rgb(255 255 255 / 0.6),
    inset 2px 2px 3px rgb(0 0 0 / 0.6);
}
```

## ویژگی‌ها (Attributes)

ویژگی‌های این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) (ویژگی‌های سراسری) نیز می‌شود.

- `autofocus`
  - : یک ویژگی Boolean است. اگر وجود داشته باشد، مشخص می‌کند که دکمه به‌محض بارگذاری صفحه، focus (تمرکز ورودی) بگیرد. **فقط یک عنصر در سند می‌تواند این ویژگی را داشته باشد.**

- `command`
  - : عملی را که باید روی یک عنصر تحت کنترل، که توسط دکمهٔ `<button>` با ویژگی `commandfor` مشخص شده، انجام شود را تعیین می‌کند. مقادیر ممکن عبارتند از:
    - `"show-modal"`
      - : دکمه، یک `<dialog>` را به‌صورت modal نمایش می‌دهد. اگر dialog از قبل modal باشد، هیچ اقدامی انجام نمی‌شود. این معادل declarative برای فراخوانی متد `HTMLDialogElement.showModal()` روی عنصر `<dialog>` است.
    - `"close"`
      - : دکمه، یک عنصر `<dialog>` را می‌بندد. اگر dialog از قبل بسته باشد، هیچ اقدامی انجام نمی‌شود. این معادل declarative برای فراخوانی متد `HTMLDialogElement.close()` روی عنصر `<dialog>` است. وقتی با ویژگی `value` استفاده شود، مقدار دکمه به‌عنوان ویژگی `returnValue` به dialog منتقل می‌شود.
    - `"request-close"`
      - : دکمه، یک رویداد `cancel` روی عنصر `<dialog>` ایجاد می‌کند تا از مرورگر بخواهد آن را ببندد و سپس یک رویداد `close` رخ می‌دهد. این رفتار با دستور `close` تفاوت دارد؛ در این حالت توسعه‌دهندگان می‌توانند روی رویداد `cancel` متد `Event.preventDefault()` را فراخوانی کنند تا از بسته‌شدن `<dialog>` جلوگیری شود. اگر dialog از قبل بسته باشد، هیچ اقدامی انجام نمی‌شود. این معادل declarative برای فراخوانی متد `HTMLDialogElement.requestClose()` روی عنصر `<dialog>` است. وقتی با ویژگی `value` دکمه استفاده شود، مقدار به‌عنوان ویژگی `returnValue` به dialog منتقل می‌شود.
    - `"show-popover"`
      - : دکمه، یک popover مخفی را نمایش می‌دهد. اگر سعی کنید یک popover که در حال نمایش است را دوباره نمایش دهید، هیچ اقدامی انجام نمی‌شود. برای جزئیات بیشتر به Popover API مراجعه کنید. این معادل مقدار `show` برای ویژگی `popovertargetaction` است و همچنین معادل declarative برای فراخوانی متد `HTMLElement.showPopover()` روی عنصر popover است.
    - `"hide-popover"`
      - : دکمه، یک popover در حال نمایش را مخفی می‌کند. اگر سعی کنید یک popover که از قبل مخفی است را دوباره مخفی کنید، هیچ اقدامی انجام نمی‌شود. برای جزئیات بیشتر به Popover API مراجعه کنید. این معادل مقدار `hide` برای ویژگی `popovertargetaction` است و همچنین معادل declarative برای فراخوانی متد `HTMLElement.hidePopover()` روی عنصر popover است.
    - `"toggle-popover"`
      - : دکمه، وضعیت یک popover را بین نمایش و مخفی‌بودن تغییر می‌دهد. اگر popover مخفی باشد، نمایش داده می‌شود و اگر در حال نمایش باشد، مخفی می‌شود. برای جزئیات بیشتر به Popover API مراجعه کنید. این معادل مقدار `toggle` برای ویژگی `popovertargetaction` است و همچنین معادل declarative برای فراخوانی متد `HTMLElement.togglePopover()` روی عنصر popover است.
    - Custom values
      - : این ویژگی می‌تواند مقادیر سفارشی را نشان دهد که با دو خط تیره (`--`) شروع می‌شوند. دکمه‌هایی با مقدار سفارشی، رویداد `CommandEvent` را روی عنصر کنترل‌شده ارسال می‌کنند.

- `commandfor`  
  - عنصر `<button>` را به یک دکمه‌ی فرمان تبدیل می‌کند و یک عنصر تعاملی مشخص را با استفاده از فرمانی که در attribute [`command`](#command) دکمه تعریف شده کنترل می‌کند. مقدار `commandfor` باید id عنصری باشد که قرار است کنترل شود. این attribute نسخه‌ای عمومی‌تر از [`popovertarget`](#popovertarget) است.

- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)  
  - این attribute بولین از تعامل کاربر با دکمه جلوگیری می‌کند: دکمه قابل کلیک یا فوکوس نیست.

- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)  
  - عنصر `<form>`ای که دکمه به آن متصل می‌شود (مالک فرم دکمه). مقدار این attribute باید `id` یک `<form>` در همان سند باشد. (اگر این attribute تنظیم نشود، `<button>` به عنصر `<form>`‌ای که ancestor آن است متصل می‌شود، در صورت وجود.)  
  - این attribute به شما امکان می‌دهد عناصر `<button>` را به `<form>`هایی در هر جای سند متصل کنید، نه فقط داخل یک `<form>`. همچنین می‌تواند یک `<form>` ancestor را نادیده بگیرد.

- `formaction`  
  - آدرسی (URL) که اطلاعات ارسال‌شده توسط دکمه را پردازش می‌کند. این attribute مقدار [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) مالک فرم دکمه را نادیده می‌گیرد. اگر مالک فرمی وجود نداشته باشد، کاری انجام نمی‌دهد.

- `formenctype`  
  - اگر دکمه از نوع submit باشد (داخل یا متصل به یک `<form>` باشد و `type="button"` نداشته باشد)، مشخص می‌کند که داده‌های فرم هنگام ارسال چگونه کدگذاری شوند. مقادیر ممکن:  
    - `application/x-www-form-urlencoded`: پیش‌فرض در صورت عدم استفاده از attribute.  
    - `multipart/form-data`: برای ارسال عناصر {{HTMLElement("input")}} که attribute [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) آنها `file` است استفاده می‌شود.  
    - `text/plain`: به عنوان ابزار اشکال‌زدایی مشخص شده و نباید برای ارسال واقعی فرم استفاده شود.  
  - اگر این attribute مشخص شود، مقدار [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) مالک فرم دکمه را نادیده می‌گیرد.

- `formmethod`  
  - اگر دکمه از نوع submit باشد (داخل یا متصل به یک `<form>` باشد و `type="button"` نداشته باشد)، این attribute [روش HTTP](/en-US/docs/Web/HTTP/Reference/Methods) مورد استفاده برای ارسال فرم را مشخص می‌کند. مقادیر ممکن:  
    - `post`: داده‌های فرم در بدنه‌ی درخواست HTTP به سرور فرستاده می‌شوند. وقتی فرم حاوی اطلاعاتی مانند رمز عبور است که نباید عمومی باشد از این روش استفاده کنید.  
    - `get`: داده‌های فرم به انتهای URL مشخص‌شده در `action` فرم اضافه می‌شوند (با جداکننده `?`) و URL حاصل به سرور ارسال می‌شود. این روش را زمانی استفاده کنید که فرم [اثر جانبی ندارد](/en-US/docs/Glossary/Idempotent)، مثل فرم‌های جستجو.  
    - `dialog`: این روش نشان می‌دهد که دکمه، [dialog](/en-US/docs/Web/HTML/Reference/Elements/dialog) متصل به خود را می‌بندد و داده‌های فرم را اصلاً ارسال نمی‌کند.  
  - اگر مشخص شود، این attribute مقدار [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) مالک فرم دکمه را نادیده می‌گیرد.

- `formnovalidate`  
  - اگر دکمه از نوع submit باشد، این attribute بولین مشخص می‌کند که فرم هنگام ارسال [اعتبارسنجی](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) نشود. اگر این attribute مشخص شود، مقدار [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) مالک فرم دکمه را نادیده می‌گیرد.  
  - این attribute در عناصر [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) و [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) نیز موجود است.

- `formtarget`
  - : اگر دکمه یک دکمهٔ submit باشد، این attribute یک نام تعریف‌شده توسط نویسنده یا یک کلیدواژه استاندارد با پیشوند underscore است که مشخص می‌کند پاسخ ارسال فرم کجا نمایش داده شود. این مقدار، `name` یا کلیدواژه‌ای برای یک _browsing context_ (یک تب، پنجره یا `<iframe>`) است. اگر این attribute مشخص شده باشد، [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) مربوط به فرمِ مالکِ دکمه را override می‌کند. کلیدواژه‌های زیر معانی خاصی دارند:
    - `_self`: پاسخ در همان browsing context فعلی بارگذاری می‌شود. اگر attribute مشخص نشده باشد، این مقدار پیش‌فرض است.
    - `_blank`: پاسخ در یک browsing context جدید بدون نام بارگذاری می‌شود — معمولاً یک تب یا پنجره جدید، بسته به تنظیمات مرورگر کاربر.
    - `_parent`: پاسخ در browsing context والدِ context فعلی بارگذاری می‌شود. اگر والد وجود نداشته باشد، این گزینه مثل `_self` عمل می‌کند.
    - `_top`: پاسخ در browsing context سطح بالا (یعنی browsing context که جدِ context فعلی است و والد ندارد) بارگذاری می‌شود. اگر والد وجود نداشته باشد، این گزینه مثل `_self` عمل می‌کند.

- `interestfor`
  - : عنصر `<button>` را به عنوان یک **interest invoker** تعریف می‌کند. مقدار آن، `id` یک عنصر هدف است که وقتی روی عنصر invoker علاقه (interest) نشان داده شود یا از بین برود (مثلاً با هاور/خروج هاور یا فوکوس/از فوکوس خارج شدن)، به نحوی تحت تأثیر قرار می‌گیرد (معمولاً نمایش داده می‌شود یا پنهان می‌شود). برای جزئیات و مثال‌های بیشتر، [Using interest invokers](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) را ببینید.

- `name`
  - : نام دکمه است که وقتی دکمه برای ارسال فرم استفاده می‌شود، به‌صورت یک جفت با `value` دکمه به‌عنوان بخشی از داده‌های فرم ارسال می‌شود.

- `popovertarget`
  - : عنصر `<button>` را به یک دکمه کنترل popover تبدیل می‌کند؛ مقدار خود را به‌عنوان ID عنصر popover ای که باید کنترل شود می‌گیرد. برقراری رابطه بین یک popover و دکمه invoker آن با استفاده از attribute `popovertarget` دو اثر مفید اضافه دارد:
    - مرورگر یک رابطه ضمنی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) و [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) بین popover و invoker ایجاد می‌کند و هنگام نمایش، popover را در موقعیت منطقی در ترتیب ناوبری با کیبورد (keyboard focus navigation) قرار می‌دهد. این کار popover را برای کاربران کیبورد و فناوری کمکی (AT) دسترس‌پذیرتر می‌کند (همچنین به [ویژگی‌های دسترس‌پذیری Popover](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features) مراجعه کنید).
    - مرورگر یک مرجع anchor ضمنی بین این دو ایجاد می‌کند و در نتیجه موقعیت‌دهی popover نسبت به کنترل‌هایش با استفاده از [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار راحت می‌شود. برای جزئیات بیشتر به [Popover anchor positioning](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

- `popovertargetaction`
  - : مشخص می‌کند چه اقدامی روی عنصر popover ای که توسط یک `<button>` کنترل‌کننده کنترل می‌شود انجام شود. مقادیر ممکن عبارتند از:
    - `"hide"`
      - : دکمه یک popover نمایش‌داده‌شده را پنهان می‌کند. اگر تلاش کنید یک popover از قبل پنهان را پنهان کنید، هیچ اقدامی انجام نمی‌شود.
    - `"show"`
      - : دکمه یک popover پنهان را نمایش می‌دهد. اگر تلاش کنید یک popover که در حال نمایش است را دوباره نشان دهید، اقدامی صورت نمی‌گیرد.
    - `"toggle"`
      - : دکمه وضعیت popover را بین نمایش و پنهان بودن تغییر می‌دهد. اگر popover پنهان باشد، نمایش داده می‌شود؛ اگر در حال نمایش باشد، پنهان می‌شود. اگر `popovertargetaction` حذف شود، `"toggle"` عمل پیش‌فرضی است که توسط دکمه کنترل‌کننده انجام می‌شود.

- `type`
  - : رفتار پیش‌فرض دکمه. مقادیر ممکن عبارت‌اند از:
    - `submit`: دکمه داده‌های فرم را به سرور ارسال می‌کند. اگر این ویژگی برای دکمه‌های مرتبط با یک `<form>` مشخص نشده باشد، یا مقدار آن خالی یا نامعتبر باشد، این مقدار پیش‌فرض است.
    - `reset`: دکمه همه کنترل‌ها را به مقادیر اولیه بازنشانی می‌کند، مانند [\<input type="reset">](/en-US/docs/Web/HTML/Reference/Elements/input/reset). (این رفتار معمولاً کاربران را آزار می‌دهد.)
    - `button`: دکمه رفتار پیش‌فرضی ندارد و در حالت پیش‌فرض با فشردن، کاری انجام نمی‌دهد. می‌توان اسکریپت‌های سمت کلاینت را به شنیدن رویدادهای این عنصر گماشت؛ این رویدادها هنگام رخ دادنشان فعال می‌شوند.

- `value`
  - : مقداری را تعریف می‌کند که هنگام ارسال داده‌های فرم، همراه با `name` دکمه ارسال می‌شود. این مقدار، وقتی فرم با این دکمه ارسال می‌شود، در پارامترها به سرور منتقل می‌شود. وقتی با فرمان‌های `close` یا `request-close` استفاده شود، ویژگی `value` مقدار `returnValue` عنصر `<dialog>` کنترل‌شده را تنظیم می‌کند.

## نکته‌ها

دکمه ارسال (submit) که ویژگی `formaction` برایش تنظیم شده اما فرم مرتبط ندارد، هیچ کاری نمی‌کند. باید صاحب فرم را تعیین کنید؛ یا آن را در یک `<form>` قرار دهید یا ویژگی `form` را به `id` فرم موردنظر تنظیم کنید.

عناصر `<button>` بسیار راحت‌تر از عناصر `<input>` استایل می‌گیرند. می‌توانید محتوای HTML داخلی اضافه کنید (مثل `<i>`، `<br>` یا حتی `<img>`) و از شبه‌عنصرهای `::after` و `::before` برای رندر پیچیده استفاده کنید.

اگر دکمه‌های شما برای ارسال داده‌های فرم به سرور نیستند، حتماً ویژگی `type` آن‌ها را روی `button` قرار دهید. در غیر این صورت، سعی می‌کنند داده‌های فرم را ارسال کنند و پاسخ (ناموجود) را بارگذاری کنند که ممکن است وضعیت فعلی سند را از بین ببرد.

در حالی که `<button type="button">` رفتار پیش‌فرضی ندارد، می‌توان رویدادگردان‌ها را برای فعال‌سازی رفتارها اسکریپت‌نویسی کرد. یک دکمه فعال می‌تواند با استفاده از [JavaScript](/en-US/docs/Learn_web_development/Core/Scripting) اقدامات برنامه‌پذیری انجام دهد، مثلاً حذف یک مورد از فهرست.

به‌طور پیش‌فرض، عامل کاربر دکمه‌ها را با `display: flow-root` استایل می‌دهد که یک [بافت قالب‌بندی بلوکی](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) جدید ایجاد می‌کند و فرزندان دکمه را تا زمانی که سرریز نکنند، هم به‌صورت افقی و هم عمودی وسط‌چین می‌کند. اگر دکمه به‌عنوان یک کانتینر فلکس یا گرید تعریف شود، فرزندان مانند آیتم‌های فلکس یا گرید رفتار می‌کنند. دکمه‌ای که `display: inline` دارد، طوری استایل می‌شود که گویی مقدار `display: inline-block` تنظیم شده است.

## دسترس‌پذیری

### دکمه‌های آیکونی

دکمه‌هایی که فقط یک آیکون نمایش می‌دهند، نام دسترس‌پذیر (accessible name) ندارند. نام‌های دسترس‌پذیر اطلاعاتی را برای فناوری کمکی مانند صفحه‌خوان‌ها فراهم می‌کنند تا هنگام تجزیه سند و تولید [درخت دسترس‌پذیری](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) به آن دسترسی داشته باشند. سپس فناوری کمکی از درخت دسترس‌پذیری برای پیمایش و دستکاری محتوای صفحه استفاده می‌کند.

برای دادن نام دسترس‌پذیر به دکمه آیکونی، متنی را در عنصر `<button>` قرار دهید که عملکرد دکمه را به‌طور خلاصه توصیف کند.

#### مثال‌ها

```html
<button name="favorite">
  <svg fill="black" viewBox="0 0 42 42">
    <path
      d="M21,1c1.081,0,5.141,12.315,6.201,13.126s13.461,1.053,13.791,2.137 c0.34,1.087-9.561,8.938-9.961,10.252c-0.409,1.307,
      3.202,13.769,2.331,14.442c-0.879,0.673-11.05-6.79-12.361-6.79 c-1.311,0-11.481,7.463-12.36,6.79c-0.871-0.674,2.739-13.136,
      2.329-14.442c-0.399-1.313-10.3-9.165-9.96-10.252 c0.33-1.084,12.731-1.326,13.791-2.137S19.91,1,21,1z"></path>
  </svg>
  Add to favorites
</button>
```

##### نتیجه

اگر میخواهید متن دکمه را به صورت بصری مخفی کنید، یک روش دسترسپذیر این است که از [ترکیبی از ویژگیهای CSS](https://www.a11yproject.com/posts/how-to-hide-content/) استفاده کنید تا آن را از نظر بصری از صفحه حذف کنید، اما همچنان برای فناوریهای کمکی قابل تحلیل باقی بماند.

با این حال، شایان ذکر است که قابل مشاهده نگه داشتن متن دکمه میتواند به افرادی کمک کند که ممکن است با معنای آیکون آشنا نباشند یا هدف دکمه را درک نکنند. این موضوع بهویژه برای افرادی که از نظر فنی چندان ماهر نیستند یا ممکن است برداشتهای فرهنگی متفاوتی از آیکون مورد استفاده دکمه داشته باشند، اهمیت دارد.

- [What is an accessible name? | Vispero](https://vispero.com/resources/what-is-an-accessible-name/)
- [MDN Understanding WCAG, Guideline 4.1 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Robust#guideline_4.1_—_compatible_maximize_compatibility_with_current_and_future_user_agents_including_assistive_technologies)
- [Understanding Success Criterion 4.1.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html)

### اندازه و نزدیکی

#### اندازه

عناصر تعاملی مانند دکمهها باید ناحیهای به اندازه کافی بزرگ داشته باشند تا به راحتی فعال شوند. این کار به گروههای مختلفی از افراد کمک میکند، از جمله افرادی که مشکلات کنترل حرکتی دارند و افرادی که از ورودیهای غیردقیق مانند قلم لمسی یا انگشت استفاده میکنند. حداقل اندازه تعاملی ۴۴×۴۴ [پیکسل CSS](/en-US/docs/Glossary/CSS_pixel) توصیه میشود.

- [Understanding Success Criterion 2.5.5: Target Size | W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- [Target Size and 2.5.5 | Adrian Roselli](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
- [Quick test: Large touch targets - The A11Y Project](https://www.a11yproject.com/posts/large-touch-targets/)

#### نزدیکی

اگر حجم زیادی از محتوای تعاملی (از جمله دکمهها) در مجاورت بصری نزدیک یکدیگر قرار گرفته باشد، باید فضایی بین آنها وجود داشته باشد. این فاصلهگذاری برای افرادی که مشکلات کنترل حرکتی دارند مفید است، زیرا ممکن است به طور تصادفی محتوای تعاملی اشتباهی را فعال کنند.

فاصلهگذاری را میتوان با استفاده از ویژگیهای CSS مانند `margin` ایجاد کرد.

- [Hand tremors and the giant-button-problem - Axess Lab](https://axesslab.com/hand-tremors/)

### اطلاعات وضعیت ARIA

برای توصیف وضعیت یک دکمه، ویژگی ARIA صحیح استفاده از [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) است و نه [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) یا [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected). برای اطلاعات بیشتر، اطلاعات مربوط به [ARIA button role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) را بخوانید.

### استایل دکمهها

بهتر است حلقه فوکوس پیشفرض عناصر دارای فوکوس را بازنویسی نکنید. اگر استایلهای دکمه بازنویسی میشوند، مهم است که **مطمئن شوید حالت فوکوس کنتراست کافی دارد** تا افراد با شرایط بینایی ضعیف بتوانند آن را درک کنند و افراد با تفاوتهای شناختی آن را بفهمند.

شبهکلاس `:focus-visible` میتواند برای اعمال استایل به عنصری که `:focus` دارد استفاده شود، فقط زمانی که قواعد اکتشافی عامل کاربر تشخیص دهد که فوکوس باید برجسته شود، مانند زمانی که `<button>` فوکوس صفحهکلید دریافت میکند. برای اطلاعات بیشتر، [focus vs :focus-visible](/en-US/docs/Web/CSS/Reference/Selectors/:focus-visible#focus_vs_focus-visible) را ببینید.

نسبت کنتراست رنگ با مقایسه روشنایی متن دکمه و مقادیر رنگ پسزمینه با پسزمینهای که دکمه روی آن قرار دارد تعیین میشود. برای مطابقت با [راهنمای دسترسپذیری محتوای وب (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/)، نسبت ۴.۵:۱ برای محتوای متنی و ۳:۱ برای متن بزرگ لازم است. (متن بزرگ به صورت ۱۸.۶۶ پیکسل و `bold` یا بزرگتر، یا ۲۴ پیکسل یا بزرگتر تعریف میشود.)

- [WebAIM: Color Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [MDN Understanding WCAG, Guideline 1.4 explanations](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.3 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)

### کلیک کردن و فوکوس

اینکه کلیک روی یک `<button>` یا دکمه‌های `<input>` به‌صورت پیش‌فرض فوکوس می‌گیرند یا نه، بسته به مرورگر و سیستم‌عامل متفاوت است. بیشتر مرورگرها به دکمه‌ای که کلیک می‌شود فوکوس می‌دهند، اما [سافاری به‌عمد این کار را نمی‌کند](https://webkit.org/b/22261#c68).

## مثال‌ها

### ساخت یک دکمهٔ ساده

این مثال یک دکمهٔ قابل‌کلیک می‌سازد. ویژگیِ `type="button"` تضمین می‌کند که دکمه رفتار پیش‌فرضی نداشته باشد. می‌توانید این دکمه را با جاوااسکریپت یا ویژگی‌هایی مانند `command` و `commandfor` تعاملی کنید.

```html
<button type="button" name="button">I'm a button</button>
```

### استفاده از مقدار `request-close` برای ویژگیِ `command`

در این مثال، المان `dialog` دو دکمهٔ رادیویی دارد که تعیین می‌کنند آیا dialog می‌تواند بسته شود یا نه. **Yes** یا **No** را انتخاب کنید و سپس برای امتحان بستن dialog روی **Request to Close** کلیک کنید. اگر **Yes** انتخاب شود، dialog بسته می‌شود؛ اگر **No** انتخاب شود، dialog باز می‌ماند و در عوض یک پیام نشان می‌دهد.

```html
<button type="button" commandfor="mydialog" command="show-modal">
  Open Dialog
</button>
<dialog id="mydialog">
  <div class="wrapper">
    <form>
      <fieldset>
        <legend>Allow this dialog to close when requested?</legend>
        <div>
          <input type="radio" id="no" name="close" value="no" checked />
          <label for="no">No</label>
        </div>
        <div>
          <input type="radio" id="yes" name="close" value="yes" />
          <label for="yes">Yes</label>
        </div>
      </fieldset>
    </form>
    <button commandfor="mydialog" command="request-close">
      Request to Close
    </button>
    <p class="warning" hidden>You must choose "Yes" to close this dialog.</p>
  </div>
</dialog>
```

```css hidden
.warning {
  color: tomato;
}
```

```js
const dialog = document.querySelector("dialog");
const radio = document.querySelector("form").elements["close"];
const warning = document.querySelector(".warning");

dialog.addEventListener("cancel", (e) => {
  if (!e.cancelable) return;
  if (radio.value === "no") {
    warning.hidden = false;
    e.preventDefault();
  } else {
    warning.hidden = true;
  }
});
```

دکمهٔ **Open Dialog** با استفاده از `command="show-modal"` المان `<dialog>` را باز می‌کند.

دکمهٔ **Request to Close** دارای `command="request-close"` است که با استفاده از ویژگیِ `commandfor="mydialog"` المان `<dialog>` را هدف می‌گیرد. وقتی روی آن کلیک شود، از `<dialog>` می‌پرسد که آیا می‌تواند بسته شود (برخلاف ویژگیِ `command="close"` که بلافاصله `<dialog>` را می‌بندد). این کار با گوش دادن به رویداد `cancel` بررسی می‌کند که آیا `<dialog>` [`cancelable`](/en-US/docs/Web/API/Event/cancelable) است.

وقتی رویداد `cancelable` باشد، مقدار دکمه‌های رادیویی بررسی می‌شود:

- اگر روی `yes` تنظیم شده باشد، dialog بسته می‌شود.
- اگر روی `no` تنظیم شده باشد، ویژگیِ `hidden` از روی پیام حذف می‌شود و متد [`preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) فراخوانی می‌شود که از رفتار پیش‌فرض بستن `<dialog>` جلوگیری می‌کند.

### استفاده از ویژگیِ `value` با دستور `close` در dialog

هنگامی که دکمهٔ **Cancel** یا **Delete** کلیک می‌شود، دیالوگ بسته شده و `returnValue` آن به مقدار ویژگی `value` دکمهٔ مربوطه تنظیم می‌شود.  
هندلر رویداد `close` مقدار `dialog.returnValue` را بررسی می‌کند تا بفهمد کاربر کدام اقدام را انتخاب کرده و نتیجه را روی صفحه نشان می‌دهد.

#### HTML

در ابتدای HTML، یک دکمهٔ **Delete Record** تعریف شده که از ویژگی `commandfor` برای تعیین دیالوگی که باید باز شود استفاده می‌کند.

در داخل دیالوگ، دکمه‌های **Cancel** و **Delete** با ویژگی `commandfor` مشخص می‌کنند که به دیالوگ فعلی اعمال می‌شوند.  
همچنین ویژگی `command` را روی `"close"` و ویژگی `value` را به ترتیب روی `"cancel"` و `"delete"` تنظیم می‌کنند — مقدار دکمهٔ انتخاب‌شده به‌صورت خودکار هنگام کلیک، در `returnValue` دیالوگ کپی می‌شود.

```html
<button commandfor="confirm-dialog" command="show-modal">Delete Record</button>
<dialog id="confirm-dialog">
  <header>
    <h1>Delete Record?</h1>
  </header>
  <p>Are you sure? This action cannot be undone</p>
  <footer>
    <button commandfor="confirm-dialog" command="close" value="cancel">
      Cancel
    </button>
    <button commandfor="confirm-dialog" command="close" value="delete">
      Delete
    </button>
  </footer>
</dialog>
```

```html
<pre id="log"></pre>
```

```css hidden
#log {
  height: 20px;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = text;
}
```

#### JavaScript

کد از یک event listener برای رویداد `close` استفاده می‌کند تا `returnValue` دیالوگ را ثبت کند.

```js
const dialog = document.getElementById("confirm-dialog");

dialog.addEventListener("close", () => {
  switch (dialog.returnValue) {
    case "cancel":
      log("Cancel was clicked");
      break;
    case "delete":
      log("Delete was clicked");
      break;
    default:
      log("Closed with value:", dialog.returnValue);
  }
});
```

#### نتایج

{{ EmbedLiveSample('using_the_value_attribute_with_dialog_close_command', 100, 200) }}

## خلاصهٔ فنی

| ویژگی | توضیحات |
|--------|----------|
| **دسته‌های محتوایی** | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content), [Interactive content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content), [Listed](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#listed), [Labelable](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#labelable), [Submittable](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#submittable) و [form-associated](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content) element, همچنین palpable content. |
| **محتوای مجاز** | [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) – اما نباید شامل [Interactive content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content) باشد. اگر `<button>` اولین فرزند یک [customizable select element](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select) باشد، می‌تواند حاوی صفر یا یک عنصر `<selectedcontent>` نیز باشد. |
| **حذف تگ** | ندارد؛ هر دو تگ شروع و پایان الزامی هستند. |
| **والدین مجاز** | هر عنصری که [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| **نقش ARIA ضمنی** | `button` |
| **نقش‌های ARIA مجاز** | `checkbox`, `combobox`, `link`, `menuitem`, `menuitemcheckbox`, `menuitemradio`, `option`, `radio`, `switch`, `tab` |
| **DOM interface** | `HTMLButtonElement` |

## مشخصات فنی

مشخصات رسمی این عنصر را می‌توانید در [HTML Living Standard](https://html.spec.whatwg.org/multipage/form-elements.html#the-button-element) و نیز [HTML 5.2 و بعد آن](https://www.w3.org/TR/html52/sec-forms.html#the-button-element) مشاهده کنید.

## سازگاری مرورگرها

اطلاعات سازگاری مرورگرها با این عنصر در جدول زیر آمده است.