---
title: "Document: execCommand() method"
---

---
title: "Document: execCommand() method"
short-title: execCommand()
slug: Web/API/Document/execCommand
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.execCommand
---

{{ApiRef("DOM")}}{{deprecated_header}}{{non-standard_header}}

> [!NOTE]
> اگرچه متد `execCommand()` منسوخ شده است، اما هنوز موارد استفاده معتبری وجود دارد که جایگزین مناسبی برای آنها در دسترس نیست. برای مثال، بر خلاف دستکاری مستقیم DOM، تغییراتی که توسط `execCommand()` انجام می‌شود، بافر بازگشت (تاریخچه ویرایش) را حفظ می‌کند. برای این موارد استفاده، همچنان می‌توانید از این متد استفاده کنید، اما برای اطمینان از سازگاری بین مرورگرها، تست کنید، مثلاً با استفاده از {{domxref("document.queryCommandSupported()")}}.

متد **`execCommand`** چندین دستور مختلف را پیاده‌سازی می‌کند. برخی از آنها دسترسی به کلیپ‌بورد را فراهم می‌کنند، در حالی که برخی دیگر برای ویرایش [ورودی‌های فرم](/en-US/docs/Web/HTML/Reference/Elements/input)، عناصر [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) یا کل اسناد (در حالت [design mode](/en-US/docs/Web/API/Document/designMode)) استفاده می‌شوند.

برای دسترسی به کلیپ‌بورد، [Clipboard API](/en-US/docs/Web/API/Clipboard_API) جدیدتر به جای `execCommand()` توصیه می‌شود.

اکثر دستورات بر [انتخاب](/en-US/docs/Web/API/Selection) سند تأثیر می‌گذارند. برای مثال، برخی دستورات (چرب، کج و غیره) متن انتخاب‌شده را قالب‌بندی می‌کنند، در حالی که برخی دیگر انتخاب را حذف می‌کنند، عناصر جدیدی وارد می‌کنند (جایگزین انتخاب می‌شوند) یا روی یک خط کامل تأثیر می‌گذارند (تورفتگی). فقط عنصر قابل ویرایش فعال فعلی قابل تغییر است، اما برخی دستورات (مثلاً `copy`) می‌توانند بدون عنصر قابل ویرایش کار کنند.

> [!NOTE]
> تغییرات انجام‌شده توسط `execCommand()` ممکن است بسته به مرورگر و تنظیمات، رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} را فعال کنند یا نکنند. در صورت فعال شدن، مدیریت‌کننده‌های رویداد قبل از بازگشت `execCommand()` اجرا می‌شوند. نویسندگان باید مراقب چنین فراخوانی‌های بازگشتی باشند، به‌ویژه اگر `execCommand()` را در پاسخ به این رویدادها فراخوانی می‌کنند. از Firefox 82، فراخوانی‌های تو در توی `execCommand()` همیشه ناموفق خواهند بود، به [bug 1634262](https://bugzil.la/1634262) مراجعه کنید.

## Syntax

```js-nolint
execCommand(commandName, showDefaultUI, valueArgument)
```

### Parameters

- `commandName`
  - : رشته‌ای که نام دستور مورد نظر برای اجرا را مشخص می‌کند. دستورات زیر تعریف شده‌اند:
    - `backColor`
      - : رنگ پس‌زمینه سند را تغییر می‌دهد. در حالت `styleWithCss`، به جای آن بر رنگ پس‌زمینه بلوک محتوا تأثیر می‌گذارد. این نیاز به یک رشته مقدار {{cssxref("&lt;color&gt;")}} به عنوان آرگومان `value` دارد.
    - `bold`
      - : قالب چرب را برای انتخاب یا در نقطه درج روشن/خاموش می‌کند.
    - `contentReadOnly`
      - : سند محتوا را فقط خواندنی یا قابل ویرایش می‌کند. این نیاز به یک مقدار بولی `true`/`false` به عنوان آرگومان `value` دارد.
    - `copy`
      - : انتخاب فعلی را در کلیپ‌بورد کپی می‌کند. شرایط فعال بودن این رفتار از مرورگری به مرورگر دیگر متفاوت است و در طول زمان تکامل یافته است. برای تعیین اینکه آیا می‌توانید از آن در مورد خود استفاده کنید، جدول سازگاری را بررسی کنید.
    - `createLink`
      - : یک پیوند فوق‌متن از انتخاب ایجاد می‌کند، اما فقط در صورتی که انتخاب وجود داشته باشد. نیاز به یک رشته {{Glossary("URI")}} به عنوان آرگومان `value` برای `href` پیوند دارد. URI باید حداقل یک کاراکتر داشته باشد که می‌تواند فضای خالی باشد.
    - `cut`
      - : انتخاب فعلی را حذف کرده و در کلیپ‌بورد کپی می‌کند. زمان فعال بودن این رفتار بین مرورگرها متفاوت است و شرایط آن در طول زمان تکامل یافته است. برای جزئیات استفاده، [جدول سازگاری](#browser_compatibility) را بررسی کنید.
    - `decreaseFontSize`
      - : یک برچسب {{HTMLElement("small")}} دور انتخاب یا در نقطه درج اضافه می‌کند.
    - `defaultParagraphSeparator`
      - : جداکننده پاراگراف مورد استفاده هنگام ایجاد پاراگراف‌های جدید در مناطق متنی قابل ویرایش را تغییر می‌دهد.
    - `delete`
      - : انتخاب فعلی را حذف می‌کند.
    - `enableAbsolutePositionEditor`
      - : گیره‌ای که امکان جابجایی عناصر با موقعیت‌یابی مطلق را فراهم می‌کند، فعال یا غیرفعال می‌کند. این گیره از Firefox 64 به طور پیش‌فرض غیرفعال است ([Firefox bug 1490641](https://bugzil.la/1490641)).
    - `enableInlineTableEditing`
      - : کنترل‌های درج و حذف سطر/ستون جدول را فعال یا غیرفعال می‌کند. این کنترل‌ها از Firefox 64 به طور پیش‌فرض غیرفعال هستند ([Firefox bug 1490641](https://bugzil.la/1490641)).
    - `enableObjectResizing`
      - : دسته‌های تغییر اندازه روی تصاویر، جداول، عناصر با موقعیت‌یابی مطلق و سایر اشیاء قابل تغییر اندازه را فعال یا غیرفعال می‌کند. این دسته‌ها از Firefox 64 به طور پیش‌فرض غیرفعال هستند ([Firefox bug 1490641](https://bugzil.la/1490641)).
    - `fontName`
      - : نام فونت را برای انتخاب یا در نقطه درج تغییر می‌دهد. این نیاز به یک رشته نام فونت (مانند `"Arial"`) به عنوان آرگومان `value` دارد.
    - `fontSize`
      - : اندازه فونت را برای انتخاب یا در نقطه درج تغییر می‌دهد. این نیاز به یک عدد صحیح از `1` تا `7` به عنوان آرگومان `value` دارد.
    - `foreColor`
      - : رنگ فونت را برای انتخاب یا در نقطه درج تغییر می‌دهد. این نیاز به یک رشته مقدار رنگ هگزادسیمال به عنوان آرگومان `value` دارد.
    - `formatBlock`
      - : یک عنصر بلوکی HTML در اطراف خط حاوی انتخاب فعلی اضافه می‌کند و در صورت وجود، عنصر بلوکی حاوی آن خط را جایگزین می‌کند (در Firefox، {{HTMLElement("blockquote")}} استثنا است — هر عنصر بلوکی محتوا را در بر می‌گیرد). نیاز به یک رشته نام برچسب به عنوان آرگومان `value` دارد. تقریباً تمام عناصر بلوکی قابل استفاده هستند. (Edge قدیمی فقط از برچسب‌های عنوان `H1` – `H6`، `ADDRESS` و `PRE` پشتیبانی می‌کند که باید درون براکت‌های زاویه‌ای قرار گیرند، مانند `"<H1>"`.)
    - `forwardDelete`
      - : کاراکتر جلوی موقعیت [مکان‌نما](https://en.wikipedia.org/wiki/Cursor_%28computers%29) را حذف می‌کند، مشابه فشردن کلید Delete روی صفحه‌کلید ویندوز.
    - `heading`
      - : یک عنصر عنوان در اطراف یک خط انتخاب یا نقطه درج اضافه می‌کند. نیاز به رشته نام برچسب به عنوان آرگومان `value` دارد (یعنی `"H1"`، `"H6"`). (توسط Safari پشتیبانی نمی‌شود.)
    - `hiliteColor`
      - : رنگ پس‌زمینه را برای انتخاب یا در نقطه درج تغییر می‌دهد. نیاز به یک رشته مقدار رنگ به عنوان آرگومان `value` دارد. برای عملکرد، `useCSS` باید `true` باشد.
    - `increaseFontSize`
      - : یک برچسب {{HTMLElement("big")}} دور انتخاب یا در نقطه درج اضافه می‌کند.
    - `indent`
      - : خط حاوی انتخاب یا نقطه درج را تورفتگی می‌دهد. در Firefox، اگر انتخاب شامل چندین خط با سطوح مختلف تورفتگی باشد، فقط کم‌تورفتگی‌ترین خطوط در انتخاب تورفتگی می‌گیرند.
    - `insertBrOnReturn`
      - : کنترل می‌کند که آیا کلید Enter یک عنصر {{HTMLElement("br")}} وارد می‌کند یا عنصر بلوکی فعلی را به دو قسمت تقسیم می‌کند.
    - `insertHorizontalRule`
      - : یک عنصر {{HTMLElement("hr")}} در نقطه درج وارد می‌کند یا انتخاب را با آن جایگزین می‌کند.
    - `insertHTML`
      - : یک نمونه {{domxref("TrustedHTML")}} یا رشته‌ای از نشانه‌گذاری HTML را در نقطه درج وارد می‌کند (انتخاب را حذف می‌کند). این نیاز به نشانه‌گذاری HTML معتبر دارد.

        > [!WARNING]
        > ورودی به عنوان HTML تجزیه شده و در DOM نوشته می‌شود. APIهایی مانند این به عنوان [sinkهای تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و به طور بالقوه یک بردار برای حملات [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند، اگر ورودی در اصل از طرف یک مهاجم باشد.
        >
        > می‌توانید این خطر را با همیشه اختصاص دادن اشیاء {{domxref("TrustedHTML")}} به جای رشته‌ها و [اجباری کردن انواع مورد اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید. برای اطلاعات بیشتر به [Trusted Types API](/en-US/docs/Web/API/Trusted_Types_API) مراجعه کنید.

    - `insertImage`
      - : یک تصویر در نقطه درج وارد می‌کند (انتخاب را حذف می‌کند). نیاز به یک رشته URL برای `src` تصویر به عنوان آرگومان `value` دارد. الزامات این رشته همانند `createLink` است.
    - `insertLineBreak`
      - : انتخاب را حذف کرده و آن را با یک [عنصر شکست خط](/en-US/docs/Web/HTML/Reference/Elements/br) جایگزین می‌کند.
    - `insertOrderedList`
      - : یک [لیست مرتب شماره‌دار](/en-US/docs/Web/HTML/Reference/Elements/ol) برای انتخاب یا در نقطه درج ایجاد می‌کند.
    - `insertUnorderedList`
      - : یک [لیست نامرتب گلوله‌ای](/en-US/docs/Web/HTML/Reference/Elements/ul) برای انتخاب یا در نقطه درج ایجاد می‌کند.
    - `insertParagraph`
      - : یک [پاراگراف](/en-US/docs/Web/HTML/Reference/Elements/p) در اطراف انتخاب یا خط فعلی وارد می‌کند.
    - `insertText`
      - : متن ساده داده شده را در نقطه درج وارد می‌کند (انتخاب را حذف می‌کند).
    - `italic`
      - : قالب کج را برای انتخاب یا در نقطه درج روشن/خاموش می‌کند.
    - `justifyCenter`
      - : انتخاب یا نقطه درج را وسط‌چین می‌کند.
    - `justifyFull`
      - : انتخاب یا نقطه درج را هم‌تراز می‌کند.
    - `justifyLeft`
      - : انتخاب یا نقطه درج را به چپ می‌چسباند.
    - `justifyRight`
      - : انتخاب یا نقطه درج را به راست می‌چسباند.
    - `outdent`
      - : تورفتگی خط حاوی انتخاب یا نقطه درج را کاهش می‌دهد.
    - `paste`
      - : محتویات کلیپ‌بورد را در نقطه درج می‌چسباند (انتخاب فعلی را جایگزین می‌کند).

        این ویژگی به عنوان غیرفعال برای _محتوای وب_ مشخص شده است، اما در برخی مرورگرها از طریق [Clipboard API](/en-US/docs/Web/API/Clipboard_API#security_considerations) پیاده‌سازی شده است. در این مرورگرها، این ویژگی نیاز به {{glossary("transient activation")}} و تأیید یک UI پاپ‌آپ هنگام چسباندن محتوای متقاطع-منبع دارد. برای اطلاعات بیشتر به [جدول سازگاری مرورگر](#browser_compatibility) مراجعه کنید.

    - `redo`
      - : آخرین دستور بازگشت را دوباره انجام می‌دهد.
    - `removeFormat`
      - : همه قالب‌بندی‌ها را از انتخاب فعلی حذف می‌کند.
    - `selectAll`
      - : تمام محتوای منطقه قابل ویرایش را انتخاب می‌کند.
    - `strikeThrough`
      - : قالب خط‌خورده را برای انتخاب یا در نقطه درج روشن/خاموش می‌کند.
    - `subscript`
      - : قالب [زیرنویس](/en-US/docs/Web/HTML/Reference/Elements/sub) را برای انتخاب یا در نقطه درج روشن/خاموش می‌کند.
    - `superscript`
      - : قالب [بالانویس](/en-US/docs/Web/HTML/Reference/Elements/sup) را برای انتخاب یا در نقطه درج روشن/خاموش می‌کند.
    - `underline`
      - : قالب [زیرخط](/en-US/docs/Web/HTML/Reference/Elements/u) را برای انتخاب یا در نقطه درج روشن/خاموش می‌کند.
    - `undo`
      - : آخرین دستور اجرا شده را بازمی‌گرداند.
    - `unlink`
      - : عنصر [لنگر](/en-US/docs/Web/HTML/Reference/Elements/a) را از یک پیوند فوق‌متن انتخاب‌شده حذف می‌کند.
    - `useCSS` {{Deprecated_inline}}
      - : استفاده از برچسب‌های HTML یا CSS را برای نشانه‌گذاری تولید شده تغییر می‌دهد. نیاز به یک مقدار بولی `true`/`false` به عنوان آرگومان `value` دارد.
        > [!NOTE]
        > این آرگومان از نظر منطقی معکوس است (یعنی برای استفاده از CSS از `false` و برای استفاده از HTML از `true` استفاده کنید). این به نفع `styleWithCSS` منسوخ شده است.
    - `styleWithCSS`
      - : جایگزین دستور `useCSS` می‌شود. `true` ویژگی‌های `style` را در نشانه‌گذاری تغییر/تولید می‌کند، `false` عناصر نمایشی تولید می‌کند.
    - `AutoUrlDetect`
      - : رفتار تشخیص خودکار پیوند مرورگر را تغییر می‌دهد.
- `showDefaultUI`
  - : یک مقدار بولی که نشان می‌دهد آیا رابط کاربری پیش‌فرض باید نمایش داده شود یا خیر. این در موزیلا پیاده‌سازی نشده است.
- `valueArgument`
  - : برای دستوراتی که به یک آرگومان ورودی نیاز دارند، یک رشته است که آن اطلاعات را فراهم می‌کند. برای مثال، `insertImage` به URL تصویر برای درج نیاز دارد. اگر نیازی به آرگومان نیست، `null` را مشخص کنید.

### Return value

یک مقدار بولی که اگر دستور پشتیبانی نشود یا غیرفعال باشد، `false` است.

> [!NOTE]
> `document.execCommand()` فقط در صورتی `true` را برمی‌گرداند که به عنوان بخشی از یک تعامل کاربر فراخوانی شود. نمی‌توانید از آن برای تأیید پشتیبانی مرورگر قبل از فراخوانی یک دستور استفاده کنید.

## Examples

### استفاده از insertText

این مثال دو ویرایشگر HTML بسیار ساده را نشان می‌دهد، یکی با استفاده از عنصر {{HTMLElement("textarea")}} و دیگری با استفاده از عنصر {{HTMLElement("pre")}} با ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) تنظیم شده.

با کلیک روی دکمه‌های "Bold" یا "Italic"، برچسب‌های مناسب در عنصر درج می‌شوند، با استفاده از `insertText` برای حفظ تاریخچه ویرایش، به طوری که کاربر بتواند عمل را بازگرداند.

#### HTML

```html
<h2>textarea</h2>

<div class="actions" data-for="textarea">
  <button data-el="b">Bold</button>
  <button data-el="i">Italic</button>
</div>

<textarea class="editarea">Some text.</textarea>

<h2>contenteditable</h2>

<div class="actions" data-for="pre">
  <button data-el="b">Bold</button>
  <button data-el="i">Italic</button>
</div>

<pre contenteditable="true" class="editarea">Some text.</pre>
```

#### JavaScript

```js
// Prepare action buttons
const buttonContainers = document.querySelectorAll(".actions");

for (const buttonContainer of buttonContainers) {
  const buttons = buttonContainer.querySelectorAll("button");
  const pasteTarget = buttonContainer.getAttribute("data-for");

  for (const button of buttons) {
    const elementName = button.getAttribute("data-el");
    button.addEventListener("click", () =>
      insertText(`<${elementName}></${elementName}>`, pasteTarget),
    );
  }
}

// Inserts text at cursor, or replaces selected text
function insertText(newText, selector) {
  const textarea = document.querySelector(selector);
  textarea.focus();

  let pasted = true;
  try {
    if (!document.execCommand("insertText", false, newText)) {
      pasted = false;
    }
  } catch (e) {
    console.error("error caught:", e);
    pasted = false;
  }

  if (!pasted) {
    console.error("paste unsuccessful, execCommand not supported");
  }
}
```

#### Result

{{EmbedLiveSample("Using insertText", 100, 300)}}

### استفاده از paste

این مثال دارای یک عنصر {{HTMLElement("textarea")}} و یک عنصر {{HTMLElement("button")}} است که می‌توانید از آن برای چسباندن محتوا درون آن استفاده کنید.

#### HTML

```html
<button id="paste">Paste</button>
<hr />
<textarea id="text_box">Some text.</textarea>
```

#### JavaScript

```js
const pasteButton = document.querySelector("#paste");
const textBox = document.querySelector("#text_box");

pasteButton.addEventListener("click", () => {
  textBox.focus();

  let pasted = document.execCommand("paste", false);
  if (!pasted) {
    textBox.textContent = "paste unsuccessful, execCommand not supported";
  }
});
```

#### Result

در مرورگرهایی که این ویژگی را با استفاده از [Clipboard API](/en-US/docs/Web/API/Clipboard_API#security_considerations) پیاده‌سازی می‌کنند، باید بتوانید محتوای هم‌منبع (مانند متن از ناحیه متنی) را کپی کرده و سپس آن را برای جایگزینی هر محتوای انتخاب‌شده بچسبانید. وقتی سعی می‌کنید محتوای متقاطع-منبع (مانند متنی که از هر صفحه یا مکان دیگری کپی شده است) را بچسبانید، ابتدا باید UI "Paste" که نمایش داده می‌شود را انتخاب کنید.

{{EmbedLiveSample("Using paste", 100, 300)}}

## Specifications

این ویژگی بخشی از هیچ مشخصات فعلی نیست. دیگر در مسیر تبدیل شدن به یک استاندارد نیست. یک [پیش‌نویس غیررسمی مشخصات execCommand از W3C](https://w3c.github.io/editing/docs/execCommand/) وجود دارد.

## Browser compatibility

{{Compat}}

## See also

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- مثال MDN: [execCommands پشتیبانی شده در مرورگر شما](https://mdn.github.io/dom-examples/execcommand/)
- {{domxref("HTMLElement.contentEditable")}}
- {{domxref("document.designMode")}}
- {{domxref("document.queryCommandEnabled()")}}
- {{domxref("document.queryCommandState()")}}
- {{domxref("document.queryCommandSupported()")}}