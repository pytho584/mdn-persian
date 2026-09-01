---
title: "CSSOM view API"
slug: Web/API/CSSOM_view_API
page-type: web-api-overview
spec-urls: https://drafts.csswg.org/cssom-view/
---

{{DefaultAPISidebar("CSSOM view API")}}

**CSSOM view API** به شما امکان می‌دهد نمای بصری یک سند را دستکاری کنید، از جمله به دست آوردن موقعیت جعبه‌های چیدمان عناصر، به دست آوردن عرض یا ارتفاع viewport از طریق اسکریپت، و همچنین اسکرول کردن یک عنصر.

## راهنماها

- [سیستم‌های مختصات](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems)
  - : سیستم‌های مختصاتی که برای مشخص کردن یک موقعیت در یک زمینه نمایشی مانند یک پنجره روی مانیتور، یک viewport روی دستگاه همراه، یا یک موقعیت روی یک برگه کاغذ هنگام چاپ استفاده می‌شوند.
- [مفاهیم Viewport](/en-US/docs/Web/CSS/Guides/CSSOM_view/Viewport_concepts)
  - : مفهوم viewport — چیست، تأثیر آن از نظر CSS، SVG و دستگاه‌های همراه — و تفاوت بین visual viewport و layout viewport.

## رابط‌ها

- {{domxref("MediaQueryList")}}
- {{domxref("MediaQueryListEvent")}}
- {{domxref("Screen")}}
- {{domxref("CaretPosition")}}
- {{domxref("VisualViewport")}}

## توسعه‌های اعمال شده بر روی سایر رابط‌ها

این ماژول ویژگی‌ها، متدها و رویدادهایی را به رابط‌های تعریف‌شده در سایر مشخصات اضافه می‌کند.

### توسعه‌های اعمال شده بر روی Window

- {{domxref("Window.devicePixelRatio", "devicePixelRatio")}}
- {{domxref("Window.innerHeight", "innerHeight")}}
- {{domxref("Window.innerWidth", "innerWidth")}}
- {{domxref("Window.matchMedia", "matchMedia()")}}
- {{domxref("Window.moveBy", "moveBy()")}}
- {{domxref("Window.moveTo", "moveTo()")}}
- {{domxref("Window.outerHeight", "outerHeight")}}
- {{domxref("Window.outerWidth", "outerWidth")}}
- `pageXOffset` (مشاهده کنید {{domxref("Window.scrollX", "scrollX")}})
- `pageYOffset` (مشاهده کنید {{domxref("Window.scrollY", "scrollY")}})
- {{domxref("Window.resizeBy", "resizeBy()")}}
- {{domxref("Window.resizeTo", "resizeTo()")}}
- {{domxref("Window.screen", "screen")}}
- {{domxref("Window.screenLeft", "screenLeft")}}
- {{domxref("Window.screenTop", "screenTop")}}
- {{domxref("Window.screenX", "screenX")}}
- {{domxref("Window.screenY", "screenY")}}
- {{domxref("Window.visualViewport", "visualViewport")}}
- {{domxref("Window.scroll", "scroll()")}}
- {{domxref("Window.scrollBy", "scrollBy()")}}
- {{domxref("Window.scrollTo", "scrollTo()")}}
- {{domxref("Window.scrollX", "scrollX")}}
- {{domxref("Window.scrollY", "scrollY")}}
- {{domxref("Window/resize_event", "resize")}} رویداد

### توسعه‌های اعمال شده بر روی Document

- {{domxref("Document.elementFromPoint", "elementFromPoint()")}}
- {{domxref("Document.caretPositionFromPoint", "caretPositionFromPoint()")}}
- {{domxref("Document.scrollingElement", "scrollingElement")}}
- {{domxref("Document/scroll_event", "scroll")}} رویداد
- {{domxref("Document/scrollend_event", "scrollend")}} رویداد

### توسعه‌های اعمال شده بر روی Element

- {{domxref("Element.checkVisibility", "checkVisibility()")}}
- {{domxref("Element.clientHeight", "clientHeight")}}
- {{domxref("Element.clientLeft", "clientLeft")}}
- {{domxref("Element.clientTop", "clientTop")}}
- {{domxref("Element.clientWidth", "clientWidth")}}
- {{domxref("Element.currentCSSZoom", "currentCSSZoom")}}
- {{domxref("Element.getBoundingClientRect", "getBoundingClientRect()")}}
- {{domxref("Element.getClientRects", "getClientRects()")}}
- {{domxref("Element.scroll", "scroll()")}}
- {{domxref("Element.scrollBy", "scrollBy()")}}
- {{domxref("Element.scrollHeight", "scrollHeight")}}
- {{domxref("Element.scrollIntoView", "scrollIntoView()")}}
- {{domxref("Element.scrollLeft", "scrollLeft")}}
- {{domxref("Element.scrollTo", "scrollTo()")}}
- {{domxref("Element.scrollTop", "scrollTop")}}
- {{domxref("Element.scrollWidth", "scrollWidth")}}
- {{domxref("Element/scroll_event", "scroll")}} رویداد
- {{domxref("Element/scrollend_event", "scrollend")}} رویداد

### توسعه‌های اعمال شده بر روی HTMLElement

- {{domxref("HTMLElement.offsetHeight", "offsetHeight")}}
- {{domxref("HTMLElement.offsetLeft", "offsetLeft")}}
- {{domxref("HTMLElement.offsetParent", "offsetParent")}}
- {{domxref("HTMLElement.offsetTop", "offsetTop")}}
- {{domxref("HTMLElement.offsetWidth", "offsetWidth")}}

### توسعه‌های اعمال شده بر روی HTMLImageElement

- {{domxref("HTMLImageElement.x", "x")}}
- {{domxref("HTMLImageElement.y", "y")}}

### توسعه‌های اعمال شده بر روی Range

- {{domxref("Range.getBoundingClientRect", "getBoundingClientRect()")}}
- {{domxref("Range.getClientRects", "getClientRects()")}}

### توسعه‌های اعمال شده بر روی MouseEvent

- {{domxref("MouseEvent.clientX", "clientX")}}
- {{domxref("MouseEvent.clientY", "clientY")}}
- {{domxref("MouseEvent.offsetX", "offsetX")}}
- {{domxref("MouseEvent.offsetY", "offsetY")}}
- {{domxref("MouseEvent.pageX", "pageX")}}
- {{domxref("MouseEvent.pageY", "pageY")}}
- {{domxref("MouseEvent.screenY", "screenY")}}
- {{domxref("MouseEvent.x", "x")}}
- {{domxref("MouseEvent.y", "y")}}

این ماژول متدهای کاربردی هندسی را تعریف می‌کند که بر روی رابط‌های {{domxref("Text")}}، {{domxref("Element")}}، {{domxref("CSSPseudoElement")}} و {{domxref("Document")}} اعمال می‌شوند. این ویژگی‌های `GeometryUtils` هنوز در هیچ مرورگری پیاده‌سازی نشده‌اند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [مدل شیء CSS (CSSOM)](/en-US/docs/Web/API/CSS_Object_Model) API
- [نمای CSSOM](/en-US/docs/Web/CSS/Guides/CSSOM_view) ماژول
- [سرریز CSS](/en-US/docs/Web/CSS/Guides/Overflow) ماژول
- [رفتار overscroll CSS](/en-US/docs/Web/CSS/Guides/Overscroll_behavior) ماژول
- [scroll snap CSS](/en-US/docs/Web/CSS/Guides/Scroll_snap) ماژول
- {{glossary("Viewport")}}
- {{glossary("Layout viewport")}}
- {{glossary("Visual viewport")}}
- {{cssxref("zoom")}}
- {{glossary("CSSOM")}}
- {{glossary("CSS pixel")}}
- {{glossary("Scroll container")}}
- {{htmlelement("meta")}}