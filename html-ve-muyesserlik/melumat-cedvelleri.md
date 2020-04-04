# Müyəssər məlumat cədvəlləri

Sadə bir HTML cədvəli aşağıdak kimi, sadə bir markapla yaradıla bilər:

```html
<table>
  <tr>
    <td>Ad</td>
    <td>Yaş</td>
    <td>Cins</td>
  </tr>
  <tr>
    <td>Hikmət</td>
    <td>13</td>
    <td>Kişi</td>
  </tr>
  <tr>
    <td>Şövkət</td>
    <td>8</td>
    <td>Qadın</td>
  </tr>
  <tr>
    <td>Nisəxanım</td>
    <td>5</td>
    <td>Qadın</td>
  </tr>
</table>
```

Lakin bu kodun problemləri var - ekran oxuyucusu istifadəçisinin sətirləri və sütunları bir-biri ilə əlaqələndirə bilməsi üçün heç bir yol yoxdur. Yuxarıda cədvəl nümunəsinə gəldikdə, bunu sadəcə vizual olaraq ayırd etmək mümkündür.

İndi isə [daha yaxşı cədvəl nümunəsi](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/styling-tables/punk-bands-complete.html)nə baxaq - burada müyəssərliyi artıran bir neçə nüans mövcuddur:

- Cədvəlin başlığı `<th>` elementi ilə işarə edilmişdir - siz həmçinin `scope` atributu vasitəsilə bu başlıqların sətirlərə yoxsa sütunlara aid olduğunu təyin edə bilərsiniz. Bu sizə ekran oxuyucularına tamamilə qruplaşdırılmış və anlaşıqlı məlumat təqdim edir.
- `<caption>` elementi və `<table>` elementinin `summary` atributu eyni işi görür - onlar cədvəlin alternativ mətni kimi qulluq göstərir və ekran oxuyucularına cədvəl haqqında ümumi məlumat verirlər. `<caption>` elementi bunlar arasında daha çox üstünlük verilənidir çünki bu həm də vizual pozğunluğu olmayan insanlar üçün də yararlıdır. İkisini birdən istifadə etməyinizə isə heç bir gərək yoxdur.

Daha sonra: [Mətn Alternativləri](html-ve-muyesserlik/metn-alternativleri.md)
