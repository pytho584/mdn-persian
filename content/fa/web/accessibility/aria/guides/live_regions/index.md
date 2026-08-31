---
title: "ARIA live regions"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions"
translated_by: "n8n + AI"
---

---
title: ARIA live regions
slug: Web/Accessibility/ARIA/Guides/Live_regions
page-type: guide
sidebar: accessibilitysidebar
---

با استفاده از JavaScript، می‌توان بخش‌هایی از صفحه را به‌صورت پویا بدون نیاز به بارگذاری مجدد کل صفحه تغییر داد — برای مثال، به‌روزرسانی آنی فهرست نتایج جستجو، یا نمایش یک اعلان یا هشدار محتاطانه که نیازی به تعامل کاربر ندارد. در حالی که این تغییرات معمولاً برای کاربرانی که صفحه را می‌بینند از نظر بصری آشکار است، ممکن است برای کاربران فناوری‌های کمکی واضح نباشد. مناطق زنده ARIA این شکاف را پر می‌کنند و راهی برای نمایش برنامه‌نویسی‌شده تغییرات محتوای پویا فراهم می‌کنند که توسط فناوری‌های کمکی قابل اعلام باشد.

> [!NOTE]
> فناوری‌های کمکی به‌طور کلی فقط تغییرات _پویا_ در محتوای یک منطقه زنده را اعلام می‌کنند.
> افزودن ویژگی `aria-live` یا یک `role` تخصصی منطقه زنده (مانند [`role="status"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)) به عنصری که می‌خواهید تغییرات آن اعلام شود، تا زمانی که ویژگی را قبل از رخ دادن تغییرات اضافه کنید کار می‌کند — چه در نشانه‌گذاری اصلی، چه به‌صورت پویا با JavaScript. با یک منطقه زنده خالی شروع کنید و سپس، در یک مرحله جداگانه، محتوای داخل منطقه را تغییر دهید.
> اگرچه به‌صراحت در مشخصات مستند نشده است، مرورگرها/فناوری‌های کمکی شامل پردازش ویژه‌ای برای [`role="alert"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role) هستند: در بیشتر موارد، محتوای داخل مناطق `role="alert"` اعلام می‌شود، حتی اگر منطقه (که از قبل حاوی اعلان/پیام است) در نشانه‌گذاری اولیه صفحه وجود داشته باشد یا به‌صورت پویا به صفحه تزریق شود. با این حال، توجه داشته باشید که مناطق `role="alert"` بسته به ترکیب خاص مرورگر/فناوری کمکی، به‌طور خودکار با پیشوند «هشدار» هنگام اعلام دریافت می‌شوند.

## مناطق زنده

محتوای پویایی که بدون بارگذاری مجدد صفحه به‌روزرسانی می‌شود، معمولاً یا یک منطقه است یا یک ویجت. تغییرات ساده محتوایی که تعاملی نیستند باید به‌عنوان مناطق زنده علامت‌گذاری شوند. یک منطقه زنده به‌صراحت با استفاده از ویژگی `aria-live` مشخص می‌شود.

**`aria-live`**: از `aria-live=POLITENESS_SETTING` برای تنظیم اولویتی استفاده می‌شود که صفحه‌خوان با آن به‌روزرسانی‌های مناطق زنده را پردازش می‌کند - تنظیمات ممکن عبارتند از: `off`، `polite` یا `assertive`. این ویژگی به‌مراتب مهم‌ترین است.

به‌طور معمول، فقط از `aria-live="polite"` استفاده می‌شود. هر منطقه‌ای که به‌روزرسانی‌هایی دریافت می‌کند که برای کاربر مهم است، اما نه آن‌قدر سریع که آزاردهنده باشد، باید این ویژگی را دریافت کند. صفحه‌خوان تغییرات را هر زمان که کاربر بیکار است اعلام می‌کند.

`aria-live="assertive"` فقط باید برای اعلان‌های حساس به زمان/بحرانی استفاده شود که کاملاً به توجه فوری کاربر نیاز دارند. به‌طور کلی، تغییر در یک منطقه زنده قاطع (assertive) هر اعلامی را که صفحه‌خوان در حال پخش آن است قطع می‌کند. بنابراین، می‌تواند بسیار آزاردهنده و مخرب باشد و فقط باید به‌ندرت استفاده شود.

به‌طور غیرمنتظره‌ای، `aria-live="off"` نشان نمی‌دهد که تغییرات نباید اعلام شوند. وقتی یک عنصر دارای `aria-live="off"` است (یا دارای `role` با این مقدار ضمنی است، مانند `role="marquee"` یا `role="timer"`)، تغییرات در محتوای عنصر فقط زمانی قرار است اعلام شوند که فوکوس روی عنصر یا داخل آن باشد.

### مثال پایه: به‌روزرسانی اطلاعات مفید روی صفحه توسط کادر کشویی

یک وب‌سایت تخصصی در ارائه اطلاعات درباره سیاره‌ها، یک کادر کشویی ارائه می‌دهد. وقتی سیاره‌ای از کادر کشویی انتخاب می‌شود، منطقه‌ای در صفحه با اطلاعات مربوط به سیاره انتخاب‌شده به‌روزرسانی می‌شود.

```html
<fieldset>
  <legend>Planet information</legend>
  <label for="planetsSelect">Planet:</label>
  <select id="planetsSelect" aria-controls="planetInfo">
    <option value="">Select a planet…</option>
    <option value="mercury">Mercury</option>
    <option value="venus">Venus</option>
    <option value="earth">Earth</option>
    <option value="mars">Mars</option>
  </select>
  <button id="renderPlanetInfoButton">Go</button>
</fieldset>

<div role="region" id="planetInfo" aria-live="polite">
  <h2 id="planetTitle">No planet selected</h2>
  <p id="planetDescription">Select a planet to view its description</p>
</div>

<p>
  <small>
    Information from
    <a href="https://en.wikipedia.org/wiki/Solar_System">Wikipedia</a>
  </small>
</p>
```

```js
const PLANETS_INFO = {
  mercury: {
    title: "Mercury",
    description:
      "Mercury is the smallest and innermost planet in the Solar System. It is named after the Roman deity Mercury, the messenger to the gods.",
  },

  venus: {
    title: "Venus",
    description:
      "Venus is the second planet from the Sun. It is named after the Roman goddess of love and beauty.",
  },

  earth: {
    title: "Earth",
    description:
      "Earth is the third planet from the Sun and the only object in the Universe known to harbor life.",
  },

  mars: {
    title: "Mars",
    description:
      'Mars is the fourth planet from the Sun and the second-smallest planet in the Solar System after Mercury. In English, Mars carries a name of the Roman god of war, and is often referred to as the "Red Planet".',
  },
};

function renderPlanetInfo(planet) {
  const planetTitle = document.querySelector("#planetTitle");
  const planetDescription = document.querySelector("#planetDescription");

  if (planet in PLANETS_INFO) {
    planetTitle.textContent = PLANETS_INFO[planet].title;
    planetDescription.textContent = PLANETS_INFO[planet].description;
  } else {
    planetTitle.textContent = "No planet selected";
    planetDescription.textContent = "Select a planet to view its description";
  }
}

const renderPlanetInfoButton = document.querySelector(
  "#renderPlanetInfoButton",
);

renderPlanetInfoButton.addEventListener("click", (event) => {
  const planetsSelect = document.querySelector("#planetsSelect");
  const selectedPlanet =
    planetsSelect.options[planetsSelect.selectedIndex].value;

  renderPlanetInfo(selectedPlanet);
});
```

{{EmbedLiveSample('Basic_example_Dropdown_box_updates_useful_onscreen_information', '', 350)}}

همان‌طور که کاربر یک سیاره جدید را انتخاب می‌کند، اطلاعات موجود در منطقه زنده اعلام می‌شود. از آنجا که منطقه زنده دارای `aria-live="polite"` است، صفحه‌خوان منتظر می‌ماند تا کاربر مکث کند و سپس به‌روزرسانی را اعلام می‌کند. بنابراین، حرکت به پایین در فهرست و انتخاب سیاره‌ای دیگر، به‌روزرسانی‌های منطقه زنده را اعلام نمی‌کند. به‌روزرسانی‌های منطقه زنده فقط برای سیاره‌ای که در نهایت انتخاب شده است اعلام می‌شود.

در اینجا یک اسکرین‌شات از VoiceOver در مک وجود دارد که به‌روزرسانی منطقه زنده را (از طریق زیرنویس) اعلام می‌کند:

![یک اسکرین‌شات از VoiceOver در مک که به‌روزرسانی یک منطقه زنده را اعلام می‌کند. زیرنویس‌ها در تصویر نشان داده شده‌اند.](web_accessibility_aria_aria_live_regions.png)

## نقش‌های با ویژگی‌های ضمنی منطقه زنده

عناصر با مقادیر `role="…"` زیر به‌طور پیش‌فرض به‌عنوان مناطق زنده عمل می‌کنند:

<table style="width: 100%;">
 <thead>
  <tr>
   <th scope="col">نقش</th>
   <th scope="col">توضیحات</th>
   <th scope="col">یادداشت‌های سازگاری</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>log</td>
   <td>گفتگو، خطا، بازی یا نوع دیگری از گزارش</td>
   <td>برای حداکثر سازگاری، هنگام استفاده از این نقش، یک <code>aria-live="polite"</code> اضافی نیز اضافه کنید.</td>
  </tr>
  <tr>
   <td>status</td>
   <td>یک نوار وضعیت یا ناحیه‌ای از صفحه که وضعیت به‌روزشده‌ای از نوعی را فراهم می‌کند. کاربران صفحه‌خوان یک فرمان ویژه برای خواندن وضعیت فعلی دارند.</td>
   <td>برای حداکثر سازگاری، هنگام استفاده از این نقش، یک <code>aria-live="polite"</code> اضافی نیز اضافه کنید.</td>
  </tr>
  <tr>
   <td>alert</td>
   <td>پیام خطا یا هشدار که روی صفحه چشمک می‌زند. هشدارها به‌ویژه برای اعلان‌های اعتبارسنجی سمت کلاینت به کاربران مهم هستند. <a href="https://www.w3.org/WAI/ARIA/apg/example-index/alert/alert.html" class="external" rel="noopener">مثال هشدار.</a></td>
   <td>برای حداکثر سازگاری، برخی افراد توصیه می‌کنند هنگام استفاده از این نقش، یک <code>aria-live="assertive"</code> اضافی نیز اضافه کنید. با این حال، اضافه کردن هر دو <code>aria-live</code> و <code>role="alert"</code> باعث مشکلات صحبت دوباره در VoiceOver در iOS می‌شود.</td>
  </tr>
  <tr>
   <td>progressbar</td>
   <td>ترکیبی بین یک ویجت و یک منطقه زنده. از این مورد با <code>aria-valuemin</code>، <code>aria-valuenow</code> و <code>aria-valuemax</code> استفاده کنید. (TBD: اطلاعات بیشتری اینجا اضافه شود).</td>
   <td></td>
  </tr>
  <tr>
   <td>marquee</td>
   <td>متنی که حرکت می‌کند، مانند یک تیکر سهام.</td>
   <td></td>
  </tr>
  <tr>
   <td>timer</td>
   <td>هر نوع تایمر یا ساعت، مانند تایمر شمارش معکوس یا نمایش کرونومتر.</td>
   <td></td>
  </tr>
 </tbody>
</table>

## ویژگی‌های اضافی منطقه زنده

مناطق زنده به خوبی پشتیبانی می‌شوند. Vispero در سال 2014 [اطلاعاتی درباره وضعیت پشتیبانی از مناطق زنده](https://vispero.com/resources/screen-reader-support-aria-live-regions/) منتشر کرد. Paul J. Adam به‌طور خاص [پشتیبانی از `aria-atomic` و `aria-relevant`](https://pauljadam.com/demos/aria-atomic-relevant.html) را تحقیق کرده است.

1. **`aria-atomic`**: از `aria-atomic=BOOLEAN` برای تنظیم اینکه آیا صفحه‌خوان همیشه باید کل منطقه زنده را به‌عنوان یک کل ارائه دهد، حتی اگر فقط بخشی از منطقه تغییر کند، استفاده می‌شود. تنظیمات ممکن عبارتند از: `false` یا `true`. مقدار پیش‌فرض `false` است.
2. [**`aria-relevant`**](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant)

   : از `aria-relevant=[LIST_OF_CHANGES]` برای تنظیم اینکه چه نوع تغییراتی برای یک منطقه زنده مرتبط هستند استفاده می‌شود. تنظیمات ممکن یک یا چند مورد از اینها هستند: `additions`، `removals`، `text`، `all`. تنظیم پیش‌فرض: `additions text` است.

### مثال‌های پایه: `aria-atomic`

به‌عنوان تصویری از `aria-atomic`، وب‌سایتی را در نظر بگیرید که یک ساعت پایه دارد و ساعت‌ها و دقیقه‌ها را نشان می‌دهد. ساعت هر دقیقه به‌روزرسانی می‌شود و زمان باقی‌مانده جدید جایگزین محتوای فعلی می‌شود.

```html
<div id="clock" role="timer" aria-live="polite">
  <span id="clock-hours"></span>
  <span id="clock-mins"></span>
</div>
```

```js
/* basic JavaScript to update the clock */
function updateClock() {
  const now = new Date();
  document.getElementById("clock-hours").textContent = now.getHours();
  document.getElementById("clock-mins").textContent =
    `0${now.getMinutes()}`.slice(-2);
}

/* first run */
updateClock();

/* update every minute */
setInterval(updateClock, 60000);
```

اولین بار که تابع اجرا می‌شود، کل رشته‌ای که اضافه شده است اعلام می‌شود. در فراخوانی‌های بعدی، فقط بخش‌هایی از محتوا که نسبت به محتوای قبلی تغییر کرده‌اند اعلام می‌شوند. برای مثال، وقتی ساعت از «17:33» به «17:34» تغییر می‌کند، فناوری‌های کمکی فقط «34» را اعلام می‌کنند که برای کاربران چندان مفید نیست.

یک راه برای دور زدن این مشکل این است که ابتدا تمام محتویات منطقه زنده را پاک کنید (در این مورد، `innerHTML` هر دو `<span id="clock-hours">` و `<span id="clock-mins">` را خالی کنید) و سپس محتوای جدید را تزریق کنید. با این حال، این روش گاهی اوقات می‌تواند غیرقابل اعتماد باشد، زیرا به زمان‌بندی دقیق این دو به‌روزرسانی وابسته است.

`aria-atomic="true"` تضمین می‌کند که هر بار منطقه زنده به‌روزرسانی می‌شود، کل محتوا به‌طور کامل اعلام شود (مثلاً «17:34»).

```html
<div id="clock" role="timer" aria-live="polite" aria-atomic="true">…</div>
```

مثال دیگری از `aria-atomic` - یک به‌روزرسانی/اعلان که در نتیجه اقدام کاربر انجام می‌شود.

```html
<div id="date-input">
  <label for="year">Year:</label>
  <input type="text" id="year" value="1990" />
</div>

<div id="date-output" aria-atomic="true" aria-live="polite">
  The set year is:
  <span id="year-output">1990</span>
</div>
```

```js
function change(event) {
  const yearOut = document.getElementById("year-output");

  switch (event.target.id) {
    case "year":
      yearOut.textContent = event.target.value;
      break;
  }
}

document.getElementById("year").addEventListener("blur", change);
```

بدون `aria-atomic="true"`، صفحه‌خوان فقط مقدار تغییر یافته سال را اعلام می‌کند. با `aria-atomic="true"`، صفحه‌خوان اعلام می‌کند «سال تنظیم شده است: _مقدار تغییر یافته_»

### مثال پایه: `aria-relevant`

با `aria-relevant` می‌توانید مشخص کنید که کدام نوع تغییرات/به‌روزرسانی‌ها در یک منطقه زنده باید اعلام شوند.

به‌عنوان مثال، یک وب‌س