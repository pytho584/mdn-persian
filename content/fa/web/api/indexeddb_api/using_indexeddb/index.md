---
title: Using IndexedDB
slug: Web/API/IndexedDB_API/Using_IndexedDB
page-type: guide
---

{{DefaultAPISidebar("IndexedDB")}}

IndexedDB روشی برای ذخیره‌سازی پایدار داده‌ها در مرورگر کاربر است. از آنجا که به شما امکان می‌دهد برنامه‌های وب با قابلیت‌های پرس‌وجوی قدرتمند بدون توجه به در دسترس بودن شبکه بسازید، برنامه‌های شما می‌توانند هم به صورت آنلاین و هم آفلاین کار کنند.

## درباره این سند

این آموزش شما را با استفاده از API ناهمگام (asynchronous) ایندکس‌دبی آشنا می‌کند. اگر با IndexedDB آشنا نیستید، ابتدا مقالهٔ [ویژگی‌های کلیدی و اصطلاحات پایه IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology) را بخوانید.

برای مستندات مرجع API ایندکس‌دبی، به مقالهٔ [API IndexedDB](/en-US/docs/Web/API/IndexedDB_API) و زیرصفحه‌های آن مراجعه کنید. این مقاله انواع اشیاء استفاده‌شده در IndexedDB و همچنین متدهای API ناهمگام را مستند می‌کند (API همگام از مشخصات حذف شده است).

## الگوی پایه

الگوی پایه‌ای که IndexedDB تشویق می‌کند به این صورت است:

1. باز کردن یک پایگاه داده.
2. ایجاد یک object store (ذخیره‌گاه اشیاء) در پایگاه داده.
3. شروع یک تراکنش و ارسال درخواست برای انجام عملیات پایگاه داده، مانند افزودن یا بازیابی داده.
4. منتظر ماندن برای تکمیل عملیات با گوش دادن به رویداد DOM مناسب.
5. انجام کاری با نتایج (که روی شیء درخواست قابل مشاهده است).

با درک این مفاهیم کلی، می‌توانیم به مطالب مشخص‌تر بپردازیم.

## ایجاد و ساختاردهی object store

### باز کردن پایگاه داده

ما کل فرایند را این‌گونه شروع می‌کنیم:

```js
// Let us open our database
const request = window.indexedDB.open("MyTestDatabase", 3);
```

دیدید؟ باز کردن پایگاه داده دقیقاً مثل هر عملیات دیگری است — باید آن را «درخواست» کنید.

درخواست باز کردن، پایگاه داده را فوراً باز نمی‌کند و تراکنش را شروع نمی‌کند. فراخوانی تابع `open()` یک شیء [`IDBOpenDBRequest`](/en-US/docs/Web/API/IDBOpenDBRequest) برمی‌گرداند که دارای یک مقدار نتیجه (موفقیت) یا خطا است که آن را به‌صورت یک رویداد مدیریت می‌کنید. بیشتر توابع ناهمگام دیگر در IndexedDB نیز همین کار را انجام می‌دهند — یک شیء [`IDBRequest`](/en-US/docs/Web/API/IDBRequest) با نتیجه یا خطا برمی‌گردانند. نتیجه تابع باز کردن، یک نمونه از `IDBDatabase` است.

پارامتر دوم متد open نسخه پایگاه داده است. نسخه پایگاه داده تعیین می‌کند که طرح پایگاه داده (schema) — یعنی object storeهای موجود در پایگاه داده و ساختار آن‌ها — چگونه باشد. اگر پایگاه داده از قبل وجود نداشته باشد، توسط عملیات `open` ساخته می‌شود و سپس رویداد `onupgradeneeded` فعال می‌شود و شما طرح پایگاه داده را در handler این رویداد ایجاد می‌کنید. اگر پایگاه داده وجود داشته باشد اما شماره نسخه بالاتری را مشخص کرده باشید، رویداد `onupgradeneeded` بلافاصله فعال می‌شود و به شما امکان می‌دهد در handler آن، طرح به‌روزشده را ارائه دهید. در ادامه در بخش [ایجاد یا به‌روزرسانی نسخه پایگاه داده](#creating_or_updating_the_version_of_the_database) و صفحه مرجع {{ domxref("IDBFactory.open") }} بیشتر درباره این موضوع توضیح داده می‌شود.

> [!WARNING]
> شماره‌های نسخه اعداد صحیح هستند، بنابراین مقادیر ارسالی گرد می‌شوند — برای مثال، مقادیر 2.1 و 2.4 هر دو به 2 گرد می‌شوند. تلاش برای ارتقاء بین اعدادی که به یک عدد صحیح گرد می‌شوند، رویداد `onupgradeneeded` را فعال نمی‌کند. هنگام کار با شماره‌های نسخه بزرگ، به [بازه اعداد صحیح](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#number_encoding) قابل نمایش در JavaScript نیز توجه کنید.

#### ایجاد handlerها

اولین کاری که تقریباً برای همه درخواست‌های تولیدشده باید انجام دهید، افزودن handlerهای موفقیت و خطا است:

```js
request.onerror = (event) => {
  // Do something with request.error!
};
request.onsuccess = (event) => {
  // Do something with request.result!
};
```

اگر درخواست موفق باشد، رویداد {{domxref("IDBRequest.success_event", "success")}} فعال می‌شود و تابع اختصاص‌داده‌شده به `onsuccess` فراخوانی می‌شود. اگر درخواست ناموفق باشد، رویداد {{domxref("IDBRequest.error_event", "error")}} فعال می‌شود و تابع اختصاص‌داده‌شده به `onerror` فراخوانی می‌شود.

API ایندکس‌دبی به‌گونه‌ای طراحی شده است که نیاز به مدیریت خطا را به حداقل برساند، بنابراین احتمالاً رویدادهای خطای زیادی نخواهید دید (حداقل بعد از اینکه به API عادت کنید!). با این حال، در مورد باز کردن پایگاه داده، شرایط رایجی وجود دارد که رویداد خطا تولید می‌کنند. محتمل‌ترین مشکل این است که کاربر به برنامه وب شما اجازه ایجاد پایگاه داده را نداده باشد. یکی از اهداف اصلی طراحی IndexedDB اجازه ذخیره حجم زیادی از داده برای استفاده آفلاین است. (برای آگاهی از میزان فضای ذخیره‌سازی در هر مرورگر، به [چقدر داده می‌توان ذخیره کرد؟ در صفحه سهمیه ذخیره‌سازی مرورگر و معیارهای حذف](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria#how_much_data_can_be_stored) مراجعه کنید.)

بدیهی است که مرورگرها نمی‌خواهند به یک شبکه تبلیغاتی یا وب‌سایت مخرب اجازه دهند رایانه شما را آلوده کند، بنابراین مرورگرها در گذشته هنگام اولین تلاش هر برنامه وب برای باز کردن یک IndexedDB جهت ذخیره‌سازی، از کاربر سؤال می‌کردند. کاربر می‌توانست اجازه دسترسی بدهد یا آن را رد کند. همچنین، ذخیره‌سازی IndexedDB در حالت خصوصی مرورگرها فقط در حافظه (in-memory) باقی می‌ماند تا زمانی که جلسه ناشناس بسته شود.

حال، فرض کنید کاربر درخواست شما برای ایجاد پایگاه داده را پذیرفته و یک رویداد موفقیت برای اجرای callback موفقیت دریافت کرده‌اید؛ بعد چه؟ درخواست در اینجا با فراخوانی `indexedDB.open()` ایجاد شده است، بنابراین `request.result` یک نمونه از `IDBDatabase` است و قطعاً می‌خواهید آن را برای بعد ذخیره کنید. کد شما ممکن است چیزی شبیه این باشد:

```js
let db;
const request = indexedDB.open("MyTestDatabase");
request.onerror = (event) => {
  console.error("Why didn't you allow my web app to use IndexedDB?!");
};
request.onsuccess = (event) => {
  db = event.target.result;
};
```

#### مدیریت خطاها

همان‌طور که در بالا ذکر شد، رویدادهای خطا bubble می‌شوند (به سمت بالا انتشار می‌یابند). رویدادهای خطا ابتدا به درخواستی که خطا را تولید کرده هدف می‌گیرند، سپس رویداد به تراکنش و در نهایت به شیء پایگاه داده انتشار می‌یابد. اگر می‌خواهید از افزودن handler خطا به هر درخواست اجتناب کنید، می‌توانید به جای آن یک handler خطای واحد روی شیء پایگاه داده اضافه کنید، مانند:

```js
db.onerror = (event) => {
  // Generic error handler for all errors targeted at this database's
  // requests!
  console.error(`Database error: ${event.target.error?.message}`);
};
```

یکی از خطاهای رایج هنگام باز کردن پایگاه داده `VER_ERR` است. این خطا نشان می‌دهد که نسخه پایگاه داده ذخیره‌شده روی دیسک _بزرگ‌تر_ از نسخه‌ای است که می‌خواهید باز کنید. این یک مورد خطا است که باید همیشه توسط handler خطا مدیریت شود.

### ایجاد یا به‌روزرسانی نسخه پایگاه داده

وقتی یک پایگاه داده جدید ایجاد می‌کنید یا شماره نسخه یک پایگاه داده موجود را افزایش می‌دهید (با مشخص کردن شماره نسخه بالاتر از قبل، هنگام [باز کردن پایگاه داده](#opening_a_database))، رویداد `onupgradeneeded` فعال می‌شود و یک شیء [IDBVersionChangeEvent](/en-US/docs/Web/API/IDBVersionChangeEvent) به هر handler رویداد `onversionchange` که روی `request.result` (یعنی `db` در مثال) تنظیم شده باشد، ارسال می‌شود. در handler رویداد `upgradeneeded`، باید object storeهای مورد نیاز این نسخه از پایگاه داده را ایجاد کنید:

```js
// This event is only implemented in recent browsers
request.onupgradeneeded = (event) => {
  // Save the IDBDatabase interface
  const db = event.target.result;

  // Create an objectStore for this database
  const objectStore = db.createObjectStore("name", { keyPath: "myKey" });
};
```

در این حالت، پایگاه داده از قبل object storeهای نسخه قبلی را خواهد داشت، بنابراین نیازی به ایجاد دوباره آن‌ها نیست. فقط باید object storeهای جدید ایجاد کنید یا object storeهایی از نسخه قبلی را که دیگر لازم نیستند حذف کنید. اگر نیاز به تغییر یک object store موجود دارید (مثلاً تغییر `keyPath`)، باید object store قدیمی را حذف و آن را با گزینه‌های جدید دوباره ایجاد کنید. (توجه کنید که این کار اطلاعات موجود در object store را حذف می‌کند! اگر نیاز به حفظ آن اطلاعات دارید، قبل از ارتقاء پایگاه داده آن‌ها را بخوانید و در جای دیگری ذخیره کنید.)

تلاش برای ایجاد یک object store با نامی که از قبل وجود دارد (یا تلاش برای حذف یک object store با نامی که وجود ندارد) باعث بروز خطا می‌شود.

اگر رویداد `onupgradeneeded` با موفقیت پایان یابد، handler `onsuccess` درخواست باز کردن پایگاه داده فعال می‌شود.

### ساختاردهی پایگاه داده

حال به ساختاردهی پایگاه داده می‌پردازیم. IndexedDB به جای جدول‌ها از object store استفاده می‌کند و یک پایگاه داده می‌تواند هر تعداد object store داشته باشد. هر زمان که مقداری در یک object store ذخیره می‌شود، با یک کلید (key) مرتبط می‌شود. بسته به اینکه object store از [key path](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_path) یا [key generator](/en-US/docs/Web/API/IndexedDB_API/Basic_Terminology#key_generator) استفاده کند، روش‌های مختلفی برای ارائه کلید وجود دارد.

جدول زیر روش‌های مختلف ارائه کلید را نشان می‌دهد:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">Key Path (<code>keyPath</code>)</th>
      <th scope="col">Key Generator (<code>autoIncrement</code>)</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>خیر</td>
      <td>خیر</td>
      <td>
        این object store می‌تواند هر نوع مقداری را نگه دارد، حتی مقادیر اولیه مانند اعداد و رشته‌ها. هر زمان که می‌خواهید مقدار جدیدی اضافه کنید، باید یک آرگومان کلید جداگانه ارائه دهید.
      </td>
    </tr>
    <tr>
      <td>بله</td>
      <td>خیر</td>
      <td>
        این object store فقط می‌تواند اشیاء JavaScript را نگه دارد. اشیاء باید دارای خاصیتی با همان نام key path باشند.
      </td>
    </tr>
    <tr>
      <td>خیر</td>
      <td>بله</td>
      <td>
        این object store می‌تواند هر نوع مقداری را نگه دارد. کلید به‌طور خودکار برای شما تولید می‌شود، یا اگر می‌خواهید از کلید خاصی استفاده کنید، می‌توانید یک آرگومان کلید جداگانه ارائه دهید.
      </td>
    </tr>
    <tr>
      <td>بله</td>
      <td>بله</td>
      <td>
        این object store فقط می‌تواند اشیاء JavaScript را نگه دارد. معمولاً یک کلید تولید می‌شود و مقدار کلید تولیدشده در خاصیتی از شیء با همان نام key path ذخیره می‌شود. با این حال، اگر چنین خاصیتی از قبل وجود داشته باشد، مقدار آن خاصیت به‌جای تولید کلید جدید به عنوان کلید استفاده می‌شود.
      </td>
    </tr>
  </tbody>
</table>

شما همچنین می‌توانید روی هر object store ایندکس ایجاد کنید، به شرطی که object store اشیاء را نگه دارد، نه مقادیر اولیه را. ایندکس به شما امکان می‌دهد مقادیر ذخیره‌شده در object store را با استفاده از مقدار یک خاصیت از شیء ذخیره‌شده جستجو کنید، به جای کلید شیء.

علاوه بر این، ایندکس‌ها می‌توانند محدودیت‌های ساده‌ای روی داده‌های ذخیره‌شده اعمال کنند. با تنظیم پرچم unique هنگام ایجاد ایندکس، ایندکس تضمین می‌کند که دو شیء با مقدار یکسان برای key path ایندکس ذخیره نشوند. بنابراین، برای مثال، اگر object store دارید که مجموعه‌ای از افراد را نگه می‌دارد و می‌خواهید مطمئن شوید که دو نفر آدرس ایمیل یکسان ندارند، می‌توانید از ایندکسی با پرچم unique استفاده کنید.

ممکن است گیج‌کننده به نظر برسد، اما این مثال ساده باید مفاهیم را روشن کند. ابتدا، داده‌های مشتری را که در مثال استفاده می‌کنیم تعریف می‌کنیم:

```js
// This is what our customer data looks like.
const customerData = [
  { ssn: "444-44-4444", name: "Bill", age: 35, email: "bill@company.com" },
  { ssn: "555-55-5555", name: "Donna", age: 32, email: "donna@home.org" },
];
```

البته، شما از شماره تأمین اجتماعی کسی به عنوان کلید اصلی جدول مشتریان استفاده نمی‌کنید، زیرا همه شماره تأمین اجتماعی ندارند، و به جای سن، تاریخ تولد را ذخیره می‌کنید، اما بیایید برای راحتی این انتخاب‌های نامناسب را نادیده بگیریم و ادامه دهیم.

حال بیایید ایجاد یک IndexedDB برای ذخیره داده‌هایمان را بررسی کنیم:

```js
const dbName = "the_name";

const request = indexedDB.open(dbName, 2);

request.onerror = (event) => {
  // Handle errors.
};
request.onupgradeneeded = (event) => {
  const db = event.target.result;

  // Create an objectStore to hold information about our customers. We're
  // going to use "ssn" as our key path because it's guaranteed to be
  // unique - or at least that's what I was told during the kickoff meeting.
  const objectStore = db.createObjectStore("customers", { keyPath: "ssn" });

  // Create an index to search customers by name. We may have duplicates
  // so we can't use a unique index.
  objectStore.createIndex("name", "name", { unique: false });

  // Create an index to search customers by email. We want to ensure that
  // no two customers have the