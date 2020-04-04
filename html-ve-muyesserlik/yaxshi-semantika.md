# Yaxşı semantika

Yaxşı semantikanı niyə istifadə etməli olduğunuz və niyə doğru iş üçün doğru HTML elementi istifadə etməli olduğunu haqqında artıq söhbət açmışıq. Bu mövzu müyəssərliyin çox pis qırıldığı nöqtə olduğu üçün laqeyd qalmamalı olduğunuz bir mövzudur.

Həqiqət budur ki, webdə hər kəs HTML ilə qəribə şeylər düzəldir. Bəziləri köhnəlmiş lakin hələ də unudulmayan praktikalardan istifadə edərək HTML-i incidir, bəziləri isə sadəcə buna məhəl qoymur. Lakin səbəbindən asılı olmayaraq, nə vaxt bu cür kodla rastlaşsanız bacardığınız qədər onu dəyişib, düzəltməyə çalışın.

Bəzi hallarda bunu edə bilməməyiniz müzakirə mövzusu ola bilər - saytınız hansısa software vasitəsilə generasiya olunub və sizin bunun üzərində tam idarəniz yoxdur və ya saytınızda dəyişə bilmədiyiniz "third party" məzmun ola bilər (misalçün, reklamlar).

Məqsədimiz "hər şey və ya heç nə" deyil, ancaq - etdiyiniz hər kiçik dəyişiklik saytın müyəssərliyini artırmağa kömək edə bilər.

## Mətn məzmunu

Ekran oxuyucularına edə biləcəyimiz ən yaxşı şey, yaxşı strukturlaşdırılmış, başlıqlı, paraqraflı, siyahılı və s. məzmun təqdim etməkdir. Yaxşı semantik nümunə aşağıdakı kimi ola bilər:

```html
<h1>Mənim başlığım</h1>

<p>Bu sənədin birinci hissəsidir.</p>

<p>Bu isə daha bir paraqrafdır.</p>

<ol>
  <li>Bu isə</li>
  <li>sizin oxumağınız üçün</li>
  <li>bir siyahıdır</li>
</ol>

<h2>İkinci dərəcəli başlıq</h2>

<p>
  Bu mənim məqaləmin ilk alt hissəsidir. Mən bu məqaləni hər kəsin tapmağını çox
  istərdim.
</p>

<h2>Daha bir ikinci dərəcəli başlıq</h2>

<p>
  Bu isə, ikinci alt hissədir. Düşünürəm ki, bu əvvəlkindən maraqlı alınıb.
</p>
```

Bu məqaləni hər hansı bir ekran oxuyucusu ilə yoxlaya bilərsiniz. Mətnin üzərindən naviqasiya etsəniz, bunun çox rahat olduğunu görəcəksiniz.

- Ekran oxuyucusu mətni oxuduqca hər bir başlığı xüsusilə qeyd edəcək və istifadəçiyə nəyin başlıq, nəyin paraqraf olduğunu aydın edəcək.
- Hər bir elementdən sonra dayanacaq və istifadəçiyə oxuma tempini seçmək imkanı yaradacaq.
- Əksər ekran oxuyucularında mövcud olan əvvəlki/sonrakı başlıqlara getmək ikmanından yararlanmağa kömək edəcək.
- Bəzi ekran oxuyucularında isə başlıqları, mündəricat kimi təqdim etmək imkanı yaracaq.

Bəzən insanlar, başlıqları və paraqrafları yazarkən, sadəcə görünüşə diqqət yetirib semantik olmayan HTML elementlərindən istifadə edirlər:

```html
<font size="7">Mənim başlığım</font> <br /><br />
Bu sənədin birinci hissəsidir.
<br /><br />
Bu isə daha bir paraqrafdır.
<br /><br />
1. Bu isə
<br /><br />
2. sizin oxumağınız üçün
<br /><br />
3. bir siyahıdır
<br /><br />
<font size="5">İkinci dərəcəli başlıq</font>
<br /><br />
Bu mənim məqaləmin ilk alt hissəsidir. Mən bu məqaləni hər kəsin tapmağını çox
istərdim.
<br /><br />
<font size="5">Daha bir ikinci dərəcəli başlıq</font>
<br /><br />
Bu isə, ikinci alt hissədir. Düşünürəm ki, bu əvvəlkindən maraqlı alınıb.
```

Görüdüyünüz bu nümunə isə, çoxumuza tanış olan, semantik olmayan HTML-in bariz nümunəsidir. Təəssüflər olsun ki, bu cür markap ekran oxuycularını heç də sevindirmir - bu markapdan ekran oxuyucuları vasitəsilə mündəricat əldə edə bilməzsiniz, ekran oxuyucuları mətnin hansı hissəsində dayanmalı olduqlarını, hansı hissənin paraqraf, hansının başlıq olduğunu bilməyəcəklər. Bu səbəbdən də hamsını bir ağızdan oxuyub keçəcəklər.

Müyəssərlikdən əlavə, bu cür markap digər çətinliklər də yaradır - yazılmış HTML-i CSS vasitəsilə görünüş vermək olduqca çətin olacaq, fikir versəniz, düzgün əməlli CSS selektorlarından istifadə etmək də olmur. Həmçinin bu vəziyyət, JavaScript vasitəsilə markapda dəyişiklik etməyi də çətinləşdirir.

## Aydın dil işlətmək

Mətndə işlətdiyiniz dil də müyəssərlikdə böyük rol oynayır. Mətnlərinizdə mürəkkəb olmayan aydın dildən istifadə etməli və gərəkzi jarqon və şivələrdən mümkün qədər az istifadə etməlisiniz. Bu sadəcə əqli pozğunluqları olan insanlara deyil hamıya müsbət təsir göstərəcək. Bundan əlavə, ekran oxuyucularının oxumaqdan çətinlik çəkdiyi simbollardan istifadə etməyi də mümkün qədər azaldın:

- Əgər alternativiniz varsa tire işarəsindən istifadə etməyin. Misalçün, 5-7 yazmaq əvəzinə, 5-dən 7-yədək yaza bilərsiniz.
- Qısaltmaları açıq şəkildə yazın. Misalçün, 10 Yan yazmaq əvəzinə 10 Yanvar yazın.
- Akronimləri ən azından bir neçə dəfə açıq şəkildə yazın. HTML yazmaq əvəzinə Hyper Text Markup Language yaza bilərsiniz.

## Səhifə sxemi (layout)

Əvvəllər bir çox insan səhifənin layoutunu hazırlamaq üçün HTML cədvəllərindən istifadə edirdilər - cədvəlin başlığını, sütunları və xanaları istifadə etməklə səhifənin müstəlif yerlərini təsvir edirdilər. Bu heç də yaxşı fikir deyil çünki səhifənin layoutu daha da mürəkkəbləşdikdə ekran oxuyucuları mənalı bir şey oxumaqda çətinlik çəkəcəklər.

HTML cədvəli ilə hazırlanmış bir səhifə layoutunu (table layout) sizə nümunə kimi göstərək:

```html
<table width="1200">
  <!-- əsas başlıq sətiri -->
  <tr id="heading">
    <td colspan="6">
      <h1 align="center">Başlıq</h1>
    </td>
  </tr>
  <!-- nav menu sətiri  -->
  <tr id="nav" bgcolor="#ffffff">
    <td width="200">
      <a href="#" align="center">Əsas səhifə</a>
    </td>
    <td width="200">
      <a href="#" align="center">Komandamız</a>
    </td>
    <td width="200">
      <a href="#" align="center">Layihələr</a>
    </td>
    <td width="200">
      <a href="#" align="center">Əlaqə</a>
    </td>
    <td width="300">
      <form width="300">
        <input type="search" name="q" placeholder="Axtarış sözü" width="300" />
      </form>
    </td>
    <td width="100">
      <button width="100">Getdik!</button>
    </td>
  </tr>
  <!-- aralıq sətri -->
  <tr id="spacer" height="10">
    <td></td>
  </tr>
  <!-- əsas məzmun və yan sətir -->
  <tr id="main">
    <td id="content" colspan="4" bgcolor="#ffffff">
      <!-- əsas məzmun burada olacaq -->
    </td>
    <td id="aside" colspan="2" bgcolor="#ff80ff" valign="top">
      <h2>Əlaqəli</h2>
      <!-- yan məzmun burada olacaq -->
    </td>
  </tr>
  <!-- ararlıq sətir -->
  <tr id="spacer" height="10">
    <td></td>
  </tr>
  <!-- footer sətiri -->
  <tr id="footer" bgcolor="#ffffff">
    <td colspan="6">
      <p>©Copyright 2050. Bütün hüquqları qorunur</p>
    </td>
  </tr>
</table>
```

Bu cür layoutu anlamağa çalışarkən ekran oxuyucusu sizə mövcud bir cədvəlin olduğunu bildirəcək. Daha sonra isə həmin cədvələ obyekt kimi baxacaq və içərisindəki hər bir xanaya və sütunlara ayrı ayrı nəzər yetirəcəksiniz.

Cədvəl layoutları keçmişin qalıqlarıdır - onları CSS dəstəyinin brauzerlərdə yaxşı olmadığı vaxtlarda istifadə etmək normal qəbul olunurdu, indi isə onlar sadəcə ekran oxuyucularının başını qarışdırmaqla məşğuldur. Əlavə olaraq bu cür layoutların markapı (HTML kodu) daha uzun olur və idarə edilməsi zamanla çətinləşir. Müasir bir səhifə layoutunun nümunəsi isə aşağıdakı kimi olmalıdır:

```html
<header>
  <h1>Başlıq</h1>
</header>

<nav>
  <!-- əsas naviqasiya burada olacaq -->
</nav>

<!-- Səhifəmizin əsas məzmunu burada olacaq -->
<main>
  <!-- Burada bir məqalə var -->
  <article>
    <h2>Məqalənin başlığı</h2>

    <!-- Məqalənin məzmunu burada olacaq -->
  </article>

  <aside>
    <h2>Əlaqəli məzmun</h2>

    <!-- Yan məzmun burada olacaq -->
  </aside>
</main>

<!-- Bu isə bizim footerimizdir -->

<footer>
  <!-- footer məzmunu burada olacaq -->
</footer>
```

Bu şəkildə yazılmış markap ekran oxuyucuları üçün problem yaratmayacaq və kod baxımından da daha az və səliqəli koddan ibarətdir. Bu da o deməkdir ki, bu cür markap idarə edilməsi daha rahat oalcaq və istifadəçilərin qurğusuna yüklənmək üçün daha az vaxt alacaq.

Bu cür layoutu yaratmağın başqa bir yolu isə çoxlus sayda iç-içə `<div>` elementlərindən istifadə etməkdir. Lakin layout hazırlayarkən uyğun elementlərdən - naviqasiya üçün `<nav>` elementindən, məqalələr üçün `<article>` elementindən, footer üçün `<footer>` elementindən və s. - istifadə etməyiniz tövsiyyə olunur. Bunu etməyiniz, ekran oxuyucuları üçün əlavə semantik məlumat vermiş olacaq və istifadəçilər saytınızı daha rahat istifadə edə biləcəklər.

## UI Kontrolları

UI kontrolları dedikdə istifadəçinin web səhifə ilə qarşılıqlı əlaqədə olmasını təmin edən elemenlər - buttonlar, linklər, form elementləri və s. - nəzərdə tutulur.

UI kontrollarının əsas xüsusiyyətlərindən biri odur ki, brauzerlər defolt olaraq onların klaviatura ilə idarə edilməsi imkanı yaradır. Buna şahid olmaq üçün bu fayla nəzər yetirməyiniz xahiş olunur: [native-keyboard-accessibility.html](https://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html) - səhifə açıldığında `Tab` düyməsi ilə müxtəlif keçidlərin, buttonların və inputların üzərindən klaviatura ilə hərəkət edə və aktiv edə bilərsiniz. Üzərində olduğunuz elementə baxsanız görəcəksiniz ki, brauzer defolt olaraq verilmiş stillərlə sizə fokuslandığınız nöqtəni işarə edir. Fokuslanmış elementlər defolt olaraq vurğulanmışdır:

![tab focus demonstation](https://media.prod.mdn.mozit.cloud/attachments/2016/10/18/14215/943a9845e5abd91bda6236067ea19f1e/button-focused-unfocused.png)

Siz Enter/Return düyməsini basmaqla üzərində olduğunuz elementi aktivləşdirə və ya üzərində olduğunuz text inputun içərisinə yazı yaza bilərsiniz. Bu funksionallığı əldə etmək üçün isə sadəcə düzgün HTML elementlərindən istifadə etməyiniz kifayətdir:

```html
<h1>Keçidlər</h1>

<p>Bu keçid <a href="https://www.mozilla.org">Mozilla</a>yadır.</p>

<p>
  <a href="https://developer.mozilla.org">Mozilla Developer Network</a>ə daha
  bir keçid.
</p>

<h2>Düymələr</h2>

<p>
  <button data-message="Bu birinci buttondandır">Məni kliklə!</button>
  <button data-message="Bu ikinci buttondandır">Məni də kliklə!</button>
  <button data-message="Bu isə üçüncü buttondandır">Və məni də!</button>
</p>

<h2>Form</h2>

<form>
  <div>
    <label for="name">Adınızı daxil edin:</label>
    <input type="text" id="name" name="name" />
  </div>
  <div>
    <label for="age">Yaşınızı daxil edin:</label>
    <input type="text" id="age" name="age" />
  </div>
  <div>
    <label for="mood">Kefinizi seçin:</label>
    <select id="mood" name="mood">
      <option>Xoşbəxt</option>
      <option>Kefsiz</option>
      <option>Əsəbi</option>
      <option>Narahat</option>
    </select>
  </div>
</form>
```

Lakin həmişə olduğu kimi insanlar HTML ilə qəribə şeylər etməyə davam edirlər. Misalçün, bəzən düymələrin `<div>` elementi ilə yazıldığının şahidi ola bilərik:

```html
<div data-message="Bu birinci buttondandır">Məni kliklə!</div>
<div data-message="Bu ikinci buttondandır">Məni də kliklə!</div>
<div data-message="Bu isə üçüncü buttondandır">Və məni də!</div>
```

Belə kod yazmaq heç tövsiyyə olunmur - bunu yazmaqla hazır keyboard accessibility funksionallığını və defolt olaraq buttonlara verilmiş dizaynı itirmiş olursunuz.

## Klaviatura müyəssərliyini geri qazanmaq

Bu cür yazılmış kodda keyboard accessibility funksionallığını geri qazanmaq bir az artıq iş tələb edir. Aşağıdakı nümunədə saxta `<div>` düymələrimizə `tabindex="0"` atributunu əlavə edərək fokus olunmaq funksionallığını gətirmişik:

```html
<div data-message="Bu birinci buttondandır" tabindex="0">Məni kliklə!</div>
<div data-message="Bu ikinci buttondandır" tabindex="0">Məni də kliklə!</div>
<div data-message="Bu isə üçüncü buttondandır" tabindex="0">Və məni də!</div>
```

Bunun nümunəsini [fake-div-buttons.html](https://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html) faylında görə bilərsiniz.

Qısası, `tabindex` atributu klaviatura ilə idarə oluna bilən elementlərin sırasını müəyyən edir. Bunu etmək bəzi qarışıqlıqlar yarada biləcəyi üçün yaxşı fikir sayılmır. Həqiqətən ehtiyacınız olmadığı təqdirdə bunu etməməyinizi tövsiyyə edirik. `tabindex`-in iki əsas istifadə üsulu var:

- `tabindex="0"` yuxarıda qeyd etdiyimiz kimi, klaviatura ilə idarə oluna bilməyən - interaktiv olmayan elementlərin interaktiv olunmasını təmin edir. Bu `tabindex`-in ən çox istifadə olunan dəyərlədindəndir.
- `tabindex="-1"` dəyəri interaktiv olmayan elementlərin kod vasitəsilə (misalçün JavaScript ilə) fokus oluna bilməsini təmin edir.

Yuxarıdakı əlavələrin bizə düymələrin arasında naviqasiya imkanı yaratmasına baxmayaraq, biz həmin elemntləri Enter/Return düymələri ilə aktiv edə bilmərik. Bunun üçün JavaScript ilə kiçik bir iş görmək lazım olacaq:

```javascript
document.onkeydown = function (e) {
  // The Enter/Return key
  if (e.keyCode === 13) {
    document.activeElement.click();
  }
};
```

Burada biz, `document` obyektinə listener əlavə etməklə, klaviatura vasitəsilə fokuslanmış elementi aşkar edirik. Daha sonra isə Enter/Return düyməsinin basılıb basılmadığını `keyCode` vasitəsilə təyin edib, səhifədəki `activeElement`-i JavaScript ilə klikləyirik.

Gördüyünüz kimi, əvvəlcədən bizə hazır verilmiş funksionallığı geri qazanmaq üçün əlavə çox iş görmək lazım olur. **Yaxşısı budur ki, düzgün işlər üçün düzgün HTML elementlərindən istifadə edək.**

## Mənalı mətn etiketləri

UI kontrol etiketləri (UI control labels) bütün istifadəçilər üçün yararlıdır, lakin onları düzgün istifadə etmək əlilliyi olan isitfadəçilər üçün daha yararlı ola bilər.

Button və linklərdə mümkün olduğu qədər anlaşıla bilən mətn etiketlərindən istifadə edin. "Click here" və s. bunun kimi ayrılıqda heç bir məna ifadə etməyən adlardan istifadə etməyin. Bəzi ekran oxuycusu istifadəçiləri bu cür linklərin və buttonların siyahısını əldə etmək istəyirlər və düymələrin üzərinə yazdığınızı etiketlər onlar üçün anlaşıqlı olmaya bilər.

Yazdığınız etiketlərin kontekst daxilində və kontekstdən kənarda məna ifadə etdiyindən əmin olun. Aşağıdakı kod parçası yaxşı adlandırılmış linkin bir nümunəsidir:

```html
<p>
  Balinalar həqiqətən möhtəşəm varlıqlardır.
  <a href="whales.html">Balinalar haqqında daha çox öyrən</a>.
</p>
```

Aşağıdakı isə, pis adlandırılmış linkin bir nümunəsidir:

```html
<p>
  Balinalar həqiqətən möhtəşəm varlıqlardır. Onlar haqqında daha çox öyrənmək
  üçün, <a href="whales.html">buraya klikləyin</a>.
</p>
```

Form etiketləri də həmçinin diqqət etməli olduğumuz nöqtədir. Bu etiketlər hansı form elementinin hansı məqsədə qulluq etdiyinin qısa izahıdır. Gəlin aşağıdakı nümunıəyə baxaq:

```html
Adınızı daxil edin: <input type="text" id="name" name="name" />
```

Bu nümunə əlil insanlar üçün heç də yararlı deyil. Burada yazılmış etiketin göstərilən input ilə necə əlaqəli olduğunu bildirən heç bir bağlantı yoxdur və əgər formu görümürsünüzsə onu doldurmağınız da sizin üçün çətin ola bilər.

Aşağıdak nümunə isə bunu etməyin düzgün variantıdır:

```html
<div>
  <label for="name">Adınızı daxil edin:</label>
  <input type="text" id="name" name="name" />
</div>
```

Bu cür yazılmış kod ilə göstərilən input və etiket arasında bağlılıq mövcuddur və ekran oxuyucularından istifadə etdən istifadəçiləriniz inputu nə üçün doldurmalı olduqlarını daha yaxşı anlamış olacaqlar. Əksər brauzerlərdə isə, etiket və inputu əlaqələndirmək vasitəsilə siz etiketə kliklədiyinizdə əlaqəli form elementinə fokuslanmış olursunuz. Bu, sözügedən form elementinə klik üçün daha böyük sahə verir və onu seçməyi rahatlaşdırır.

Daha sonra: [Müyəssər Məlumat Cədvəlləri](html-ve-muyesserlik/melumat-cedvelleri.md)
