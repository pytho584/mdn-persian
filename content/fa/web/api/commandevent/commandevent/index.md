---
title: "CommandEvent: CommandEvent() constructor"
---

---
title: "CommandEvent: CommandEvent() constructor"
short-title: CommandEvent()
slug: Web/API/CommandEvent/CommandEvent
page-type: web-api-constructor
browser-compat: api.CommandEvent.CommandEvent
---

{{APIRef("Invoker Commands API")}}

سازندهٔ **`CommandEvent()`** یک شیء {{domxref("CommandEvent")}} جدید ایجاد می‌کند.

## نحو

```js-nolint
new CommandEvent(type)
new CommandEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته با نام رویداد.
    به بزرگی یا کوچکی حروف حساس است و مرورگرها آن را روی `command` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `source` {{optional_inline}}
      - : یک {{domxref("HTMLButtonElement")}} که نشان‌دهندهٔ دکمه‌ای است که برای ایجاد این رویداد با آن تعامل شده است. این می‌تواند هر عنصری باشد، اما برای جلوگیری از نتایج غیرمنتظره، توصیه می‌کنیم فقط از دکمه به‌عنوان منبع استفاده کنید.
    - `command` {{optional_inline}}
      - : یک رشته حاوی دستوری که عنصر کنترل‌شده باید آن را اجرا کند. هنگام نمونه‌سازی دستی یک `CommandEvent` می‌توان از هر مقدار رشته‌ای استفاده کرد، اما توصیه می‌شود برای تضمین سازگاری با آینده، از یکی از نام‌های داخلی استفاده کنید یا آن را با دو خط تیره (`--`) پیشوند کنید.

### مقدار بازگشتی

یک شیء {{domxref("CommandEvent")}} جدید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Invoker Commands API", "Invoker Commands API", "", "nocode")}}
- {{domxref("HTMLButtonElement.command")}}
- {{domxref("HTMLButtonElement.commandForElement")}}
- {{domxref("CommandEvent")}}