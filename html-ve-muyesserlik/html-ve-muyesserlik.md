# HTML və Accessibility

HTML barəsində daha çox öyrəndikcə - çoxlu resurlar oxuduqda və çoxlu nümunələrlə tanış olduqda - davamlı olaraq mühüm bir mövzu ilə rastlaşacaqsınız: semantik HTML-in əhəmiyyəti (bəzən POSH - plain old HTML də adlandırılır). Bu o deməkdir ki, biz hər bir HTML elementini onların nəzərdə tutulmuş funksionallıqlarına görə istifadə etməliyik.

Düşünə bilərsiniz ki, bu nəyə lazımdır. Çünki, siz CSS və JavaScript vasitəsilə istədiyiniz HTML elementini istədiyiniz cür davranmağa vadar edə bilərsiniz. Misalçün, saytınızdakı videonu oynatmaq üçün düyməni bu cür yaza bilərsiniz:

```html
<div>Oynat</div>
```

Lakin daha sonra da tanış olacağımız kimi, hər iş üçün düzgün HTML elementini istifadə etmək daha məqsədəuyğundur:

```html
<button>Oynat</button>
```

HTML `<button>` elementləri sadəcə hazır görünüşü ilə deyil (çox güman ki, həmin görünüşü sonradan dəyişəcəksiniz) həmçinin defolt keyboard accessibility funksionallığı ilə də sizə kömək edə bilər - istifadəçilər `Tab` düyməsi vasitəsilə düymələr arasında seçim edə və `Return` və ya `Enter` düyməsi ilə seçimlərini aktivləşdirə bilərlər.

Semantik HTML-in yazılması semantik olmayan (pis) makrapın yazılmasından çox vaxt almır. Sadəcə olaraq layihənizin əvvəlindən bunu belə planlaşdırmalısınız. Semantik makrapın müyəssərlikdən əlavə digər üstün cəhətləri də var:

- **Yazılması daha asandır** - yuxarıda qeyd olunduğu kimi, bəzi funksiyaları hazırca əldə edirsiniz və əlavə olaraq markapın alaşılması daha asan olur.
- **Mobil qurğularda daha yaxşıdır** - semantik HTML semantik olmayan, spagetti koddan daha yüngüldür və responsiv edilməsi daha rahatdır.
- **CEO üçün yaxşıdır** - axtarış mühərrikləri başlıqların, keçidlərin və s. semantik elementlərin içərisindəki məzmuna `<div>` kimi semantik olmayan elementlərdən daha çox diqqət yetirir və bu müştərilərinizin sizin saytı daha tez tapmağına kömək edir.

Gəlin accessible HTML anlayışı ilə daha yaxından tanış olaq.

Daha sonra: [Yaxşı Semantika](html-ve-muyesserlik/yaxshi-semantika.md)
