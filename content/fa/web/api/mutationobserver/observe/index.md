---
title: "MutationObserver: observe() method"
---

---
title: "MutationObserver: observe() method"
short-title: observe()
slug: Web/API/MutationObserver/observe
page-type: web-api-instance-method
browser-compat: api.MutationObserver.observe
---

{{APIRef("DOM WHATWG")}}

متد **`observe()`** در {{domxref("MutationObserver")}}، تابع فراخوان (callback) مربوط به `MutationObserver` را به‌گونه‌ای پیکربندی می‌کند که شروع به دریافت اعلان‌هایی دربارهٔ تغییرات DOM که با گزینه‌های داده‌شده مطابقت دارند، بکند.

بسته به پیکربندی، مشاهده‌گر (observer) ممکن است یک {{domxref("Node")}} تنها در درخت DOM را نظارت کند، یا آن گره و برخی یا تمام گره‌های فرزند آن را. یک گرهٔ یکسان می‌تواند توسط چندین مشاهده‌گر نظارت شود و همچنین یک `MutationObserver` یکسان می‌تواند با فراخواندن چندبارهٔ `observe()` روی همان `MutationObserver`، تغییرات بخش‌های مختلف درخت DOM و/یا انواع مختلف تغییرات را دنبال کند.

برای متوقف کردن `MutationObserver` (به‌طوری که دیگر هیچ‌کدام از فراخوان‌های آن اجرا نشوند)، از {{domxref("MutationObserver.disconnect()")}} استفاده کنید.

## سینتکس

```js-nolint
observe(target, options)
```

### پارامترها

- `target`
  - : یک {{domxref("Node")}} در درخت DOM (که ممکن است یک {{domxref("Element")}} باشد) که برای نظارت بر تغییرات در نظر گرفته می‌شود، یا ریشهٔ زیردرختی از گره‌ها که باید نظارت شوند.
- `options`
  - : یک شیء شامل گزینه‌هایی که مشخص می‌کند کدام تغییرات DOM باید به `callback` مربوط به `mutationObserver` گزارش شوند. در هنگام فراخواندن `observe()`، حداقل یکی از گزینه‌های `childList`، `attributes` و/یا `characterData` باید برابر `true` باشد؛ در غیر این صورت استثنای `TypeError` پرتاب می‌شود.

    گزینه‌ها به شرح زیر هستند:
    - `subtree` {{optional_inline}}
      - : به `true` تنظیم کنید تا نظارت به کل زیردرخت گره‌هایی که ریشهٔ آن‌ها `target` است گسترش یابد. در این حالت، همهٔ ویژگی‌های دیگر به جای اعمال فقط روی گرهٔ `target`، به تمام گره‌های موجود در زیردرخت اعمال می‌شوند. مقدار پیش‌فرض `false` است. توجه داشته باشید که اگر یکی از فرزندان `target` حذف شود، تغییرات در زیردرخت آن فرزند همچنان تا زمانی که اعلان مربوط به خودِ حذف تحویل داده شود، نظارت می‌شود.
    - `childList` {{optional_inline}}
      - : به `true` تنظیم کنید تا گرهٔ هدف (و در صورت `true` بودن `subtree`، فرزندان آن) برای افزوده‌شدن گره‌های فرزند جدید یا حذف گره‌های فرزند موجود نظارت شود. مقدار پیش‌فرض `false` است.
    - `attributes` {{optional_inline}}
      - : به `true` تنظیم کنید تا تغییرات در مقادیر ویژگی‌های (attributes) گره یا گره‌های تحت نظارت دنبال شود. اگر یکی از گزینه‌های `attributeFilter` یا `attributeOldValue` مشخص شده باشد، مقدار پیش‌فرض `true` است؛ در غیر این صورت مقدار پیش‌فرض `false` است.
    - `attributeFilter` {{optional_inline}}
      - : آرایه‌ای از نام ویژگی‌های خاصی که باید نظارت شوند. اگر این ویژگی وارد نشود، تغییرات در همهٔ ویژگی‌ها منجر به اعلان‌های تغییر (mutation notifications) می‌شود.
    - `attributeOldValue` {{optional_inline}}
      - : به `true` تنظیم کنید تا مقدار قبلی هر ویژگی که تغییر می‌کند ثبت شود. برای مثالی از نظارت بر تغییرات ویژگی‌ها و ثبت مقادیر، به بخش [نظارت بر مقادیر ویژگی‌ها](#monitoring_attribute_values) مراجعه کنید. مقدار پیش‌فرض `false` است.
    - `characterData` {{optional_inline}}
      - : به `true` تنظیم کنید تا گرهٔ هدف مشخص‌شده (و در صورت `true` بودن `subtree`، فرزندان آن) برای تغییرات در داده‌های کاراکتری (character data) موجود در گره یا گره‌ها نظارت شود. اگر `characterDataOldValue` مشخص شده باشد، مقدار پیش‌فرض `true` است؛ در غیر این صورت مقدار پیش‌فرض `false` است.
    - `characterDataOldValue` {{optional_inline}}
      - : به `true` تنظیم کنید تا در هر بار تغییر متن گره‌های تحت نظارت، مقدار قبلی متن آن گره ثبت شود. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- {{jsxref('TypeError')}}
  - : در هر یک از شرایط زیر پرتاب می‌شود:
    - گزینه‌ها طوری پیکربندی شده باشند که در عمل چیزی نظارت نشود. (مثلاً اگر `childList`، `attributes` و `characterData` همگی `false` باشند.)
    - مقدار `options.attributes` برابر `false` باشد (یعنی تغییرات ویژگی‌ها قرار نیست نظارت شوند)، اما `attributeOldValue` برابر `true` باشد و/یا `attributeFilter` وجود داشته باشد.
    - گزینهٔ `characterDataOldValue` برابر `true` باشد اما `characterData` برابر `false` باشد (یعنی تغییرات کاراکتری قرار نیست نظارت شوند).

## مثال‌ها

### استفادهٔ پایه

در این مثال نشان می‌دهیم که چگونه متد **`observe()`** را روی یک نمونه از {{domxref("MutationObserver")}} پس از آماده‌سازی آن فراخوانی کنیم؛ به این صورت که یک عنصر هدف و یک شیء `options` به آن می‌دهیم.

```js
// create a new instance of `MutationObserver` named `observer`,
// passing it a callback function
const observer = new MutationObserver(() => {
  console.log("callback that runs when observer is triggered");
});

// call `observe()`, passing it the element to observe, and the options object
observer.observe(document.querySelector("#element-to-observe"), {
  subtree: true,
  childList: true,
});
```

### فرزندان حذف‌شده هنگام استفاده از `subtree`

اگر گرهی را با استفاده از گزینهٔ `subtree` نظارت کنید، حتی پس از حذف بخشی از زیردرخت نیز همچنان اعلان‌هایی دربارهٔ تغییرات فرزندان آن گره دریافت خواهید کرد. با این حال، پس از تحویل اعلان مربوط به حذف، تغییرات بعدی در زیردرخت جدا شده دیگر مشاهده‌گر را فعال نخواهند کرد.

این کار مانع از دست‌دادن تغییراتی می‌شود که پس از قطع ارتباط و پیش از آن‌که فرصت نظارت اختصاصی بر گره یا زیردرخت جابه‌جاشده را پیدا کنید، رخ می‌دهند. از نظر تئوری، این یعنی اگر اشیاء {{domxref("MutationRecord")}} را که تغییرات رخ‌داده را توصیف می‌کنند پیگیری کنید، می‌توانید تغییرات را «واگردانی» کنید و DOM را به حالت اولیه‌اش بازگردانید.

```html
<div id="target">
  <div id="child"></div>
</div>
```

```js
const target = document.getElementById("target");
const child = document.getElementById("child");

const observer = new MutationObserver((mutations) => {
  mutations.forEach((mutation) => {
    console.log(mutation.type, mutation.target.id, mutation.attributeName);

    if (mutation.type === "childList" && mutation.target.id === "target") {
      // After receiving the notification that the child was removed,
      // further modifications to the detached subtree no longer trigger the observer.
      child.setAttribute("data-bar", "");
    }
  });
});

observer.observe(target, {
  attributes: true,
  childList: true,
  subtree: true,
});

target.removeChild(child);
// This change happens before the "childList target" notification is delivered,
// so it will also trigger the observer.
child.setAttribute("data-foo", "");

// Output:
// childList target null
// attributes child data-foo
// There is no "attributes child data-bar" notification.
```

### استفاده از `attributeFilter`

در این مثال، یک Mutation Observer برای نظارت بر تغییرات ویژگی‌های `status` و `username` در تمام عناصر موجود در زیردرختی که نام کاربران یک اتاق گفتگو را نمایش می‌دهد، تنظیم شده است. این کار به کد اجازه می‌دهد تا برای مثال، تغییرات نام‌های کاربری را منعکس کند یا کاربران را به‌عنوان دور از صفحه‌کلید (AFK) یا آفلاین علامت‌گذاری کند.

```js
function callback(mutationList) {
  mutationList.forEach((mutation) => {
    switch (mutation.type) {
      case "attributes":
        switch (mutation.attributeName) {
          case "status":
            userStatusChanged(mutation.target.username, mutation.target.status);
            break;
          case "username":
            usernameChanged(mutation.oldValue, mutation.target.username);
            break;
        }
        break;
    }
  });
}

const userListElement = document.querySelector("#user-list");

const observer = new MutationObserver(callback);
observer.observe(userListElement, {
  attributeFilter: ["status", "username"],
  attributeOldValue: true,
  subtree: true,
});
```

### نظارت بر مقادیر ویژگی‌ها

در این مثال، یک عنصر را برای تغییرات مقادیر ویژگی‌ها نظارت می‌کنیم و یک دکمه اضافه می‌کنیم که ویژگی [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) عنصر را بین `"ltr"` و `"rtl"` تغییر می‌دهد. در داخل تابع فراخوانِ مشاهده‌گر، مقدار قبلی ویژگی را ثبت (log) می‌کنیم.

#### HTML

```html
<button id="toggle">Toggle direction</button><br />
<div id="container">
  <input type="text" id="rhubarb" dir="ltr" value="Tofu" />
</div>
<pre id="output"></pre>
```

#### CSS

```css
body {
  background-color: paleturquoise;
}

button,
input,
pre {
  margin: 0.5rem;
}
```

#### JavaScript

```js
const toggle = document.querySelector("#toggle");
const rhubarb = document.querySelector("#rhubarb");
const observerTarget = document.querySelector("#container");
const output = document.querySelector("#output");

toggle.addEventListener("click", () => {
  rhubarb.dir = rhubarb.dir === "ltr" ? "rtl" : "ltr";
});

const config = {
  subtree: true,
  attributeOldValue: true,
};

const callback = (mutationList) => {
  for (const mutation of mutationList) {
    if (mutation.type === "attributes") {
      output.textContent = `The ${mutation.attributeName} attribute was modified from "${mutation.oldValue}".`;
    }
  }
};

const observer = new MutationObserver(callback);
observer.observe(observerTarget, config);
```

#### نتیجه

{{EmbedLiveSample("Monitoring attribute values")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}