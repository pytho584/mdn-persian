---
title: "<button> HTML button element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/button"
translated_by: "n8n + AI"
---

عنصر **`<button>`** در [HTML](/en-US/docs/Web/HTML) یک عنصر تعاملی است که کاربر می‌تواند با ماوس، صفحه‌کلید، لمس، فرمان صوتی یا سایر فناوری‌های کمکی آن را فعال کند. پس از فعال‌سازی، عملی مثل ارسال [فرم](/en-US/docs/Learn_web_development/Extensions/Forms) یا باز کردن دیالوگ انجام می‌دهد.

به‌طور پیش‌فرض، دکمه‌های HTML ظاهری مشابه پلتفرمی دارند که user agent روی آن اجرا می‌شود؛ اما می‌توانید ظاهر آن‌ها را با [CSS](/en-US/docs/Web/CSS) تغییر دهید.

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

## Attributes

attributeهای این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `autofocus`
  - : این Boolean attribute مشخص می‌کند که وقتی صفحه بارگذاری می‌شود، دکمه باید focus بگیرد. **فقط یک element در سند می‌تواند این attribute را داشته باشد.**

- `command`
  - : عملی را که قرار است روی عنصر تحت کنترل یک دکمهٔ `<button>` (که با ویژگی `commandfor` مشخص شده) انجام شود، تعیین می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"show-modal"`
      - : دکمه یک عنصر `<dialog>` را به‌صورت modal نمایش می‌دهد. اگر dialog از قبل modal باشد، هیچ اقدامی انجام نمی‌شود. این روش معادل declarative فراخوانی متد `HTMLDialogElement.showModal()` روی عنصر `<dialog>` است.
    - `"close"`
      - : دکمه یک عنصر `<dialog>` را می‌بندد. اگر dialog از قبل بسته باشد، هیچ اقدامی انجام نمی‌شود. این روش معادل declarative فراخوانی متد `HTMLDialogElement.close()` روی عنصر `<dialog>` است. وقتی با ویژگی `value` استفاده شود، مقدار دکمه به‌عنوان ویژگی `returnValue` به dialog منتقل می‌شود.
    - `"request-close"`
      - : دکمه یک رویداد `cancel` روی عنصر `<dialog>` فعال می‌کند تا از مرورگر بخواهد آن را ببندد، و پس از آن یک رویداد `close` رخ می‌دهد. تفاوت این دستور با `close` در این است که نویسندگان می‌توانند روی رویداد `cancel` متد `Event.preventDefault()` را صدا بزنند تا از بسته شدن `<dialog>` جلوگیری کنند. اگر dialog از قبل بسته باشد، هیچ اقدامی انجام نمی‌شود. این روش معادل declarative فراخوانی متد `HTMLDialogElement.requestClose()` روی عنصر `<dialog>` است. وقتی با ویژگی `value` دکمه استفاده شود، مقدار به‌عنوان ویژگی `returnValue` به dialog منتقل می‌شود.
    - `"show-popover"`
      - : دکمه یک popover مخفی را نمایش می‌دهد. اگر تلاش کنید popoverی که در حال نمایش است را دوباره نمایش دهید، هیچ اقدامی انجام نمی‌شود. برای جزئیات بیشتر به Popover API مراجعه کنید. این معادل تنظیم مقدار `show` برای ویژگی [`popovertargetaction`](#popovertargetaction) است و همچنین معادل declarative برای فراخوانی متد `HTMLElement.showPopover()` روی عنصر popover به شمار می‌رود.
    - `"hide-popover"`
      - : دکمه یک popover در حال نمایش را مخفی می‌کند. اگر تلاش کنید popoverی که از قبل مخفی است را مخفی کنید، هیچ اقدامی انجام نمی‌شود. برای جزئیات بیشتر به Popover API مراجعه کنید. این معادل تنظیم مقدار `hide` برای ویژگی [`popovertargetaction`](#popovertargetaction) است و همچنین معادل declarative برای فراخوانی متد `HTMLElement.hidePopover()` روی عنصر popover به شمار می‌رود.
    - `"toggle-popover"`
      - : دکمه یک popover را بین حالت نمایش و مخفی جابه‌جا می‌کند. اگر popover مخفی باشد، نمایش داده می‌شود و اگر در حال نمایش باشد، مخفی می‌شود. برای جزئیات بیشتر به Popover API مراجعه کنید. این معادل تنظیم مقدار `toggle` برای ویژگی [`popovertargetaction`](#popovertargetaction) است و همچنین معادل declarative برای فراخوانی متد `HTMLElement.togglePopover()` روی عنصر popover به شمار می‌رود.
    - مقادیر سفارشی
      - : این ویژگی می‌تواند مقادیر سفارشی‌ای را نشان دهد که با دو خط تیره (`--`) شروع می‌شوند. دکمه‌هایی که مقدار سفارشی دارند، رویداد `CommandEvent` را روی عنصر کنترل‌شده به راه می‌اندازند.

- `commandfor`
  - : یک عنصر `<button>` را به یک دکمهٔ فرمان (command button) تبدیل می‌کند؛ با صدور فرمان مشخص‌شده در attribute [`command`](#command) دکمه، عنصر تعاملی موردنظر را کنترل می‌کند. مقدار `commandfor` باید ID عنصری باشد که قرار است کنترل شود. این attribute نسخهٔ عمومی‌تری از [`popovertarget`](#popovertarget) است.
- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : این attribute بولی مانع تعامل کاربر با دکمه می‌شود: دکمه نه قابل فشار است و نه قابل فوکوس.
- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : عنصر `<form>` ای که دکمه باید با آن مرتبط شود (_مالک فرم_). مقدار این attribute باید `id` یک `<form>` در همان سند باشد. (اگر این attribute تنظیم نشود، `<button>` با عنصر `<form>` جد خود، در صورت وجود، مرتبط می‌شود.)

    این attribute به شما اجازه می‌دهد عناصر `<button>` را به `<form>`هایی در هر نقطه از سند مرتبط کنید، نه فقط داخل یک `<form>`. همچنین می‌تواند اثر عنصر `<form>` جد را لغو کند.
- `formaction`
  - : URLای که اطلاعات ارسال‌شده توسط دکمه را پردازش می‌کند. این attribute، [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) مربوط به مالک فرم دکمه را لغو می‌کند. اگر مالک فرمی وجود نداشته باشد، تأثیری ندارد.
- `formenctype`
  - : اگر دکمه یک دکمهٔ submit باشد (داخل `<form>` قرار داشته باشد یا به آن مرتبط شده باشد و `type="button"` نداشته باشد)، مشخص می‌کند داده‌های فرم ارسالی چگونه کدگذاری شوند. مقادیر ممکن:
    - `application/x-www-form-urlencoded`: مقدار پیش‌فرض در صورت استفاده‌نکردن از attribute.
    - `multipart/form-data`: برای ارسال عناصر {{HTMLElement("input")}} که attribute [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) آن‌ها روی `file` تنظیم شده، استفاده می‌شود.
    - `text/plain`: به‌عنوان ابزاری برای دیباگ مشخص شده؛ نباید برای ارسال واقعی فرم استفاده شود.

    اگر این attribute مشخص شود، attribute [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) مالک فرم دکمه را لغو می‌کند.
- `formmethod`
  - : اگر دکمه یک دکمهٔ submit باشد (داخل `<form>` قرار داشته باشد یا به آن مرتبط شده باشد و `type="button"` نداشته باشد)، این attribute روش [HTTP](/en-US/docs/Web/HTTP/Reference/Methods) مورد استفاده برای ارسال فرم را مشخص می‌کند. مقادیر ممکن:
    - `post`: داده‌های فرم در بدنهٔ درخواست HTTP هنگام ارسال به سرور قرار می‌گیرند. زمانی از این روش استفاده کنید که فرم حاوی اطلاعاتی است که نباید عمومی باشد، مانند اعتبارنامه‌های ورود.
    - `get`: داده‌های فرم به URL اکشن فرم اضافه می‌شوند و با `?` جدا می‌شوند و URL نهایی به سرور ارسال می‌شود. از این روش زمانی استفاده کنید که فرم [عوارض جانبی ندارد](/en-US/docs/Glossary/Idempotent)، مانند فرم‌های جستجو.
    - `dialog`: این روش نشان می‌دهد که دکمه، [dialog](/en-US/docs/Web/HTML/Reference/Elements/dialog) مرتبط با خود را می‌بندد و داده‌های فرم را اصلاً ارسال نمی‌کند.

    اگر مشخص شود، این attribute، attribute [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) مربوط به مالک فرم دکمه را لغو می‌کند.
- `formnovalidate`
  - : اگر دکمه یک دکمهٔ submit باشد، این attribute بولی مشخص می‌کند که فرم هنگام ارسال [اعتبارسنجی](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) نشود. اگر این attribute مشخص شود، attribute [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) مالک فرم دکمه را لغو می‌کند.

    این attribute روی عناصر [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) و [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) نیز در دسترس است.

- `formtarget`
  - : اگر دکمه از نوع submit باشد، این ویژگی یک نام تعریف‌شده توسط نویسنده یا یک کلیدواژهٔ استاندارد با پیشوند زیرخط است که مشخص می‌کند پاسخ ارسال فرم کجا نمایش داده شود. این مقدار، `name` یا کلیدواژه‌ای برای یک _browsing context_ (زبانه، پنجره، یا `<iframe>`) است. اگر این ویژگی مشخص شده باشد، بر ویژگی [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) متعلق به فرمِ صاحب دکمه اولویت دارد. کلیدواژه‌های زیر معانی خاصی دارند:
    - `_self`: پاسخ را در همان browsing context فعلی بارگذاری کن. این رفتار پیش‌فرض وقتی است که ویژگی مشخص نشده باشد.
    - `_blank`: پاسخ را در یک browsing context جدید بدون نام بارگذاری کن — معمولاً یک زبانه یا پنجره جدید، بسته به تنظیمات مرورگر کاربر.
    - `_parent`: پاسخ را در browsing context والدِ زمینهٔ فعلی بارگذاری کن. اگر والد وجود نداشته باشد، این گزینه مانند `_self` عمل می‌کند.
    - `_top`: پاسخ را در browsing context سطح بالا بارگذاری کن (یعنی زمینه‌ای که جدِ زمینهٔ فعلی است و والد ندارد). اگر والد وجود نداشته باشد، این گزینه مانند `_self` عمل می‌کند.

- `interestfor`
  - : عنصر `<button>` را به عنوان یک **interest invoker** تعریف می‌کند. مقدار آن `id` یک عنصر هدف است که وقتی علاقه (interest) روی عنصر invoker نشان داده شود یا از بین برود (مثلاً با قرار دادن/برداشتن نشانگر روی آن یا فوکوس/از دست دادن فوکوس)، به نحوی تحت تأثیر قرار می‌گیرد (معمولاً نمایش داده یا پنهان می‌شود). برای جزئیات و مثال‌های بیشتر به [Using interest invokers](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) مراجعه کنید.

- `name`
  - : نام دکمه است که وقتی آن دکمه برای ارسال فرم استفاده می‌شود، همراه با `value` دکمه به‌صورت یک جفت در داده‌های فرم ارسال می‌شود.

- `popovertarget`
  - : عنصر `<button>` را به یک دکمهٔ کنترل popover تبدیل می‌کند؛ مقدار آن، `id` عنصر popover مورد نظر برای کنترل است. برقراری رابطه بین یک popover و دکمهٔ invoker آن با استفاده از ویژگی `popovertarget` دو اثر مفید اضافی دارد:
    - مرورگر یک رابطهٔ ضمنی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) و [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) بین popover و invoker ایجاد می‌کند و وقتی popover نمایش داده می‌شود، آن را در موقعیت منطقی در ترتیب ناوبری فوکوس صفحه‌کلید قرار می‌دهد. این کار popover را برای کاربران صفحه‌کلید و فناوری کمکی (AT) در دسترس‌تر می‌کند (همچنین به [ویژگی‌های دسترس‌پذیری Popover](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features) مراجعه کنید).
    - مرورگر یک مرجع anchor ضمنی بین این دو ایجاد می‌کند که موقعیت‌دهی popoverها نسبت به کنترل‌هایشان را با استفاده از [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) بسیار راحت می‌کند. برای جزئیات بیشتر به [Popover anchor positioning](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) مراجعه کنید.

- `popovertargetaction`
  - : عملیاتی را که روی یک عنصر popover کنترل‌شده توسط یک دکمهٔ `<button>` انجام می‌شود مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"hide"`
      - : دکمه، یک popover نمایش‌داده‌شده را پنهان می‌کند. اگر تلاش کنید یک popover از قبل پنهان را پنهان کنید، هیچ عملی انجام نمی‌شود.
    - `"show"`
      - : دکمه، یک popover پنهان را نمایش می‌دهد. اگر تلاش کنید یک popover در حال نمایش را نمایش دهید، هیچ عملی انجام نمی‌شود.
    - `"toggle"`
      - : دکمه وضعیت popover را بین نمایش و پنهان بودن تغییر می‌دهد. اگر popover پنهان باشد، نمایش داده می‌شود؛ اگر در حال نمایش باشد، پنهان می‌شود. اگر `popovertargetaction` حذف شده باشد، `"toggle"` عمل پیش‌فرضی است که توسط دکمهٔ کنترل انجام می‌شود.

- `type`
  - : رفتار پیش‌فرض دکمه. مقادیر ممکن عبارتند از:
    - `submit`: دکمه داده‌های فرم را به سرور ارسال می‌کند. اگر این attribute برای دکمه‌های مرتبط با یک `<form>` مشخص نشده باشد، یا مقدار آن خالی یا نامعتبر باشد، این مقدار پیش‌فرض است.
    - `reset`: دکمه همه کنترل‌ها را به مقادیر اولیه بازنشانی می‌کند، مانند [\<input type="reset">](/en-US/docs/Web/HTML/Reference/Elements/input/reset). (این رفتار معمولاً کاربران را آزار می‌دهد.)
    - `button`: دکمه هیچ رفتار پیش‌فرضی ندارد و به طور پیش‌فرض با فشردن کاری انجام نمی‌دهد. اسکریپت‌های سمت کلاینت می‌توانند به رویدادهای element گوش دهند؛ این رویدادها هنگام رخ دادن فعال می‌شوند.

- `value`
  - : مقدار مرتبط با `name` دکمه را هنگام ارسال با داده‌های فرم تعریف می‌کند. این مقدار وقتی فرم با این دکمه ارسال می‌شود، در پارامترها به سرور فرستاده می‌شود. وقتی همراه با دستورهای `close` یا `request-close` استفاده شود، attribute دکمه (`value`)، `returnValue` عنصر `<dialog>` موردنظر را تنظیم می‌کند.

## یادداشت‌ها

یک دکمه submit که attribute `formaction` روی آن تنظیم شده باشد، بدون فرم مرتبط هیچ کاری انجام نمی‌دهد. باید یک فرم مشخص کنید؛ یا آن را در یک `<form>` قرار دهید، یا attribute `form` را برابر با id فرم موردنظر قرار دهید.

عناصر `<button>` خیلی راحت‌تر از عناصر `<input>` استایل می‌گیرند. می‌توانید محتوای HTML داخلی اضافه کنید (مثل `<i>`، `<br>` یا حتی `<img>`) و از pseudo-elementهای `::after` و `::before` برای رندر پیچیده استفاده کنید.

اگر دکمه‌های شما برای ارسال داده‌های فرم به سرور نیستند، حتماً attribute نوع (`type`) آن‌ها را روی `button` تنظیم کنید. در غیر این صورت، سعی می‌کنند داده‌های فرم را ارسال کنند و پاسخ (ناموجود) را بارگذاری کنند که احتمالاً وضعیت فعلی سند را از بین می‌برد.

در حالی که `<button type="button">` رفتار پیش‌فرضی ندارد، می‌توان برای event handlerها اسکریپت نوشت تا رفتارها را فعال کنند. یک دکمه فعال می‌تواند با [JavaScript](/en-US/docs/Learn_web_development/Core/Scripting) کارهای برنامه‌پذیر انجام دهد، مثلاً حذف یک آیتم از فهرست.

به طور پیش‌فرض، user agentها دکمه‌ها را با `display: flow-root` استایل می‌دهند؛ این کار یک [block formatting context](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) جدید ایجاد می‌کند و فرزندان دکمه را تا زمانی که سرریز نکنند، هم به صورت افقی و هم عمودی در مرکز قرار می‌دهد. اگر دکمه به عنوان یک flex container یا grid container تعریف شود، فرزندان به صورت آیتم‌های flex یا grid رفتار می‌کنند. دکمه‌ای که `display: inline` گرفته باشد، طوری استایل می‌شود که انگار مقدار `display: inline-block` تنظیم شده است.

## دسترس‌پذیری

### دکمه‌های آیکونی

دکمه‌هایی که فقط یک آیکون نمایش می‌دهند، _accessible name_ ندارند. نام‌های دسترس‌پذیر اطلاعاتی را برای فناوری کمکی، مانند screen readerها، فراهم می‌کنند تا هنگام تجزیه سند و تولید [یک درخت دسترس‌پذیری](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) به آن‌ها دسترسی داشته باشند. سپس فناوری کمکی از درخت دسترس‌پذیری برای پیمایش و دستکاری محتوای صفحه استفاده می‌کند.

برای دادن یک accessible name به دکمه آیکونی، متنی در عنصر `<button>` قرار دهید که عملکرد دکمه را به طور خلاصه توصیف کند.

#### مثال

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

اگر میخواهید متن دکمه را بهصورت بصری پنهان کنید، یک راه دسترسپذیر این است که با [ترکیبی از خصوصیتهای CSS](https://www.a11yproject.com/posts/how-to-hide-content/) آن را از روی صفحه حذف کنید، اما همچنان آن را برای فناوریهای کمکی قابل پردازش نگه دارید.

با این حال، شایان ذکر است که قابل مشاهده نگه داشتن متن دکمه میتواند به افرادی کمک کند که با معنای آیکون آشنا نیستند یا هدف دکمه را متوجه نمیشوند. این موضوع بهویژه برای افرادی که از نظر فنی چندان ماهر نیستند یا ممکن است برداشتهای فرهنگی متفاوتی از آیکونی که دکمه استفاده میکند داشته باشند، اهمیت دارد.

- [نام دسترسپذیر چیست؟ | Vispero](https://vispero.com/resources/what-is-an-accessible-name/)
- [درک WCAG از MDN، توضیحات راهنمای 4.1](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Robust#guideline_4.1_—_compatible_maximize_compatibility_with_current_and_future_user_agents_including_assistive_technologies)
- [درک معیار موفقیت 4.1.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html)

### اندازه و فاصله

#### اندازه

عناصر تعاملی مانند دکمهها باید ناحیهای به اندازه کافی بزرگ داشته باشند تا بهراحتی فعال شوند. این کار به افراد مختلفی کمک میکند، از جمله افرادی که مشکلات کنترل حرکتی دارند و افرادی که از ورودیهای غیردقیق مانند قلم لمسی یا انگشت استفاده میکنند. حداقل اندازه تعاملی ۴۴×۴۴ [پیکسل CSS](/en-US/docs/Glossary/CSS_pixel) توصیه میشود.

- [درک معیار موفقیت 2.5.5: اندازه هدف | W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- [اندازه هدف و 2.5.5 | Adrian Roselli](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
- [آزمون سریع: اهداف لمسی بزرگ - پروژه A11Y](https://www.a11yproject.com/posts/large-touch-targets/)

#### فاصله

مقادیر زیادی از محتوای تعاملی — از جمله دکمهها — که از نظر بصری نزدیک به یکدیگر قرار دارند، باید با فاصله از هم جدا شوند. این فاصلهگذاری برای افرادی که مشکلات کنترل حرکتی دارند و ممکن است بهطور تصادفی محتوای تعاملی اشتباهی را فعال کنند، مفید است.

فاصلهگذاری را میتوان با استفاده از خصوصیتهای CSS مانند `margin` ایجاد کرد.

- [لرزش دست و مشکل دکمه بزرگ - Axess Lab](https://axesslab.com/hand-tremors/)

### اطلاعات وضعیت ARIA

برای توصیف وضعیت یک دکمه، ویژگی ARIA درست [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) است و نه [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) یا [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected). برای اطلاعات بیشتر، مطلب مربوط به [نقش دکمه ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) را بخوانید.

### استایل دکمهها

بهترین کار این است که حلقه فوکوس پیشفرض عناصری که فوکوس میگیرند را بازنویسی نکنید. اگر استایلهای دکمه بازنویسی میشوند، مهم است که **اطمینان حاصل کنید وضعیت فوکوس کنتراست کافی دارد** تا افرادی که مشکلات بینایی خفیف دارند بتوانند آن را درک کنند و افرادی با تفاوتهای شناختی آن را بفهمند.

شبهکلاس `:focus-visible` را میتوان برای اعمال استایل به عنصری که دارای `:focus` است استفاده کرد، فقط زمانی که الگوریتمهای عامل کاربر تعیین کنند که فوکوس باید برجسته شود، مثلاً وقتی یک `<button>` فوکوس کیبورد دریافت میکند. برای اطلاعات بیشتر به [مقایسه :focus با :focus-visible](/en-US/docs/Web/CSS/Reference/Selectors/:focus-visible#focus_vs_focus-visible) مراجعه کنید.

نسبت کنتراست رنگ با مقایسه درخشندگی (Luminosity) مقدار رنگ متن دکمه و پسزمینه آن با پسزمینهای که دکمه روی آن قرار دارد، تعیین میشود. برای مطابقت با [دستورالعملهای دسترسپذیری محتوای وب (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/) فعلی، نسبت 4.5:1 برای محتوای متنی و 3:1 برای متن بزرگ لازم است. (متن بزرگ بهصورت حداقل 18.66 پیکسل با وزن `bold` یا بزرگتر، یا حداقل 24 پیکسل تعریف شده است.)

- [WebAIM: بررسی کنتراست رنگ](https://webaim.org/resources/contrastchecker/)
- [توضیحات MDN درباره WCAG، راهنمای ۱.۴](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [درک معیار موفقیت ۱.۴.۳ | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)

### کلیک کردن و فوکوس

اینکه کلیک روی یک `<button>` یا `<input>` از نوع دکمه، به‌طور پیش‌فرض باعث فوکوس شود یا نه، به مرورگر و سیستم‌عامل بستگی دارد. اکثر مرورگرها به دکمه‌ای که روی آن کلیک می‌شود فوکوس می‌دهند، اما [سافاری به‌صورت عمدی این کار را نمی‌کند](https://webkit.org/b/22261#c68).

## مثال‌ها

### ساخت یک دکمه ساده

این مثال یک دکمه قابل کلیک می‌سازد. وجود attribute با مقدار `type="button"` تضمین می‌کند که دکمه هیچ رفتار پیش‌فرضی نداشته باشد. می‌توانید این دکمه را با استفاده از JavaScript یا attributeهایی مثل `command` و `commandfor` تعاملی کنید.

```html
<button type="button" name="button">I'm a button</button>
```

### استفاده از مقدار `request-close` برای attribute مربوط به `command`

در این مثال، دیالوگ دو دکمه رادیویی دارد که مشخص می‌کنند آیا دیالوگ می‌تواند بسته شود یا نه. گزینه **Yes** یا **No** را انتخاب کنید و سپس روی **Request to Close** کلیک کنید تا تلاش کند دیالوگ را ببندد. اگر **Yes** انتخاب شده باشد، دیالوگ بسته می‌شود؛ اگر **No** انتخاب شده باشد، دیالوگ باز می‌ماند و به جای آن یک پیام نمایش می‌دهد.

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

دکمه **Open Dialog** با استفاده از `command="show-modal"`، element `<dialog>` را باز می‌کند.

دکمه **Request to Close** دارای `command="request-close"` است که با استفاده از attribute مربوط به `commandfor="mydialog"`، element `<dialog>` را هدف قرار می‌دهد. وقتی روی آن کلیک می‌شود، از `<dialog>` می‌پرسد که آیا می‌تواند بسته شود (برخلاف attribute مربوط به `command="close"` که بلافاصله `<dialog>` را می‌بندد). این کار با استفاده از رویداد `cancel` بررسی می‌کند که آیا رویداد `cancelable` است یا خیر.

وقتی رویداد `cancelable` باشد، مقدار دکمه‌های رادیویی بررسی می‌شود:

- اگر روی `yes` تنظیم شده باشد، دیالوگ بسته می‌شود.
- اگر روی `no` تنظیم شده باشد، attribute مربوط به `hidden` روی پیام هشدار غیرفعال می‌شود و متد [`preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) فراخوانی می‌شود که از رفتار پیش‌فرض بسته شدن `<dialog>` جلوگیری می‌کند.

### استفاده از attribute `value` به‌همراه command مربوط به `close` در دیالوگ

این مثال نشان می‌دهد که چگونه می‌توان با استفاده از attribute مربوط به `value` در دکمه و command از نوع `close`، مقدار property `returnValue` در یک dialog را مقداردهی کرد.

وقتی کاربر روی دکمهٔ **Cancel** یا **Delete** کلیک کند، dialog بسته می‌شود و `returnValue` آن به مقدار `value` همان دکمه تنظیم می‌شود. شنوندهٔ رویداد `close` سپس مقدار `dialog.returnValue` را بررسی می‌کند تا بفهمد کاربر کدام عملیات را انتخاب کرده و نتیجه را به نمایش درمی‌آورد.

#### HTML

در ابتدای HTML، دکمه‌ای به نام **Delete Record** تعریف شده که با استفاده از attribute «commandfor» مشخص می‌کند کدام dialog باید باز شود.

در داخل dialog، دکمه‌های **Cancel** و **Delete** با attribute «commandfor» به dialog جاری اشاره می‌کنند. همچنین attribute «command» آنها روی `"close"` و attribute «value» به ترتیب روی `"cancel"` و `"delete"` تنظیم شده است. وقتی روی هرکدام از این دکمه‌ها کلیک شود، مقدار دکمهٔ انتخابی به‌صورت خودکار در `returnValue` dialog کپی می‌شود.

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

این کد با یک شنوندهٔ رویداد `close` مقدار `returnValue` dialog را ثبت می‌کند.

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

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content">محتوای تعاملی</a>،
        عنصر <a href="/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content">مرتبط با فرم</a>
        از نوع <a href="/en-US/docs/Web/HTML/Guides/Content_categories#listed">listed</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#labelable">labelable</a> و
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#submittable">submittable</a>،
        محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی</a>،
        اما نباید هیچ
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content">محتوای تعاملی</a>
        وجود داشته باشد. اگر <code>&lt;button&gt;</code> اولین فرزند یک
        <a href="/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select">عنصر customizable select</a>
        باشد، می‌تواند صفر یا یک عنصر <code>&lt;selectedcontent&gt;</code> نیز داشته باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ تگ شروع و تگ پایان هر دو الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role">button</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role"><code>checkbox</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role"><code>combobox</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"><code>link</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"><code>menuitem</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"><code>menuitemcheckbox</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"><code>menuitemradio</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role"><code>option</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role"><code>radio</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role"><code>switch</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"><code>tab</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLButtonElement</code></td>
    </tr>
  </tbody>
</table>