---
title: Kanban board with drag and drop
slug: Web/API/HTML_Drag_and_Drop_API/Kanban_board
page-type: guide
---

{{DefaultAPISidebar("HTML Drag and Drop API")}}

همان‌طور که در [صفحه اصلی](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#concepts_and_usage) اشاره شده است، API کشیدن و رها کردن (Drag and Drop) سه مورد استفاده را همزمان مدل‌سازی می‌کند: کشیدن عناصر درون یک صفحه، کشیدن داده‌ها به بیرون از صفحه، و کشیدن داده‌ها به داخل صفحه. این آموزش مورد استفاده اول را نشان می‌دهد: کشیدن عناصر درون یک صفحه. ما یک برنامه کانبان (Kanban) مشابه قابلیت‌های ارائه‌شده توسط [پروژه‌های گیت‌هاب](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects) یا [Trello](https://trello.com/) پیاده‌سازی خواهیم کرد.

## چیدمان پایه صفحه

از آنجایی که تمرکز اصلی ما بر روی کشیدن و مرتب‌سازی مجدد است، برخی جنبه‌های پویای یک تخته کانبان واقعی مانند افزودن و حذف وظایف را حذف می‌کنیم. در عوض، تمام ستون‌ها و وظایف ما به صورت ثابت در HTML تعریف شده‌اند.

```html live-sample___kanban
<div class="container">
  <div class="task-column">
    <h2>To Do</h2>
    <ul class="tasks">
      <li class="task" draggable="true">Find out where Soul Stone is</li>
    </ul>
  </div>
  <div class="task-column">
    <h2>In Progress</h2>
    <ul class="tasks">
      <li class="task" draggable="true">Collect Time Stone from Dr. Strange</li>
      <li class="task" draggable="true">Collect Mind Stone from Vision</li>
      <li class="task" draggable="true">
        Collect Reality Stone from the Collector
      </li>
    </ul>
  </div>
  <div class="task-column">
    <h2>Done</h2>
    <ul class="tasks">
      <li class="task" draggable="true">Collect Power Stone from Xandar</li>
      <li class="task" draggable="true">Collect Space Stone from Asgard</li>
    </ul>
  </div>
</div>
```

```css live-sample___kanban
body {
  font-family: "Arial", sans-serif;
}

.container {
  display: flex;
  gap: 0.5rem;
}

.task-column {
  border: 1px solid #cccccc;
  border-radius: 5px;
  margin: 10px;
  padding: 10px;
  flex: 1;
}

.tasks {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  list-style: none;
  padding: 0;
}

.task-column h2 {
  text-align: center;
}

.task {
  background-color: #f9f9f9;
  border: 1px solid #eeeeee;
  border-radius: 3px;
  padding: 8px;
  cursor: grab;
}

.task:active {
  cursor: grabbing;
}

@media (width < 600px) {
  .container {
    flex-direction: column;
  }
}
```

این ساختار پایه و استایل‌های برنامه ما را تعریف می‌کند. هر وظیفه [قابل کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#draggable_items) شده است، اما هنوز هنگام کشیدن کاری انجام نمی‌دهند.

## تعریف اهداف رها کردن

ما می‌خواهیم ستون‌های وظایف را به [اهداف رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#drop_target) معتبر برای وظایف کشیده‌شده تبدیل کنیم. به عنوان پایه، باید به رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} گوش دهیم و آن را لغو کنیم. اما دقت می‌کنیم که رویداد را فقط در صورتی لغو کنیم که رویداد کشیدن در حال کشیدن یک وظیفه باشد – اگر بخواهیم چیز دیگری را رها کنیم، ستون نباید هدف رها کردن باشد.

ابتدا همه ستون‌ها را در یک متغیر سراسری ذخیره می‌کنیم.

```js live-sample___kanban
const columns = document.querySelectorAll(".task-column");
```

سپس، یک کنترل‌کننده رویداد `dragover` برای هر ستون تعریف می‌کنیم – این کنترل‌کننده بعداً گسترش خواهد یافت.

```js
columns.forEach((column) => {
  column.addEventListener("dragover", (event) => {
    // Test a custom type we will set later
    if (event.dataTransfer.types.includes("task")) {
      event.preventDefault();
    }
  });
});
```

اکنون، هنگامی که یک وظیفه روی یک ستون کشیده می‌شود، ممکن است یک [اثر مکان‌نما](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations#drop_effects) مانند علامت بعلاوه مشاهده کنید که نشان‌دهنده کپی شدن وظیفه هنگام رها کردن است، زیرا کپی کردن اقدام پیش‌فرض است. بعداً این نشانگر را تغییر می‌دهیم زیرا وظیفه در واقع جابه‌جا می‌شود.

## جابه‌جایی عناصر

اکنون عملکرد اصلی را پیاده‌سازی می‌کنیم: قابلیت جابه‌جایی وظایف بین ستون‌ها. این کار شامل دو مرحله است: افزودن عنصر کشیده‌شده به ستون مقصد و حذف آن از ستون مبدأ.

عنصر کشیده‌شده و ستون مبدأ را به این ترتیب ردیابی می‌کنیم: در `dragstart`، وظیفه کشیده‌شده را با یک `id` علامت‌گذاری می‌کنیم. سپس در `drop`، می‌توانیم از این ID برای شناسایی وظیفه و حذف آن از ستون مبدأ استفاده کنیم. در نهایت فراموش نمی‌کنیم که ID را در `dragend` حذف کنیم تا در کشیدن بعدی IDهای تکراری ایجاد نشوند.

```js live-sample___kanban
const tasks = document.querySelectorAll(".task");

tasks.forEach((task) => {
  task.addEventListener("dragstart", (event) => {
    task.id = "dragged-task";
    event.dataTransfer.effectAllowed = "move";
    // Custom type to identify a task drag
    event.dataTransfer.setData("task", "");
  });

  task.addEventListener("dragend", (event) => {
    task.removeAttribute("id");
  });
});
```

گزینه‌های دیگری نیز وجود دارد، مانند دادن یک ID منحصربه‌فرد به هر آیتم و سپس ذخیره این ID در داخل [`dataTransfer`](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)، یا ذخیره یک ارجاع به عنصر DOM در یک متغیر سراسری. همه این رویکردها تقریباً اثر یکسانی دارند.

از آنجایی که وظایف همیشه قرار است جابه‌جا شوند و هرگز کپی یا پیوند داده نشوند، ویژگی {{domxref("DataTransfer.effectAllowed")}} را روی `"move"` تنظیم می‌کنیم تا تنها اثر مجاز باشد. این تغییر، اثر مکان‌نما را به‌روزرسانی می‌کند تا یک عملیات جابه‌جایی را نشان دهد. علاوه بر این، یک آیتم `dataTransfer` از نوع `task` تنظیم می‌کنیم که برای شناسایی وظیفه کشیده‌شده همان‌طور که قبلاً نشان داده شد استفاده می‌شود.

همان‌طور که در [اثرات رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations#drop_effects) ذکر شد، شما فقط می‌توانید `effectAllowed` را در کنترل‌کننده `dragstart` برای عنصر قابل کشیدن تنظیم کنید.

اکنون، می‌توانیم عمل جابه‌جایی را در داخل کنترل‌کننده {{domxref("HTMLElement/drop_event", "drop")}} در ستون مقصد فعال کنیم. می‌توانیم وظیفه کشیده‌شده را با ID آن شناسایی کنیم، آن را با استفاده از {{domxref("Element.remove()")}} از درخت DOM حذف کنیم، و سپس دوباره آن را در ستون مقصد قرار دهیم. از آنجایی که فقط در صورت رها شدن یک وظیفه اجازه رها کردن می‌دهیم، می‌توانیم با اطمینان ادامه دهیم که `draggedTask` وجود دارد.

```js
columns.forEach((column) => {
  column.addEventListener("drop", (event) => {
    event.preventDefault();

    const draggedTask = document.getElementById("dragged-task");
    draggedTask.remove();
    column.children[1].appendChild(draggedTask);
  });
});
```

در این مرحله، تجربه کاربری اصلی وجود دارد و می‌توانید وظایف را بین ستون‌ها بکشید.

## درج در مکان مشخص

در حال حاضر، وظیفه رها شده بدون توجه به جایی که رها کرده‌ایم، همیشه در انتهای ستون درج می‌شود. اکنون منطق رها کردن را بهبود می‌بخشیم تا به جای آن در محل رها شدن درج شود. اما چگونه باید محل رها شدن را به یک شاخص درج در ستون مقصد نگاشت کنیم؟ این یک قضاوت است، اما ما از اکتشافی زیر استفاده خواهیم کرد (در انتخاب اکتشافی دلخواه خود آزاد هستید): آیتم در شاخص آیتمی که مکان‌نما روی آن قرار دارد درج خواهد شد. اگر مکان‌نما بالای اولین آیتم یا پایین آخرین آیتم باشد، به ترتیب در ابتدا یا انتهای ستون درج می‌شود. اگر مکان‌نما بین دو آیتم باشد، در شاخص آیتم زیر مکان‌نما درج می‌شود.

برای مشخص کردن محل رها شدن، یک [نشانگر بصری](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations#custom_drop_feedback) برای محل رها شدن اضافه می‌کنیم. این کار را می‌توان با درج یک عنصر مکان‌نما (placeholder) در محل رها شدن انجام داد، که هنگام رها شدن با وظیفه کشیده‌شده جایگزین می‌شود. ابتدا تابع سازنده مکان‌نما را تعریف می‌کنیم:

```css live-sample___kanban
.placeholder {
  border: 1px solid #cccccc;
  border-radius: 3px;
}
```

```js live-sample___kanban
function makePlaceholder(draggedTask) {
  const placeholder = document.createElement("li");
  placeholder.classList.add("placeholder");
  placeholder.style.height = `${draggedTask.offsetHeight}px`;
  return placeholder;
}
```

این نشانگر در طول رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} جابه‌جا می‌شود. این پیچیده‌ترین بخش است، بنابراین آن را در یک تابع جداگانه استخراج کرده‌ایم. کد قبلی برای رویداد `dragover` به این تابع منتقل شده است. ابتدا عناصر مورد نیاز را دریافت می‌کنیم و در صورت عدم کشیدن یک وظیفه، به طور ایمن از تابع خارج می‌شویم:

```js live-sample___kanban
function movePlaceholder(event) {
  if (!event.dataTransfer.types.includes("task")) {
    return;
  }
  event.preventDefault();
  // Must exist because the ID is added for all drag events with a "task" data entry
  const draggedTask = document.getElementById("dragged-task");
  const column = event.currentTarget;
  const tasks = column.children[1];
  const existingPlaceholder = column.querySelector(".placeholder");
```

اگر از قبل یک مکان‌نما وجود داشته باشد و مکان‌نما هنوز داخل آن باشد، نیازی به تغییر چیزی نیست. توجه داشته باشید که در این مرحله مکان‌نمای موجود را حذف نمی‌کنیم، زیرا این کار باعث تغییر طرح‌بندی صفحه و احتمالاً ایجاد لرزش (flicker) می‌شود. فقط پس از تعیین کامل موقعیت جدید، طرح‌بندی را تغییر می‌دهیم.

```js live-sample___kanban
if (existingPlaceholder) {
  const placeholderRect = existingPlaceholder.getBoundingClientRect();
  if (
    placeholderRect.top <= event.clientY &&
    placeholderRect.bottom >= event.clientY
  ) {
    return;
  }
}
```

در غیر این صورت، به دنبال اولین وظیفه‌ای می‌گردیم که کاملاً بالای مکان‌نما نباشد. این وظیفه ممکن است اولین وظیفه باشد اگر مکان‌نما بالای همه آیتم‌ها باشد، وظیفه‌ای که مکان‌نما را در خود دارد، یا وظیفه زیر مکان‌نما اگر مکان‌نما بین دو آیتم باشد. مکان‌نمای ما باید در محل این وظیفه قرار گیرد. توجه داشته باشید که فقط مختصات Y را مقایسه می‌کنیم: حتی اگر مکان‌نما در حاشیه‌های چپ یا راست باشد، باید به عنوان قرار گرفتن روی وظیفه در نظر گرفته شود. پس از یافتن نقطه درج مناسب، چند چیز را تعیین می‌کنیم:

- اگر نقطه درج همان مکان‌نما باشد، نیازی به تغییر چیزی نیست. توجه داشته باشید که این کاملاً با شرط بالا یکسان نیست: این یکی ممکن است درست باشد اگر مکان‌نما بلافاصله بالای مکان‌نما بین دو آیتم باشد.
- اگر هنگام رها شدن، آیتم کشیده شده دقیقاً در جایی قرار گیرد که شروع کرده است، نباید اصلاً مکان‌نما نشان دهیم. این زمانی اتفاق می‌افتد که مکان‌نما قرار است بلافاصله در کنار وظیفه کشیده‌شده قرار گیرد، بنابراین بررسی می‌کنیم که آیا بلافاصله قبل از `draggedTask` (`task === draggedTask`) یا بعد از آن (`task.previousElementSibling === draggedTask`) درج می‌کنیم. در این صورت، همچنان مکان‌نمای موجود را در صورت وجود حذف می‌کنیم.
- در نهایت، مکان‌نما را در موقعیت تعیین‌شده درج می‌کنیم.

```js live-sample___kanban
for (const task of tasks.children) {
  if (task.getBoundingClientRect().bottom >= event.clientY) {
    if (task === existingPlaceholder) return;
    existingPlaceholder?.remove();
    if (task === draggedTask || task.previousElementSibling === draggedTask)
      return;
    tasks.insertBefore(
      existingPlaceholder ?? makePlaceholder(draggedTask),
      task,
    );
    return;
  }
}
```

اگر حلقه بالا یک وظیفه مناسب پیدا نکرد، به این معنی است که همه وظایف موجود بالای مکان‌نما هستند و باید مکان‌نما را در انتها درج کنیم. باز هم، اگر وظیفه کشیده‌شده از قبل آخرین آیتم باشد، مکان‌نما را اضافه نمی‌کنیم.

```js live-sample___kanban
  existingPlaceholder?.remove();
  if (tasks.lastElementChild === draggedTask) return;
  tasks.append(existingPlaceholder ?? makePlaceholder(draggedTask));
}
```

در نهایت، مکان‌نما در هنگام {{domxref("HTMLElement/dragleave_event", "dragleave")}} یا {{domxref("HTMLElement/drop_event", "drop")}} حذف می‌شود. توجه داشته باشید که `dragleave` زمانی فعال می‌شود که مکان‌نما از ستون خارج شده و وارد عنصر فرزند آن شود. از آنجایی که فقط می‌خواهیم مکان‌نما را زمانی که مکان‌نما کاملاً از ستون خارج می‌شود حذف کنیم، باید بررسی کنیم که آیا {{domxref("MouseEvent/relatedTarget", "relatedTarget")}}، که عنصری است که به سمت آن حرکت می‌کنیم، فرزندی از ستون است یا خیر.

کنترل‌کننده `drop` چیزی را که در [جابه‌جایی عناصر](#جابه‌جایی-عناصر) پیاده‌سازی کردیم اصلاح می‌کند. به جای افزودن وظیفه در انتها، باید آن را در وسط درج کنیم و از موقعیت مکان‌نما برای این کار استفاده می‌کنیم.

```js live-sample___kanban
columns.forEach((column) => {
  column.addEventListener("dragover", movePlaceholder);
  column.addEventListener("dragleave", (event) => {
    // If we are moving into a child element,
    // we aren't actually leaving the column
    if (column.contains(event.relatedTarget)) return;
    const placeholder = column.querySelector(".placeholder");
    placeholder?.remove();
  });
  column.addEventListener("drop", (event) => {
    event.preventDefault();

    const draggedTask = document.getElementById("dragged-task");
    const placeholder = column.querySelector(".placeholder");
    if (!placeholder) return;
    draggedTask.remove();
    column.children[1].insertBefore(draggedTask, placeholder);
    placeholder.remove();
  });
});
```

## خاکستری کردن وظیفه اصلی

در طول کشیدن، ممکن است به نظر برسد که وظیفه اصلی همچنان در جای خود است. برای نشان دادن بصری اینکه وظیفه در حال جابجایی است، می‌توانیم یک اثر "خاکستری" (grayed out) اعمال کنیم. همچنین معمول است که آن را از DOM حذف کنیم، اما این ممکن است با سایر منطق‌های اندازه‌گیری DOM که تنظیم کرده‌ایم تداخل داشته باشد، بنابراین می‌توانیم از CSS برای دستیابی به اثر مطلوب استفاده کنیم. این کار ساده است زیرا ما از قبل یک ID پایدار برای وظیفه کشیده‌شده داریم.

```css live-sample___kanban
#dragged-task {
  opacity: 0.2;
}
```

## نتیجه

{{EmbedLiveSample("kanban", "", 400)}}

## همچنین ببینید

- [HTML Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [Drag Operations](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)