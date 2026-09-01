---
title: "EventTarget: addEventListener() method"
short-title: addEventListener()
slug: Web/API/EventTarget/addEventListener
page-type: web-api-instance-method
browser-compat: api.EventTarget.addEventListener
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

متد **`addEventListener()`** از رابط {{domxref("EventTarget")}} تابعی را تنظیم می‌کند که هر زمان رویداد مشخص‌شده به هدف (target) تحویل داده شود، فراخوانی خواهد شد.

اهداف معمول عبارت‌اند از {{domxref("Element")}}، فرزندان آن، {{domxref("Document")}} و {{domxref("Window")}}؛ اما هدف می‌تواند هر شیءای باشد که از رویدادها پشتیبانی می‌کند (مانند {{domxref("IDBRequest")}}).

> [!NOTE]
> روش `addEventListener()` روش _پیشنهادشده_ برای ثبت یک شنونده رویداد است. مزایای آن به شرح زیر است:
>
> - امکان افزودن بیش از یک کنترل‌کننده برای یک رویداد را فراهم می‌کند. این ویژگی به‌ویژه برای کتابخانه‌ها، ماژول‌های جاوااسکریپت یا هر نوع کد دیگری که باید با سایر کتابخانه‌ها یا افزونه‌ها به‌خوبی کار کند، مفید است.
> - برخلاف استفاده از یک ویژگی `onXYZ`، کنترل دقیق‌تری روی فازی که شنونده فعال می‌شود (capturing در برابر bubbling) به شما می‌دهد.
> - روی هر هدف رویدادی کار می‌کند، نه فقط عناصر HTML یا SVG.

روش `addEventListener()` با افزودن یک تابع، یا یک شیء که تابع `handleEvent()` را پیاده‌سازی می‌کند، به فهرست شنوندگان رویداد برای نوع رویداد مشخص‌شده روی {{domxref("EventTarget")}} که بر روی آن فراخوانی شده است، کار می‌کند. اگر تابع یا شیء از قبل در فهرست شنوندگان رویداد برای این هدف وجود داشته باشد، تابع یا شیء بار دوم اضافه نمی‌شود.

> [!NOTE]
> اگر یک تابع بی‌نام خاص در فهرست شنوندگان رویداد ثبت‌شده برای یک هدف مشخص وجود داشته باشد و بعداً در کد، تابع بی‌نام یکسانی در یک فراخوانی `addEventListener` داده شود، تابع دوم _نیز_ به فهرست شنوندگان رویداد برای آن هدف اضافه خواهد شد.
>
> در واقع، توابع بی‌نام حتی اگر با استفاده از _همان_ کد منبعِ بدون تغییر و به‌طور مکرر تعریف شوند، یکسان نیستند، **حتی اگر در یک حلقه باشند**.
>
> تعریف مکرر همان تابع بدون نام در چنین مواردی می‌تواند مشکل‌ساز باشد. (به [مشکلات حافظه](#memory_issues) در پایین مراجعه کنید.)

اگر یک شنونده رویداد از داخل شنونده دیگری — یعنی در حین پردازش رویداد — به یک {{domxref("EventTarget")}} اضافه شود، آن رویداد شنونده جدید را فعال نخواهد کرد. با این حال، شنونده جدید ممکن است در مرحله بعدی جریان رویداد، مانند فاز bubbling، فعال شود.

## نحو

```js-nolint
addEventListener(type, listener)
addEventListener(type, listener, options)
addEventListener(type, listener, useCapture)
```

### پارامترها

- `type`
  - : رشته‌ای است که به بزرگی/کوچکی حروف حساس است و [نوع رویداد](/en-US/docs/Web/API/Document_Object_Model/Events) موردنظر برای شنیدن را نشان می‌دهد.
- `listener`
  - : شیءای که هنگام رخ دادن رویدادی از نوع مشخص‌شده، اعلان دریافت می‌کند (شیءای که رابط {{domxref("Event")}} را پیاده‌سازی می‌کند). این مقدار باید `null`، یک شیء با متد `handleEvent()`، یا یک [تابع](/en-US/docs/Web/JavaScript/Guide/Functions) جاوااسکریپت باشد. برای جزئیات بیشتر درباره خود تابع بازخوانی (callback)، به [تابع بازخوانی شنونده رویداد](#the_event_listener_callback) مراجعه کنید.
- `options` {{optional_inline}}
  - : شیءای که ویژگی‌های شنونده رویداد را مشخص می‌کند. گزینه‌های موجود عبارت‌اند از:
    - `capture` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد رویدادهای این نوع پیش از ارسال به هر `EventTarget` پایین‌تر در درخت DOM، به `listener` ثبت‌شده ارسال خواهند شد. اگر مشخص نشود، پیش‌فرض `false` است.
    - `once` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد `listener` حداکثر یک بار پس از افزوده‌شدن فراخوانی شود. اگر `true` باشد، `listener` پس از فراخوانی به‌طور خودکار حذف می‌شود. اگر مشخص نشود، پیش‌فرض `false` است.
    - `passive` {{optional_inline}}
      - : یک مقدار بولی که اگر `true` باشد، نشان می‌دهد تابع تعیین‌شده توسط `listener` هرگز {{domxref("Event.preventDefault", "preventDefault()")}} را فراخوانی نخواهد کرد. اگر یک شنونده غیرفعال (passive) تابع `preventDefault()` را فراخوانی کند، هیچ اتفاقی نمی‌افتد و ممکن است یک هشدار در کنسول تولید شود.

        اگر این گزینه مشخص نشود، پیش‌فرض آن `false` است — به‌جز در مرورگرهای غیر از Safari که برای رویدادهای {{domxref("Element/wheel_event", "wheel")}}، {{domxref("Element/mousewheel_event", "mousewheel")}}، {{domxref("Element/touchstart_event", "touchstart")}} و {{domxref("Element/touchmove_event", "touchmove")}} مقدار پیش‌فرض `true` است. برای اطلاعات بیشتر به [استفاده از شنوندگان غیرفعال](#using_passive_listeners) مراجعه کنید.
    - `signal` {{optional_inline}}
      - : یک {{domxref("AbortSignal")}}. زمانی که متد {{domxref("AbortController/abort()", "abort()")}} از {{domxref("AbortController")}} (که مالک `AbortSignal` است) فراخوانی شود، شنونده حذف خواهد شد. اگر مشخص نشود، هیچ `AbortSignal` به شنونده مرتبط نمی‌شود.
- `useCapture` {{optional_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا رویدادهای این نوع به `listener` ثبت‌شده _قبل از_ ارسال به هر `EventTarget` پایین‌تر در درخت DOM ارسال می‌شوند یا خیر. رویدادهایی که در درخت به سمت بالا حباب می‌زنند، شنونده‌ای را که برای استفاده از capture تعیین شده است فعال نمی‌کنند. رویدادهای bubbling و capturing دو روش انتشار رویدادهایی هستند که در یک عنصر تودرتو درون عنصر دیگر رخ می‌دهند، زمانی که هر دو عنصر یک کنترل‌کننده برای آن رویداد ثبت کرده باشند. حالت انتشار رویداد تعیین می‌کند که عناصر به چه ترتیبی رویداد را دریافت کنند. برای توضیح دقیق به [مشخصات DOM](https://dom.spec.whatwg.org/#introduction-to-dom-events) و [ترتیب رویداد در جاوااسکریپت](https://www.quirksmode.org/js/events_order.html#link4) مراجعه کنید. اگر مشخص نشود، `useCapture` به‌طور پیش‌فرض `false` است.

    > [!NOTE]
    > برای شنوندگان رویدادی که به هدف رویداد متصل شده‌اند، رویداد در فاز هدف (target phase) قرار دارد، نه در فازهای capturing و bubbling.
    > شنوندگان رویداد در فاز _capturing_ قبل از شنوندگان رویداد در فازهای هدف و حباب فراخوانی می‌شوند.

- `wantsUntrusted` {{optional_inline}} {{non-standard_inline}}
  - : پارامتری مخصوص Firefox (Gecko). اگر `true` باشد، شنونده رویدادهای مصنوعی (synthetic) ارسال‌شده توسط محتوای وب را دریافت می‌کند (پیش‌فرض برای {{glossary("chrome")}} مرورگر `false` و برای صفحات وب معمولی `true` است). این پارامتر برای کدهایی که در افزونه‌ها و همچنین خود مرورگر استفاده می‌شوند مفید است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## نکات استفاده

### تابع بازخوانی شنونده رویداد

شنونده رویداد می‌تواند یا به‌صورت یک تابع بازخوانی (callback) مشخص شود یا به‌صورت یک شیء که متد `handleEvent()` آن به‌عنوان تابع بازخوانی عمل می‌کند.

خود تابع بازخوانی همان پارامترها و مقدار بازگشتی متد `handleEvent()` را دارد؛ یعنی تابع بازخوانی یک پارامتر واحد می‌پذیرد: یک شیء بر اساس {{domxref("Event")}} که رویداد رخ‌داده را توصیف می‌کند، و هیچ مقداری برنمی‌گرداند.

به‌عنوان مثال، یک تابع بازخوانی کنترل‌کننده رویداد که می‌تواند برای مدیریت هر دو رویداد {{domxref("Element/fullscreenchange_event", "fullscreenchange")}} و {{domxref("Element/fullscreenerror_event", "fullscreenerror")}} استفاده شود، می‌تواند به شکل زیر باشد:

```js
function handleEvent(event) {
  if (event.type === "fullscreenchange") {
    /* handle a full screen toggle */
  } else {
    /* handle a full screen toggle error */
  }
}
```

### مقدار "this" درون کنترل‌کننده

اغلب مطلوب است به عنصری که کنترل‌کننده رویداد روی آن اجرا شده است ارجاع داده شود، مثلاً هنگام استفاده از یک کنترل‌کننده عمومی برای مجموعه‌ای از عناصر مشابه.

هنگام اتصال یک تابع کنترل‌کننده به یک عنصر با استفاده از `addEventListener()`، مقدار {{jsxref("this")}} درون کنترل‌کننده ارجاعی به همان عنصر خواهد بود. این مقدار با مقدار ویژگی `currentTarget` آرگومان رویدادی که به کنترل‌کننده ارسال می‌شود یکسان خواهد بود.

```js
myElement.addEventListener("click", function (e) {
  console.log(this.className); // logs the className of myElement
  console.log(e.currentTarget === this); // logs `true`
});
```

به‌عنوان یادآوری، [توابع پیکانی زمینه `this` مخصوص به خود را ندارند](/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#cannot_be_used_as_methods).

```js
myElement.addEventListener("click", (e) => {
  console.log(this.className); // WARNING: `this` is not `myElement`
  console.log(e.currentTarget === this); // logs `false`
});
```

اگر یک کنترل‌کننده رویداد (مثلاً {{domxref("Element.click_event", "onclick")}}) روی یک عنصر در کد HTML مشخص شده باشد، کد جاوااسکریپت موجود در مقدار ویژگی عملاً در یک تابع کنترل‌کننده قرار می‌گیرد که مقدار `this` را به‌گونه‌ای سازگار با `addEventListener()` می‌بندد؛ هر occurrence از `this` درون کد، ارجاعی به عنصر را نشان می‌دهد.

```html
<table id="my-table" onclick="console.log(this.id);">
  <!-- `this` refers to the table; logs 'my-table' -->
  …
</table>
```

توجه کنید که مقدار `this` درون یک تابع، که توسط کد موجود در مقدار ویژگی _فراخوانی می‌شود_، طبق [قوانین استاندارد](/en-US/docs/Web/JavaScript/Reference/Operators/this) رفتار می‌کند. این موضوع در مثال زیر نشان داده شده است:

```html
<script>
  function logID() {
    console.log(this.id);
  }
</script>
<table id="my-table" onclick="logID();">
  <!-- when called, `this` will refer to the global object -->
  …
</table>
```

مقدار `this` درون `logID()` ارجاعی به شیء سراسری {{domxref("Window")}} است (یا در مورد [حالت سخت‌گیرانه](/en-US/docs/Web/JavaScript/Reference/Strict_mode)، `undefined`).

#### مشخص کردن "this" با استفاده از bind()

متد {{jsxref("Function.prototype.bind()")}} به شما امکان می‌دهد یک زمینه ثابت `this` برای همه فراخوانی‌های بعدی ایجاد کنید — و از مشکلاتی که در آنها مشخص نیست `this` چه خواهد بود، بسته به زمینه‌ای که تابع از آن فراخوانی شده است، عبور کنید. توجه داشته باشید که باید یک ارجاع به شنونده را نگه دارید تا بتوانید بعداً آن را حذف کنید.

این یک مثال با و بدون `bind()` است:

```js
class Something {
  name = "Something Good";
  constructor(element) {
    // bind causes a fixed `this` context to be assigned to `onclick2`
    this.onclick2 = this.onclick2.bind(this);
    element.addEventListener("click", this.onclick1);
    element.addEventListener("click", this.onclick2); // Trick
  }
  onclick1(event) {
    console.log(this.name); // undefined, as `this` is the element
  }
  onclick2(event) {
    console.log(this.name); // 'Something Good', as `this` is bound to the Something instance
  }
}

const s = new Something(document.body);
```

راه‌حل دیگر استفاده از یک تابع ویژه به نام `handleEvent()` برای دریافت هر رویدادی است:

```js
class Something {
  name = "Something Good";
  constructor(element) {
    // Note that the listeners in this case are `this`, not this.handleEvent
    element.addEventListener("click", this);
    element.addEventListener("dblclick", this);
  }
  handleEvent(event) {
    console.log(this.name); // 'Something Good', as this is bound to newly created object
    switch (event.type) {
      case "click":
        // some code here…
        break;
      case "dblclick":
        // some code here…
        break;
    }
  }
}

const s = new Something(document.body);
```

روش دیگر برای مدیریت ارجاع به `this` استفاده از تابع پیکانی است که زمینه `this` جداگانه‌ای ایجاد نمی‌کند.

```js
class SomeClass {
  name = "Something Good";

  register() {
    window.addEventListener("keydown", (e) => {
      this.someMethod(e);
    });
  }

  someMethod(e) {
    console.log(this.name);
    switch (e.code) {
      case "ArrowUp":
        // some code here…
        break;
      case "ArrowDown":
        // some code here…
        break;
    }
  }
}

const myObject = new SomeClass();
myObject.register();
```

### انتقال داده به درون و خارج از یک شنونده رویداد

شنوندگان رویداد فقط یک آرگومان می‌گیرند، یک {{domxref("Event")}} یا زیرکلاسی از `Event`، که به‌طور خودکار به شنونده ارسال می‌شود و مقدار بازگشتی نادیده گرفته می‌شود. بنابراین، برای انتقال داده به داخل و خارج یک شنونده رویداد، به جای عبور دادن داده از طریق پارامترها و مقادیر بازگشتی، باید به جای آن [closure](/en-US/docs/Web/JavaScript/Guide/Closures) ایجاد کنید.

توابعی که به‌عنوان شنونده رویداد منتقل می‌شوند به همه متغیرهایی که در حوزه‌های بیرونی حاوی آن تابع اعلام شده‌اند دسترسی دارند.

```js
const myButton = document.getElementById("my-button-id");
let someString = "Data";

myButton.addEventListener("click", () => {
  console.log(someString);
  // 'Data' on first click,
  // 'Data Again' on second click

  someString = "Data Again";
});

console.log(someString); // Expected Value: 'Data' (will never output 'Data Again')
```

برای اطلاعات بیشتر درباره حوزه‌های تابع، [راهنمای تابع](/en-US/docs/Web/JavaScript/Guide/Functions#function_scopes_and_closures) را بخوانید.

### مشکلات حافظه

```js
const elems = document.getElementsByTagName("*");

// Case 1
for (const elem of elems) {
  elem.addEventListener("click", (e) => {
    // Do something
  });
}

// Case 2
function processEvent(e)