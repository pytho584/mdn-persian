---
title: "Element: setAttributeNS() method"
---

---
title: "Element: setAttributeNS() method"
short-title: setAttributeNS()
slug: Web/API/Element/setAttributeNS
page-type: web-api-instance-method
browser-compat: api.Element.setAttributeNS
---

{{ APIRef("DOM") }}

> [!WARNING]
> این متد می‌تواند مقدارهایی از صفت‌ها را بپذیرد که بسته به صفت مورد نظر، به‌صورت HTML، اسکریپت یا URL اسکریپت تجزیه می‌شوند.
> چنین APIهایی با نام [injection sinks](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و اگر مقدار اصلی از طرف یک مهاجم آمده باشد، به‌طور بالقوه می‌توانند بردار حملهٔ [cross-site scripting (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید این خطر را با همیشه ارسال شیء trusted type مناسب ({{domxref("TrustedHTML")}}، {{domxref("TrustedScript")}} یا {{domxref("TrustedScriptURL")}}) به‌جای رشته‌ها برای صفاتی که به آن نیاز دارند و [اعمال trusted types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](/en-US/docs/Web/API/Element/setAttribute#security_considerations) در {{domxref("Element.setAttribute()")}} مراجعه کنید.

متد **`setAttributeNS()`** از رابط {{domxref("Element")}} یک صفت جدید اضافه می‌کند یا مقدار صفتی را که دارای فضای نام و نام معین است تغییر می‌دهد.

اگر با اسناد HTML کار می‌کنید و نیازی به مشخص کردن صفت مورد نظر به‌عنوان بخشی از یک فضای نام خاص ندارید، به‌جای آن از متد {{domxref("Element.setAttribute()", "setAttribute()")}} استفاده کنید.

## سینتکس

```js-nolint
setAttributeNS(namespaceURI, qualifiedName, value)
```

### پارامترها

- `namespaceURI`
  - : رشته‌ای که فضای نام (namespace) صفت مورد نظر برای تنظیم را مشخص می‌کند، یا رشتهٔ خالی.

- `qualifiedName`
  - : رشته‌ای که صفت را با نام واجد شرایط (qualified name) آن شناسایی می‌کند؛ این نام قالبی به شکل `prefix:localName` یا `localName` دارد و بخش‌های آن به‌صورت زیر تعریف می‌شوند:
    - `prefix`
      - : «نام مستعار کوتاه» برای فضای نام.
        پیشوند اختیاری است، اما اگر مشخص شده باشد، پارامتر `namespaceURI` نیز باید مشخص شود.
        اگر پیشوند برابر با `xml` یا `xmlns` باشد، `namespaceURI` باید به‌ترتیب `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` باشد.

    - `localName`
      - : نام محلی (local name) صفت.

- `value`
  - : یک شیء trusted type یا رشته‌ای که مقدار اختصاص‌داده‌شده به صفت را در خود دارد.

    زمانی که trusted types اعمال شوند، برای صفت‌های زیر باید نمونه‌های trusted type ارسال شود:
    - صفت‌های محتوای رویداد، مانند `onclick` و `onload`، به یک {{domxref("TrustedScript")}} نیاز دارند.
    - {{domxref("HTMLIFrameElement.srcdoc")}} به یک نمونهٔ {{domxref("TrustedHTML")}} نیاز دارد.
    - {{domxref("HTMLScriptElement.src")}} به یک نمونهٔ {{domxref("TrustedScriptURL")}} نیاز دارد.
    - {{domxref("SVGScriptElement.href")}} به یک نمونهٔ {{domxref("TrustedScriptURL")}} نیاز دارد.

    Trusted types برای سایر صفت‌ها اعمال نمی‌شوند؛ بنابراین می‌توان یک رشته یا هر نوع trusted type را ارسال کرد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NamespaceError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که مقدار [`namespaceURI`](#namespaceuri):
    - یک URI فضای نام معتبر نباشد.
    - وقتی `prefix` مقداری داشته باشد، رشتهٔ خالی باشد.
    - وقتی [`prefix`](#prefix) به‌ترتیب به `xml` یا `xmlns` تنظیم شده باشد، با `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` مطابقت نداشته باشد.
- `InvalidCharacterError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که یکی از [`prefix`](#prefix) یا [`localName`](#localname) نامعتبر باشد:
    - `prefix` باید حداقل یک نویسه داشته باشد و نمی‌تواند حاوی فاصله‌های خالی (whitespace) ASCII، `NULL`، `/` یا `>` باشد (به‌ترتیب U+0000، U+002F یا U+003E).
    - `localName` باید حداقل یک نویسه داشته باشد و نمی‌تواند حاوی فاصله‌های خالی ASCII، `NULL`، `/`، `=` یا `>` باشد (به‌ترتیب U+0000، U+002F، U+003D یا U+003E).

    > [!NOTE]
    > نسخه‌های پیشین مشخصات محدودیت‌های بیشتری داشتند و خواستار آن بودند که `qualifiedName` یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر باشد.

- `TypeError`
  - : زمانی پرتاب می‌شود که برای [`value`](#value) یک رشته به‌جای شیء trusted type ارسال شود (برای آن دسته از صفاتی که به آن نیاز دارند) در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) [توسط یک CSP اعمال شده‌اند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ سیاست پیش‌فرضی تعریف نشده باشد.

## مثال‌ها

### استفادهٔ پایه

```js
let d = document.getElementById("d1");
d.setAttributeNS(
  "http://www.mozilla.org/ns/specialspace",
  "spec:align",
  "center",
);
```

### Trusted types

مثال [تنظیم صفت‌های ناامن](/en-US/docs/Web/API/Element/setAttribute#setting_unsafe_attributes) در `setAttribute()` نشان می‌دهد که چگونه می‌توانید از `setAttributeNS()` با [trusted types](/en-US/docs/Web/API/Trusted_Types_API) استفاده کنید.

## توصیه‌های رسمی

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttributeNS()")}}
- {{domxref("Element.getAttributeNS()")}}
- {{domxref("Element.removeAttributeNS()")}}
- {{domxref("Element.setAttribute()")}}