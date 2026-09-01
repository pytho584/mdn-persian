---
title: "Element: ariaLive property"
---

---
title: "Element: ariaLive property"
short-title: ariaLive
slug: Web/API/Element/ariaLive
page-type: web-api-instance-property
browser-compat: api.Element.ariaLive
---

{{APIRef("DOM")}}

ویژگی **`ariaLive`** در رابط {{domxref("Element")}} منعکس‌کننده‌ی مقدار ویژگی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) است. این ویژگی نشان می‌دهد که یک عنصر به‌روزرسانی خواهد شد و انواع به‌روزرسانی‌هایی را توصیف می‌کند که عامل‌های کاربر (user agents)، فناوری‌های کمکی و کاربر می‌توانند از [منطقه‌ی زنده (live region)](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) انتظار داشته باشند.

## مقدار

یک رشته (string) با یکی از مقادیر زیر:

- `"assertive"`
  - : نشان می‌دهد که به‌روزرسانی‌های منطقه بالاترین اولویت را دارند و باید بلافاصله به کاربر ارائه شوند.
- `"off"`
  - : نشان می‌دهد که به‌روزرسانی‌های منطقه نباید به کاربر ارائه شوند، مگر اینکه کاربر در حال حاضر روی آن منطقه تمرکز (فوکوس) داشته باشد.
- `"polite"`
  - : نشان می‌دهد که به‌روزرسانی‌های منطقه باید در نخستین فرصت مناسب ارائه شوند؛ مانند پایان جمله‌ی در حال گفتار یا زمانی که کاربر تایپ را متوقف می‌کند.

## مثال‌ها

در این مثال، ویژگی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) روی عنصری با شناسه‌ی `planetInfo` روی `"polite"` تنظیم شده است. سپس مقدار آن را به `"assertive"` تغییر می‌دهیم.

```html
<div role="region" id="planetInfo" aria-live="polite">
  <h2 id="planetTitle">No planet selected</h2>
  <p id="planetDescription">Select a planet to view its description</p>
</div>
```

```js
let el = document.getElementById("planetInfo");
console.log(el.ariaLive); // "polite"
el.ariaLive = "assertive";
console.log(el.ariaLive); // "assertive"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}