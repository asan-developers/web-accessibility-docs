# Müyəssərliyin layihənizdə tətbiqi

Accessibility haqqında əsas miflərdən biri odur ki, onu layihənizə tətbiq etmək uzun işdir və bir sıra çətinliklər yarada bilər.
Bu mif aşağıdakı hallarda doğru ola bilər:

- Artıq çoxdan hazır olan bir sayta accessibility tətbiq etmək istəyirsinizsə və həmin saytın bununla bağlı ciddi problemləri varsa
- Saytınızın çox hissəsi artıq hazırdır və siz son mərhələlərdə sayta accessibility əlavə etmək istəyirsiniz

Lakin əgər saytınızın müyəssərliyini, layihənin ilkin mərhələlərindən nəzərə alsanır, bunu sisteminizə tətbiq etmək elə də çətin olmayacaq.

Layihənizi planla yarkən, müyəssərliyin test olunmasını normal test rejiminə daxil edin. Necə ki, saytınızın digər funksionallıqlarını test edirsiniz, onu accessibility test üçün də hazırlayın.
İlkin mərhələlərdə bunun üçün avtomatlaşdırılmış testlərdən istifadə edərək, çatışmayan cəhətləri (misalçün `alt` atributu olmayan `img` teqlərini və s.) müəyyən edə bilərsiniz.
Daha sonra isə əlilliyi olan bəzi insan qrupları ilə işləyib, digər çatışmayan cəhətləri ortaya çıxara bilərsiniz. Buna misal olaraq aşağıdakıları göstərmək olar:

- Saytınızdakı date picker elementi ekran oxuyucuları istifadəçiləri tərəfindən istifadəyə yararlıdırmı?
- Saytınızdakı məzmun dinamik olaraq yenilənirsə, vizual əlilliyi olan insanlar bunun fərqinə varacaqlarmı?
- İstifadə etiyiniz UI Buttonlar klaviatura istifadəçilə üçün əlçatandırmı?

Kontenti daha çox müyəssər etmək üçün bacardığınız qədər araşdırın, potensial problemləri ortaya çıxarın və həllər/alternativlər barəsində düşünün. Mətnlə işiniz rahatdı, bəs əgər saytınızda qəşəng görünən 3D qrafika varsa?
Bu cür məzmunu hamı üçün əlçatan etmək üçün hansı yolların olduğuna baxmalı və tətbiq etməlisiniz. Misalçün, bütün multimediya kontentinizin transkriptinin olması, bir az uzun iş olsa da məsələnin bir həllidir.

Realist olmağa çalışın - 100% müyəssərlik ideal bir nəticədir lakin real deyil - siz həmişə hansısa kənar hallarla rastlaşacaqsınız ki, hər hansı bir istifadəçi üçün sizin saytı istifadə etmək çətinlik yaradacaq.
Lakin buna baxmayaraq əlinizdən gələni də etməlisiniz. Əgər saytınıza WebGL ilə qurulmuş 3D pie chart daxil etmək istəyirsinizsə, siz həmçinin bunun alternativi olaraq həmin məlumatı hansısa bir cədvələ də daxil etməlisiniz.
Və ya, həmin 3D pie chart-dan imtina edib, sadəcə cədvəl istifadə edə bilərsiniz - HTML cədvəlləri hamı üçün əlçatandır, daha az kod yazılmasını tələb edir və daha az CPU intensivdir.

Digər tərəfdən, əgər saytınız 3D grafikadan çoxlu istifadə edən galereya saytıdırsa görmə problemləri olan hər bir insan üçün müyəssər olmasını düşünmək də realistik deyil.

Müyəssərlik haqqında düşündüyünüzü göstərmək üçün, saytınızda sizin müyəssərlik barəsində siyasətinizi və gördüyünüz işləri detallı şəkildə izah edən accessibility statement (bəyanat) paylaşın. Əgər kimsə saytınızda mövcud olan problemlə bağlı şikayət edərsə, onlarla dialoq qurun və məsuliyyəti üzərinizə götürərək yaranmış problemi aradan qaldırmağa çalışın.

Yekun olaraq:

- Layihənizin əvvəlindən müyəssərlik mövzusunu nəzərə alın və saytınızı tez-tez test edin. Bütün digər bug-lar kimi, accessibility ilə bağlı problemlər də sonradan aşkarlandığında çətinliklər yarada bilər.
- Yadınızda saxlayın ki, accessibility üçün nəzərdə tutulmuş ən yaxşı praktikalar hər kəs üçün xeyirlidir, sadəcə əlilliyi olan insanlar üçün deyil. Misalçün, semantik HTML sadəcə ekran oxuyucuları üçün deyil həm də saytınızın tez yüklənməsinə və performansına müsbət təsir göstərir. Bu, hər kəsə, ələlxüsus da zəif internet bağlantısı olanlara və mobil qurğulardan saytınıza daxil olanlara xeyirli olacaqdır.
- Saytınızda müyəssərliklə bağlı bəyanat paylaşın və problem yaşayan insanlarla ünsiyyət qurun.

Daha sonra: [Müyəssərliyin qaydaları və qanunvericilik](muyesserlik-nedir/qaydalar-ve-qanunvericilik.md)
