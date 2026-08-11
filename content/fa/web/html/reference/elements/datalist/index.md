---
title: "<datalist> HTML data list element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/datalist"
translated_by: "n8n + AI"
---

# عنصر `<datalist>` در HTML

المان **`<datalist>`** در [HTML](/en-US/docs/Web/HTML) شامل مجموعه‌ای از المان‌های `<option>` است که گزینه‌های مجاز یا پیشنهادی برای انتخاب در سایر کنترل‌ها را نشان می‌دهند.

```html interactive-example
<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />

<datalist id="ice-cream-flavors">
  <option value="Chocolate"></option>
  <option value="Coconut"></option>
  <option value="Mint"></option>
  <option value="Strawberry"></option>
  <option value="Vanilla"></option>
</datalist>
```

```css interactive-example
label {
  display: block;
  margin-bottom: 10px;
}
```

برای اتصال `<datalist>` به کنترل، یک شناسه یکتا در attribute با نام [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) به آن می‌دهیم و سپس attribute با نام [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) را به المان `<input>` اضافه می‌کنیم و مقدار آن را همان شناسه قرار می‌دهیم. فقط انواع خاصی از `<input>` از این رفتار پشتیبانی می‌کنند و این رفتار می‌تواند در مرورگرهای مختلف متفاوت باشد.

هر المان `<option>` باید یک attribute به نام `value` داشته باشد که نشان‌دهنده پیشنهادی است که قرار است در ورودی وارد شود. این المان می‌تواند attribute به نام `label` هم داشته باشد، یا در نبود آن، کمی متن محتوا؛ این متن ممکن است توسط مرورگر به جای `value` (در Firefox) یا علاوه بر `value` (در Chrome و Safari، به عنوان متن تکمیلی) نمایش داده شود. محتوای دقیق منوی کشویی به مرورگر بستگی دارد، اما وقتی روی گزینه کلیک شود، محتوای واردشده در فیلد کنترل همیشه از attribute با نام `value` می‌آید.

> [!NOTE]
> `<datalist>` جایگزینی برای `<select>` نیست. `<datalist>` خودش یک ورودی را نمایش نمی‌دهد؛ بلکه فهرستی از مقادیر پیشنهادی برای یک کنترل مرتبط است. کنترل همچنان می‌تواند هر مقداری که اعتبارسنجی را پاس کند بپذیرد، حتی اگر در این فهرست پیشنهادی نباشد.

## Attributes

این المان هیچ attribute دیگری به غیر از [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) که برای همه المان‌ها مشترک است، ندارد.

## دسترس‌پذیری

وقتی تصمیم به استفاده از المان `<datalist>` می‌گیرید، باید به چند مسئله دسترس‌پذیری توجه کنید:

- اندازه فونت گزینه‌های فهرست داده با زوم مرورگر تغییر نمی‌کند و همیشه ثابت می‌ماند. محتوای پیشنهاد خودکار وقتی بقیه محتوا بزرگ یا کوچک می‌شود، بزرگ یا کوچک نمی‌شود.
- چون هدف قرار دادن فهرست گزینه‌ها با CSS بسیار محدود یا تقریباً غیرممکن است، نمی‌توان ظاهر آن را برای حالت کنتراست بالا استایل داد.
- برخی ترکیب‌های صفحه‌خوان/مرورگر، از جمله NVDA و Firefox، محتوای پاپ‌آپ پیشنهاد خودکار را اعلام نمی‌کنند.

## مثال‌ها

### انواع متنی

مقادیر پیشنهادی در انواع `text`، `search`، `url`، `tel`، `email` و `number` وقتی کاربر روی کنترل کلیک یا دوبار کلیک کند، در یک منوی کشویی نمایش داده می‌شوند. معمولاً سمت راست کنترل یک فلش به وجود مقادیر از‌پیش تعیین‌شده اشاره می‌کند.

```html
<label for="myBrowser">Choose a browser from this list:</label>
<input list="browsers" id="myBrowser" name="myBrowser" />
<datalist id="browsers">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
  <option value="Opera"></option>
  <option value="Safari"></option>
  <option value="Microsoft Edge"></option>
</datalist>
```

### انواع تاریخ و زمان

انواع `{{HTMLElement("input/month", "month")}}`، `{{HTMLElement("input/week", "week")}}`، `{{HTMLElement("input/date", "date")}}`، `{{HTMLElement("input/time", "time")}}` و `{{HTMLElement("input/datetime-local", "datetime-local")}}` می‌توانند واسطی را نمایش دهند که انتخاب راحت تاریخ و زمان را ممکن می‌کند.  
مقادیر از پیش‌تعریف‌شده در آن‌جا قابل نمایش هستند و کاربر می‌تواند سریعاً مقدار کنترل را پر کند.

> [!NOTE]
> وقتی این انواع پشتیبانی نمی‌شوند، به‌جای آن‌ها یک `text` ساده رندر می‌شود که یک فیلد متنی ایجاد می‌کند. آن فیلد مقادیر توصیه‌شده را به درستی تشخیص می‌دهد و در یک منوی کشویی به کاربر نمایش می‌دهد.

```html
<input type="time" list="popularHours" />
<datalist id="popularHours">
  <option value="12:00"></option>
  <option value="13:00"></option>
  <option value="14:00"></option>
</datalist>
```

### نوع Range

وقتی attributeهای `value` روی عناصر `<option>` که برای یک datalist مرتبط با نوع `{{HTMLElement("input/range", "range")}}` تعریف شده‌اند، قرار بگیرند، آن‌ها به صورت یک سری خط‌کش (tick marks) نمایش داده می‌شوند که کاربر به راحتی می‌تواند انتخاب کند.

```html
<label for="tick">Tip amount:</label>
<input type="range" list="tickmarks" min="0" max="100" id="tick" name="tick" />
<datalist id="tickmarks">
  <option value="0" label="0%"></option>
  <option value="10" label="Minimum Tip"></option>
  <option value="20" label="Standard"></option>
  <option value="30" label="Generous"></option>
  <option value="50" label="Very Generous"></option>
</datalist>
```

> [!NOTE]
> attribute `label` برای ارائه برچسب برای خط‌کش‌ها در نظر گرفته شده است، همان‌طور که در [HTML Standard](<https://html.spec.whatwg.org/multipage/input.html#range-state-(type=range)>) تعریف شده است. با این حال، پشتیبانی مرورگرها متفاوت است؛ ممکن است برچسب‌ها به صورت بصری یا tooltip نمایش داده نشوند.

### نوع Color

نوع `{{HTMLElement("input/color", "color")}}` می‌تواند رنگ‌های از پیش‌تعریف‌شده را در واسط ارائه‌شده توسط مرورگر نمایش دهد.

```html
<label for="colors">Pick a color (preferably a red tone):</label>
<input type="color" list="redColors" id="colors" />
<datalist id="redColors">
  <option value="#800000"></option>
  <option value="#8B0000"></option>
  <option value="#A52A2A"></option>
  <option value="#DC143C"></option>
</datalist>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتویات جریانی</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتویات عبارتی</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتویات مجاز</th>
      <td>
        یا
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتویات عبارتی</a>
        یا صفر یا بیشتر عنصر {{HTMLElement("option")}}.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچکدام؛ هم تگ آغازین و هم تگ پایانی ضروری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتویات عبارتی</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role">listbox</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLDataListElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری مرورگر

## همچنین ببینید

- عنصر `<input>` و به طور خاص ویژگی [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) آن؛
- عنصر `<option>`.