# Müyəssər audio və video kontrolları

Web əsaslı audio/video üçün kontrollar yaratmaq asan işdi hə? Gəlin bir yerdə araşdıraq.

## Native HTML5 kontrolları ilə bağlı problem

HTML5 video və audio elementləri medianı rahat idarə edə biləyiniz üçün hazır kontrollar ilə birgə gəlir. Milsalçün, [native-controls.html](https://github.com/mdn/learning-area/blob/master/accessibility/multimedia/native-controls.html) faylına (və ya [canlı nümunəyə](https://mdn.github.io/learning-area/accessibility/multimedia/native-controls.html)) baxın.

```html
<audio controls>
  <source src="viper.mp3" type="audio/mp3" />
  <source src="viper.ogg" type="audio/ogg" />
  <p>
    Your browser doesn't support HTML5 audio. Here is a
    <a href="viper.mp3">link to the audio</a> instead.
  </p>
</audio>

<br />

<video controls>
  <source src="rabbit320.mp4" type="video/mp4" />
  <source src="rabbit320.webm" type="video/webm" />
  <p>
    Your browser doesn't support HTML5 video. Here is a
    <a href="rabbit320.mp4">link to the video</a> instead.
  </p>
</video>
```

`controls` atributu sizi play/pause düymələrilə, səs artırıb azaltma düymələrilə və digər yararlı kontrollarla təmin edir. Bu kontrolları Firefox və Chrome-da aşağıdakı kimi görünür:

<img src="https://media.prod.mdn.mozit.cloud/attachments/2016/12/03/14440/2dd9c8069bc48948a475cae85811ff96/native-controls-firefox.png" alt="native video/audio controls in firefox" width="400px" />

<img src="https://media.prod.mdn.mozit.cloud/attachments/2016/12/03/14438/3bb04ba8bd6a9e2b403e8872399d38d4/native-controls-chrome.png" alt="native video/audio controls in chrome" width="400px" />

Lakin bu kontrollar ilə bağlı bir-iki problem mövcuddur:

- Bu kontrllar bütün brauzerlərdə keyboard accessible deyil. Misalçün, tab düyməsilə kontrollar arasında hərəkət edə və düymələri aktivləşdirə bilməzsiniz. Opera və Chrome bunu bir az tətbiq etsə də, yenə də tam ideal deyil.
- Müxtəlif brauzerlərdə bu pleyerlərin müxtəlif cür görünüşləri var. Bu kontrollara CSS ilə stil vermək olmur, yəni onları saytınızın stilinə uyğunlaşdırmaq bir az qəliz məsələ olacaq.

Bunun yeganə dərmanı isə defolt verilən kontrolları gizlədib öz kontrollarımızı yaratmaqdır.

## Öz audio və video kontrollarımızı yaratmaq

HTML5 video və audio elementləri ortaq bir API paylaşırlar - HTML Media Element - siz bu API-lardan istifdə edərək funksionallığı öz hazırladığınız buttonlara bağlaya bilərsiniz.

Gəlin yuxarıda gördüyünüz video nümunəsinə öz kontrollarımızı əlavə edək.

## İlkin quraşdırma

Əvvəlcə gəlin bayaqkı HTML koduna öz əlavələrimizi edək:

```html
<section class="player">
  <video controls>
    <source src="rabbit320.mp4" type="video/mp4" />
    <source src="rabbit320.webm" type="video/webm" />
    <p>
      Your browser doesn't support HTML5 video. Here is a
      <a href="rabbit320.mp4">link to the video</a> instead.
    </p>
  </video>

  <div class="controls">
    <button class="playpause">Play</button>
    <button class="stop">Stop</button>
    <button class="rwd">Rwd</button>
    <button class="fwd">Fwd</button>
    <div class="time">00:00</div>
  </div>
</section>
```

## JavaScriptin quraşdırılması

Yuxarıda gördüyünüz kimi, videonu idarə etmək üçün bəzi sadə buttonlar əlavə etmişik. Təbii ki, bu buttonlar öz-özərinə heç nə etməyəcəklər - bəsit funksionallığı təmin etmək üçün JavaScriptdən istifadə edəcəyik.

Əvvəlcə hər bir kontrolu JavaScript ilə seçəcəyik:

```javascript
const playPauseBtn = document.querySelector('.playpause');
const stopBtn = document.querySelector('.stop');
const rwdBtn = document.querySelector('.rwd');
const fwdBtn = document.querySelector('.fwd');
const timeLabel = document.querySelector('.time');
```

Daha sonra isə həmin audio/video playerə JavaScript ilə istinad edəcəyik:

```javascript
const player = document.querySelector('video');
```

Bu dəyişən üzərində bizim üçün yararlı olacaq propertylər və methodlar saxlayan [`HTMLMediaElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement) obyekyinə istinad edir. Bu methodlardan və propertylərdən istifadə edərək əlavə etdiyimiz buttonlara funksionallıq yükləyəcəyik.

Öz buttonlarımıza funksionallığı əlavə etməzdən əvvəl gəlin video playerin üzərindəki kontrollardan qurtulaq ki, qarışıqlıq yaranmasın:

```javascript
player.removeAttribute('controls');
```

Deyə bilərsiniz ki, bu kontrolları JavaScript ilə silmək əvəzinə (`controls` atributunu silməklə) ümumiyyətlə markapa daxil etməyə bilərdik. Lakin hər hansı səbəbdən JavaScript faylımız brauzerə yüklənməsə (misalçün, JavaScript bloklansa) o zaman bu defolt kontrollar istifadəçilərə yardımçı olacaq.

## Düymələri düz-qoş etmək

Əvvəlcə gəlin play/pause düyməsini quraşdıraq. Bunu etmək üçün sadə bir şərti funksiya yazıb düymənin halını play və pause arasında dəyişə bilərik:

```javascript
playPauseBtn.onclick = function () {
  if (player.paused) {
    player.play();
    playPauseBtn.textContent = 'Pause';
  } else {
    player.pause();
    playPauseBtn.textContent = 'Play';
  }
};
```

Stop düyməsini işə salmaq üçün isə aşağıdakı kimi bir kod yazacağıq:

```javascript
stopBtn.onclick = function () {
  player.pause();
  player.currentTime = 0;
  playPauseBtn.textContent = 'Play';
};
```

`HTMLMediaElement`in üzərində `stop()` funksiyası mövcud olmadığı üçün biz `pause()` methodundan istifadə edəcək və `currentTime`-ı sıfıra bərabər edəcəyik.

Daha sonra isə irəli və geri düymələrini quraşdıracağıq - bunun üçün aşağıdakı kodu istifadə edə bilərsiniz:

```javascript
rwdBtn.onclick = function () {
  player.currentTime -= 3;
};

fwdBtn.onclick = function () {
  player.currentTime += 3;
  if (player.currentTime >= player.duration || player.paused) {
    player.pause();
    player.currentTime = 0;
    playPauseBtn.textContent = 'Play';
  }
};
```

Bu çox sadədir, sadəcə olaraq düymələr hər dəfə klikləndiyində `currentTime`-a 3 əlavə edib və ya çıxırıq. Real video playerdə isə bundan daha mürəkkəb bir mexanizm fikirləşib tətbiq etməli ola bilərsiniz.

Fikir verin ki, biz həmçinin `currentTime` propertysinin `duration`-dan (videonun uzunluğundan) kiçik olmasını və videonun hal hazırda oynadılıb oynadılmamasını da yoxlayırıq. Əgər bu hallardan hansısa ödənərsə o zaman biz sadəcə olaraq videonu dayandırırıq.

Sonda isə aşağıdakı kod vasitəsilə videonun nə qədərinin qaldığını göstəririk:

```javascript
player.ontimeupdate = function () {
  let minutes = Math.floor(player.currentTime / 60);
  let seconds = Math.floor(player.currentTime - minutes * 60);
  let minuteValue;
  let secondValue;

  if (minutes < 10) {
    minuteValue = '0' + minutes;
  } else {
    minuteValue = minutes;
  }

  if (seconds < 10) {
    secondValue = '0' + seconds;
  } else {
    secondValue = seconds;
  }

  mediaTime = minuteValue + ':' + secondValue;
  timeLabel.textContent = mediaTime;
};
```

Vaxt hər dəfə yeniləndiyində bu funksiya işə düşəcək və verilmiş `currentTime`-ın dəyərindən gedən dəqiqəni və saniyəni göstərəcək.

Göstərdiyimiz sadəcə öz video playerinizi hazırlamağın çox sadə bir nümunəsi idi. Daha mürəkkəb funksionallıqlara malik playerləri hazırlaya bilmək üçün aşağıdakı mənbələrdən yararlana bilərsiniz.

- [Audio and video delivery](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery)
- [Video player styling basics](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery/Video_player_styling_basics)
- [Creating a cross-browser video player](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery/cross_browser_video_player)

Həmçinin göstərdiyimiz sadə nümunənin [canlı versiyası](https://mdn.github.io/learning-area/accessibility/multimedia/custom-controls-OOJS/) ilə də tanış ola bilərsiniz.
