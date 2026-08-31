---
title: "ARIA: aria-labelledby attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-labelledby attribute"
short-title: aria-labelledby
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-labelledby
sidebar: accessibilitysidebar
---

ویژگی `aria-labelledby` عنصر (یا عناصری) را که برچسب عنصر مورد نظر را تعیین می‌کند، مشخص می‌کند.

## توضیحات

ویژگی `aria-labelledby` به نویسندگان اجازه می‌دهد تا به عناصر دیگر در صفحه برای تعریف یک نام دسترسی‌پذیر (accessible name) ارجاع دهند. این ویژگی زمانی مفید است که از عناصری استفاده می‌کنید که پشتیبانی بومی برای مرتبط‌سازی عناصر برای ارائه یک نام دسترسی‌پذیر ندارند.

برخی از عناصر [نام دسترسی‌پذیر](https://w3c.github.io/accname/#dfn-accessible-name) خود را از محتوای داخلی خود دریافت می‌کنند. به عنوان مثال، نام دسترسی‌پذیر برای یک {{HTMLElement('button')}}، {{HTMLElement('a')}} یا {{HTMLElement('td')}} از متن بین تگ‌های باز و بسته می‌آید. عناصر دیگر، مانند {{HTMLElement('textarea')}}، {{HTMLElement('fieldset')}} و {{HTMLElement('table')}} فرم، نام دسترسی‌پذیر خود را از محتوای عناصر مرتبط دریافت می‌کنند؛ برای این عناصر، نام دسترسی‌پذیر از {{HTMLElement('label')}} با ویژگی `for`، {{HTMLElement('legend')}} و {{HTMLElement('caption')}} به ترتیب می‌آید.

همه عناصر تعاملی باید یک نام دسترسی‌پذیر داشته باشند. `aria-labelledby` می‌تواند برای ارجاع به عنصر دیگری برای تعریف نام دسترسی‌پذیر آن استفاده شود، زمانی که نام دسترسی‌پذیر یک عنصر نیاز به استفاده از محتوای جای دیگری از DOM دارد.

اگر هیچ محتوایی برای ارجاع برای ایجاد یک نام دسترسی‌پذیر وجود نداشته باشد، باید از ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده شود.

هدف `aria-labelledby` همان هدف `aria-label` است. این ویژگی یک نام دسترسی‌پذیر قابل تشخیص برای یک عنصر تعاملی در اختیار کاربر قرار می‌دهد. اگر یک عنصر هر دو ویژگی را داشته باشد، `aria-labelledby` استفاده خواهد شد. `aria-labelledby` همچنین بر اکثر روش‌های دیگر ارائه یک نام دسترسی‌پذیر، مانند {{HTMLElement('label')}} و متن داخلی عنصر، اولویت دارد. توجه داشته باشید که {{domxref("Element.ariaLabelledByElements")}} بالاترین اولویت را برای تنظیم برچسب ARIA دارد.

ویژگی‌های `aria-labelledby` و [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) هر دو به عناصر دیگر برای محاسبه جایگزین‌های متنی ارجاع می‌دهند. `aria-labelledby` باید به متنی کوتاه ارجاع دهد که یک نام دسترسی‌پذیر برای عنصر فراهم کند. `aria-describedby` برای ارجاع به محتوای طولانی‌تر که یک توضیح ارائه می‌دهد، استفاده می‌شود. اگر هیچ عنصری در DOM وجود نداشته باشد که یک برچسب کوتاه مناسب برای یک نام دسترسی‌پذیر برای یک عنصر تعاملی ارائه دهد، از `aria-label` برای تعریف نام دسترسی‌پذیر برای یک عنصر تعاملی استفاده کنید.

> [!NOTE]
> در حالی که در انگلیسی آمریکایی، "labeled" با یک "l" نوشته می‌شود، املای "labelledby" تثبیت شده و املای مورد استفاده در API‌های دسترسی‌پذیری است.

مثال زیر از `aria-labelledby` برای ارائه یک نام دسترسی‌پذیر برای یک ورودی چک‌باکس با استفاده از محتوای متنی یک عنصر هم‌سطح استفاده می‌کند:

```html
<span
  role="checkbox"
  aria-checked="false"
  tabindex="0"
  aria-labelledby="tac"></span>
<span id="tac">I agree to the Terms and Conditions.</span>
```

> [!NOTE]
> عناصر {{htmlelement("span")}} به طور پیش‌فرض نقش [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) را دارند و نمی‌توانند از `aria-labelledby` استفاده کنند مگر اینکه نقشی را مشخص کنند که بتواند یک نام دسترسی‌پذیر فراهم کند.
> در اینجا این کار را با `role="checkbox"` انجام می‌دهیم.

در حالی که استفاده از `aria-labelledby` در این شرایط مشابه استفاده از عنصر HTML {{HTMLElement('label')}} با ویژگی `for` است، تفاوت‌های بسیار مهمی وجود دارد. ویژگی `aria-labelledby` فقط نام دسترسی‌پذیر را تعریف می‌کند. هیچ‌یک از قابلیت‌های دیگر `<label>` را فراهم نمی‌کند، مانند اینکه کلیک روی عنصر برچسب‌گذار، ورودی مرتبط با آن را فعال کند. این قابلیت باید با JavaScript اضافه شود.

خوشبختانه، {{HTMLElement('input')}} HTML با `type="checkbox"` با `<label>` بومی کار می‌کند. در صورت امکان، از موارد زیر استفاده کنید:

```html
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions" />
  I agree to the Terms and Conditions.
</label>
<p><a href="tac.html">Read our Terms and Conditions</a>.</p>
```

### مزایا (و معایب)

1. ویژگی `aria-labelledby` بالاترین اولویت را در هنگام محاسبه نام‌های دسترسی‌پذیر توسط مرورگرها دارد. توجه داشته باشید که این ویژگی بر سایر روش‌های نام‌گذاری عنصر، از جمله `aria-label`، سایر ویژگی‌های نام‌گذاری و حتی محتوای خود عنصر غلبه می‌کند.

   ```html
   <button aria-label="Blue" aria-labelledby="color">Red</button>
   <span id="color">Yellow</span>
   ```

   در این مثال، نام دسترسی‌پذیر "Yellow" است.

2. ویژگی `aria-labelledby` یک لیست مرجع id با فاصله جدا شده را به عنوان مقدار می‌پذیرد، به این معنی که می‌توانید بیش از یک عنصر را در یک نام دسترسی‌پذیر واحد ترکیب کنید. می‌توانید [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) خود عنصر را برای ارجاع به محتوای خودش درج کنید.

   ```html
   <h2 id="attr" class="article-title">13 ARIA attributes you need to know</h2>
   <p>
     There are over 50 ARIA states and properties, but 13 of them stand out…
     <a href="13.html" id="rm13" aria-labelledby="rm13 attr">read more</a>
   </p>
   ```

   در این مثال، نام دسترسی‌پذیر "read more 13 ARIA attributes you need to know" است.

3. ترتیب مقدار ویژگی `aria-labelledby` مهم است. هنگامی که بیش از یک عنصر توسط `aria-labelledby` ارجاع داده می‌شود، محتوای هر عنصر ارجاع داده شده به ترتیبی که در مقدار `aria-labelledby` ارجاع داده شده‌اند، ترکیب می‌شود. اگر `aria-labelledby="attr rm13">` می‌نوشتیم، نام دسترسی‌پذیر "13 ARIA attributes you need to know read more" می‌شد.

4. ویژگی `aria-labelledby` از `id`های تکراری در مقدار خود چشم‌پوشی می‌کند. اگر یک عنصر بیش از یک بار ارجاع داده شود، فقط اولین ارجاع پردازش می‌شود. `aria-labelledby="attr attr rm13 rm13">` به عنوان `aria-labelledby="attr rm13">` در نظر گرفته می‌شود.

5. مقدار ویژگی `aria-labelledby` می‌تواند شامل محتوایی از عناصری باشد که حتی قابل مشاهده نیستند. در حالی که باید به کاربران فناوری کمکی همان محتوایی را ارائه دهید که به سایر کاربران می‌دهید، می‌توانید محتوایی از عناصر با ویژگی HTML [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden)، CSS [`display: none`](/en-US/docs/Web/CSS/Reference/Properties/display) و CSS [`visibility: hidden`](/en-US/docs/Web/CSS/Reference/Properties/visibility) را در رشته نام محاسبه شده بگنجانید.

6. ویژگی `aria-labelledby` مقدار عناصر ورودی را در خود جای می‌دهد. اگر مقدار به یک `<input>` ارجاع دهد، مقدار فعلی کنترل فرم در رشته نام محاسبه شده گنجانده می‌شود و در صورت به‌روزرسانی مقدار تغییر می‌کند.

7. ویژگی `aria-labelledby` قابل زنجیره‌سازی نیست. اگر یک عنصر با `aria-labelledby` به عنصر دیگری که `aria-labelledby` نیز دارد ارجاع دهد، ویژگی `aria-labelledby` روی عنصر ارجاع داده شده نادیده گرفته می‌شود.

> [!WARNING]
> از آنجایی که محاسبه نام یک عنصر با `aria-labelledby` می‌تواند پیچیده باشد و به محتوای پنهان ارجاع دهد، آزمایش با فناوری‌های کمکی برای اطمینان از اینکه نام مورد انتظار به کاربران ارائه می‌شود، بسیار مهم است.

## مقادیر

- لیست مرجع ID
  - : لیست جدا شده با فاصله از یک یا چند مقدار ID که به عناصری که عنصر فعلی را برچسب‌گذاری می‌کنند، ارجاع می‌دهد.

## رابط‌های مرتبط

- {{domxref("Element.ariaLabelledByElements")}}
  - : ویژگی `ariaLabelledByElements` بخشی از رابط هر عنصر است.
    مقدار آن آرایه‌ای از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` در ویژگی `aria-labelledby` را منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaLabelledByElements")}}
  - : ویژگی `ariaLabelledByElements` بخشی از رابط هر عنصر سفارشی است.
    مقدار آن آرایه‌ای از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` در ویژگی `aria-labelledby` را منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

در تقریباً همه نقش‌ها استفاده می‌شود **به جز** نقش‌هایی که نمی‌توانند توسط نویسنده یک نام دسترسی‌پذیر دریافت کنند.

ویژگی `aria-labelledby` در موارد زیر **پشتیبانی نمی‌شود**:

- [`caption`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`code`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`deletion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`emphasis`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role)
- [`insertion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`mark`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/mark_role)
- [`paragraph`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) / [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)
- [`strong`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`subscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`suggestion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/suggestion_role)
- [`superscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role)
- [`time`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('label')}}
- عنصر HTML {{HTMLElement('legend')}}
- عنصر HTML {{HTMLElement('caption')}}
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)