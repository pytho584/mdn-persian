---
title: "Performance: measureUserAgentSpecificMemory() method"
short-title: measureUserAgentSpecificMemory()
slug: Web/API/Performance/measureUserAgentSpecificMemory
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Performance.measureUserAgentSpecificMemory
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`measureUserAgentSpecificMemory()`** برای تخمین میزان حافظه‌ی مصرفی یک برنامه‌ی وب، شامل تمام iframeها و workerهای آن، استفاده می‌شود.

## نحو (Syntax)

```js-nolint
measureUserAgentSpecificMemory()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به شیءای شامل ویژگی‌های زیر resolve می‌شود:

- `bytes`
  - : عددی که میزان کل حافظه‌ی مصرفی را نشان می‌دهد.
- `breakdown`
  - : یک {{jsxref("Array")}} از اشیاء که کل `bytes` را بخش‌بندی کرده و اطلاعات مربوط به تخصیص (attribution) و نوع حافظه را فراهم می‌کند. این شیء شامل ویژگی‌های زیر است:
    - `bytes`
      - : اندازه‌ی حافظه‌ای که این ورودی توصیف می‌کند.
    - `attribution`
      - : یک {{jsxref("Array")}} از عناصر ظرف (container) مربوط به قلمروهای جاوااسکریپت (JavaScript realms) که از این حافظه استفاده می‌کنند. این شیء ویژگی‌های زیر را دارد:
        - `url`
          - : اگر این انتساب مربوط به یک قلمرو جاوااسکریپت هم‌خاستگاه (same-origin) باشد، این ویژگی شامل URL آن قلمرو است. در غیر این صورت، رشته‌ی `"cross-origin-url"` است.
        - `container`
          - : شیءای که عنصر DOM شامل این قلمرو جاوااسکریپت را توصیف می‌کند. این شیء ویژگی‌های زیر را دارد:
            - `id`
              - : ویژگی `id` عنصر ظرف.
            - `src`
              - : ویژگی `src` عنصر ظرف. اگر عنصر ظرف یک عنصر {{HTMLElement("object")}} باشد، این فیلد حاوی مقدار ویژگی `data` است.
        - `scope`
          - : رشته‌ای که نوع قلمرو جاوااسکریپت هم‌خاستگاه را توصیف می‌کند: `"Window"`، `"DedicatedWorkerGlobalScope"`، `"SharedWorkerGlobalScope"`، `"ServiceWorkerGlobalScope"` یا در مورد cross-origin، `"cross-origin-aggregated"`.
    - `types`
      - : آرایه‌ای از انواع حافظه‌ی تعریف‌شده توسط پیاده‌سازی (implementation-defined) که با این حافظه مرتبط هستند.

یک مثال از مقدار بازگشتی به این شکل است:

```json
{
  "bytes": 1500000,
  "breakdown": [
    {
      "bytes": 1000000,
      "attribution": [
        {
          "url": "https://example.com",
          "scope": "Window"
        }
      ],
      "types": ["DOM", "JS"]
    },
    {
      "bytes": 0,
      "attribution": [],
      "types": []
    },
    {
      "bytes": 500000,
      "attribution": [
        {
          "url": "https://example.com/iframe.html",
          "container": {
            "id": "example-id",
            "src": "redirect.html?target=iframe.html"
          },
          "scope": "Window"
        }
      ],
      "types": ["JS", "DOM"]
    }
  ]
}
```

### استثناها (Exceptions)

- `SecurityError` {{domxref("DOMException")}}
  - : اگر [الزامات امنیتی](#security_requirements) برای جلوگیری از نشت اطلاعات بین‌خاستگاهی (cross-origin) برآورده نشوند، پرتاب می‌شود.

## توضیحات

مرورگر هنگام ایجاد اشیاء به‌طور خودکار حافظه اختصاص می‌دهد و وقتی دیگر به آن‌ها دسترسی نباشد (جمع‌آوری زباله)، حافظه را آزاد می‌کند. این جمع‌آوری زباله (GC) یک تقریب است، زیرا مسئله‌ی کلی تعیین اینکه آیا یک قطعه‌ی خاص از حافظه هنوز مورد نیاز است یا نه، غیرممکن است (همچنین به [مدیریت حافظه‌ی جاوااسکریپت](/en-US/docs/Web/JavaScript/Guide/Memory_management) مراجعه کنید). توسعه‌دهندگان باید اطمینان حاصل کنند که اشیاء جمع‌آوری می‌شوند، حافظه نشت نمی‌کند، و مصرف حافظه در طول زمان به‌طور غیرضروری رشد نمی‌کند که منجر به برنامه‌های وب کند و بی‌پاسخ شود. نشت حافظه معمولاً در اثر فراموش کردن لغو ثبت یک شنونده‌ی رویداد (event listener)، نبستن یک worker، انباشتن اشیاء در آرایه‌ها و موارد دیگر ایجاد می‌شود.

API `measureUserAgentSpecificMemory()` داده‌های مصرف حافظه را جمع‌آوری می‌کند تا به شما در یافتن نشت حافظه کمک کند. می‌توان از آن برای تشخیص بازگشت مشکلات حافظه (memory regression) یا برای آزمایش A/B ویژگی‌ها به منظور ارزیابی تأثیر آن‌ها بر حافظه استفاده کرد. بهتر است به‌جای فراخوانی‌های تکی این متد، فراخوانی‌های دوره‌ای انجام دهید تا تغییرات مصرف حافظه در طول یک نشست (session) پیگیری شود.

مقادیر `byte` که این API برمی‌گرداند در بین مرورگرهای مختلف یا بین نسخه‌های مختلف یک مرورگر قابل مقایسه نیستند، زیرا این مقادیر به شدت به پیاده‌سازی وابسته هستند. همچنین نحوه‌ی ارائه‌ی آرایه‌های `breakdown` و `attribution` نیز به مرورگر بستگی دارد. بهتر است هیچ فرض ثابت و از پیش تعیین‌شده‌ای درباره‌ی این داده‌ها نداشته باشید. این API بیشتر برای فراخوانی دوره‌ای (با فاصله‌ی زمانی تصادفی) طراحی شده است تا داده‌ها جمع‌آوری و تفاوت بین نمونه‌ها تحلیل شود.

## الزامات امنیتی

برای استفاده از این متد، سند شما باید در یک [بافت امن (secure context)](/en-US/docs/Web/Security/Defenses/Secure_Contexts) باشد و همچنین {{domxref("Window.crossOriginIsolated","cross-origin isolated","","nocode")}} باشد.

می‌توانید از ویژگی‌های {{domxref("Window.crossOriginIsolated")}} و {{domxref("WorkerGlobalScope.crossOriginIsolated")}} برای بررسی اینکه آیا سند cross-origin isolated است استفاده کنید:

```js
if (crossOriginIsolated) {
  // استفاده از measureUserAgentSpecificMemory
}
```

## مثال‌ها

### نظارت بر مصرف حافظه

کد زیر نحوه‌ی فراخوانی متد `measureUserAgentSpecificMemory()` را هر پنج دقیقه با یک فاصله‌ی زمانی تصادفی با استفاده از [توزیع نمایی (Exponential distribution)](https://en.wikipedia.org/wiki/Exponential_distribution#Random_variate_generation) نشان می‌دهد.

```js
function runMemoryMeasurements() {
  const interval = -Math.log(Math.random()) * 5 * 60 * 1000;
  console.log(`Next measurement in ${Math.round(interval / 1000)} seconds.`);
  setTimeout(measureMemory, interval);
}

async function measureMemory() {
  const memorySample = await performance.measureUserAgentSpecificMemory();
  console.log(memorySample);
  runMemoryMeasurements();
}

if (crossOriginIsolated) {
  runMemoryMeasurements();
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Window.setTimeout", "setTimeout()")}}
- [Monitor your web page's total memory usage with measureUserAgentSpecificMemory() - web.dev](https://web.dev/articles/monitor-total-page-memory-usage)