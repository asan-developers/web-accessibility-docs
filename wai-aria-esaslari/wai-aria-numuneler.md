# WAI-ARIA praktiki nümunələr

Bu məqalədə WAI-ARIA-nın əvvəlki məqalədə qeyd etdiyimiz dörd əsas istifadə sahələrinə ətraflı nəzər yetirəcəyik.

## İşarələr/Əlamətlər

WAI-ARIA saytımızda istifadə etdiyimiz elementlərə əlavə semantik məlumat yükləmək üçün [role atributu](https://www.w3.org/TR/wai-aria-1.1/#role_definitions)nu təqdim edir. İlkin olaraq `role` atributunun işi ekran oxuyucularına əlavə məlumat verməkdir ki, istifadəçilər səhifənizdəki elementləri tapa bilsin. Gəlin bunun canlı şahidi olmaq üçün [website-no-roles](https://github.com/mdn/learning-area/tree/master/accessibility/aria/website-no-roles) nümunəsinə baxaq ([canlı nümunə](https://mdn.github.io/learning-area/accessibility/aria/website-no-roles/)yə bax). Saytın strukturu aşağıdakı kimidir:

```html
<header>
  <h1>...</h1>
  <nav>
    <ul>
      ...
    </ul>
    <form>
      <!-- search form  -->
    </form>
  </nav>
</header>

<main>
  <article>...</article>
  <aside>...</aside>
</main>

<footer>...</footer>
```

Bu nümunəni ekran oxuyucusu ilə hər hansı bir müasir brauzerdə yoxlasanız faydalı məlumatlar ala biləcəksiniz. Misalçün, VoiceOver sizə aşağıdakı məlumatları verəcək:

- `<header>` elementində — "banner, 2 items" (başlıq və `<nav>`).
- `<nav>` elementində — "navigation 2 items" (siyahı və form).
- `<main>` elementində — "main 2 items" (məqalə və `<aside>`).
- `<aside>` elementində — "complementary 2 items" (başlıq və sihayı).
- Axtarış inputunda — "Search query, insertion at beginning of text".
- `<footer>` elementində — "footer 1 item".

Əgər VoiceOver-in işarələr (landmarks) menyusuna getsəniz görəcəksiniz ki, elementlərin əksəriyyəti tez-bazar istifadə olunmaq üçün səliqəli şəkildə siyahıya alınmışdır.

![voice over landmarks](https://media.prod.mdn.mozit.cloud/attachments/2016/11/24/14420/8456b032c1a7107f56457c76f071a1b1/landmarks-list.png)

Lakin bunda daha yaxşısını edə bilərik. Axtarış formu insanların tez tapmaq istəyəcəyi element olmasına baxmayaraq işarələr menyusunda siyahıya alınmamış və ya lazımlı bir element kimi görülməmişdir. Bundan əlavə axtarış xanasının axtarış üçün olduğu xüsusi olaraq vurğulanmışdır (`<input type="search">`).

Gəlin WAI-ARIA atributlarından istifadə edərək yuxarıdakı nümunəni təkmilləşdirək. Əvvəlkə bəzi elementlərə `role` atributu əlavə etməkdən başlayaq:

```html
<header>
  <h1>...</h1>
  <nav role="navigation">
    <ul>
      ...
    </ul>
    <form role="search">
      <!-- search form  -->
    </form>
  </nav>
</header>

<main>
  <article role="article">...</article>
  <aside role="complementary">...</aside>
</main>

<footer>...</footer>
```

Nümunə də həm də axtarış inputuna `aria-label` atributu əlavə olunmuşdur. Bu həmin inputun əlaqəli `<label>` elementinin olmamasına rəğmən ekran oxuyucusuna axtarış xanası ilə bağlı təsvir təqdim edəcəkdir. Əksər hallarda səhifənin dizaynını korlamamaq üçün bu cür axtarış inputlarına görünən `<label>` bağlanmır.

```html
<input
  type="search"
  name="q"
  placeholder="Search query"
  aria-label="Search through site content"
/>
```

İndi isə VoiceOveri istifadə etsək, bir qədər irəliləyiş olduğunu görəcəyik:

- Axtarış formu artıq ayrıca bir element kimi tanınır və landmarks menyusunda siyahıya alınır.
- Form inputu istifadə edildikdə əlavə olunmuş `aria-label` atributunun dəyəri səsli oxunur.

Bundan əlavə göstərdiyimiz sayt köhnə brauzerlərdən (misalçün IE8) istifadə edən istifadəçilər üçün daha müyəssər olacaq. Bu səbəbdən ARIA rollarını saytınızdakı elementlərə əlavə etmək yaxşı fikirdir. Və əgər hansısa səbəbdən saytınız ancaq `div` elementlərindən ibarətdirsə, o zaman ARIA rollarından mütləq istifadə etməlisiniz.

## Dinamik kontent yenilənmələri

DOM-a yüklənmiş, mətn məzmunundan tutmuş text alternativi olan bütün multimedia ekran oxucuları üçün müyəssərdir. Bu səbəbdən də ənənəvi statik web saytları görmə pozğunluğu olan insanlar üçün müyəssər etmək rahat işdir.

Məsələ orasındadır ki, müasir web tətbiqlər çox vaxt elə statik deyillər - onların içərisində çoxlu sayda dinamik olaraq yenilənən kontent, səhifə yenilənmədən [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest), [Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) və ya [DOM API](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)-larından istifadə edilərək daima dəyişən və yenilənən məzmun mövcuddur. Saytın bu hissələri tez-tez **canlı sahələr** (live regions) deyə adlandırılır.

Gəlin aşağıdakı nümunəyə baxaq - [aria-no-live.html](https://github.com/mdn/learning-area/blob/master/accessibility/aria/aria-no-live.html) ([canlı bax](https://mdn.github.io/learning-area/accessibility/aria/aria-no-live.html)). Bu nümunədə ixtiyari sitatlar göstərən qutu mövcuddur:

```html
<section>
  <h1>Random quote</h1>
  <blockquote>
    <p></p>
  </blockquote>
</section>
```

Yazılan JavaScript, `XMLHttpRequest` vasitəsilə içərisində bir sıra sitatlar olan JSON faylını yükləyir. Bu proses tamamlandıqdan sonra `setInterval()` vasitəsilə hər 10 saniyədən bir qutuda yeni sitat göstərilir:

```javascript
let intervalID = window.setInterval(showQuote, 10000);
```

Bu nümunə normal olaraq işləyəcək lakin ekran oxuyucusu işlədən istifadəçilər nə baş verdiyinin fərqinə baxmayacaqlar. Misalçün, chat otağı və ya hansısa strategiya oyunu kimi daim yenilənən dinamik contentlə bol olan bir saytınız olduğunu düşünün - bu halda istifadəçiyə saytda nə baş verdiyini başa salmaq müşkül məsələ olacaqdır.

Xoşbəxtlikdən WAI-ARIA bu cür bildirişləri vermək üçün faydalı bir mexanizm təklif edir - `aria-live` atributu. Bu atributu elementlərə əlavə etmək ekran oxuyucularını yenilənən kontenti oxumağa vadar edir. Kontentin hansı tezliklə oxunduğunu isə atributun dəyəri təyin edir:

- `off`: defolt dəyərdir. Yenilənmələr istifadəçiyə bildirilməməlidir.
- `polite`: Yenilənmələr sadəcə istifadəçi boş-bekar olduğunda biildirilməlidir.
- `assertive`: Yenilənmələr istifadəçiyə mümkün qədər tez çatdırılmalıdır.

Bu məlumata əsaslanaraq bayaqkı kodumuzu aşağıdakı kimi dəyişə bilərik:

```html
<section aria-live="assertive"></section>
```

Bu kod ekran oxuyucularını yenilənmiş kontenti oxumağa vadar edəcək. Burada nəzər yetirməli olduğumuz daha bir məsələ odur ki, ekran oxuyucusu sadəcə yenilənmiş kontenti oxuyacaq. Daha yaxşı olardı ki, istifadəçiyə nəyin yeniləndiyini yada salmaq üçün başlıq da səsli olaraq oxunsun. Bunu təmin etmək üçün `aria-atomic` atributundan istfadə edəcəyik:

```html
<section aria-live="assertive" aria-atomic="true"></section>
```

Tamamlanmış nümunəyə baxmaq üçün [aria-live.html](https://github.com/mdn/learning-area/blob/master/accessibility/aria/aria-live.html) ([canlı bax](https://mdn.github.io/learning-area/accessibility/aria/aria-live.html)) faylına baxın.

## Klaviatura müyəssərliyini artırmaq

Daha əvvəl də qeyd etdiyimiz kimi, HTML-in güclü cəhətlərindən biri də button, link, form elementləri və s. interaktiv elementlərin defolt olaraq keyboard accessible olmasıdır. Yəni ki, siz Tab düyməsi vasitəsilə həmin kontrolların üzərində gəzişə və Enter/Return düyməsi ilə onları aktiv edə bilərsiniz. Digər elementləri isə başqa düymələrlə idarə etmək imkanınız olacaq (misalçün, `<select>` elementinin variantlarını arasında aşağı və yuxarı düymələri vasitəsilə seçə bilərsiniz).

Lakin bəzi hallarda semantik olmayan kod yazmaq məcburiyyətində qaldığınızda bu kimi xüsusiyyətləri itirmiş olacaqsınız. Buna misal olaraq sizə verilən kodun pis yazılması və ya mürəkkəb kontrollar yazmağı misal göstərmək olar.

Klaviatura vasitəsilə fokus oluna bilməyən elementlərə fokuslanmaq qabiliyyəti verə bilməyiniz üçün WAI-ARIA `tabindex` atributuna yeni dəyərlər əlavə etmişdir:

- `tabindex="0"` klaviatura ilə idarə oluna bilməyən - interaktiv olmayan elementlərin interaktiv olunmasını təmin edir. Bu `tabindex`-in ən çox istifadə olunan dəyərlədindəndir.
- `tabindex="-1"` dəyəri interaktiv olmayan elementlərin kod vasitəsilə (misalçün JavaScript ilə) fokus oluna bilməsini təmin edir.

Bununla bağlı [Klaviatura müyəssərliyini geri qazanmaq](/html-ve-muyesserlik/yaxshi-semantika?id=klaviatura-m%c3%bcy%c9%99ss%c9%99rliyini-geri-qazanmaq) məqaləsində daha ətraflı danışmışdıq.

## Semantik olmayan kontrolların müyəssərliyi

Əvvəlcə də qeyd etdiyimiz kim, iç-içə yazılmış çoxlu sayda `<div>` elementindən ibarət olan, CSS/JavaScript ilə düzəldilən və funksionallığı JavaScriptə əsaslanan widgetləri tək ekran oxuyucularının başa düşməsi çətin olmur, həm də klaviatura istifadəçiləri bu tip kontrolları istifadə etməkdə çətinlik çəkirlər. Bu cür qəliz, mürəkkəb UI kontrollarının müyəssərliyini artırmaq üçün ARIA bizə elementlərdə çatışmayan semantikanı bərpa etmək imkanı verir.

## Form validation və xəta bildirişləri

Əvvəlcə gəlin JavaScrip və CSS müyəssərliyi məqaləsində baxdığımız nümunəyə bir daha nəzər yetirək. Məqalənin sonunda xəta mesajlarını göstərən qutuya bəzi ARIA atributlarını əlavə etdiyimizi demişdik:

```html
<div class="errors" role="alert" aria-relevant="all">
  <ul></ul>
</div>
```

- `role="alert"` qeyd edilən hissəni avtomatik olaraq canlı sahəyə (live region) çeviri və bu sahədə olan dəyişikliklər ekran oxuyucusu tərəfindən səsli oxunur. Bu həm də semantik olaraq sözügedən elementin bildiriş mesajı daşıdığına və önəmli məlumat ehtiva etdiyinə işarə edir.

- `aria-relevant="all"` isə ekran oxuyucusunu mesajlar əlavə edildiyində və silindiyində onları oxumağa vadar edir. Bu istifadəçilər üçün yararlıdır çünki istifadəçilər hansı xətaların həll olunduğunu və hansıların qaldığını bilmək istəyəcəklər.

Biz əlavə olaraq digər ARIA atributlarından istifadə edərək formun müyəssərliyinə daha da köməklik götərə bilərik. Misalçün, hansı sahələrin mütləq doldurulmalı olduğunu və yaş aralığını təyin edə bilərik.

1. İlkin olaraq `<form>` elementinin üzərinə paraqraf əlavə edərək və bütün `<label>` elementlərinə ulduz (\*) işarəsi əlavə edərək hansı sahələrin doldurulmalı olduğunu işarə edək.

```html
<p>
  Ulduz işarəsilə (*) göstərilən xanaların mütləq doldurulması tələb olunur.
</p>
```

2. Vizual olaraq bu istifadəçilərə kömək etsə də ekran oxuyucuları istifadəçiləri üçün bunu başa düşmək rahat deyil. Xoşbəxtlikdən, WAI-ARIA-nın `aria-required` atributu ekran oxuyucularına bu maddə ilə bağlı ipucları vermək üçün yararlıdır. `<input>` elementlərini aşağıdakı kimi dəyişə bilərik:

```html
<input type="text" name="name" id="name" aria-required="true" />

<input type="number" name="age" id="age" aria-required="true" />
```

3. Həmçinin vizual olaraq problemi olmayan istifadəçilərə o cümlədən ekran oxuyucusu işlədən istifadəçilərə yaş xanasının hansı dəyərlər üçün nəzərdə tutulduğunu göstərə bilərik. Bu adətən hansısa tooltip vasitəsilə və ya `placeholder` əlavə etməklə həll olunur. WAI-ARIA bu kimi məqsədlər üçün `aria-valuemin` və `aria-valuemax` kimi spesifik atributlar təklif edir lakin təəssüflər olsun ki, bu atributlar üçün brauzer dəstəyi elə də ürəkaçan deyil. Bu hal üçün istifadə edəcəyimiz ən yaxşı və sadə üsul `input` elementinə `placeholder` əlavə etməkdir:

```html
<input
  type="number"
  name="age"
  id="age"
  placeholder="Enter 1 to 150"
  aria-required="true"
/>
```

Tamamlanmış nümunəyə baxmaq üçün [form-validation-updated.html](https://mdn.github.io/learning-area/accessibility/aria/form-validation-updated.html) faylına baxın.

WAI-ARIA həmçinin klassik `<label>` elementindən əlavə etiketləmənin digər üsullarını da təklif edir. Bunlardan bəzilərinə daha əvvəl nəzər yetirmişdik. Etiketləmə texnikaları kimi siz `aria-label` (form `<label>`-inin əvəzinə), `aria-labelledby` və `aria-describedby` kimi atributlardan istifadə edə bilərsiniz. Bu üsullar sizə klassik etiketləmədən daha çox imkanlar yaradacaqdır. Daha ətraflı məlumat üçün WebAIM-in [Advanced Form Labelling məqaləsi](https://webaim.org/techniques/forms/advanced)nə baxın.

Bundan başqa elementlərin statuslarını (hallarını) göstərmək üçün də çoxlu sayda ARIA atributları mövcuddur. Milsaçün, `aria-disabled="true"` atributunu form elementinin bloklandığını göstərmək üçün istifadə edə bilərsiniz. Əksər brauzerlər `disabled` attributunun üzədindən keçir və ekran oxuyucularına belə bir form elementinin olmasından xəbər vermirlər. Bu səbəbdən ARIA attributları ilə form elementinin orada olduğunu lakin bloklandığını ekran oxuyucularına bildirmək daha yaxşı fikirdir.

Əgər bloklanmış form elementinin halı dəyişəcəksə, bunun nə vaxt baş verdiyini qeyd etmək və nəticənin nə olduğunu bildirmək yaxşı fikirdir. Misalçün, [form-validation-checkbox-disabled.html](https://mdn.github.io/learning-area/accessibility/aria/form-validation-checkbox-disabled.html) nümunəsinə baxın, burada bir checkbox mövcuddur. Həmin checkbox check olunduğunda daha bloklanmış form elementi yenidən aktiv olur və istifadəçidən daha çox məlumat qeyd etməsi tələb olunur. Həmçinin bu halın dəyişdiyini ekran oxuyucularına göstərmək üçün `absolute` positioning vasitəsilə vizual olaraq gizlədilmiş live region əlavə edilmişdir:

```html
<p class="hidden-alert" aria-live="assertive"></p>
```

Checkbox check/uncheck olunduqda ekran oxuyucularını məlumatlandırmaq üçün həmin live regionun içərisində bu barədə məlumat qeyd edilir və form elementinin `aria-disabled` atributunun dəyəri dəyişdirilir:

```javascript
function toggleMusician(bool) {
  let instruItem = formItems[formItems.length - 1];
  if (bool) {
    instruItem.input.disabled = false;
    instruItem.label.style.color = '#000';
    instruItem.input.setAttribute('aria-disabled', 'false');
    hiddenAlert.textContent =
      'Instruments played field now enabled; use it to tell us what you play.';
  } else {
    instruItem.input.disabled = true;
    instruItem.label.style.color = '#999';
    instruItem.input.setAttribute('aria-disabled', 'true');
    instruItem.input.removeAttribute('aria-label');
    hiddenAlert.textContent = 'Instruments played field now disabled.';
  }
}
```
