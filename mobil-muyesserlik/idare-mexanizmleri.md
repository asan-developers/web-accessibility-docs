# İdarə Mexanizmləri

CSS və JavaScript ilə bağlı əvvəlki məqaləmizdə xüsusi kontrol mexanizmlərinə xas olan xüsusi eventlərdən danışdıq ([Maus-spesifik evenlər](/css-ve-js-praktikada/js?id=maus-spesifik-eventlər)). Yadınıza salmaq üçün onu deyək ki, müxtəlif idarə mexanizmləri müxtəlif cür eventləri işə salır və eyni funksionallıq ilə əlaqələndirilə bilmər. Misalçün, `onmouseover`, `onmouseout` kimi eventləri maus olmadan (misalçün, lkaviatura və ya touch screen ilə) işə sala bilməzsiniz.

Əgər siz [simple-box-drag.html](https://github.com/mdn/learning-area/blob/master/accessibility/mobile/simple-box-drag.html) nümunəsinə baxsanız ([canlı nümunə](https://mdn.github.io/learning-area/accessibility/mobile/simple-box-drag.html)yə baxın) ekrandakı qutunun klaviatura və ya toxunuş ilə idarə edilə bilməyəcəyini görəcəksiniz. Bunun baş vermə səbəbi isə aşağıdakı kimi yazılmış koddur:

```javascript
div.onmousedown = function () {
  initialBoxX = div.offsetLeft;
  initialBoxY = div.offsetTop;
  movePanel();
};

document.onmouseup = stopMove;
```

Bu cür funksionallığı başqa bir idarə mexanizmi ilə əlaqələndirə bilmək üçün, həmin idarə mexanizminə spesifik olan eventlərdən istifadə etməlisiniz. Misalçün `ontouchstart`, `ontouchend` eventləri touch screen qurğuları nəzərə almaq üçün yaxşı üsuldur:

```javascript
div.ontouchstart = function (e) {
  initialBoxX = div.offsetLeft;
  initialBoxY = div.offsetTop;
  positionHandler(e);
  movePanel();
};

panel.ontouchend = stopMove;
```

Maus və touch eventlərin istifadə olunduğu tam nümunəyə baxmaq üçün [multi-control-drag-box.html](https://github.com/mdn/learning-area/blob/master/accessibility/mobile/multi-control-box-drag.html) faylına və ya [canlı nümunə](https://mdn.github.io/learning-area/accessibility/mobile/multi-control-box-drag.html)yə baxın.

Daha sonra: [Responsiv Dizayn](mobil-muyesserlik/responsiv-dizayn.md)
