# Mətn alternativləri

Mətnlər təbii olaraq müyəssər olduğuna baxmayaraq eyni şeyi vizual kontentlər üçün deyə bilmərik - şəkil/video kimi multimedia görmə əngəlli insanlar üçün, audio isə eşitmə əngəlli insanlar üçün müyəssər deyil. Video və audio məzmunu ilə bağlı daha ətraflı sonrakı məqalələrdə danışacağıq, bu məqalədə isə `<img>` elementinin müyəssərliyi ilə bağlı danışacağıq.

Aşağıdakı nümunədə eyni şəklin 4 fərqli nümunəsinə baxa bilərsiniz:

```html
<img src="dinosaur.png" />

<img
  src="dinosaur.png"
  alt="A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth."
/>

<img
  src="dinosaur.png"
  alt="A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth."
  title="The Mozilla red dinosaur"
/>

<img src="dinosaur.png" aria-labelledby="dino-label" />

<p id="dino-label">
  The Mozilla red Tyrannosaurus Rex: A two legged dinosaur standing upright like
  a human, with small arms, and a large head with lots of sharp teeth.
</p>
```

Birinci şəkil ekran oxuyucusu vasitəsilə oxunduğunda istifadəçiyə kifayət qədər məlumat vermir - VoiceOver bu şəkli oxuduğunda `"/dinosaur.png, image".` kimi oxuyacaq və bu halda şəklin hansısa dinozavr şəkli olduğunu anlayacağıq. Lakin real layihələrdə şəkilləri heç də bu cür adlandırmırıq, bu adlar daha çox kompüter (misalçün fotoaparat) vasitəsilə generasiya olunmuş adlar olur.

Ekran oxuyucusu ikinci şəkli oxuduğunda `alt` atributunu şəkilə alternativ olaraq oxuyacaq - "A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth."

Bu məqam təkcə `alt` atributunun önəmliliyini deyil həm də nə üçün fayllara mənalı adlar qoymalı olduğumuzu bizə göstərir. Nəzərə alın ki, `alt` atributu şəklin vizual olaraq daşıdığı məlumatın təsviri olmalıdır. Buraya əlavə və gərəksiz məlumatlar yazmaq tövsiyyə olunmur.

Nəzərə almalı olduğunuz bir şey də, istifadə etdiyiniz şəklin kontentin içərisində hər hansı bir məna daşıyıb daşımamağıdır. Əgər şəkil sadəcə vizual dekorasiya üçün nəzərdə tutlubsa `alt` atributunu boş saxlaya və ya həmin şəkli CSS ilə `background-image` kimi istifadə edə bilərsiniz.

Şəkilə daha çox məlumat əlavə etmək istəsəniz, şəkli əhatə edən mətndən əlavə `title` atributundan da istifadə edə bilərsiniz. Bu halda, ekran oxuyucuları `alt` textini, `title` atributunu daha sonra isə faylın adını oxuyacaq. Onu da qeyd edək ki, `title` atributunda yazılmış məlumatı əksər brauzerlər şəklin üzərinə gəldiyinizdə (mouseover) tooltip kimi göstərəcəklər.

![mozilla red dinasour tooltip](https://media.prod.mdn.mozit.cloud/attachments/2016/11/10/14333/325e4485a405f1fb1f95595a9a6c9615/title-attribute.png)

Gəlin axırıncı metoda daha yaxından baxaq:

```html
<img src="dinosaur.png" aria-labelledby="dino-label" />

<p id="dino-label">The Mozilla red Tyrannosaurus ...</p>
```

Bu halda biz `alt` atributundan istifadə etmirik - əvəzində şəklin geniş təsvirini bir paraqrafda yazıb, həmin paraqrafa `id` atributu əlavə etmişik və `aria-labelledby` atributunu istifadə edərək bu paraqrafın həmin şəklin alternativ texti/etiketi olduğunu göstərmişik. Əgər bir neçə şəkil üçün eyni təsvir istifadə edirsinizsə bu üsul sizin işinizə yaraya bilər. `alt` atributu ilə bunu etmək mümkün deyil.

## Digər mətn alternativi mexanizmləri

Şəkillər üçün alternativ text təqdim etməyin daha bir yolu `longdesc` atributunda istifadə etməkdir. Bununla siz şəklin geniş təsviri yazılmış başqa bir HTML faylına istinad edirsiniz:

```html
<img src="dinosaur.png" longdesc="dino-info.html" />
```

Bəzi hallar üçün bu yaxşı fikir kimi səslənir. Xüsusilə də içərisində çoxlu məlumat saxlayan böyük qrafikləri bu cür təsvir etmək olar. Hərçənd `longdesc` atributu əksər ekran oxuyucuları tərəfindən dəstəklənmədiyi və ekran oxuyucusu işlətməyən adi istifadəçilər üçün əlçatan olmadığı üçün uzun təsviri eyni səhifədə saxlamaq və ya həmin yerə bir başa keçid qoymaq daha məqsədə uyğundur.

HTML5 həmçinin hər hansı bir fiquru (bu şəkil olmaq məcburiyyətində deyil) və fiqur haqqında məlumatı təsvir etmək üçün `<figure>` və `<figcaption>` elementləri təklif edir:

```html
<figure>
  <img src="dinosaur.png" alt="The Mozilla Tyrannosaurus" />
  <figcaption>
    A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a
    human, with small arms, and a large head with lots of sharp teeth.
  </figcaption>
</figure>
```

Təssüfllər olsun ki, ekran oxuyucuları bu cür fiqurları əlaqəli başlıqları ilə əlaqələndirə bilmir. Lakin bu struktur CSS stilləri tətbiq etmək üçün yararlıdır və kodun daxilində şəklin başlığının şəkillə bərabər yazılması imkanı yaradır.

## Boş alt atributları

```html
<h3>
  <img src="article-icon.png" alt="" />
  Tyrannosaurus Rex: the king of the dinosaurs
</h3>
```

Bəzi vaxtlarda kontentə daxil etdiyimiz şəkil, məzmunun bir parçası olmayıb sadəcə dekorasiya vəzifəsi daşıyır.
Yuxarıdakı kod nümunəsinə fikir versəniz, `alt` atributunun boş olduğunu görəcəksiniz - bu ekran oxuyucularını vadar edir ki, şəkli oxusunlar lakin onu təsvir etməyə çalışmasınlar (əksər hallarda sadəcə "image" deyə səsləndirirlər).

Boş `alt` atributunu daxil etməyin səbəbi odur ki, ekran oxuyucuları `alt` atributu görmədikdə şəklin URL-ini tam olaraq oxuyurlar. Yuxarıdakı nümunədə, şəkil başlığa sadəcə dekorasiya kimi qulluq edir. Şəklin heç bir məzmunu olmadıqda və sadəcə vizual dekorasiya məqsədli olduqda, boş `alt` atributu daxil etməyiniz tövsiyyə olunur. Bu davranışa nail olmağın digər yolu isə `role="presentation"` atributundan istifadə etməkdir.

> **Qeyd:** Dekorativ şəkilləri mümkün olduqca CSS ilə sayta daxil etməyə çalışın.

Daha sonra: [Keçidlər Haqqında](html-ve-muyesserlik/kecidler-haqqinda.md)
