# Yaxşı semantika

Yaxşı semantikanı niyə istifadə etməli olduğunuz və niyə doğru iş üçün doğru HTML elementi istifadə etməli olduğunu haqqında artıq söhbət açmışıq. Bu mövzu müyəssərliyin çox pis qırıldığı nöqtə olduğu üçün laqeyd qalmamalı olduğunuz bir mövzudur.

Həqiqət budur ki, webdə hər kəs HTML ilə qəribə şeylər düzəldir. Bəziləri köhnəlmiş lakin hələ də unudulmayan praktikalardan istifadə edərək HTML-i incidir, bəziləri isə sadəcə buna məhəl qoymur. Lakin səbəbindən asılı olmayaraq, nə vaxt bu cür kodla rastlaşsanız bacardığınız qədər onu dəyişib, düzəltməyə çalışın.

Bəzi hallarda bunu edə bilməməyiniz müzakirə mövzusu ola bilər - saytınız hansısa software vasitəsilə generasiya olunub və sizin bunun üzərində tam idarəniz yoxdur və ya saytınızda dəyişə bilmədiyiniz "third party" məzmun ola bilər (misalçün, reklamlar).

Məqsədimiz "hər şey və ya heç nə" deyil, ancaq - etdiyiniz hər kiçik dəyişiklik saytın müyəssərliyini artırmağa kömək edə bilər.

## Mətn məzmunu

Ekran oxuyucularına edə biləcəyimiz ən yaxşı şey, yaxşı strukturlaşdırılmış, başlıqlı, paraqraflı, siyahılı və s. məzmun təqdim etməkdir. Yaxşı semantik nümunə aşağıdakı kimi ola bilər:

```html
<h1>Mənim başlığım</h1>

<p>Bu sənədin birinci hissəsidir.</p>

<p>Bu isə daha bir paraqrafdır.</p>

<ol>
  <li>Bu isə</li>
  <li>sizin oxumağınız üçün</li>
  <li>bir siyahıdır</li>
</ol>

<h2>İkinci dərəcəli başlıq</h2>

<p>
  Bu mənim məqaləmin ilk alt hissəsidir. Mən bu məqaləni hər kəsin tapmağını çox
  istərdim.
</p>

<h2>Daha bir ikinci dərəcəli başlıq</h2>

<p>
  Bu isə, ikinci alt hissədir. Düşünürəm ki, bu əvvəlkindən maraqlı alınıb.
</p>
```

Bu məqaləni hər hansı bir ekran oxuyucusu ilə yoxlaya bilərsiniz. Mətnin üzərindən naviqasiya etsəniz, bunun çox rahat olduğunu görəcəksiniz.

- Ekran oxuyucusu mətni oxuduqca hər bir başlığı xüsusilə qeyd edəcək və istifadəçiyə nəyin başlıq, nəyin paraqraf olduğunu aydın edəcək.
- Hər bir elementdən sonra dayanacaq və istifadəçiyə oxuma tempini seçmək imkanı yaradacaq.
- Əksər ekran oxuyucularında mövcud olan əvvəlki/sonrakı başlıqlara getmək ikmanından yararlanmağa kömək edəcək.
- Bəzi ekran oxuyucularında isə başlıqları, mündəricat kimi təqdim etmək imkanı yaracaq.

Bəzən insanlar, başlıqları və paraqrafları yazarkən, sadəcə görünüşə diqqət yetirib semantik olmayan HTML elementlərindən istifadə edirlər:

```html
<font size="7">Mənim başlığım</font> <br /><br />
Bu sənədin birinci hissəsidir.
<br /><br />
Bu isə daha bir paraqrafdır.
<br /><br />
1. Bu isə
<br /><br />
2. sizin oxumağınız üçün
<br /><br />
3. bir siyahıdır
<br /><br />
<font size="5">İkinci dərəcəli başlıq</font>
<br /><br />
Bu mənim məqaləmin ilk alt hissəsidir. Mən bu məqaləni hər kəsin tapmağını çox
istərdim.
<br /><br />
<font size="5">Daha bir ikinci dərəcəli başlıq</font>
<br /><br />
Bu isə, ikinci alt hissədir. Düşünürəm ki, bu əvvəlkindən maraqlı alınıb.
```

Görüdüyünüz bu nümunə isə, çoxumuza tanış olan, semantik olmayan HTML-in bariz nümunəsidir. Təəssüflər olsun ki, bu cür markap ekran oxuycularını heç də sevindirmir - bu markapdan ekran oxuyucuları vasitəsilə mündəricat əldə edə bilməzsiniz, ekran oxuyucuları mətnin hansı hissəsində dayanmalı olduqlarını, hansı hissənin paraqraf, hansının başlıq olduğunu bilməyəcəklər. Bu səbəbdən də hamsını bir ağızdan oxuyub keçəcəklər.

Müyəssərlikdən əlavə, bu cür markap digər çətinliklər də yaradır - yazılmış HTML-i CSS vasitəsilə görünüş vermək olduqca çətin olacaq, fikir versəniz, düzgün əməlli CSS selektorlarından istifadə etmək də olmur. Həmçinin bu vəziyyət, JavaScript vasitəsilə markapda dəyişiklik etməyi də çətinləşdirir.
