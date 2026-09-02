---
title: "IIRFilterNode"
---

---
title: IIRFilterNode
slug: Web/API/IIRFilterNode
page-type: web-api-interface
browser-compat: api.IIRFilterNode
---

{{APIRef("Web Audio API")}}

رابط **`IIRFilterNode`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک پردازندهٔ {{domxref("AudioNode")}} است که یک فیلتر [پاسخ ضربهٔ بینهایت](https://en.wikipedia.org/wiki/Infinite_impulse_response) (IIR) عمومی را پیاده‌سازی می‌کند؛ از این نوع فیلتر می‌توان برای پیاده‌سازی دستگاه‌های کنترل تُن و همچنین اکولایزرهای گرافیکی استفاده کرد. این رابط به شما اجازه می‌دهد پارامترهای پاسخ فیلتر را مشخص کنید تا در صورت نیاز تنظیم شود.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال</th>
      <td><code>"max"</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال</th>
      <td>همانند ورودی</td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

به‌طور معمول، بهتر است برای پیاده‌سازی فیلترهای مرتبه‌بالاتر از رابط {{domxref("BiquadFilterNode")}} استفاده کنید. دلایل متعددی برای این کار وجود دارد:

- فیلترهای Biquad معمولاً حساسیت کمتری نسبت به ناهنجاری‌های عددی دارند.
- پارامترهای فیلترهای Biquad قابل خودکارسازی هستند.
- همهٔ فیلترهای IIR با مرتبهٔ زوج را می‌توان با استفاده از {{domxref("BiquadFilterNode")}} ایجاد کرد.

با این حال، اگر نیاز به ایجاد یک فیلتر IIR با مرتبهٔ فرد دارید، باید از `IIRFilterNode` استفاده کنید. همچنین اگر به خودکارسازی نیاز ندارید یا به دلایل دیگر، ممکن است این رابط برای شما مفید باشد.

> [!NOTE]
> پس از ایجاد گره، نمی‌توانید ضرایب آن را تغییر دهید.

گره‌های `IIRFilterNode` دارای مرجع زمان دنباله (tail-time) هستند؛ یعنی با ورودی صفر نیز به تولید خروجی صوتی غیرسکوت ادامه می‌دهند. از آنجا که این یک فیلتر IIR است، ورودی غیرصفر برای همیشه ادامه می‌یابد، اما در عمل پس از مدت زمان محدودی که خروجی به اندازهٔ کافی به صفر نزدیک شود، می‌توان آن را محدود کرد. زمان واقعی مورد نیاز به ضرایب فیلتر ارائه‌شده بستگی دارد.

## سازنده

- {{domxref("IIRFilterNode.IIRFilterNode", "IIRFilterNode()")}}
  - : یک نمونهٔ جدید از یک شیء IIRFilterNode ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط هیچ ویژگی خاص خود را ندارد؛ با این حال، ویژگی‌های والد خود، {{domxref("AudioNode")}}، را به ارث می‌برد._

## روش‌های نمونه

_روش‌هایی را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد. همچنین روش‌های اضافی زیر را دارد:_

- {{domxref("IIRFilterNode.getFrequencyResponse", "getFrequencyResponse()")}}
  - : با استفاده از تنظیمات فعلی پارامترهای فیلتر، پاسخ فرکانس‌هایی را که در آرایهٔ فرکانس‌های داده‌شده مشخص شده‌اند محاسبه می‌کند.

## مثال‌ها

می‌توانید یک [نمایش زندهٔ ساده از فیلتر IIR](https://mdn.github.io/webaudio-examples/iirfilter-node/) را پیدا کنید. همچنین [کد منبع در GitHub](https://github.com/mdn/webaudio-examples/tree/main/iirfilter-node) را ببینید. این کد شامل مقادیر ضرایب مختلفی برای فرکانس‌های پایین‌گذر متفاوت است — می‌توانید مقدار ثابت `filterNumber` را به عددی بین 0 و 3 تغییر دهید تا افکت‌های مختلف موجود را بررسی کنید.

همچنین راهنمای [استفاده از فیلترهای IIR](/en-US/docs/Web/API/Web_Audio_API/Using_IIR_filters) را برای توضیح کامل ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("AudioNode")}}
- {{domxref("BiquadFilterNode")}}