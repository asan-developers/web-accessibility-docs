# Yaxşı semantika

Yaxşı semantikanı niyə istifadə etməli olduğunuz və niyə doğru iş üçün doğru HTML elementi istifadə etməli olduğunu haqqında artıq söhbət açmışıq. Bu mövzu müyəssərliyin çox pis qırıldığı nöqtə olduğu üçün laqeyd qalmamalı olduğunuz bir mövzudur.

Həqiqət budur ki, webdə hər kəs HTML ilə qəribə şeylər düzəldir. Bəziləri köhnəlmiş lakin hələ də unudulmayan praktikalardan istifadə edərək HTML-i incidir, bəziləri isə sadəcə buna məhəl qoymur. Lakin səbəbindən asılı olmayaraq, nə vaxt bu cür kodla rastlaşsanız bacardığınız qədər onu dəyişib, düzəltməyə çalışın.

Bəzi hallarda bunu edə bilməməyiniz müzakirə mövzusu ola bilər - saytınız hansısa software vasitəsilə generasiya olunub və sizin bunun üzərində tam idarəniz yoxdur və ya saytınızda dəyişə bilmədiyiniz "third party" məzmun ola bilər (misalçün, reklamlar).

Məqsədimiz "hər şey və ya heç nə" deyil, ancaq - etdiyiniz hər kiçik dəyişiklik saytın müyəssərliyini artırmağa kömək edə bilər.

### Mətn məzmunu

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
