---
title: CSSStyleSheet
slug: Web/API/CSSStyleSheet
page-type: web-api-interface
browser-compat: api.CSSStyleSheet
---

{{APIRef("CSSOM")}}

رابط **`CSSStyleSheet`** یک برگه‌ی استایل CSS را نمایش می‌دهد و به شما امکان می‌دهد فهرست قوانین موجود در برگه‌ی استایل را بررسی و تغییر دهید. این رابط ویژگی‌ها و روش‌ها را از والد خود، {{domxref("StyleSheet")}} به ارث می‌برد.

{{InheritanceDiagram}}

یک برگه‌ی استایل از مجموعه‌ای از اشیاء {{domxref("CSSRule")}} تشکیل شده است که هر کدام نمایانگر یک قانون در برگه‌ی استایل هستند. این قوانین در یک {{domxref("CSSRuleList")}} قرار دارند که می‌توان آن را از طریق ویژگی {{domxref("CSSStyleSheet.cssRules", "cssRules")}} برگه‌ی استایل به دست آورد.

برای مثال، یک قانون ممکن است یک شیء {{domxref("CSSStyleRule")}} باشد که استایلی مانند زیر را در بر دارد:

```css
h1,
h2 {
  font-size: 16pt;
}
```

قانون دیگر ممکن است یک _at-rule_ مانند {{cssxref("@import")}} یا {{cssxref("@media")}} باشد و غیره.

بخش [دریافت یک برگه‌ی استایل](#obtaining_a_stylesheet) را برای روش‌های مختلف به‌دست آوردن یک شیء `CSSStyleSheet` ببینید. یک شیء `CSSStyleSheet` همچنین می‌تواند مستقیماً ساخته شود. سازنده و روش‌های {{domxref("CSSStyleSheet.replace()")}} و {{domxref("CSSStyleSheet.replaceSync()")}} افزوده‌های جدیدتری به مشخصات هستند که امکان _برگه‌های استایل قابل ساخت_ را فراهم می‌کنند.

برای اعمال یک `CSSStyleSheet` به یک سند یا ریشه‌ی سایه، آن را به ترتیب به ویژگی {{domxref("Document.adoptedStyleSheets")}} یا {{domxref("ShadowRoot.adoptedStyleSheets")}} اختصاص دهید.

## سازنده

- {{domxref("CSSStyleSheet.CSSStyleSheet()", "CSSStyleSheet()")}}
  - : یک شیء جدید `CSSStyleSheet` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("StyleSheet")}} به ارث می‌برد._

- {{domxref("CSSStyleSheet.cssRules")}} {{ReadOnlyInline}}
  - : یک {{domxref("CSSRuleList")}} زنده برمی‌گرداند که فهرست به‌روز اشیاء {{domxref("CSSRule")}} تشکیل‌دهنده‌ی برگه‌ی استایل را نگه می‌دارد.

    > [!NOTE]
    > در برخی مرورگرها، اگر برگه‌ی استایل از یک دامنه‌ی متفاوت بارگذاری شود، دسترسی به `cssRules` باعث ایجاد یک `SecurityError` می‌شود.

- {{domxref("CSSStyleSheet.ownerRule")}} {{ReadOnlyInline}}
  - : اگر این برگه‌ی استایل با استفاده از یک قانون {{cssxref("@import")}} به سند وارد شده باشد، ویژگی `ownerRule` شیء {{domxref("CSSImportRule")}} متناظر را برمی‌گرداند؛ در غیر این صورت، مقدار این ویژگی `null` است.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("StyleSheet")}} به ارث می‌برد._

- {{domxref("CSSStyleSheet.deleteRule()")}}
  - : قانون موجود در شاخص مشخص‌شده در فهرست قوانین برگه‌ی استایل را حذف می‌کند.
- {{domxref("CSSStyleSheet.insertRule()")}}
  - : یک قانون جدید را با توجه به نمایش متنی قانون، در موقعیت مشخص‌شده در برگه‌ی استایل درج می‌کند.
- {{domxref("CSSStyleSheet.replace()")}}
  - : محتوای برگه‌ی استایل را به صورت ناهمگام جایگزین می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که با `CSSStyleSheet` به‌روز شده حل می‌شود.
- {{domxref("CSSStyleSheet.replaceSync()")}}
  - : محتوای برگه‌ی استایل را به صورت همگام جایگزین می‌کند.

## ویژگی‌های قدیمی

_این ویژگی‌ها قدیمی هستند و توسط مایکروسافت معرفی شده‌اند؛ برای سازگاری با سایت‌های موجود حفظ شده‌اند._

- {{domxref("CSSStyleSheet.rules", "rules")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : ویژگی `rules` از نظر عملکردی با ویژگی استاندارد {{domxref("CSSStyleSheet.cssRules", "cssRules")}} یکسان است؛ یک {{domxref("CSSRuleList")}} زنده برمی‌گرداند که فهرست به‌روز همه‌ی قوانین موجود در برگه‌ی استایل را نگه می‌دارد.

## روش‌های قدیمی

_این روش‌ها قدیمی هستند و توسط مایکروسافت معرفی شده‌اند؛ برای سازگاری با سایت‌های موجود حفظ شده‌اند._

- {{domxref("CSSStyleSheet.addRule", "addRule()")}} {{Deprecated_Inline}}
  - : یک قانون جدید به برگه‌ی استایل اضافه می‌کند، با توجه به انتخاب‌گری که استایل به آن اعمال می‌شود و بلوک استایلی که به عناصر مطابق اعمال می‌شود.

    این روش با {{domxref("CSSStyleSheet.insertRule", "insertRule()")}} تفاوت دارد، که نمایش متنی کل قانون را به عنوان یک رشته‌ی واحد دریافت می‌کند.

- {{domxref("CSSStyleSheet.removeRule", "removeRule()")}} {{Deprecated_Inline}}
  - : از نظر عملکردی با {{domxref("CSSStyleSheet.deleteRule", "deleteRule()")}} یکسان است؛ قانون موجود در شاخص مشخص‌شده را از فهرست قوانین برگه‌ی استایل حذف می‌کند.

## دریافت یک برگه‌ی استایل

یک برگه‌ی استایل حداکثر با یک {{domxref("Document")}} مرتبط است که به آن اعمال می‌شود (مگر اینکه {{domxref("StyleSheet.disabled", "disabled", "", 1)}} باشد). فهرستی از اشیاء `CSSStyleSheet` برای یک سند مشخص را می‌توان با استفاده از ویژگی {{domxref("Document.styleSheets")}} به دست آورد. یک برگه‌ی استایل خاص همچنین می‌تواند از شیء _مالک_ آن (Node یا `CSSImportRule`)، در صورت وجود، دسترسی پیدا کند.

یک شیء `CSSStyleSheet` زمانی که یک برگه‌ی استایل برای یک سند بارگذاری می‌شود، به طور خودکار توسط مرورگر ایجاد و در فهرست {{domxref("Document.styleSheets")}} سند درج می‌شود.

فهرست (احتمالاً ناقص) از روش‌هایی که یک برگه‌ی استایل می‌تواند با یک سند مرتبط شود، در ادامه آمده است:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">دلیل ارتباط برگه‌ی استایل با سند</th>
      <th scope="col">در فهرست <code>document.<br />styleSheets</code> ظاهر می‌شود</th>
      <th scope="col">دریافت عنصر/قانون مالک با توجه به شیء برگه‌ی استایل</th>
      <th scope="col">رابط برای شیء مالک</th>
      <th scope="col">دریافت شیء CSSStyleSheet از مالک</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>عناصر {{HTMLElement("style")}} و {{HTMLElement("link")}} در سند</td>
      <td>بله</td>
      <td>{{domxref("StyleSheet.ownerNode", ".ownerNode")}}</td>
      <td>{{domxref("HTMLLinkElement")}}،<br />{{domxref("HTMLStyleElement")}}،<br />یا {{domxref("SVGStyleElement")}}</td>
      <td>{{domxref("HTMLLinkElement.sheet")}}،<br />{{domxref("HTMLStyleElement.sheet")}}،<br />یا {{domxref("SVGStyleElement.sheet")}}</td>
    </tr>
    <tr>
      <td>قانون CSS {{cssxref("@import")}} در سایر برگه‌های استایل اعمال‌شده به سند</td>
      <td>بله</td>
      <td>{{domxref("CSSStyleSheet.ownerRule", ".ownerRule")}}</td>
      <td>{{domxref("CSSImportRule")}}</td>
      <td>{{domxref("CSSImportRule.styleSheet", ".styleSheet")}}</td>
    </tr>
    <tr>
      <td>دستورالعمل پردازش <code>&#x3C;?xml-stylesheet ?></code> در سند (غیر HTML)</td>
      <td>بله</td>
      <td>{{domxref("StyleSheet.ownerNode", ".ownerNode")}}</td>
      <td>{{domxref("ProcessingInstruction")}}</td>
      <td>{{domxref("ProcessingInstruction.sheet", ".sheet")}}</td>
    </tr>
    <tr>
      <td>جاوا اسکریپت <a href="/en-US/docs/Web/JavaScript/Reference/Statements/import/with"><code>import ... with { type: "css" }</code></a></td>
      <td>خیر</td>
      <td>نامعتبر</td>
      <td>نامعتبر</td>
      <td>نامعتبر</td>
    </tr>
    <tr>
      <td>هدر پیوند HTTP</td>
      <td>بله</td>
      <td><em>نامعتبر</em></td>
      <td>نامعتبر</td>
      <td>نامعتبر</td>
    </tr>
    <tr>
      <td>برگه‌های استایل پیش‌فرض (User agent)</td>
      <td>خیر</td>
      <td>نامعتبر</td>
      <td>نامعتبر</td>
      <td>نامعتبر</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model)
- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)