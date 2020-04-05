# Keçidlər haqqında

Keçidlər (`href` atributu ilə işlənən `<a>` teqləri) istifadə olunmalarından asılı olaraq müyəssərliyə kömək edə və ya zərər verə bilərlər. Defolt olaraq keçidlər görünüşcə müyəssərdirlər - onlar istifadəçilərə səhifəni tez-bazar naviqasiya etmək imkanı yaradırlar. Halbuki onların CSS stilləri dəyişdirilsə və ya JavaScript vasitəsilə davranışları gözlənilməyən dəyişikliklərə məruz qalsa bu keçidlər saytınızın müyəssərliyinə zərər yetirə bilər.

## Linklərin stilləşdirilməsi

Defolt olaraq linklər digər textdən vizual baxımdan həm rənginə görə həm də text dekorasiyasına görə fərqlənirlər - adi vəziyyətə mavi və altdan xətt çəkilmiş, baş çəkilmiş vəziyyətdə bənövşəyi rəngdə, fokus olunduqda isə mavi outline ilə style olunmuş olurlar.

Rəng dəyişikliyi linkəri digər textdən fərqləndirmək üçün yeganə metod olmalı deyil. Keçidlərin rəngləri digər textlər kimi arxa fondan olduqca fərqlənməlidir. Əlavə olaraq, link olan text link olmayan textdən də fərqlənməlidir.

## Onclick eventləri

`<a>` teqləri çox vaxt adi düymələr kimi istifadə edilə bilmək üçün `onclick` eventləri ilə dəyişikliyə məruz qoyulur, `href` atributu `#` və ya `javascript:void(0)` ilə əvəz olunur ki, səhifə yenilənməsin.

Bu dəyərlər linkləri kopyalayarkən, sürüşdürərkən, linkləri yeni pəncərədə açarkən, bookmark edərkən və JavaScript yükləndiyində və ya tamamilə bloklandığında gözlənilməyən nəticələrə gətirib çıxara bilər. Bu həmçinin assistiv texnologiyalara yanlış semantik informasiya təqdim edir. Bu cür hallar üçün `<button>` elementindən istifadə etmək daha məqsədə uyğundur. Ümumiyyətlə əgər `<a>` elementini istifadə edirsinizsə, bu yalnız lazım olan halda və düzgün URL ilə istifadə olunmalıdır.

## Xarici keçidlər və HTML olmayan məzmuna keçid

Həm `target="_blank"` vasitəsilə açılan həm də `href` atributu başqa tip fayla istinad edən linklər aktiv olunduqda bu cür davranışın baş verəcəyini hansısa yolla təsvir etməlidirlər.

Zəif görmə problemi olan və ekran oxuyucularından istifadə edən və ya əqli narahatlığı olan insanlar gözlənilmədən yeni pəncərə və ya başqa bir tətbiq açıldığında qarışıqlığa düşə bilərlər. Aşağıdakı nümunələr yeni pəncərə açan və Power Point faylı açan keçidlərin yaxşı nümunəsidir:

```html
<a target="_blank" href="https://www.wikipedia.org/">
  Wikipedia (yeni pəncərədə açılır)
</a>

<a target="_blank" href="2017-annual-report.ppt">
  2017 İllik Hesabat (PowerPoint)
</a>
```

Diqqət yetirsəniz, bu keçidlərin təsvirində Power Point faylını və yeni pəncərə açacağı əvvəlcədən qeyd edilmişdir. Əgər bu davranışı təsvir etmək üçün hansısa ikondan istifadə edirsinizsə, alternativ mətn yazdığınızdan əmin olun.

## Skip linklər

Skip link və ya skipnav `<body>` elementinin başlanğıcına mümkün qədər yaxın yerləşdirilmiş və səhifənin əsas məzmununa keçidi göstərən `a` elementidir. Bu linklər insanlara bütün səhifələrdə təkrarlanan kontentin (misalçün, header və əsas naviqasiya) üzərindən keçmək imkanı yaradır.

Skip linklər saytınızda assistiv texnologiyaların köməyilə gəzişən istifadəçilər üçün xüsusilə yararlıdır çünki bu cür istiafəçilər üçün təkrarlanan keçidlərin üzərindən dəfələrlə keçmək bezdirici ola bilər. Skip linklərə aid aşağıdakı resurslardan daha ətraflı məlumat ala bilərsiniz:

- [WebAIM: "Skip Navigation" Links](https://webaim.org/techniques/skipnav/)
- [How–to: Use Skip Navigation links - The A11Y Project](https://a11yproject.com/posts/skip-nav-links/)
- [Understanding Success Criterion 2.4.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html)
