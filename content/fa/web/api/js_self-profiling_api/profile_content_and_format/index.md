---
title: "Profile anatomy and format"
---

---
title: Profile anatomy and format
slug: Web/API/JS_Self-Profiling_API/Profile_content_and_format
page-type: guide
---

{{DefaultAPISidebar("JS Self-Profiling API")}}

در این صفحه، نحوهٔ تفسیر یک پروفایل گرفته‌شده با استفاده از Self-Profiling API را شرح می‌دهیم.

قالب شیء بازگردانده‌شده توسط {{domxref("Profiler.stop()")}} به‌گونه‌ای طراحی شده است که از نظر فضا کارآمد باشد: برای مثال، این قالب می‌کوشد از تکرار مقادیر URL برای تابع‌هایی که در یک اسکریپت تعریف شده‌اند اجتناب کند. این بدان معناست که برای درک اینکه یک نمونه در شیء پروفایل به چه مکانی در برنامه نگاشت می‌شود، به تفسیر نیاز است و این صفحهٔ راهنما قصد دارد نحوهٔ انجام این تفسیر را توضیح دهد.

در بخش نخست، [abstract structure of a profile](#anatomy_of_a_profile) را توصیف می‌کنیم. در بخش بعد، [the format of the profile object](#profile_format) بازگردانده‌شده توسط {{domxref("Profiler.stop()")}} را شرح می‌دهیم. در پایان، [walk through an example](#example) را مرور می‌کنیم تا نشان دهیم پروفایل یک برنامهٔ معین چگونه است و چگونه می‌توان آن را تفسیر کرد.

## Anatomy of a profile

در این بخش، ساختار انتزاعی یک پروفایل را توصیف می‌کنیم. توجه داشته باشید که این ساختار با قالب شیء بازگردانده‌شده توسط {{domxref("Profiler.stop()")}} یکسان نیست: آن قالب را در بخش بعدی این راهنما شرح خواهیم داد.

یک پروفایل شامل آرایه‌ای از نمونه‌ها است. هر نمونه شامل یک برچسب زمانی (timestamp) و یک پشتهٔ فراخوانی (call stack) است. هر پشتهٔ فراخوانی از آرایه‌ای از فریم‌های پشته (stack frames) تشکیل شده است و هر فریم پشته، اطلاعاتی دربارهٔ مکان تابع متناظرش در برنامه در بر دارد:

![Diagram of a profile](profile.svg)

برچسب زمانی یک {{domxref("DOMHighResTimeStamp")}} است که میلی‌ثانیه‌ها را از _time origin_ (مبدأ زمان) اندازه‌گیری می‌کند: برای بافتار پنجره (window context)، این مقدار زمانی است که پنجره ساخته شده است (اگر پنجره جدید باشد) یا زمانی که مرورگر پیمایش به این سند را آغاز کرده است.

پشتهٔ فراخوانی، نمایشی از پشتهٔ فراخوانی JavaScript است که به شما امکان می‌دهد مسیر اجرا تا نقطهٔ مکانی برنامه را در لحظهٔ برداشته‌شدن نمونه درک کنید.

پشتهٔ فراخوانی شامل آرایه‌ای از فریم‌های پشته است. یک فریم پشته اساساً یک فراخوانی تابع تودرتو را نشان می‌دهد؛ بنابراین اگر تابع `a()` تابع `b()` را فراخوانی کند و تابع `b()` تابع `c()` را فراخوانی کند و نمونه‌ای در حالی گرفته شود که مرورگر در حال اجرای `c()` است، آنگاه پشتهٔ فراخوانی شامل فریم‌های `[a, b, c]` خواهد بود:

```js
function c() {
  // sample taken here
}

function b() {
  c();
}

function a() {
  b();
}
```

هر فریم پشته، اطلاعاتی دربارهٔ مکان تابع متناظرش در برنامه در بر دارد:

- URL اسکریپت
- نام تابع
- شمارهٔ خط تعریف تابع در اسکریپت
- شمارهٔ ستون تعریف تابع در آن خط

## Profile format

اگرچه بخش بالا ساختار _منطقی_ یک پروفایل را توصیف می‌کند، قالب شیء بازگردانده‌شده توسط {{domxref("Profiler.stop()")}} متفاوت است. دلیل این است که این قالب برای کارآمدی از نظر فضا طراحی شده است: برای مثال، قالب می‌کوشد از تکرار مقادیر URL برای تابع‌هایی که در یک اسکریپت تعریف شده‌اند اجتناب کند.

شیء پروفایل شامل چهار ویژگی است که همگی آرایه هستند:

- `frames`
  - : آرایه‌ای از اشیا که هر یک اطلاعاتی دربارهٔ یک فریم پشته در بر دارند:
    - `column`: شمارهٔ ستون تعریف تابع.
    - `line`: شمارهٔ خط تعریف تابع.
    - `name`: نام تابع.
    - `resourceId`: ایندکس یک آیتم در `resources` که نشانی URL اسکریپتی را نشان می‌دهد که تابع در آن تعریف شده است.

    فقط `name` همیشه وجود دارد: اگر تابع در یک اسکریپت تعریف نشده باشد (مثلاً اگر تابعی باشد که در مرورگر تعبیه شده است)، سه ویژگی دیگر حذف می‌شوند.

- `resources`
  - : آرایه‌ای از رشته‌ها که هر یک نشانی URL یک اسکریپت را نشان می‌دهد.
- `samples`
  - : آرایه‌ای از اشیا که هر یک دو ویژگی دارد:
    - `timestamp`: زمانی که نمونه در آن برداشته شده است.
    - `stackId`: ایندکس یک عنصر در آرایهٔ `stacks`.
- `stacks`
  - : آرایه‌ای از اشیا که هر یک دو ویژگی دارد:
    - `frameId`: ایندکس یک عنصر در `frames` که درونی‌ترین فریم در پشته را نشان می‌دهد.
    - `parentId`: ایندکس یک ورودی دیگر در `stacks` که پشتهٔ فراخوانی را تا قبل از فریمِ متناظر با `frameId` (و بدون آن) نشان می‌دهد. اگر فریمِ متناظر با `frameId` در سطح بالای پشته بود، این ویژگی وجود ندارد.

## Example

در مثال زیر، یک صفحهٔ وب داریم که شامل یک دکمه است: وقتی کاربر دکمه را فشار دهد، صفحه تعدادی عدد اول تولید می‌کند.

HTML فقط شامل دکمه است:

```html
<button id="generate">generate!</button>
```

JavaScript بین دو فایل تقسیم شده است. اسکریپت «main.js» شامل کنترل‌کنندهٔ کلیک برای دکمه است. این کنترل‌کننده یک پروفایل را آغاز می‌کند، سپس کد تولید اعداد اول را فراخوانی می‌کند و در پایان پروفایل حاصل را در کنسول ثبت می‌کند:

```js
// main.js

import { genPrimes } from "./generate.js";

async function handleClick() {
  const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 10000 });

  const primes = genPrimes();
  console.log(`Finished generating ${primes.length} primes!`);

  const trace = await profiler.stop();
  console.log(JSON.stringify(trace));
}

document.querySelector("#generate").addEventListener("click", handleClick);
```

اسکریپت «generate.js» اعداد اول را تولید می‌کند و در دو تابع به نام‌های `genPrimes()` و `isPrime()` سازماندهی شده است:

```js
// generate.js

const MAX_PRIME = 1000000000;
const PRIMES_QUOTA = 10000;

function isPrime(n) {
  for (let i = 2; i <= Math.sqrt(n); i++) {
    if (n % i === 0) {
      return false;
    }
  }
  return n > 1;
}

export function genPrimes() {
  const primes = [];
  while (primes.length < PRIMES_QUOTA) {
    const candidate = Math.floor(Math.random() * MAX_PRIME);
    if (isPrime(candidate)) {
      primes.push(candidate);
    }
  }
  return primes;
}
```

اگر این کد را اجرا کنیم، پروفایلی مانند نمونهٔ زیر در کنسول ابزارهای توسعه‌دهنده ثبت می‌شود:

```json
{
  "frames": [
    { "name": "Profiler" },
    { "column": 27, "line": 5, "name": "handleClick", "resourceId": 0 },
    { "column": 17, "line": 6, "name": "isPrime", "resourceId": 1 },
    { "column": 26, "line": 15, "name": "genPrimes", "resourceId": 1 }
  ],
  "resources": [
    "http://localhost:3000/main.js",
    "http://localhost:3000/generate.js"
  ],
  "samples": [
    { "stackId": 1, "timestamp": 2972.734999999404 },
    { "stackId": 3, "timestamp": 2973.4899999946356 },
    { "stackId": 3, "timestamp": 2974.5700000077486 },
    { "stackId": 3, "timestamp": 2977.8649999946356 },
    { "stackId": 3, "timestamp": 2978.4899999946356 },
    { "stackId": 3, "timestamp": 2978.6950000077486 },
    { "stackId": 3, "timestamp": 2978.9500000029802 },
    { "stackId": 3, "timestamp": 2979.405000001192 },
    { "stackId": 2, "timestamp": 2980.030000001192 },
    { "stackId": 2, "timestamp": 2980.655000001192 }
  ],
  "stacks": [
    { "frameId": 1 },
    { "frameId": 0, "parentId": 0 },
    { "frameId": 3, "parentId": 0 },
    { "frameId": 2, "parentId": 2 }
  ]
}
```

این پروفایل ۱۰ نمونه را ضبط کرده است که در ویژگی `samples` فهرست شده‌اند.

ویژگی `stackId` هر نمونه به ما امکان می‌دهد بفهمیم برنامه در لحظهٔ برداشته‌شدن نمونه در چه مکانی بوده است؛ و در این مورد، نمونه‌ها در سه مکان مختلف برداشته شده‌اند:

- `stackId: 1`: یک نمونه
- `stackId: 3`: هفت نمونه
- `stackId: 2`: دو نمونه

برای یافتن پشتهٔ فراخوانی کامل یک نمونه، پشته را با استفاده از `stackId` بازیابی می‌کنیم، سپس از مقدار `frameId` در پشته برای یافتن درونی‌ترین تابع استفاده می‌کنیم و پس از آن، با استفاده از `parentId`، پشته‌های والد را به‌صورت بازگشتی واکشی می‌کنیم تا به سطح بالایی برسیم که مقدار `parentId` ندارد.

برای مثال، نمودار زیر نشان می‌دهد که چگونه می‌توانیم پشتهٔ فراخوانی کامل را برای هفت نمونه‌ای که `stackId` آن‌ها ۳ است به دست آوریم:

![Deriving a call stack from a sample](profile-format.svg)

همچنین توجه داشته باشید که اولین آیتم در `frames`، که مقدار `name` آن `Profiler` است، نمونه‌ای را نشان می‌دهد که در سازندهٔ {{domxref("Profiler.Profiler", "Profiler()")}} گرفته شده است: از آنجا که این یک تابع ارائه‌شده توسط مرورگر است، فریم شامل اطلاعات اسکریپت نیست.