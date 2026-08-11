---
title: "<details> HTML details disclosure element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/details"
translated_by: "n8n + AI"
---

عنصر `<details>` یک ویجت بازشونده (disclosure widget) در HTML ایجاد می‌کند که محتوای آن فقط در حالت باز (open) نمایش داده می‌شود. برای این ویجت باید یک برچسب یا عنوان با استفاده از عنصر `<summary>` ارائه شود.

یک ویجت بازشونده معمولاً با یک مثلث کوچک نمایش داده می‌شود که برای نشان دادن وضعیت باز یا بسته می‌چرخد (یا کج می‌شود) و یک برچسب در کنار آن قرار دارد. محتوای عنصر `<summary>` به‌عنوان برچسب ویجت استفاده می‌شود و محتوای `<details>` توضیح دسترس‌پذیر (accessible description) برای `<summary>` را فراهم می‌کند.

```html
<details>
  <summary>جزئیات</summary>
  چیزی به‌اندازه‌ای کوچک که از توجه معمولی دور بماند.
</details>
```

```css
details {
  border: 1px solid #aaaaaa;
  border-radius: 4px;
  padding: 0.5em 0.5em 0;
}

summary {
  font-weight: bold;
  margin: -0.5em -0.5em 0;
  padding: 0.5em;
}

details[open] {
  padding: 0.5em;
}

details[open] summary {
  border-bottom: 1px solid #aaaaaa;
  margin-bottom: 0.5em;
}
```

ویجت `<details>` می‌تواند در یکی از دو حالت باشد. حالت پیش‌فرض _بسته_ فقط مثلث و برچسب داخل `<summary>` را نشان می‌دهد (اگر `<summary>` وجود نداشته باشد، مرورگر یک متن پیش‌فرض نمایش می‌دهد).

وقتی کاربر روی ویجت کلیک کند یا با فاصله (space bar) روی آن فوکس کند، ویجت باز می‌شود و محتوای خود را آشکار می‌کند. به دلیل چرخش مثلث برای نمایش باز و بسته شدن، به این ویجت‌ها گاهی "twisty" هم می‌گویند.

می‌توانید با CSS ظاهر ویجت را استایل دهید و با تنظیم یا حذف attribute `open` آن را به صورت برنامه‌نویسی باز و بسته کنید. در حال حاضر راهی داخلی برای انیمیت کردن تغییر حالت بین باز و بسته وجود ندارد.

وقتی ویجت بسته است، ارتفاع آن فقط به اندازه‌ی مثلث و برچسب است. وقتی باز می‌شود، محتوای داخل آن را نمایش می‌دهد.

پیاده‌سازی‌های کاملاً مطابق استاندارد به طور خودکار `display: list-item` را روی عنصر `<summary>` اعمال می‌کنند. می‌توانید از این ویژگی یا pseudo-element `::marker` برای سفارشی‌سازی ویجت بازشونده استفاده کنید.

## ویژگی‌ها (Attributes)

این عنصر شامل ویژگی‌های سراسری (global attributes) نیز می‌شود.

- `open`
  - : یک ویژگی Boolean که مشخص می‌کند جزئیات (محتوای داخل `<details>) در حال حاضر قابل مشاهده هستند یا خیر. اگر این ویژگی وجود داشته باشد، جزئیات نمایش داده می‌شوند و اگر وجود نداشته باشد، پنهان می‌مانند. به طور پیش‌فرض این ویژگی وجود ندارد یعنی جزئیات قابل مشاهده نیستند.

    > **توجه:** برای پنهان کردن جزئیات باید این ویژگی را به طور کامل حذف کنید. `open="false"` باعث نمایش جزئیات می‌شود چون این ویژگی از نوع Boolean است.

- `name`
  - : این ویژگی به چند عنصر `<details>` اجازه می‌دهد به هم متصل شوند به طوری که فقط یکی در یک زمان باز باشد. این کار به توسعه‌دهندگان امکان می‌دهد بدون نیاز به اسکریپت‌نویسی، المان‌های UI مثل آکاردئون (accordion) ایجاد کنند.

    ویژگی `name` یک نام گروه را مشخص می‌کند. به چند عنصر `<details>` مقدار `name` یکسان بدهید تا در یک گروه قرار گیرند. فقط یکی از عناصر گروه می‌تواند در یک زمان باز باشد – باز کردن یکی باعث بسته شدن دیگری می‌شود. اگر چند عنصر گروه‌بندی شده ویژگی `open` را داشته باشند، فقط اولین عنصر در ترتیب سورس (source order) به صورت باز نمایش داده می‌شود.

    > **توجه:** عناصر `<details>` برای قرار گرفتن در یک گروه نیازی به مجاورت در سورس ندارند.

علاوه بر رویدادهای معمولی که المان‌های HTML پشتیبانی می‌کنند، المان `<details>` از رویداد `toggle` هم پشتیبانی می‌کند. این رویداد هر بار که حالت المان بین باز و بسته تغییر کند، روی `<details>` ارسال می‌شود. رویداد _بعد از_ تغییر حالت فرستاده می‌شود؛ با این حال، اگر حالت قبل از اینکه مرورگر بتواند رویداد را ارسال کند چند بار تغییر کند، رویدادها ادغام می‌شوند تا فقط یک رویداد ارسال شود.

برای تشخیص تغییر حالت ویجت، می‌توانید از یک شنوندهٔ رویداد (event listener) برای رویداد `toggle` استفاده کنید:

```js
details.addEventListener("toggle", (event) => {
  if (details.open) {
    /* the element was toggled open */
  } else {
    /* the element was toggled closed */
  }
});
```

## مثال‌ها

### یک مثال پایه از disclosure

این مثال یک المان پایهٔ `<details>` را همراه با یک `<summary>` نشان می‌دهد.

```html
<details>
  <summary>System Requirements</summary>
  <p>
    Requires a computer running an operating system. The computer must have some
    memory and ideally some kind of long-term storage. An input device as well
    as some form of output device is recommended.
  </p>
</details>
```

### ساخت یک باکس باز disclosure

برای اینکه باکس `<details>` در حالت باز شروع به کار کند، attribute بولی `open` را اضافه کنید:

```html
<details open>
  <summary>System Requirements</summary>
  <p>
    Requires a computer running an operating system. The computer must have some
    memory and ideally some kind of long-term storage. An input device as well
    as some form of output device is recommended.
  </p>
</details>
```

### چند باکس disclosure همنام

چند باکس `<details>` قرار داده‌ایم که همه `name` یکسانی دارند تا فقط یکی در هر زمان باز باشد:

```html
<details name="requirements">
  <summary>Graduation Requirements</summary>
  <p>
    Requires 40 credits, including a passing grade in health, geography,
    history, economics, and wood shop.
  </p>
</details>
<details name="requirements">
  <summary>System Requirements</summary>
  <p>
    Requires a computer running an operating system. The computer must have some
    memory and ideally some kind of long-term storage. An input device as well
    as some form of output device is recommended.
  </p>
</details>
<details name="requirements">
  <summary>Job Requirements</summary>
  <p>
    Requires knowledge of HTML, CSS, JavaScript, accessibility, web performance,
    privacy, security, and internationalization, as well as a dislike of
    broccoli.
  </p>
</details>
```

سعی کنید همهٔ ویجت‌های disclosure را باز کنید. وقتی یکی را باز می‌کنید، بقیه به‌طور خودکار بسته می‌شوند.

### سفارشی‌سازی ظاهر

حالا کمی CSS اعمال می‌کنیم تا ظاهر باکس disclosure را سفارشی کنیم.

#### CSS

```css
details {
  font:
    16px "Open Sans",
    "Calibri",
    sans-serif;
  width: 620px;
}

details > summary {
  padding: 2px 6px;
  width: 15em;
  background-color: #dddddd;
  border: none;
  box-shadow: 3px 3px 4px black;
  cursor: pointer;
}

details > p {
  border-radius: 0 0 10px 10px;
  background-color: #dddddd;
  padding: 2px 6px;
  margin: 0;
  box-shadow: 3px 3px 4px black;
}

details:open > summary {
  background-color: #ccccff;
}
```

این CSS ظاهری شبیه به رابط تب‌دار ایجاد می‌کند؛ با کلیک روی تب، باز شده و محتویات آن نمایان می‌شود.

> [!NOTE]
> در مرورگرهایی که شبه‌کلاس `:open` را پشتیبانی نمی‌کنند، می‌توانید از attribute selector با نام `details[open]` برای استایل دادن به المان `<details>` در حالت باز استفاده کنید.

#### HTML

```html
<details>
  <summary>System Requirements</summary>
  <p>
    Requires a computer running an operating system. The computer must have some
    memory and ideally some kind of long-term storage. An input device as well
    as some form of output device is recommended.
  </p>
</details>
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>، ریشهٔ بخش‌بندی، محتوای تعاملی، محتوای قابل لمس.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        یک عنصر <code>&lt;summary&gt;</code> و سپس <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچکدام، هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a> را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLDetailsElement</code></td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility

## See also

- `<summary>`
- `::details-content`