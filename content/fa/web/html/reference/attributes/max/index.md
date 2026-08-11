---
title: "max HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/max"
translated_by: "n8n + AI"
---

ویژگی `max` حداکثر مقدار قابل قبول و معتبر را برای ورودی (input) حاوی این ویژگی مشخص می‌کند. اگر مقدار `value` عنصر از این مقدار بیشتر باشد، عنصر در [اعتبارسنجی (validation)](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) مردود می‌شود. این مقدار باید بزرگ‌تر یا مساوی مقدار ویژگی [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) باشد. اگر `max` وجود داشته باشد اما مشخص نشده یا نامعتبر باشد، هیچ مقدار `max` اعمال نمی‌شود. اگر `max` معتبر باشد و یک مقدار غیرتهی (non-empty) از حداکثر مجاز تعیین‌شده توسط `max` بیشتر باشد، اعتبارسنجی محدودیت (constraint validation) از ارسال فرم جلوگیری می‌کند.

ویژگی `max` برای انواع عددی input قابل استفاده است، از جمله {{HTMLElement("input/date", "date")}}، {{HTMLElement("input/month", "month")}}، {{HTMLElement("input/week", "week")}}، {{HTMLElement("input/time", "time")}}، {{HTMLElement("input/datetime-local", "datetime-local")}}، {{HTMLElement("input/number", "number")}} و {{HTMLElement("input/range", "range")}}، و همچنین برای عناصر {{htmlelement('progress')}} و {{htmlelement('meter')}}. این یک عدد است که مشخص می‌کند کنترل فرم (form control) برای معتبر بودن چه حداکثر مقداری باید داشته باشد.

اگر مقدار از حداکثر مجاز `max` بیشتر باشد، {{domxref('validityState.rangeOverflow')}} برابر `true` می‌شود و کنترل با شبه‌کلاس‌های {{cssxref(':out-of-range')}} و {{cssxref(':invalid')}} مطابقت پیدا می‌کند.

## نحو (Syntax)

<table class="no-markdown">
  <caption>
    نحو مقادیر <code>max</code> بر اساس <code>type</code> ورودی
  </caption>
  <thead>
    <tr>
      <th>نوع ورودی</th>
      <th>نحو</th>
      <th>مثال</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{HTMLElement("input/date", "date")}}</td>
      <td><code>yyyy-mm-dd</code></td>
      <td><code>&#x3C;input type="date" max="2019-12-25" step="1"></code></td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/month", "month")}}</td>
      <td><code>yyyy-mm</code></td>
      <td><code>&#x3C;input type="month" max="2019-12" step="12"></code></td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/week", "week")}}</td>
      <td><code>yyyy-W##</code></td>
      <td><code>&#x3C;input type="week" max="2019-W23" step=""></code></td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/time", "time")}}</td>
      <td><code>HH:mm</code></td>
      <td><code>&#x3C;input type="time" max="17:00" step="900"></code></td>
    </tr>
    <tr>
      <td>
        {{HTMLElement("input/datetime-local", "datetime-local")}}
      </td>
      <td><code>yyyy-mm-ddTHH:mm</code></td>
      <td>
        <code>&#x3C;input type="datetime-local" max="2019-12-25T23:59"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/number", "number")}}</td>
      <td><a href="/en-US/docs/Web/CSS/Reference/Values/number">&#x3C;number></a></td>
      <td>
        <code>&#x3C;input type="number" min="0" step="5" max="100"></code>
      </td>
    </tr>
    <tr>
      <td>{{HTMLElement("input/range", "range")}}</td>
      <td><a href="/en-US/docs/Web/CSS/Reference/Values/number">&#x3C;number></a></td>
      <td>
        <code>&#x3C;input type="range" min="60" step="5" max="100"></code>
      </td>
    </tr>
  </tbody>
</table>

> **توجه:** وقتی داده‌ای که کاربر وارد می‌کند با حداکثر مقدار تعیین‌شده مطابقت نداشته باشد، آن مقدار در اعتبارسنجی محدودیت (constraint validation) نامعتبر در نظر گرفته می‌شود و با شبه‌کلاس‌های {{cssxref(':invalid')}} و {{cssxref(':out-of-range')}} مطابقت پیدا می‌کند.

برای اطلاعات بیشتر به [اعتبارسنجی سمت کلاینت (Client-side validation)](/en-US/docs/Web/HTML/Guides/Constraint_validation) و {{domxref("ValidityState.rangeOverflow", "rangeOverflow")}} مراجعه کنید.

در عنصر `<progress>`، ویژگی `max` مشخص می‌کند که وظیفه‌ی نشان‌داده‌شده توسط عنصر `progress` به چه میزان کار نیاز دارد. اگر این ویژگی وجود داشته باشد، مقدار آن باید بزرگ‌تر از صفر و یک عدد اعشاری معتبر باشد. در عنصر `<meter>`، ویژگی `max` کران بالای عددی محدوده‌ی اندازه‌گیری را تعریف می‌کند. اگر [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) مشخص شده باشد، مقدار `max` باید بزرگ‌تر از آن باشد. در هر دو حالت، اگر این ویژگی ذکر نشود، مقدار پیش‌فرض ۱ است.

<table class="no-markdown">
  <caption>
    سینتکس مقدار <code>max</code> برای سایر عناصر
  </caption>
  <thead>
    <tr>
      <th>نوع ورودی</th>
      <th>سینتکس</th>
      <th>مثال</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>progress</code></td>
      <td><a href="/en-US/docs/Web/CSS/Reference/Values/number">&#x3C;number></a></td>
      <td>
        <code>&#x3C;progress id="file" max="100" value="70"> 70% &#x3C;/progress></code>
      </td>
    </tr>
    <tr>
      <td><code>meter</code></td>
      <td><a href="/en-US/docs/Web/CSS/Reference/Values/number">&#x3C;number></a></td>
      <td>
        <code>&#x3C;meter id="fuel" min="0" max="100" low="33" high="66" optimum="80" value="40"> at 40/100&#x3C;/meter></code>
      </td>
    </tr>
  </tbody>
</table>

## نکات دسترس‌پذیری

برای کمک به کاربران در درک نحوه‌ی تکمیل فرم و استفاده از هر یک از کنترل‌های فرم، دستورالعمل‌هایی ارائه دهید. ورودی‌های اجباری و اختیاری، قالب داده‌ها و سایر اطلاعات مرتبط را مشخص کنید. هنگام استفاده از ویژگی `max`، مطمئن شوید که کاربر این حداکثر مجاز را به درستی متوجه می‌شود. ارائه‌ی دستورالعمل‌ها درون `<label>` ممکن است کافی باشد. اگر دستورالعمل‌ها را خارج از `<label>` ارائه می‌دهید — که امکان چیدمان و طراحی انعطاف‌پذیرتری دارد — از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) استفاده کنید.

## جستارهای وابسته

- [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step)
- [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min)
- [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [اعتبارسنجی فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [`validityState.rangeOverflow`](/en-US/docs/Web/API/ValidityState/rangeOverflow)
- [`:out-of-range`](/en-US/docs/Web/CSS/:out-of-range)
- [`<input>`](/en-US/docs/Web/HTML/Element/input)
- انواع [`date`](/en-US/docs/Web/HTML/Element/input/date)، [`month`](/en-US/docs/Web/HTML/Element/input/month)، [`week`](/en-US/docs/Web/HTML/Element/input/week)، [`time`](/en-US/docs/Web/HTML/Element/input/time)، [`datetime-local`](/en-US/docs/Web/HTML/Element/input/datetime-local)، [`number`](/en-US/docs/Web/HTML/Element/input/number) و [`range`](/en-US/docs/Web/HTML/Element/input/range) و عنصر [`<meter>`](/en-US/docs/Web/HTML/Element/meter)