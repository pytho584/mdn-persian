---
title: "Navigator: requestMIDIAccess() method"
short-title: requestMIDIAccess()
slug: Web/API/Navigator/requestMIDIAccess
page-type: web-api-instance-method
browser-compat: api.Navigator.requestMIDIAccess
---

{{APIRef("Web MIDI API")}}{{SecureContext_Header}}

متد **`requestMIDIAccess()`** از رابط {{domxref('Navigator')}} یک {{jsxref('Promise')}} برمی‌گرداند که نمایانگر درخواست دسترسی به دستگاه‌های MIDI در سیستم کاربر است. این متد بخشی از [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API) است که راهی برای دسترسی، شمارش و دستکاری دستگاه‌های MIDI فراهم می‌کند.

این متد ممکن است از کاربر برای دسترسی به دستگاه‌های MIDI موجود در سیستمش درخواست مجوز کند، یا ممکن است از یک ترجیح قبلاً تعیین‌شده برای اعطا یا رد دسترسی استفاده کند. اگر مجوز داده شود، {{jsxref('Promise')}} حل می‌شود و یک شیء [`MIDIAccess`](/en-US/docs/Web/API/MIDIAccess) برگردانده می‌شود.

## نحو (Syntax)

```js-nolint
requestMIDIAccess()
requestMIDIAccess(MIDIOptions)
```

### پارامترها

- `MIDIOptions` {{optional_inline}}
  - : یک {{jsxref('Object')}} که گزینه‌هایی را برای ارسال به متد نشان می‌دهد. این گزینه‌ها عبارتند از:
    - `sysex`
      - : یک مقدار {{jsxref('Boolean')}} که اگر `true` تنظیم شود، امکان ارسال و دریافت پیام‌های سیستمی اختصاصی (sysex) را فراهم می‌کند. مقدار پیش‌فرض `false` است.
    - `software`
      - : یک مقدار {{jsxref('Boolean')}} که اگر `true` تنظیم شود، به سیستم اجازه می‌دهد از هر سینت‌سایزر نرم‌افزاری نصب‌شده استفاده کند. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که با یک شیء [`MIDIAccess`](/en-US/docs/Web/API/MIDIAccess) حل می‌شود.

### استثناها (Exceptions)

- `AbortError` {{domxref("DOMException")}}
  - : در صورت بسته شدن سند یا صفحه به دلیل پیمایش کاربر (navigation) پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورت بروز هر خطایی از سوی سیستم زیرین پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در صورت پشتیبانی نشدن ویژگی یا گزینه‌ها توسط سیستم پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی که کاربر یا سیستم از ایجاد یک شیء [MIDIAccess](/en-US/docs/Web/API/MIDIAccess) با گزینه‌های درخواستی جلوگیری کند، یا اگر سند مجاز به استفاده از این ویژگی نباشد (مثلاً به دلیل [Permission Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) یا اینکه کاربر قبلاً درخواست مجوز را رد کرده است) پرتاب می‌شود.

## الزامات امنیتی

دسترسی به API مشروط به محدودیت‌های زیر است:

- متد باید در یک [زمینه امن (secure context)](/en-US/docs/Web/Security/Defenses/Secure_Contexts) فراخوانی شود.
- دسترسی ممکن است توسط [Permission Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) HTTP به نام [`midi`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/midi) محدود شود.
- کاربر باید صریحاً مجوز استفاده از API را از طریق یک مکانیزم خاص عامل کاربر (user-agent) اعطا کند، یا قبلاً مجوز داده باشد.
  توجه داشته باشید که اگر دسترسی توسط یک permission policy رد شود، نمی‌توان آن را با مجوز کاربر اعطا کرد.

وضعیت مجوز را می‌توان با استفاده از متد [Permissions API](/en-US/docs/Web/API/Permissions_API) به نام [`navigator.permissions.query()`](/en-US/docs/Web/API/Permissions/query) پرس‌وجو کرد، و یک توصیف‌گر مجوز با permission `midi` و ویژگی (اختیاری) `sysex` به آن داد:

```js
navigator.permissions.query({ name: "midi", sysex: true }).then((result) => {
  if (result.state === "granted") {
    // دسترسی اعطا شد.
  } else if (result.state === "prompt") {
    // استفاده از API باعث درخواست مجوز خواهد شد
  }
  // مجوز توسط درخواست کاربر یا permission policy رد شد
});
```

## مثال‌ها

### درخواست دسترسی MIDI

در مثال زیر، متد `Navigator.requestMIDIAccess()` شیء {{domxref("MIDIAccess")}} را برمی‌گرداند که دسترسی به اطلاعات پورت‌های ورودی و خروجی MIDI را فراهم می‌کند.

```js
navigator.requestMIDIAccess().then((access) => {
  // دریافت لیست کنترل‌کننده‌های MIDI موجود
  const inputs = access.inputs.values();
  const outputs = access.outputs.values();
  // …
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API)
- [Introduction to Web MIDI](https://code.tutsplus.com/introduction-to-web-midi--cms-25220t)