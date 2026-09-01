---
title: HTML Drag and Drop API
slug: Web/API/HTML_Drag_and_Drop_API
page-type: web-api-overview
spec-urls: https://html.spec.whatwg.org/multipage/dnd.html
---

{{DefaultAPISidebar("HTML Drag and Drop API")}}

رابط‌های **HTML Drag and Drop** به برنامه‌ها امکان می‌دهند از قابلیت کشیدن-و-رها کردن در مرورگرها استفاده کنند.

کاربر می‌تواند عناصر _کشیدنی_ را با ماوس انتخاب کند، آن‌ها را به یک عنصر _رهاکردنی_ بکشد، و با رها کردن دکمه ماوس رها کند. یک نمایش نیمه‌شفاف از عناصر _کشیدنی_ در طول عملیات کشیدن، نشانگر را دنبال می‌کند.

می‌توانید تعیین کنید کدام عناصر می‌توانند _کشیدنی_ شوند، نوع بازخوردی که عناصر _کشیدنی_ تولید می‌کنند، و عناصر _رهاکردنی_ را سفارشی کنید.

این نمای کلی از HTML Drag and Drop شامل توضیحی از رابط‌ها، مراحل اولیه برای افزودن پشتیبانی کشیدن-و-رها کردن به یک برنامه، و خلاصه‌ای از قابلیت تعامل‌پذیری رابط‌ها است.

## مفاهیم و کاربرد

در ظاهر، Drag and Drop در واقع سه مورد استفاده مجزا دارد: [کشیدن عناصر درون یک صفحه](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Kanban_board)، کشیدن داده به بیرون از صفحه، و [کشیدن داده به درون صفحه](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/File_drag_and_drop). هرکدام نیازمندی‌ها و پیاده‌سازی‌های کمی متفاوت دارند. با این حال، API Drag and Drop یک مدل یکپارچه برای تفکر درباره همه این تعاملات فراهم می‌کند.

در هسته خود، یک عملیات کشیدن شامل سه چیز است:

- [موردی که کشیده می‌شود](#draggable_items)
- [داده‌های زمینه‌ای که منتقل می‌شوند](#drag_data_store)
- [هدف رها کردن](#drop_target)

لزوماً درست نیست که هر سه تحت کنترل شما هستند یا باید خودتان آن‌ها را تعریف کنید:

- هنگام کشیدن داده خارجی به درون صفحه، مورد کشیدنی برای تعریف وجود ندارد (مثلاً می‌تواند یک فایل در کاوشگر فایل سیستم عامل باشد).
- هنگام کشیدن عناصر درون یک صفحه، اغلب نیازی به تعریف هیچ داده منتقل‌شده‌ای ندارید؛ فقط عنصر کشیده‌شده را دستکاری می‌کنید.
- هنگام کشیدن به بیرون از صفحه، هدف رها کردنی برای تعریف وجود ندارد.

خواهیم دید که چگونه هر یک می‌تواند تعریف و استفاده شود.

### رویدادهای کشیدن

HTML drag-and-drop از [مدل رویداد DOM](/en-US/docs/Web/API/Event) و _[رویدادهای کشیدن](/en-US/docs/Web/API/DragEvent)_ که از [رویدادهای ماوس](/en-US/docs/Web/API/MouseEvent) به ارث برده‌اند استفاده می‌کند. در طول عملیات کشیدن، چندین نوع رویداد شلیک می‌شود، و برخی رویدادها ممکن است بارها شلیک شوند، مانند رویدادهای {{domxref('HTMLElement/drag_event', 'drag')}} و {{domxref('HTMLElement/dragover_event', 'dragover')}}.

| رویداد                                                   | زمان شلیک                                                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| {{domxref('HTMLElement/dragstart_event', 'dragstart')}} | ...مورد [کشیدنی](#draggable_items) شروع به کشیده شدن می‌کند.                                     |
| {{domxref('HTMLElement/drag_event', 'drag')}}           | ...مورد کشیدنی در حال کشیده شدن است، هر چند صد میلی‌ثانیه.                                        |
| {{domxref('HTMLElement/dragenter_event', 'dragenter')}} | ...عنصر دارای یک مورد کشیدنی است که وارد آن می‌شود.                                               |
| {{domxref('HTMLElement/dragleave_event', 'dragleave')}} | ...عنصر دارای یک مورد کشیدنی است که از آن خارج می‌شود.                                           |
| {{domxref('HTMLElement/dragover_event', 'dragover')}}   | ...عنصر دارای یک مورد کشیدنی است که روی آن کشیده می‌شود، هر چند صد میلی‌ثانیه.                   |
| {{domxref('HTMLElement/drop_event', 'drop')}}           | ...عنصر یک [هدف رها کردن](#drop_target) است و مورد کشیدنی روی آن رها می‌شود.                      |
| {{domxref('HTMLElement/dragend_event', 'dragend')}}     | ...مورد کشیدنی از کشیده شدن بازمی‌ایستد.                                                          |

> [!NOTE]
> رویدادهای `dragstart`، `drag` و `dragend` روی مورد کشیده‌شده شلیک می‌شوند، و بنابراین هنگام کشیدن یک فایل از سیستم‌عامل به داخل مرورگر نمی‌توانند شلیک شوند. به طور مشابه، رویدادهای `dragenter`، `dragleave`، `dragover` و `drop` روی عناصری که اهداف رها کردن بالقوه هستند شلیک می‌شوند، و بنابراین هنگام کشیدن یک مورد به بیرون از مرورگر نمی‌توانند شلیک شوند.

برای اطلاعات بیشتر، [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations) را ببینید.

### موارد کشیدنی

در HTML، تصاویر، پیوندها و انتخاب‌ها به طور پیش‌فرض کشیدنی هستند. برای کشیدنی کردن یک عنصر دلخواه، ویژگی [`draggable`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable) را به مقدار `"true"` تنظیم کنید.

```html live-sample___draggable_element live-sample___drop_target
<p id="p1" draggable="true">This element is draggable.</p>
```

در این مرحله، عنصر از قبل ظاهر کشیدن را دارد، اگرچه هنوز رفتاری برای آن تعریف نشده است:

{{EmbedLiveSample("draggable_element", "", 100)}}

برای تصاویر و پیوندها، `draggable` به طور پیش‌فرض `true` است، بنابراین فقط آن را روی `false` تنظیم می‌کنید تا کشیدن این عناصر غیرفعال شود. برای عناصر غیرکشیدنی، ژست «کشیدن» معمولاً در عوض متن را انتخاب می‌کند.

> [!NOTE]
> وقتی یک عنصر کشیدنی می‌شود، متن یا عناصر دیگر درون آن دیگر نمی‌توانند به روش معمول با کلیک و کشیدن ماوس انتخاب شوند. در عوض، کاربر باید کلید <kbd>Alt</kbd> را نگه دارد تا متن را با ماوس انتخاب کند، یا از صفحه‌کلید استفاده کند.

یک انتخاب نیز کشیدنی است. در این حالت، _گره مبدأ_، یا گره‌ای که رویدادهای مختلفی مانند `dragstart` و `dragend` روی آن شلیک می‌شوند، گره متنی است که کشیدن از آن شروع شده است. انتخاب می‌تواند به طور جزئی یا کامل شامل چندین گره، شامل گره‌های متنی و گره‌های عنصر باشد، که همه به طور همزمان کشیده شده در نظر گرفته می‌شوند.

همانطور که پیشتر ذکر شد، مورد کشیده‌شده می‌تواند چیزی باشد که در یک صفحه وب نیست - مثلاً یک فایل در کاوشگر فایل سیستم عامل. با این حال، فقط موارد موجود در صفحه وب می‌توانند باعث شلیک رویدادهای {{domxref('HTMLElement/dragstart_event', 'dragstart')}} و {{domxref('HTMLElement/dragend_event', 'dragend')}} شوند.

برای اطلاعات بیشتر، [راهنمای عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations) را ببینید.

### ذخیره‌گاه داده کشیدن

نمی‌توانید اشیاء جاوااسکریپت را مستقیماً به صفحات وب دلخواه منتقل کنید، و قطعاً نه به برنامه‌های خارجی، بنابراین برای انتقال داده به درون و بیرون از صفحه وب، داده باید به یک رشته (یا به عنوان یک {{domxref("File")}}) سریالایز شود. در کشیدن-و-رها کردن، این رشته در یک شیء {{domxref("DataTransferItem")}} محصور می‌شود، که همچنین یک `type` خاص - معمولاً یک نوع MIME مانند `text/html` - را تعریف می‌کند که نحوه تفسیر رشته را مشخص می‌کند.

هر عملیات کشیدن-و-رها کردن دارای یک _ذخیره‌گاه داده کشیدن_ مرتبط است، که یک شیء {{domxref("DataTransfer")}} است که از طریق ویژگی {{domxref("DragEvent.dataTransfer","dataTransfer")}} رویداد {{domxref("DragEvent")}} قابل دسترسی است. برای موارد پیش‌فرض کشیدنی مانند تصاویر، پیوندها و انتخاب‌ها، داده کشیدن از قبل توسط مرورگر تعریف شده است؛ برای عناصر کشیدنی سفارشی که با استفاده از ویژگی `draggable` تعریف می‌شوند، باید خودتان داده کشیدن را تعریف کنید. تنها زمانی که می‌توانید تغییری در ذخیره‌گاه داده ایجاد کنید در درون کنترل‌کننده {{domxref("HTMLElement/dragstart_event", "dragstart")}} است - برای `dataTransfer` هر رویداد کشیدن دیگر، ذخیره‌گاه داده غیرقابل تغییر است.

از متد {{domxref("DataTransfer.setData", "setData()")}} می‌توان برای افزودن یک مورد به داده کشیدن استفاده کرد، همانطور که در مثال زیر نشان داده شده است.

```js live-sample___drop_target
function dragstartHandler(ev) {
  // Add different types of drag data
  ev.dataTransfer.setData("text/plain", ev.target.innerText);
  ev.dataTransfer.setData("text/html", ev.target.outerHTML);
  ev.dataTransfer.setData(
    "text/uri-list",
    ev.target.ownerDocument.location.href,
  );
}

const p1 = document.getElementById("p1");
p1.addEventListener("dragstart", dragstartHandler);
```

علاوه بر این، تنها زمانی که می‌توانید از ذخیره‌گاه داده _خواندن_ کنید، به جز رویداد `dragstart`، در طول رویداد `drop` است (که به هدف رها کردن امکان بازیابی داده را می‌دهد). برای همه رویدادهای دیگر، ذخیره‌گاه داده قابل دسترسی نیست.

برای اطلاعات بیشتر، [کار با ذخیره‌گاه داده کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store) را بخوانید.

### هدف رها کردن

_هدف رها کردن_ عنصری است که کاربر می‌تواند یک مورد کشیده‌شده را روی آن رها کند. به طور پیش‌فرض، بیشتر عناصر اهداف رها کردن نیستند، و اگر کشیدن را رها کنید، یک انیمیشن «بازگشت» نمایش داده می‌شود که نشان می‌دهد کشیدن-و-رها کردن ناموفق بوده است. هر عنصری می‌تواند با لغو رویداد {{domxref("HTMLElement.dragover_event","dragover")}} که روی آن شلیک می‌شود با استفاده از `preventDefault()` به یک هدف رها کردن تبدیل شود.

رویداد {{domxref("HTMLElement/drop_event", "drop")}} فقط روی اهداف رها کردن شلیک می‌شود، و این تنها زمانی است که می‌توانید ذخیره‌گاه داده کشیدن را بخوانید.

مثال زیر یک هدف رها کردن معتبر حداقلی را نشان می‌دهد، و همچنین کد مثال‌های قبلی را ترکیب می‌کند.

```html live-sample___drop_target
<p id="target">Drop Zone</p>
```

```js live-sample___drop_target
const target = document.getElementById("target");

// Cancel dragover so that drop can fire
target.addEventListener("dragover", (ev) => {
  ev.preventDefault();
});
target.addEventListener("drop", (ev) => {
  ev.preventDefault();
  const data = ev.dataTransfer.getData("text/plain");
  ev.target.append(data);
});
```

{{EmbedLiveSample("drop_target", "", 300)}}

برای اطلاعات بیشتر، [مشخص کردن اهداف رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations#dragging_over_elements_and_specifying_drop_targets) را ببینید.

## راهنماها

- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
  - : مراحلی را که در طول یک عملیات کشیدن-و-رها کردن رخ می‌دهد و آنچه برنامه باید در هر کنترل‌کننده انجام دهد را توصیف می‌کند.
- [کار با ذخیره‌گاه داده کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)
  - : نحوه خواندن و نوشتن در ذخیره‌گاه داده کشیدن را در طول یک عملیات کشیدن-و-رها کردن توصیف می‌کند.
- [کشیدن-و-رها کردن فایل](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/File_drag_and_drop)
  - : یک راهنمای عملی برای پیاده‌سازی یک رابط پایه که رها کردن فایل را می‌پذیرد.
- [تخته کانبان با کشیدن-و-رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Kanban_board)
  - : یک راهنمای عملی برای پیاده‌سازی یک تخته کانبان که شامل کشیدن و رها کردن عناصر درون یک صفحه وب است.

## رابط‌ها

- {{domxref("DragEvent")}}
  - : شیء رویدادی که به کنترل‌کننده‌های رویداد کشیدن ارسال می‌شود.
- {{domxref("DataTransfer")}}
  - : هر داده منتقل‌شده بین زمینه‌ها را نگه می‌دارد، شامل موارد متنی و موارد فایل. در ابتدا برای کشیدن-و-رها کردن طراحی شده بود، اکنون در زمینه‌های دیگر مانند [API کلیپ‌بورد](/en-US/docs/Web/API/Clipboard_API) نیز استفاده می‌شود.
- {{domxref("DataTransferItem")}}
  - : نماینده یک مورد در ذخیره‌گاه داده کشیدن است، که می‌تواند یک مورد متنی یا یک مورد فایل باشد.
- {{domxref("DataTransferItemList")}}
  - : نماینده فهرست اشیاء {{domxref("DataTransferItem")}} در ذخیره‌گاه داده کشیدن است.

## مثال‌ها

- [کپی و جابجایی عناصر با رابط `DataTransfer`](https://mdn.github.io/dom-examples/drag-and-drop/copy-move-DataTransfer.html)
- [کپی و جابجایی عناصر با رابط `DataTransferListItem`](https://mdn.github.io/dom-examples/drag-and-drop/copy-move-DataTransferItemList.html)

صفحات مرجع هر رابط نیز مثال‌های جداگانه دارند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه داده کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)
- [استاندارد زنده HTML: کشیدن و رها کردن](https://html.spec.whatwg.org/multipage/interaction.html#dnd)
- [داده‌های قابلیت تعامل‌پذیری Drag and Drop از CanIUse](https://caniuse.com/#search=draganddrop)