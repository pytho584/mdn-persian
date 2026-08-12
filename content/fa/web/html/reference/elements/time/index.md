---
title: <time> HTML time (date) element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/time
translated_by: n8n + AI
---

# \<time> HTML time (date) element

المان **`<time>`** یک [HTML](../../../../../../../en-US/docs/Web/HTML/) است که یک بازهٔ زمانی مشخص را نمایش می‌دهد. این المان می‌تواند شامل ویژگی `datetime` باشد تا تاریخ را به فرمت قابل‌خواندن توسط ماشین تبدیل کند؛ این کار نتایج بهتر در موتورهای جستجو و امکانات سفارشی مانند یادآورها را ممکن می‌سازد.

این المان می‌تواند یکی از موارد زیر را نمایش دهد:

* یک زمان در ساعت ۲۴ ساعته.
* یک تاریخ دقیق در [تقویم میلادی](https://en.wikipedia.org/wiki/Gregorian_calendar) (به‌همراه ساعت و اطلاعات منطقهٔ زمانی به‌صورت اختیاری).
* یک [مدت‌زمان معتبر](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#valid-duration-string).

### ویژگی‌ها

همانند همهٔ المان‌های HTML، این المان از [ویژگی‌های سراسری](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) پشتیبانی می‌کند.

* `datetime`
  * : این ویژگی زمان و/یا تاریخ المان را نشان می‌دهد و باید در یکی از قالب‌هایی باشد که در ادامه توضیح داده شده است.

### نکات استفاده

این المان برای نمایش تاریخ و زمان در قالبی قابل‌خواندن برای ماشین است. به‌عنوان مثال، می‌تواند به عامل کاربر (user agent) کمک کند که افزودن رویداد به تقویم کاربر را پیشنهاد دهد.

این المان نباید برای تاریخ‌های قبل از معرفی تقویم میلادی استفاده شود (به دلیل پیچیدگی‌های محاسبهٔ این تاریخ‌ها).

مقدار **datetime** (مقدار قابل‌خواندن توسط ماشین datetime) همان مقدار ویژگی `datetime` المان است و باید در قالب صحیح باشد (به زیر مراجعه کنید). اگر المان ویژگی `datetime` را نداشته باشد، **نباید هیچ المان فرزندی داشته باشد** و مقدار datetime محتوای متنی فرزند المان است.

#### مقادیر datetime معتبر

| توضیحات                       | میکروسینتکس                                                                                                                                                                                                                                                                                                                                        | مثال‌ها                                                                                                                                                                                                                                                                                 |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| رشته ماه معتبر                | `*YYYY*-*MM*`                                                                                                                                                                                                                                                                                                                                      | `2011-11`، `2013-05`                                                                                                                                                                                                                                                                    |
| رشته تاریخ معتبر              | `*YYYY*-*MM*-*DD*`                                                                                                                                                                                                                                                                                                                                 | `1887-12-01`                                                                                                                                                                                                                                                                            |
| رشته تاریخ بدون سال معتبر     | `*MM*-*DD*`                                                                                                                                                                                                                                                                                                                                        | `11-12`                                                                                                                                                                                                                                                                                 |
| رشته زمان معتبر               | <p><code>*HH*:*MM*</code><br><code>*HH*:*MM*:*SS*</code><br><code>*HH*:*MM*:*SS*.*mmm*</code></p>                                                                                                                                                                                                                                                  | <p><code>23:59</code><br><code>12:15:47</code><br><code>12:15:52.998</code></p>                                                                                                                                                                                                         |
| رشته تاریخ و زمان محلی معتبر  | <p><code>*YYYY*-*MM*-*DD* *HH*:*MM*</code><br><code>*YYYY*-*MM*-*DD* *HH*:*MM*:*SS*</code><br><code>*YYYY*-*MM*-*DD* *HH*:*MM*:*SS*.*mmm*</code><br><code>*YYYY*-*MM*-*DD*T*HH*:*MM*</code><br><code>*YYYY*-*MM*-*DD*T*HH*:*MM*:*SS*</code><br><code>*YYYY*-*MM*-*DD*T*HH*:*MM*:*SS*.*mmm*</code></p>                                              | <p><code>2013-12-25 11:12</code><br><code>1972-07-25 13:43:07</code><br><code>1941-03-15 07:06:23.678</code><br><code>2013-12-25T11:12</code><br><code>1972-07-25T13:43:07</code><br><code>1941-03-15T07:06:23.678</code></p>                                                           |
| رشته افست منطقه زمانی معتبر   | <p><code>Z</code><br><code>+*HHMM*</code><br><code>+*HH*:*MM*</code><br><code>-*HHMM*</code><br><code>-*HH*:*MM*</code></p>                                                                                                                                                                                                                        | <p><code>Z</code><br><code>+0200</code><br><code>+04:30</code><br><code>-0300</code><br><code>-08:00</code></p>                                                                                                                                                                         |
| رشته تاریخ و زمان جهانی معتبر | هر ترکیبی از یک رشته تاریخ و زمان محلی معتبر به‌همراه یک رشته افست منطقه زمانی معتبر                                                                                                                                                                                                                                                               | <p><code>2013-12-25 11:12+0200</code><br><code>1972-07-25 13:43:07+04:30</code><br><code>1941-03-15 07:06:23.678Z</code><br><code>2013-12-25T11:12-08:00</code></p>                                                                                                                     |
| رشته هفته معتبر               | `*YYYY*-W*WW*`                                                                                                                                                                                                                                                                                                                                     | `2013-W46`                                                                                                                                                                                                                                                                              |
| چهار رقم یا بیشتر ASCII       | `*YYYY*`                                                                                                                                                                                                                                                                                                                                           | `2013`، `0001`                                                                                                                                                                                                                                                                          |
| رشته مدت زمان معتبر           | <p><code>P*d*DT*h*H*m*M*s*S</code><br><code>P*d*DT*h*H*m*M*s*.*X*S</code><br><code>P*d*DT*h*H*m*M*s*.*XX*S</code><br><code>P*d*DT*h*H*m*M*s*.*XXX*S</code><br><code>PT*h*H*m*M*s*S</code><br><code>PT*h*H*m*M*s*.*X*S</code><br><code>PT*h*H*m*M*s*.*XX*S</code><br><code>PT*h*H*m*M*s*.*XXX*S</code><br><code>*w*w *d*d *h*h *m*m *s*s</code></p> | <p><code>P12DT7H12M13S</code><br><code>P12DT7H12M13.3S</code><br><code>P12DT7H12M13.45S</code><br><code>P12DT7H12M13.455S</code><br><code>PT7H12M13S</code><br><code>PT7H12M13.2S</code><br><code>PT7H12M13.56S</code><br><code>PT7H12M13.999S</code><br><code>7d 5h 24m 13s</code></p> |

### مثال‌ها

#### مثال پایه

**HTML**

```html
<p>The concert starts at <time datetime="2018-07-07T20:00:00">20:00</time>.</p>
```

#### مثال `datetime`

**HTML**

```html
<p>
  The concert took place on <time datetime="2001-05-15T19:00">May 15</time>.
</p>
```

### خلاصه فنی

| [دسته‌بندی محتوا](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | [Flow content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content), [phrasing content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content), palpable content. |
| -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| محتوای مجاز                                                                            | [Phrasing content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content).                                                                                                                     |
| حذف تگ                                                                                 | هیچ؛ هم تگ شروع و هم تگ پایانی اجباری هستند.                                                                                                                                                                                  |
| والدهای مجاز                                                                           | هر عنصری که [phrasing content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content) را بپذیرد.                                                                                               |
| نقش ARIA ضمنی                                                                          | [`time`](../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles/#structural_roles_with_html_equivalents)                                                                                     |
| نقش‌های ARIA مجاز                                                                      | Any                                                                                                                                                                                                                           |
| رابط DOM                                                                               | `HTMLTimeElement`                                                                                                                                                                                                             |

### همچنین ببینید

* عنصر `<data>` که برای نمایش سایر نوع مقادیر به کار می‌رود.
