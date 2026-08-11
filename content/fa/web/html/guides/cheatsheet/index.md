---
title: "HTML cheatsheet for syntax and common tasks"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Cheatsheet"
translated_by: "n8n + AI"
---

# برگه تقلب HTML برای نحو و کارهای رایج

وقتی با HTML کار می‌کنید، داشتن راهی سریع برای یادآوری نحوهٔ استفادهٔ درست از تگ‌ها و به‌کارگیری آن‌ها خیلی مفید است. MDN علاوه بر مستندات مرجع کامل HTML، مجموعه‌ای آموزشی و عمیق از راهنماهای HTML هم ارائه می‌دهد. اما در بسیاری از مواقع فقط به چند راهنمایی سریع در حین کار نیاز داریم. کل هدف برگهٔ تقلب همین است: دادن چند قطعه‌کد آماده و دقیق برای کاربردهای رایج.

> [!NOTE]
> تگ‌های HTML باید بر اساس ارزش معنایی (semantic) استفاده شوند، نه ظاهرشان. همیشه می‌توان با CSS ظاهر و حس یک تگ را کاملاً تغییر داد؛ بنابراین هنگام استفاده از HTML، روی معنا تمرکز کنید نه ظاهر.

## عناصر خطی (inline)

یک «element» بخشی واحدی از یک صفحهٔ وب است. برخی عناصر بزرگ هستند و عناصر کوچک‌تری را مثل ظرف داخل خود نگه می‌دارند. برخی عناصر کوچک هستند و داخل عناصر بزرگ‌تر «تودرتو» (nested) می‌شوند. به‌طور پیش‌فرض، «عناصر خطی» در یک صفحهٔ وب کنار هم ظاهر می‌شوند. آن‌ها فقط به اندازهٔ فضایی که نیاز دارند عرض اشغال می‌کنند و به‌صورت افقی کنار هم قرار می‌گیرند، مثل کلمه‌ها در یک جمله یا کتاب‌هایی که پهلوی هم در یک ردیف چیده شده‌اند. همهٔ عناصر خطی را می‌توان درون عنصر `<body>` قرار داد.

```markdown
| کاربرد | عنصر | مثال |
|--------|------|------|
| یک پیوند | `<a>` | ```html<br><a href="https://example.org">A link to example.org</a>.<br>``` |
| یک تصویر | `<img>` | ```html<br><img src="beast.png" width="50" /><br>``` |
| یک محفظهٔ درون‌خطی (inline container) | `<span>` | ```html<br>Used to group elements: for example, to <span style="color:blue">style them</span>.<br>``` |
| تأکید بر متن | `<em>` | ```html<br><em>I'm posh</em>.<br>``` |
| متن ایتالیک | `<i>` | ```html<br>Mark a phrase in <i>italics</i>.<br>``` |
| متن پررنگ | `<b>` | ```html<br>Bold <b>a word or phrase</b>.<br>``` |
| متن مهم | `<strong>` | ```html<br><strong>I'm important!</strong><br>``` |
| برجسته‌سازی متن | `<mark>` | ```html<br><mark>Notice me!</mark><br>``` |
| خط خورده | `<s>` | ```html<br><s>I'm irrelevant.</s><br>``` |
| زیرنویس (subscript) | `<sub>` | ```html<br>H<sub>2</sub>O<br>``` |
| متن کوچک | `<small>` | ```html<br>Used to represent the <small>small print</small> of a document.<br>``` |
| آدرس | `<address>` | ```html<br><address>Main street 67</address><br>``` |
| نقل‌قول متنی | `<cite>` | ```html<br>For more monsters, see <cite>The Monster Book of Monsters</cite>.<br>``` |
| بالانویس (superscript) | `<sup>` | ```html<br>x<sup>2</sup><br>``` |
| نقل‌قول درون‌خطی | `<q>` | ```html<br><q>Me?</q>, she said.<br>``` |
| شکست خط | `<br>` | ```html<br>Line 1<br />Line 2<br>``` |
| شکست خط احتمالی | `<wbr>` | ```html<br><div style="width: 200px">Llanfair<wbr />pwllgwyngyll<wbr />gogerychwyrndrobwllllantysiliogogogoch.</div><br>``` |
| تاریخ | `<time>` | ```html<br>Used to format the date. For example: <time datetime="2020-05-24">published on 23-05-2020</time>.<br>``` |
| قالب کد | `<code>` | ```html<br>This text is in normal format, but <code>this text is in code format</code>.<br>``` |
| صدا | `<audio>` | ```html<br><audio controls><source src="/shared-assets/audio/t-rex-roar.mp3" type="audio/mpeg" /></audio><br>``` |
| ویدئو | `<video>` | ```html<br><video controls width="250" src="/shared-assets/videos/flower.webm"><a href="/shared-assets/videos/flower.webm">Download WebM video</a></video><br>``` |
```

## عناصر بلوکی

از طرف دیگر، عناصر بلوکی تمام عرض یک صفحه وب را می‌گیرند. همچنین یک خط کامل از صفحه را اشغال می‌کنند و کنار هم قرار نمی‌گیرند. در عوض، مثل پاراگراف‌های یک مقاله یا بلوک‌های اسباب‌بازی در یک برج روی هم انباشته می‌شوند.

> [!NOTE]
> چون این برگه تقلب فقط به چند عنصر که ساختارهای خاصی را نشان می‌دهند یا معانی ویژه دارند محدود شده است، عنصر [`div`](/en-US/docs/Web/HTML/Reference/Elements/div) عمداً گنجانده نشده است — چون عنصر `div` هیچ چیز خاصی را نشان نمی‌دهد و معنای ویژه‌ای ندارد.

<table class="standard-table">
  <thead>
    <tr>
      <th scope="col">کاربرد</th>
      <th scope="col">عنصر</th>
      <th scope="col">مثال</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>یک پاراگراف ساده</td>
      <td><code>&lt;p&gt;</code></td>
      <td>
        <pre class="brush: html">
&#x3C;p>I'm a paragraph&#x3C;/p>
&#x3C;p>I'm another paragraph&#x3C;/p></pre>
      </td>
    </tr>
    <tr>
      <td>نقل‌قول بلند</td>
      <td><code>&lt;blockquote&gt;</code></td>
      <td>
        <pre class="brush: html">
They said:
&#x3C;blockquote>The blockquote element indicates
an extended quotation.&#x3C;/blockquote></pre>
      </td>
    </tr>
    <tr>
      <td>اطلاعات اضافی</td>
      <td><code>&lt;details&gt;</code></td>
      <td>
        <pre class="brush: html">
&#x3C;details>
  &#x3C;summary>HTML Cheat Sheet&#x3C;/summary>
  &#x3C;p>Inline elements&#x3C;/p>
  &#x3C;p>Block elements&#x3C;/p>
&#x3C;/details></pre>
      </td>
    </tr>
    <tr>
      <td>لیست نامرتب</td>
      <td><code>&lt;ul&gt;</code></td>
      <td>
        <pre class="brush: html">&#x3C;ul>
  &#x3C;li>I'm an item&#x3C;/li>
  &#x3C;li>I'm another item&#x3C;/li>
&#x3C;/ul></pre>
      </td>
    </tr>
    <tr>
      <td>لیست مرتب</td>
      <td><code>&lt;ol&gt;</code></td>
      <td>
        <pre class="brush: html">&#x3C;ol>
  &#x3C;li>I'm the first item&#x3C;/li>
  &#x3C;li>I'm the second item&#x3C;/li>
&#x3C;/ol></pre>
      </td>
    </tr>
    <tr>
      <td>لیست تعریفی</td>
      <td><code>&lt;dl&gt;</code></td>
      <td>
        <pre class="brush: html">&#x3C;dl>
  &#x3C;dt>A Term&#x3C;/dt>
  &#x3C;dd>Definition of a term&#x3C;/dd>
  &#x3C;dt>Another Term&#x3C;/dt>
  &#x3C;dd>Definition of another term&#x3C;/dd>
&#x3C;/dl></pre>
      </td>
    </tr>
    <tr>
      <td>خط افقی</td>
      <td><code>&lt;hr&gt;</code></td>
      <td>
        <pre class="brush: html">before&#x3C;hr />after</pre>
      </td>
    </tr>
    <tr>
      <td>عنوان متن</td>
      <td><code>&lt;h1&gt;-&lt;h6&gt;</code></td>
      <td>
        <pre class="brush: html">
&#x3C;h1> This is Heading 1 &#x3C;/h1>
&#x3C;h2> This is Heading 2 &#x3C;/h2>
&#x3C;h3> This is Heading 3 &#x3C;/h3>
&#x3C;h4> This is Heading 4 &#x3C;/h4>
&#x3C;h5> This is Heading 5 &#x3C;/h5>
&#x3C;h6> This is Heading 6 &#x3C;/h6></pre>
      </td>
    </tr>
  </tbody>
</table>