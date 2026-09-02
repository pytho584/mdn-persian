---
title: "KeyboardEvent"
---

---
title: KeyboardEvent
slug: Web/API/KeyboardEvent
page-type: web-api-interface
browser-compat: api.KeyboardEvent
---

{{APIRef("UI Events")}}

اشیاء **`KeyboardEvent`** تعامل کاربر با صفحه‌کلید را توصیف می‌کنند؛ هر رویداد یک تعامل واحد بین کاربر و یک کلید (یا ترکیبی از یک کلید با کلیدهای اصلاح‌کننده) روی صفحه‌کلید را توصیف می‌کند. نوع رویداد ({{domxref("Element/keydown_event", "keydown")}}، {{domxref("Element/keypress_event", "keypress")}} یا {{domxref("Element/keyup_event", "keyup")}}) مشخص می‌کند که چه نوع فعالیت صفحه‌کلیدی رخ داده است.

> [!NOTE]
> رویدادهای `KeyboardEvent` فقط نشان می‌دهند که کاربر در سطح پایین با یک کلید روی صفحه‌کلید چه تعاملی داشته است و معنای زمینه‌ای برای آن تعامل ارائه نمی‌دهند. وقتی نیاز به مدیریت ورودی متن دارید، به‌جای آن از رویداد {{domxref("Element/input_event", "input")}} استفاده کنید. اگر کاربر از روش جایگزینی برای وارد کردن متن استفاده کند، مانند سیستم نوشتن دستی روی رایانه لوحی یا تبلت گرافیکی، ممکن است رویدادهای صفحه‌کلید فعال نشوند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("KeyboardEvent.KeyboardEvent", "KeyboardEvent()")}}
  - : یک شیء جدید `KeyboardEvent` می‌سازد.

## ثابت‌ها

رابط `KeyboardEvent` ثابت‌های زیر را تعریف می‌کند.

### مکان‌های صفحه‌کلید

ثابت‌های زیر مشخص می‌کنند که رویداد کلید از کدام بخش صفحه‌کلید منشأ گرفته است. آن‌ها به‌صورت `KeyboardEvent.DOM_KEY_LOCATION_STANDARD` و غیره در دسترس هستند.

<table class="standard-table">
  <caption>
    شناسه‌های مکان صفحه‌کلید
  </caption>
  <thead>
    <tr>
      <th scope="col">ثابت</th>
      <th scope="col">مقدار</th>
      <th scope="col">توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>DOM_KEY_LOCATION_STANDARD</code></td>
      <td>0x00</td>
      <td>
        <p>
          کلیدی که توسط رویداد توصیف می‌شود، در ناحیه خاصی از صفحه‌کلید قرار ندارد؛ روی صفحه‌کلید عددی قرار ندارد (مگر اینکه کلید NumLock باشد)، و برای کلیدهایی که در سمت چپ و راست صفحه‌کلید تکرار شده‌اند، آن کلید به هر دلیلی با آن مکان مرتبط نیست.
        </p>
        <p>
          نمونه‌ها شامل کلیدهای حروفی-عددی در صفحه‌کلید استاندارد PC 101 آمریکایی، کلید NumLock و نوار فاصله هستند.
        </p>
      </td>
    </tr>
    <tr>
      <td><code>DOM_KEY_LOCATION_LEFT</code></td>
      <td>0x01</td>
      <td>
        <p>
          این کلید یکی از کلیدهایی است که ممکن است در چندین مکان روی صفحه‌کلید وجود داشته باشد و در این مورد، در سمت چپ صفحه‌کلید قرار دارد.
        </p>
        <p>
          نمونه‌ها شامل کلید Control چپ، کلید Command چپ در صفحه‌کلید مکینتاش یا کلید Shift چپ هستند.
        </p>
      </td>
    </tr>
    <tr>
      <td><code>DOM_KEY_LOCATION_RIGHT</code></td>
      <td>0x02</td>
      <td>
        <p>
          این کلید یکی از کلیدهایی است که ممکن است در چندین موقعیت روی صفحه‌کلید وجود داشته باشد و در این مورد، در سمت راست صفحه‌کلید قرار دارد.
        </p>
        <p>
          نمونه‌ها شامل کلید Shift راست و کلید Alt راست (Option در صفحه‌کلید مک) هستند.
        </p>
      </td>
    </tr>
    <tr>
      <td><code>DOM_KEY_LOCATION_NUMPAD</code></td>
      <td>0x03</td>
      <td>
        <p>
          کلید روی صفحه‌کلید عددی قرار دارد، یا اگر بیش از یک مکان برای منشأ گرفتن کلید وجود داشته باشد، یک کلید مجازی مرتبط با صفحه‌کلید عددی است. کلید NumLock در این گروه قرار نمی‌گیرد و همیشه با مکان <code>DOM_KEY_LOCATION_STANDARD</code> کدگذاری می‌شود.
        </p>
        <p>
          نمونه‌ها شامل ارقام روی صفحه‌کلید عددی، کلید Enter صفحه‌کلید عددی و نقطه اعشار روی آن هستند.
        </p>
      </td>
    </tr>
  </tbody>
</table>

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های والدین خود، {{domxref("UIEvent")}} و {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("KeyboardEvent.altKey")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که اگر کلید <kbd>Alt</kbd> (<kbd>Option</kbd> یا <kbd>⌥</kbd> در macOS) هنگام تولید رویداد کلید فعال بود، `true` است.

- {{domxref("KeyboardEvent.code")}} {{ReadOnlyInline}}
  - : یک رشته شامل مقدار کد کلید فیزیکی نمایش‌داده‌شده توسط رویداد را برمی‌گرداند.

    > [!WARNING]
    > این ویژگی چیدمان صفحه‌کلید کاربر را نادیده می‌گیرد، بنابراین اگر کاربر کلید را در موقعیت «Y» در چیدمان صفحه‌کلید QWERTY فشار دهد (نزدیک وسط ردیف بالای ردیف اصلی)، همیشه «KeyY» برمی‌گرداند، حتی اگر کاربر صفحه‌کلید QWERTZ داشته باشد (که به این معنی است که کاربر انتظار «Z» را دارد و همه ویژگی‌های دیگر «Z» را نشان می‌دهند) یا چیدمان صفحه‌کلید Dvorak (که در آن کاربر انتظار «F» را دارد). اگر می‌خواهید ضربه‌های کلید صحیح را به کاربر نمایش دهید، می‌توانید از {{domxref("Keyboard.getLayoutMap()")}} استفاده کنید.

- {{domxref("KeyboardEvent.ctrlKey")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که اگر کلید <kbd>Ctrl</kbd> هنگام تولید رویداد کلید فعال بود، `true` است.

- {{domxref("KeyboardEvent.isComposing")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که اگر رویداد بین بعد از `compositionstart` و قبل از `compositionend` فعال شده باشد، `true` است.
- {{domxref("KeyboardEvent.key")}} {{ReadOnlyInline}}
  - : یک رشته نشان‌دهنده مقدار کلیدِ نمایش‌داده‌شده توسط رویداد را برمی‌گرداند.
- {{domxref("KeyboardEvent.location")}} {{ReadOnlyInline}}
  - : یک عدد نشان‌دهنده مکان کلید روی صفحه‌کلید یا سایر دستگاه‌های ورودی را برمی‌گرداند. فهرست ثابت‌های شناسایی مکان‌ها در بالا در [مکان‌های صفحه‌کلید](#keyboard_locations) نشان داده شده است.
- {{domxref("KeyboardEvent.metaKey")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که اگر کلید <kbd>Meta</kbd> (در صفحه‌کلیدهای مک، کلید <kbd>⌘ Command</kbd>؛ در صفحه‌کلیدهای ویندوز، کلید ویندوز (<kbd>⊞</kbd>)) هنگام تولید رویداد کلید فعال بود، `true` است.

- {{domxref("KeyboardEvent.repeat")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که اگر کلید به‌گونه‌ای نگه داشته شده باشد که به‌طور خودکار تکرار می‌شود، `true` است.
- {{domxref("KeyboardEvent.shiftKey")}} {{ReadOnlyInline}}
  - : یک مقدار بولین برمی‌گرداند که اگر کلید <kbd>Shift</kbd> هنگام تولید رویداد کلید فعال بود، `true` است.

### ویژگی‌های منسوخ

- {{domxref("KeyboardEvent.charCode")}} {{Deprecated_inline}} {{ReadOnlyInline}}
  - : یک عدد نشان‌دهنده شماره مرجع یونیکدِ کلید را برمی‌گرداند؛ این ویژگی فقط توسط رویداد `keypress` استفاده می‌شود. برای کلیدهایی که ویژگی `char` آن‌ها شامل چند نویسه است، این مقدار یونیکدِ اولین نویسه در آن ویژگی است. در Firefox 26 این مقدار کدهای نویسه‌های قابل‌چاپ را برمی‌گرداند.

- {{domxref("KeyboardEvent.keyCode")}} {{deprecated_inline}} {{ReadOnlyInline}}
  - : یک عدد نشان‌دهنده کد عددی وابسته به سیستم و پیاده‌سازی را برمی‌گرداند که مقدار اصلاح‌نشده کلید فشرده‌شده را شناسایی می‌کند.

- {{domxref("KeyboardEvent.keyIdentifier")}} {{Non-standard_inline}} {{deprecated_inline}} {{ReadOnlyInline}}
  - : این ویژگی غیراستاندارد است و به نفع {{domxref("KeyboardEvent.key")}} منسوخ شده است. این ویژگی بخشی از نسخه قدیمی DOM Level 3 Events بود.

## روش‌های نمونه

_این رابط همچنین روش‌های والدین خود، {{domxref("UIEvent")}} و {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("KeyboardEvent.getModifierState()")}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا هنگام ایجاد رویداد، یک کلید اصلاح‌کننده مانند <kbd>Alt</kbd>، <kbd>Shift</kbd>، <kbd>Ctrl</kbd> یا <kbd>Meta</kbd> فشرده شده بود یا خیر.

### روش‌های منسوخ

- {{domxref("KeyboardEvent.initKeyboardEvent()")}} {{deprecated_inline}}
  - : یک شیء `KeyboardEvent` را مقداردهی اولیه می‌کند. این روش اکنون منسوخ شده است. در عوض باید از سازنده {{domxref("KeyboardEvent.KeyboardEvent", "KeyboardEvent()")}} استفاده کنید.

## رویدادها

رویدادهای زیر بر اساس نوع `KeyboardEvent` هستند. در فهرست زیر، هر رویداد به مستندات مدیریت‌کننده `Element` برای آن رویداد پیوند می‌دهد که به‌طور کلی برای همه دریافت‌کننده‌ها، از جمله {{domxref("Element")}}، {{domxref("Document")}} و {{domxref("Window")}} کاربرد دارد.

- {{domxref("Element.keydown_event", "keydown")}}
  - : یک کلید فشرده شده است.
- {{domxref("Element.keyup_event", "keyup")}}
  - : یک کلید رها شده است.

### رویدادهای منسوخ

- {{domxref("Element.keypress_event", "keypress")}} {{deprecated_inline}}
  - : یک کلید که معمولاً یک مقدار نویسه تولید می‌کند، فشرده شده است. این رویداد به‌شدت به دستگاه وابسته بود و منسوخ شده است. نباید از آن استفاده کنید.

## نکات استفاده

سه نوع رویداد صفحه‌کلید وجود دارد: {{domxref("Element/keydown_event", "keydown")}}، {{domxref("Element/keypress_event", "keypress")}} و {{domxref("Element/keyup_event", "keyup")}}. برای بیشتر کلیدها، Gecko دنباله‌ای از رویدادهای کلید را به این ترتیب ارسال می‌کند:

1. وقتی کلید برای اولین بار فشرده می‌شود، رویداد `keydown` ارسال می‌شود.
2. اگر کلید یک کلید اصلاح‌کننده نباشد، رویداد `keypress` ارسال می‌شود.
3. وقتی کاربر کلید را رها می‌کند، رویداد `keyup` ارسال می‌شود.

### موارد خاص

برخی کلیدها وضعیت یک چراغ نشانگر را تغییر می‌دهند؛ این کلیدها شامل کلیدهایی مانند Caps Lock، Num Lock و Scroll Lock هستند. در ویندوز و لینوکس، این کلیدها فقط رویدادهای `keydown` و `keyup` را ارسال می‌کنند.

> [!NOTE]
> در لینوکس، Firefox 12 و نسخه‌های قبلی نیز رویداد `keypress` را برای این کلیدها ارسال می‌کردند.

با این حال، یک محدودیت در مدل رویداد macOS باعث می‌شود Caps Lock فقط رویداد `keydown` را ارسال کند. Num Lock در برخی مدل‌های قدیمی‌تر لپ‌تاپ (مدل‌های ۲۰۰۷ و قدیمی‌تر) پشتیبانی می‌شد، اما از آن پس، macOS حتی روی صفحه‌کلیدهای خارجی نیز Num Lock را پشتیبانی نکرده است. در MacBookهای قدیمی‌تر که دارای کلید Num Lock هستند، آن کلید هیچ رویداد کلیدی تولید نمی‌کند. Gecko از کلید Scroll Lock پشتیبانی می‌کند اگر یک صفحه‌کلید خارجی دارای کلید F14 متصل باشد. در برخی نسخه‌های قدیمی‌تر Firefox، این کلید یک رویداد `keypress` تولید می‌کرد؛ این رفتار ناسازگار [باگ Firefox 602812](https://bugzil.la/602812) بود.

### مدیریت تکرار خودکار

وقتی یک کلید فشرده شده و نگه داشته می‌شود، شروع به تکرار خودکار می‌کند. این امر منجر به ارسال دنباله‌ای از رویدادها مشابه موارد زیر می‌شود:

1. `keydown`
2. `keypress`
3. `keydown`
4. `keypress`
5. <\<تکرار تا زمانی که کاربر کلید را رها کند>>
6. `keyup`

این همان چیزی است که مشخصات DOM Level 3 می‌گوید باید رخ دهد. با این حال، نکات احتیاطی وجود دارد که در زیر توضیح داده شده است.

#### تکرار خودکار در برخی محیط‌های GTK مانند Ubuntu 9.4

در برخی محیط‌های مبتنی بر GTK، تکرار خودکار به‌طور خودکار یک رویداد کلید-بالا (key-up) بومی را در طول تکرار خودکار ارسال می‌کند و Gecko هیچ راهی برای تشخیص تفاوت بین یک سری فشردن کلیدهای تکراری و یک تکرار خودکار ندارد. بنابراین، در آن پلتفرم‌ها، یک کلید با تکرار خودکار دنباله رویدادهای زیر را تولید می‌کند:

1. `keydown`
2. `keypress`
3. `keyup`
4. `keydown`
5. `keypress`
6. `keyup`
7. <\<تکرار تا زمانی که کاربر کلید را رها کند>>
8. `keyup`

متأسفانه، در این محیط‌ها، محتوای وب هیچ راهی برای تشخیص تفاوت بین کلیدهای با تکرار خودکار و کلیدهایی که فقط به‌طور مکرر فشرده می‌شوند، ندارد.

## مثال

```js
document.addEventListener("keydown", (event) => {
  const keyName = event.key;

  if (keyName === "Control") {
    // do not alert when only Control key is pressed.
    return;
  }

  if (event.ctrlKey) {
    // Even though event.key is not 'Control' (e.g., 'a' is pressed),
    // event.ctrlKey may be true if Ctrl key is pressed at the same time.
    alert(`Combination of ctrlKey + ${keyName}`);
  } else {
    alert(`Key pressed ${keyName}`);
  }
});

document.addEventListener("keyup", (event) => {
  const keyName = event.key;

  // As the user releases the Ctrl key, the key is no longer active,
  // so event.ctrlKey is false.
  if (keyName === "Control") {
    alert("Control key was released");
  }
});
```

## مشخصات

{{Specifications}}

مشخصات رابط `KeyboardEvent` از نسخه‌های پیش‌نویس متعددی عبور کرد، ابتدا در DOM Events Level 2 که به دلیل عدم حصول اجماع کن