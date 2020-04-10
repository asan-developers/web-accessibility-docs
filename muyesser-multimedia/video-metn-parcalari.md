# Video Mətn Parçaları

Videonu görmə, eşitmə əngəlli insanlar və digər qrup insanlar (misalçün, zəif internet bağlantısı olanlar və ya videonuzun orijinal dilini başa düşməyənlər) üçün accessible etmək üçün videonuzla birlikdə mətn parçaları (misalçün, alt yazılar) da paylaşmalısınız.

> **Qeyd:** Mətn parçaları tək əlilliyi olan istifadəçi üçün yox istənilən istifadəçi üçün yararlıdır. Misalçün, istifadəçilər hansısa səsli mühitdə olarsa səsi eşitməyə bilər və ya kitabxana kimi səssizliyin qorunması vacib olan yerlərdə videonu səssiz izləyə bilərlər. Bu səbəbdən video ilə birlikdə paylaşılmış mətn parçaları onlar üçün yararlı ola bilər.

Bu yeni bir mövhum deyil - altyazılran televiziya xidmətlərində uzun müddətdən bəri mövcud olub.
Əksər ölkələr çəkdiyi filmləri ingilis dilli altyazı ilə birgə yayımlayır və əksər DVD-lərdə digər dillərdə də altyazılar mövcud olur.

Mətn parçalarının fərqli məqsədlər üçün nəzərdə tutulmuş bir neçə növü var. Qarşılaşacağınız əsas olanlar aşağıdakılardır:

- Titrlar (captions) - bunlar səsləri eşidə bilməyən isitifadəçilər üçün nəzərdə tutulmuşdur. Bu yazılara, videoda danışılar sözlər ilə birgə həmin sözləri kimin dediyi, videodakı insanların əsəbi və ya kefsiz olduğu, hal hazırda ifa olunan musiqinin gülməli və ya ağlamalı olduğu kimi kontekst ilə əlaqəli məlumatlar da daxildir.
- Altyazılar - videoda danışılanların tərcüməsindən ibarətdir. Bu tip mətn parçaları sadəcə videoda danışılan dili başa düşməyənlər üçün nəzərdə tutulmuşdur.
- Təsvirlər - səhnəni görə bilməyən (görmə əngəlli) insanlar üçün nəzərdə tutulmuşdur. Bu tip mətn parçaları, adətən izləyiciyə səhnəni və səhnədə baş verənləri təsvir edir.
- Fəsil başlıqları - bu başlıqlar istifadəçilərə media üzərində naviqasiya etmək imkanı yaradır.

## HTML5 video mətn parçalarının tətbiqi

HTML5 video elementi üçün nəzərdə tutulmuş mətn parçaları WebVTT (Web Video Text Tracks) formatında yazılmalıdır. Bu format, özündə mətn parçaları və həmin parçanın videonun hansı hissəsində göstərilməli olduğu, səhnənin hansı hissəsində yer almalı olduğu kimi əlavə metadata saxlayır. Bu mətn parçaları replikalar adlandırılır.

Səciyyəvi WebVTT faylı aşağıdakı kimi olur:

```
WEBVTT

1
00:00:22.230 --> 00:00:24.606
Bu birinci alt yazıdır.

2
00:00:30.739 --> 00:00:34.074
Bu isə ondan sonrakıdır.

  ...
```

Bu cür faylı HTML5 media elementinə daxil etmək üçün siz:

- Faylı .vtt formatında uyğun bir yerdə saxlamalısınız
- .vtt faylına [`<track>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/track) elementi ilə istinad edin. `<track>` elementi `<video>` və ya `<audio>` elementinin içərisində yerləşdirilməli lakin bütün `<source>` elementlərindən sonra daxil edilməlidir. [`kind`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/track#attr-kind) atributunu istifadə edərək mətn parçalarının altyazı, titr və ya təsvir olduğunu təyin edin. Son olaraq [`srclang`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/track#attr-srclang) atributu ilə yazdığınız mətnin hansı dildə olduğunu brauzerə bildirin.

Bu da sizə kiçik bir nümunə:

```html
<video controls>
  <source src="example.mp4" type="video/mp4" />
  <source src="example.webm" type="video/webm" />
  <track kind="subtitles" src="subtitles_en.vtt" srclang="en" />
</video>
```

Nəticə isə aşağıdakı kimi bir şey olacaq:

![video text tracks example](https://media.prod.mdn.mozit.cloud/attachments/2014/06/06/7887/8cd4155a98a0f851a524d22eb53ccb52/video-player-with-captions.png)

Daha ətraflı məlumat üçün [Adding captions and subtitles to HTML5 video](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video) məqaləsini oxumağınızı tövsiyyə edirik. Məqalədə düzəldilən [nümunəyə canlı bax](http://iandevlin.github.io/mdn/video-player-with-captions/)a və ya [mənbə kodu](https://github.com/iandevlin/iandevlin.github.io/tree/master/mdn/video-player-with-captions)na nəzər yetirə bilərsiniz. Bu nümunədə müxtəlif altyazılar seçmək imkanı yaratmaq üçün JavaScriptdən istifadə olunmuşdur. Nəzərə alın ki, altyazıları görmək üçün "CC" düyməsinə basıb, oradan dili seçməlisiniz.

> **Qeyd:** Search enginelər əsasən mətn üzərində işlədikləri üçün mətn parçaları sizə [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO) ilə bağlı da çox kömək edəcək. Mətn parçaları həmçinin search enginelərə videonun müəyyən bir yerini göstərməyə də kömək edir.
