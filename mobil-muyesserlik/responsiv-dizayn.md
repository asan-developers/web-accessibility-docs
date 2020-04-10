# Responsiv Dizayn

[Responsiv dizayn](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Responsive/responsive_design_building_blocks) saytınızın layoutunun və digər funsionallıqlarının ekran ölçüsü və resolution kimi faktorlara görə dəyişməsinin və bu səbəbdən də müxtəlif növ qurğuları dəstəkləməsinin tətbiqi prosesidir.

Xüsusi olaraq mobil qurğularda həll olunması gərək olan problemlər aşağıdakılardır:

- Səhifə layoutunun mobil qurğulara uyğun olması. Misalçün, dar ekranlarda çox sütunlu layoutlar yaxşı görünməyəcək və bəzi hallarda fontun ölçüsünün kiçildilməsi lazım olacaq və s. Bu məsələlər, [media querylər](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries), [viewport](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag) və [flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox) kimi texnologiyalar vastəsilə həll oluna bilər.
- Yüklənən şəkillərin ölçüsünü nəzərdə tutmaq. Kiçik ölçülü ekranları olan qurğulara böyük ölçülü şəkilləri yükləməyin heç bir mənası yoxdur. Bu cür qurğular adətən zəif internet bağlantısından istifadə edir. Bu səbəbdən də, dar ekranlar üçün kiçik ölçülü şəkillər istifadə etməyiniz tövsiyyə olunur. Bunun üçün [responsive image techniques](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images) adlı məqaləyə istinad edə bilərsiniz.
- Yüksək resolutionlar barədə fikirləşmək. Əksər mobil qurğuların yüksək resolutionlu ekranı olduğu üçün, yüksək-resolutionlu şəkillərdən istifadə etmək lazımdır. Yuxarıda qeyd etdiyimiz kimi, responsiv şəkil texnikalarından istifadə edərək buna nail ola bilərsiniz. Əlavə olaraq, bütün ehtiyaclarınızı ödəyə bilən və əksər brauzerlərin dəstəklədiyi SVG vektor qrafikasından da istifadə edə bilərsiniz. SVG faylı həcm cəhətdən çox iri olmur və istənilən ekran ölçüsünə uyğun iti görüntü verəcəkdir.

## Mobil-spesifik mülahizələr

Mobil qurğularda müyəssərliyi təmin etmək üçün nəzərə alınmalı digər mühüm nöqtələr də mövcuddur. Onların bəziləri haqqında aşağıda tanış olacağıq.

## Böyütmənin qarşısını almamaq

[viewport](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag)u istifadə edərək böyütmənin qarşısını almaq mümkündür. Ölçüləndirmənin həmişə açıq olduğundan əmin olun və uzunluğu qurğunun ekranının uzunluğuna bərabər edin:

```html
<meta name="viewport" content="width=device-width; user-scalable=yes" />
```

Mümkünsə heç vaxt `user-scalable=no` istifadə etməyin - bir çox insan saytınızdakı bəzi kontenti görmək üçün böyütmə (zoom) funksiyasında istifadə edir və bu funksionallğı onlardan almaq yaxşı fikir deyil. Elə hallar ola bilər ki, ekranı böyütmək sizin dizaynınızı poza bilər; bu kimi hallarda böyütmənin qarşısını almalı olsanız da alternativ bir yol təklif etməyi unutmayın. Misalçün, saytınızdakı mətnin ölçüsünü dizaynınıza xələl gətirməyəcək şəkilə böyütmək imkanı yarada bilərsiniz.

## Menyuları müyəssər etmək

Mobil qurğuların ekranı dar olduğu üçün saytdakı menyunu media querylər və digər texnologiyalar vasitəsilə saytın yuxarısındakı kiçik bir ikona çevirmək ümumi praktikadır. Bu ikona kliklədiyinizdə menyu açılır və istifadəçi ancaq lazım olduqda menyunu görür. Bu ikonlar adətən alt-alta üç horizontal xətdən ibarət olur və hamburger və ya burger menyu adlandırılır.

Bu menyuları saytınızda tətbiq edərkən ikonun müxtəlif idarə mexanizmləri tərəfindən rahat idarə edilə biləcəyindən əmin olun.
Yaxşı hamburger menyu nümunəsinə baxmaq üçün [good hamburger menu example](http://fritz-weisshart.de/meg_men/) saytına baxın.
