---
title: "itemscope HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope"
translated_by: "n8n + AI"
---

**`itemscope`** یک ویژگی (attribute) سراسری از نوع boolean است که محدودهٔ ابرداده‌های مرتبط را مشخص می‌کند. با تنظیم `itemscope` روی یک عنصر، یک آیتم جدید ایجاد می‌شود که شامل مجموعه‌ای از جفت‌های نام-مقدار (name-value pairs) مرتبط با آن عنصر است.

ویژگی مرتبط دیگر، [`itemtype`](/fa/docs/Web/HTML/Reference/Global_attributes/itemtype)، برای تعیین URL معتبر یک واژگان (vocabulary) مانند [schema.org](https://schema.org/) استفاده می‌شود که زمینهٔ آیتم و ویژگی‌های آن را توصیف می‌کند. در تمام مثال‌های زیر، واژگان از [schema.org](https://schema.org/) گرفته شده است.

هر عنصر HTML می‌تواند دارای `itemscope` باشد. یک عنصر دارای `itemscope` که `itemtype` هم ندارد، باید حتماً `itemref` داشته باشد.

> **توجه:** اطلاعات بیشتر دربارهٔ ویژگی `itemtype` را در <https://schema.org/Thing> ببینید.

## نکات استفاده

### ویژگی‌های id در itemscope

وقتی `itemscope` را روی یک عنصر قرار می‌دهید، یک آیتم جدید ساخته می‌شود. این آیتم شامل گروهی از جفت‌های نام-مقدار است. برای عناصری که هم `itemscope` و هم `itemtype` دارند، می‌توانید ویژگی [`id`](/fa/docs/Web/HTML/Reference/Global_attributes/id) را نیز مشخص کنید. از `id` برای تعیین یک شناسهٔ سراسری (global identifier) برای آیتم جدید استفاده می‌شود. این شناسه به آیتم اجازه می‌دهد با سایر آیتم‌های موجود در صفحات دیگر وب ارتباط برقرار کند.

## مثال‌ها

### نمایش داده‌های ساختاریافته برای یک فیلم

مثال زیر `itemtype` را به صورت `http://schema.org/Movie` تعیین کرده و چهار ویژگی `itemprop` مرتبط را مشخص می‌کند.

| `itemscope` | `itemtype` | `itemprop` (نام ویژگی) | `itemprop` (مقدار ویژگی) |
|-------------|------------|------------------------|---------------------------|
| ✅          | Movie      | director               | James Cameron             |
|             |            | genre                  | Science Fiction           |
|             |            | name                   | Avatar                    |
|             |            | trailer                | https://youtu.be/0AY1XIkX7bY |

```html
<div itemscope itemtype="https://schema.org/Movie">
  <h1 itemprop="name">Avatar</h1>
  <span>
    Director: <span itemprop="director">James Cameron</span> (born August 16,
    1954)
  </span>
  <span itemprop="genre">Science fiction</span>
  <a href="https://youtu.be/0AY1XIkX7bY" itemprop="trailer">Trailer</a>
</div>
```

### نمایش داده‌های ساختاریافته برای یک دستور پخت

در مثال زیر چهار ویژگی `itemscope` وجود دارد. هر `itemscope` محدودهٔ `itemtype` متناظر خود را مشخص می‌کند. `itemtype`های `Recipe`، `AggregateRating` و `NutritionInformation` در این مثال بخشی از داده‌های ساختاریافته [schema.org](https://www.schema.org/) برای یک دستور پخت هستند که توسط اولین `itemtype` یعنی `http://schema.org/Recipe` مشخص شده است.

<table class="standard-table">
  <tbody>
    <tr>
      <td rowspan="14">itemscope</td>
      <td>itemtype</td>
      <td colspan="2">Recipe</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>Grandma's Holiday Apple Pie</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>image</td>
      <td>https://c1.staticflickr.com/1/30/42759561_8631e2f905_n.jpg</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>datePublished</td>
      <td>2022-11-05</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>description</td>
      <td>
        This is my grandmother's apple pie recipe. I like to add a dash of
        nutmeg.
      </td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>prepTime</td>
      <td>PT30M</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>cookTime</td>
      <td>PT1H</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>totalTime</td>
      <td>PT1H30M</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>recipeYield</td>
      <td>1 9" pie (8 servings)</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>recipeIngredient</td>
      <td>Thinly-sliced apples: 6 cups</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>recipeIngredient</td>
      <td>White sugar: 3/4 cup</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>recipeInstructions</td>
      <td>
        1. Cut and peel apples 2. Mix sugar and cinnamon. Use additional sugar
        for tart apples.
      </td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td colspan="2">author [Person]</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>Carol Smith</td>
    </tr>
    <tr>
      <td rowspan="3">itemscope</td>
      <td>itemprop[itemtype]</td>
      <td colspan="2">aggregateRating [AggregateRating]</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>ratingValue</td>
      <td>4.0</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>reviewCount</td>
      <td>35</td>
    </tr>
    <tr>
      <td rowspan="4">itemscope</td>
      <td>itemprop[itemtype]</td>
      <td colspan="2">nutrition [NutritionInformation]</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>servingSize</td>
      <td>1 medium slice</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>calories</td>
      <td>250 cal</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>fatContent</td>
      <td>12 g</td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> ابزار کاربردی برای استخراج ساختارهای microdata از HTML، ابزار [Rich Results Testing Tool](https://search.google.com/test/rich-results) گوگل است. آن را روی HTML نشان‌داده‌شده امتحان کنید.

#### HTML

```html
<div itemscope itemtype="https://schema.org/Recipe">
  <h2 itemprop="name">Grandma's Holiday Apple Pie</h2>
  <img
    itemprop="image"
    src="https://c1.staticflickr.com/1/30/42759561_8631e2f905_n.jpg"
    width="50"
    height="50" />
  <p>
    By
    <span itemprop="author" itemscope itemtype="https://schema.org/Person">
      <span itemprop="name">Carol Smith</span>
    </span>
  </p>
  <p>
    Published:
    <time datetime="2022-11-05" itemprop="datePublished">
      November 5, 20022
    </time>
  </p>
  <span itemprop="description">
    This is my grandmother's apple pie recipe. I like to add a dash of nutmeg.
  </span>
  <br />
  <span
    itemprop="aggregateRating"
    itemscope
    itemtype="https://schema.org/AggregateRating">
    <span itemprop="ratingValue">4.0</span> stars based on
    <span itemprop="reviewCount">35</span> reviews
  </span>
  <br />
  Prep time: <time datetime="PT30M" itemprop="prepTime">30 min</time>
  <br />
  Cook time: <time datetime="PT1H" itemprop="cookTime">1 hour</time>
  <br />
  Total time: <time datetime="PT1H30M" itemprop="totalTime">1 hour 30 min</time>
  <br />
  Yield: <span itemprop="recipeYield">1 9" pie (8 servings)</span>
  <br />
  <span
    itemprop="nutrition"
    itemscope
    itemtype="https://schema.org/NutritionInformation">
    Serving size: <span itemprop="servingSize">1 medium slice</span><br />
    Calories per serving: <span itemprop="calories">250 cal</span><br />
    Fat per serving: <span itemprop="fatContent">12 g</span><br />
  </span>
  <p>
    Ingredients:<br />
    <span itemprop="recipeIngredient">Thinly-sliced apples: 6 cups<br /></span>
    <span itemprop="recipeIngredient">White sugar: 3/4 cup<br /></span>
    …
  </p>
  Directions: <br />
  <div itemprop="recipeInstructions">
    1. Cut and peel apples<br />
    2. Mix sugar and cinnamon. Use additional sugar for tart apples. <br />
    …
  </div>
</div>
```

#### نتیجه

## مشخصات

## همچنین ببینید

- [Other different global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- سایر ویژگی‌های سراسری (global attributes) مرتبط با microdata:
  - [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - [`itemprop`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop)
  - [`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref)
  - [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype)