---
title: "NodeList"
---

---
title: NodeList
slug: Web/API/NodeList
page-type: web-api-interface
browser-compat: api.NodeList
---

{{APIRef("DOM")}}

**`NodeList`** اشیایی هستند که مجموعه‌ای از [گره‌ها](/en-US/docs/Web/API/Node) را در بر می‌گیرند و معمولاً توسط ویژگی‌هایی مانند {{domxref("Node.childNodes")}} و روش‌هایی مانند {{domxref("document.querySelectorAll()")}} بازگردانده می‌شوند.

این رابط در اصل [تلاشی برای ساخت یک فهرست تغییرناپذیر](https://stackoverflow.com/questions/74630989/why-use-domstringlist-rather-than-an-array/74641156#74641156) بود و تنها برای اینکه کدهایی که قبلاً از آن استفاده می‌کنند دچار مشکل نشوند، همچنان پشتیبانی می‌شود. APIهای مدرن ساختارهای فهرستی را با استفاده از نوع‌های مبتنی بر [آرایه‌های](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) جاوااسکریپت نمایش می‌دهند؛ بنابراین بسیاری از روش‌های آرایه را در دسترس قرار می‌دهند و در عین حال معناشناسی بیشتری را بر نحوه استفاده از آن‌ها اعمال می‌کنند (مانند فقط‌خواندنی کردن آیتم‌هایشان).

این دلایل تاریخی به این معنا نیستند که شما به‌عنوان توسعه‌دهنده باید از `NodeList` اجتناب کنید. شما خودتان اشیاء `NodeList` را نمی‌سازید، بلکه آن‌ها را از APIهایی مانند {{domxref("Document.querySelectorAll()")}} دریافت می‌کنید و این APIها منسوخ (deprecated) نشده‌اند. با این حال، مراقب تفاوت‌های معنایی آن با یک آرایه واقعی باشید.

اگرچه `NodeList` یک `Array` نیست، می‌توان با `forEach()` روی آن پیمایش کرد. همچنین می‌توان آن را با {{jsxref("Array.from()")}} به یک `Array` واقعی تبدیل کرد.

## NodeList های زنده در برابر ایستا

اگرچه هر دو به‌عنوان اشیاء `NodeList` در نظر گرفته می‌شوند، دو نوع NodeList وجود دارد: _زنده_ (_live_) و _ایستا_ (_static_).

در بیشتر موارد، `NodeList` از نوع _زنده_ است، یعنی تغییرات DOM به‌طور خودکار مجموعه را به‌روزرسانی می‌کنند.

برای مثال، {{domxref("Node.childNodes")}} زنده است:

```js
const parent = document.getElementById("parent");
let childNodes = parent.childNodes;
console.log(childNodes.length); // let's assume "2"
parent.appendChild(document.createElement("div"));
console.log(childNodes.length); // outputs "3"
```

در موارد دیگر، `NodeList` از نوع _ایستا_ است؛ یعنی هر تغییری در DOM بر محتوای مجموعه تأثیری نمی‌گذارد. روش پرکاربرد {{domxref("document.querySelectorAll()")}} تنها API است که یک `NodeList` _ایستا_ بازمی‌گرداند.

بهتر است این تفاوت را هنگام انتخاب روش پیمایش آیتم‌های `NodeList` و اینکه آیا باید `length` فهرست را کش کنید، در نظر داشته باشید.

## ویژگی‌های نمونه

- {{domxref("NodeList.length")}} {{ReadOnlyInline}}
  - : تعداد گره‌های موجود در `NodeList`.

## روش‌های نمونه

- {{domxref("NodeList.item()")}}
  - : یک آیتم از فهرست را بر اساس اندیس آن بازمی‌گرداند، یا اگر اندیس خارج از محدوده باشد `null` برمی‌گرداند.

    این روش جایگزینی برای دسترسی به `nodeList[i]` است (که در صورت خارج بودن `i` از محدوده، `undefined` بازمی‌گرداند). این روش عمدتاً برای پیاده‌سازی‌های DOM که مبتنی بر جاوااسکریپت نیستند مفید است.

- {{domxref("NodeList.entries()")}}
  - : یک {{jsxref("Iteration_protocols","iterator")}} برمی‌گرداند که به کد اجازه می‌دهد از تمام جفت‌های کلید/مقدار موجود در مجموعه عبور کند. (در این حالت، کلیدها اعداد صحیح شروع‌شونده از `0` و مقدارها گره‌ها هستند.)

- {{domxref("NodeList.forEach()")}}
  - : یک تابع داده‌شده را یک‌بار برای هر عنصر `NodeList` اجرا می‌کند و آن عنصر را به‌عنوان آرگومان به تابع می‌دهد.

- {{domxref("NodeList.keys()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator")}} برمی‌گرداند که به کد اجازه می‌دهد از تمام کلیدهای جفت‌های کلید/مقدار موجود در مجموعه عبور کند. (در این حالت، کلیدها اعداد صحیح شروع‌شونده از `0` هستند.)

- {{domxref("NodeList.values()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator")}} برمی‌گرداند که به کد اجازه می‌دهد از تمام مقدارها (گره‌ها)ی جفت‌های کلید/مقدار موجود در مجموعه عبور کند.

## مثال

می‌توان با استفاده از حلقه [for](/en-US/docs/Web/JavaScript/Reference/Statements/for) روی آیتم‌های یک `NodeList` پیمایش کرد:

```js
for (let i = 0; i < myNodeList.length; i++) {
  let item = myNodeList[i];
}
```

**برای شمارش آیتم‌های `NodeList` از [`for...in`](/en-US/docs/Web/JavaScript/Reference/Statements/for...in) استفاده نکنید**، زیرا این حلقه ویژگی‌های `length` و `item` را نیز _شمارش_ می‌کند و اگر اسکریپت شما فرض کند که فقط با اشیاء {{domxref("element")}} سروکار دارد، خطا ایجاد می‌کند. همچنین، `for...in` ترتیب خاصی را برای بازدید از ویژگی‌ها تضمین نمی‌کند.

[`for...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) به‌درستی روی اشیاء `NodeList` پیمایش می‌کند:

```js
const list = document.querySelectorAll("input[type=checkbox]");
for (const checkbox of list) {
  checkbox.checked = true;
}
```

مرورگرها همچنین از روش iterator یعنی {{domxref("NodeList.forEach()", "forEach()")}} و نیز {{domxref("NodeList.entries()", "entries()")}}، {{domxref("NodeList.values()", "values()")}} و {{domxref("NodeList.keys()", "keys()")}} پشتیبانی می‌کنند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}