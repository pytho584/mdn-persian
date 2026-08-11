---
title: "<dialog> HTML dialog element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog"
translated_by: "n8n + AI"
---

عنصر `<dialog>` یک جعبه محاوره‌ای (dialog box) یا وضعیت‌دهنده (modal) یا غیروضعیت‌دهنده (non-modal) را نشان می‌دهد؛ مثل یک هشدار قابل بستن، یک بازرس (inspector) یا یک زیرپنجره.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

> [!WARNING]
> از ویژگی `tabindex` روی عنصر `<dialog>` **نباید** استفاده شود. برای اطلاعات بیشتر به [یادداشت‌های اضافی](#additional_notes) مراجعه کنید.

- `closedby`
  - : مشخص می‌کند چه نوع کارهای کاربری می‌توانند عنصر `<dialog>` را ببندند. این ویژگی سه روش برای بستن دیالوگ را مشخص می‌کند:
    - یک _عمل کاربری سبک (light dismiss)_ که در آن وقتی کاربر بیرون از `<dialog>` کلیک یا ضربه بزند، دیالوگ بسته می‌شود. این معادل [رفتار "light dismiss" در popoverهای حالت "auto"] است.
    - یک _عمل کاربری وابسته به پلتفرم_ مثل فشار دادن کلید <kbd>Esc</kbd> در دسکتاپ یا ژست "بازگشت" یا "بستن" در موبایل.
    - یک مکانیزم مشخص‌شده توسط توسعه‌دهنده مثل یک {{htmlelement("button")}} با هندلر [`click`](/en-US/docs/Web/API/Element/click_event) که {{domxref("HTMLDialogElement.close()")}} را فراخوانی می‌کند یا ارسال یک {{htmlelement("form")}}.

    مقادیر ممکن:
    - `any`
      - : دیالوگ با هر سه روش قابل بستن است.
    - `closerequest`
      - : دیالوگ با عمل کاربری وابسته به پلتفرم یا مکانیزم توسعه‌دهنده قابل بستن است.
    - `none`
      - : دیالوگ فقط با مکانیزم توسعه‌دهنده قابل بستن است.

    اگر عنصر `<dialog>` مقدار معتبری برای `closedby` نداشته باشد:
    - اگر با استفاده از {{domxref("HTMLDialogElement.showModal()", "showModal()")}} باز شده باشد، طوری رفتار می‌کند که انگار مقدار `"closerequest"` است.
    - در غیر این صورت، طوری رفتار می‌کند که انگار مقدار `"none"` است.

- `open`
  - : نشان می‌دهد که جعبه محاوره‌ای فعال است و برای تعامل در دسترس است. اگر ویژگی `open` تنظیم نشده باشد، دیالوگ برای کاربر قابل مشاهده نیست.
    توصیه می‌شود برای نمایش دیالوگ‌ها از متدهای `.show()` یا `.showModal()` استفاده کنید، نه از ویژگی `open`. اگر `<dialog>` با استفاده از ویژگی `open` باز شود، غیروضعیت‌دهنده (non-modal) است.

    > [!NOTE]
    > اگرچه می‌توانید با اضافه/حذف کردن ویژگی `open` بین حالت باز و بستهٔ دیالوگ‌های غیروضعیت‌دهنده جابجا شوید، این روش توصیه نمی‌شود. برای اطلاعات بیشتر به {{domxref("HTMLDialogElement.open", "open")}} مراجعه کنید.

## توضیحات

عنصر HTML `<dialog>` برای ایجاد جعبه‌های محاوره‌ای وضعیت‌دهنده (modal) و غیروضعیت‌دهنده (non-modal) استفاده می‌شود. دیالوگ‌های وضعیت‌دهنده تعامل با سایر عناصر رابط کاربری را مسدود می‌کنند و بقیهٔ صفحه را [غیرفعال (inert)](/en-US/docs/Web/HTML/Reference/Global_attributes/inert#:~:text=When,clicked) می‌کنند، در حالی که دیالوگ‌های غیروضعیت‌دهنده اجازهٔ تعامل با بقیهٔ صفحه را می‌دهند.

### کنترل دیالوگ‌ها با JavaScript

جاوااسکریپت می‌تواند برای نمایش و بستن عنصر `<dialog>` استفاده شود. می‌توانید از متد {{domxref("HTMLDialogElement.showModal()", "showModal()")}} برای نمایش یک دیالوگ وضعیت‌دهنده و از متد {{domxref("HTMLDialogElement.show()", "show()")}} برای نمایش یک دیالوگ غیروضعیت‌دهنده استفاده کنید. جعبه محاوره‌ای را می‌توان با متد {{domxref("HTMLDialogElement.close()", "close()")}} یا با استفاده از متد [`dialog`](/en-US/docs/Web/HTML/Reference/Elements/form#method) هنگام ارسال یک `<form>` که داخل عنصر `<dialog>` قرار دارد، بست. دیالوگ‌های وضعیت‌دهنده همچنین با فشار دادن کلید <kbd>Esc</kbd> بسته می‌شوند.

### دیالوگ‌های وضعیت‌دهنده با استفاده از دستورات invoker (دستورات فراخوان)

با استفاده از [Invoker Commands API](/en-US/docs/Web/API/Invoker_Commands_API) می‌توان دیالوگ‌های modal را به صورت اعلانی (declarative) باز و بسته کرد. این کار با کمک attributeهای HTML [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor) و [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command) انجام می‌شود که می‌توان روی عناصر {{htmlelement("button")}} تنظیم کرد.

attribute `command` مشخص می‌کند که با کلیک روی `<button>` چه دستوری ارسال شود، و `commandfor` هم `id` دیالوگ هدف را تعیین می‌کند. دستورهایی که برای دیالوگ‌ها می‌توان ارسال کرد عبارتند از [`"show-modal"`](/en-US/docs/Web/HTML/Reference/Elements/button#show-modal)، [`"close"`](/en-US/docs/Web/HTML/Reference/Elements/button#close) و [`"request-close"`](/en-US/docs/Web/HTML/Reference/Elements/button#request-close).

HTML زیر نحوهٔ استفاده از این attributeها روی یک `<button>` را نشان می‌دهد تا با کلیک روی آن، یک `<dialog>` modal با `id` برابر `"my-dialog"` باز شود:

```html
<button command="show-modal" commandfor="my-dialog">Open dialog</button>

<dialog id="my-dialog">
  <p>This dialog was opened using an invoker command.</p>
  <button commandfor="my-dialog" command="close">Close</button>
</dialog>
```

### دیالوگ‌های غیر modal با استفاده از popover commands

دیالوگ‌های غیر modal را می‌توان با استفاده از [Popover API](/en-US/docs/Web/API/Popover_API) و attributeهای HTML [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) و [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) به صورت اعلانی باز، بسته و جابه‌جا (toggle) کرد. این attributeها روی عناصر {{htmlelement("button")}} و {{htmlelement("input")}} قابل تعریف هستند.

برای این کار باید `<dialog>` با افزودن attribute `popover` به یک popover تبدیل شود. سپس می‌توان از `popovertarget` روی دکمه یا input برای指定 popover هدف، و از `popovertargetaction` برای تعیین عملی که هنگام کلیک روی دکمه روی popover انجام می‌شود استفاده کرد. توجه داشته باشید که چون دیالوگ یک popover است، غیر modal خواهد بود و می‌توان با کلیک خارج از دیالوگ آن را بست.

HTML زیر نحوهٔ اعمال این attributeها روی یک `<button>` را نشان می‌دهد تا با کلیک روی آن، یک `<dialog>` modal با `id` برابر `"my-dialog"` نمایش داده و پنهان شود:

```html
<button popovertarget="my-dialog">Open dialog</button>

<dialog id="my-dialog" popover>
  <p>This dialog was opened using a popovertargetaction attribute.</p>
  <button popovertarget="my-dialog" popovertargetaction="hide">Close</button>
</dialog>
```

Popover API همچنین propertyهایی ارائه می‌دهد که می‌توان برای دریافت و تنظیم وضعیت در JavaScript از آن‌ها استفاده کرد.

### بستن دیالوگ‌ها

برای هر عنصر `<dialog>` باید یک سازوکار بستن فراهم کنید و مطمئن شوید که روی دستگاه‌هایی که صفحه‌کلید فیزیکی ندارند نیز کار می‌کند.

روش‌های مختلفی برای بستن یک دیالوگ وجود دارد:

- ارسال فرم داخل `<dialog>` با `method="dialog"` روی عنصر `<form>` (مثال [Using the dialog open attribute](#using_the_dialog_open_attribute) را ببینید).
- کلیک خارج از ناحیهٔ دیالوگ زمانی که «light dismiss» فعال است (مثال [Popover API HTML attributes](#popover_api_html_attributes) را ببینید).
- فشردن کلید <kbd>Esc</kbd> در دیالوگ‌هایی که این قابلیت فعال است (مثال [Popover API HTML attributes](#popover_api_html_attributes) را ببینید).
- فراخوانی متد {{domxref("HTMLDialogElement.close()")}} (مثال [modal example](#creating_a_modal_dialog) را ببینید).

### استایل‌دهی با CSS

یک `<dialog>` را می‌توان با نام عنصر آن (مانند هر عنصر دیگر) انتخاب کرد. همچنین می‌توان وضعیت آن را با استفاده از pseudo-classهایی مانند [`:modal`](/en-US/docs/Web/CSS/Reference/Selectors/:modal) و [`:open`](/en-US/docs/Web/CSS/Reference/Selectors/:open) مطابقت داد.

پس‌زمینه (backdrop) یک دیالوگ مدال را می‌توان با استفاده از شبه‌عنصر (pseudo-element) CSS ::backdrop استایل‌دهی کرد. این پس‌زمینه پشت عنصر `<dialog>` قرار می‌گیرد و زمانی نمایش داده می‌شود که دیالوگ با متد HTMLDialogElement.showModal() باز شده باشد.  
برای مثال می‌توان از این شبه‌عنصر برای محو، تاریک یا به‌طور کلی پنهان کردن محتوای غیرفعال (inert) پشت دیالوگ مدال استفاده کرد.

### نکات اضافی

- عناصر HTML `<form>` می‌توانند برای بستن یک دیالوگ به کار روند اگر دارای ویژگی `method="dialog"` باشند، یا اگر دکمه‌ای که فرم را ارسال می‌کند دارای `formmethod="dialog"` باشد. وقتی یک `<form>` داخل `<dialog>` با متد `dialog` ارسال می‌شود، دیالوگ بسته می‌شود، وضعیت کنترل‌های فرم ذخیره می‌شود (اما ارسال نمی‌شود) و ویژگی `returnValue` (مقدار بازگشتی) برابر با مقدار دکمه‌ای که فعال شده است قرار می‌گیرد.
- ویژگی `autofocus` باید به عنصری اضافه شود که انتظار می‌رود کاربر بلافاصله پس از باز شدن دیالوگ مدال با آن تعامل کند. اگر هیچ عنصر دیگری نیاز به تعامل فوری‌تری ندارد، توصیه می‌شود `autofocus` را روی دکمه بستن داخل دیالوگ قرار دهید، یا اگر کاربر باید با کلیک یا فعال کردن خود دیالوگ آن را ببندد، روی خود `<dialog>`.
- ویژگی `tabindex` را به عنصر `<dialog>` اضافه نکنید، زیرا این عنصر تعاملی (interactive) نیست و فوکوس دریافت نمی‌کند. محتوای داخل دیالوگ (از جمله دکمه بستن) می‌تواند فوکوس بگیرد و تعاملی باشد.

## دسترس‌پذیری (Accessibility)

هنگام پیاده‌سازی یک دیالوگ، مهم است که بهترین مکان برای قرار دادن فوکوس کاربر را در نظر بگیرید. وقتی از `HTMLDialogElement.showModal()` برای باز کردن `<dialog>` استفاده می‌شود، فوکوس روی اولین عنصر قابل فوکوس درون دیالوگ قرار می‌گیرد. مشخص کردن صریح مکان فوکوس اولیه با استفاده از ویژگی `autofocus` کمک می‌کند تا فوکوس روی عنصری قرار گیرد که برای آن دیالوگ بهترین گزینه محسوب می‌شود. در مواقعی که مطمئن نیستید (مثلاً ممکن است همیشه مشخص نباشد که فوکوس اولیه در کجای دیالوگ قرار گیرد، به‌ویژه وقتی محتوای دیالوگ به‌صورت پویا هنگام فراخوانی رندر می‌شود)، خود عنصر `<dialog>` ممکن است بهترین مکان برای فوکوس اولیه باشد.

حتماً مکانیزمی برای بستن دیالوگ در اختیار کاربران قرار دهید. مطمئن‌ترین راه برای اطمینان از اینکه همه کاربران می‌توانند دیالوگ را ببندند، افزودن یک دکمه صریح برای این کار است؛ مانند دکمه تأیید، لغو یا بستن.

به‌طور پیش‌فرض، دیالوگی که با متد `showModal()` فراخوانی می‌شود، با فشار دادن کلید <kbd>Esc</kbd> بسته می‌شود. یک دیالوغ غیرمدال (non-modal) به‌طور پیش‌فرض با کلید <kbd>Esc</kbd> بسته نمی‌شود و بسته به ماهیت آن، ممکن است این رفتار مطلوب نباشد. کاربران صفحه‌کلید انتظار دارند که کلید <kbd>Esc</kbd> دیالوگ‌های مدال را ببندد؛ مطمئن شوید این رفتار پیاده‌سازی و حفظ شده است. اگر چندین دیالوگ مدال باز باشند، فشار دادن <kbd>Esc</kbd> باید فقط آخرین دیالوگ نمایش‌داده‌شده را ببندد. هنگام استفاده از `<dialog>`، این رفتار توسط مرورگر ارائه می‌شود.

اگرچه می‌توان دیالوگ‌ها را با سایر عناصر ساخت، اما عنصر بومی `<dialog>` ویژگی‌های کاربردی و دسترس‌پذیری دارد که در صورت استفاده از عناصر دیگر برای هدف مشابه باید بازتولید شوند. اگر یک پیاده‌سازی سفارشی برای دیالوگ ایجاد می‌کنید، مطمئن شوید که تمام رفتارهای پیش‌فرض مورد انتظار پشتیبانی می‌شوند و توصیه‌های مربوط به برچسب‌گذاری (labeling) رعایت می‌گردند.

عنصر `<dialog>` توسط مرورگرها به شکلی مشابه با dialog‌های سفارشی که از ویژگی ARIA `role="dialog"` استفاده می‌کنند، نمایش داده می‌شود. dialog‌هایی که با متد `showModal()` فراخوانی می‌شوند، به طور ضمنی دارای `aria-modal="true"` هستند؛ در حالی که dialog‌هایی که با متد `show()` فراخوانی می‌شوند یا با استفاده از ویژگی `open` یا تغییر `display` پیش‌فرض یک `<dialog>` نمایش داده می‌شوند، به صورت `[aria-modal="false"]` در معرض قرار می‌گیرند. هنگام پیاده‌سازی dialog‌های modal، همه چیز به جز خود `<dialog>` و محتوای آن باید با استفاده از ویژگی `inert` غیرفعال (inert) رندر شود. اگر از `<dialog>` همراه با `HTMLDialogElement.showModal()` استفاده کنید، این رفتار توسط مرورگر تأمین می‌شود.

## مثال‌ها

### ویژگی‌های HTML مربوط به Invoker Command API

این مثال نشان می‌دهد چگونه می‌توانید یک dialog modal را با استفاده از ویژگی‌های HTML `commandfor` و `command` مربوط به [Invoker Commands API](/en-US/docs/Web/API/Invoker_Commands_API) باز و بسته کنید.

ابتدا یک عنصر `<button>` تعریف می‌کنیم و ویژگی `command` را به `"show-modal"` و ویژگی `commandfor` را به `id` دیالوگ مورد نظر (`my-dialog`) تنظیم می‌کنیم.
سپس یک عنصر `<dialog>` شامل یک دکمه "Close" تعریف می‌کنیم. این دکمه فرمان `"close"` را به همان `id` dialog ارسال می‌کند.

```html
<button command="show-modal" commandfor="my-dialog">Open dialog</button>

<dialog id="my-dialog">
  <p>This dialog was opened using an invoker command.</p>
  <button commandfor="my-dialog" command="close">Close</button>
</dialog>
```

#### نتیجه

با کلیک روی دکمه "Open dialog" dialog را باز کنید. می‌توانید dialog را با کلیک روی دکمه "Close" یا زدن کلید <kbd>Esc</kbd> ببندید.

### ویژگی‌های HTML مربوط به Popover API

این مثال نشان می‌دهد چگونه می‌توانید یک dialog غیر modal را با استفاده از ویژگی‌های HTML `popover`، `popovertarget` و `popovertargetaction` مربوط به [Popover API](/en-US/docs/Web/API/Popover_API) باز و بسته کنید.

با افزودن ویژگی `popover`، `<dialog>` به یک popover تبدیل می‌شود. از آنجا که مقدار خاصی برای ویژگی مشخص نکرده‌ایم، مقدار پیش‌فرض `"auto"` استفاده می‌شود. این رفتار "light dismiss" را فعال می‌کند و به شما امکان می‌دهد dialog را با کلیک خارج از آن یا با زدن <kbd>Esc</kbd> ببندید. اگر می‌خواستید این رفتار غیرفعال شود، می‌توانستید `popover="manual"` تنظیم کنید؛ در این صورت dialog فقط با دکمه "Close" بسته می‌شد.

توجه کنید که برای دکمه بازکننده dialog، ویژگی `popovertargetaction` را مشخص نکرده‌ایم. نیازی به این کار نیست، زیرا مقدار پیش‌فرض آن `toggle` است و با کلیک، dialog بین حالت باز و بسته جابه‌جا می‌شود.

```html
<button popovertarget="my-dialog">Open dialog</button>

<dialog id="my-dialog" popover>
  <p>This dialog was opened using a popovertargetaction attribute.</p>
  <button popovertarget="my-dialog" popovertargetaction="hide">Close</button>
</dialog>
```

#### نتیجه

با کلیک روی دکمه "Open dialog" dialog را باز کنید. می‌توانید dialog را با کلیک روی دکمه "Close" یا زدن <kbd>Esc</kbd> ببندید. همچنین می‌توانید با کلیک خارج از dialog آن را ببندید، زیرا این dialog غیر modal است.

### استفاده از ویژگی `open` در dialog

این مثال نشان می‌دهد که چطور می‌توانید attribute بولی `open` را روی یک `<dialog>` قرار دهید تا یک دیالوگ غیرمودال (non-modal) purely HTML بسازید که هنگام بارگذاری صفحه از قبل باز باشد.

دیالوگ با کلیک روی دکمه «OK» بسته می‌شود، چون `method` attribute در `<form>` برابر `"dialog"` است. در این حالت برای بستن فرم نیازی به JavaScript نیست.

```html
<dialog open>
  <p>Greetings, one and all!</p>
  <form method="dialog">
    <button>OK</button>
  </form>
</dialog>
```

#### نتیجه

این دیالوگ در ابتدا باز است و غیرمودال است، به دلیل وجود attribute `open`. پس از کلیک روی «OK»، دیالوگ بسته می‌شود و کادر نتیجه خالی می‌ماند.

> **نکته:** صفحه را مجدداً بارگذاری کنید تا خروجی ریست شود.

وقتی دیالوگ بسته شد، روشی برای باز کردن مجدد آن ارائه نشده است. روش ترجیحی برای نمایش دیالوگ‌های غیرمودال استفاده از متد `show()` از `HTMLDialogElement` است. امکان تغییر وضعیت نمایش دیالوگ با افزودن یا حذف attribute بولی `open` وجود دارد، اما این روش توصیه نمی‌شود.

### ایجاد یک دیالوگ مودال

این مثال یک دیالوگ مودال با پس‌زمینه [gradient](/en-US/docs/Web/CSS/Reference/Values/gradient) را نشان می‌دهد. متد `.showModal()` وقتی دکمه «Show the dialog» فعال شود، دیالوگ مودال را باز می‌کند. دیالوگ را می‌توان با فشردن کلید <kbd>Esc</kbd> یا از طریق متد `close()` وقتی دکمه «Close» داخل دیالوگ فعال شود، بست.

وقتی دیالوگ باز می‌شود، مرورگر به طور پیش‌فرض فوکوس را به اولین عنصر قابل فوکوس داخل دیالوگ می‌دهد. در این مثال، attribute [`autofocus`](/en-US/docs/Web/HTML/Reference/Global_attributes/autofocus) روی دکمه «Close» اعمال شده است تا هنگام باز شدن دیالوگ، فوکوس روی آن باشد، زیرا انتظار می‌رود کاربر بلافاصله پس از باز شدن دیالوگ با این عنصر تعامل کند.

#### HTML

```html
<dialog>
  <button autofocus>Close</button>
  <p>This modal dialog has a groovy backdrop!</p>
</dialog>
<button>Show the dialog</button>
```

#### CSS

می‌توانیم پس‌زمینه دیالوگ را با استفاده از pseudo-element `::backdrop` استایل دهیم.

```css
::backdrop {
  background-image: linear-gradient(
    45deg,
    magenta,
    rebeccapurple,
    dodgerblue,
    green
  );
  opacity: 0.75;
}
```

#### JavaScript

دیالوگ به صورت مودال با استفاده از متد `.showModal()` باز می‌شود و با متد `.close()` یا `.requestClose()` بسته می‌شود.

```js
const dialog = document.querySelector("dialog");
const showButton = document.querySelector("dialog + button");
const closeButton = document.querySelector("dialog button");

// "Show the dialog" button opens the dialog modally
showButton.addEventListener("click", () => {
  dialog.showModal();
});

// "Close" button closes the dialog
closeButton.addEventListener("click", () => {
  dialog.close();
});
```

#### نتیجه

وقتی دیالوگ مودال نمایش داده می‌شود، بالای هر دیالوگ دیگری که ممکن است وجود داشته باشد ظاهر می‌شود. همه چیز خارج از دیالوگ مودال غیرفعال (inert) است و تعاملات خارج از دیالوگ مسدود می‌شوند. توجه کنید که وقتی دیالوگ باز است، به جز خود دیالوگ، تعامل با سند ممکن نیست؛ دکمه «Show the dialog» تا حد زیادی توسط پس‌زمینه تقریباً مات دیالوگ پنهان شده و غیرفعال است.

### مدیریت مقدار بازگشتی از دیالوگ

این مثال [`returnValue`](/en-US/docs/Web/API/HTMLDialogElement/returnValue) مربوط به `<dialog>` و نحوه بستن یک دیالوگ مودال با استفاده از فرم را نشان می‌دهد. به طور پیش‌فرض، `returnValue` برابر با رشته خالی یا مقدار دکمه‌ای است که فرم را درون `<dialog>` ارسال می‌کند (اگر چنین دکمه‌ای وجود داشته باشد).

این مثال یک دیالوگ modal را باز می‌کند وقتی دکمهٔ "Show the dialog" فعال شود. داخل دیالوگ یک فرم با یک عنصر `<select>` و دو دکمه `<button>` وجود دارد که دکمه‌ها به‌طور پیش‌فرض `type="submit"` دارند. یک event listener مقدار دکمهٔ "Confirm" را با تغییر گزینه‌های select به‌روز می‌کند. اگر دکمهٔ "Confirm" برای بستن دیالوگ فعال شود، مقدار فعلی دکمه به‌عنوان return value در نظر گرفته می‌شود. اگر دیالوگ با فشار دادن دکمهٔ "Cancel" بسته شود، `returnValue` برابر `"cancel"` خواهد بود.

وقتی دیالوگ بسته می‌شود، مقدار بازگشتی زیر دکمهٔ "Show the dialog" نمایش داده می‌شود. اگر دیالوگ با کلید <kbd>Esc</kbd> بسته شود، `returnValue` به‌روز نمی‌شود و رویداد `close` رخ نمی‌دهد، بنابراین متن داخل عنصر `<output>` تغییر نمی‌کند.

#### HTML

```html
<!-- یک دیالوگ modal حاوی یک فرم -->
<dialog id="favDialog">
  <form>
    <p>
      <label>
        Favorite animal:
        <select>
          <option value="default">Choose…</option>
          <option>Brine shrimp</option>
          <option>Red panda</option>
          <option>Spider monkey</option>
        </select>
      </label>
    </p>
    <div>
      <button value="cancel" formmethod="dialog">Cancel</button>
      <button id="confirmBtn" value="default">Confirm</button>
    </div>
  </form>
</dialog>
<p>
  <button id="showDialog">Show the dialog</button>
</p>
<output></output>
```

#### JavaScript

دیالوگ با استفاده از یک event listener روی دکمهٔ "Show the dialog" باز می‌شود که وقتی دکمه کلیک شود، متد `HTMLDialogElement.showModal()` را فراخوانی می‌کند.

دیالوگ وقتی دکمهٔ "Cancel" کلیک شود بسته می‌شود، زیرا دکمه شامل ویژگی `formmethod="dialog"` است. وقتی `method` یک فرم `dialog` باشد، وضعیت فرم ذخیره می‌شود اما ارسال نمی‌شود و دیالوگ بسته می‌شود (این ویژگی متد پیش‌فرض `GET` عنصر `<form>` را نادیده می‌گیرد). بدون `action`، ارسال فرم با متد پیش‌فرض `GET` باعث بارگذاری مجدد صفحه می‌شود. ما از JavaScript برای جلوگیری از ارسال و بستن دیالوگ به‌ترتیب با متدهای `event.preventDefault()` و `HTMLDialogElement.close()` استفاده می‌کنیم.

```js
const showButton = document.getElementById("showDialog");
const favDialog = document.getElementById("favDialog");
const outputBox = document.querySelector("output");
const selectEl = favDialog.querySelector("select");
const confirmBtn = favDialog.querySelector("#confirmBtn");

// دکمه "Show the dialog" دیالوگ را به صورت modal باز می‌کند
showButton.addEventListener("click", () => {
  favDialog.showModal();
});

// دکمه "Cancel" دیالوگ را بدون ارسال می‌بندد (به دلیل [formmethod="dialog"]) و رویداد close را فعال می‌کند
favDialog.addEventListener("close", (e) => {
  outputBox.value =
    favDialog.returnValue === "default"
      ? "No return value."
      : `ReturnValue: ${favDialog.returnValue}.`; // باید "default" بررسی شود نه رشته خالی
});

// جلوگیری از رفتار پیش‌فرض دکمه "confirm" (ارسال فرم) و بستن دیالوگ با متد close() که رویداد close را فعال می‌کند
confirmBtn.addEventListener("click", (event) => {
  event.preventDefault(); // نمی‌خواهیم این فرم جعلی ارسال شود
  favDialog.close(selectEl.value); // مقدار select را اینجا ارسال می‌کنیم
});
```

#### Result

### بستن یک دیالوگ با input اجباری در فرم

وقتی یک فرم داخل دیالوگ دارای یک input اجباری (required) باشد، user agent فقط زمانی اجازه می‌دهد دیالوگ بسته شود که مقدار آن input را وارد کرده باشید. برای بستن چنین دیالوگی، یا از ویژگی `formnovalidate` روی دکمه بستن استفاده کنید، یا هنگام کلیک روی دکمه بستن، متد `close()` را روی شیء dialog فراخوانی کنید.

```markdown
<dialog id="dialog">
  <form method="dialog">
    <p>
      <label>
        Favorite animal:
        <input type="text" required />
      </label>
    </p>
    <div>
      <input type="submit" id="normal-close" value="Normal close" />
      <input
        type="submit"
        id="novalidate-close"
        value="Novalidate close"
        formnovalidate />
      <input type="submit" id="js-close" value="JS close" />
    </div>
  </form>
</dialog>
<p>
  <button id="show-dialog">Show the dialog</button>
</p>
<output></output>
```

```css hidden
[type="submit"] {
  margin-right: 1rem;
}
```

#### JavaScript

```js
const showBtn = document.getElementById("show-dialog");
const dialog = document.getElementById("dialog");
const jsCloseBtn = dialog.querySelector("#js-close");

showBtn.addEventListener("click", () => {
  dialog.showModal();
});

jsCloseBtn.addEventListener("click", (e) => {
  e.preventDefault();
  dialog.close();
});
```

#### Result

از خروجی می‌بینیم که بستن دیالوگ با دکمهٔ _Normal close_ غیرممکن است. اما اگر با استفاده از ویژگی `formnovalidate` روی دکمهٔ _Cancel_ اعتبارسنجی فرم را دور بزنیم، دیالوگ بسته می‌شود. همچنین به صورت برنامه‌نویسی‌شده، `dialog.close()` می‌تواند چنین دیالوگی را ببندد.

### مقایسهٔ رفتارهای مختلف closedby

این مثال تفاوت رفتار بین مقادیر مختلف ویژگی [`closedby`](#closedby) را نشان می‌دهد.

#### HTML

ما سه عنصر `<button>` و سه عنصر `<dialog>` داریم. هر دکمه طوری برنامه‌ریزی می‌شود که دیالوگ متفاوتی را باز کند و رفتار یکی از سه مقدار ویژگی `closedby` یعنی `none`، `closerequest` و `any` را نشان دهد. توجه داشته باشید که هر عنصر `<dialog>` شامل یک عنصر `<button>` است که برای بستن آن استفاده می‌شود.

```html live-sample___closedbyvalues
<p>Choose a <code>&lt;dialog&gt;</code> type to show:</p>
<div id="controls">
  <button id="none-btn"><code>closedby="none"</code></button>
  <button id="closerequest-btn">
    <code>closedby="closerequest"</code>
  </button>
  <button id="any-btn"><code>closedby="any"</code></button>
</div>

<dialog closedby="none">
  <h2><code>closedby="none"</code></h2>
  <p>
    Only closable using a specific provided mechanism, which in this case is
    pressing the "Close" button below.
  </p>
  <button class="close">Close</button>
</dialog>

<dialog closedby="closerequest">
  <h2><code>closedby="closerequest"</code></h2>
  <p>Closable using the "Close" button or the Esc key.</p>
  <button class="close">Close</button>
</dialog>

<dialog closedby="any">
  <h2><code>closedby="any"</code></h2>
  <p>
    Closable using the "Close" button, the Esc key, or by clicking outside the
    dialog. "Light dismiss" behavior.
  </p>
  <button class="close">Close</button>
</dialog>
```

```css hidden live-sample___closedbyvalues
body {
  font-family: sans-serif;
}

#controls {
  display: flex;
  justify-content: space-around;
}

dialog {
  width: 480px;
  border-radius: 5px;
  border-color: rgb(0 0 0 / 0.3);
}

dialog h2 {
  margin: 0;
}

dialog p {
  line-height: 1.4;
}
```

#### JavaScript

در اینجا متغیرهای مختلفی را برای ارجاع به عناصر `<button>` کنترلی اصلی، عناصر `<dialog>` و عناصر `<button>` با برچسب «Close» داخل دیالوگ‌ها تعریف می‌کنیم. ابتدا برای هر دکمهٔ کنترل، یک شنوندهٔ رویداد [`click`](/en-US/docs/Web/API/Element/click_event) با استفاده از [`addEventListener`](/en-US/docs/Web/API/EventTarget/addEventListener) تنظیم می‌کنیم؛ تابع مدیریت رویداد، عنصر `<dialog>` مرتبط را از طریق [`showModal()`](/en-US/docs/Web/API/HTMLDialogElement/showModal) باز می‌کند. سپس در میان ارجاع عناصر `<button>` با برچسب «Close» حلقه می‌زنیم و به هر کدام یک تابع مدیریت رویداد `click` اختصاص می‌دهیم که عنصر `<dialog>` مربوطه را از طریق [`close()`](/en-US/docs/Web/API/HTMLDialogElement/close) می‌بندد.
```

```js live-sample___closedbyvalues
const noneBtn = document.getElementById("none-btn");
const closerequestBtn = document.getElementById("closerequest-btn");
const anyBtn = document.getElementById("any-btn");

const noneDialog = document.querySelector("[closedby='none']");
const closerequestDialog = document.querySelector("[closedby='closerequest']");
const anyDialog = document.querySelector("[closedby='any']");

const closeBtns = document.querySelectorAll(".close");

noneBtn.addEventListener("click", () => {
  noneDialog.showModal();
});

closerequestBtn.addEventListener("click", () => {
  closerequestDialog.showModal();
});

anyBtn.addEventListener("click", () => {
  anyDialog.showModal();
});

closeBtns.forEach((btn) => {
  btn.addEventListener("click", () => {
    btn.parentElement.close();
  });
});
```

#### نتیجه

خروجی به‌صورت زیر است:

روی هر دکمه کلیک کنید تا یک dialog باز شود. dialog اول فقط با کلیک روی دکمه «بستن» (Close) خودش بسته می‌شود. dialog دوم علاوه بر آن، با یک عمل کاربری خاص دستگاه مثل فشار دادن کلید <kbd>Esc</kbd> هم بسته می‌شود. dialog سوم رفتار کامل [light-dismiss](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) را دارد، یعنی با کلیک یا ضربه زدن بیرون از dialog نیز بسته می‌شود.

### پویانمایی (انیمیشن) dialog‌ها

عناصر `<dialog>` وقتی مخفی هستند، `display: none;` و وقتی نمایش داده می‌شوند، `display: block;` دارند. همچنین از top layer و [درخت دسترسی‌پذیری](/en-US/docs/Web/Performance/Guides/How_browsers_work#building_the_accessibility_tree) حذف یا به آن اضافه می‌شوند. بنابراین برای اینکه عناصر `<dialog>` بتوانند پویانمایی شوند، باید خاصیت `display` قابل انیمیشن باشد. [مرورگرهای پشتیبانی‌کننده](/en-US/docs/Web/CSS/Reference/Properties/display#browser_compatibility) با استفاده از یک نوع انیمیشن گسسته (discrete animation type) `display` را متحرک می‌کنند. به‌طور خاص، مرورگر بین `none` و مقدار دیگری از `display` جابه‌جا می‌شود تا محتوای متحرک برای کل مدت انیمیشن نمایش داده شود.

برای مثال:

- هنگام انیمیشن `display` از `none` به `block` (یا هر مقدار قابل مشاهده دیگر)، مقدار در `0%` از مدت زمان انیمیشن به `block` تغییر می‌کند تا در تمام طول انیمیشن قابل مشاهده باشد.
- هنگام انیمیشن `display` از `block` (یا هر مقدار قابل مشاهده دیگر) به `none`، مقدار در `100%` از مدت زمان انیمیشن به `none` تغییر می‌کند تا در تمام طول انیمیشن قابل مشاهده باشد.

> [!NOTE]
> هنگام استفاده از [CSS transitions](/en-US/docs/Web/CSS/Guides/Transitions) برای انیمیشن، باید [`transition-behavior: allow-discrete`](/en-US/docs/Web/CSS/Reference/Properties/transition-behavior) تنظیم شود تا رفتار بالا فعال شود. این رفتار هنگام استفاده از [CSS animations](/en-US/docs/Web/CSS/Guides/Animations) به‌صورت پیش‌فرض در دسترس است و نیازی به گام مشابهی نیست.

#### انتقال (transition) عناصر dialog

هنگام پویانمایی `<dialog>`ها با CSS transitions، ویژگی‌های زیر مورد نیاز است:

#### قانون @starting-style

- `@starting-style` یک at-rule است که به شما امکان می‌دهد مجموعه‌ای از مقادیر شروع را برای ویژگی‌های `<dialog>` تعریف کنید که می‌خواهید هر بار که باز می‌شود از آن مقادیر transition کنید. این کار برای جلوگیری از رفتار غیرمنتظره ضروری است. به طور پیش‌فرض، transition های CSS فقط زمانی فعال می‌شوند که یک ویژگی روی یک عنصر قابل مشاهده از مقداری به مقدار دیگر تغییر کند؛ آن‌ها در اولین به‌روزرسانی استایل عنصر یا زمانی که `display` از `none` به مقدار دیگری تغییر می‌کند، فعال نمی‌شوند.

#### ویژگی `display`

- `display` را به لیست transition اضافه کنید تا `<dialog>` در طول مدت transition به عنوان `display: block` (یا هر مقدار قابل مشاهده‌ی دیگری که روی حالت باز دیالوگ تنظیم شده است) باقی بماند و بقیه‌ی transitionها قابل مشاهده باشند.

#### ویژگی `overlay`

- `overlay` را در لیست transition قرار دهید تا اطمینان حاصل شود که حذف `<dialog>` از لایه بالایی (top layer) تا پایان transition به تأخیر بیفتد و در نتیجه transition قابل مشاهده باشد.

#### ویژگی `transition-behavior`

- مقدار `transition-behavior: allow-discrete` را روی transition های `display` و `overlay` (یا روی shorthand `transition`) تنظیم کنید تا transition های گسسته (discrete) برای این دو ویژگی که به طور پیش‌فرض قابل انیمیشن نیستند، فعال شوند.

در ادامه یک مثال سریع برای نشان دادن نحوه‌ی کار این موارد آورده شده است.

##### HTML

HTML شامل یک عنصر `<dialog>` و یک دکمه برای نمایش دیالوگ است. همچنین درون `<dialog>` یک دکمه‌ی دیگر برای بستن خودش وجود دارد.

```html
<dialog id="dialog">
  Content here
  <button class="close">close</button>
</dialog>

<button class="show">Show Modal</button>
```

##### CSS

در CSS، یک بلوک `@starting-style` تعریف می‌کنیم که استایل‌های شروع transition را برای ویژگی‌های `opacity` و `transform` مشخص می‌کند. همچنین استایل‌های پایان transition را روی حالت `dialog:open` و استایل‌های پیش‌فرض روی حالت `dialog` (برای بازگشت به حالت اولیه پس از نمایش `<dialog>`) تعریف می‌کنیم. توجه کنید که لیست transition عنصر `<dialog>` نه تنها این ویژگی‌ها، بلکه `display` و `overlay` را نیز شامل می‌شود و روی هر کدام `allow-discrete` تنظیم شده است.

همچنین یک مقدار استایل شروع برای ویژگی `background-color` روی `::backdrop` (که پشت `<dialog>` هنگام باز شدن ظاهر می‌شود) تعریف می‌کنیم تا یک انیمیشن تیره‌کننده‌ی زیبا ایجاد کند. انتخابگر `dialog:open::backdrop` فقط پس‌زمینه‌های عناصر `<dialog>` را در حالت باز انتخاب می‌کند.

```css
/* حالت باز دیالوگ */
dialog:open {
  opacity: 1;
  transform: scaleY(1);
}

/* حالت بسته دیالوگ */
dialog {
  opacity: 0;
  transform: scaleY(0);
  transition:
    opacity 0.7s ease-out,
    transform 0.7s ease-out,
    overlay 0.7s ease-out allow-discrete,
    display 0.7s ease-out allow-discrete;
  /* معادل:
  transition: all 0.7s allow-discrete; */
}

/* حالت قبل از باز شدن */
/* باید بعد از قانون قبلی dialog:open قرار گیرد تا اثر کند،
   زیرا specificity یکسان است */
@starting-style {
  dialog:open {
    opacity: 0;
    transform: scaleY(0);
  }
}

/* transition برای :backdrop وقتی دیالوگ مودال به لایه بالایی منتقل می‌شود */
dialog::backdrop {
  background-color: transparent;
  transition:
    display 0.7s allow-discrete,
    overlay 0.7s allow-discrete,
    background-color 0.7s;
  /* معادل:
  transition: all 0.7s allow-discrete; */
}

dialog:open::backdrop {
  background-color: rgb(0 0 0 / 25%);
}

/* این قانون @starting-style نمی‌تواند داخل انتخابگر بالا تودرتو شود
   زیرا انتخابگر تودرتو نمی‌تواند pseudo-elements را نمایش دهد. */

@starting-style {
  dialog:open::backdrop {
    background-color: transparent;
  }
}
```

> **نکته:** در مرورگرهایی که از شبه‌کلاس `:open` پشتیبانی نمی‌کنند، می‌توانید از انتخابگر ویژگی `dialog[open]` برای استایل‌دهی به عنصر `<dialog>` در حالت باز استفاده کنید.

##### JavaScript

JavaScript رویدادهای کلیک را به دکمه‌های نمایش و بستن اضافه می‌کند تا با کلیک روی آن‌ها `<dialog>` نمایش داده یا بسته شود.

```js
const dialog = document.getElementById("dialog");
const showButton = document.querySelector(".show");
const closeButton = document.querySelector(".close");

showButton.addEventListener("click", () => {
  dialog.showModal();
});

closeButton.addEventListener("click", () => {
  dialog.close();
});
```

```js
const dialogElem = document.getElementById("dialog");
const showBtn = document.querySelector(".show");
const closeBtn = document.querySelector(".close");

showBtn.addEventListener("click", () => {
  dialogElem.showModal();
});

closeBtn.addEventListener("click", () => {
  dialogElem.close();
});
```

##### نتیجه

کد بالا به شکل زیر نمایش داده می‌شود:

{{ EmbedLiveSample("Transitioning dialog elements", "100%", "200") }}

> [!NOTE]
> از آنجایی که `<dialog>` هر بار که نمایش داده می‌شود از `display: none` به `display: block` تغییر می‌کند، در هر بار ورود، `<dialog>` از استایل‌های `@starting-style` خود به استایل‌های `dialog:open` انتقال می‌یابد. وقتی `<dialog>` بسته می‌شود، از حالت `dialog:open` به حالت پیش‌فرض `dialog` بازمی‌گردد.
>
> در این موارد ممکن است انتقال استایل در ورود و خروج متفاوت باشد. برای اثبات این موضوع، به مثال [نشان‌دهنده زمان استفاده از استایل‌های شروع](/en-US/docs/Web/CSS/Reference/At-rules/@starting-style#demonstration_of_when_starting_styles_are_used) ما مراجعه کنید.

#### انیمیشن‌های keyframe برای `<dialog>`

هنگام انیمیت کردن یک `<dialog>` با انیمیشن‌های `@keyframes` CSS، تفاوت‌هایی با transitionها وجود دارد:

- نیازی به ارائه `@starting-style` نیست.
- مقدار `display` را در یک keyframe قرار می‌دهید؛ این مقدار برای تمام مدت انیمیشن اعمال می‌شود، مگر اینکه به مقدار `display` دیگری غیر از `none` برخورد کنید.
- نیازی به فعال‌سازی صریح انیمیشن‌های گسسته (discrete) نیست؛ معادلی برای `allow-discrete` درون keyframes وجود ندارد.
- همچنین نیازی به تنظیم `overlay` درون keyframes نیست؛ انیمیشن `display` کار انیمیت کردن `<dialog>` از حالت نمایش به مخفی را انجام می‌دهد.

بیایید یک مثال ببینیم تا متوجه شوید این قابلیت چگونه کار می‌کند.

##### HTML

ابتدا HTML شامل یک عنصر `<dialog>` و یک دکمه برای نمایش dialog است. همچنین عنصر `<dialog>` خود شامل یک دکمه دیگر برای بستن خودش می‌شود.

```html
<dialog id="dialog">
  Content here
  <button class="close">close</button>
</dialog>

<button class="show">Show Modal</button>
```

##### CSS

CSS keyframeهایی را تعریف می‌کند که بین حالت بسته و باز `<dialog>` انیمیشن ایجاد کنند، به علاوه انیمیشن محو شدن (fade-in) برای پس‌زمینه (backdrop) `<dialog>`. انیمیشن‌های `<dialog>` شامل انیمیت کردن `display` هستند تا اطمینان حاصل شود که افکت‌های بصری قابل مشاهده در تمام مدت انیمیشن باقی می‌مانند. توجه داشته باشید که امکان انیمیت کردن محو شدن (fade-out) پس‌زمینه وجود ندارد – پس‌زمینه بلافاصله پس از بسته شدن `<dialog>` از DOM حذف می‌شود، بنابراین چیزی برای انیمیت کردن وجود ندارد.

```css
dialog {
  animation: fade-out 0.7s ease-out;
}

dialog:open {
  animation: fade-in 0.7s ease-out;
}

dialog:open::backdrop {
  background-color: black;
  animation: backdrop-fade-in 0.7s ease-out forwards;
}

/* Animation keyframes */

@keyframes fade-in {
  0% {
    opacity: 0;
    transform: scaleY(0);
    display: none;
  }

  100% {
    opacity: 1;
    transform: scaleY(1);
    display: block;
  }
}

@keyframes fade-out {
  0% {
    opacity: 1;
    transform: scaleY(1);
    display: block;
  }

  100% {
    opacity: 0;
    transform: scaleY(0);
    display: none;
  }
}

@keyframes backdrop-fade-in {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 0.25;
  }
}

body,
button {
  font-family: system-ui;
}
```

##### JavaScript

در نهایت، JavaScript رویدادگردان‌هایی به دکمه‌ها اضافه می‌کند تا نمایش و بستن `<dialog>` امکان‌پذیر شود:

```js
const dialogElem = document.getElementById("dialog");
const showBtn = document.querySelector(".show");
const closeBtn = document.querySelector(".close");

showBtn.addEventListener("click", () => {
  dialogElem.showModal();
});

closeBtn.addEventListener("click", () => {
  dialogElem.close();
});
```

##### نتیجه

کد بالا به شکل زیر نمایش داده می‌شود:

{{ EmbedLiveSample("dialog keyframe animations", "100%", "200") }}

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        ریشه بخش‌بندی
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچکدام، تگ شروع و پایان هر دو الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>
        را می‌پذیرد
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role">dialog</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role"><code>alertdialog</code></a></td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>HTMLDialogElement</td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- رابط HTMLDialogElement
- رویداد `close` از رابط HTMLDialogElement
- رویداد `cancel` از رابط HTMLDialogElement
- خاصیت `open` از رابط HTMLDialogElement
- ویژگی سراسری [`inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert) برای عناصر HTML
- شبه‌عنصر CSS `::backdrop`
- [فرم‌های وب](/en-US/docs/Learn_web_development/Extensions/Forms) در بخش آموزش