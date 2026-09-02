---
title: "KeyboardEvent: location property"
short-title: location
slug: Web/API/KeyboardEvent/location
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.location
---

{{APIRef("UI Events")}}

ویژگی فقط-خواندنی **`KeyboardEvent.location`** یک عدد صحیح بدون علامت (`unsigned long`) را برمی‌گرداند که مکان کلید روی صفحه‌کلید یا دیگر دستگاه ورودی را نشان می‌دهد.

مقادیر ممکن عبارتند از:

<table class="standard-table">
  <thead>
    <tr>
      <th>ثابت</th>
      <th>مقدار</th>
      <th>توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>DOM_KEY_LOCATION_STANDARD</code></td>
      <td>0</td>
      <td>
        کلید فقط یک نسخه دارد، یا بین نسخه‌های چپ و راست قابل تشخیص نیست، و روی صفحه‌کلید عددی یا کلیدی که بخشی از صفحه‌کلید عددی محسوب می‌شود فشار داده نشده است.
      </td>
    </tr>
    <tr>
      <td><code>DOM_KEY_LOCATION_LEFT</code></td>
      <td>1</td>
      <td>
        کلید نسخه‌ی چپ بود؛ برای مثال، کلید چپ <kbd>Control</kbd> روی یک صفحه‌کلید استاندارد ۱۰۱ کلیدی آمریکایی فشار داده شد. این مقدار فقط برای کلیدهایی استفاده می‌شود که بیش از یک موقعیت ممکن روی صفحه‌کلید دارند.
      </td>
    </tr>
    <tr>
      <td><code>DOM_KEY_LOCATION_RIGHT</code></td>
      <td>2</td>
      <td>
        کلید نسخه‌ی راست بود؛ برای مثال، کلید راست <kbd>Control</kbd> روی یک صفحه‌کلید استاندارد ۱۰۱ کلیدی آمریکایی فشار داده شد. این مقدار فقط برای کلیدهایی استفاده می‌شود که بیش از یک موقعیت ممکن روی صفحه‌کلید دارند.
      </td>
    </tr>
    <tr>
      <td><code>DOM_KEY_LOCATION_NUMPAD</code></td>
      <td>3</td>
      <td>
        <p>
          کلید روی صفحه‌کلید عددی بود، یا کد کلید مجازی‌ای دارد که با صفحه‌کلید عددی مطابقت دارد.
        </p>
        <div class="note">
          <p>
            <strong>توجه:</strong> وقتی <kbd>NumLock</kbd> قفل است، فایرفاکس همیشه برای کلیدهای روی صفحه‌کلید عددی <code>DOM_KEY_LOCATION_NUMPAD</code> را برمی‌گرداند. در غیر این صورت، وقتی <kbd>NumLock</kbd> باز است و صفحه‌کلید واقعاً صفحه‌کلید عددی دارد، فایرفاکس همیشه <code>DOM_KEY_LOCATION_NUMPAD</code> را نیز برمی‌گرداند. از سوی دیگر، اگر صفحه‌کلید فاقد صفحه‌کلید عددی باشد، مثلاً در یک لپ‌تاپ، برخی کلیدها فقط وقتی NumLock قفل است، به صفحه‌کلید عددی تبدیل می‌شوند. وقتی چنین کلیدهایی رویدادهای کلید را ایجاد می‌کنند، مقدار ویژگی location به کلید بستگی دارد. یعنی نباید <code>DOM_KEY_LOCATION_NUMPAD</code> باشد.
          </p>
        </div>
        <div class="note">
          <p>
            <strong>توجه:</strong> رویدادهای کلید <kbd>NumLock</kbd> هم در فایرفاکس و هم در اینترنت اکسپلورر <code>DOM_KEY_LOCATION_STANDARD</code> را نشان می‌دهند.
          </p>
        </div>
      </td>
    </tr>
    <tr>
      <td>
        <code>DOM_KEY_LOCATION_MOBILE</code>
        {{Non-standard_inline()}} {{deprecated_inline}}
      </td>
      <td>4</td>
      <td>
        <p>
          کلید روی یک دستگاه همراه بود؛ این می‌تواند روی صفحه‌کلید فیزیکی یا صفحه‌کلید مجازی باشد.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code>DOM_KEY_LOCATION_JOYSTICK</code> {{Non-standard_inline()}}
        {{deprecated_inline}}
      </td>
      <td>5</td>
      <td>
        <p>
          کلید یک دکمه روی کنترل‌کننده بازی یا یک جوی‌استیک روی دستگاه همراه بود.
        </p>
      </td>
    </tr>
  </tbody>
</table>

## مقدار

یک عدد.

## مثال‌ها

```js
function keyEvent(event) {
  console.log(`Location of key pressed: ${event.location}`);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("KeyboardEvent")}}