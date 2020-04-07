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
