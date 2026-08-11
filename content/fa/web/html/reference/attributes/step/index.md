---
title: "step HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/step"
translated_by: "n8n + AI"
---

# ویژگی `step` در HTML

ویژگی **`step`** یک عدد است که میزان دقت (granularity) مقدار ورودی را مشخص می‌کند، یا می‌تواند مقدار `any` باشد. این ویژگی برای انواع ورودی عددی معتبر است، از جمله:

- {{HTMLElement("input/date", "date")}}
- {{HTMLElement("input/month", "month")}}
- {{HTMLElement("input/week", "week")}}
- {{HTMLElement("input/time", "time")}}
- {{HTMLElement("input/datetime-local", "datetime-local")}}
- {{HTMLElement("input/number", "number")}}
- {{HTMLElement("input/range", "range")}}

`step` فاصلهٔ گام (stepping interval) را هنگام کلیک روی دکمه‌های بالا/پایین spinner، حرکت دادن slider روی range، و اعتبارسنجی انواع تاریخ تعیین می‌کند. اگر به‌طور صریح مقداردهی نشود، `step` برای `number` و `range` برابر `1` و برای انواع تاریخ/زمان برابر `1` واحد (دقیقه، هفته، ماه، روز) خواهد بود. مقدار باید یک عدد مثبت (integer یا float) یا مقدار ویژهٔ `any` باشد. `any` به این معناست که هیچ گام‌بندی اعمال نمی‌شود و هر مقدار (با رعایت محدودیت‌های دیگر مانند `min` و `max`) مجاز است.

فقط مقادیری معتبر هستند که تعداد صحیحی از گام‌ها از مبدأ گام (step base) فاصله داشته باشند. مبدأ گام به‌ترتیب زیر تعیین می‌شود:

- اگر `min` مشخص شده باشد، مبدأ همان `min` است.
- در غیر این صورت، اگر `value` مشخص شده باشد، مبدأ همان `value` است.
- در غیر این صورت، مبدأ `0` است (به جز برای `week` که مبدأ پیش‌فرض آن `-259,200,000` میلی‌ثانیه، یعنی شروع هفتهٔ `1970-W01` است).

## نحو (Syntax)

<table class="no-markdown">
  <caption>مقادیر پیش‌فرض `step`</caption>
  <thead>
    <tr>
      <th>نوع ورودی</th>
      <th>مقدار پیش‌فرض</th>
      <th>مثال</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>&lt;input type="date"&gt;</code></td>
      <td>۱ (روز)</td>
      <td><code>&lt;input type="date" min="2019-12-25" step="1"&gt;</code></td>
    </tr>
    <tr>
      <td><code>&lt;input type="month"&gt;</code></td>
      <td>۱ (ماه)</td>
      <td><code>&lt;input type="month" min="2019-12" step="12"&gt;</code></td>
    </tr>
    <tr>
      <td><code>&lt;input type="week"&gt;</code></td>
      <td>۱ (هفته)</td>
      <td><code>&lt;input type="week" min="2019-W23" step="2"&gt;</code></td>
    </tr>
    <tr>
      <td><code>&lt;input type="time"&gt;</code></td>
      <td>۶۰ (ثانیه)</td>
      <td><code>&lt;input type="time" min="09:00" step="900"&gt;</code></td>
    </tr>
    <tr>
      <td><code>&lt;input type="datetime-local"&gt;</code></td>
      <td>۶۰ (ثانیه)</td>
      <td><code>&lt;input type="datetime-local" min="2019-12-25T19:30" step="900"&gt;</code></td>
    </tr>
    <tr>
      <td><code>&lt;input type="number"&gt;</code></td>
      <td>۱</td>
      <td><code>&lt;input type="number" min="0" step="0.1" max="10"&gt;</code></td>
    </tr>
    <tr>
      <td><code>&lt;input type="range"&gt;</code></td>
      <td>۱</td>
      <td><code>&lt;input type="range" min="0" step="2" max="10"&gt;</code></td>
    </tr>
  </tbody>
</table>

اگر مقدار `any` به‌طور صریح تنظیم نشود، مقادیر معتبر برای انواع `number`، تاریخ/زمان و `range` برابر با مبدأ گام (`min`) و افزایش‌های مضرب `step` تا `max` (در صورت مشخص بودن) خواهند بود. مثال زیر فقط اعداد زوج بزرگ‌تر یا مساوی ۱۰ را معتبر می‌کند:

```html
<input type="number" min="10" step="2" />
```

اگر `step` حذف شود، هر عدد صحیحی معتبر است، اما اعداد اعشاری مانند ۴.۲ معتبر نیستند، زیرا `step` پیش‌فرض ۱ دارد. برای اینکه ۴.۲ معتبر باشد:

- یا `step` باید برابر `any`، ۰.۱ یا ۰.۲ تنظیم شود،
- یا مقدار `min` باید به عددی ختم شود که با ۰.۲ تمام می‌شود، مانند ۰.۲، ۱.۲ یا ۵.۲-.

### تأثیر `min` بر `step`

مقدار `min` مقادیر معتبر را تعیین می‌کند، حتی اگر attribute `step` وجود نداشته باشد. دلیل این است که مقدار پیش‌فرض `step` برای نوع ورودی `number` برابر با `1` است.

در این مثال، یک حاشیه‌ی قرمز ضخیم دور ورودی‌های نامعتبر اضافه می‌کنیم:

```css
input:invalid {
  border: solid red 3px;
}
```

سپس یک ورودی با حداقل مقدار 1.2 و گام (step) برابر با 2 تعریف می‌کنیم:

```html
<input id="myNumber" name="myNumber" type="number" step="2" min="1.2" />
```

مقادیر معتبر شامل 1.2، 3.2، 5.2، 7.2، 9.2، 11.2 و ... می‌شود. فقط اعداد اعشاری (float) که بخش صحیح‌شان عددی فرد و بخش اعشاری‌شان .2 باشد معتبرند. اگر اسپینر عددی موجود باشد، مقادیر اعشاری معتبر از 1.2 به بالا را با افزایش 2 تولید می‌کند.

> [!NOTE]
> وقتی داده‌ی واردشده توسط کاربر با پیکربندی گام (step) مطابقت نداشته باشد، آن مقدار در اعتبارسنجی محدودیت‌ها (constraint validation) نامعتبر در نظر گرفته می‌شود و با شبه‌کلاس‌های `:invalid` و `:out-of-range` مطابقت خواهد داشت.

برای اطلاعات بیشتر به [Client-side validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) و [`stepMismatch`](/en-US/docs/Web/API/ValidityState/stepMismatch) مراجعه کنید.

## دسترسی‌پذیری

راهنمایی‌هایی برای کاربران فراهم کنید تا نحوه‌ی تکمیل فرم و استفاده از کنترل‌های فرم را بفهمند. ورودی‌های اجباری و اختیاری، قالب داده‌ها و سایر اطلاعات مرتبط را مشخص کنید. هنگام استفاده از attribute `min`، مطمئن شوید که کاربر این حداقل مورد نیاز را درک می‌کند. ارائه‌ی راهنما درون [`<label>`](/en-US/docs/Web/HTML/Reference/Elements/label) ممکن است کافی باشد. اگر راهنما خارج از برچسب‌ها ارائه می‌شود (که امکان جایگذاری و طراحی انعطاف‌پذیرتری می‌دهد)، از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) استفاده کنید.

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
- [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min)
- [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) (Constraint validation)
- [اعتبارسنجی فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) (Form validation)
- [`stepMismatch`](/en-US/docs/Web/API/ValidityState/stepMismatch)
- [:out-of-range](/en-US/docs/Web/CSS/:out-of-range)
- [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input)
- انواع [`date`](/en-US/docs/Web/HTML/Reference/Elements/input/date)، [`month`](/en-US/docs/Web/HTML/Reference/Elements/input/month)، [`week`](/en-US/docs/Web/HTML/Reference/Elements/input/week)، [`time`](/en-US/docs/Web/HTML/Reference/Elements/input/time)، [`datetime-local`](/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local)، [`number`](/en-US/docs/Web/HTML/Reference/Elements/input/number) و [`range`](/en-US/docs/Web/HTML/Reference/Elements/input/range) و element [`<meter>`](/en-US/docs/Web/HTML/Reference/Elements/meter)