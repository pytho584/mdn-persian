---
title: "<menu> HTML menu element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/menu"
translated_by: "n8n + AI"
---

عنصر `<menu>` در HTML در مشخصات HTML به‌عنوان جایگزین معنایی برای `<ul>` معرفی شده، اما در مرورگرها (و در درخت دسترس‌پذیری) دقیقاً مثل `<ul>` رفتار می‌شود. این عنصر یک لیست نامرتب از آیتم‌ها را نشان می‌دهد (که هر آیتم با `<li>` مشخص می‌شود).

{{InteractiveExample("HTML Demo: &lt;menu&gt;", "tabbed-shorter")}}

```html interactive-example
<div class="news">
  <a href="#">NASA's Webb Delivers Deepest Infrared Image of Universe Yet</a>
  <menu>
    <li><button id="save">ذخیره برای بعد</button></li>
    <li><button id="share">اشتراک‌گذاری</button></li>
  </menu>
</div>
```

```css interactive-example
.news {
  background-color: bisque;
  padding: 1em;
  border: solid thin black;
}

menu {
  list-style-type: none;
  display: flex;
  padding: 0;
  margin-bottom: 0;
  gap: 1em;
}
```

## ویژگی‌ها

این عنصر از [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز پشتیبانی می‌کند.

- `compact` {{Deprecated_inline}}
  - : این ویژگی Boolean به مرورگر می‌گوید که لیست باید به صورت فشرده نمایش داده شود. نحوهٔ تفسیر این ویژگی به مرورگر بستگی دارد. به جای آن از [CSS](/en-US/docs/Web/CSS) استفاده کنید: برای ایجاد اثری مشابه `compact` می‌توانید از خاصیت {{cssxref("line-height")}} با مقدار `80%` استفاده کنید.

## نکات استفاده

`<menu>` و `<ul>` هر دو یک لیست نامرتب از آیتم‌ها را نشان می‌دهند. تفاوت اصلی این است که `<ul>` بیشتر برای نمایش محتوا به کار می‌رود، در حالی که `<menu>` یک نوار ابزار (toolbar) شامل دستوراتی را نشان می‌دهد که کاربر می‌تواند اجرا یا فعال کند.

> [!NOTE]
> در نسخه‌های اولیهٔ مشخصات HTML، عنصر `<menu>` کاربرد دیگری هم داشت: به‌عنوان منوی راست‌کلیک (context menu). این قابلیت اکنون منسوخ شده و در مشخصات جدید وجود ندارد.

## مثال‌ها

### نوار ابزار

در این مثال از `<menu>` برای ساخت نوار ابزار یک برنامهٔ ویرایشی استفاده شده است.

#### HTML

```html
<menu>
  <li><button onclick="copy()">کپی</button></li>
  <li><button onclick="cut()">برش</button></li>
  <li><button onclick="paste()">چسباندن</button></li>
</menu>
```

توجه کنید که این کد از نظر عملکردی با کد زیر تفاوتی ندارد:

```html
<ul>
  <li><button onclick="copy()">کپی</button></li>
  <li><button onclick="cut()">برش</button></li>
  <li><button onclick="paste()">چسباندن</button></li>
</ul>
```

#### CSS

```css
menu,
ul {
  display: flex;
  list-style: none;
  padding: 0;
  width: 400px;
}

li {
  flex-grow: 1;
}

button {
  width: 100%;
}
```

#### نتیجه

{{EmbedLiveSample("Toolbar", "100%", 100)}}

## خلاصهٔ فنی

| محتوا | توضیح |
|------|-------|
| [دستهٔ محتوا](/en-US/docs/Web/HTML/Reference/Content_categories) | جریان (flow content)، محتوای قابل لمس (palpable content). |
| محتوای مجاز | صفر یا چند عنصر {{HTMLElement("li")}}، {{HTMLElement("script")}}، {{HTMLElement("template")}}. |
| حذف تگ | هیچ‌کدام. تگ شروع و پایان اجباری است. |
| والدین مجاز | هر عنصری که محتوای جریان را می‌پذیرد. |
| نقش ARIA ضمنی | `list` |
| نقش‌های ARIA مجاز | هر نقشی به جز `list` (زیرا `menu` نقش `list` را دارد). |
| رابط DOM | {{domxref("HTMLMenuElement")}} |

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- سایر عناصر لیست: {{HTMLElement("ol")}}، {{HTMLElement("ul")}}، {{HTMLElement("li")}}.
- {{HTMLElement("nav")}} برای ناوبری

```markdown
<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌های محتوا</a>
      </th>
      <td>
        <p>
          محتوای جریانی (<a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>). اگر عنصر حداقل یک عنصر <code>&lt;li&gt;</code> در فرزندان خود داشته باشد: محتوای قابل لمس (<a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">Palpable content</a>).
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <p>
          صفر یا چند بار تکرار از <code>&lt;li&gt;</code>، <code>&lt;script&gt;</code> و <code>&lt;template&gt;</code>.
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که محتوای جریانی (<a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>) را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role">list</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/directory_role"><code>directory</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a>,
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role">listbox</a></code>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role"><code>menu</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role"><code>menubar</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role"><code>radiogroup</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role"><code>tablist</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role"><code>toolbar</code></a> یا <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role"><code>tree</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLMenuElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- سایر عناصر HTML مرتبط با لیست: `<ol>`، `<ul>` و `<li>`.
```