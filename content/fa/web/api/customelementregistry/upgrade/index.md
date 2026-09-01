---
title: "CustomElementRegistry: upgrade() method"
short-title: upgrade()
slug: Web/API/CustomElementRegistry/upgrade
page-type: web-api-instance-method
browser-compat: api.CustomElementRegistry.upgrade
---

{{APIRef("Web Components")}}

متد **`upgrade()`** از رابط {{domxref("CustomElementRegistry")}} تمام عناصر سفارشی که دارای سایه (shadow) هستند را در یک زیردرخت {{domxref("Node")}} ارتقا می‌دهد، حتی پیش از آنکه به سند اصلی متصل شوند.

## نحو

```js-nolint
upgrade(root)
```

### پارامترها

- `root`
  - : یک نمونه از {{domxref("Node")}} که شامل عناصر نزولی دارای سایه برای ارتقا است. اگر هیچ عنصر نزولی قابل ارتقایی وجود نداشته باشد، خطایی پرتاب نمی‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## توضیحات

هنگامی که یک عنصر HTML تجزیه یا ایجاد می‌شود، ممکن است از یک نام برچسب استفاده کند که منطبق با یک [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) است (مانند `<my-element>`). اگر کلاس عنصر سفارشی در زمان ایجاد عنصر هنوز در {{domxref("CustomElementRegistry")}} مناسب ثبت نشده باشد، عنصر به عنوان یک {{domxref("HTMLElement")}} تعریف‌نشده و ساده وجود دارد. این عنصر مانند هر عنصر ناشناخته‌ای ظاهر و رفتار می‌کند – هیچ رفتار خاصی، فراخوان‌های چرخه حیات یا متدهای نمونه اولیه سفارشی ندارد.

**ارتقا** فرآیند ارتقای پس‌نگرانه چنین عنصری به یک عنصر سفارشی کامل است، زمانی که تعریف آن در دسترس قرار می‌گیرد. هنگامی که یک عنصر ارتقا می‌یابد:

1. نمونه اولیه (prototype) آن به کلاس عنصر سفارشی که با {{domxref("CustomElementRegistry.define()", "define()")}} ثبت شده است، تغییر می‌یابد.
2. {{domxref("HTMLElement/connectedCallback", "connectedCallback()")}} و هر فراخوان چرخه حیات [دیگر](/en-US/docs/Web/API/Web_components/Using_custom_elements#custom_element_lifecycle_callbacks) که قابل اعمال است، فراخوانی می‌شود.
3. اگر کلاس {{domxref("HTMLElement/observedAttributes", "observedAttributes")}} را تعریف کند، {{domxref("HTMLElement/attributeChangedCallback", "attributeChangedCallback()")}} برای هر ویژگی که قبلاً مقدار دارد، فراخوانی می‌شود.

به طور معمول، عناصر به طور خودکار هنگامی که تعریف آنها از طریق `define()` ثبت می‌شود، ارتقا می‌یابند، اما تنها در صورتی که قبلاً به سند متصل باشند. متد `upgrade()` زمانی مفید است که نیاز به ارتقای عناصری دارید که در یک زیردرخت DOM غیرمتصل وجود دارند (به عنوان مثال، عناصری که از طریق {{domxref("Document.createElement()")}} ایجاد شده‌اند یا در یک {{domxref("DocumentFragment")}} تجزیه شده‌اند) پیش از آنکه به سند وارد شوند.

## مثال‌ها

برگرفته از [مشخصات HTML](https://html.spec.whatwg.org/multipage/custom-elements.html#dom-customelementregistry-upgrade):

```js
const el = document.createElement("spider-man");

class SpiderMan extends HTMLElement {}
customElements.define("spider-man", SpiderMan);

console.assert(!(el instanceof SpiderMan)); // هنوز ارتقا نیافته است

customElements.upgrade(el);
console.assert(el instanceof SpiderMan); // اکنون ارتقا یافته است!
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}