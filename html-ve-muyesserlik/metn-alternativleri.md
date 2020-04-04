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
