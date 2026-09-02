---
title: "KeyboardEvent: getModifierState() method"
---

---
title: "KeyboardEvent: getModifierState() method"
short-title: getModifierState()
slug: Web/API/KeyboardEvent/getModifierState
page-type: web-api-instance-method
browser-compat: api.KeyboardEvent.getModifierState
---

{{APIRef("UI Events")}}

متد **`KeyboardEvent.getModifierState()`** وضعیت فعلی کلید اصلاح‌کنندهٔ مشخص‌شده را برمی‌گرداند: اگر کلید اصلاح‌کننده فعال باشد (یعنی کلید اصلاح‌کننده فشار داده شده یا قفل باشد) مقدار `true` و در غیر این صورت مقدار `false` برگردانده می‌شود.

## نحو

```js-nolint
getModifierState(key)
```

### پارامترها

- `key`
  - : یک مقدار کلید اصلاح‌کننده. این مقدار باید یکی از مقادیر {{domxref("KeyboardEvent.key")}} باشد که کلیدهای اصلاح‌کننده را نمایش می‌دهند، یا رشته `"Accel"` {{deprecated_inline}}. این مقدار به بزرگی/کوچکی حروف حساس است.

### مقدار بازگشتی

یک مقدار بولین.

## کلیدهای اصلاح‌کننده در فایرفاکس

چه زمانی `getModifierState()` در فایرفاکس مقدار `true` برمی‌گرداند؟

<table class="standard-table">
  <thead>
    <tr>
      <th scope="row"></th>
      <th scope="col">Windows</th>
      <th scope="col">Linux (GTK)</th>
      <th scope="col">Mac</th>
      <th scope="col">Android 2.3</th>
      <th scope="col">Android 3.0 یا بالاتر</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row"><code>"Alt"</code></th>
      <td>فشردن کلید <kbd>Alt</kbd> یا کلید <kbd>AltGr</kbd></td>
      <td>فشردن کلید <kbd>Alt</kbd></td>
      <td>فشردن کلید <kbd>⌥ Option</kbd></td>
      <td colspan="2">فشردن کلید <kbd>Alt</kbd> یا کلید <kbd>option</kbd></td>
    </tr>
    <tr>
      <th scope="row"><code>"AltGraph"</code></th>
      <td>
        <p>
          هر دو کلید <kbd>Alt</kbd> و <kbd>Ctrl</kbd> فشار داده شده باشند، یا کلید <kbd>AltGr</kbd> فشار داده شده باشد
        </p>
      </td>
      <td>
        فشردن کلید <kbd>Level 3 Shift</kbd> (یا کلید <kbd>Level 5 Shift</kbd>)
      </td>
      <td>فشردن کلید <kbd>⌥ Option</kbd></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
    <tr>
      <th scope="row"><code>"CapsLock"</code></th>
      <td colspan="3">در حالی که چراغ LED کلید <kbd>⇪ Caps Lock</kbd> روشن است</td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>در حالی که <kbd>CapsLock</kbd> قفل است</td>
    </tr>
    <tr>
      <th scope="row"><code>"Control"</code></th>
      <td>فشردن کلید <kbd>Ctrl</kbd> یا کلید <kbd>AltGr</kbd></td>
      <td>فشردن کلید <kbd>Ctrl</kbd></td>
      <td>فشردن کلید <kbd>control</kbd></td>
      <td>فشردن کلید <kbd>menu</kbd>.</td>
      <td>
        فشردن کلید <kbd>Ctrl</kbd>، کلید <kbd>control</kbd> یا کلید <kbd>menu</kbd>.
      </td>
    </tr>
    <tr>
      <th scope="row"><code>"Fn"</code></th>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>
        کلید <kbd>Function</kbd> فشار داده شده است، اما مطمئن نیستیم کدام کلید وضعیت اصلاح‌کننده را فعال می‌کند. کلید <kbd>Fn</kbd> در صفحه‌کلید Mac باعث فعال شدن این حالت نمی‌شود.
      </td>
    </tr>
    <tr>
      <th scope="row"><code>"FnLock"</code></th>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
    <tr>
      <th scope="row"><code>"Hyper"</code></th>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
    <tr>
      <th scope="row"><code>"Meta"</code></th>
      <td>فشردن کلید <kbd>⊞ Windows Logo</kbd> (از فایرفاکس 118)</td>
      <td>فشردن کلید <kbd>Meta</kbd></td>
      <td>فشردن کلید <kbd>⌘ Command</kbd></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>فشردن کلید <kbd>⊞ Windows Logo</kbd> یا کلید <kbd>command</kbd></td>
    </tr>
    <tr>
      <th scope="row"><code>"NumLock"</code></th>
      <td colspan="2">در حالی که چراغ LED کلید <kbd>Num Lock</kbd> روشن است</td>
      <td>فشردن یک کلید در صفحه‌کلید عددی (numpad)</td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>در حالی که <kbd>NumLock</kbd> قفل است</td>
    </tr>
    <tr>
      <th scope="row"><code>"OS"</code></th>
      <td>فشردن کلید <kbd>⊞ Windows Logo</kbd> (قبل از فایرفاکس 118)</td>
      <td>
        فشردن کلید <kbd>Super</kbd> یا کلید <kbd>Hyper</kbd> (معمولاً به کلید <kbd>⊞ Windows Logo</kbd> نگاشت می‌شود)
      </td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
    <tr>
      <th scope="row"><code>"ScrollLock"</code></th>
      <td>در حالی که چراغ LED کلید <kbd>Scroll Lock</kbd> روشن است</td>
      <td>
        در حالی که چراغ LED کلید <kbd>Scroll Lock</kbd> روشن است، اما معمولاً این مورد توسط سیستم‌عامل پشتیبانی نمی‌شود
      </td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>در حالی که <kbd>ScrollLock</kbd> قفل است</td>
    </tr>
    <tr>
      <th scope="row"><code>"Shift"</code></th>
      <td colspan="5">فشردن کلید <kbd>⇧ Shift</kbd></td>
    </tr>
    <tr>
      <th scope="row"><code>"Super"</code></th>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
    <tr>
      <th scope="row"><code>"Symbol"</code></th>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
    <tr>
      <th scope="row"><code>"SymbolLock"</code></th>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
      <td>❌ <em>پشتیبانی نمی‌شود</em></td>
    </tr>
  </tbody>
</table>

- در سایر پلتفرم‌ها، «Alt»، «Control» و «Shift» ممکن است پشتیبانی شوند.
- همه اصلاح‌کننده‌ها (به‌جز `"FnLock"`، `"Hyper"`، `"Super"` و `"Symbol"` که بعد از پیاده‌سازی این قابلیت در فایرفاکس تعریف شده‌اند) همیشه برای رویدادهای غیرقابل اعتماد (untrusted) در فایرفاکس پشتیبانی می‌شوند. این موضوع به پلتفرم بستگی ندارد.

## اصلاح‌کننده مجازی `"Accel"`

> [!NOTE]
> اصلاح‌کننده مجازی `"Accel"` عملاً در پیش‌نویس‌های فعلی مشخصات DOM3 Events **منسوخ (deprecated)** شده است.

متد `getModifierState()` همچنین یک اصلاح‌کننده مجازی منسوخ به نام `"Accel"` را می‌پذیرد. `event.getModifierState("Accel")` زمانی مقدار `true` برمی‌گرداند که حداقل یکی از {{domxref("KeyboardEvent.ctrlKey")}} یا {{domxref("KeyboardEvent.metaKey")}} برابر `true` باشد.

در پیاده‌سازی‌های قدیمی و مشخصات منسوخ، این متد زمانی `true` برمی‌گرداند که کلید اصلاح‌کنندهٔ معمول برای کلید میانبر فشار داده شده باشد. برای مثال، در Windows فشردن کلید <kbd>Ctrl</kbd> ممکن است باعث برگرداندن `true` شود. با این حال، در Mac فشردن کلید <kbd>⌘ Command</kbd> ممکن است باعث برگرداندن `true` شود. توجه داشته باشید که اینکه کدام کلید اصلاح‌کننده باعث بازگرداندن `true` می‌شود به پلتفرم، مرورگر و تنظیمات کاربر بستگی دارد. برای مثال، کاربران فایرفاکس می‌توانند این رفتار را با یک ترجیح (pref) به نام `"ui.key.accelKey"` سفارشی‌سازی کنند.

## مثال‌ها

```js
function handleKeyboardEvent(event) {
  // Ignore if following modifier is active.
  if (
    event.getModifierState("Fn") ||
    event.getModifierState("Hyper") ||
    event.getModifierState("OS") ||
    event.getModifierState("Super") ||
    event.getModifierState("Win") /* hack for IE */
  ) {
    return;
  }

  // Also ignore if two or more modifiers except Shift are active.
  if (
    event.getModifierState("Control") +
      event.getModifierState("Alt") +
      event.getModifierState("Meta") >
    1
  ) {
    return;
  }

  // Handle shortcut key with standard modifier
  if (event.getModifierState("Accel")) {
    switch (event.key.toLowerCase()) {
      case "c":
        if (event.getModifierState("Shift")) {
          // Handle Accel + Shift + C
          event.preventDefault(); // consume the key event
        }
        break;
      case "k":
        if (!event.getModifierState("Shift")) {
          // Handle Accel + K
          event.preventDefault(); // consume the key event
        }
        break;
    }
    return;
  }

  // Do something different for arrow keys if ScrollLock is locked.
  if (
    (event.getModifierState("ScrollLock") ||
      event.getModifierState("Scroll")) /* hack for IE */ &&
    !event.getModifierState("Control") &&
    !event.getModifierState("Alt") &&
    !event.getModifierState("Meta")
  ) {
    switch (event.key) {
      case "ArrowDown":
      case "Down": // hack for IE and old Firefox
        event.preventDefault(); // consume the key event
        break;
      case "ArrowLeft":
      case "Left": // hack for IE and old Firefox
        // Do something different if ScrollLock is locked.
        event.preventDefault(); // consume the key event
        break;
      case "ArrowRight":
      case "Right": // hack for IE and old Firefox
        // Do something different if ScrollLock is locked.
        event.preventDefault(); // consume the key event
        break;
      case "ArrowUp":
      case "Up": // hack for IE and old Firefox
        // Do something different if ScrollLock is locked.
        event.preventDefault(); // consume the key event
        break;
    }
  }
}
```

> [!NOTE]
> اگرچه این مثال از `.getModifierState()` با `"Alt"`، `"Control"`، `"Meta"` و `"Shift"` استفاده می‌کند، استفاده از `event.altKey`، `event.ctrlKey`، `event.metaKey` و `event.shiftKey` ممکن است ترجیح داده شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("KeyboardEvent")}} که این متد به آن تعلق دارد.
- {{domxref("MouseEvent.getModifierState")}}