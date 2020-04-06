# JavaScript

JavaScript də istifadə olunmasından asılı olaraq müyəssərliyə zərər yetirə bilər.

Müasir JavaScript güclü bir dildir və onu UI yeniləmələrindən tutmuş, 2D və 3D oyunların hazırlanmasına qədər istənilən yerdə istifadə edə bilərik. Bütün məzmunun 100% bütün insanlar üçün müyəssər olmasını tələb edən heç bir qayda yoxdu - sadəcə olaraq saytlarınızı və tətbiqlərinizi əlinizdən gəldiyi qədər müyəssər etməlisiniz.

Mətn, şəkil, cədvəl, formlar, düymələr kimi sadə kontentləri müyəssər etmək nisbətən asandır. HTML ilə bağlı əvvəlki məqaləmizdə də vurğuladığımız kimi bir neçə şeyi nəzərinizdə saxlamalısınız:

- Yaxşı semantika: hər iş üçün düzgün HTML elementini istifadə etmək. Misalçün, paraqraflar, başlıqlar, düymələr və keçidlər üçün düzgün HTML elementlərini istifadə etməlisiniz.
- Məzmunu mətn formasında təqdim etmək: form elementləri üçün yaxşı mətn etiketlərindən istifadə etmək, şəkillər və digər multimedia üçün alternativ mətn yazmaq və s.

Biz həmçinin JavaScripti istifadə etməklə klaviatura müyəssərliyini yenidən qurmağı da öyrəndik. Lakin bu ideal deyil - siz hər bir HTML elementini öz nəzərdə tutulmuş məqsədi üçün işlətməlisiniz. Bəzi hallarda isə HTML ilə bunu edə bilmədiyiniz zamanlarda JavaScript sizin köməyinizə çata bilər. Müyəssərliyi artırmağın digər yolu isə WAI-ARIA-dan istifadə edərək saytınızın JavaScriptə əsaslananr hissələrini (misalçün datepicker komponenti) ekran oxuyucuları üçün müyəssər etməkdir.

3D oyunlar kimi mürəkkəb funksionallığı müyəssər etmək isə asan iş deyil - [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) vasitəsilə yaradılmış oyun hansısa mətn alternativi ilə görmə pozğunluğu olan insanlara çatdıra bilməyəcəyimiz `<canvas>` elementi üzərində render olunur. Bu cür oyunların auditoriyasının isə kor insanlar olduğunu düşünmək heç də məntiqli deyil, edə biləcəyiniz ən yaxşı şey klaviatura müyəssərliyini artırmaqla maus işlətməyən istifadəçilərə və ya düzgün rəng sexmi seçməklə rəng korluğu problemi olan insanlara yardım etməyinizdir.

## Həddindən artıq çox JavaScript ilə bağlı problemlər

Problem o vaxt yaranır ki, insanlar JavaSciptə çox etibar edirlər. Çox vaxt elə saytlarla rastlaşırıq ki, orada hər şey JavaScript ilə işləyir - HTML JavaScript ilə generasiya olunur, CSS JavaScript ilə generasiya olunur və s. Bu üsulun çoxlu sayda müyəssərlik və digər problemləri olduğu üçün tövsiyyə edilmir.

Düzgün HTML elementlərini düzgün məqsədlər üçün istifadə etməli olduğunuz kimi, düzgün işlər üçün də düzgün texnologiyalardan istifadə etməlisiniz. Saytınıza qoyduğunuz 3D məlumat qutusuna həqiqətən ehtiyacınızın olub olmadığını bir də düşünün, bəlkə bunu adi mətn ilə edə bilərsiniz? Və ya yaxşı görünən və standart olmayan form komponenti həqiqətən sizə lazımdırmı? Bəlkə elə adi text input sizin işinizi görəcək. Və son olaraq, mümkünsə saytınızın bütün HTML kontentini JavaScript ilə generasiya etməyin.

## JavaScripti gözə çarpmayan etmək

JavaScripti əlinizdən gəldiyi qədər gözə çarpmaz dərəcədə istifadə edin. Bu o deməkdir ki, JavaScript sadəcə mövcud funksionallığı artırmaq üçün istifadə edilməlidir, onu bütünlüklə yaratmaq üçün yox. Bəsit funksionallıq JavaScript olmadan da işləməlidir. Bunun həmişə mümkün olmadığını başa düşürük, lakin nəzərinizdə saxlamağınız hamı üçün xeyirlidir.

Buna misal olaraq aşağıdakı halları göstərmək olar:

- Saytınızdakı formlara client-side doğrulama (validation) mexanizmi əlavə edə bilərsiniz. Bu doğrulama mexanizmi, istifadəçi səhv etdiyində bildirişlər və digər köməkçi informasiyalar vasitəsilə istifadəçiyə yardımçı olmalıdır. Bu halda, əgər JavaScript olmasa form əvvəlki funksionallığını da qoruyub saxlayacaq, təbii ki, server-side doğrulama mexanizminizin də olduğunu fərz edirik.

- HTML5 `<video>` elementi üçün klaviatura müyəssərliyi olan (keyboard accessible) custom kontrollar düzəldə bilərsiniz. Defolt olaraq əksər brauzerlərin `<video>` elementi üçün təqdim etdiyi kontrollar klaviatura ilə idarə edilə bilmir.

Nümunə üçün tez-bazar hazırlanmış client-side form validationu sizə göstərə bilərik, kodlara baxmaq üçün [form-validation.html](https://github.com/mdn/learning-area/blob/master/accessibility/css/form-validation.html) faylını açın (və ya [canlı nümunə](https://mdn.github.io/learning-area/accessibility/css/form-validation.html)yə baxın). Burada form elementlərindən hər hansı birini boş buraxsanız, form məlumatları serverə göndərilməyəcək və sizə xəta mesajları göstəriləcək.

JavaScriptin bu cür tətbiqi gözəçarpmazdır - JavaScript bloklandığında siz formu eyni formada doldurmağa və istifadə etməyə davam edə bilərsiniz. Əlbəttə ki, istənilən formda server-side validation prosesi də olmalıdır çünki bu cür client-side validation istifadəçilər tərəfindən asanlıqla yan keçilə bilər. Buna baxmayaraq, uzun çəkən server-side validation proseslərindən fərqli olaraq client-side validation istifadəçiləri məlumatlandırmaq və formlarınızın istifadəsini rahat etmək üçün çox yararlı üsuldur.

Bu form həm də kifayət qədər müyəssərdir. Formda ekran oxuyucularının işini asanlaşdırmaq üçün `<label>` elementlərindən istifadə olunumş və müvafiq inputlarla əlaqələndirilmişdir.

```html
<label for="name">Enter your name:</label>
<input type="text" name="name" id="name" />
```

Form ancaq submit olunduqda doğrulama prosesi başlayır - bu yolla lazımsız IU yeniləmələri ilə ekran oxuyucularını çaşdırmırıq:

```javascript
form.onsubmit = validate;

function validate(e) {
  errorList.innerHTML = '';
  for (let i = 0; i < formItems.length; i++) {
    const testItem = formItems[i];
    if (testItem.input.value === '') {
      errorField.style.left = '360px';
      createLink(testItem);
    }
  }

  if (errorList.innerHTML !== '') {
    e.preventDefault();
  }
}
```

Real form validation prosesi bundan daha qəliz olur - misalçün, daxil edilmiş adın həqiqətən ada oxşayacağını yoxlamalı, yaşın ədəd olduğunu və realistik (misalçün, 2 rəqəmli və mənfi olmayan) yaş olduğunu da yoxlamalı olacaqsınız. Verdiyimiz nümunədə sadəcə olaraq inputların boş olub olmadığı yoxlanılmışdır (`if(testItem.input.value === '')`).

Doğrulama prosesi baş verdikdə, testlər müvəffəqiyyətlə tamamlandıqda form məlumatları serverə göndərilir. Əgər validation zamanı hər hansı bir xəta baş verərsə form submission dayandırılır (`preventDefault()`) və xəta mesajları istifadəçiyə göstərilir.

Dəyəri doldurulmayan hər bir input üçün içərisində link olar bir sihayı elementi düzəldilir və `errorList`-ə əlavə olunur:

```javascript
function createLink(testItem) {
  const listItem = document.createElement('li');
  const anchor = document.createElement('a');

  anchor.textContent =
    testItem.input.name +
    ' field is empty: fill in your ' +
    testItem.input.name +
    '.';
  anchor.href = '#' + testItem.input.name;
  anchor.onclick = function () {
    testItem.input.focus();
  };
  listItem.appendChild(anchor);
  errorList.appendChild(listItem);
}
```

Burada hər bir link iki məqsəd daşıyır - istifadəçiyə xətanın nə olduğunu deyir və linkin üzərinə kliklədiyinizdə xətanızı düzəltmək üçün müvafiq inputun üzərinə yönləndirilirsiniz.

Əlavə olaraq, kodlara baxsanız görərsiniz ki, `errorField` ardıcıllıq olaraq ən yuxarıda yerləşdirilmişdir. Bu o deməkdir ki, istifəçilər form ilə bağlı xətalarının nə olduğunu öyrənmək üçün səhifənin başlığına gedəcəklər.

Son olaraq onu da qeyd edək ki, səhifənin yenilənən hissələrinin yaratdığı accessibility problemlərinə həll olaraq WAI-ARIA atributlarından istifadə olunmuşdur:

```html
<div class="errors" role="alert" aria-relevant="all">
  <ul></ul>
</div>
```

> **Qeyd:** Form validation haqqında daha ətraflı [Usable and Accessible Form Validation and Error Recovery](https://webaim.org/techniques/formvalidation/) bu məqalədən öyrənə bilərsiniz.

## Maus-spesifik eventlər

Bildiyiniz kimi, JavaScript ilə düzəldilən əksər interaktiv funksionallıqlar event handlerlər vasitəsilə həyata keçirilir. Event handler - hər hansı bir event (hadisə, misalçün click eventi) baş verdikdə işə düşən funksiyadır. Bəzi eventlərin müyəssərlik mövzusundə bir sıra problemləri mövcuddur. Qarşılaşacağınız əsas nümunələr isə [mouseover](https://developer.mozilla.org/en-US/docs/Web/API/Element/mouseover_event), [mouseout](https://developer.mozilla.org/en-US/docs/Web/API/Element/mouseout_event) və [dblclick](https://developer.mozilla.org/en-US/docs/Web/API/Element/dblclick_event) kimi maus-spesifik eventlər olacaqdır. Bu eventlərə cavab olaraq işə düşən funksiyalar klaviatura düymələrinin basılması kimi başqa mexanizmlərlə işə düşməyəcək.

Bu məsələyə həll olaraq siz eyni zamanda digər mexanizmlər vasitəsilə işə düşən eventlərdən də istifadə etməlisiniz - misalçün, [focus](https://developer.mozilla.org/en-US/docs/Web/API/Element/focus_event) və [blur](https://developer.mozilla.org/en-US/docs/Web/API/Element/blur_event) eventləri klaviatura istifadəçiləri üçün müyəssərliyi təmin edəcəkdir.

Gəlin bu üsulun yararlı olacağı bir nümunəyə baxaq. Tutaq ki, siz hansısa e-commerce saytınızda balaca bir şəkil yerləşdirmisiniz və kursoru həmin şəkilin üzərinə gətirdiyinizdə və şəkil fokuslandığında həmin şəkilin böyük versiyası görünməlidir.

Bu nümunə ilə tanış olmaq üçün [mouse-and-keyboard-events.html](https://mdn.github.io/learning-area/accessibility/css/mouse-and-keyboard-events.html) səhifəsinə daxil ola bilərsiniz ([mənbə kodu](https://github.com/mdn/learning-area/blob/master/accessibility/css/mouse-and-keyboard-events.html)na baxın). Kodun içərisində yaxınlaşdırılmış şəkli göstərmək və gizlətmək üçün iki funksiya yazılmışdır və həmin funksiyalar aşağıdak kimi eventlərə bağlanmışdır:

```javascript
imgThumb.onmouseover = showImg;
imgThumb.onmouseout = hideImg;

imgThumb.onfocus = showImg;
imgThumb.onblur = hideImg;
```

İlk iki sətir kursoru şəklin üzərinə gətirdiyimizdə şəklin böyük versiyasını görünməsini, kursoru çəkdiyimizdə isə onun gizlədilməsini təmin edir. Lakin bu funksionallıq mausu olmayan istifadəçilər üçün yararlı deyil. Bu səbəbdən axırıncı iki sətirdə yazılan kod şəkil fokuslandığında (`onfocus`) böyük şəkli göstərilməsini və fokus itdiyində (`onblur`) isə böyük şəklin gizlədilməsini təmin edir. Şəklin üzərinə Tab düyməsi vasitəsilə fokuslana bilərsiniz, buna `img` elementinə `tabindex="0"` əlavə etməklə nail olmuşuq.

[click](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event) eventi isə bir az maraqlıdır - mausdan asılı olduğu görünsə də, əksər brauzerlərdə hər hansı bir linkin və ya fokuslanmış inputun üzərində Enter/Return düyməsi basıldıqda, touchscreen qurğularda ekrana toxunduqda `click` eventi aktivləşəcəkdir.
