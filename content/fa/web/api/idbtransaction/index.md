---
title: IDBTransaction
slug: Web/API/IDBTransaction
page-type: web-api-interface
browser-compat: api.IDBTransaction
---

{{APIRef("IndexedDB")}} {{AvailableInWorkers}}

رابط **`IDBTransaction`** در [API IndexedDB](/en-US/docs/Web/API/IndexedDB_API) یک تراکنش ایستا و ناهمزمان روی پایگاه‌داده با استفاده از ویژگی‌های مدیریت‌کننده رویداد فراهم می‌کند. تمام خواندن و نوشتن داده‌ها درون تراکنش‌ها انجام می‌شود. از {{domxref("IDBDatabase")}} برای شروع تراکنش‌ها، از `IDBTransaction` برای تنظیم حالت تراکنش (مثلاً `readonly` یا `readwrite`) استفاده می‌کنید، و برای ارسال درخواست به یک {{domxref("IDBObjectStore")}} دسترسی پیدا می‌کنید. همچنین می‌توانید از یک شیء `IDBTransaction` برای لغو تراکنش‌ها استفاده کنید.

{{InheritanceDiagram}}

تراکنش‌ها در زمان ایجاد شدن شروع می‌شوند، نه زمانی که اولین درخواست قرار داده می‌شود؛ برای مثال به این کد توجه کنید:

```js
const trans1 = db.transaction("foo", "readwrite");
const trans2 = db.transaction("foo", "readwrite");
const objectStore2 = trans2.objectStore("foo");
const objectStore1 = trans1.objectStore("foo");
objectStore2.put("2", "key");
objectStore1.put("1", "key");
```

پس از اجرای کد، فروشگاه اشیاء باید حاوی مقدار "2" باشد، زیرا `trans2` باید پس از `trans1` اجرا شود.

یک تراکنش بین حالت‌های _فعال_ و _غیرفعال_ در میان وظایف حلقه رویداد جابه‌جا می‌شود. در وظیفه‌ای که ایجاد شده و در هر وظیفه از مدیریت‌کننده‌های رویداد [`success`](/en-US/docs/Web/API/IDBRequest/success_event) یا [`error`](/en-US/docs/Web/API/IDBRequest/error_event) درخواست‌ها فعال است. در بقیه وظایف غیرفعال است، که در این صورت قرار دادن درخواست‌ها با شکست مواجه می‌شود. اگر در زمانی که تراکنش فعال است هیچ درخواست جدیدی قرار داده نشود و درخواست‌های معلق دیگری نیز وجود نداشته باشد، تراکنش به‌طور خودکار انجام می‌شود.

## شکست‌های تراکنش

تراکنش‌ها می‌توانند به دلایل مشخصی شکست بخورند که همهٔ آنها (به جز خراب شدن مرورگر) باعث فراخوانی یک بازگشت لغو می‌شوند:

- لغو به دلیل درخواست‌های نامعتبر، مانند تلاش برای `add()` کردن یک کلید تکراری، یا `put()` با کلید ایندکس تکراری و محدودیت یکتایی. این باعث خطا روی درخواست می‌شود که می‌تواند به خطا روی تراکنش منتقل شود و تراکنش را لغو کند. با استفاده از `preventDefault()` روی رویداد خطای درخواست می‌توان از این کار جلوگیری کرد.
- فراخوانی صریح `abort()` از طرف اسکریپت.
- یک استثنای مدیریت‌نشده در مدیریت‌کننده `success`/`error` درخواست.
- یک خطای I/O (مثلاً شکست واقعی در نوشتن روی دیسک، یا سایر خرابی‌های سیستم‌عامل/سخت‌افزار).
- تجاوز از سهمیه.
- خراب شدن مرورگر.

## تضمین‌های ماندگاری در فایرفاکس

توجه داشته باشید که از فایرفاکس ۴۰ به بعد، تراکنش‌های IndexedDB تضمین‌های ماندگاری سست‌تری برای افزایش کارایی دارند (به [بگ فایرفاکس 1112702](https://bugzil.la/1112702) مراجعه کنید). پیش‌تر در یک تراکنش `readwrite`، رویداد {{domxref("IDBTransaction.complete_event","complete")}} فقط زمانی فعال می‌شد که تضمین شود تمام داده‌ها روی دیسک نوشته شده‌اند. در فایرفاکس ۴۰+ رویداد `complete` پس از آنکه به سیستم‌عامل دستور نوشتن داده داده شد فعال می‌شود، اما احتمالاً قبل از اینکه آن داده واقعاً روی دیسک نوشته شود. بنابراین رویداد `complete` ممکن است سریع‌تر از قبل تحویل داده شود، اما احتمال کمی وجود دارد که کل تراکنش از بین برود اگر سیستم‌عامل خراب شود یا برق قبل از نوشتن داده روی دیسک قطع شود. از آنجایی که چنین رویدادهای فاجعه‌باری نادر هستند، بسیاری از مصرف‌کنندگان نیازی به نگرانی بیشتر ندارند.

اگر به هر دلیلی باید ماندگاری را تضمین کنید (مثلاً داده‌های بحرانی ذخیره می‌کنید که بعداً قابل محاسبه مجدد نیستند)، می‌توانید با ایجاد یک تراکنش با استفاده از حالت تجربی (غیراستاندارد) `readwriteflush`، تراکنش را مجبور به نوشتن روی دیسک قبل از تحویل رویداد `complete` کنید (به {{domxref("IDBDatabase.transaction")}} مراجعه کنید).

## ویژگی‌های نمونه

- {{domxref("IDBTransaction.db")}} {{ReadOnlyInline}}
  - : اتصال پایگاه‌داده‌ای که این تراکنش با آن مرتبط است.
- {{domxref("IDBTransaction.durability")}} {{ReadOnlyInline}}
  - : راهنمای ماندگاری که تراکنش با آن ایجاد شده را برمی‌گرداند.
- {{domxref("IDBTransaction.error")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMException")}} را برمی‌گرداند که نوع خطای رخ‌داده را در صورت ناموفق بودن تراکنش نشان می‌دهد. این ویژگی اگر تراکنش تمام نشده باشد، تمام شده و با موفقیت انجام شده باشد، یا با تابع {{domxref("IDBTransaction.abort()")}} لغو شده باشد، `null` است.
- {{domxref("IDBTransaction.mode")}} {{ReadOnlyInline}}
  - : حالت دسترسی ایزوله به داده‌ها در فروشگاه‌های اشیاء در محدوده تراکنش. مقدار پیش‌فرض `readonly` است.
- {{domxref("IDBTransaction.objectStoreNames")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMStringList")}} از نام‌های اشیاء {{domxref("IDBObjectStore")}} مرتبط با تراکنش را برمی‌گرداند.

## روش‌های نمونه

ارث‌بری از: {{domxref("EventTarget")}}

- {{domxref("IDBTransaction.abort()")}}
  - : تمام تغییرات روی اشیاء پایگاه‌داده مرتبط با این تراکنش را برمی‌گرداند. اگر این تراکنش لغو یا تکمیل شده باشد، این روش یک رویداد خطا فعال می‌کند.
- {{domxref("IDBTransaction.objectStore()")}}
  - : یک شیء {{domxref("IDBObjectStore")}} را برمی‌گرداند که نمایانگر یک فروشگاه اشیاء در محدوده این تراکنش است.
- {{domxref("IDBTransaction.commit()")}}
  - : برای یک تراکنش فعال، تراکنش را انجام می‌دهد. توجه داشته باشید که معمولاً نیازی به فراخوانی این روش نیست - یک تراکنش به‌طور خودکار زمانی انجام می‌شود که تمام درخواست‌های معلق برآورده شده و هیچ درخواست جدیدی انجام نشده باشد. `commit()` می‌تواند برای شروع فرآیند انجام بدون انتظار برای ارسال رویدادهای درخواست‌های معلق استفاده شود.

## رویدادها

به این رویدادها با استفاده از `addEventListener()` یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید.

- [`abort`](/en-US/docs/Web/API/IDBTransaction/abort_event)
  - : رویدادی که وقتی تراکنش `IndexedDB` لغو می‌شود فعال می‌شود.
    همچنین از طریق ویژگی `onabort` در دسترس است؛ این رویداد به {{domxref("IDBDatabase")}} منتقل می‌شود.
- [`complete`](/en-US/docs/Web/API/IDBTransaction/complete_event)
  - : رویدادی که وقتی تراکنش با موفقیت به پایان می‌رسد فعال می‌شود.
    همچنین از طریق ویژگی `oncomplete` در دسترس است.
- [`error`](/en-US/docs/Web/API/IDBTransaction/error_event)
  - : رویدادی که وقتی یک درخواست خطا برمی‌گرداند و رویداد به شیء اتصال ({{domxref("IDBDatabase")}}) منتقل می‌شود فعال می‌شود.
    همچنین از طریق ویژگی `onerror` در دسترس است.

## ثابت‌های حالت

{{Deprecated_Header}}

> [!WARNING]
> این ثابت‌ها دیگر در دسترس نیستند - در Gecko 25 حذف شدند. باید مستقیماً از ثابت‌های رشته‌ای استفاده کنید. ([بگ فایرفاکس 888598](https://bugzil.la/888598))

تراکنش‌ها می‌توانند یکی از سه حالت زیر را داشته باشند:

<table class="standard-table">
  <thead>
    <tr>
      <th scope="col">ثابت</th>
      <th scope="col">مقدار</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code><a>READ_ONLY</a></code>
      </td>
      <td>"readonly" (0 در Chrome)</td>
      <td><p>اجازه خواندن داده را می‌دهد اما تغییر آن را نه.</p></td>
    </tr>
    <tr>
      <td>
        <code><a>READ_WRITE</a></code>
      </td>
      <td>"readwrite" (1 در Chrome)</td>
      <td>
        اجازه خواندن و نوشتن داده در فروشگاه‌های داده موجود برای تغییر را می‌دهد.
      </td>
    </tr>
    <tr>
      <td>
        <code><a>VERSION_CHANGE</a></code>
      </td>
      <td>"versionchange" (2 در Chrome)</td>
      <td>
        اجازه انجام هر عملیاتی را می‌دهد، از جمله عملیاتی که فروشگاه‌های اشیاء و ایندکس‌ها را حذف و ایجاد می‌کنند. تراکنش‌های این حالت نمی‌توانند همزمان با سایر تراکنش‌ها اجرا شوند. تراکنش‌های این حالت به عنوان "تراکنش‌های ارتقا" شناخته می‌شوند.
      </td>
    </tr>
  </tbody>
</table>

اگرچه این ثابت‌ها اکنون منسوخ شده‌اند، هنوز هم می‌توانید در صورت نیاز برای سازگاری با نسخه‌های قدیمی از آنها استفاده کنید. باید کد را به‌گونه‌ای بنویسید که در صورت عدم وجود شیء، به‌طور تدافعی عمل کند:

```js
const myIDBTransaction = window.IDBTransaction ||
  window.webkitIDBTransaction || { READ_WRITE: "readwrite" };
```

## مثال‌ها

در قطعه کد زیر، یک تراکنش خواندن/نوشتن روی پایگاه‌داده خود باز می‌کنیم و داده‌هایی را به یک فروشگاه اشیاء اضافه می‌کنیم. همچنین به توابع متصل به مدیریت‌کننده‌های رویداد تراکنش توجه کنید که نتیجه باز شدن تراکنش را در صورت موفقیت یا شکست گزارش می‌دهند. برای یک مثال کامل کار، به برنامه [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.getElementById("notifications");

// یک نمونه از شیء db برای ذخیره داده‌های IDB
let db;

// بیایید پایگاه‌داده را باز کنیم
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "پایگاه‌داده مقداردهی اولیه شد.";

  // نتیجه باز کردن پایگاه‌داده را در متغیر db ذخیره کنید
  // این متغیر در ادامه بسیار استفاده می‌شود
  db = DBOpenRequest.result;

  // داده را به پایگاه‌داده اضافه کنید
  addData();
};

function addData() {
  // یک شیء جدید برای درج در IDB ایجاد کنید
  const newItem = [
    {
      taskTitle: "Walk dog",
      hours: 19,
      minutes: 30,
      day: 24,
      month: "December",
      year: 2013,
      notified: "no",
    },
  ];

  // یک تراکنش خواندن/نوشتن db باز کنید، آماده برای اضافه کردن داده
  const transaction = db.transaction(["toDoList"], "readwrite");

  // موفقیت باز شدن تراکنش را گزارش دهید
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "تراکنش تکمیل شد: تغییر پایگاه‌داده به پایان رسید.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "تراکنش به دلیل خطا باز نشد. موارد تکراری مجاز نیستند.";
  };

  // یک فروشگاه اشیاء روی تراکنش ایجاد کنید
  const objectStore = transaction.objectStore("toDoList");

  // شیء newItem را به فروشگاه اشیاء اضافه کنید
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // موفقیت درخواست را گزارش دهید (این به معنای ذخیره موفقیت‌آمیز آیتم در DB نیست - برای آن به transaction.oncomplete نیاز دارید)
    note.appendChild(document.createElement("li")).textContent =
      "درخواست موفقیت‌آمیز بود.";
  };
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- شروع تراکنش‌ها: {{domxref("IDBDatabase")}}
- تنظیم بازه کلیدها: {{domxref("IDBKeyRange")}}
- بازیابی و ایجاد تغییرات در داده‌های خود: {{domxref("IDBObjectStore")}}
- استفاده از نشانگرها: {{domxref("IDBCursor")}}
- مثال مرجع: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([مشاهده مثال زنده](https://mdn.github.io/dom-examples/to-do-notifications/)).