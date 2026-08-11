---
title: "min HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/min"
translated_by: "n8n + AI"
---

ویژگی `min` کمترین مقدار قابل قبول و معتبر را برای `input`ای که این ویژگی را دارد مشخص می‌کند. اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) عنصر از این مقدار کمتر باشد، عنصر در اعتبارسنجی (validation) مردود می‌شود. این مقدار باید کوچک‌تر یا مساوی مقدار ویژگی `max` باشد.

برخی از انواع `input` دارای حداقل پیش‌فرض هستند. اگر `input` حداقل پیش‌فرض نداشته باشد و مقداری برای `min` مشخص شود که نتوان آن را به عدد معتبر تبدیل کرد (یا هیچ مقدار حداقلی تعیین نشده باشد)، آن `input` حداقلی نخواهد داشت.

این ویژگی برای انواع `input` زیر معتبر است: {{HTMLElement("input/date", "date")}}، {{HTMLElement("input/month", "month")}}، {{HTMLElement("input/week", "week")}}، {{HTMLElement("input/time", "time")}}، {{HTMLElement("input/datetime-local", "datetime-local")}}، {{HTMLElement("input/number", "number")}} و {{HTMLElement("input/range", "range")}}، و همچنین عنصر {{htmlelement('meter')}}.

## نحو (Syntax)

| نوع input                                     | نحو (Syntax)              | مثال                                                         |
| --------------------------------------------- | ---------------------------- | ------------------------------------------------------------ |
| {{HTMLElement("input/date", "date")}}         | `yyyy-mm-dd`                 | `<input type="date" min="2019-12-25" step="1">`               |
| {{HTMLElement("input/month", "month")}}       | `yyyy-mm`                    | `<input type="month" min="2019-12" step="12">`                |
| {{HTMLElement("input/week", "week")}}         | `yyyy-W##`                   | `<input type="week" min="2019-W23" step="">`                  |
| {{HTMLElement("input/time", "time")}}         | `HH:mm`                      | `<input type="time" min="09:00" step="900">`                  |
| {{HTMLElement("input/datetime-local", "datetime-local")}} | `yyyy-mm-ddTHH:mm`           | `<input type="datetime-local" min="2019-12-25T19:30">`        |
| {{HTMLElement("input/number", "number")}}     | [`<number>`](/en-US/docs/Web/CSS/Reference/Values/number) | `<input type="number" min="0" step="5" max="100">`            |
| {{HTMLElement("input/range", "range")}}       | [`<number>`](/en-US/docs/Web/CSS/Reference/Values/number) | `<input type="range" min="60" step="5" max="100">`            |

> **نکته:** اگر داده‌ای که کاربر وارد می‌کند با مقدار `min` تعیین‌شده مطابقت نداشته باشد، آن مقدار در اعتبارسنجی محدودیت‌ها (constraint validation) نامعتبر محسوب می‌شود و با شبه‌کلاس‌های {{cssxref(':invalid')}} و {{cssxref(':out-of-range')}} مطابقت پیدا می‌کند.

برای اطلاعات بیشتر به [اعتبارسنجی سمت کاربر (Client-side validation)](/en-US/docs/Web/HTML/Guides/Constraint_validation) و {{domxref("ValidityState.rangeUnderflow", "rangeUnderflow")}} مراجعه کنید.

برای عنصر {{htmlelement('meter')}}، ویژگی `min` کران پایین عددی دامنه اندازه‌گیری‌شده را مشخص می‌کند. اگر ویژگی [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) نیز تعیین شده باشد، این مقدار باید از آن کمتر باشد. در هر دو حالت، اگر مقداری تعیین نشود، مقدار پیش‌فرض برابر با ۱ خواهد بود.

<table class="no-markdown">
  <caption>
    نحو (Syntax) برای مقادیر <code>min</code> در سایر عناصر
  </caption>
  <thead>
    <tr>
      <th>نوع input</th>
      <th>نحو (Syntax)</th>
      <th>مثال</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{HTMLElement("meter")}}</td>
      <td><a href="/en-US/docs/Web/CSS/Reference/Values/number">&#x3C;number></a></td>
      <td>
        <code
          >&#x3C;meter id="fuel" min="0" max="100" low="33" high="66"
          optimum="80" value="40"> at 40/100&#x3C;/meter></code
        >
      </td>
    </tr>
  </tbody>
</table>

### تأثیر بر step

مقادیر `min` و `step` مشخص می‌کنند که چه مقادیری معتبر هستند، حتی اگر attribute `step` ذکر نشده باشد، زیرا `step` به‌طور پیش‌فرض برابر `0` است.

یک حاشیه قرمز بزرگ به inputهای نامعتبر اضافه می‌کنیم:

```css
input:invalid {
  border: solid red 3px;
}
```

سپس یک input با حداقل مقدار 7.2 تعریف می‌کنیم، بدون ذکر attribute step که در این صورت به‌طور پیش‌فرض 1 است.

```html
<input id="myNumber" name="myNumber" type="number" min="7.2" value="8" />
```

از آنجایی که `step` به‌طور پیش‌فرض 1 است، مقادیر معتبر شامل `7.2`، `8.2`، `9.2` و ... می‌شوند. مقدار 8 معتبر نیست. از آنجایی که یک مقدار نامعتبر قرار داده‌ایم، مرورگرهای پشتیبانی‌کننده مقدار را به‌عنوان نامعتبر نشان می‌دهند.

اگر به‌صراحت مشخص نشود، `step` برای inputهای `number` و `range` برابر ۱ و برای inputهای تاریخ/زمان برابر ۱ واحد (ثانیه، هفته، ماه، روز) خواهد بود.

## ملاحظات دسترسی‌پذیری (Accessibility)

دستورالعمل‌هایی ارائه دهید تا کاربران متوجه شوند چگونه فرم را پر کنند و از کنترل‌های فرم استفاده کنند. هر input اجباری و اختیاری، قالب داده‌ها و سایر اطلاعات مرتبط را مشخص کنید. هنگام استفاده از attribute `min`، مطمئن شوید که این حداقل نیاز برای کاربر قابل درک است. ارائه دستورالعمل‌ها درون {{htmlelement('label')}} ممکن است کافی باشد. اگر دستورالعمل‌ها را خارج از label ارائه می‌دهید (که امکان موقعیت‌دهی و طراحی انعطاف‌پذیرتری دارد)، از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step)
- [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
- سایر attributeهای meter: [`low`](/en-US/docs/Web/HTML/Reference/Elements/meter#low), [`high`](/en-US/docs/Web/HTML/Reference/Elements/meter#high), [`optimum`](/en-US/docs/Web/HTML/Reference/Elements/meter#optimum)
- [Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [Form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- {{domxref('validityState.rangeUnderflow')}}
- {{cssxref(':out-of-range')}}
- {{htmlelement('input')}}
- {{HTMLElement("input/date", "date")}}, {{HTMLElement("input/month", "month")}}, {{HTMLElement("input/week", "week")}}, {{HTMLElement("input/time", "time")}}, {{HTMLElement("input/datetime-local", "datetime-local")}}, {{HTMLElement("input/number", "number")}} و {{HTMLElement("input/range", "range")}} و {{htmlelement('meter')}}