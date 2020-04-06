# CSS

CSS və JavaScript accessibility mövzusunda HTML qədər mühüm olmasa da, düzgün istifadə olunmadıqda müyəssərliyə zərər yetirə bilər. Gəlin əvvəlcə CSS-ə baxmaqla başlayaq.

## Düzgün semantika və istifadəçinin gözləntiləri

CSS vasitəsilə istədiyiniz HTML elementini istədiyiniz cür göstərə bilərsiniz. Lakin daha əvvəl də qeyd etdiyimiz kimi, düzgün HTML elementlərini düzgün iş üçün seçmək vacib məsələdir. Bunu etməsəniz əksər istifadəçilər üçün, ələlxüsus da əlilliyi olan istifadəçiləriniz üçün qarışıqlıq yaratmış olacaqsınız. Düzgün semantikan istifadə etməyin istifadəçi gözləntisi ilə çox bağlılığı var - elementlər müəyyən şəkildə görünür və funksionallıq baxımından müəyyən cür davranışları var, bu görüntü və davranışlar istifadəçi gözləntisinin bir parçasıdır.

Misalçün, əgər proqramçı səgifədəki başlıqlar üçün düzgün HTML elementlərindən istifadə etməyibsə, ekran oxuyucuları başlıqlar vasitəsilə səhifədə naviqasiya edə bilməyəcəklər. Eyni səbəbdən, proqramçı əgər başlığa CSS vasitəsilə qəribə görünüş verirsə, həmin başlıq vizual olaraq başlıq vəzifəsini itirmiş olur.

Yaxşı qayda odur ki, səhifədəki hər hansı bir elementi öz dizaynınıza uyğunlaşdırmaq üçün dəyişə bilərsiniz, lakin bir elementi vizual olaraq öz məqsədini itirəcək qədər dəyişməyiniz tövsiyyə olunmur.

## Standart text kontent strukturu

Başlıqlar, paraqraflar və siyahılar səhifənizin əsas text məzmununu təşkil edir:

```html
<h1>Başlıq</h1>

<p>Paraqraf</p>

<ul>
  <li>Mənim siyahımın</li>
  <li>iki elementi var.</li>
</ul>
```

Buna uyğun səciyyəvi CSS isə aşağıdakı kimi ola bilər:

```css
h1 {
  font-size: 5rem;
}

p,
li {
  line-height: 1.5;
  font-size: 1.6rem;
}
```

Səhifənizi dizayn edərkən, siz:

- Səhifənizdəki mətnin aydın, məntiqli və rahat oxuna bilən olması üçün `font-size`, `line-height`, `letter-spacing` və s. parametrləri düzgün istifadə etməlisiniz.
- Səhifənizdəki başlıqların digər məzmundan seçildiyinə əmin olun. Başlıqlar öz defolt görünüşlərində olduğu kimi səciyyəvi qara və qalın text formasında olmalıdır.
- Səhifənizdəki bütün text məzmunu arxa fon ilə yaxşı təzad (kontrast) təşkil etməlidir.

### Vurğulanmış mətn

Siz inline `<em>` və `<strong>` markapından istifadə etməklə textin istənilən hissəsini xüsusi vurğulaya bilərsiniz:

```html
<p>The water is <em>very hot</em>.</p>

<p>
  Water droplets collecting on surfaces is called <strong>condensation</strong>.
</p>
```

Vurğulanmış mətninizə yüngülcə rəng verə bilərsiniz:

```css
strong,
em {
  color: #a60000;
}
```

Normal şərlər altında vurğulanmış mətnin stilini dəyişməyə ehtiyacınız olmayacaq. Qalın və italik text hər kəs tərəfindən tanınır, bu stili dəyişməyiniz qarışıqlığa səbəb ola bilər.

### Abreviaturalar

Abreviaturaları, akronimləri və onların açılışını yazmaq üçün `<abbr>` elementindən istifadə edin:

```html
<p>
  Web kontent <abbr title="Hypertext Markup Language">HTML</abbr> vasitəsilə
  yazılır.
</p>
```

Yenə də, bu cür mətnə istədiyiniz kimi stil verə bilərsiniz:

```css
abbr {
  color: #a60000;
}
```

Abreviaturalar üçün tanınmış stil textin altından qırıq-qırıq xəttin çəkilməsidir, bundan başqa bir stil tətbiq eləmək tövsiyyə olunmur.

### Keçidlər

Keçidlər web səhifədə başqa yerlərə keçməyinizə kömək edir:

```html
<p>
  <a href="https://www.mozilla.org">Mozillanın əsas səhifəsi</a>nə baş çəkin.
</p>
```

Keçidləri stilləşdirmək üçün CSS nümunəsi aşağıdak kimi ola bilər:

```css
a {
  color: #ff0000;
}

a:hover,
a:visited,
a:focus {
  color: #a60000;
  text-decoration: none;
}

a:active {
  color: #000000;
  background-color: #a60000;
}
```

Linklərin standart görünüşü textin altından xətt çəkilməsi və defolt halında başqa rəngdə olmasıdır (defolt göy rəng). Baş çəkilmiş və aktiv olunmuş linklərin rəngləri isə standart haldan fərqli rəngə olmalıdır. Əlavə olaraq, hər hansı bir keçidin üzərinə gəldiyinizdə kursor dəyişməli və Tab düyməsilə linkin üzərinə fokuslandığınızda, həmin link xüsusi stillə vurğulanmalıdır. Aşağıdakı nümunədə, Firefox (altdan qırıq-qırıq xətt ilə) və Chromeda (mavi outline ilə) üzərinə fokuslanmış keçidləri görə bilərsiniz:

![firefox focused link](https://media.prod.mdn.mozit.cloud/attachments/2016/11/15/14371/7c7319592c97a737e8e3d196c26ef7f1/focus-highlight-firefox.png)
![chrome focused link](https://media.prod.mdn.mozit.cloud/attachments/2016/11/15/14369/9a347196b6a3c5789fb9736e1cda9e99/focus-highlight-chrome.png)

Keçidləri dizayn edərkən öz kreativliyinizdən istifadə edə bilərsiniz, sadəcə olaraq istifadəçilərin onlar ilə qarşılıqlı əlaqədə olduğu zaman yetərli feedback aldıqlarından əmin olun. Keçidin halı dəyişdiyində, fokuslandığında və kursoru üzərinə gətirdiyinizdə mütləq nəsə baş verməlidir (misalçün rəngi dəyişməli, kursor dəyişməli, kənarında outline əmələ gəlməli və s.). Bunlar klaviatura istifadəçiləri üçün önəmli parametrlərdir.

### Form elementləri

Form elementləri istifadəçilərin sizin səhifənizə məlumat daxil etməsinə kömək edir:

```html
<div>
  <label for="name">Adınızı daxil edin</label>
  <input type="text" id="name" name="name" />
</div>
```

Form elementlərinin CSS vasitəsilə stilləşdirilməsinin yaxşı nümunəsi ilə [form-css.html](https://github.com/mdn/learning-area/blob/master/accessibility/css/form-css.html) faylında tanış ola bilərsiniz (həmçinin [canlı nümunəyə baxın](https://mdn.github.io/learning-area/accessibility/css/form-css.html)).

Form elementlərinə stil verərkən, işinizin əksər hissəsi ölçüləri dəyişmək, label və inputları bir sıraya düzmək və onların səliqəli göründüyündən əmin olmaq olacaq.

Lakin bu stilləri verərkən istifadəçi form elementlərinə fokuslandığında və s. vaxtlarda gözlənilən feedbackdən çox kənara çıxmayın. Focus/hover hallarınə bir cür stil verməklə və ya dizaynınıza uyğun şəkildə dəyişməklə bütün bruzerlərdə eyni olan dizayn əladə edə bilərsiniz - yenə də qeyd edirik ki, əksər insanlar bu cür kiçik görünən parameterlərdən asılı vəziyyətdədirlər.

### Cədvəllər

Cədvəllər vasitəsilə müxtəlif məlumatları səhifənizdə görüntüləyə bilərsiniz.

[table-css.html](https://github.com/mdn/learning-area/blob/master/accessibility/css/table-css.html) faylına baxaraq cədvəl HTML və CSS kodlarının yaxşı nümunəsilə tanış ola bilərsiniz (həmçinin [canlı nümunəyə baxın](https://mdn.github.io/learning-area/accessibility/css/table-css.html)).

Cədvləllərin stilini çox vaxt öz dizayınıza uğunlaşdırmaq və ya cədvli daha az çirkin göstərmək üçün dəyişəcəksiniz. Bu stilləri verərkən, cədvəlin başlığını digər sətirlərdən fərqləndirmək və digər sətirləri zebra tərzi zolaqlamaq tövsiyyə olunur.

### Rəng və rəng kontrastı

Saytınız üçün rəng sxemi seçərkən mətnin rənginin və arxa fon rəngnini bir-birilə ziddiyət təşkil etdiyindən əmin olun (başqa sözlə desək rəng kontrastına fikir verin). Dizaynınız qəşəng görünə bilər lakin rəng korluğu kimi görmə problemi olan insanlar üçün saytınızın məzmununu oxumaq çətin olacaq.

Saytınızdakı rəng kontrastını yoxlamaq çox asandır - bunun üçün internetdə çoxlu sayda alətlər tapa bilərsiniz. Bu alətlərə nümunə olaraq, WebAIM tərəfindən hazırlanmış [Color Contrast Checker](https://webaim.org/resources/contrastchecker/)ə baxa bilərsiniz. Bu istifasi asan olan bir alətdir və sizə WCAG kriteriyalarına uyğunlaşmaq üçün nələr etməli olduğunuzu da izah edəcək.

> **Qeyd:** Yaxşı seçilmiş rəng kontrastı gün işiğında parlaq ekranlı planşet və ya telefon işlədən istifadəçiləriniz üçün çox yararlı olacaq.

Daha bir tövsiyyəmiz odur ki, işarələri və xüsusi məlumatları vurğulamaq üçün rənglərə çox da güvənməyin. Rəng korluğu olan insanlar üçün bunun heç bir əhəmiyyəti olmayacaq. Misalçün, form xanasının mütləq doldurulmalı olduğunu işarə etmək üçün tək qırmızı rəngdən deyil, qırmışı rənglənmiş ulduz işarəsindən istifadə edə bilərsiniz.

### Elementləri gizlətmək

Bəzən ela hallar yaranır ki, dizayna görə bəzi kontentləri gizlədib digərlərini göstərməli oluruq. Misalçün, [bizim tab nümunəsi](https://mdn.github.io/learning-area/css/css-layout/practical-positioning-examples/info-box.html) ([mənbə kodu](https://github.com/mdn/learning-area/blob/master/css/css-layout/practical-positioning-examples/info-box.html)na baxın) bu hallardan biridir. Sözügedən nümunədə bizim 3 panelimiz var və piz [CSS positioning](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Positioning)dən istifadə edərək panelləri bir-birinin üzərində yerləşdirmişik. Fikir verin ki, tablar həm də klavişlə rahat idarə oluna bilir.

![tabs example](https://media.prod.mdn.mozit.cloud/attachments/2016/05/23/13368/1481309f8899f071fba559e9c807e49e/tabbed-info-box.png)

Ekran oxuycusu işlədən istifadəçiləri bütün bunlar maraqlandırmır - koddakı ardıcıllıq düzgün olduğu və bütün məzmunu oxuya bildikləri halda onlar xoşbəxtdirlər. "Abosolute positioning" vizual olaraq elementləri gizlətmək və göstərmək üçün ən yaxşı üsullardan biri hesab olunur çünki bu halda ekran oxuyucuları bütün məzmunu görə bilirlər.

Digər tərəfdən, `visibility: hidden` və `display: none` kimi CSS deklarasiyalarından istifadə etmək tövsiyyə olunmur - onlar kontenti ekran oxuycularından gizlədirlər. Əgər hansısa kontenti ekran oxuyucularının görməsini istəmirsinizsə, bu başqa məsələ.

> **Qeyd:** [Invisible Content Just for Screen Reader Users](https://webaim.org/techniques/css/invisiblecontent/) məqaləsinda bu barədə ətraflı müzəkirələr aparılır.

### İstifadəçilərin sizi stilləri dəyişəcəyini qəbul edin

İstifadəçilərin sizin saytınızdakı stilləri dəyişdirəcəyi halını da nəzərdə tutun. İstifadəçilər bunu müxtəlif səbəblərdən edə bilərlər. Gözü yaxşı görməyən istifadəçi bütün saytdakı font ölçüsünü böyüdə, rəng koruluğu olan isitfadəçi isə saytdakı rəngləri dəyişərək kontrastı özləri istəyən kimi düz-qoş edə bilər. Səbəbi nə olur olsun, bu cür dəyişiklərə hazır olmalı və saytınızın dizaynını elə qurmalısınız ki, bu cür dəyişikliklər rahat edilə bilsin. Misalçün, saytınızın əsas hissəsinin böyük ölçülü text ilə rahat yola getməsini təmin edin - font ölçüsü böydüyündə saytınız mətni gizlədə və ya tamamilə pis vəziyyətə sala bilər.
