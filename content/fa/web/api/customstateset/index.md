---
title: CustomStateSet
slug: Web/API/CustomStateSet
page-type: web-api-interface
browser-compat: api.CustomStateSet
---

{{APIRef("Web Components")}}

رابط **`CustomStateSet`** از [مدل شیء سند (Document Object Model)](/en-US/docs/Web/API/Document_Object_Model) فهرستی از حالت‌ها را برای یک [عنصر سفارشی خودکار (autonomous custom element)](/en-US/docs/Web/API/Web_components/Using_custom_elements#types_of_custom_element) ذخیره می‌کند و امکان افزودن و حذف حالت‌ها را از مجموعه فراهم می‌آورد.

از این رابط می‌توان برای نمایش حالت‌های داخلی یک عنصر سفارشی استفاده کرد و به کدی که از عنصر استفاده می‌کند اجازه داد تا آن حالت‌ها را در انتخاب‌گرهای CSS به کار گیرد.

## خصوصیات نمونه

- {{domxref("CustomStateSet.size")}}
  - : تعداد مقادیر موجود در `CustomStateSet` را برمی‌گرداند.

## روش‌های نمونه

- {{domxref("CustomStateSet.add()")}}
  - : یک مقدار به مجموعه اضافه می‌کند.
- {{domxref("CustomStateSet.clear()")}}
  - : همه عناصر را از شیء `CustomStateSet` حذف می‌کند.
- {{domxref("CustomStateSet.delete()")}}
  - : یک مقدار را از شیء `CustomStateSet` حذف می‌کند.
- {{domxref("CustomStateSet.entries()")}}
  - : یک iterator جدید با مقادیر هر عنصر در `CustomStateSet` به ترتیب درج برمی‌گرداند.
- {{domxref("CustomStateSet.forEach()")}}
  - : یک تابع ارائه‌شده را برای هر مقدار در شیء `CustomStateSet` اجرا می‌کند.
- {{domxref("CustomStateSet.has()")}}
  - : یک {{jsxref("Boolean")}} برمی‌گرداند که مشخص می‌کند آیا عنصری با مقدار داده شده وجود دارد یا خیر.
- {{domxref("CustomStateSet.keys()")}}
  - : یک نام مستعار برای {{domxref("CustomStateSet.values()")}}.
- {{domxref("CustomStateSet.values()")}}
  - : یک شیء iterator جدید برمی‌گرداند که مقادیر هر عنصر در شیء `CustomStateSet` را به ترتیب درج تولید می‌کند.

## توضیحات

عناصر HTML داخلی می‌توانند _حالت‌های_ متفاوتی داشته باشند، مانند «فعال» و «غیرفعال»، «علامت‌خورده» و «علامت‌نخورده»، «اولیه»، «در حال بارگیری» و «آماده». برخی از این حالت‌ها عمومی هستند و می‌توان با استفاده از خصوصیات/ویژگی‌ها (properties/attributes) آن‌ها را تنظیم یا پرس‌وجو کرد، در حالی که برخی دیگر عملاً داخلی هستند و نمی‌توان مستقیماً آن‌ها را تنظیم کرد. صرف‌نظر از خارجی یا داخلی بودن، معمولاً می‌توان حالت‌های یک عنصر را با استفاده از [شبه‌کلاس‌های CSS](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes) به عنوان انتخاب‌گر انتخاب و استایل‌دهی کرد.

`CustomStateSet` به توسعه‌دهندگان اجازه می‌دهد تا حالت‌هایی را برای عناصر سفارشی خودکار (اما نه عناصر مشتق‌شده از عناصر داخلی) اضافه و حذف کنند. سپس این حالت‌ها را می‌توان به عنوان انتخاب‌گرهای شبه‌کلاس حالت سفارشی (custom state pseudo-classes) به شکلی مشابه شبه‌کلاس‌های عناصر داخلی به کار برد.

### تنظیم حالت‌های عنصر سفارشی

برای در دسترس قرار دادن `CustomStateSet`، یک عنصر سفارشی ابتدا باید {{domxref("HTMLElement.attachInternals()")}} را فراخوانی کند تا یک شیء {{domxref("ElementInternals")}} به آن متصل شود. سپس `CustomStateSet` توسط {{domxref("ElementInternals.states")}} بازگردانده می‌شود. توجه داشته باشید که `ElementInternals` را نمی‌توان به یک عنصر سفارشی مبتنی بر یک عنصر داخلی متصل کرد، بنابراین این ویژگی فقط برای عناصر سفارشی خودکار کار می‌کند (به [github.com/whatwg/html/issues/5166](https://github.com/whatwg/html/issues/5166) مراجعه کنید).

نمونه `CustomStateSet` یک [شیء شبیه به `Set`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set#set-like_browser_apis) است که می‌تواند یک مجموعه مرتب از مقادیر حالت را نگه دارد. هر مقدار یک شناسه سفارشی است. شناسه‌ها را می‌توان به مجموعه اضافه یا از آن حذف کرد. اگر یک شناسه در مجموعه وجود داشته باشد، حالت خاص `true` است، و اگر حذف شود، حالت `false` است.

عناصر سفارشی که حالت‌هایی با بیش از دو مقدار دارند، می‌توانند آن‌ها را با چندین حالت بولی نشان دهند که در هر لحظه فقط یکی از آن‌ها `true` (در `CustomStateSet` وجود دارد) است.

حالت‌ها را می‌توان در داخل عنصر سفارشی استفاده کرد، اما از خارج از مؤلفه سفارشی مستقیماً قابل دسترسی نیستند.

### تعامل با CSS

می‌توانید یک عنصر سفارشی را که در یک حالت خاص قرار دارد با استفاده از شبه‌کلاس حالت سفارشی {{cssxref(":state()")}} انتخاب کنید. قالب این شبه‌کلاس `:state(my-state-name)` است که `my-state-name` همان حالتی است که در عنصر تعریف شده است. شبه‌کلاس حالت سفارشی فقط در صورتی با عنصر سفارشی مطابقت دارد که حالت `true` باشد (یعنی `my-state-name` در `CustomStateSet` وجود داشته باشد).

برای مثال، CSS زیر یک عنصر سفارشی `labeled-checkbox` را هنگامی که `CustomStateSet` عنصر شامل حالت `checked` است، مطابقت می‌دهد و یک حاشیه `solid` به جعبه علامت (checkbox) اعمال می‌کند:

```css
labeled-checkbox:state(checked) {
  border: solid;
}
```

همچنین می‌توان از CSS برای مطابقت یک حالت سفارشی [درون DOM سایه‌ای یک عنصر سفارشی](/en-US/docs/Web/CSS/Reference/Selectors/:state#matching_a_custom_state_in_a_custom_elements_shadow_dom) با مشخص کردن `:state()` درون تابع شبه‌کلاس {{cssxref(":host()")}} استفاده کرد.

علاوه بر این، می‌توان از شبه‌کلاس `:state()` پس از شبه‌عنصر {{cssxref("::part()")}} برای مطابقت [بخش‌های سایه‌ای](/en-US/docs/Web/CSS/Guides/Shadow_parts) یک عنصر سفارشی که در یک حالت خاص هستند، استفاده کرد.

> [!WARNING]
> مرورگرهایی که هنوز از {{cssxref(":state()")}} پشتیبانی نمی‌کنند، از یک `<dashed-ident>` برای انتخاب حالت‌های سفارشی استفاده می‌کنند که اکنون منسوخ شده است. برای اطلاع از نحوه پشتیبانی از هر دو رویکرد، به بخش [سازگاری با نحو `<dashed-ident>`](#compatibility_with_dashed-ident_syntax) در زیر مراجعه کنید.

## مثال‌ها

### مطابقت حالت سفارشی یک عنصر جعبه علامت سفارشی

این مثال که از مشخصات اقتباس شده است، یک عنصر جعبه علامت سفارشی را نشان می‌دهد که دارای یک حالت داخلی «checked» است. این حالت به حالت سفارشی `checked` نگاشت می‌شود و امکان اعمال استایل با استفاده از شبه‌کلاس حالت سفارشی `:state(checked)` فراهم می‌شود.

#### JavaScript

ابتدا کلاس `LabeledCheckbox` خود را که از `HTMLElement` ارث‌بری می‌کند تعریف می‌کنیم. در سازنده (constructor) متد `super()` را فراخوانی می‌کنیم، یک شنونده برای رویداد کلیک اضافه می‌کنیم و {{domxref("HTMLElement.attachInternals()", "this.attachInternals()")}} را فراخوانی می‌کنیم تا یک شیء {{domxref("ElementInternals", "ElementInternals")}} متصل شود.

بیشتر «کار» باقی‌مانده به `connectedCallback()` سپرده می‌شود که زمانی که یک عنصر سفارشی به صفحه اضافه می‌شود فراخوانی می‌شود. محتوای عنصر با استفاده از یک عنصر `<style>` به صورت متن `[]` یا `[x]` به همراه یک برچسب تعریف می‌شود. نکته قابل توجه این است که از شبه‌کلاس حالت سفارشی برای انتخاب متن نمایش داده شده استفاده می‌شود: `:host(:state(checked))`. پس از مثال زیر، جزئیات بیشتری درباره آنچه در قطعه کد رخ می‌دهد توضیح خواهیم داد.

```js
class LabeledCheckbox extends HTMLElement {
  constructor() {
    super();
    this._boundOnClick = this._onClick.bind(this);
    this.addEventListener("click", this._boundOnClick);

    // Attach an ElementInternals to get states property
    this._internals = this.attachInternals();
  }

  connectedCallback() {
    const shadowRoot = this.attachShadow({ mode: "open" });
    shadowRoot.innerHTML = `<style>
  :host {
    display: block;
  }
  :host::before {
    content: "[ ]";
    white-space: pre;
    font-family: monospace;
  }
  :host(:state(checked))::before {
    content: "[x]";
  }
</style>
<slot>Label</slot>
`;
  }

  get checked() {
    return this._internals.states.has("checked");
  }

  set checked(flag) {
    if (flag) {
      this._internals.states.add("checked");
    } else {
      this._internals.states.delete("checked");
    }
  }

  _onClick(event) {
    // Toggle the 'checked' property when the element is clicked
    this.checked = !this.checked;
  }

  static isStateSyntaxSupported() {
    return CSS.supports("selector(:state(checked))");
  }
}

customElements.define("labeled-checkbox", LabeledCheckbox);

// Display a warning to unsupported browsers
if (!LabeledCheckbox.isStateSyntaxSupported()) {
  if (!document.getElementById("state-warning")) {
    const warning = document.createElement("div");
    warning.id = "state-warning";
    warning.style.color = "red";
    warning.textContent = "This feature is not supported by your browser.";
    document.body.insertBefore(warning, document.body.firstChild);
  }
}
```

در کلاس `LabeledCheckbox`:

- در `get checked()` و `set checked()` از `ElementInternals.states` برای دریافت `CustomStateSet` استفاده می‌کنیم.
- متد `set checked(flag)` اگر پرچم تنظیم شده باشد، شناسه `"checked"` را به `CustomStateSet` اضافه می‌کند و اگر پرچم `false` باشد، شناسه را حذف می‌کند.
- متد `get checked()` فقط بررسی می‌کند که آیا خصوصیت `checked` در مجموعه تعریف شده است یا خیر.
- مقدار خصوصیت زمانی که عنصر کلیک می‌شود، تغییر می‌کند (toggle).

سپس متد {{domxref("CustomElementRegistry/define", "define()")}} را روی شیء بازگردانده شده توسط {{domxref("Window.customElements")}} فراخوانی می‌کنیم تا عنصر سفارشی را ثبت کنیم:

```js
customElements.define("labeled-checkbox", LabeledCheckbox);
```

#### HTML

پس از ثبت عنصر سفارشی، می‌توانیم از عنصر در HTML به صورت زیر استفاده کنیم:

```html
<labeled-checkbox>You need to check this</labeled-checkbox>
```

#### CSS

در نهایت از شبه‌کلاس حالت سفارشی `:state(checked)` برای انتخاب CSS مربوط به زمانی که جعبه علامت خورده است استفاده می‌کنیم.

```css
labeled-checkbox {
  border: dashed red;
}
labeled-checkbox:state(checked) {
  border: solid;
}
```

#### نتیجه

روی عنصر کلیک کنید تا با تغییر حالت `checked` جعبه علامت، حاشیه متفاوتی اعمال شود.

{{EmbedLiveSample("Labeled Checkbox", "100%", 50)}}

### مطابقت یک حالت سفارشی در یک بخش سایه‌ای از یک عنصر سفارشی

این مثال که از مشخصات اقتباس شده است، نشان می‌دهد که می‌توان از حالت‌های سفارشی برای هدف‌گیری [بخش‌های سایه‌ای (shadow parts)](/en-US/docs/Web/CSS/Guides/Shadow_parts) یک عنصر سفارشی برای استایل‌دهی استفاده کرد. بخش‌های سایه‌ای بخش‌هایی از درخت سایه هستند که عمداً در معرض صفحاتی که از عنصر سفارشی استفاده می‌کنند قرار می‌گیرند.

این مثال یک عنصر سفارشی `<question-box>` ایجاد می‌کند که یک اعلان سؤال را به همراه یک جعبه علامت با برچسب «بله» نمایش می‌دهد. این عنصر از `<labeled-checkbox>` تعریف شده در [مثال قبلی](#matching_the_custom_state_of_a_custom_checkbox_element) برای جعبه علامت استفاده می‌کند.

#### JavaScript

```js hidden
class LabeledCheckbox extends HTMLElement {
  constructor() {
    super();
    this._boundOnClick = this._onClick.bind(this);
    this.addEventListener("click", this._boundOnClick);

    // Attach an ElementInternals to get states property
    this._internals = this.attachInternals();
  }

  connectedCallback() {
    const shadowRoot = this.attachShadow({ mode: "open" });
    shadowRoot.innerHTML = `<style>
  :host {
    display: block;
  }
  :host::before {
    content: "[ ]";
    white-space: pre;
    font-family: monospace;
  }
  :host(:state(checked))::before {
    content: "[x]";
  }
</style>
<slot>Label</slot>
`;
  }

  get checked() {
    return this._internals.states.has("checked");
  }

  set checked(flag) {
    if (flag) {
      this._internals.states.add("checked");
    } else {
      this._internals.states.delete("checked");
    }
  }

  _onClick(event) {
    // Toggle the 'checked' property when the element is clicked
    this.checked = !this.checked;
  }

  static isStateSyntaxSupported() {
    return CSS.supports("selector(:state(checked))");
  }
}

customElements.define("labeled-checkbox", LabeledCheckbox);

if (!LabeledCheckbox.isStateSyntaxSupported()) {
  if (!document.getElementById("state-warning")) {
    const warning = document.createElement("div");
    warning.id = "state-warning";
    warning.style.color = "red";
    warning.textContent = "This feature is not supported by your browser.";
    document.body.insertBefore(warning, document.body.firstChild);
  }
}
```

ابتدا کلاس عنصر سفارشی `QuestionBox` را تعریف می‌کنیم که از `HTMLElement` ارث‌بری می‌کند. طبق معمول، سازنده ابتدا متد `super()` را فراخوانی می‌کند. سپس با فراخوانی [`attachShadow()`](/en-US/docs/Web/API/Element/attachShadow) یک درخت DOM سایه‌ای به عنصر سفارشی متصل می‌کنیم.

```js
class QuestionBox extends HTMLElement {
  constructor() {
    super();
    const shadowRoot = this.attachShadow({ mode: "open" });
    shadowRoot.innerHTML = `<div><slot>Question</slot></div>
<labeled-checkbox part="checkbox">Yes</labeled-checkbox>
`;
  }
}
```

محتوای ریشه سایه با استفاده از [`innerHTML`](/en-US/docs/Web/API/ShadowRoot/innerHTML) تنظیم می‌شود. این یک عنصر {{HTMLElement("slot")}} تعریف می‌کند که حاوی متن پیش‌فرض اعلان «Question» برای عنصر است. سپس یک عنصر سفارشی `<labeled-checkbox>` با متن پیش‌فرض `"Yes"` تعریف می‌کنیم. این جعبه علامت با استفاده از ویژگی [`part`](/en-US/docs/Web/HTML/Reference/Global_attributes/part) به عنوان یک بخش سایه‌ای از جعبه سؤال با نام `checkbox` در معرض دید قرار می‌گیرد.

توجه داشته باشید که کد و استایل عنصر `<labeled-checkbox>` دقیقاً مشابه [مثال قبلی](#matching_the_custom_state_of_a_custom_checkbox_element) است و بنابراین در اینجا تکرار نمی‌شود.

سپس متد {{domxref("CustomElementRegistry/define", "define()")}} را روی شیء بازگردانده شده توسط {{domxref("Window.customElements")}} فراخوانی می‌کنیم تا عنصر سفارشی را با نام `question-box` ثبت کنیم:

```js
customElements.define("question-box", QuestionBox);
```

#### HTML

پس از ثبت عنصر سفارشی، می‌توانیم از عنصر در HTML به صورت زیر استفاده کنیم.

```html
<!-- Question box with default prompt "Question" -->
<question-box></question-box>

<!-- Question box with custom prompt "Continue?" -->
<question-box>Continue?</question-box>
```

#### CSS

بلوک اول CSS بخش سایه‌ای در معرض دید به نام `checkbox` را با استفاده از انتخاب‌گر {{cssxref("::part()")}} مطابقت می‌دهد و آن را به طور پیش‌فرض به رنگ `red` استایل می‌دهد.

```css
question-box::part(checkbox) {
  color: red;
}
```

بلوک دوم پس از `::part()` از `:state()` برای مطابقت بخش‌های `checkbox` که در حالت `checked` هستند استفاده می‌کند:

```css
question-box::part(checkbox):state(checked) {
  color: green;
  outline: dashed 1px green;
}
```

#### نتیجه

روی هر یک از جعبه‌های علامت کلیک کنید تا با تغییر حالت `checked`، رنگ از `red` به `green` با یک خط حاشیه تغییر کند.

{{EmbedLiveSample("Question box", "100%", 100)}}

### حالت‌های داخلی غیربولی

این مثال نحوه مدیریت موردی را نشان می‌دهد که عنصر سفارشی دارای یک خصوصیت داخلی با چندین مقدار ممکن است.

عنصر سفارشی در این مورد یک خصوصیت `state` با مقادیر مجاز: "loading"، "interactive" و "complete" دارد. برای عملی کردن این کار، هر مقدار را به حالت سفارشی خود نگاشت می‌کنیم و کدی ایجاد می‌کنیم تا اطمینان حاصل شود که فقط شناسه متناظر با حالت داخلی تنظیم شده است. این را در پیاده‌سازی متد `set state()` می‌بینید: حالت داخلی را تنظیم می‌کنیم، شناسه مربوط به حالت سفارشی منطبق را به `CustomStateSet` اضافه می‌کنیم و شناسه‌های مرتبط با سایر مقادیر را حذف می‌کنیم.

بیشتر کد باقی‌مانده مشابه مثالی است که یک حالت بولی واحد را نشان می‌دهد (ما برای هر حالت متن متفاوتی را با کلیک کاربر برای جابجایی بین حالت‌ها نمایش می‌دهیم).

#### JavaScript

```js
class ManyStateElement extends HTMLElement {
  constructor() {
    super();
    this._boundOnClick = this._onClick.bind(this);
    this.addEventListener("click", this._boundOnClick);
    // Attach an ElementInternals to get states property
    this._internals = this.attachInternals();
  }

  connectedCallback() {
    this.state = "loading";

    const shadowRoot = this.attachShadow({ mode: "open" });
    shadowRoot.innerHTML = `<style>
  :host {
    display: block;
    font-family: monospace;
  }
  :host::before {
    content: "[ unknown ]";
    white-space: pre;
  }
  :host(:state(loading))::before {
    content: "[ loading ]";
  }
  :host(:state(interactive))::before {
    content: "[ interactive ]";
  }
  :host(:state(complete))::before {
    content: "[ complete ]";
  }
</style>
<slot>Click me</slot>
`;
  }

  get state() {
    return this._state;
  }

  set state(stateName) {
    // Set internal state to passed value
    // Add identifier matching state and delete others
    if (stateName === "loading") {
      this._state = "loading";
      this._internals.states.add("loading");
      this._internals.states.delete("interactive");
      this._internals.states.delete("complete");
    } else if (stateName === "interactive") {
      this._state = "interactive";
      this._internals.states.delete("loading");
      this._internals.states.add("interactive");
      this._internals.states.delete("complete");
    } else if (stateName === "complete") {
      this._state = "complete";
      this._internals.states.delete("loading");
      this._internals.states.delete("interactive");
      this._internals.states.add("complete");
    }
  }

  _onClick(event) {
    // Cycle the state when element clicked
    if (this.state === "loading") {
      this.state = "interactive";
    } else if (this.state === "interactive") {
      this.state = "complete";
    } else if (this.state === "complete") {
      this.state = "loading";
    }
  }

  static isStateSyntaxSupported() {
    return CSS.supports("selector(:state(loading))");
  }
}

customElements.define("many-state-element", ManyStateElement);

if (!LabeledCheckbox.isStateSyntaxSupported()) {
  if (!document.getElementById("state-warning")) {
    const warning = document.createElement("div");
    warning.id = "state-warning";
    warning.style.color = "red";
    warning.textContent = "This feature is not supported by your browser.";
    document.body.insertBefore(warning, document.body.firstChild);
  }
}
```

#### HTML

پس از ثبت عنصر جدید، آن را به HTML اضافه می‌کنیم. این مشابه مثالی است که یک حالت بولی واحد را نشان می‌دهد، با این تفاوت که مقداری مشخص نمی‌کنیم و از مقدار پیش‌فرض slot (`<slot>Click me</slot>`) استفاده می‌کنیم.

```html
<many-state-element></many-state-element>
```

#### CSS

در CSS از سه شبه‌کلاس حالت سفارشی برای انتخاب CSS مربوط به هر یک از مقادیر حالت داخلی استفاده می‌کنیم: `:state(loading)`، `:state(interactive)`، `:state(complete)`. توجه داشته باشید که کد عنصر سفارشی تضمین می‌کند که فقط یکی از این حالت‌های سفارشی در یک زمان می‌تواند تعریف شود.

```css
many-state-element:state(loading) {
  border: dotted grey;
}
many-state-element:state(interactive) {
  border: dashed blue;
}
many-state-element:state(complete) {
  border: solid green;
}
```

#### نتایج

روی عنصر کلیک کنید تا با تغییر حالت، حاشیه متفاوتی اعمال شود.

{{EmbedLiveSample("Non-boolean internal states", "100%", 50)}}

## سازگاری با نحو `<dashed-ident>`

پیش از این، عناصر سفارشی با حالت‌های سفارشی با استفاده از یک `<dashed-ident>` به جای تابع {{cssxref(":state()")}} انتخاب می‌شدند. نسخه‌های مرورگر که از `:state()` پشتیبانی نمی‌کنند، در صورت ارائه یک ident که با دو خط تیره پیشوند نشده باشد، خطا می‌دهند. اگر نیاز به پشتیبانی از این مرورگرها دارید، یا از یک بلوک [try...catch](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) برای پشتیبانی از هر دو نحو استفاده کنید، یا از یک `<dashed-ident>` به عنوان مقدار حالت استفاده کرده و آن را با هر دو انتخاب‌گر CSS `:--my-state` و `:state(--my-state)` انتخاب کنید.

### استفاده از یک بلوک try...catch

این کد نحوه استفاده از `try...catch` را برای تلاش برای افزودن یک شناسه حالت که از `<dashed-ident>` استفاده نمی‌کند، و در صورت بروز خطا، بازگشت به `<dashed-ident>` را نشان می‌دهد.

#### JavaScript

```js
class CompatibleStateElement extends HTMLElement {
  constructor() {
    super();
    this._internals = this.attachInternals();
  }

  connectedCallback() {
    // The double dash is required in browsers with the
    // legacy syntax, not supplying it will throw
    try {
      this._internals.states.add("loaded");
    } catch {
      this._internals.states.add("--loaded");
    }
  }
}
```

#### CSS

```css
compatible-state-element:is(:--loaded, :state(loaded)) {
  border: solid green;
}
```

### استفاده از identهای پیشوند با دو خط تیره

یک راه حل جایگزین می‌تواند استفاده از `<dashed-ident>` درون JavaScript باشد. نقطه ضعف این رویکرد این است که خط تیره‌ها باید در هنگام استفاده از نحو `:state()` در CSS گنجانده شوند.

#### JavaScript

```js
class CompatibleStateElement extends HTMLElement {
  constructor() {
    super();
    this._internals = this.attachInternals();
  }
  connectedCallback() {
    // The double dash is required in browsers with the
    // legacy syntax, but works with the modern syntax
    this._internals.states.add("--loaded");
  }
}
```

#### CSS

```css
compatible-state-element:is(:--loaded, :state(--loaded)) {
  border: solid green;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

[استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements)