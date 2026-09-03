---
title: Using the Popover API
slug: Web/API/Popover_API/Using
page-type: guide
---

{{DefaultAPISidebar("Popover API")}}

**Popover API** سازوکاری استاندارد، سازگار و انعطاف‌پذیر در اختیار توسعه‌دهندگان قرار می‌دهد تا بتوانند محتوای پاپاور را روی دیگر محتوای صفحه نمایش دهند. محتوای پاپاور را می‌توان یا به‌صورت اعلانی (declarative) با استفاده از ویژگی‌های HTML کنترل کرد، یا از طریق جاوااسکریپت. این مقاله راهنمای مفصلی برای استفاده از تمام قابلیت‌های این API ارائه می‌دهد.

## ایجاد پاپاورهای اعلانی

در ساده‌ترین شکل، یک پاپاور با افزودن ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) به عنصری که می‌خواهید محتوای پاپاور را در خود نگه دارد ایجاد می‌شود. برای مرتبط‌کردن پاپاور با کنترل‌هایش، به یک `id` نیز نیاز دارید.

```html
<div id="mypopover" popover>Popover content</div>
```

> [!NOTE]
> تنظیم ویژگی `popover` بدون مقدار، معادل تنظیم `popover="auto"` است.

با افزودن این ویژگی، عنصر در بارگذاری صفحه با اعمال {{cssxref("display", "display: none")}} مخفی می‌شود. برای نمایش/پنهان‌کردن پاپاور، باید حداقل یک دکمه کنترل (که به آن فراخوانِ پاپاور یا **invoker** نیز گفته می‌شود) اضافه کنید. می‌توانید یک {{htmlelement("button")}} (یا {{htmlelement("input")}} با `type="button"`) را با دادن ویژگی [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) به دکمهٔ کنترل پاپاور تبدیل کنید؛ مقدار این ویژگی باید ID پاپاوری باشد که قرار است کنترل شود:

```html
<button popovertarget="mypopover">Toggle the popover</button>
<div id="mypopover" popover>Popover content</div>
```

رفتار پیش‌فرض این است که دکمه به‌صورت دکمهٔ تغییر وضعیت (toggle) عمل می‌کند؛ با فشردن مکرر آن، پاپاور بین حالت نمایش و مخفی جابه‌جا می‌شود.

اگر می‌خواهید این رفتار را تغییر دهید، می‌توانید از ویژگی [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) استفاده کنید؛ این ویژگی یکی از مقادیر `"hide"`، `"show"` یا `"toggle"` را می‌پذیرد. برای مثال، برای ایجاد دکمه‌های جداگانهٔ نمایش و پنهان‌کردن می‌توانید چنین کنید:

```html
<button popovertarget="mypopover" popovertargetaction="show">
  Show popover
</button>
<button popovertarget="mypopover" popovertargetaction="hide">
  Hide popover
</button>
<div id="mypopover" popover>Popover content</div>
```

می‌توانید نتیجهٔ رندر قطعه‌کد بالا را در [نمونهٔ پاپاور اعلانی پایه](https://mdn.github.io/dom-examples/popover-api/basic-declarative/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/basic-declarative)) ببینید.

> [!NOTE]
> اگر ویژگی `popovertargetaction` ذکر نشود، عمل پیش‌فرضی که دکمهٔ کنترل انجام می‌دهد «toggle» است.

وقتی پاپاوری نمایش داده می‌شود، `display: none` از آن حذف می‌شود و به {{glossary("top layer")}} منتقل می‌شود تا روی تمام محتوای دیگر صفحه قرار بگیرد.

### `command` و `commandfor`

ویژگی‌های [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor) و [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command) عملکردی بسیار مشابه `popovertarget` و `popovertargetaction` ارائه می‌دهند، اما با طراحی عمومی‌تر که هدف آن فراهم‌کردن قابلیت‌هایی فراتر از دستورات پاپاور، از جمله دستورات سفارشی، است.

قطعه‌کد قبلی را می‌توان این‌گونه بازنویسی کرد:

```html live-sample___command-commandfor
<button commandfor="mypopover" command="show-popover">Show popover</button>
<button commandfor="mypopover" command="hide-popover">Hide popover</button>
<div id="mypopover" popover>Popover content</div>
```

{{EmbedLiveSample("command-commandfor", "100%", "100")}}

## حالت auto و «light dismiss»

وقتی عنصر پاپاور با `popover` یا `popover="auto"` همان‌طور که در بالا نشان داده شد تنظیم شود، گفته می‌شود در **حالت auto** قرار دارد. رفتارهای مهم این حالت عبارت‌اند از:

- پاپاور قابلیت «light dismiss» دارد؛ یعنی می‌توانید با کلیک‌کردن بیرون از آن، پاپاور را مخفی کنید.
- پاپاور را می‌توان با مکانیزم‌های خاص مرورگر مانند فشردن کلید <kbd>Esc</kbd> نیز بست.
- معمولاً فقط یک پاپاور `auto` می‌تواند در هر لحظه نمایش داده شود — نمایش یک پاپاور دوم وقتی پاپاوری در حال نمایش است، پاپاور اول را مخفی می‌کند. استثنای این قاعده زمانی است که پاپاورهای `auto` تودرتو داشته باشید. برای جزئیات بیشتر، بخش [پاپاورهای تودرتو](#nested_popovers) را ببینید.

> [!NOTE]
> پاپاورهای `popover="auto"` همچنین وقتی فراخوانی موفق {{domxref("HTMLDialogElement.showModal()")}} یا {{domxref("Element.requestFullscreen()")}} روی عناصر دیگر سند انجام شود، بسته می‌شوند. توجه داشته باشید که فراخواندن این متدها روی یک پاپاورِ در حال نمایش با شکست مواجه می‌شود، زیرا این رفتارها برای پاپاوری که از قبل نمایش داده شده معنایی ندارند. با این حال، می‌توانید این متدها را روی عنصری که ویژگی `popover` دارد ولی در حال حاضر نمایش داده نشده است فراخوانی کنید.

حالت auto زمانی مفید است که فقط می‌خواهید در هر لحظه یک پاپاور واحد نمایش داده شود. شاید چند پیام آموزشی رابط کاربری دارید که می‌خواهید نمایش دهید، اما نمی‌خواهید نمایش صفحه شلوغ و گیج‌کننده شود؛ یا پیام‌های وضعیتی نشان می‌دهید که در آن‌ها وضعیت جدید، وضعیت قبلی را لغو می‌کند.

می‌توانید رفتار توصیف‌شده را در [نمونهٔ پاپاورهای auto چندگانه](https://mdn.github.io/dom-examples/popover-api/multiple-auto/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/multiple-auto)) در عمل ببینید. پس از نمایش پاپاورها، «light dismiss» را امتحان کنید و ببینید وقتی می‌خواهید هر دو را هم‌زمان نمایش دهید چه اتفاقی می‌افتد.

## ویژگی‌های دسترس‌پذیری پاپاور

وقتی از طریق ویژگی `popovertarget` رابطه‌ای بین یک پاپاور و کنترل‌کنندهٔ آن (فراخوان) برقرار شود، API به‌طور خودکار دو تغییر دیگر در محیط ایجاد می‌کند تا کاربران صفحه‌کلید و فناوری‌های کمکی (AT) بتوانند راحت‌تر با پاپاور تعامل کنند:

- وقتی پاپاور نمایش داده می‌شود، ترتیب پیمایش فوکوس با صفحه‌کلید به‌روزرسانی می‌شود تا پاپاور در مرحلهٔ بعدی ترتیب قرار گیرد؛ برای مثال، وقتی دکمه‌ای برای نمایش پاپاور فشرده می‌شود، هر دکمه‌ای که داخل پاپاور باشد در ترتیب بعدی tab قرار می‌گیرد (با فشردن کلید <kbd>Tab</kbd> فوکوس می‌گیرد). برعکس، هنگام بستن پاپاور با صفحه‌کلید (معمولاً با کلید <kbd>Esc</kbd>)، فوکوس به فراخوان بازگردانده می‌شود.
- برای اینکه فناوری کمکی مانند صفحه‌خوان‌ها بتوانند رابطهٔ بین فراخوان و پاپاور را درک کنند، یک رابطهٔ ضمنی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) و [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) بین آن‌ها برقرار می‌شود.

برقراری رابطه بین پاپاور و کنترل‌کننده‌اش به این روش، یک ارجاع لنگر ضمنی (implicit anchor reference) بین آن دو نیز ایجاد می‌کند — برای جزئیات بیشتر به بخش [جای‌گذاری پاپاور نسبت به لنگر](#popover_anchor_positioning) مراجعه کنید.

## روش‌های دیگر برقراری رابطه پاپاور و فراخوان

علاوه بر استفاده از ویژگی `popovertarget`، می‌توانید رابطه پاپاور و فراخوان را به روش‌های دیگری نیز برقرار کنید:

- با استفاده از گزینهٔ `source` در متدهای {{domxref("HTMLElement.showPopover()")}} یا {{domxref("HTMLElement.togglePopover()")}}. توجه داشته باشید که در این حالت فقط تغییرات ترتیب پیمایش فوکوس اعمال می‌شود، نه رابطهٔ ضمنی ARIA. دلیل این است که گزینهٔ `source` را می‌توان به هر نوع عنصری تنظیم کرد، نه فقط عناصر {{htmlelement("button")}}، و نمی‌توان تضمین کرد که چنین رابطه‌ای همیشه معنا داشته باشد.
- بین عنصر {{htmlelement("select")}} و انتخابگر بازشوی آن، زمانی که آن را با مقدار `base-select` ویژگی {{cssxref("appearance")}} به قابلیت [عنصر select سفارشی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select) وارد می‌کنید. در این حالت، یک رابطهٔ ضمنی پاپاور-فراخوان بین آن دو ایجاد می‌شود.

## استفاده از حالت manual پاپاور

یک جایگزین برای حالت auto، **حالت manual** است که با تنظیم `popover="manual"` روی عنصر پاپاور به دست می‌آید:

```html
<div id="mypopover" popover="manual">Popover content</div>
```

در این حالت:

- پاپاور را نمی‌توان با «light dismiss» بست، هرچند دکمه‌های اعلانی نمایش/پنهان‌کردن/تغییر وضعیت (که قبلاً دیدیم) همچنان کار می‌کنند.
- می‌توان چند پاپاور مستقل را هم‌زمان نمایش داد.

می‌توانید این رفتار را در [نمونهٔ پاپاورهای manual چندگانه](https://mdn.github.io/dom-examples/popover-api/multiple-manual/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/multiple-manual)) ببینید.

## رویدادهای `beforetoggle` و `toggle`

می‌توانید به نمایش یا پنهان‌شدن پاپاور با استفاده از رویدادهای [`beforetoggle`](/en-US/docs/Web/API/HTMLElement/beforetoggle_event) و [`toggle`](/en-US/docs/Web/API/HTMLElement/toggle_event) پاسخ دهید:

- رویداد `beforetoggle` درست قبل از نمایش یا پنهان‌شدن پاپاور رخ می‌دهد. این رویداد را می‌توان برای مثال برای جلوگیری از نمایش یا پنهان‌شدن پاپاور (با استفاده از {{domxref("Event.preventDefault()")}})، افزودن کلاس‌های انیمیشن به پاپاور برای جان‌دارکردن آن، یا پاک‌سازی وضعیت پاپاور پس از استفاده از آن به کار برد.
- رویداد `toggle` درست بعد از نمایش یا پنهان‌شدن پاپاور رخ می‌دهد. معمولاً از این رویداد برای اجرای کدهای دیگر در پاسخ به تغییر وضعیت باز/بسته پاپاور استفاده می‌شود.

هر دوی این رویدادها دارای شیء رویداد {{domxref("ToggleEvent")}} هستند. این شیء علاوه بر ویژگی‌هایی که از شیء پیش‌فرض {{domxref("Event")}} به ارث می‌برد، ویژگی‌های زیر را نیز دارد:

- ویژگی‌های {{domxref("ToggleEvent.oldState", "oldState")}} و {{domxref("ToggleEvent.newState", "newState")}} نشان می‌دهند که پاپاور به‌تازگی از چه حالتی به چه حالتی منتقل شده است و به شما امکان می‌دهند به‌طور خاص به باز یا بسته‌شدن پاپاور پاسخ دهید.
- ویژگی {{domxref("ToggleEvent.source", "source")}} حاوی ارجاعی به عنصر کنترل HTML پاپاوری است که تغییر وضعیت را آغاز کرده است و به شما امکان می‌دهد بسته به این‌که کدام کنترل رویداد را فعال کرده، کد متفاوتی اجرا کنید.

یک نمونهٔ استفادهٔ معمول می‌تواند چیزی شبیه به این باشد:

```js
const popover = document.getElementById("mypopover");

popover.addEventListener("toggle", (e) => {
  console.log(e.newState);
});
```

توجه داشته باشید که فراخواندن {{domxref("HTMLElement.showPopover()", "showPopover()")}}، {{domxref("HTMLElement.hidePopover()", "hidePopover()")}} یا {{domxref("HTMLElement.togglePopover()", "togglePopover()")}} از داخل شنوندهٔ رویداد `beforetoggle` در حالی که پاپاور دیگری در حال نمایش یا پنهان‌شدن است، مجاز نیست و باعث ایجاد `InvalidStateError` از نوع `DOMException` می‌شود.

برای اطلاعات بیشتر و مثال‌ها، به پیوندهای مرجع پیشین مراجعه کنید.

## نمایش پاپاورها از طریق جاوااسکریپت

همچنین می‌توانید پاپاورها را با استفاده از یک API جاوااسکریپتی کنترل کنید.

از ویژگی {{domxref("HTMLElement.popover")}} می‌توان برای خواندن یا تنظیم ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) استفاده کرد. این ویژگی برای ایجاد پاپاور از طریق جاوااسکریپت به کار می‌رود و برای تشخیص پشتیبانی (feature detection) نیز مفید است. برای مثال:

```js
function supportsPopover() {
  return Object.hasOwn(HTMLElement.prototype, "popover");
}
```

به‌طور مشابه:

- ویژگی‌های {{domxref("HTMLButtonElement.popoverTargetElement")}} و {{domxref("HTMLInputElement.popoverTargetElement")}} معادلی برای ویژگی [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) فراهم می‌کنند و به شما امکان می‌دهند دکمه(های) کنترل یک پاپاور را تنظیم کنید. با این تفاوت که مقدار این ویژگی، یک ارجاع به عنصر DOM پاپاور موردنظر است.
- ویژگی‌های {{domxref("HTMLButtonElement.popoverTargetAction")}} و {{domxref("HTMLInputElement.popoverTargetAction")}} معادلی برای ویژگی [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) فراهم می‌کنند و به شما امکان می‌دهند عمل موردنظر دکمهٔ کنترل را مشخص کنید.

با کنار هم گذاشتن این سه مورد، می‌توانید به‌صورت برنامه‌نویسی‌شده یک پاپاور و دکمهٔ کنترل آن را تنظیم کنید:

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

const popoverSupported = supportsPopover();

if (popoverSupported) {
  popover.popover = "auto";
  toggleBtn.popoverTargetElement = popover;
  toggleBtn.popoverTargetAction = "toggle";
} else {
  toggleBtn.style.display = "none";
}
```

همچنین چندین روش برای کنترل نمایش و پنهان‌کردن در اختیار دارید:

- {{domxref("HTMLElement.showPopover()")}} برای نمایش پاپاور.
- {{domxref("HTMLElement.hidePopover()")}} برای پنهان‌کردن پاپاور.
- {{domxref("HTMLElement.togglePopover()")}} برای تغییر وضعیت پاپاور.

برای مثال، شاید بخواهید امکان روشن/خاموش‌کردن یک پاپاور راهنما را با کلیک روی دکمه یا فشردن یک کلید خاص از صفحه‌کلید فراهم کنید. حالت اول را می‌توان به‌صورت اعلانی انجام داد، یا همان‌طور که در بالا نشان داده شد با جاوااسکریپت پیاده‌سازی کرد.

برای حالت دوم، می‌توانید یک event handler ایجاد کنید که دو کلید جداگانه را مدیریت کند؛ یکی برای بازکردن پاپاور و دیگری برای بستن آن:

```js
document.addEventListener("keydown", (event) => {
  if (event.key === "h") {
    if (popover.matches(":popover-open")) {
      popover.hidePopover();
    }
  }

  if (event.key === "s") {
    if (!popover.matches(":popover-open")) {
      popover.showPopover();
    }
  }
});
```

این مثال از {{domxref("Element.matches()")}} برای بررسی برنامه‌نویسی‌شدهٔ نمایش‌داشته‌شدن پاپاور استفاده می‌کند. شبه‌کلاس {{cssxref(":popover-open")}} فقط پاپاورهایی را انتخاب می‌کند که در حال حاضر نمایش داده می‌شوند. این موضوع برای جلوگیری از خطاهایی اهمیت دارد که هنگام تلاش برای نمایش یک پاپاورِ از‌قبل‌نمایش‌داده‌شده یا پنهان‌کردن یک پاپاورِ از‌قبل‌پنهان رخ می‌دهند.

از طرف دیگر، می‌توانید یک کلید واحد را طوری برنامه‌ریزی کنید که پاپاور را هم نمایش دهد و هم مخفی کند:

```js
document.addEventListener("keydown", (event) => {
  if (event.key === "h") {
    popover.togglePopover();
  }
});
```

برای مشاهدهٔ ویژگی‌های جاوااسکریپتی پاپاور، تشخیص پشتیبانی و متد `togglePopover()` در عمل، به [نمونهٔ رابط کاربری راهنمای تغییر وضعیت](https://mdn.github.io/dom-examples/popover-api/toggle-help-ui/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/toggle-help-ui)) مراجعه کنید.

## پاپاورهای تودرتو

برای قاعدهٔ «نمایش‌ندادن چند پاپاور auto به‌طور هم‌زمان» یک استثنا وجود دارد — وقتی پاپاورها داخل یکدیگر تودرتو باشند. در چنین مواردی، به دلیل رابطهٔ آن‌ها با یکدیگر، چند پاپاور می‌توانند هم‌زمان باز باشند. این الگو برای پشتیبانی از موارد استفاده‌ای مانند منوهای پاپاور تودرتو در نظر گرفته شده است.

سه روش مختلف برای ایجاد پاپاورهای تودرتو وجود دارد:

۱. فرزندان مستقیم DOM:

```html
<div popover>
  Parent
  <div popover>Child</div>
</div>
```

۲. از طریق عناصر فراخوان/کنترل:

```html
<div popover>
  Parent
  <button popovertarget="foo">Click me</button>
</div>

<div popover id="foo">Child</div>
```

۳. از طریق ویژگی `anchor`:

```html
<div popover id="foo">Parent</div>

<div popover anchor="foo">Child</div>
```

> [!NOTE]
> یک پاپاور `auto` نمی‌تواند در پشتهٔ پاپاور `auto` دارای پدری از نوع `hint` باشد (هرچند می‌تواند پاپاورهای `auto` یا `hint` را تودرتو کند).
> اگر یک پاپاور `auto` به‌صورت ساختاری درون یک پاپاور `hint` قرار گرفته باشد — برای مثال، پاپاور `auto` فرزند DOM پاپاور `hint` باشد یا فراخوان آن درون پاپاور `hint` باشد — مرورگر به‌طور خودکار نوع مؤثر پاپاور `auto` را به `hint` تنزل می‌دهد و با آن چنین رفتار می‌شود.

برای مثال، به [نمونهٔ منوی پاپاور تودرتو](https://mdn.github.io/dom-examples/popover-api/nested-popovers/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/nested-popovers)) مراجعه کنید. خواهید دید که برای نمایش و پنهان‌کردن مناسب زیرپاپاور هنگام دسترسی با ماوس و صفحه‌کلید، و همچنین برای پنهان‌کردن هر دو منو وقتی از هرکدام گزینه‌ای انتخاب می‌شود، تعداد قابل توجهی event handler به کار رفته است. بسته به اینکه بارگذاری محتوای جدید را در یک SPA یا وب‌سایت چندصفحه‌ای مدیریت کنید، ممکن است برخی یا همهٔ این‌ها ضروری نباشند، اما برای اهداف نمایشی در این دمو گنجانده شده‌اند.

### ایجاد زیرمنوها با `popover="auto"`

زیرمنوهای بازشو به‌صورت اعلانی و با استفاده از پاپاورهای `auto` ساخته شده‌اند.

ابتدا دکمه‌های کنترل:

```html
<section id="button-bar">
  <button popovertarget="submenu-1" popovertargetaction="toggle" id="menu-1">
    Menu A
  </button>

  <button popovertarget="submenu-2" popovertargetaction="toggle" id="menu-2">
    Menu B
  </button>

  <button popovertarget="submenu-3" popovertargetaction="toggle" id="menu-3">
    Menu C
  </button>
</section>
```

حالا خود پاپاورها:

```html
<div id="submenu-1" popover="auto">
  <button>Option A</button><br /><button>Option B</button>
</div>
<div id="submenu-2" popover="auto">
  <button>Option A</button><br /><button>Option B</button>
</div>
<div id="submenu-3" popover="auto">
  <button>Option A</button><br /><button>Option B</button>
</div>
```

## استفاده از حالت پاپاور «hint»

نوع سومی از پاپاور نیز وجود دارد که می‌توانید بسازید — **پاپاورهای hint** که با تنظیم `popover="hint"` روی عنصر پاپاور مشخص می‌شوند. این پاپاورها قابلیت «light dismiss» دارند و به درخواست‌های بستن پاسخ می‌دهند.

پاپاورهای `hint` هنگام نمایش، پاپاورهای `auto` را نمی‌بندند؛ اما سایر پاپاورهای `hint` را که در [پشتهٔ hint](#popover_openclose_interaction_rules) نیای آن‌ها نیستند می‌بندند. عکس این موضوع نیز صادق است: بستن یک پاپاور `auto` با فشردن کلید <kbd>Esc</kbd> یا با «light dismiss» روی پاپاورهای `hint` اثری نمی‌گذارد، مگر این‌که آن‌ها از فرزندان پاپاور autoِ بسته‌شده باشند.

این حالت برای موقعیت‌هایی مفید است که مثلاً دکمه‌های نوار ابزار دارید که با فشردن آن‌ها پاپاورهای رابط کاربری نمایش داده می‌شوند، اما می‌خواهید هنگام بردن نشانگر روی دکمه‌ها، tooltip ها نیز بدون بستن پاپاورهای رابط کاربری باز ظاهر شوند.

پاپاورهای `hint` معمولاً در پاسخ به رویدادهای جاوااسکریپتیِ غیر از کلیک مانند [`mouseover`](/en-US/docs/Web/API/Element/mouseover_event)/[`mouseout`](/en-US/docs/Web/API/Element/mouseout_event) و [`focus`](/en-US/docs/Web/API/Element/focus_event)/[`blur`](/en-US/docs/Web/API/Element/blur_event) نمایش داده و مخفی می‌شوند. توجه داشته باشید که ممکن است برای بازکردن پاپاور `hint` روی دکمه‌ای کلیک کنید، اما این کلیک باعث «light dismiss» شدن پاپاورهای `auto`ای می‌شود که دکمه بیرون از آن‌هاست (که احتمالاً قصد شما نیست).

برای مشاهدهٔ نمونه‌ای که دقیقاً مطابق توضیح بالا عمل می‌کند، [دموی پاپاور hint](https://mdn.github.io/dom-examples/popover-api/popover-hint/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/popover-hint)) را ببینید. در این دمو یک نوار دکمه وجود دارد؛ با فشردن دکمه‌ها، زیرمنوهای بازشوی `auto` نمایش داده می‌شوند که داخل آن‌ها می‌توان گزینه‌های بیشتری انتخاب کرد. علاوه بر این، وقتی نشانگر ماوس روی دکمه‌ها می‌رود یا آن‌ها فوکوس می‌گیرند، tooltip هایی (پاپاورهای `hint`) نیز نمایش داده می‌شوند تا به کاربر ایده‌ای از عملکرد هر دکمه بدهند، بدون این‌که زیرمنوی در حال نمایش مخفی شود.

در بخش‌های زیر، تمام بخش‌های مهم کد را بررسی خواهیم کرد.

> [!NOTE]
> می‌توانید پاپاورهای `hint` را در کنار پاپاورهای `manual` استفاده کنید، هرچند دلیل چندانی برای این کار وجود ندارد. پاپاورهای `hint` برای دور زدن برخی از محدودیت‌های پاپاورهای `auto` طراحی شده‌اند و موارد استفاده‌ای مانند نمونهٔ شرح‌داده‌شده در این بخش را ممکن می‌سازند.
>
> همچنین توجه داشته باشید که `popover="hint"` در مرورگرهای فاقد پشتیبانی، به `popover="manual"` بازمی‌گردد.

> [!NOTE]
> یک ویژگی مرتبط نیز وجود دارد — **interest invokers** — که می‌توان از آن برای ایجاد قابلیت پاپاور هنگام hover/focus به‌شکلی راحت و سازگار، بدون نیاز به جاوااسکریپت استفاده کرد. برای آشنایی بیشتر، [استفاده از interest invokers](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) را ببینید.

### ایجاد tooltip ها با `popover="hint"`

زیرمنوهای پاپاور همان‌طور که هستند درست کار می‌کنند و با فشردن دکمه‌های نوار ابزار باز می‌شوند، اما چگونه می‌توانیم هنگام hover/focus روی دکمه‌ها tooltip نیز نمایش دهیم؟ ابتدا tooltip ها را در HTML و با استفاده از پاپاورهای `hint` می‌سازیم:

```html
<div id="tooltip-1" class="tooltip" popover="hint">Tooltip A</div>
<div id="tooltip-2" class="tooltip" popover="hint">Tooltip B</div>
<div id="tooltip-3" class="tooltip" popover="hint">Tooltip C</div>
```

> [!NOTE]
> در [کد منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/popover-hint) دمو، tooltip ها داخل دکمه‌های کنترل پاپاور قرار گرفته‌اند؛ زیرا این کار بازگشت به عقب (fallback) بهتری در مرورگرهایی فراهم می‌کند که از CSS anchor positioning پشتیبانی نمی‌کنند — پاپاورهای `hint` در آن حالت کنار دکمه‌های کنترل مربوطه ظاهر می‌شوند، نه جای دیگر.

برای کنترل نمایش/پنهان‌کردن، باید از جاوااسکریپت استفاده کنیم. ابتدا ارجاع‌هایی به پاپاورهای `hint` و دکمه‌های کنترل را در دو {{domxref("NodeList")}} جداگانه با استفاده از {{domxref("Document.querySelectorAll()")}} می‌گیریم:

```js
const tooltips = document.querySelectorAll(".tooltip");
const btns = document.querySelectorAll("#button-bar button");
```

سپس تابعی به نام `addEventListeners()` می‌سازیم که چهار شنوندهٔ رویداد (از طریق {{domxref("EventTarget.addEventListener()")}}) روی یک {{htmlelement("button")}} مشخص تنظیم می‌کند؛ دکمهٔ موردنظر با گرفتن عنصر `<button>` در اندیس خاصی از `NodeList` به نام `btns` انتخاب می‌شود. این توابع روی پاپاور `hint` در همان اندیس از `NodeList` به نام `tooltips` عمل می‌کنند و به این ترتیب دکمه‌ها و tooltip ها همگام می‌مانند — هنگام تعامل با هر دکمه، tooltip درست نمایش یا مخفی می‌شود.

شنونده‌های رویداد، پاپاور را در رویدادهای [`mouseover`](/en-US/docs/Web/API/Element/mouseover_event) و [`focus`](/en-US/docs/Web/API/Element/focus_event) [نمایش](/en-US/docs/Web/API/HTMLElement/showPopover) می‌دهند و در رویدادهای [`mouseout`](/en-US/docs/Web/API/Element/mouseout_event) و [`blur`](/en-US/docs/Web/API/Element/blur_event) [مخفی](/en-US/docs/Web/API/HTMLElement/hidePopover) می‌کنند؛ یعنی tooltip ها هم با ماوس و هم با صفحه‌کلید قابل دسترسی هستند.

```js
function addEventListeners(i) {
  btns[i].addEventListener("mouseover", () => {
    tooltips[i].showPopover({ source: btns[i] });
  });

  btns[i].addEventListener("mouseout", () => {
    tooltips[i].hidePopover();
  });

  btns[i].addEventListener("focus", () => {
    tooltips[i].showPopover({ source: btns[i] });
  });

  btns[i].addEventListener("blur", () => {
    tooltips[i].hidePopover();
  });
}
```

در نهایت، با یک حلقهٔ [`for`](/en-US/docs/Web/JavaScript/Reference/Statements/for) روی عناصر `<button>` در `NodeList` به نام `btns` پیمایش می‌کنیم و برای تک‌تک آن‌ها تابع `addEventListeners()` را صدا می‌زنیم تا همهٔ آن‌ها شنونده‌های رویداد موردنظر را داشته باشند.

```js
for (let i = 0; i < btns.length; i++) {
  addEventListeners(i);
}
```

## قوانین تعامل باز و بسته‌شدن پاپاور

مرورگر دو پشتهٔ مستقل برای پاپاورهای باز نگه می‌دارد: یک **پشتهٔ auto** برای پاپاورهای `auto` و یک **پشتهٔ hint** برای پاپاورهای `hint`. وقتی پاپاوری نمایش داده می‌شود، به پشتهٔ مناسب اضافه می‌شود؛ وقتی پنهان می‌شود، مرورگر در آن پشته به سمت پایین حرکت می‌کند و ابتدا هر پاپاور فرزندی را که در آن پشته است می‌بندد. از آنجا که این دو پشته از هم جدا هستند، عملیات روی یکی به‌طور خودکار روی دیگری اثر نمی‌گذارد.

چند قاعدهٔ خاص دربارهٔ نحوهٔ تعامل پاپاورها که از این مشخصات به دست می‌آیند عبارت‌اند از:

- نمایش پاپاور `hint` پاپاورهای `auto` را نمی‌بندد.
- نمایش پاپاور `hint` سایر پاپاورهای `hint` را می‌بندد، به‌جز آن‌هایی که در پشتهٔ hint نیای پاپاور جدید هستند.
- کلیک بیرون از یک پاپاور، تمام پاپاورهای باز `auto` و `hint` را که نیای آن پاپاور نیستند با «light dismiss» می‌بندد.
- پنهان‌کردن پاپاور `auto` پاپاورهای `hint` را که از فرزندان آن نیستند نمی‌بندد.
- نمایش پاپاور `auto` به‌عنوان فرزند یک پاپاور `hint`، نوع پاپاور `auto` را به `hint` تنزل می‌دهد.
- نمایش یک پاپاور در حالی که پاپاور دیگری در حال نمایش یا پنهان‌شدن است مجاز نیست.

توجه داشته باشید که پاپاورهای `manual` در هیچ‌یک از این دو پشته شرکت نمی‌کنند — آن‌ها به‌صورت مستقل نمایش داده و مخفی می‌شوند و روی پاپاورهای auto یا hint اثری ندارند.

## استایل‌دهی به پاپاورها

این بخش برخی از تکنیک‌های انتخاب و جای‌گذاری CSS مرتبط با پاپاورها را پوشش می‌دهد.

### انتخاب پاپاورها

می‌توانید همهٔ پاپاورها را با یک attribute selector ساده انتخاب کنید:

```css
[popover] {
  /* Declarations here */
}
```

همچنین می‌توانید نوع خاصی از پاپاور را با افزودن مقدار به attribute selector انتخاب کنید:

```css
[popover="auto"] {
  /* Declarations here */
}
```

می‌توانید فقط پاپاورهایی را که در حال نمایش هستند با شبه‌کلاس {{cssxref(":popover-open")}} انتخاب کنید:

```css
:popover-open {
  /* Declarations here */
}
```

### استایل‌دهی به پس‌زمینهٔ پاپاور

شبه‌عنصر {{cssxref("::backdrop")}} یک عنصر تمام‌صفحه است که دقیقاً پشت عناصر پاپاورِ در حال نمایش در {{glossary("top layer")}} قرار می‌گیرد و در صورت تمایل امکان افزودن افکت به محتوای پشت پاپاور(ها) را فراهم می‌کند. برای مثال، شاید بخواهید محتوای پشت پاپاور را تار کنید تا توجه کاربر بر پاپاور متمرکز شود:

```css
::backdrop {
  backdrop-filter: blur(3px);
}
```

برای آشنایی با نتیجهٔ این کار، [نمونهٔ پس‌زمینهٔ تار پاپاور](https://mdn.github.io/dom-examples/popover-api/blur-background/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/blur-background)) را ببینید.

### جای‌گذاری پاپاورها

هنگام مشاهدهٔ چند مثال ابتدای مقاله، احتمالاً متوجه شده‌اید که پاپاورها در وسط viewport ظاهر می‌شوند، محتوای خود را در بر می‌گیرند و حاشیهٔ مشکی دارند. این استایل پیش‌فرض است که با قاعدهٔ زیر در stylesheet مرورگر (UA) به دست می‌آید:

```css
[popover] {
  position: fixed;
  inset: 0;
  width: fit-content;
  height: fit-content;
  margin: auto;
  border: solid;
  padding: 0.25em;
  overflow: auto;
  color: CanvasText;
  background-color: Canvas;
}
```

برای اعمال اندازهٔ سفارشی و قراردادن پاپاور در جای دیگر، می‌توانید استایل‌های بالا را با چیزی شبیه به این بازنویسی کنید:

```css
:popover-open {
  width: 200px;
  height: 100px;
  position: absolute;
  inset: unset;
  bottom: 5px;
  right: 5px;
  margin: 0;
}
```

یک مثال مستقل از این موضوع را در [نمونهٔ جای‌گذاری پاپاور](https://mdn.github.io/dom-examples/popover-api/popover-positioning/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/popover-positioning)) می‌بینید.

### جای‌گذاری پاپاور نسبت به لنگر

گزینهٔ مفید دیگری برای جای‌گذاری نیز وجود دارد که Popover API فراهم می‌کند. اگر می‌خواهید پاپاور را نسبت به فراخوان آن جای‌گذاری کنید، نه نسبت به viewport یا یک ancestor موقعیت‌دار، می‌توانید از این واقعیت بهره ببرید که پاپاورها و فراخوان‌هایشان یک **ارجاع لنگر ضمنی** دارند.

[همراه‌کردن هر نوع پاپاور با فراخوانش](#other_ways_to_set_up_a_popover-invoker_relationship) یک ارجاع لنگر ضمنی بین آن دو ایجاد می‌کند. این باعث می‌شود فراخوان به **عنصر لنگر** پاپاور تبدیل شود؛ یعنی می‌توانید پاپاور را با استفاده از [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) نسبت به آن جای‌گذاری کنید.

از آنجا که ارتباط بین پاپاور و فراخوان ضمنی است، نیازی به برقراری ارتباط صریح با ویژگی‌های {{cssxref("anchor-name")}} و {{cssxref("position-anchor")}} نیست. با این حال، همچنان باید CSS جای‌گذاری را مشخص کنید.

برای مثال، می‌توانید از ترکیبی از مقادیر تابع {{cssxref("anchor()")}} در {{glossary("inset properties")}} و مقادیر `anchor-center` در ویژگی‌های تراز استفاده کنید:

```css
.my-popover {
  margin: 0;
  inset: auto;
  bottom: calc(anchor(top) + 20px);
  justify-self: anchor-center;
}
```

یا می‌توانید از ویژگی {{cssxref("position-area")}} استفاده کنید:

```css
.my-popover {
  margin: 0;
  inset: auto;
  position-area: top;
}
```

هنگام استفاده از {{cssxref("position-area")}} یا {{cssxref("anchor()")}} برای جای‌گذاری پاپاورها، توجه داشته باشید که [استایل‌های پیش‌فرض پاپاورها](https://html.spec.whatwg.org/multipage/rendering.html#flow-content-3) ممکن است با موقعیتی که می‌خواهید به دست آورید در تضاد باشد. معمولاً مقصر اصلی، استایل‌های پیش‌فرض `margin` و `inset` هستند؛ بنابراین بهتر است مانند مثال‌های بالا آن‌ها را بازنشانی کنید. گروه کاری CSS در حال [بررسی راه‌هایی برای بی‌نیاز شدن از این راهکار](https://github.com/w3c/csswg-drafts/issues/10258) است.

برای جزئیات بیشتر دربارهٔ ارتباط عناصر لنگر و عناصر موقعیت‌دار و جای‌گذاری عناصر نسبت به لنگرشان، به [استفاده از CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#positioning_elements_relative_to_their_anchor) مراجعه کنید.

> [!NOTE]
> برای نمونه‌ای که از این ارتباط ضمنی استفاده می‌کند، [دموی پاپاور hint](https://mdn.github.io/dom-examples/popover-api/popover-hint/) ([منبع](https://github.com/mdn/dom-examples/tree/main/popover-api/popover-hint)) را ببینید. اگر کد CSS را بررسی کنید، می‌بینید که هیچ ارتباط لنگر صریحی با ویژگی‌های {{cssxref("anchor-name")}} و {{cssxref("position-anchor")}} برقرار نشده است.

> [!NOTE]
> اگر می‌خواهید ارجاع لنگر ضمنی را حذف کنید تا پاپاور به فراخوانش لنگر نشود، می‌توانید ویژگی `position-anchor` پاپاور را روی نام لنگری تنظیم کنید که در سند فعلی وجود ندارد، مانند `--not-an-anchor-name`. همچنین به [حذف یک ارتباط لنگر](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#removing_an_anchor_association) مراجعه کنید.

## انیمیت کردن پاپاورها

پاپاورها وقتی پنهان هستند با `display: none;` و وقتی نمایش داده می‌شوند با `display: block;` تنظیم می‌شوند؛ همچنین از {{glossary("top layer")}} و [درخت دسترس‌پذیری](/en-US/docs/Web/Performance/Guides/How_browsers_work#building_the_accessibility_tree) حذف یا به آن اضافه می‌شوند. بنابراین برای اینکه پاپاورها قابل انیمیت باشند، ویژگی {{cssxref("display")}} باید قابل انیمیت باشد. [مرورگرهای پشتیبان](/en-US/docs/Web/CSS/Reference/Properties/display#browser_compatibility) مقدار `display` را با تغییری از [نوع انیمیشن گسسته](/en-US/docs/Web/CSS/Guides/Animations/Animatable_properties#discrete) انیمیت می‌کنند. به‌طور مشخص، مرورگر بین `none` و مقدار دیگری از `display` جابه‌جا می‌شود تا محتوای انیمیت‌شده در تمام مدت انیمیشن دیده شود. برای مثال:

- هنگام انیمیت `display` از `none` به `block` (یا هر مقدار نمایش دیگری)، مقدار در `0%` مدت انیمیشن به `block` تغییر می‌کند تا در تمام مدت قابل مشاهده باشد.
- هنگام انیمیت `display` از `block` (یا هر مقدار نمایش دیگری) به `none`، مقدار در `100%` مدت انیمیشن به `none` تغییر می‌کند تا در تمام مدت قابل مشاهده باشد.

> [!NOTE]
> هنگام انیمیت با [CSS transitions](/en-US/docs/Web/CSS/Guides/Transitions)، باید [`transition-behavior: allow-discrete`](/en-US/docs/Web/CSS/Reference/Properties/transition-behavior) تنظیم شود تا رفتار بالا فعال شود. هنگام انیمیت با [CSS animations](/en-US/docs/Web/CSS/Guides/Animations)، رفتار بالا به‌صورت پیش‌فرض در دسترس است و مرحلهٔ مشابهی لازم نیست.

### ترنزیشن دادن به پاپاور

هنگام انیمیت پاپاورها با CSS transitions، امکانات زیر لازم هستند:

- شئقانون {{CSSxRef("@starting-style")}}
  - : مجموعه‌ای از مقادیر شروع را برای ویژگی‌هایی که روی پاپاور تنظیم شده‌اند و می‌خواهید هنگام نخستین نمایش، ترنزیشن را از آن‌ها شروع کنید فراهم می‌کند. این کار برای جلوگیری از رفتار غیرمنتظره لازم است. به‌طور پیش‌فرض، CSS transitions فقط زمانی رخ می‌دهند که یک ویژگی روی یک عنصر قابل مشاهده از یک مقدار به مقدار دیگر تغییر کند؛ آن‌ها در نخستین به‌روزرسانی استایل یک عنصر یا وقتی نوع `display` از `none` به نوع دیگری تغییر می‌کند، فعال نمی‌شوند.
- ویژگی {{CSSxRef("display")}}
  - : `display` را به فهرست ترنزیشن‌ها اضافه کنید تا پاپاور در طول مدت ترنزیشن به‌صورت `display: block` (یا مقدار نمایشی دیگر) باقی بماند و سایر ترنزیشن‌ها قابل مشاهده باشند.
- ویژگی {{CSSxRef("overlay")}}
  - : `overlay` را در فهرست ترنزیشن‌ها قرار دهید تا حذف پاپاور از top layer تا پایان ترنزیشن به تعویق بیفتد و ترنزیشن دیده شود.
- ویژگی {{cssxref("transition-behavior")}}
  - : مقدار `transition-behavior: allow-discrete` را روی ترنزیشن‌های `display` و `overlay` (یا روی shorthand مربوط به {{cssxref("transition")}}) تنظیم کنید تا ترنزیشن گسسته روی این دو ویژگی که به‌طور پیش‌فرض قابل انیمیت نیستند فعال شود.

بیایید به یک مثال نگاه کنیم تا ببینید این موضوع چگونه است:

#### HTML

HTML شامل یک عنصر {{htmlelement("div")}} است که با ویژگی سراسری [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) به‌عنوان پاپاور تعریف شده و یک عنصر {{htmlelement("button")}} که به‌عنوان دکمهٔ کنترل نمایش پاپاور تعیین شده است:

```html
<button popovertarget="mypopover">Show the popover</button>
<div popover="auto" id="mypopover">I'm a Popover! I should animate.</div>
```

#### CSS

دو ویژگی پاپاوری که می‌خواهیم ترنزیشن بدهیم، {{cssxref("opacity")}} و {{cssxref("transform")}} هستند. می‌خواهیم پاپاور هنگام ورود یا خروج، هم محو/ظاهر شود و هم به‌صورت افقی کوچک/بزرگ شود. برای رسیدن به این هدف، یک حالت شروع برای این ویژگی‌ها در حالت پنهان عنصر پاپاور (که با [attribute selector](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) `[popover]` انتخاب می‌شود) و یک حالت پایان برای حالت نمایش عنصر پاپاور (که با شبه‌کلاس {{cssxref(":popover-open")}} انتخاب می‌شود) تنظیم می‌کنیم. همچنین از ویژگی {{cssxref("transition")}} برای تعریف ویژگی‌های قابل ترنزیشن و مدت زمان انیمیشن هنگام نمایش یا پنهان‌شدن پاپاور استفاده می‌کنیم.

```css
html {
  font-family: "Helvetica", "Arial", sans-serif;
}

/* Transition for the popover itself */

[popover]:popover-open {
  opacity: 1;
  transform: scaleX(1);
}

[popover] {
  font-size: 1.2rem;
  padding: 10px;

  /* Final state of the exit animation */
  opacity: 0;
  transform: scaleX(0);

  transition:
    opacity 0.7s,
    transform 0.7s,
    overlay 0.7s allow-discrete,
    display 0.7s allow-discrete;
  /* Equivalent to
  transition: all 0.7s allow-discrete; */
}

/* Needs to be after the previous [popover]:popover-open rule
to take effect, as the specificity is the same */
@starting-style {
  [popover]:popover-open {
    opacity: 0;
    transform: scaleX(0);
  }
}

/* Transition for the popover's backdrop */

[popover]::backdrop {
  background-color: transparent;
  transition:
    display 0.7s allow-discrete,
    overlay 0.7s allow-discrete,
    background-color 0.7s;
  /* Equivalent to
  transition: all 0.7s allow-discrete; */
}

[popover]:popover-open::backdrop {
  background-color: rgb(0 0 0 / 25%);
}

/* The nesting selector (&) cannot represent pseudo-elements
so this starting-style rule cannot be nested */

@starting-style {
  [popover]:popover-open::backdrop {
    background-color: transparent;
  }
}
```

همان‌طور که پیش‌تر بحث شد، ما همچنین:

- یک حالت شروع برای `transition` داخل بلوک `@starting-style` تنظیم کرده‌ایم.
- `display` را به فهرست ویژگی‌های ترنزیشن‌پذیر اضافه کرده‌ایم تا عنصر انیمیت‌شده در تمام مدت انیمیشن ورود و خروج پاپاور قابل مشاهده باشد (یعنی `display: block` بماند). بدون این کار، انیمیشن خروج دیده نمی‌شد و پاپاور عملاً ناپدید می‌شد.
- `overlay` را به فهرست ویژگی‌های ترنزیشن‌پذیر اضافه کرده‌ایم تا مطمئن شویم حذف عنصر از top layer تا پایان انیمیشن به تعویق می‌افتد. اثر این کار ممکن است در انیمیشن‌های ساده‌ای مانند این مثال چندان محسوس نباشد، اما در موارد پیچیده‌تر، حذف این ویژگی می‌تواند باعث شود عنصر پیش از پایان ترنزیشن از overlay حذف شود.
- در ترنزیشن‌های بالا، مقدار `allow-discrete` را روی هر دو ویژگی تنظیم کرده‌ایم تا [ترنزیشن‌های گسسته](/en-US/docs/Web/CSS/Guides/Animations/Animatable_properties#discrete) فعال شوند.

توجه خواهید کرد که برای {{cssxref("::backdrop")}} که هنگام بازشدن پاپاور پشت آن ظاهر می‌شود نیز ترنزیشن در نظر گرفته‌ایم که انیمیشن تیره‌شدن مناسبی ایجاد می‌کند.

#### نتیجه

کد به این شکل رندر می‌شود:

{{ EmbedLiveSample("Transitioning a popover", "100%", "200") }}

> [!NOTE]
> چون پاپاورها هر بار که نمایش داده می‌شوند از `display: none` به `display: block` تغییر می‌کنند، پاپاور در هر بار انجام ترنزیشن ورود، از استایل‌های `@starting-style` خود به استایل‌های `[popover]:popover-open` ترنزیشن می‌کند. وقتی پاپاور بسته می‌شود، از حالت `[popover]:popover-open` به حالت پیش‌فرض `[popover]` ترنزیشن می‌کند.
>
> در چنین مواردی ممکن است ترنزیشن استایل هنگام ورود و خروج متفاوت باشد. برای اثبات این موضوع، به [نمونهٔ نشان‌دهندهٔ زمان استفاده از استایل‌های شروع](/en-US/docs/Web/CSS/Reference/At-rules/@starting-style#demonstration_of_when_starting_styles_are_used) مراجعه کنید.

### انیمیشن keyframe برای پاپاور

هنگام انیمیت پاپاور با انیمیشن‌های keyframe در CSS، تفاوت‌هایی وجود دارد که باید به آن‌ها توجه کنید:

- نیازی به ارائه‌ی `@starting-style` نیست؛ مقادیر «از» و «به» مربوط به `display` را داخل keyframe ها قرار می‌دهید.
- انیمیشن‌های گسسته را به‌صورت صریح فعال نمی‌کنید؛ معادلی برای `allow-discrete` درون keyframe ها وجود ندارد.
- نیازی به تنظیم `overlay` درون keyframe ها نیست؛ انیمیشن `display`، انیمیشن پاپاور را از حالت نمایش به حالت پنهان مدیریت می‌کند.

بیایید یک مثال را بررسی کنیم.

#### HTML

HTML شامل یک عنصر {{htmlelement("div")}} است که به‌عنوان پاپاور تعریف شده و یک عنصر {{htmlelement("button")}} که به‌عنوان دکمهٔ کنترل نمایش پاپاور تعیین شده است:

```html
<button popovertarget="mypopover">Show the popover</button>
<div popover="auto" id="mypopover">I'm a Popover! I should animate.</div>
```

#### CSS

ما keyframe هایی تعریف کرده‌ایم که انیمیشن ورود و خروج موردنظر را مشخص می‌کنند و یک انیمیشن ورود فقط برای backdrop. توجه کنید که امکان انیمیت محو شدن backdrop وجود نداشت؛ چون وقتی پاپاور بسته می‌شود، backdrop بلافاصله از DOM حذف می‌شود و در نتیجه چیزی برای انیمیت باقی نمی‌ماند.

```css
html {
  font-family: "Helvetica", "Arial", sans-serif;
}

[popover] {
  font-size: 1.2rem;
  padding: 10px;
  animation: fade-out 0.7s ease-out;
}

[popover]:popover-open {
  animation: fade-in 0.7s ease-out;
}

[popover]:popover-open::backdrop {
  animation: backdrop-fade-in 0.7s ease-out forwards;
}

/* Animation keyframes */

@keyframes fade-in {
  0% {
    opacity: 0;
    transform: scaleX(0);
  }

  100% {
    opacity: 1;
    transform: scaleX(1);
  }
}

@keyframes fade-out {
  0% {
    opacity: 1;
    transform: scaleX(1);
    /* display needed on the closing animation to keep the popover
    visible until the animation ends */
    display: block;
  }

  100% {
    opacity: 0;
    transform: scaleX(0);
    /* display: none not required here because it is the default value
    for a closed popover, but including it so the behavior is clear */
    display: none;
  }
}

@keyframes backdrop-fade-in {
  0% {
    background-color: transparent;
  }

  100% {
    background-color: rgb(0 0 0 / 25%);
  }
}
```

#### نتیجه

کد به این شکل رندر می‌شود:

{{ EmbedLiveSample("A popover keyframe animation", "100%", "200") }}

## همچنین ببینید

- مجموعه‌ای از [نمونه‌های Popover API](https://mdn.github.io/dom-examples/popover-api/)