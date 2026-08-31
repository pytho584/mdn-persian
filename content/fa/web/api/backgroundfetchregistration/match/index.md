---
title: "BackgroundFetchRegistration: match() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/match"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: match() method"
short-title: match()
slug: Web/API/BackgroundFetchRegistration/match
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.match
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`match()`** از رابط {{domxref("BackgroundFetchRegistration")}} اولین {{domxref("BackgroundFetchRecord")}} منطبق را بازمی‌گرداند.

## نحو

```js-nolint
match(request)
match(request, options)
```

### پارامترها

- `request`
  - : {{domxref("Request")}} که برای آن تلاش می‌کنید رکوردهایی را بیابید.
    این می‌تواند یک شیء {{domxref("Request")}} یا یک URL باشد.
- `options` {{optional_inline}}
  - : یک شیء که گزینه‌هایی را برای عملیات `match` تنظیم می‌کند. گزینه‌های موجود عبارتند از:
    - `ignoreSearch` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا رشته جستجو در URL نادیده گرفته شود یا خیر. به عنوان مثال، اگر روی `true` تنظیم شود، قسمت `?value=bar` از `https://example.com/?value=bar` هنگام انجام تطبیق نادیده گرفته می‌شود. مقدار پیش‌فرض `false` است.
    - `ignoreMethod` {{optional_inline}}
      - : یک مقدار بولی. وقتی `true` باشد، از اعتبارسنجی متد HTTP {{domxref("Request")}} توسط عملیات تطبیق جلوگیری می‌کند. اگر `false` (پیش‌فرض) باشد، فقط `GET` و `HEAD` مجاز هستند.
    - `ignoreVary` {{optional_inline}}
      - : یک مقدار بولی. وقتی `true` باشد، نشان می‌دهد که هدر {{HTTPHeader("Vary")}} باید نادیده گرفته شود. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با اولین {{domxref("BackgroundFetchRecord")}} که با درخواست مطابقت دارد، حل می‌شود، یا اگر هیچ تطبیقی یافت نشود، {{jsxref("undefined")}}.

> [!NOTE]
> `BackgroundFetchRegistration.match()` اساساً مشابه {{domxref("BackgroundFetchRegistration.matchAll()")}} است، با این تفاوت که به جای حل شدن با یک آرایه از تمام رکوردهای منطبق، تنها با اولین رکورد منطبق حل می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `match()` را زمانی که هیچ واکشی در حال انجام نیست فراخوانی کنید، بازگردانده می‌شود. این حالت با تنظیم شدن {{domxref("BackgroundFetchRegistration.recordsAvailable")}} روی `false` منعکس می‌شود.

## مثال‌ها

در این مثال، ما به دنبال رکوردی با URL "/ep-5.mp3" می‌گردیم. اگر یک {{domxref("BackgroundFetchRecord")}} پیدا شود، می‌توانیم برخی اطلاعات در مورد آن را بازگردانیم.

```js
bgFetch.match("/ep-5.mp3").then(async (record) => {
  if (!record) {
    console.log("No record found");
    return;
  }

  console.log(`Here's the request`, record.request);
  const response = await record.responseReady;
  console.log(`And here's the response`, response);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}