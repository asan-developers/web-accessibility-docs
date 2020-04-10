# Web Accessibility

> İnternet informasiya ehtiyatlarının əlilliyi olan şəxslər
> üçün müyəssərliyinə dair tələblər

Web Development-də müyəssərlik (accessibility və ya a11y - "a" daha sonra 11 hərf və "y"), web saytların mümkün qədər çox istifadəçi qrupu üçün əlçatar olmasıdır. Hətta bəzi qrupların müəyyən dərəcədə əlilliyi və ya saytı istifadə etməsi üçün əngəlləri olsa belə.

Texnologiya əksər insanlar üçün çox şeyi asanlaşdırır. Müəyyən dərəcədə əlilliyi olan insanlar üçün isə bəzi mümkün olmayan şeyləri mümkün hala gətirir. Accessibility, web məzmununun elə yazılmasıdır ki, bu məzmun şəxsin fiziki və ya əqli bacarıqlarında və şəxsin web sayta hansı yolla daxil olduğundan asılı olmayaraq mümkün qədər müyəssər olmasıdır.

> Web əsaslı şəkildə insanların hardware, software, dil, məkan, mədəniyyət və fiziki və ya əqli bacarıqlarından asılı olmayaraq hər kəs üçün dizayn olunmuşdur. Nə vaxt ki, Web bu məqsədləri əhatə edir, o zaman adıçəkilən bütün qruplar üçün əlçatan olur. ([W3C Accessibility](https://www.w3.org/standards/webdesign/accessibility))

## Ümumi baxış

"Accessible" (və ya müyəssər) dedikdə o nəzərdə tutulur ki, istənilən istifadəçi texnologiyanı necə istifadə etməyindən və onun əqli və ya fiziki qüsurlarından asılı olmayaraq saytı rahat istifadə edə bilməli və məzmunu başa düşə bilməlidir.

- Saytlar klaviatura, maus, touch screen və digər yollarla sayta daxil olan istifadəçilər tərəfindən rahat istifadə edilə bilməlidir. Buna screen oxuyucular və Alexa və Google Home kimi səs asistantları da daxildir.

- Tətbiqlər rahat anlaşıla bilən və rahat istifadə oluna bilən olmalıdır. Bu səbəbdən, istifadəçinin vizual, fiziki və əqli qüsurları da nəzərə alınmalıdır.

- Saytlar həmçinin heç bir zərərə səbəb olmamalıdır: animasiya kimi bəzi web funksionallıqlar, baş ağrısına və ya [epileptik tutulma](https://en.wikipedia.org/wiki/Epileptic_seizure)ya səbəb ola bilər.

**Defolt olaraq, HTML düzgün istifadə olunarsa, müyəssərdir.**

## Kiçik bir nümunə

Accessibility, sadəcə Web texnologiyalara aid bir mövhum deyil, o bütün texnologiyalar adiddir. Accessibility-ni yoxmalaq üçün, hər hansı bir fiziki və ya əqli qüsurunuzun olmasına ehtiyac yoxdur. Əgər hər hansı bir sayta mobil qurğunuz vasitəsilə daxil olduqda onu istifadə etməkdə çətinlik çəkirsinizsə və ya siçanınız olmadıqda hansısa bir saytı tək klaviatura ilə istifadə edə bilmirsinizsə, bu həmin saytın müyəssər (accessible) olaraq yazılmaması ilə bağlıdır.

Bunu yoxlamaq, üçün tanıdığınız istənilən web sayta daxil ola bilərsiniz. Nümunə üçün, https://www.edx.org/ saytına daxil olub, siçanı istifadə etmədən, tək klaviaturanız ilə saytda gəzişməyə çalışın.

> **Qeyd:** Bu sənədləşmədə "accessibility" və müyəssərlik sözünü bir-birinin əvəzi olaraq işlədəcəyik.

Aşağıdakı məqalələri oxuyaraq, accessibility haqqında daha detallı məlumat əldə edə və ən yaxşı praktikaları öyrənə bilərsiniz.
Bütün məqalələr, [Mozilla Developers Network](https://developer.mozilla.org/en-US/)-ün [accessibility haqqında paylaşdığı məlumatlar](https://developer.mozilla.org/en-US/docs/Web/Accessibility)a əsaslanaraq yazılmışdır.

- Müyəssərlik nədir?

  - [Müyəssərlik haqqında](muyesserlik-nedir/muyesserlik-haqqinda.md)
  - [Hansı növ əlilliklər nəzərə alınır?](muyesserlik-nedir/elilliyin-novleri.md)
  - [Müyəssərliyin tətbiqi](muyesserlik-nedir/tetbiqi.md)
  - [Müyəssərliyin qaydaları və qanunvericilik](muyesserlik-nedir/qaydalar-ve-qanunvericilik.md)
  - [Müyəssərlik API-ləri](muyesserlik-nedir/apiler.md)

- HTML: Müyəssərlik üçün əsas

  - [HTML və Müyəssərlik](html-ve-muyesserlik/html-ve-muyesserlik.md)
  - [Yaxşı Semantika](html-ve-muyesserlik/yaxshi-semantika.md)
  - [Müyəssər Məlumat Cədvəlləri](html-ve-muyesserlik/melumat-cedvelleri.md)
  - [Mətn Alternativləri](html-ve-muyesserlik/metn-alternativleri.md)
  - [Keçidlər Haqqında](html-ve-muyesserlik/kecidler-haqqinda.md)

- CSS və JavaScript ən yaxşı praktikalar

  - [CSS](css-ve-js-praktikada/css.md)
  - [JavaScript](css-ve-js-praktikada/js.md)

- WAI-ARIA əsasları

  - [WAI-ARIA Nədir?](wai-aria-esaslari/wai-aria-nedir.md)
  - [WAI-ARIA praktiki nümunələr](wai-aria-esaslari/wai-aria-numuneler.md)

- Müyəssər Multimedia

  - [Multimedia və Müyəssərlik](muyesser-multimedia/multimedia-ve-muyesserlik.md)
  - [Müyəssər Audio və Video](muyesser-multimedia/muyesser-audio-ve-video.md)
  - [Audio Transkriptlər](muyesser-multimedia/audio-transkriptler.md)
  - [Video Mətn Parçaları](muyesser-multimedia/video-metn-parcalari.md)

- Mobil Müyəssərlik

  - [Mobil Qurğularda Müyəssərlik](mobil-muyesserlik/mobil-qurgularda-muyesserlik.md)
  - [Android və iOS-da screen oxuyucuları](mobil-muyesserlik/screen-oxuyuculari-android-ios.md)
  - [İdarə Mexanizmləri](mobil-muyesserlik/idare-mexanizmleri.md)
  - [Responsiv Dizayn](mobil-muyesserlik/responsiv-dizayn.md)
  - [User inputlar](mobil-muyesserlik/user-inputlar.md)
