---
title: CloseWatcher
---

{{APIRef("HTML DOM")}}

رابط کاربری `CloseWatcher` به یک کامپوننت UI سفارشی که دارای معنای باز و بسته شدن است، امکان میدهد تا به اقدامات بستنِ مخصوص دستگاه، دقیقاً به همان روشی که کامپوننتهای داخلی پاسخ میدهند، واکنش نشان دهد.

{{InheritanceDiagram}}

رابط `CloseWatcher` از {{domxref("EventTarget")}} به ارث میبرد.

## سازنده

- {{domxref("CloseWatcher.CloseWatcher", "CloseWatcher()")}}
  - : یک نمونهی جدید از `CloseWatcher` میسازد.

## روشهای نمونه

_این رابط همچنین روشهای والد خود، {{domxref("EventTarget")}} را به ارث میبرد._

- {{domxref("CloseWatcher.requestClose()")}}
  - : یک رویداد `cancel` را فعال میکند و اگر آن رویداد با {{domxref("Event.preventDefault()")}} لغو نشود، به راهاندازی رویداد `close` ادامه میدهد و در نهایت watcher را به همان صورت که گویی `destroy()` فراخوانی شده است، غیرفعال میکند.
- {{domxref("CloseWatcher.close()")}}
  - : بلافاصله رویداد `close` را فعال میکند، بدون اینکه ابتدا `cancel` را فعال کند، و watcher را به همان صورت که گویی `destroy()` فراخوانی شده است، غیرفعال میکند.
- {{domxref("CloseWatcher.destroy()")}}
  - : watcher را غیرفعال میکند تا دیگر رویدادهای `close` را دریافت نکند.

## رویدادها

- {{domxref("CloseWatcher.cancel_event", "cancel")}}
  - : رویدادی که قبل از رویداد `close` فعال میشود، به طوری که میتوان از فعال شدن `close` جلوگیری کرد.
- {{domxref("CloseWatcher.close_event", "close")}}
  - : رویدادی که هنگام دریافت درخواست بستن فعال میشود.

## توضیحات

برخی از کامپوننتهای UI «رفتار بستن» دارند، به این معنی که کامپوننت ظاهر میشود و کاربر میتواند پس از اتمام کار با آن، آن را ببندد. به عنوان مثال: نوارهای کناری، پنجرههای بازشو (popup)، دیالوگها یا اعلانها.

کاربران معمولاً انتظار دارند بتوانند از یک سازوکار خاص برای بستن این عناصر استفاده کنند و این سازوکار معمولاً مخصوص دستگاه است. به عنوان مثال، در دستگاهی با صفحهکلید، ممکن است کلید <kbd>Esc</kbd> باشد، اما اندروید ممکن است از دکمهی بازگشت استفاده کند. برای کامپوننتهای داخلی، مانند [popover](/en-US/docs/Web/API/Popover_API) یا عناصر {{htmlelement("dialog")}}، مرورگر این تفاوتها را مدیریت میکند و هنگام انجام عمل بستن مناسب برای دستگاه، عنصر را میبندد. با این حال، زمانی که یک توسعهدهندهی وب کامپوننت UI قابل بستن خودش را پیادهسازی میکند (مثلاً یک نوار کناری)، پیادهسازی این رفتار بستن مخصوص دستگاه دشوار است.

رابط `CloseWatcher` این مشکل را با ارائهی یک رویداد `cancel` و به دنبال آن یک رویداد `close`، زمانی که کاربر عمل بستن مخصوص دستگاه را انجام میدهد، حل میکند.
برنامههای وب میتوانند از کنترلکنندهی `onclose` برای بستن عنصر UI در پاسخ به رویداد مخصوص دستگاه استفاده کنند.
آنها همچنین میتوانند این رویدادها را در پاسخ به سازوکار عادی بستن عنصر UI فعال کنند و سپس مدیریت مشترک رویداد `close` را هم برای عمل بستنِ مبتنی بر برنامه و هم برای عمل بستنِ مخصوص دستگاه پیادهسازی کنند.
هنگامی که کنترلکنندهی رویداد `onclose` کامل شد، `CloseWatcher` از بین میرود و رویدادها دیگر فعال نخواهند شد.

در برخی برنامهها، عنصر UI فقط زمانی مجاز به بستن است که در حالت خاصی باشد؛ به عنوان مثال، زمانی که اطلاعات لازم پر شده باشد.
برای رسیدگی به این موارد، برنامهها میتوانند با پیادهسازی یک کنترلکننده برای رویداد `cancel` که در صورت آماده نبودن عنصر UI برای بستن، {{domxref("Event.preventDefault()")}} را فراخوانی میکند، از انتشار رویداد `close` جلوگیری کنند.

میتوانید نمونههای `CloseWatcher` را بدون [فعالسازی کاربر](/en-US/docs/Web/Security/Defenses/User_activation) ایجاد کنید، و این میتواند برای پیادهسازی مواردی مانند دیالوگهای تایم اوت عدم فعالیت مفید باشد. با این حال، اگر بیش از یک `CloseWatcher` بدون فعالسازی کاربر ایجاد کنید، watcherها گروهبندی میشوند، بنابراین یک درخواست بستنِ واحد، هر دوی آنها را میبندد.
علاوه بر این، اولین watcher بستن لزوماً نباید یک شیء `CloseWatcher` باشد: میتواند یک عنصر دیالوگ مودال باشد، یا یک popover که توسط عنصری با ویژگی popover تولید شده است.

## مثالها

### پردازش درخواستهای بستن

در این مثال، شما یک کامپوننت UI اختصاصی خودتان (یک انتخابگر) دارید و میخواهید هم از روش بستن پیشفرض پلتفرم (مثلاً کلید <kbd>Esc</kbd>) و هم از روش بستن سفارشی خودتان (دکمهی بستن) پشتیبانی کنید.

شما یک `CloseWatcher` برای مدیریت همهی رویدادهای `close` ایجاد میکنید.

کنترلکنندهی `onclick` کامپوننت UI شما میتواند `requestClose` را فراخوانی کند تا درخواست بستن را انجام دهد و درخواست بستن شما را از طریق همان کنترلکنندهی `onclose` که روش بستن پلتفرم استفاده میکند، هدایت کند.

```js
const watcher = new CloseWatcher();
const picker = setUpAndShowPickerDOMElement();
let chosenValue = null;

watcher.onclose = () => {
  chosenValue = picker.querySelector("input").value;
  picker.remove();
};

picker.querySelector(".close-button").onclick = () => watcher.requestClose();
```

### بستن یک نوار کناری با استفاده از درخواست بستن پلتفرم

در این مثال، یک کامپوننت نوار کناری داریم که با انتخاب دکمهی «باز کردن» نمایش داده میشود و با استفاده از دکمهی «بستن» یا سازوکارهای بومی پلتفرم پنهان میشود.
برای جالبتر کردن آن، این یک مثال زنده است!

همچنین توجه داشته باشید که مثال کمی مصنوعی است، زیرا معمولاً از یک دکمهی تغییر وضعیت برای تغییر حالت نوار کناری استفاده میکنیم.
مطمئناً میتوانیم این کار را انجام دهیم، اما استفاده از دکمههای جداگانهی «باز کردن» و «بستن» نمایش این ویژگی را آسانتر میکند.

#### HTML

HTML عناصر {{htmlelement("button")}} «باز کردن» و «بستن»، همراه با عناصر {{htmlelement("div")}} برای محتوای اصلی و نوار کناری را تعریف میکند.
از CSS برای متحرک سازی نمایش عنصر نوار کناری هنگام اضافه یا حذف شدن کلاس `open` از عناصر نوار کناری و محتوا استفاده میشود (این CSS پنهان است زیرا به مثال مربوط نمیشود).

```html
<button id="sidebar-open" type="button">Open</button>
<button id="sidebar-close" type="button">Close</button>
<div class="sidebar">Sidebar</div>
<div class="main-content">Main content</div>
```

```css hidden
.sidebar {
  position: fixed;
  top: 20px;
  left: -300px;
  right: auto;
  bottom: 0;
  width: 300px; /* Adjust the width as needed */
  background-color: lightblue;
}

.main-content {
  position: fixed;
  top: 20px;
  left: 0;
  right: 0;
  bottom: 0;
  width: auto; /* Adjust the width as needed */
  background-color: green;
  margin-left: 0px; /* Adjust for the sidebar width */
}

.sidebar.open {
  left: 0; /* Slide the sidebar to the right when open */
  transition: left 0.3s ease-in-out; /* Add a smooth transition effect */
}

.main-content.open {
  margin-left: 300px; /* Adjust for the sidebar width */
  transition: margin-left 0.3s ease-in-out;
  background-color: green;
}
```

#### جاواسکریپت

کد ابتدا متغیرهایی برای دکمهها و عناصر `<div>` تعریفشده در HTML میگیرد.
همچنین تابع `closeSidebar()` را تعریف میکند که هنگام بستن نوار کناری فراخوانی میشود تا کلاس `open` را از عناصر `<div>` حذف کند، و یک شنوندهی رویداد `click` اضافه میکند که با کلیک روی دکمهی «باز کردن»، متد `openSidebar()` را فراخوانی میکند.

```js
const sidebar = document.querySelector(".sidebar");
const mainContent = document.querySelector(".main-content");
const sidebarOpen = document.getElementById("sidebar-open");
const sidebarClose = document.getElementById("sidebar-close");

function closeSidebar() {
  sidebar.classList.remove("open");
  mainContent.classList.remove("open");
}

sidebarOpen.addEventListener("click", openSidebar);
```

پیادهسازی `openSidebar()` در زیر آورده شده است.
متد ابتدا بررسی میکند که آیا نوار کناری از قبل باز است یا خیر، و اگر نبود، کلاس `open` را به عناصر اضافه میکند تا نوار کناری نمایش داده شود.

سپس یک `CloseWatcher` جدید ایجاد میکنیم و یک شنونده اضافه میکنیم که اگر دکمهی «بستن» کلیک شود، {{domxref("CloseWatcher.close()", "close()")}} را روی آن فراخوانی کند.
این تضمین میکند که رویداد `close` چه زمانی که روشهای بستن بومی پلتفرم استفاده میشوند و چه زمانی که دکمهی «بستن» استفاده میشود، فراخوانی شود.
پیادهسازی کنترلکنندهی رویداد `onclose()` به سادگی نوار کناری را میبندد و `CloseWatcher` سپس به طور خودکار از بین میرود.

```js
function openSidebar() {
  if (!sidebar.classList.contains("open")) {
    sidebar.classList.add("open");
    mainContent.classList.add("open");

    // Add new CloseWatcher
    const watcher = new CloseWatcher();

    sidebarClose.addEventListener("click", () => watcher.close());

    // Handle close event, invoked by platform mechanisms or "Close" button
    watcher.onclose = () => {
      closeSidebar();
    };
  }
}
```

توجه کنید که ما تصمیم گرفتیم به جای {{domxref("CloseWatcher.requestClose()")}} متد `close()` را روی watcher فراخوانی کنیم، زیرا نیازی به انتشار رویداد `cancel` نداریم (اگر دلیلی برای جلوگیری از بسته شدن زودهنگام نوار کناری وجود داشت، از `requestClose()` و کنترلکنندهی رویداد `cancel` استفاده میکردیم).

#### نتیجه

دکمهی «باز کردن» را برای باز کردن نوار کناری انتخاب کنید. باید بتوانید نوار کناری را با استفاده از دکمهی «بستن» یا روش معمول پلتفرم، مانند کلید <kbd>Esc</kbd> در ویندوز، ببندید.

{{ EmbedLiveSample("Closing a sidebar using a platform close request", "100%", "200") }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("HTMLDialogElement.close_event", "close")}} در {{domxref("HTMLDialogElement")}}