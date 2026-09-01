---
title: "عملیات کشیدن"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations"
---

---
title: Drag operations
slug: Web/API/HTML_Drag_and_Drop_API/Drag_operations
page-type: guide
---

{{DefaultAPISidebar("HTML Drag and Drop API")}}

محوریت API کشیدن و رها کردن (Drag and Drop) بر رویدادهای مختلف [کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#drag_events) است که به ترتیب مشخصی رخ می‌دهند و انتظار می‌رود به روش خاصی مدیریت شوند. این سند مراحل انجام یک عملیات کشیدن و رها کردن و وظایف برنامه در هر handler را شرح می‌دهد.

در سطح بالا، مراحل احتمالی یک عملیات کشیدن و رها کردن به شرح زیر است:

- کاربر [کشیدن را آغاز می‌کند](#starting_a_drag) روی یک گره مبدأ؛ رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} روی گره مبدأ شلیک می‌شود. در این رویداد، گره مبدأ بستر عملیات کشیدن را آماده می‌کند، از جمله داده‌های کشیدن، تصویر بازخورد، و اثرات رها کردن مجاز.
- کاربر [مورد را به اطراف می‌کشد](#dragging_over_elements_and_specifying_drop_targets): هر بار که یک عنصر جدید وارد می‌شود، رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} روی آن عنصر شلیک می‌شود، و رویداد {{domxref("HTMLElement/dragleave_event", "dragleave")}} روی عنصر قبلی شلیک می‌شود. هر چند صد میلی‌ثانیه، یک رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} روی عنصری که کشیدن در حال حاضر درون آن است شلیک می‌شود، و رویداد {{domxref("HTMLElement/drag_event", "drag")}} روی گره مبدأ شلیک می‌شود.
- کشیدن وارد یک هدف رها کردن معتبر می‌شود: هدف رها کردن رویداد `dragover` خود را لغو (cancel) می‌کند تا نشان دهد که یک هدف رها کردن معتبر است. نوعی [بازخورد رها کردن](#drop_feedback) اثر رها کردن مورد انتظار را به کاربر نشان می‌دهد.
- کاربر [رها کردن را انجام می‌دهد](#performing_a_drop): رویداد {{domxref("HTMLElement/drop_event", "drop")}} روی هدف رها کردن شلیک می‌شود. در این رویداد، گره هدف داده‌های کشیدن را می‌خواند.
- [عملیات کشیدن به پایان می‌رسد](#finishing_the_drag): رویداد {{domxref("HTMLElement/dragend_event", "dragend")}} روی گره مبدأ شلیک می‌شود. این رویداد صرف‌نظر از موفقیت یا عدم موفقیت رها کردن شلیک می‌شود.

## شروع کشیدن

کشیدن روی یک [مورد قابل کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#draggable_items) شروع می‌شود، که می‌تواند یک انتخاب، یک عنصر قابل کشیدن (شامل لینک‌ها، تصاویر، و هر عنصری با `draggable="true"`)، یک فایل از مرورگر فایل سیستم عامل، و غیره باشد. ابتدا، رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} روی _گره مبدأ_ شلیک می‌شود، که همان عنصر قابل کشیدن یا، برای انتخاب‌ها، گره متنی است که کشیدن از آن شروع شده است. اگر این رویداد لغو شود، عملیات کشیدن متوقف می‌شود. در غیر این صورت، رویداد {{domxref("Element/pointercancel_event", "pointercancel")}} نیز روی گره مبدأ شلیک می‌شود.

رویداد `dragstart` تنها زمانی است که می‌توانید {{domxref("DragEvent.dataTransfer", "dataTransfer")}} را تغییر دهید. برای یک عنصر قابل کشیدن سفارشی، تقریباً همیشه می‌خواهید داده‌های کشیدن را تغییر دهید، که به طور مفصل در [تغییر ذخیره‌گاه داده‌های کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store#modifying_the_drag_data_store) پوشش داده شده است. دو چیز دیگر وجود دارد که می‌توانید تغییر دهید: [تصویر بازخورد](#setting_the_drag_feedback_image) و [اثرات رها کردن مجاز](#drop_effects).

در این مثال، یک شنونده برای رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} با استفاده از متد `addEventListener()` اضافه می‌کنیم.

```html
<p draggable="true">این متن <strong>ممکن است</strong> کشیده شود.</p>
```

```js
const draggableElement = document.querySelector('p[draggable="true"]');
draggableElement.addEventListener("dragstart", (event) => {
  event.dataTransfer.setData("text/plain", "این متن ممکن است کشیده شود");
});
```

همچنین می‌توانید به یک ancestor بالاتر گوش دهید زیرا رویدادهای کشیدن مانند بسیاری از رویدادهای دیگر به سمت بالا حباب می‌شوند (bubble up). به همین دلیل، معمول است که target رویداد را نیز بررسی کنید، تا کشیدن یک انتخاب درون این عنصر باعث فعال شدن `setData` نشود (اگرچه انتخاب متن درون عنصر دشوار است، اما غیرممکن نیست):

```js
draggableElement.addEventListener("dragstart", (event) => {
  if (event.target === draggableElement) {
    event.dataTransfer.setData("text/plain", "این متن ممکن است کشیده شود");
  }
});
```

### تنظیم تصویر بازخورد کشیدن

هنگامی که یک کشیدن رخ می‌دهد، یک تصویر نیمه‌شفاف از گره مبدأ تولید می‌شود و در طول کشیدن دنبال pointer کاربر می‌رود. این تصویر به طور خودکار ایجاد می‌شود، بنابراین نیازی به ایجاد آن ندارید. با این حال، می‌توانید از {{domxref("DataTransfer.setDragImage","setDragImage()")}} برای مشخص کردن یک تصویر بازخورد سفارشی استفاده کنید.

```js
draggableElement.addEventListener("dragstart", (event) => {
  event.dataTransfer.setDragImage(image, xOffset, yOffset);
});
```

سه آرگومان لازم است. اولین آرگومان یک ارجاع به یک تصویر است. این ارجاع معمولاً به یک عنصر `<img>` است، اما می‌تواند به یک `<canvas>` یا هر عنصر دیگری نیز باشد. تصویر بازخورد از آنچه که تصویر روی صفحه نمایش داده می‌شود تولید می‌شود، اگرچه برای تصاویر، آنها در اندازه اصلی خود رسم می‌شوند. آرگومان دوم و سوم متد {{domxref("DataTransfer.setDragImage","setDragImage()")}} offsetهایی هستند که نشان می‌دهند تصویر نسبت به pointer ماوس در کجا ظاهر شود.

همچنین می‌توانید از تصاویر و canvasهایی که در سند نیستند استفاده کنید. این تکنیک زمانی مفید است که می‌خواهید با استفاده از عنصر canvas تصاویر کشیدن سفارشی رسم کنید، مانند مثال زیر:

```js
draggableElement.addEventListener("dragstart", (event) => {
  const canvas = document.createElement("canvas");
  canvas.width = canvas.height = 50;

  const ctx = canvas.getContext("2d");
  ctx.lineWidth = 4;
  ctx.moveTo(0, 0);
  ctx.lineTo(50, 50);
  ctx.moveTo(0, 50);
  ctx.lineTo(50, 0);
  ctx.stroke();

  event.dataTransfer.setDragImage(canvas, 25, 25);
});
```

در این مثال، یک canvas را به عنوان تصویر کشیدن قرار می‌دهیم. از آنجایی که canvas 50×50 پیکسل است، از offsetهای نصف این مقدار (`25`) استفاده می‌کنیم تا تصویر در مرکز pointer ماوس ظاهر شود.

## کشیدن روی عناصر و مشخص کردن اهداف رها کردن

در طول کل عملیات کشیدن، تمام رویدادهای ورودی دستگاه (مانند ماوس یا صفحه کلید) سرکوب می‌شوند. داده‌های کشیده شده می‌توانند روی عناصر مختلف در سند، یا حتی عناصر در سندهای دیگر حرکت کنند. هر بار که یک عنصر جدید وارد می‌شود، یک رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} روی آن عنصر شلیک می‌شود، و یک رویداد {{domxref("HTMLElement/dragleave_event", "dragleave")}} روی عنصر قبلی شلیک می‌شود.

> [!NOTE]
> `dragleave` همیشه _بعد از_ `dragenter` شلیک می‌شود، بنابراین از نظر مفهومی، بین این دو رویداد، هدف وارد یک عنصر جدید شده است اما هنوز از عنصر قبلی خارج نشده است.

هر چند صد میلی‌ثانیه، دو رویداد شلیک می‌شوند: یک رویداد {{domxref("HTMLElement/drag_event", "drag")}} در گره مبدأ، و یک رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} در عنصری که کشیدن در حال حاضر درون آن است. بیشتر نواحی یک صفحه وب یا برنامه مکان‌های معتبری برای رها کردن داده نیستند، بنابراین عناصر به طور پیش‌فرض هر رها کردنی را که روی آنها اتفاق بیفتد نادیده می‌گیرند. عنصر می‌تواند با لغو رویداد `dragover` خود را به عنوان یک هدف رها کردن معتبر معرفی کند. اگر عنصر یک فیلد متنی قابل ویرایش باشد، مانند {{HTMLElement("textarea")}} یا [`<input type="text">`](/en-US/docs/Web/HTML/Reference/Elements/input/text)، و ذخیره‌گاه داده حاوی یک مورد `text/plain` باشد، آنگاه عنصر به طور پیش‌فرض بدون لغو `dragover` یک هدف رها کردن معتبر است.

```html
<div id="drop-target">می‌توانید یک مورد قابل کشیدن را اینجا بکشید و رها کنید</div>
```

```js
const dropElement = document.getElementById("drop-target");

dropElement.addEventListener("dragover", (event) => {
  event.preventDefault();
});
```

> [!NOTE]
> مشخصات (spec) ایجاب می‌کند که رویداد `dragenter` نیز برای یک هدف رها کردن لغو شود، در غیر این صورت رویدادهای `dragover` یا `dragleave` حتی روی این عنصر شروع به شلیک نخواهند کرد. در عمل هیچ مرورگری این را پیاده‌سازی نمی‌کند، و "عنصر فعلی" هر بار که یک عنصر جدید وارد می‌شود تغییر می‌کند.

> [!NOTE]
> مشخصات ایجاب می‌کند که لغو رویداد `drag` باعث [متوقف شدن](#a_failed_drop) کشیدن شود. در عمل هیچ مرورگری این را پیاده‌سازی نمی‌کند. مثال زیر را ببینید:
>
> {{EmbedLiveSample("cancel_drag", "", 100)}}

```html hidden live-sample___cancel_drag
<p draggable="true" id="draggable">من را به مدت ۱ ثانیه بکشید!</p>
<p id="output"></p>
```

```js hidden live-sample___cancel_drag
const draggableElement = document.getElementById("draggable");
const output = document.getElementById("output");
let time = null;
draggableElement.addEventListener("dragstart", (event) => {
  time = Date.now();
  output.textContent = "";
});
draggableElement.addEventListener("drag", (event) => {
  if (time !== null && Date.now() - time > 1000) {
    event.preventDefault();
    output.textContent =
      "عملیات کشیدن لغو شد؛ اگر هنوز گره را می‌کشید، مرورگر شما از لغو برنامه‌ریزی شده کشیدن پشتیبانی نمی‌کند.";
    time = null;
  }
});
```

### اهداف رها کردن شرطی

معمولاً می‌خواهید هدف رها کردن فقط در شرایط خاصی رها کردن را بپذیرد (مثلاً فقط اگر یک لینک در حال کشیده شدن است). برای انجام این کار، یک شرط را بررسی کنید و فقط زمانی که شرط برآورده شد رویداد را لغو کنید. به عنوان مثال، می‌توانید بررسی کنید که داده‌های کشیده شده حاوی لینک هستند:

```js
dropElement.addEventListener("dragover", (event) => {
  const isLink = event.dataTransfer.types.includes("text/uri-list");
  if (isLink) {
    event.preventDefault();
  }
});
```

در این مثال، از متد `includes` برای بررسی اینکه آیا نوع [`text/uri-list`](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store#dragging_links) در لیست انواع وجود دارد استفاده می‌کنیم. اگر وجود داشته باشد، رویداد را لغو می‌کنیم تا رها کردن مجاز شود. اگر داده‌های کشیدن حاوی لینک نباشند، رویداد لغو نمی‌شود و رها کردن نمی‌تواند در آن مکان رخ دهد.

## بازخورد رها کردن

اکنون کاربر در حال کشیدن به یک هدف رها کردن معتبر است. چندین راه برای نشان دادن به کاربر وجود دارد که رها کردن در این مکان مجاز است و اگر رها کردن اتفاق بیفتد چه اتفاقی می‌افتد. معمولاً، pointer ماوس بسته به مقدار ویژگی {{domxref("DataTransfer.dropEffect", "dropEffect")}} به‌روز می‌شود. اگرچه ظاهر دقیق به پلتفرم کاربر بستگی دارد، معمولاً یک نماد علامت بعلاوه برای `copy` ظاهر می‌شود، و یک نماد "نمی‌توان اینجا رها کرد" زمانی که رها کردن مجاز نیست ظاهر می‌شود. این بازخورد pointer ماوس در بسیاری موارد کافی است.

### اثرات رها کردن

هنگام رها کردن، چندین عملیات ممکن است انجام شود:

- `copy`
  - : داده پس از رها کردن به طور همزمان در مکان مبدأ و هدف وجود خواهد داشت.
- `move`
  - : داده فقط در مکان هدف وجود خواهد داشت و از مکان مبدأ حذف می‌شود.
- `link`
  - : نوعی پیوند بین مکان مبدأ و رها کردن ایجاد می‌شود. تنها یک نمونه از داده در مکان مبدأ وجود دارد.
- `none`
  - : هیچ اتفاقی نمی‌افتد؛ رها کردن ناموفق بود.

با رویدادهای {{domxref("HTMLElement/dragenter_event", "dragenter")}} و {{domxref("HTMLElement/dragover_event", "dragover")}}، ویژگی {{domxref("DataTransfer.dropEffect","dropEffect")}} به اثری که کاربر درخواست می‌کند مقداردهی اولیه می‌شود. کاربر می‌تواند با فشار دادن کلیدهای modifier اثر مورد نظر را تغییر دهد. اگرچه کلیدهای دقیق بسته به پلتفرم متفاوت است، معمولاً از کلیدهای <kbd>Shift</kbd> و <kbd>Control</kbd> برای جابجایی بین کپی، انتقال و پیوند استفاده می‌شود. pointer ماوس تغییر می‌کند تا نشان دهد کدام عملیات مورد نظر است. به عنوان مثال، برای `copy`، مکان‌نما ممکن است با یک علامت بعلاوه در کنار آن ظاهر شود.

می‌توانید ویژگی {{domxref("DataTransfer.dropEffect","dropEffect")}} را در طول رویدادهای {{domxref("HTMLElement/dragenter_event", "dragenter")}} یا {{domxref("HTMLElement/dragover_event", "dragover")}} تغییر دهید، برای مثال اگر یک هدف رها کردن خاص فقط از عملیات خاصی پشتیبانی می‌کند. می‌توانید ویژگی {{domxref("DataTransfer.dropEffect","dropEffect")}} را تغییر دهید تا اثر کاربر را نادیده بگیرید و یک عملیات رها کردن خاص را اعمال کنید.

```js
target.addEventListener("dragover", (event) => {
  event.dataTransfer.dropEffect = "move";
});
```

در این مثال، `move` اثری است که انجام می‌شود.

می‌توانید از مقدار `none` برای نشان دادن اینکه هیچ رها کردنی در این مکان مجاز نیست استفاده کنید. معمولاً باید این کار را انجام دهید اگر عنصر به طور موقت رها کردن را نمی‌پذیرد. اگر قرار نیست یک هدف رها کردن باشد، فقط نباید رویداد را لغو کنید.

توجه داشته باشید که تنظیم `dropEffect` فقط اثر مورد نظر _در این لحظه خاص_ را نشان می‌دهد. یک ارسال `dragover` بعدی ممکن است آن را تغییر دهد. برای تداوم انتخاب، باید آن را در هر رویداد `dragover` تنظیم کنید. همچنین، این اثر فقط _اطلاع‌رسانی_ است، و اینکه چه اثری در نهایت پیاده‌سازی می‌شود به هر دو گره مبدأ و هدف بستگی دارد (مثلاً اگر گره مبدأ قابل تغییر نباشد، حتی اگر یک اثر "move" درخواست شود، ممکن است امکان‌پذیر نباشد).

برای هر دو حرکت کاربر و تنظیم برنامه‌ریزی شده `dropEffect`، به طور پیش‌فرض، هر سه اثر رها کردن در دسترس هستند. عنصر قابل کشیدن می‌تواند با تنظیم ویژگی {{domxref("DataTransfer.effectAllowed","effectAllowed")}} درون یک شنونده رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} خود را محدود کند که فقط اثرات خاصی را مجاز کند.

```js
draggableElement.addEventListener("dragstart", (event) => {
  event.dataTransfer.effectAllowed = "copyLink";
});
```

در این مثال، فقط عملیات کپی یا پیوند مجاز است، اما عملیات انتقال نه از طریق اسکریپت و نه از طریق حرکت‌های کاربر قابل انتخاب نیست.

مقادیر `effectAllowed` ترکیبی از `dropEffect` هستند:

| مقدار            | توضیحات                                                                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------ |
| `none`           | هیچ عملیاتی مجاز نیست                                                                                             |
| `copy`           | فقط `copy`                                                                                                        |
| `move`           | فقط `move`                                                                                                        |
| `link`           | فقط `link`                                                                                                        |
| `copyMove`       | فقط `copy` یا `move`                                                                                              |
| `copyLink`       | فقط `copy` یا `link`                                                                                              |
| `linkMove`       | فقط `link` یا `move`                                                                                              |
| `all`            | `copy`، `move`، یا `link`                                                                                         |
| `uninitialized`  | مقدار پیش‌فرض وقتی اثر تنظیم نشده است؛ معمولاً معادل `all` است، به جز اینکه `dropEffect` پیش‌فرض ممکن است همیشه `copy` نباشد. |

به طور پیش‌فرض، `dropEffect` بر اساس `effectAllowed` به ترتیب `copy`، `link`، `move` مقداردهی اولیه می‌شود و اولین موردی را که مجاز است انتخاب می‌کند. اثرات مجاز اما انتخاب نشده نیز ممکن است در صورت مناسب به عنوان پیش‌فرض انتخاب شوند. به عنوان مثال، در ویندوز، نگه داشتن کلید <kbd>Alt</kbd> باعث می‌شود `link` در اولویت استفاده شود. اگر `effectAllowed` برابر `uninitialized` باشد و عنصر کشیده شده یک لینک `<a>` باشد، `dropEffect` پیش‌فرض `link` است. اگر `effectAllowed` برابر `uninitialized` باشد و عنصر کشیده شده یک انتخاب از یک فیلد متنی قابل ویرایش باشد، `dropEffect` پیش‌فرض `move` است.

```html hidden live-sample___drop_effects
<div class="sources-container">
  اینها منابع با <code>allowedEffect</code> متفاوت هستند
  <div id="sources"></div>
</div>
<div class="targets-container">
  اینها اهداف با <code>dropEffect</code> متفاوت هستند
  <div id="targets"></div>
</div>
```

```css hidden live-sample___drop_effects
.sources-container,
.targets-container {
  width: calc(100% - 2rem);
  border: 2px dashed gray;
  padding: 0.5rem;
  margin: 1rem 0;
}

#sources,
#targets {
  display: grid;
  gap: 0.5rem;
  width: 100%;
}

#sources {
  grid-template-columns: 1fr 1fr 1fr;
}

#targets {
  grid-template-columns: 1fr 1fr;
}

#sources div,
#targets div {
  border: 2px solid black;
  flex: 1 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

#sources div {
  height: 50px;
}

#targets div {
  height: 75px;
}
```

```js hidden live-sample___drop_effects
for (const allowedEffect of [
  "none",
  "copy",
  "move",
  "link",
  "copyMove",
  "copyLink",
  "linkMove",
  "all",
  "uninitialized",
]) {
  const div = document.createElement("div");
  div.textContent = allowedEffect;
  div.draggable = true;
  div.addEventListener("dragstart", (event) => {
    event.dataTransfer.effectAllowed = allowedEffect;
  });
  document.getElementById("sources").appendChild(div);
}

for (const dropEffect of ["none", "copy", "move", "link"]) {
  const div = document.createElement("div");
  div.textContent = dropEffect;
  div.addEventListener("dragover", (event) => {
    event.preventDefault();
    event.dataTransfer.dropEffect = dropEffect;
  });
  document.getElementById("targets").appendChild(div);
}
```

{{EmbedLiveSample("drop_effects", "", 500)}}

### بازخورد رها کردن سفارشی

برای جلوه‌های بصری پیچیده‌تر، می‌توانید عملیات دیگری را در طول رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} انجام دهید، برای مثال با درج یک عنصر در مکان‌ی که رها کردن اتفاق می‌افتد. این می‌تواند یک نشانگر درج یا یک عنصر باشد که عنصر کشیده شده را در مکان جدید خود نشان می‌دهد. برای انجام این کار، می‌توانید یک عنصر [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img) ایجاد کنید و آن را در طول رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} در سند وارد کنید.

رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} روی عنصری که ماوس به آن اشاره می‌کند شلیک می‌شود. طبیعتاً، ممکن است نیاز داشته باشید نشانگر درج را درون handler رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} نیز جابجا کنید. می‌توانید از ویژگی‌های {{domxref("MouseEvent.clientX","clientX")}} و {{domxref("MouseEvent.clientY","clientY")}} رویداد مانند سایر رویدادهای ماوس برای تعیین مکان pointer ماوس استفاده کنید.

در نهایت، رویداد {{domxref("HTMLElement/dragleave_event", "dragleave")}} روی یک عنصر زمانی شلیک می‌شود که کشیدن از عنصر خارج می‌شود. این زمانی است که باید هر نشانگر درج یا برجسته‌سازی را حذف کنید. نیازی به لغو این رویداد نیست. رویداد {{domxref("HTMLElement/dragleave_event", "dragleave")}} همیشه شلیک می‌شود، حتی اگر کشیدن لغو شود، بنابراین می‌توانید همیشه مطمئن شوید که هر پاکسازی نقطه درج می‌تواند در طول این رویداد انجام شود.

برای یک مثال عملی از استفاده از این رویدادها، به [مثال تخته کانبان](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Kanban_board#inserting_at_a_particular_location) ما مراجعه کنید.

## انجام رها کردن

هنگامی که کاربر ماوس را رها می‌کند، عملیات کشیدن و رها کردن به پایان می‌رسد.

برای اینکه رها کردن _احتمالاً موفق_ باشد، رها کردن باید روی یک [هدف رها کردن معتبر](#dragging_over_elements_and_specifying_drop_targets) اتفاق بیفتد، و `dropEffect` در زمان رها کردن ماوس نباید `none` باشد. در غیر این صورت، عملیات رها کردن [ناموفق](#a_failed_drop) در نظر گرفته می‌شود.

اگر رها کردن احتمالاً موفق باشد، یک رویداد {{domxref("HTMLElement/drop_event", "drop")}} روی هدف رها کردن شلیک می‌شود. باید این رویداد را با استفاده از `preventDefault()` لغو کنید تا رها کردن واقعاً موفق در نظر گرفته شود. در غیر این صورت، رها کردن نیز در صورتی موفق در نظر گرفته می‌شود که رها کردن متن (داده حاوی یک مورد `text/plain`) در یک فیلد متنی قابل ویرایش باشد. در این حالت، متن در فیلد درج می‌شود (یا در موقعیت مکان‌نما یا در انتها، بسته به قراردادهای پلتفرم) و اگر `dropEffect` برابر `move` باشد در حالی که مبدأ یک انتخاب درون یک ناحیه قابل ویرایش است، مبدأ حذف می‌شود. در غیر این صورت، برای سایر داده‌های کشیدن و اهداف رها کردن، رها کردن ناموفق در نظر گرفته می‌شود.

در طول رویداد {{domxref("HTMLElement/drop_event", "drop")}}، باید داده‌های مورد نظر را از ذخیره‌گاه داده‌های کشیدن با استفاده از {{domxref("DataTransfer.getData()")}} بازیابی کنید و آن را در مکان رها کردن وارد کنید. می‌توانید از ویژگی {{domxref("DataTransfer.dropEffect","dropEffect")}} برای تعیین اینکه کدام عملیات کشیدن مورد نظر بود استفاده کنید. رویداد `drop` تنها زمانی است که می‌توانید ذخیره‌گاه داده‌های کشیدن را بخوانید، به غیر از `dragstart`.

```js
target.addEventListener("drop", (event) => {
  event.preventDefault();
  const data = event.dataTransfer.getData("text/plain");
  target.textContent = data;
});
```

در مثال اینجا، پس از بازیابی داده، رشته را به عنوان محتوای متنی هدف وارد می‌کنیم. این اثر درج متن کشیده شده در جایی که رها شده است را دارد، با فرض اینکه هدف رها کردن یک ناحیه متنی مانند یک عنصر `p` یا `div` باشد.

متد `getData()` اگر ذخیره‌گاه داده حاوی داده‌ای از نوع مشخص شده نباشد، یک رشته خالی برمی‌گرداند. اگر [اهداف رها کردن شرطی](#conditional_drop_targets) را پیاده‌سازی کرده باشید، این وضعیت نباید رخ دهد، زیرا هدف رها کردن فقط زمانی باید رها کردن را بپذیرد که داده مورد نظر وجود داشته باشد.

همچنین می‌توانید انواع دیگری از داده را بازیابی کنید. اگر داده یک لینک باشد، باید نوع [`text/uri-list`](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store#dragging_links) را داشته باشد. سپس می‌توانید یک لینک را در محتوا وارد کنید.

```js
target.addEventListener("drop", (event) => {
  event.preventDefault();
  const lines = event.dataTransfer.getData("text/uri-list").split("\r\n");
  lines
    .filter((line) => !line.startsWith("#"))
    .forEach((line) => {
      const link = document.createElement("a");
      link.href = line;
      link.textContent = line;
      target.appendChild(link);
    });
});
```

برای اطلاعات بیشتر در مورد نحوه خواندن داده‌های کشیدن، به [کار با ذخیره‌گاه داده‌های کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store#reading_the_drag_data_store) مراجعه کنید.

همچنین مسئولیت عناصر مبدأ و هدف است که برای پیاده‌سازی `dropEffect` همکاری کنند—مبدأ به رویداد `dragend` گوش می‌دهد و هدف به رویداد `drop` گوش می‌دهد. به عنوان مثال، اگر `dropEffect` برابر `move` باشد، یکی از این عناصر باید مورد کشیده شده را از مکان قدیمی خود حذف کند (معمولاً خود عنصر مبدأ، زیرا عنصر هدف لزوماً مبدأ را نمی‌شناسد یا بر آن کنترل ندارد).

<!-- TODO: default action of dropping files/links into browsers -->

## رها کردن ناموفق

عملیات کشیدن و رها کردن در صورتی ناموفق در نظر گرفته می‌شود که یکی از موارد زیر صادق باشد:

1. کاربر کلید <kbd>Escape</kbd> را فشار داد
2. رها کردن خارج از یک [هدف رها کردن معتبر](#dragging_over_elements_and_specifying_drop_targets) اتفاق افتاد
3. اثر رها کردن در زمان رها کردن ماوس `none` بود
4. رویداد `drop` لغو نشد و رها کردن متن (حاوی داده `text/plain`) در یک فیلد متنی قابل ویرایش نبود (به [انجام رها کردن](#performing_a_drop) مراجعه کنید)

برای موارد 1 و 3، اگر لغو شدن در حالی که روی یک هدف رها کردن معتبر معلق است اتفاق بیفتد، هدف رها کردن یک رویداد {{domxref("HTMLElement/dragleave_event", "dragleave")}} دریافت می‌کند، گویی که رها کردن دیگر روی آن اتفاق نمی‌افتد، تا بتواند هر [بازخورد رها کردن](#custom_drop_feedback) را پاک کند. در همه موارد، `dropEffect` برای رویدادهای بعدی روی `none` تنظیم می‌شود.

پس از آن، یک رویداد {{domxref("HTMLElement/dragend_event", "dragend")}} در گره مبدأ شلیک می‌شود. مرورگر ممکن است یک انیمیشن از بازگشت انتخاب کشیده شده به مبدأ عملیات کشیدن و رها کردن نمایش دهد.

## پایان کشیدن

پس از اتمام کشیدن، یک رویداد {{domxref("HTMLElement/dragend_event", "dragend")}} در مبدأ کشیدن (همان عنصری که رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} را دریافت کرد) شلیک می‌شود. این رویداد صرف‌نظر از موفقیت یا عدم موفقیت کشیدن شلیک می‌شود.

اگر ویژگی {{domxref("DataTransfer.dropEffect","dropEffect")}} در طول یک {{domxref("HTMLElement/dragend_event", "dragend")}} مقدار `none` داشته باشد، آنگاه کشیدن لغو شده است. در غیر این صورت، اثر مشخص می‌کند که کدام عملیات انجام شده است. مبدأ می‌تواند از این اطلاعات پس از یک عملیات `move` برای حذف مورد کشیده شده از مکان قدیمی استفاده کند.

یک رها کردن می‌تواند در همان پنجره یا در یک برنامه دیگر اتفاق بیفتد. رویداد {{domxref("HTMLElement/dragend_event", "dragend")}} همیشه صرف‌نظر از این شلیک می‌شود. ویژگی‌های {{domxref("MouseEvent.screenX","screenX")}} و {{domxref("MouseEvent.screenY","screenY")}} رویداد روی مختصات صفحه‌ای که رها کردن در آن اتفاق افتاد تنظیم می‌شوند.

پس از پایان انتشار رویداد {{domxref("HTMLElement/dragend_event", "dragend")}}، عملیات کشیدن و رها کردن کامل می‌شود.

## همچنین ببینید

- [HTML Drag and Drop API (بررسی کلی)](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [کار با ذخیره‌گاه داده‌های کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)