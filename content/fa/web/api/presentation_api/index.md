---
title: "Presentation API"
---

---
title: Presentation API
slug: Web/API/Presentation_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.Presentation
---

{{securecontext_header}}{{SeeCompatTable}}{{DefaultAPISidebar("Presentation API")}}

رابط برنامه‌نویسی Presentation به یک {{Glossary("user agent")}} (مانند مرورگر وب) امکان می‌دهد محتوای وب را به‌طور مؤثر از طریق دستگاه‌های نمایش بزرگ مانند پروژکتورها و تلویزیون‌های متصل به شبکه نمایش دهد. انواع پشتیبانی‌شده دستگاه‌های چندرسانه‌ای شامل نمایشگرهایی است که به‌صورت باسیم از طریق HDMI، DVI یا مشابه آن متصل می‌شوند، یا به‌صورت بی‌سیم با استفاده از [DLNA](https://www.dlna.org/)، [Chromecast](https://developers.google.com/cast/)، [AirPlay](https://developer.apple.com/documentation/technologyoverviews/streaming) یا [Miracast](https://www.wi-fi.org/applications) کار می‌کنند.

![حالت ۱-عامل‌کاربر: صفحه‌های کنترل و ارائه با هم بارگذاری می‌شوند و سپس به نمایشگرها خروجی داده می‌شوند. حالت ۲-عامل‌کاربر: این دو صفحه به‌صورت جداگانه با پروتکل کنترل ارائه بارگذاری می‌شوند.](presentation_mode_illustration.png)

به‌طور کلی، یک صفحه وب از رابط برنامه‌نویسی Presentation Controller برای مشخص کردن محتوای وب که قرار است روی دستگاه ارائه نمایش داده شود و شروع جلسه ارائه استفاده می‌کند. با استفاده از Presentation Receiver API، محتوای وب ارائه‌شونده وضعیت جلسه را دریافت می‌کند. با فراهم کردن یک کانال مبتنی بر پیام برای هر دو صفحه کنترل‌کننده و گیرنده، توسعه‌دهنده وب می‌تواند تعامل بین این دو صفحه را پیاده‌سازی کند.

بسته به مکانیزم اتصالی که توسط دستگاه ارائه فراهم می‌شود، صفحه کنترل‌کننده و صفحه گیرنده می‌توانند توسط همان عامل کاربر یا توسط عامل‌های کاربر جداگانه رندر شوند.

- در حالت ۱-عامل‌کاربر، هر دو صفحه توسط همان عامل کاربر بارگذاری می‌شوند. با این حال، نتیجه رندر صفحه گیرنده از طریق پروتکل رندر از راه دور پشتیبانی‌شده به دستگاه ارائه ارسال می‌شود.
- در حالت ۲-عامل‌کاربر، صفحه گیرنده مستقیماً روی دستگاه ارائه بارگذاری می‌شود. عامل کاربر کنترل‌کننده از طریق پروتکل کنترل ارائه پشتیبانی‌شده با دستگاه ارائه ارتباط برقرار می‌کند تا جلسه ارائه را کنترل کند و پیام‌ها را بین دو صفحه منتقل کند.

## رابط‌ها

- {{domxref("Presentation")}}
  - : در بافت مرور کنترل‌کننده، رابط `Presentation` مکانیزمی برای لغو رفتار پیش‌فرض مرورگر در شروع ارائه به صفحه نمایش خارجی فراهم می‌کند. در بافت مرور گیرنده، رابط `Presentation` دسترسی به اتصالات ارائه موجود را فراهم می‌کند.
- {{domxref("PresentationRequest")}}
  - : یک ارائه ساخته‌شده توسط بافت مرور کنترل‌کننده را شروع یا دوباره به آن متصل می‌شود.
- {{domxref("PresentationAvailability")}}
  - : یک شیء [PresentationAvailability](/en-US/docs/Web/API/PresentationAvailability) با نمایشگرهای ارائه موجود مرتبط است و _در دسترس بودن نمایشگر ارائه_ را برای یک درخواست ارائه نشان می‌دهد.
- {{domxref("PresentationConnectionAvailableEvent")}}
  - : رویداد `PresentationConnectionAvailableEvent` روی یک [`PresentationRequest`](/en-US/docs/Web/API/PresentationRequest) وقتی که یک اتصال مرتبط با آن شیء ایجاد می‌شود، شلیک می‌شود.
- {{domxref("PresentationConnection")}}
  - : هر اتصال ارائه با یک شیء [PresentationConnection](/en-US/docs/Web/API/PresentationConnection) نمایش داده می‌شود.
- {{domxref("PresentationConnectionCloseEvent")}}
  - : یک رویداد `PresentationConnectionCloseEvent` وقتی که یک اتصال ارائه وارد حالت `closed` می‌شود، شلیک می‌شود.
- {{domxref("PresentationReceiver")}}
  - : [PresentationReceiver](/en-US/docs/Web/API/PresentationReceiver) به یک بافت مرور گیرنده اجازه می‌دهد به بافت‌های مرور کنترل‌کننده دسترسی پیدا کند و با آن‌ها ارتباط برقرار کند.
- {{domxref("PresentationConnectionList")}}
  - : `PresentationConnectionList` مجموعه اتصالات ارائه غیرپایان‌یافته را نشان می‌دهد. همچنین یک پایش‌کننده برای رویداد اتصال ارائه جدید موجود است.

## مثال

کدهای نمونه زیر استفاده از ویژگی‌های اصلی رابط برنامه‌نویسی Presentation را نشان می‌دهند: `controller.html` کنترل‌کننده را پیاده‌سازی می‌کند و `presentation.html` ارائه را پیاده‌سازی می‌کند. هر دو صفحه از دامنه `https://example.org` سرو می‌شوند (`https://example.org/controller.html` و `https://example.org/presentation.html`). این مثال‌ها فرض می‌کنند که صفحه کنترل‌کننده در هر زمان یک ارائه را مدیریت می‌کند. برای جزئیات بیشتر لطفاً به توضیحات داخل کدها مراجعه کنید.

### پایش در دسترس بودن نمایشگرهای ارائه

در `controller.html`:

```html
<button id="presentBtn" class="hidden">Present</button>
```

```css
.hidden {
  display: none;
}
```

```js
// دکمه Present اگر حداقل یک نمایشگر ارائه در دسترس باشد قابل مشاهده است
const presentBtn = document.getElementById("presentBtn");

// همچنین می‌توان از URL نسبی ارائه استفاده کرد، مثلاً "presentation.html"
const presUrls = [
  "https://example.com/presentation.html",
  "https://example.net/alternate.html",
];

// نمایش یا مخفی‌کردن دکمه ارائه بسته به در دسترس بودن نمایشگر
const handleAvailabilityChange = (available) => {
  if (available) {
    presentBtn.classList.remove("hidden");
  } else {
    presentBtn.classList.add("hidden");
  }
};

// این Promise به محض مشخص شدن در دسترس بودن نمایشگر ارائه حل می‌شود.
const request = new PresentationRequest(presUrls);
request
  .getAvailability()
  .then((availability) => {
    // مقدار availability.value ممکن است توسط عامل کاربر کنترل‌کننده تا زمانی
    // که شیء availability زنده است به‌روز نگه داشته شود. به توسعه‌دهندگان وب
    // توصیه می‌شود به محض عدم نیاز، آن را کنار بگذارند.
    handleAvailabilityChange(availability.value);
    availability.onchange = () => {
      handleAvailabilityChange(availability.value);
    };
  })
  .catch(() => {
    // پایش در دسترس بودن توسط پلتفرم پشتیبانی نمی‌شود، بنابراین کشف
    // نمایشگرهای ارائه فقط پس از فراخوانی request.start() انجام می‌شود.
    // برای سادگی فرض می‌کنیم دستگاه‌ها در دسترس هستند؛ یا می‌توان یک حالت
    // سوم برای دکمه پیاده‌سازی کرد.
    handleAvailabilityChange(true);
  });
```

### شروع یک ارائه جدید

در `controller.html`:

```js
presentBtn.onclick = () => {
  // شروع ارائه جدید.
  request
    .start()
    // اتصال به ارائه در صورت موفقیت به تابع setConnection منتقل می‌شود.
    .then(setConnection);
  // در غیر این صورت، کاربر گفتگوی انتخاب را لغو کرده یا هیچ صفحه‌ای پیدا نشده است.
};
```

### اتصال مجدد به یک ارائه

در فایل `controller.html`:

```html
<button id="reconnectBtn" class="hidden">Reconnect</button>
```

```js
const reconnect = () => {
  const presId = localStorage.getItem("presId");
  // هنگام اتصال مجدد به یک ارائه، presId الزامی است.
  if (presId) {
    request
      .reconnect(presId)
      // اتصال جدید به ارائه در صورت موفقیت به
      // setConnection منتقل می‌شود.
      .then(setConnection);
    // هیچ اتصالی برای presUrl و presId پیدا نشد، یا خطایی رخ داد.
  }
};
// هنگام پیمایش کنترل‌کننده، به‌طور خودکار اتصال مجدد برقرار کن.
reconnect();
// یا امکان اتصال مجدد دستی را فراهم کن.
reconnectBtn.onclick = reconnect;
```

### شروع ارائه توسط عامل کاربر کنترل‌کننده

در فایل `controller.html`:

```js
navigator.presentation.defaultRequest = new PresentationRequest(presUrls);
navigator.presentation.defaultRequest.onconnectionavailable = (evt) => {
  setConnection(evt.connection);
};
```

تنظیم `presentation.defaultRequest` به صفحه اجازه می‌دهد تا `PresentationRequest` مورد استفاده را زمانی که عامل کاربر کنترل‌کننده یک ارائه را شروع می‌کند، مشخص کند.

### پایش وضعیت اتصال و تبادل داده

در `controller.html`:

```html
<button id="disconnectBtn" class="hidden">Disconnect</button>
<button id="stopBtn" class="hidden">Stop</button>
<button id="reconnectBtn" class="hidden">Reconnect</button>
```

```js
let connection;

// دکمه‌های Disconnect و Stop اگر یک ارائه متصل وجود داشته باشد قابل مشاهده هستند
const stopBtn = document.querySelector("#stopBtn");
const reconnectBtn = document.querySelector("#reconnectBtn");
const disconnectBtn = document.querySelector("#disconnectBtn");

stopBtn.onclick = () => {
  connection?.terminate();
};

disconnectBtn.onclick = () => {
  connection?.close();
};

function setConnection(newConnection) {
  // قطع اتصال از ارائه موجود، اگر در حال تلاش برای اتصال مجدد نیستیم
  if (
    connection &&
    connection !== newConnection &&
    connection.state !== "closed"
  ) {
    connection.onclose = undefined;
    connection.close();
  }

  // تنظیم اتصال جدید و ذخیره شناسه ارائه
  connection = newConnection;
  localStorage.setItem("presId", connection.id);

  function showConnectedUI() {
    // به کاربر اجازه دهید از ارائه قطع شود یا آن را خاتمه دهد
    stopBtn.classList.remove("hidden");
    disconnectBtn.classList.remove("hidden");
    reconnectBtn.classList.add("hidden");
  }

  function showDisconnectedUI() {
    disconnectBtn.classList.add("hidden");
    stopBtn.classList.add("hidden");
    if (localStorage.getItem("presId")) {
      // اگر presId در localStorage وجود دارد، به کاربر اجازه اتصال مجدد بده
      reconnectBtn.classList.remove("hidden");
    } else {
      reconnectBtn.classList.add("hidden");
    }
  }

  // پایش وضعیت اتصال
  connection.onconnect = () => {
    showConnectedUI();

    // ثبت مدیریت‌کننده پیام
    connection.onmessage = (message) => {
      console.log(`Received message: ${message.data}`);
    };

    // ارسال پیام اولیه به صفحه ارائه
    connection.send("Say hello");
  };

  connection.onclose = () => {
    connection = null;
    showDisconnectedUI();
  };

  connection.onterminate = () => {
    localStorage.removeItem("presId");
    connection = null;
    showDisconnectedUI();
  };
}
```

### پایش اتصال(های) موجود و سلام کردن

در `presentation.html`:

```js
const addConnection = (connection) => {
  connection.onmessage = (message) => {
    if (message.data === "Say hello") connection.send("hello");
  };
};

navigator.presentation.receiver.connectionList.then((list) => {
  list.connections.forEach((connection) => {
    addConnection(connection);
  });
  list.onconnectionavailable = (evt) => {
    addConnection(evt.connection);
  };
});
```

### ارسال اطلاعات زبان با یک پیام

در فایل `controller.html`:

```html
connection.send('{"string": "你好，世界!", "lang": "zh-CN"}');
connection.send('{"string": "こんにちは、世界!", "lang": "ja"}');
connection.send('{"string": "안녕하세요, 세계!", "lang": "ko"}');
connection.send('{"string": "Hello, world!", "lang": "en-US"}');
```

در فایل `presentation.html`:

```js
connection.onmessage = (message) => {
  const messageObj = JSON.parse(message.data);
  const spanElt = document.createElement("SPAN");
  spanElt.lang = messageObj.lang;
  spanElt.textContent = messageObj.string;
  document.body.appendChild(spanElt);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

[پلی‌فیل Presentation API](https://mediascape.github.io/presentation-api-polyfill/) شامل یک پلی‌فیل جاوااسکریپت از مشخصات [Presentation API](https://w3c.github.io/presentation-api/) است که در حال استانداردسازی در [گروه کاری صفحه دوم](https://www.w3.org/2014/secondscreen/) در W3C است. این پلی‌فیل عمدتاً برای بررسی چگونگی پیاده‌سازی Presentation API بر روی مکانیزم‌های مختلف ارائه در نظر گرفته شده است.