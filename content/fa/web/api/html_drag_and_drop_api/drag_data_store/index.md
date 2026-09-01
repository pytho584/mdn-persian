---
title: "کار با فروشگاه دادهٔ کشیدن (drag data store)"
slug: Web/API/HTML_Drag_and_Drop_API/Drag_data_store
page-type: guide
---

{{DefaultAPISidebar("HTML Drag and Drop API")}}

رابط {{domxref("DragEvent")}} دارای ویژگی {{domxref("DragEvent.dataTransfer","dataTransfer")}} است که یک شیء {{domxref("DataTransfer")}} می‌باشد. اشیاء {{domxref("DataTransfer")}} زمینهٔ اصلی عملیات کشیدن را نشان می‌دهند و در طول رویدادهای مختلفِ فعال‌شده، یکسان باقی می‌مانند. این اشیاء شامل [داده‌های کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#drag_data_store)، [تصویر کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations#setting_the_drag_feedback_image)، [اثر رهاسازی](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations#drop_effects) و غیره هستند. این مقاله بر بخش _فروشگاه داده_ در `dataTransfer` تمرکز دارد.

## ساختار فروشگاه دادهٔ کشیدن

در بنیان، فروشگاه دادهٔ کشیدن فهرستی از آیتم‌ها است که به صورت {{domxref("DataTransferItemList")}} از اشیاء {{domxref("DataTransferItem")}} نمایش داده می‌شود. هر آیتم می‌تواند یکی از دو [نوع](/en-US/docs/Web/API/DataTransferItem/kind) باشد:

- `string`: بارِ آن یک رشته است که با {{domxref("DataTransferItem.getAsString", "getAsString()")}} قابل دریافت است.
- `file`: بارِ آن یک شیء فایل است که با {{domxref("DataTransferItem.getAsFile", "getAsFile()")}} قابل دریافت است (یا در صورت نیاز به عملیات پیچیده‌تر روی سیستم فایل، با {{domxref("DataTransferItem.getAsFileSystemHandle", "getAsFileSystemHandle()")}} یا {{domxref("DataTransferItem.webkitGetAsEntry", "webkitGetAsEntry()")}}).

علاوه بر این، هر آیتم با یک [نوع (type)](/en-US/docs/Web/API/DataTransferItem/type) نیز شناسایی می‌شود که طبق قرارداد، در قالب یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) است. این نوع می‌تواند به مصرف‌کننده بگوید که بارِ داده چگونه باید تجزیه یا رمزگشایی شود. برای همهٔ آیتم‌های متنی، فهرست فقط می‌تواند برای هر نوع، یک آیتم داشته باشد؛ بنابراین فهرست در عمل شامل دو مجموعهٔ مجزا است: فهرستی از فایل‌ها که احتمالاً انواع تکراری دارند، و یک {{jsxref("Map")}} از آیتم‌های متنی که با نوع آن‌ها کلیدگذاری شده است. به طور کلی، فهرست فایل‌ها نشان‌دهندهٔ چندین فایل در حال کشیدن است. نقشهٔ متنی _نشان‌دهندهٔ_ چند منبع در حال انتقال نیست، بلکه نشان‌دهندهٔ یک منبع واحد است که به روش‌های مختلف کدگذاری شده، تا طرف دریافت‌کننده بتواند مناسب‌ترین تفسیر پشتیبانی‌شده را انتخاب کند. آیتم‌های متنی باید به ترتیب نزولی اولویت مرتب شوند.

این فهرست از طریق ویژگی {{domxref("DataTransfer.items")}} قابل دسترسی است.

HTML Drag and Drop API چندین بار تکرار شده و در نتیجه دو روش هم‌زمان برای مدیریت فروشگاه داده وجود دارد. پیش از رابط‌های `DataTransferItemList` و `DataTransferItem`، «روش قدیمی» از ویژگی‌های زیر روی `DataTransfer` استفاده می‌کرد:

- {{domxref("DataTransfer.types", "types")}}: شامل ویژگی‌های `type` مربوط به _آیتم‌های متنی_ در فهرست، به علاوه مقدار `"files"` در صورت وجود هر _آیتم فایلی_ است.
- {{domxref("DataTransfer.setData", "setData()")}}، {{domxref("DataTransfer.getData", "getData()")}}، {{domxref("DataTransfer.clearData", "clearData()")}}: دسترسی به _آیتم‌های متنی_ فهرست را با استفاده از مدل «نگاشت نوع به بار» فراهم می‌کنند.
- {{domxref("DataTransfer.files", "files")}}: دسترسی به _آیتم‌های فایلی_ فهرست را به صورت یک {{domxref("FileList")}} فراهم می‌کند.

ممکن است متوجه شده باشید که انواع _آیتم‌های فایلی_ به طور مستقیم در معرض دید قرار نمی‌گیرند. آن‌ها همچنان قابل دسترسی هستند، اما فقط از طریق ویژگی {{domxref("Blob.type", "type")}} هر شیء {{domxref("File")}} در فهرست `files`؛ بنابراین اگر نتوانید فایل‌ها را بخوانید، نمی‌توانید انواع آن‌ها را نیز بدانید (برای زمان خواندن فروشگاه داده، بخش [خواندن فروشگاه دادهٔ کشیدن](#reading_the_drag_data_store) را ببینید).

برای دریافت فایل‌ها و انواع آن‌ها، توصیه می‌کنیم از ویژگی `items` استفاده کنید، زیرا رابط سازگارتر و منعطف‌تری ارائه می‌دهد. برای آیتم‌های متنی نیز بهتر است برای سازگاری از ویژگی `items` استفاده کنید، هرچند روش `getData()` برای دسترسی به یک نوع خاص یا حذف آن راحت‌تر است.

یکی دیگر از تفاوت‌های کلیدی بین رابط‌های {{domxref("DataTransfer")}} و {{domxref("DataTransferItem")}} این است که اولی از روش همگام {{domxref("DataTransfer.getData","getData()")}} برای دسترسی به بار متنی استفاده می‌کند، در حالی که دومی از روش ناهمگام {{domxref("DataTransferItem.getAsString","getAsString()")}} استفاده می‌کند.

## اصلاح فروشگاه دادهٔ کشیدن

برای آیتم‌هایی که به طور پیش‌فرض قابل کشیدن هستند، مانند تصاویر، پیوندها و انتخاب‌ها، دادهٔ کشیدن از قبل توسط مرورگر تعریف شده است؛ برای عناصر قابل کشیدن سفارشی که با استفاده از ویژگی `draggable` تعریف می‌شوند، باید دادهٔ کشیدن را خودتان تعریف کنید. تنها زمانی که می‌توانید هر تغییری در فروشگاه داده ایجاد کنید، درون کنترل‌کنندهٔ رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} است—زیرا برای `dataTransfer` هر رویداد کشیدن دیگری، فروشگاه داده غیرقابل تغییر است.

برای افزودن دادهٔ متنی به فروشگاه دادهٔ کشیدن، «روش جدید» از متد {{domxref("DataTransferItemList.add()")}} استفاده می‌کند، در حالی که «روش قدیمی» از متد {{domxref("DataTransfer.setData()")}} استفاده می‌کند.

```js
function dragstartHandler(ev) {
  // روش جدید: add(data, type)
  ev.dataTransfer.items.add(ev.target.innerText, "text/plain");
  // روش قدیمی: setData(type, data)
  ev.dataTransfer.setData("text/html", ev.target.outerHTML);
}

const p1 = document.getElementById("p1");
p1.addEventListener("dragstart", dragstartHandler);
```

برای هر دو روش، اگر زمانی که فروشگاه داده غیرقابل تغییر است فراخوانی شوند، هیچ اتفاقی نمی‌افتد. اگر آیتم متنی با همان نوع از قبل وجود داشته باشد، `add()` یک خطا پرتاب می‌کند در حالی که `setData()` آیتم موجود را بازنویسی می‌کند.

برای افزودن دادهٔ فایلی به فروشگاه دادهٔ کشیدن، «روش جدید» همچنان از متد {{domxref("DataTransferItemList.add()")}} استفاده می‌کند. از آنجا که «روش قدیمی» آیتم‌های فایلی را در ویژگی {{domxref("DataTransfer.files")}} ذخیره می‌کند که یک {{domxref("FileList")}} فقط‌خواندنی است، معادل مستقیمی وجود ندارد.

```js
function dragstartHandler(ev) {
  // روش جدید: add(data)
  ev.dataTransfer.items.add(new File([blob], "image.png"));
}

const p1 = document.getElementById("p1");
p1.addEventListener("dragstart", dragstartHandler);
```

توجه داشته باشید که هنگام افزودن دادهٔ فایلی، `add()` پارامتر `type` را نادیده می‌گیرد و از ویژگی {{domxref("Blob.type", "type")}} شیء `File` استفاده می‌کند.

> [!NOTE]
> محافظت خواندن/نوشتن به صورت [per-job](/en-US/docs/Web/JavaScript/Reference/Execution_model#job_queue_and_event_loop) انجام می‌شود، به این معنی که فقط _کد همگام_ درون کنترل‌کنندهٔ `dragstart` می‌تواند فروشگاه داده را تغییر دهد. اگر پس از یک عملیات ناهمگام سعی در دسترسی به فروشگاه داده کنید، دیگر مجوز نوشتن نخواهید داشت. برای مثال، این کار نمی‌کند:
>
> ```js example-bad
> function dragstartHandler(ev) {
>   canvas.toBlob((blob) => {
>     ev.dataTransfer.items.add(new File([blob], "image.png"));
>   });
> }
> ```

حذف داده نیز مشابه است، با استفاده از متدهای {{domxref("DataTransferItemList.remove()")}}، {{domxref("DataTransferItemList.clear()")}} یا {{domxref("DataTransfer.clearData()")}}.

## خواندن فروشگاه دادهٔ کشیدن

تنها زمانی که می‌توانید از فروشگاه داده _بخوانید_، به جز رویداد `dragstart` که دسترسی کامل به فروشگاه داده دارید، در طول رویداد {{domxref("HTMLElement/drop_event", "drop")}} است که به هدف رهاسازی امکان بازیابی داده را می‌دهد.

برای خواندن دادهٔ متنی از فروشگاه دادهٔ کشیدن، «روش جدید» از شیء {{domxref("DataTransferItemList")}} استفاده می‌کند، در حالی که «روش قدیمی» از متد {{domxref("DataTransfer.getData()")}} استفاده می‌کند. روش جدید برای پیمایش همهٔ آیتم‌ها راحت‌تر است، در حالی که روش قدیمی برای دسترسی به یک نوع خاص راحت‌تر است.

```js
function dropHandler(ev) {
  // روش جدید: پیمایش آیتم‌ها
  for (const item of ev.dataTransfer.items) {
    if (item.kind === "string") {
      item.getAsString((data) => {
        // انجام کاری با data
      });
    }
  }
  // روش قدیمی: getData(type)
  const data = ev.dataTransfer.getData("text/plain");
}

const p1 = document.getElementById("p1");
p1.addEventListener("drop", dropHandler);
```

برای خواندن دادهٔ فایلی از فروشگاه دادهٔ کشیدن، «روش جدید» همچنان از شیء {{domxref("DataTransferItemList")}} استفاده می‌کند، در حالی که «روش قدیمی» از ویژگی {{domxref("DataTransfer.files")}} استفاده می‌کند.

```js
function dropHandler(ev) {
  // روش جدید: پیمایش آیتم‌ها
  for (const item of ev.dataTransfer.items) {
    if (item.kind === "file") {
      const file = item.getAsFile(); // یک شیء File
    }
  }
  // روش قدیمی: پیمایش فایل‌ها
  for (const file of ev.dataTransfer.files) {
    // انجام کاری با file
  }
}

const p1 = document.getElementById("p1");
p1.addEventListener("drop", dropHandler);
```

### حالت محافظت‌شده

در خارج از رویدادهای `dragstart` و `drop`، فروشگاه داده در _حالت محافظت‌شده_ قرار دارد و به کد اجازه نمی‌دهد به هیچ بارِ داده‌ای دسترسی پیدا کند. یعنی:

- تمام تلاش‌های [تغییر](#modifying_the_drag_data_store) بی‌صدا هیچ کاری نمی‌کنند یا یک `DOMException` پرتاب می‌کنند (فقط برای `items.add()` و `items.remove()`).
- `DataTransfer.getData()` همیشه رشتهٔ خالی را برمی‌گرداند.
- `DataTransfer.files` همیشه یک فهرست خالی را برمی‌گرداند.
- `DataTransferItem.getAsString()` بدون فراخوانی callback برمی‌گردد.
- `DataTransferItem.getAsFile()` همیشه `null` را برمی‌گرداند.

باز هم، محافظت خواندن/نوشتن به صورت [per-job](/en-US/docs/Web/JavaScript/Reference/Execution_model#job_queue_and_event_loop) انجام می‌شود، به این معنی که فقط _کد همگام_ درون کنترل‌کنندهٔ `drop` می‌تواند فروشگاه داده را بخواند. اگر پس از یک عملیات ناهمگام سعی در دسترسی به فروشگاه داده کنید، دیگر مجوز نوشتن نخواهید داشت. برای مثال، این کار نمی‌کند:

```js example-bad
function getDataPromise(item) {
  return new Promise((resolve) => {
    item.getAsString((data) => {
      resolve(data);
    });
  });
}

async function dropHandler(ev) {
  for (const item of ev.dataTransfer.items) {
    if (item.kind === "string") {
      // بد: تا بار دوم که این اجرا می‌شود، دیگر در همان job نیستیم
      const data = await getDataPromise(item);
    }
  }
}

const p1 = document.getElementById("p1");
p1.addEventListener("drop", dropHandler);
```

در عوض، باید همهٔ متدهای دسترسی را به صورت همگام و از ابتدا فراخوانی کنید و بعداً منتظر نتایج آن‌ها بمانید:

```js example-good
async function dropHandler(ev) {
  const promises = [];
  for (const item of ev.dataTransfer.items) {
    if (item.kind === "string") {
      // بد: تا بار دوم که این اجرا می‌شود، دیگر در همان job نیستیم
      promises.push(getDataPromise(item));
    }
  }
  const results = await Promise.all(promises);
}
```

## انواع دادهٔ متداول کشیدن

این مشخصات فقط رفتار چند نوع داده را تعریف می‌کند، اما مرورگرها گاهی به طور بومی از انواع بیشتری پشتیبانی می‌کنند. به طور کلی، انواع به عنوان یک _پروتکل_ مشابه انواع MIME در نظر گرفته می‌شوند و می‌توانید از هر نوعی استفاده کنید تا زمانی که طرف دریافت‌کننده (یک صفحهٔ وب دیگر، بخش دیگری از همان صفحهٔ وب، یا حتی جایی خارج از مرورگر) آن را بفهمد. این بخش برخی قراردادهای رایج و رفتارهای پیش‌فرض مرورگرها را شرح می‌دهد.

توجه داشته باشید که سناریوهای زیر به _قصد_ اشاره دارند نه _رفتار_. به عنوان مثال، وقتی می‌گوییم «کشیدن یک پیوند»، کاربر ممکن است یک عنصر واقعی `<a>` را نکشد؛ ممکن است محفظه‌ای را بکشد که حاوی یک یا چند پیوند است، اما قصد انتقال پیوند(ها) به عنوان داده است، بنابراین فروشگاه داده‌ای که آماده می‌کنید می‌تواند همان باشد که گویی کاربر یک پیوند واقعی را می‌کشد.

### کشیدن متن

برای کشیدن متن، از نوع `text/plain` با رشتهٔ کشیده‌شده به عنوان مقدار استفاده کنید. برای مثال:

```js
event.dataTransfer.items.add("This is text to drag", "text/plain");
```

همیشه باید داده‌ای از نوع `text/plain` را به عنوان یک گزینهٔ جایگزین برای برنامه‌ها یا اهداف رهاسازی که از انواع دیگر پشتیبانی نمی‌کنند اضافه کنید، مگر اینکه جایگزین متنی منطقی‌ای وجود نداشته باشد. همیشه این نوع `text/plain` را آخر اضافه کنید، زیرا کمترین ویژگی را دارد و نباید ترجیح داده شود.

در `getData()`، `setData()` و `clearData()`، نوع `Text` (بدون حساسیت به حروف بزرگ) به عنوان `text/plain` در نظر گرفته می‌شود.

به طور پیش‌فرض، وقتی یک انتخاب کشیده می‌شود، آیتم‌های دادهٔ زیر ایجاد می‌شوند:

- `text/plain`: حاوی متن انتخاب‌شده. فایرفاکس و سافاری این آیتم را بعد از `text/html` مرتب می‌کنند، اگرچه این مشخصات آن را اول می‌خواهد.
- `text/html`: حاوی کد HTML کامل عناصر انتخاب‌شده (با تمام استایل‌های درون‌خطی).

این مشخصات همچنین آیتم