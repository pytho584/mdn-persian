---
title: "Checking when a deadline is due"
---

---
title: Checking when a deadline is due
slug: Web/API/IndexedDB_API/Checking_when_a_deadline_is_due
page-type: guide
---

{{DefaultAPISidebar("IndexedDB")}}

در این مقاله، به بررسی یک مثال پیچیده می‌پردازیم که شامل بررسی زمان و تاریخ فعلی در برابر یک مهلت ذخیره‌شده از طریق IndexedDB است. پیچیدگی اصلی اینجا، بررسی اطلاعات مهلت ذخیره‌شده (ماه، ساعت، روز و ...) در برابر زمان و تاریخ فعلی است که از یک شیء Date گرفته می‌شود.

![A screenshot of the sample app. A red main title saying To do app, a test to-do item, and a red form for users to enter new tasks](to-do-app.png)

برنامهٔ مثال اصلی که در این مقاله به آن اشاره می‌کنیم، **To-do list notifications** است؛ یک برنامهٔ سادهٔ فهرست کارها که عنوان کارها و زمان و تاریخ مهلت‌ها را از طریق IndexedDB ذخیره می‌کند و وقتی تاریخ‌های مهلت فرا می‌رسند، از طریق APIهای Notification و Vibration به کاربران اعلان می‌دهد. می‌توانید برنامهٔ To-do list notifications را از GitHub دانلود کنید و با کد منبع آن کار کنید، یا [برنامهٔ در حال اجرا را به‌صورت زنده ببینید](https://mdn.github.io/dom-examples/to-do-notifications/).

## مسئلهٔ اصلی

در برنامهٔ فهرست کارها، ابتدا می‌خواستیم اطلاعات زمان و تاریخ را در قالبی ثبت کنیم که هم برای ماشین قابل‌خواندن باشد و هم هنگام نمایش برای انسان قابل‌درک؛ سپس بررسی کنیم که آیا هر زمان و تاریخ در لحظهٔ فعلی رخ می‌دهد یا نه. به‌طور اساسی، می‌خواهیم بدانیم اکنون زمان و تاریخ چیست و سپس هر رویداد ذخیره‌شده را بررسی کنیم تا ببینیم آیا هرکدام از مهلت‌هایشان با زمان و تاریخ فعلی مطابقت دارد یا نه. اگر مطابقت داشت، می‌خواهیم با نوعی اعلان به کاربر اطلاع دهیم.

اگر فقط دو شیء Date را با هم مقایسه می‌کردیم، کار آسان بود؛ اما طبیعتاً کاربران نمی‌خواهند اطلاعات مهلت را در قالبی وارد کنند که جاوااسکریپت می‌فهمد. تاریخ‌های قابل‌خواندن برای انسان کاملاً متفاوت‌اند و بازنمایی‌های مختلفی دارند.

### ثبت اطلاعات تاریخ

برای ارائهٔ تجربهٔ کاربری مناسب در دستگاه‌های همراه و کاهش ابهام‌ها، تصمیم گرفتم یک فرم HTML با این بخش‌ها بسازم:

![The form of the to-do app, containing fields to fill in a task title, and minute, hour, day, month and year values for the deadline.](to-do-app-form2.png)

- یک فیلد متنی برای وارد کردن عنوان کار در فهرست کارها. این بخش اجتناب‌ناپذیرترین بخش تایپ کاربر است.
- فیلدهای عددی برای بخش ساعت و دقیقهٔ مهلت. در مرورگرهایی که از `type="number"` پشتیبانی می‌کنند، یک انتخابگر عددی کوچک با فلش‌های بالا و پایین می‌بینید. در پلتفرم‌های همراه معمولاً یک صفحه‌کلید عددی برای وارد کردن داده دریافت می‌کنید که مفید است. در بقیهٔ مرورگرها فقط یک فیلد متنی استاندارد می‌بینید که کافی است.
- عنصرهای {{HTMLElement("select")}} برای وارد کردن روز، ماه و سال مهلت. از آنجا که این مقادیر مبهم‌ترین ورودی‌ها برای کاربران هستند (مثلاً 7، sunday، sun؟ یا 04، 4، April، Apr؟ یا 2013، '13، 13؟)، تصمیم گرفتم بهترین راه‌حل این باشد که به آنها یک گزینه برای انتخاب بدهیم؛ این کار همچنین تایپ آزاردهنده را برای کاربران همراه کاهش می‌دهد. روزها به‌صورت عددیِ روزِ ماه، ماه‌ها به‌صورت نام کامل ماه، و سال‌ها از سال فعلی تا ۱۲ سال بعد پر می‌شوند.

در هنگام راه‌اندازی برنامه، فهرست کشویی سال را پر می‌کنیم و سال فعلی را برای استفاده‌های بعدی ذخیره می‌کنیم:

```js
const currentYear = new Date().getFullYear();
for (let i = 0; i <= 12; i++) {
  const option = document.createElement("option");
  const yearValue = currentYear + i;
  option.value = yearValue;
  option.textContent = yearValue;
  year.appendChild(option);
}
year.value = currentYear;
```

وقتی دکمهٔ ارسال فرم فشرده می‌شود، تابع `addData()` را اجرا می‌کنیم که این‌گونه شروع می‌شود:

```js
function addData(e) {
  e.preventDefault();

  if (
    !title.value ||
    !hours.value ||
    !minutes.value ||
    !day.value ||
    !month.value ||
    !year.value
  ) {
    note.appendChild(document.createElement("li")).textContent =
      "Data not submitted — form incomplete.";
    return;
  }
  // ...
}
```

در این بخش، بررسی می‌کنیم که آیا همهٔ فیلدهای فرم پر شده‌اند یا نه. اگر پر نشده باشند، یک پیام در پنل اعلان‌های توسعه‌دهنده (سمت چپ پایین رابط کاربری برنامه) قرار می‌دهیم تا به کاربر بگوید چه اتفاقی افتاده است و از تابع خارج می‌شویم. این مرحله عمدتاً برای مرورگرهایی است که اعتبارسنجی فرم HTML را پشتیبانی نمی‌کنند (من در HTML خود از ویژگی `required` استفاده کرده‌ام تا در مرورگرهایی که پشتیبانی می‌کنند، اعتبارسنجی اجباری شود).

```js
function addData(e) {
  // ...
  const newItem = [
    {
      taskTitle: title.value,
      hours: hours.value,
      minutes: minutes.value,
      day: day.value,
      month: month.value,
      year: year.value,
      notified: "no",
    },
  ];

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // report on the success of opening the transaction
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction opened for task addition.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction not opened due to error. Duplicate items not allowed.";
  };

  // create an object store on the transaction
  const objectStore = transaction.objectStore("toDoList");

  // add our newItem object to the object store
  const request = objectStore.add(newItem[0]);

  // ...
}
```

در این بخش، یک شیء به نام `newItem` می‌سازیم که داده‌ها را در قالب لازم برای درج در پایگاه داده ذخیره می‌کند. چند خط بعد تراکنش پایگاه داده را باز می‌کنند و پیام‌هایی را برای اطلاع کاربر از موفقیت یا شکست این کار فراهم می‌کنند. سپس یک `objectStore` ساخته می‌شود که آیتم جدید به آن اضافه می‌شود. ویژگی `notified` در شیء داده نشان می‌دهد که مهلت آیتم فهرست کارها هنوز فرا نرسیده و اعلان آن ارسال نشده است — بعداً بیشتر دربارهٔ این توضیح می‌دهیم!

> [!NOTE]
> متغیر `db` ارجاعی به نمونهٔ پایگاه دادهٔ IndexedDB نگهداری می‌کند؛ سپس می‌توانیم از ویژگی‌های مختلف این متغیر برای دستکاری داده‌ها استفاده کنیم.

```js
function addData(e) {
  // ...
  request.onsuccess = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "New item added to database.";

    title.value = "";
    hours.value = null;
    minutes.value = null;
    day.value = "01";
    month.value = "January";
    year.value = currentYear;
  };
  // update the display of data to show the newly added item, by running displayData() again.
  displayData();
}
```

بخش بعدی یک پیام لاگ می‌سازد که افزودن آیتم جدید موفق بوده است و فرم را بازنشانی می‌کند تا برای وارد کردن کار بعدی آماده باشد. توجه کنید که فیلد سال به `currentYear` بازنشانی می‌شود؛ مقداری که هنگام راه‌اندازی برنامه تنظیم شده است. در نهایت، تابع `displayData()` را اجرا می‌کنیم که نمایش داده‌ها را در برنامه به‌روزرسانی می‌کند تا کار تازه‌واردشده نشان داده شود.

### بررسی اینکه آیا مهلتی فرا رسیده است

در این مرحله داده‌های ما در پایگاه داده هستند؛ حالا می‌خواهیم بررسی کنیم که آیا هر یک از مهلت‌ها فرا رسیده‌اند یا نه. این کار با تابع `checkDeadlines()` انجام می‌شود:

```js
function checkDeadlines() {
  const now = new Date();
  const minuteCheck = now.getMinutes();
  const hourCheck = now.getHours();
  const dayCheck = now.getDate();
  const monthCheck = now.getMonth();
  const yearCheck = now.getFullYear();
  // ...
}
```

ابتدا با ایجاد یک شیء خالی `Date`، تاریخ و زمان فعلی را می‌گیریم. شیء `Date` روش‌های متعددی برای استخراج بخش‌های مختلف تاریخ و زمان درون خود دارد. در اینجا دقیقه‌های فعلی (یک مقدار عددی ساده می‌دهد)، ساعت فعلی (یک مقدار عددی ساده می‌دهد)، روز ماه (`getDate()` برای این کار لازم است، چون `getDay()` روز هفته را از ۰ تا ۶ برمی‌گرداند)، ماه (عددی از ۰ تا ۱۱ برمی‌گرداند، به زیر مراجعه کنید) و سال را می‌گیریم (`getFullYear()` لازم است؛ `getYear()` منسوخ شده است و مقدار عجیبی برمی‌گرداند که به درد هیچ‌کس نمی‌خورد!)

```js
function checkDeadlines() {
  // ...
  const objectStore = db
    .transaction(["toDoList"], "readwrite")
    .objectStore("toDoList");

  objectStore.openCursor().onsuccess = (event) => {
    const cursor = event.target.result;
    let monthNumber;

    if (!cursor) return;
    // ...
    cursor.continue();
  };
}
```

سپس یک `objectStore` دیگر IndexedDB می‌سازیم و با استفاده از متد `openCursor()` یک نشانگر (cursor) باز می‌کنیم که اساساً راهی در IndexedDB برای پیمایش همهٔ آیتم‌های موجود در فروشگاه است. سپس تا زمانی که آیتم معتبری در نشانگر باقی مانده باشد، از میان همهٔ آیتم‌های نشانگر حلقه می‌زنیم. آخرین خط تابع، نشانگر را به جلو می‌برد و باعث می‌شود سازوکار بررسی مهلت بالا برای کار بعدی ذخیره‌شده در IndexedDB اجرا شود.

حالا شروع به پر کردن کد در کنترل‌کنندهٔ `onsuccess` برای بررسی مهلت‌ها می‌کنیم.

```js
const { hours, minutes, day, month, year, notified, taskTitle } = cursor.value;
const monthNumber = MONTHS.indexOf(month);
if (monthNumber === -1) throw new Error("Incorrect month entered in database.");
```

اولین کاری که انجام می‌دهیم این است که نام ماه‌های ذخیره‌شده در پایگاه داده را به شمارهٔ ماهی تبدیل کنیم که جاوااسکریپت آن را بفهمد. همان‌طور که قبلاً دیدیم، شیء `Date` در جاوااسکریپت مقدار ماه را به‌صورت عددی بین ۰ و ۱۱ می‌سازد.

حالا که بخش‌های زمان و تاریخ فعلی که می‌خواهیم با مقادیر ذخیره‌شده در IndexedDB مقایسه کنیم، همگی آماده شده‌اند، وقت انجام بررسی‌هاست. می‌خواهیم همهٔ مقادیر مطابقت داشته باشند تا به کاربر نوعی اعلان نشان دهیم که مهلتش فرا رسیده است. اگر همهٔ بررسی‌ها مطابقت داشتند، تابع `createNotification()` را اجرا می‌کنیم تا اعلانی به کاربر ارائه دهد.

```js
let matched = parseInt(hours, 10) === hourCheck;
matched &&= parseInt(minutes, 10) === minuteCheck;
matched &&= parseInt(day, 10) === dayCheck;
matched &&= monthNumber === monthCheck;
matched &&= parseInt(year, 10) === yearCheck;
if (matched && notified === "no") {
  // If the numbers all do match, run the createNotification() function to create a system notification
  // but only if the permission is set
  if (Notification.permission === "granted") {
    createNotification(taskTitle);
  }
}
```

بررسی `notified === "no"` برای این طراحی شده است که مطمئن شوید برای هر آیتم فهرست کارها فقط یک اعلان دریافت می‌کنید. وقتی برای هر شیء آیتم یک اعلان فعال می‌شود، ویژگی `notification` آن به `"yes"` تنظیم می‌شود؛ بنابراین این بررسی در تکرار بعدی موفق نخواهد بود. این کار از طریق کد زیر درون تابع `createNotification()` انجام می‌شود (برای توضیح بیشتر، [استفاده از IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB) را بخوانید):

```js
// now we need to update the value of notified to "yes" in this particular data object, so the
// notification won't be set off on it again

// first open up a transaction as usual
const objectStore = db
  .transaction(["toDoList"], "readwrite")
  .objectStore("toDoList");

// Get the to-do list object that has this title as its title
const objectStoreTitleRequest = objectStore.get(title);

objectStoreTitleRequest.onsuccess = () => {
  // Grab the data object returned as the result
  const data = objectStoreTitleRequest.result;

  // Update the notified value in the object to 'yes'
  data.notified = "yes";

  // Create another request that inserts the item back into the database
  const updateTitleRequest = objectStore.put(data);

  // When this new request succeeds, run the displayData() function again to update the display
  updateTitleRequest.onsuccess = () => {
    displayData();
  };
};
```

### ادامهٔ بررسی!

البته اجرای یک‌بارهٔ تابع بررسی مهلت بالا فایده‌ای ندارد! می‌خواهیم دائماً همهٔ مهلت‌ها را بررسی کنیم تا ببینیم آیا هر یک از آنها فرا می‌رسند یا نه. برای این کار، از `setInterval()` استفاده می‌کنیم تا تابع `checkDeadlines()` را هر ثانیه یک‌بار اجرا کند:

```js
setInterval(checkDeadlines, 1000);
```