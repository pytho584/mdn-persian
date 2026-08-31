---
title: "WAI-ARIA Roles"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles"
translated_by: "n8n + AI"
---

---
title: WAI-ARIA Roles
short-title: Roles
slug: Web/Accessibility/ARIA/Reference/Roles
page-type: landing-page
sidebar: accessibilitysidebar
---

نقش‌های ARIA معنای معنایی به محتوا می‌بخشند و به صفحه‌خوان‌ها و سایر ابزارها اجازه می‌دهند تا تعامل با یک شیء را به‌گونه‌ای ارائه و پشتیبانی کنند که با انتظارات کاربر از آن نوع شیء هماهنگ باشد. از نقش‌های <abbr>ARIA</abbr> می‌توان برای توصیف عناصری استفاده کرد که به‌طور بومی در HTML وجود ندارند یا وجود دارند اما هنوز از پشتیبانی کامل مرورگر برخوردار نیستند.

به‌طور پیش‌فرض، بسیاری از عناصر معنایی HTML دارای نقش هستند؛ برای مثال، `<input type="radio">` دارای نقش «radio» است. عناصر غیرمعنایی در HTML نقشی ندارند؛ `<div>` و `<span>` بدون معناشناسی افزوده، مقدار `null` برمی‌گردانند. ویژگی `role` می‌تواند معناشناسی را فراهم کند.

نقش‌های ARIA با استفاده از `role="role type"` به عناصر HTML اضافه می‌شوند، که در آن _نوع نقش_ نام یک نقش در مشخصات ARIA است. برخی نقش‌ها مستلزم گنجاندن حالت‌ها یا ویژگی‌های مرتبط ARIA هستند؛ برخی دیگر فقط در ارتباط با نقش‌های دیگر معتبرند.

برای مثال، `<ul role="tabpanel">` به‌وسیله صفحه‌خوان‌ها به‌عنوان «پنل تب» اعلام می‌شود. با این حال، اگر پنل تب دارای تب‌های تودرتو نباشد، عنصر دارای نقش tabpanel در واقع پنل تب نیست و دسترس‌پذیری عملاً تحت تأثیر منفی قرار گرفته است.

[حالت‌ها و ویژگی‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes) مرتبط با هر نقش در صفحه‌های همان نقش گنجانده شده‌اند و هر ویژگی نیز صفحه اختصاصی خود را دارد.

## انواع نقش‌های ARIA

۶ دسته از نقش‌های ARIA وجود دارد:

### ۱. نقش‌های ساختار سند

نقش‌های ساختار سند برای ارائه توصیف ساختاری از یک بخش محتوا استفاده می‌شوند. بیشتر این نقش‌ها دیگر نباید استفاده شوند، زیرا مرورگرها اکنون از عناصر HTML معنایی با همان معنا پشتیبانی می‌کنند. نقش‌هایی که معادل HTML ندارند، مانند نقش‌های presentation، toolbar و tooltip، اطلاعات ساختار سند را در اختیار فناوری‌های کمکی مانند صفحه‌خوان‌ها قرار می‌دهند، زیرا برچسب‌های بومی HTML معادل در دسترس نیستند.

- [`toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role)
- [`tooltip`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tooltip_role)
- [`feed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role)
- [`math`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/math_role)
- [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) / [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)
- [`note`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/note_role)

برای بیشتر نقش‌های ساختار سند، عناصر معادل HTML معنایی در دسترس و پشتیبانی‌شده هستند. از استفاده از موارد زیر خودداری کنید:

- [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [`article`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/article_role) (از {{HTMLElement('article')}} استفاده کنید)
- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) (از {{HTMLElement('td')}} استفاده کنید)
- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) (از `{{HTMLElement('th', '&lt;th scope="col">')}}` استفاده کنید)
- [`definition`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/definition_role) (از {{HTMLElement('dfn')}} استفاده کنید)
- [`directory`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/directory_role)
- [`document`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role)
- [`figure`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/figure_role) (در عوض از {{HTMLElement('figure')}} استفاده کنید)
- [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
- [`heading`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role) (از {{HTMLElement("Heading_Elements", "h1")}} تا {{HTMLElement("Heading_Elements", "h6")}} استفاده کنید)
- [`img`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role) (در عوض از {{HTMLElement('img')}} یا {{HTMLElement('picture')}} استفاده کنید)
- [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role) (در عوض از {{HTMLElement('ul')}} یا {{HTMLElement('ol')}} استفاده کنید)
- [`listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role) (در عوض از {{HTMLElement('li')}} استفاده کنید)
- [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role) (در عوض از {{HTMLElement('meter')}} استفاده کنید)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) (از {{HTMLElement('tr')}} همراه با {{HTMLElement('table')}} استفاده کنید)
- [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) (از {{HTMLElement('thead')}}، {{HTMLElement('tfoot')}} و {{HTMLElement('tbody')}} استفاده کنید)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) (از `{{HTMLElement('th','&lt;th scope="row">')}}` استفاده کنید)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) (اگر فوکوس ندارد از {{HTMLElement('hr')}} استفاده کنید)
- [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) (از {{HTMLElement('table')}} استفاده کنید)
- [`term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role) (از {{HTMLElement('dfn')}} استفاده کنید)

این موارد برای کامل‌بودن فهرست شده‌اند، اما در بیشتر موارد به‌ندرت (در صورت وجود) مفید هستند:

- [`associationlist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`associationlistitemkey`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`associationlistitemvalue`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`blockquote`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`caption`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`code`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`deletion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`emphasis`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`insertion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`paragraph`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`strong`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`subscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`superscript`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`time`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)

### ۲. نقش‌های ویجت

نقش‌های ویجت برای تعریف الگوهای تعاملی رایج استفاده می‌شوند. مانند نقش‌های ساختار سند، برخی از نقش‌های ویجت دارای معناشناسی مشابه با عناصر بومی HTML با پشتیبانی خوب هستند و بنابراین باید از آن‌ها اجتناب شود. تفاوت کلیدی این است که نقش‌های ویجت معمولاً برای تعامل به جاوااسکریپت نیاز دارند، در حالی که نقش‌های ساختار سند اغلب چنین نیازی ندارند.

- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) (هنگامی که قابل فوکوس است)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)
- [`tabpanel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

از [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)، [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)، [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`link`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role)، [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)، [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)، [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)، [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)، [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role) و [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) استفاده نکنید؛ این موارد را برای کامل‌بودن فهرست آورده‌ایم. برای بیشتر آن‌ها، معادل‌های معنایی با تعامل‌پذیری دسترس‌پذیر موجود و پشتیبانی‌شده هستند. برای اطلاعات بیشتر به مستندات هر نقش مراجعه کنید.

#### نقش‌های ویجت ترکیبی

- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
- [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
- [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

از [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role) و [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role) استفاده نکنید؛ این موارد را برای کامل‌بودن فهرست آورده‌ایم. برای اطلاعات بیشتر به مستندات هر نقش مراجعه کنید.

توجه داشته باشید که یک نقش ویجت (`role="widget"`) نیز وجود دارد که یک نقش انتزاعی است و در دسته نقش‌های ویجت قرار نمی‌گیرد.

### ۳. نقش‌های لندمارک

نقش‌های لندمارک راهی برای شناسایی سازمان‌دهی و ساختار یک صفحه وب فراهم می‌کنند. با طبقه‌بندی و برچسب‌گذاری بخش‌های یک صفحه، اطلاعات ساختاری که به‌صورت بصری از طریق چیدمان منتقل می‌شود، به‌صورت برنامه‌نویسی‌شده بازنمایی می‌شود. صفحه‌خوان‌ها از نقش‌های لندمارک برای ارائه ناوبری صفحه‌کلید به بخش‌های مهم یک صفحه استفاده می‌کنند. از این نقش‌ها به‌میزان محدود استفاده کنید. تعداد بیش از حد نقش‌های لندمارک در صفحه‌خوان‌ها «نویز» ایجاد می‌کند و درک چیدمان کلی صفحه را دشوار می‌سازد.

- [`banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role) (سربرگ سند {{HTMLElement('header')}})
- [`complementary`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role) ({{HTMLElement('aside')}})
- [`contentinfo`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role) (پابرگ سند {{HTMLElement('footer')}})
- [`form`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role) ({{HTMLElement('form')}})
- [`main`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role) ({{HTMLElement('main')}})
- [`navigation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role) ({{HTMLElement('nav')}})
- [`region`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role) ({{HTMLElement('section')}})
- [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role) ({{HTMLElement('search')}})

### ۴. نقش‌های ناحیه زنده

نقش‌های ناحیه زنده برای تعریف عناصری با محتوایی که به‌صورت پویا تغییر خواهد کرد استفاده می‌شوند. کاربران بینا می‌توانند تغییرات پویا را زمانی که از نظر بصری قابل توجه هستند ببینند. این نقش‌ها به کاربران کم‌بینا و نابینا کمک می‌کنند تا از به‌روزرسانی محتوا مطلع شوند. فناوری‌های کمکی، مانند صفحه‌خوان‌ها، می‌توانند اعلام تغییرات محتوای پویا را انجام دهند:

- [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)
- [`log`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)
- [`marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role)
- [`status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)
- [`timer`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/timer_role)

### ۵. نقش‌های پنجره

نقش‌های پنجره، زیرپنجره‌هایی را در همان پنجره و نسبت به پنجره اصلی سند تعریف می‌کنند، مانند دیالوگ‌های مودال بازشو:

- [`alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role)
- [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)

### ۶. نقش‌های انتزاعی

نقش‌های انتزاعی فقط برای استفاده توسط مرورگرها در نظر گرفته شده‌اند تا به سازمان‌دهی و روان‌سازی یک سند کمک کنند. توسعه‌دهندگانی که نشانه‌گذاری HTML می‌نویسند نباید از آن‌ها استفاده کنند. انجام این کار به انتقال اطلاعات معنی‌دار به فناوری‌های کمکی یا کاربران منجر نخواهد شد.

از [`command`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/command_role)، [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`input`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/input_role)، [`landmark`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/landmark_role)، [`range`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/range_role)، [`roletype`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/roletype_role)، [`section`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/section_role)، [`sectionhead`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/sectionhead_role)، [`select`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/select_role)، [`structure`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structure_role)، [`widget`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/widget_role) و [`window`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/window_role) استفاده نکنید.

> [!NOTE]
> از نقش‌های انتزاعی در سایت‌ها و برنامه‌های خود استفاده نکنید. این نقش‌ها برای استفاده مرورگرها هستند و فقط برای مرجع فهرست شده‌اند.

> [!WARNING]
> «نقش‌های انتزاعی برای هستان‌شناسی استفاده می‌شوند. نویسندگان **نباید** از نقش‌های انتزاعی در محتوا استفاده کنند.» - مشخصات <abbr>WAI-ARIA</abbr>

## نقش‌های تعریف‌شده در MDN

صفحات مرجع زیر نقش‌های WAI-ARIA را که در <abbr>MDN</abbr> بحث شده‌اند پوشش می‌دهند.

{{SubpagesWithSummaries}}

## همچنین ببینید

- [استفاده از ARIA: نقش‌ها، حالت‌ها و ویژگی‌ها](/en-US/docs/Web/Accessibility/ARIA/Guides/Techniques)
- [حالت‌ها و ویژگی‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes)