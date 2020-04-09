# Multimedia və Müyəssərlik

Müyəssərlikdə problem yaradar digər bir kateqoriya isə multimediadır - video, audio və şəkillərin, assistiv texnologiyalar və onların istifadəçiləri tərəfindən başa düşülməsi üçün mətn alternativləri olmalıdır. Bu məqalədə bunu necə etmək lazım olduğunu öyrənəcəyik.

İndiyədək sadə mətndən tutmuş, məlumat cədvəllərinə (data tables), şəkillərə, button, link və form elementləri kimi kontrolları və hətta (WAI-ARIA ilə) daha mürəkkəb kontrolları necə müyəssər etmək lazım olduğu barəsində ətraflı danışdıq. Bu məqalədə müyəssərliyinin təmin olunması o qədər də asan olmayan digər kontentlər - multimedia haqqında danışacağıq. Şəkilləri, videolar, `<canvas>` elementləri, Flash filmlər və s. kimi məzmunun ekran oxuyucuları vasitəsilə oxunması və ya klaviatura ilə idarə olunmasını təmin etmək elə də asan deyil.

Lakin ruhdan düşməyin - bu modulda multimedianı necə müyəssər etməli olduğumuz barəsində müxtəlif yanaşmalar və texnikalar təqdim edəcəyik.

## Adi şəkillər

[Mətn Alternativləri](/html-ve-muyesserlik/metn-alternativleri) məqaləmizdə HTML `img` elementləri üçün mətn alternativləri yazılması barəsində ətraflı danışmışdıq. Detallar üçün həmin məqaləyə istinad edə bilərsiniz. Qısası, vizual kontent üçün həmişə mətn alternativi təqdim etdiyinizdən əmin olun ki.

Misalçün:

```html
<img
  src="dinosaur.png"
  alt="A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth."
/>
```

Daha sonra: [Müyəssər Audio və Video](muyesser-multimedia/muyesser-audio-ve-video.md)
