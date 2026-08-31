```
---
title: "Accessibility information for web authors"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Information_for_Web_authors"
translated_by: "n8n + AI"
---

---
title: Accessibility information for web authors
short-title: Information for web authors
slug: Web/Accessibility/Guides/Information_for_Web_authors
page-type: guide
sidebar: accessibilitysidebar
---

این سند فهرستی از دستورالعمل‌ها و مقررات، راهنماهای عملی و ابزارهایی برای بررسی و رفع مشکلات دسترس‌پذیری در وب‌سایت‌ها ارائه می‌دهد.

## دستورالعمل‌ها و مقررات

- [<abbr>ARIA</abbr> راهنمای شیوه‌های تألیف (<abbr>APG</abbr>)](https://www.w3.org/WAI/ARIA/apg/)
  - : راهنمایی برای معناشناسی دسترس‌پذیری که توسط مشخصات برنامه کاربردی اینترنتی غنی از دسترس‌پذیری (<abbr>ARIA</abbr>) تعریف شده است تا تجربه‌های وب قابل دسترسی ایجاد کند. نحوه اعمال معناشناسی دسترس‌پذیری به الگوهای طراحی و ویجت‌های رایج را توصیف می‌کند و الگوهای طراحی و مثال‌های کاربردی ارائه می‌دهد.
- [دستورالعمل‌های دسترس‌پذیری محتوای وب (<abbr>WCAG</abbr>)](https://www.w3.org/WAI/standards-guidelines/wcag/)
  - : مجموعه مهم دیگری از دستورالعمل‌های _ابتکار دسترس‌پذیری وب (<abbr>WAI</abbr>)_ در W3C. اتحادیه اروپا قصد دارد مقررات آینده دسترس‌پذیری خود را بر اساس این دستورالعمل‌ها بنا کند. این دستورالعمل‌ها در [فهرست بحث گروه علاقه‌مندان <abbr>WAI</abbr>](https://www.w3.org/WAI/about/groups/waiig/#mailinglist) مورد بحث قرار می‌گیرند.
- [ARIA در این سایت](/en-US/docs/Web/Accessibility/ARIA)
  - : <abbr>MDN</abbr> راهنمای همه [نقش‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) و [ویژگی‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes)، شامل بهترین شیوه‌ها، نقش‌ها و ویژگی‌های مرتبط و مثال‌ها.

## راهنماهای عملی

- [دسترس‌پذیری برای تیم‌ها](https://digital.gov/guides/accessibility-for-teams/)
  - : راهنمای مختصری از خدمات تحول فناوری اداره خدمات عمومی ایالات متحده که چندین موضوع دسترس‌پذیری را پوشش می‌دهد و پیوندهایی به ویدیوهای «چگونگی» و منابع مرتبط با <abbr>WCAG</abbr> دارد.
- [نویسندگی صفحات وب قابل دسترس](https://www.ibm.com/able/requirements/requirements/)
  - : IBM الزامات دسترس‌پذیری خود را که باید رعایت شوند به‌صورت عمومی و تعاملی در دسترس قرار داده است.

## بررسی و ترمیم خودکار

برای بررسی سریع خطاهای رایج در مرورگر خود از یک ابزار استفاده کنید.

- [HTML CodeSniffer](https://squizlabs.github.io/HTML_CodeSniffer/)
- [aXe](https://chromewebstore.google.com/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US)
- [Lighthouse Accessibility Audit](https://developer.chrome.com/docs/lighthouse/overview/)
- [Accessibility Insights](https://accessibilityinsights.io/)
- [<abbr>WAVE</abbr>](https://wave.webaim.org/extension/)

ابزارهایی برای ادغام در فرآیند ساخت خود، که به‌صورت برنامه‌نویسی آزمون‌های دسترس‌پذیری را اضافه می‌کنند، تا بتوانید هنگام توسعه برنامه وب خود خطاها را شناسایی کنید:

- [axe-core](https://github.com/dequelabs/axe-core)
- [jsx-a11y](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y)
- [Lighthouse Audits](https://github.com/GoogleChrome/lighthouse/blob/main/docs/readme.md#using-programmatically)
- [AccessLint.js](https://github.com/accesslint/accesslint.js/tree/master)

{{glossary("Continuous integration")}} ابزارهایی برای یافتن مشکلات دسترس‌پذیری در درخواست‌های کشش گیت‌هاب شما:

- [AccessLint](https://www.accesslint.com/)

اگرچه بهترین کار آزمایش برنامه‌های وب با کاربران واقعی است، می‌توانید کوررنگی، کم‌بینایی، کنتراست پایین و بزرگنمایی را شبیه‌سازی کنید. همیشه باید سایت خود را بدون ماوس و بدون لمس، برای آزمایش پیمایش با صفحه‌کلید، امتحان کنید. همچنین ممکن است بخواهید سایت خود را با دستورات صوتی امتحان کنید. سعی کنید ماوس خود را غیرفعال کنید و از افزونه‌های مرورگر مانند [Web Disability Simulator](https://chromewebstore.google.com/detail/web-disability-simulator/olioanlbgbpmdlgjnnampnnlohigkjla) استفاده کنید.
```