# WAI-ARIA nədir?

Bəzən biz mürəkkəb UI kontrolları düzəltmək üçün semantik olmayan HTML yazmalı və JavaScript ilə daim istifadəçi interfeysini yeniləməli oluruq. WAI-ARIA bu cür problemləri həll etmək üçün HTML kontentə brauzer və assistiv texnologiyalar üçün yararlı olacaq əlavə semantika əlavə edərək müyəssərliyi artırmağımıza kömək edən texnologiyadır. Bu məqalədə WAI-ARIA-nın bəsit isitfadə qaydalarına və müyəssərliyi artırmaq üçün ondan necə istifadə edəcəyimizə baxacağıq.

## Yaranan yeni növ problemlər

Web tətbiqlər getdikcə daha mürəkkəb və dinamik olduqca, yeni-yeni müyəssərlik problemləri üzə çıxmağa başlamışdır.

Misalçün, HTML5 web səhifənin müxtəlif hissələrini təsvir etmək üçün çoxlu sayda semantik elementlər (`<nav>`, `<footer>` və s.) təqdim etmişdir. Bundan əvvəl developerlər, `<div>` elementlərindən istifadə edir və həmin elementlərə class və ID-lər əlavə etməklə həmin `div`in səhifənin hansı hissəsini təsvir etdiyini göstərirdilər (`<div class="nav">` kimi). Lakin bu problemli yanaşma idi çünki proqramlı şəkildə səhifənin hansısa hissəsini (misalçün, əsas naviqasiyanı) tapmaq asan olmurdu.

İlkin həllər onda ibarət idi ki, proqramçılar səhifənin başlığına səhifənin bəzi önəmli yerlərini işarə edən gizlədilmiş keçidlər əlavə edirdilər:

```html
<a href="#hidden" class="hidden">Skip to navigation</a>
```

Lakin bu tam dəqiq yanaşma deyil və ancaq ekran oxuyucuları səhifənin ən başından oxumağa başlasa yararlı ola bilər.

Daha bir nümunə isə datepicker, slider və s. bunun kimi mürəkkəb IU kontrollarıdır ki, HTML5 bunlar üçün də sadə input `type`ları təqdim etmişdir:

```html
<input type="date" name="date" placeholder="Tarixi seçin" />
<input type="range" name="rating" placeholder="Qiymətləndirmənizi seçin" />
```

Bu cür inputlar bütün brauzerlər tərəfindən tam dəstəklənmir və dizayn olunması olduqca çətindir, bu səbəbdən də websaytların dizaynlarına inteqrasiya etmək çətindir. Bunun nəticəsi olaraq, developerlər bu cür kontrolları generasiya etmək üçün çox vaxt CSS ilə style olunmuş iç-içə `div`-lərdən və `table`-lardan ibarət JavaScript kitabxanalarından istifadə edirlər.

Burada problem odur ki, bu cür mürəkkəb UI kontrlları vizual olaraq mənalı olsa da, ekran oxuyucuları onlarla rastlaşdıqda bir dəstə iç-içə yığılmış mənasız kontentdən başqa heç nə başa düşmür.

## WAI-ARIA-ya giriş

[WAI-ARIA](https://www.w3.org/TR/wai-aria-1.1/) (Web Accessibility Initiative - Accessible Rich Internet Applications) World Wide Web Consortium (W3C) tərəfindən yazılmış, HTML elementlərinə müyəssərliyi artırmaq üçün əlavə semantikə yükləyən atributlar yığınıdır. Spesifikasiyada qeyd olunmuş üç əsas sahə var:

- **Rollar** - elementin nə olduğunu və nə etdiyini təyin edir. Bunların əksəriyyəti HTML5-in strukturu təyin edən semantik elementləri ilə üst-üstə düşür; misalçün, `role="navigation"` (`<nav>`) və ya `role="complementary"` (`<aside>`). Digərləri isə səhifənin müxtəlif yerlərini təsvir etmək üçündür: `role="banner"`, `role="search"`, `role="tabgroup"`, `role="tab"` və s.

- **Xassələr** - elementlərin əlavə məna və semantika əlavə edən müxtəlif xassələrini təyin edir. Misalçün, `aria-required="true"` form elementinin mütləq doldurulmalı olduğunu, `aria-labelledby="label"` isə sözügedən elementin işarələnmiş (`label`) ID-li element tərəfindən təsvir olunduğunu təyin edir.

- **Hallar** - elementlərin xüsusi hallarını təyin edən atributlardır. Misalçün, `aria-disabled="true"` ekran oxuyucusunu sözügedən form elementinin bloklandığından xəbərdar edir. Bu hallar əksər vaxtlarda JavaScript vasitəsilə yenilənir.

Onu da qeyd edək ki, WAI-ARIA brauzerlərin accessibility API-larına əlavə məlumat ifşa etməsindən savayı saytınızla bağlı heç nəyi dəyişmir. WAI-ARIA saytınızın strukturuna, DOM-a və s. heç bir təsir göstərmir, bəzi hallarda CSS selektorları kimi işinə yaraya bilər.

## WAI-ARIA harada dəstəklənir?

Bu suala cavab vermək asan məsələ deyil. WAI-ARIA-nın hansı xüsusiyyətlərinin harada dəstəkləndiyini göstərən qəti bir resurs resurs yoxdu, çünki:

- WAI-ARIA  spesifikasiyalarında yuxarıda sadaladığımız bəziləri kimi çoxlu sayda xüsusiyyətlər var.
- Çoxlu sayda mməliyyat sistemi, brauzer və ekran oxuyucusu kombinasiyaları mövcuddur.

Axırıncı punk əsas məsələdir - ekran oxuyucusunu işlədə bilmək üçün ilk öncə əməliyyat sistemi ekran oxuyucusunun öz işini görə bilməsi üçün müəyyən accessibility API-ları olan brauzer işlətməlidir. Əksər əməliyyat sistemlərinin ekran oxuyucularının işləyə biləcəyi bir və ya iki brauzeri var.

Daha sonra brauzerinizin ARIA funksionallıqlarını dəstəklədiyindən və həmin funksionallıqların accessibility API vasitəsilə ifşa olunduğundan əmin olmaq lazımdır. Və əlbəttə ki, ekran oxuyucusu da öz növbəsində bu məlumatı oxuya və istifadəçiyə çatdıra bilməlidir.

1. Brauzer dəstəyi ümumi baxışda pis deyil - [caniuse.com](https://caniuse.com/#feat=wai-aria)-un verdiyi hesabatına görə brauzerlər arasında qlobal WAI-ARIA dəstəyi 96%-dir.
2. Ekran oxuyucularının dəstəyi isə hələ ki, bu səviyyəyə çatmamışdır lakin əksər ekran oxuycuları bu nəticəyə yaxınlaşmaq üzrədir. [WAI-ARIA Screen reader compatibility](https://www.powermapper.com/tests/screen-readers/aria/) məqaləsinə baxaraq ekran oxuyucularının WAI-ARIA dəstəyi ilə tanış ola bilərsiniz.

Bu məqalədə, WAI-ARIA-nın bütün xüsusiyyətlərindən danışmayacağıq, əvəzində ən çox istifadə olunan və lazımlı xassələri sizinlə paylaşacağıq. Brauzer və ekran oxuyucus dətəyini isə ona görə qeyd etdik ki, bu funksionallıqların tam olaraq dəstəklənmədiyindən məlumatınız olsun.

> **Qeyd:** Bəzi JavaScript kitabxanaları mürəkkəb UI kontrollarını generasiya edərkən WAI-ARIA dəstəyini əsirgəməmiş və komponentlərin müyəssərliyini artırmışlar. Əgər "3rd party" UI komponentləri axtarırsınızsa, WAI-ARIA-nı dəstəkləyən kitabxanaları seçməyinizi tövsiyyə edirik. Bunlara nümunə kimi [jQuery UI](https://jqueryui.com/about/#deep-accessibility-support), [ExtJs](https://www.sencha.com/products/extjs/) və [Dojo/Dijit](https://dojotoolkit.org/reference-guide/1.10/dijit/a11y/statement.html)i misal göstərmək olar.

## WAI-ARIA-nı nə vaxt istifadə etməli?

WAI-ARIA-nın yaranmasına səbəb olan problemləri daha öncə qeyd etdik. İndi isə gəlin WAI-ARIA-nın dörd əsas istifadə sahələrinə baxaq:

1. **İşarə/Əlamət** - `role` atributu həm HTML5-in semantik elementlərini əvəz edə həm də HTML5-də olmayan lakin əksər saytlarda mövcud olan bəzi komponentlərə (`search`, `tabgroup`, `tab`, `listbox`) semantika əlavə etməyə kömək edir.
2. **Məzmunun dinamik yenilənməsi** - Ekran oxuyucuları tez-tez dəyişən dinamik məzmunu oxumaqda çətinlik çəkir. ARIA-nın `aria-live` atributu vasitəsilə ekran oxuyucularını [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) və ya [DOM API](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)-ləri vasitəsilə yenilənən məzmun barədə xəbərdar etmək olar.
3. **Klaviatura müyəssərliyini artırmaq** - Defolt olaraq keyboard accessible HTML elementləri (`a`, `button` və s.) mövcud olmasına baxmayaraq bəzi developerlər digər elementləri JavaScript ilə birləşdirərək eyni funksionallığı yaratmağa çalışırlar. Bunun nəticəsində isə ekran oxuyucuları və klaviatura müyəssərliyi əziyyət çəkir. Bu hal qaçınılmaz olduqda WAI-ARIA bu cür elementlərin fokus almasını təmin etmək üçün `tabindex` atributunu təqdim etmişdir.
4. **Semantik olmayan kontrolların müyəssərliyi** - Mürəkkəb IU komponentləri onlarla iç-içə yazılmış `div`-lərdən ibarət olduqda və tamamilə JavaScript ilə idarə olunduqda müyəssərlik zərər görə bilər - ekran oxuycuları bu cür markapın nə işə yaradığını anlamaqda çətinlik çəkə bilər və klaviatura istifadəçilər bu komponentləri istifadə edə bilməz. Bu hallarda, ARIA assistiv texnologiyalara `button`, `listbox`, `tabgroup` kimi rollarla və `aria-required`, `aria-posinset` kimi atributlarla funksionallığa dair ipucları verə bilər.

Yadda saxlamalı olduğunuz bir şey odur ki, **WAI-ARIA-nı ancaq və ancaq lazım olduğunda istifadə etməlisiniz!**. Normal olaraq həmişə native HTML elementlərindən istifadə etməli, yalnız məcbur qaldığınız hallarda mürəkkəb komponentlər hazırladığınızda və s. hallarda ARIA atributlarından istifadə etməlisiniz.
