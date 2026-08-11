---
title: "<time> HTML time (date) element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/time"
translated_by: "n8n + AI"
---

المان **`<time>`** یک [HTML](/en-US/docs/Web/HTML) است که یک بازهٔ زمانی مشخص را نمایش می‌دهد. این المان می‌تواند شامل ویژگی `datetime` باشد تا تاریخ را به فرمت قابل‌خواندن توسط ماشین تبدیل کند؛ این کار نتایج بهتر در موتورهای جستجو و امکانات سفارشی مانند یادآورها را ممکن می‌سازد.

این المان می‌تواند یکی از موارد زیر را نمایش دهد:

- یک زمان در ساعت ۲۴ ساعته.
- یک تاریخ دقیق در [تقویم میلادی](https://en.wikipedia.org/wiki/Gregorian_calendar) (به‌همراه ساعت و اطلاعات منطقهٔ زمانی به‌صورت اختیاری).
- یک [مدت‌زمان معتبر](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#valid-duration-string).

## ویژگی‌ها

همانند همهٔ المان‌های HTML، این المان از [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `datetime`
  - : این ویژگی زمان و/یا تاریخ المان را نشان می‌دهد و باید در یکی از قالب‌هایی باشد که در ادامه توضیح داده شده است.

## نکات استفاده

این المان برای نمایش تاریخ و زمان در قالبی قابل‌خواندن برای ماشین است. به‌عنوان مثال، می‌تواند به عامل کاربر (user agent) کمک کند که افزودن رویداد به تقویم کاربر را پیشنهاد دهد.

این المان نباید برای تاریخ‌های قبل از معرفی تقویم میلادی استفاده شود (به دلیل پیچیدگی‌های محاسبهٔ این تاریخ‌ها).

مقدار **datetime** (مقدار قابل‌خواندن توسط ماشین datetime) همان مقدار ویژگی `datetime` المان است و باید در قالب صحیح باشد (به زیر مراجعه کنید). اگر المان ویژگی `datetime` را نداشته باشد، **نباید هیچ المان فرزندی داشته باشد** و مقدار datetime محتوای متنی فرزند المان است.

### مقادیر datetime معتبر

| توضیحات | میکروسینتکس | مثال‌ها |
|---------|------------|----------|
| رشته ماه معتبر | `*YYYY*-*MM*` | `2011-11`، `2013-05` |
| رشته تاریخ معتبر | `*YYYY*-*MM*-*DD*` | `1887-12-01` |
| رشته تاریخ بدون سال معتبر | `*MM*-*DD*` | `11-12` |
| رشته زمان معتبر | `*HH*:*MM*`<br>`*HH*:*MM*:*SS*`<br>`*HH*:*MM*:*SS*.*mmm*` | `23:59`<br>`12:15:47`<br>`12:15:52.998` |
| رشته تاریخ و زمان محلی معتبر | `*YYYY*-*MM*-*DD* *HH*:*MM*`<br>`*YYYY*-*MM*-*DD* *HH*:*MM*:*SS*`<br>`*YYYY*-*MM*-*DD* *HH*:*MM*:*SS*.*mmm*`<br>`*YYYY*-*MM*-*DD*T*HH*:*MM*`<br>`*YYYY*-*MM*-*DD*T*HH*:*MM*:*SS*`<br>`*YYYY*-*MM*-*DD*T*HH*:*MM*:*SS*.*mmm*` | `2013-12-25 11:12`<br>`1972-07-25 13:43:07`<br>`1941-03-15 07:06:23.678`<br>`2013-12-25T11:12`<br>`1972-07-25T13:43:07`<br>`1941-03-15T07:06:23.678` |
| رشته افست منطقه زمانی معتبر | `Z`<br>`+*HHMM*`<br>`+*HH*:*MM*`<br>`-*HHMM*`<br>`-*HH*:*MM*` | `Z`<br>`+0200`<br>`+04:30`<br>`-0300`<br>`-08:00` |
| رشته تاریخ و زمان جهانی معتبر | هر ترکیبی از یک رشته تاریخ و زمان محلی معتبر به‌همراه یک رشته افست منطقه زمانی معتبر | `2013-12-25 11:12+0200`<br>`1972-07-25 13:43:07+04:30`<br>`1941-03-15 07:06:23.678Z`<br>`2013-12-25T11:12-08:00` |
| رشته هفته معتبر | `*YYYY*-W*WW*` | `2013-W46` |
| چهار رقم یا بیشتر ASCII | `*YYYY*` | `2013`، `0001` |
| رشته مدت زمان معتبر | `P*d*DT*h*H*m*M*s*S`<br>`P*d*DT*h*H*m*M*s*.*X*S`<br>`P*d*DT*h*H*m*M*s*.*XX*S`<br>`P*d*DT*h*H*m*M*s*.*XXX*S`<br>`PT*h*H*m*M*s*S`<br>`PT*h*H*m*M*s*.*X*S`<br>`PT*h*H*m*M*s*.*XX*S`<br>`PT*h*H*m*M*s*.*XXX*S`<br>`*w*w *d*d *h*h *m*m *s*s` | `P12DT7H12M13S`<br>`P12DT7H12M13.3S`<br>`P12DT7H12M13.45S`<br>`P12DT7H12M13.455S`<br>`PT7H12M13S`<br>`PT7H12M13.2S`<br>`PT7H12M13.56S`<br>`PT7H12M13.999S`<br>`7d 5h 24m 13s` |

## مثال‌ها

### مثال پایه

#### HTML

```html
<p>The concert starts at <time datetime="2018-07-07T20:00:00">20:00</time>.</p>
```

### مثال `datetime`

#### HTML

```html
<p>
  The concert took place on <time datetime="2001-05-15T19:00">May 15</time>.
</p>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ هم تگ شروع و هم تگ پایانی اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a> را بپذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">time</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>Any</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLTimeElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- عنصر `<data>` که برای نمایش سایر نوع مقادیر به کار می‌رود.