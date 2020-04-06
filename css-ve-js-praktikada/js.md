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
