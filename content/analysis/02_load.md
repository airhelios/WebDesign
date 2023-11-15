---
Title: 02_load
Description: This is the load time report
Template: analysis
---
Kmom05 - Load time-rapport
=======================


Mätvärden på bland annat prestanda och olika laddningstider för tre personsidor tas fram och analyseras i denna uppgift.

Urval{.analysis-h1}
-----------------------
Jag fortsätter med samma sidor som i [Kmom04](./01_colors). Några av anledningarna till varför dessa personsidor valdes ut var att jag får en känsla av att de tre personerna som presenteras på sidorna är:
<ol class="ol-analysis">
<li>Väldigt måna om sin image (såklart, de är ju kändisar).</li>
<li>Inte så tekniskt kunniga.</li>
<li>Känns lite "mänskligare" att recensera en personsida än ett företag eller produkt.</li>
</ol>

De tre sidorna är som sagt:

* [David McRaney](https://www.davidmcraney.com/) - skapare av podd "You're not so smart". 
* [Selena Gomez](https://www.selenagomez.com/#/) - Världskänd tjejpopsångerska.
* [Cristiano Ronaldos](https://www.cristianoronaldo.com/#cr7) - Topp två fotbollsspelare i världen. 

Metod{.analysis-h1}
-----------------------

<ol class="ol-analysis">
<li>[Google's PageSpeed Insights](https://pagespeed.web.dev/): Den kontrollerar en sida baserat på en del mätvärden såsom hur lång tid det tar innan första DOM-objektet ritas ut (FCP), hur lång tid det tar innan det störta objektet i above the fold ritas ut (LCP) med mera.</li>
<li>`Developer Tools > Network`. Här har transfer-mängden, resource-mängden, finish-time och load-time mätts.</li>
</ol>

För varje personsida så har tre underliggande sidor valts ut för analyserna. Då `Network`-analyserna har gjorts så består varje mätvärde av genomsnittet av tre värden. Dessa mätvärden tas genom att ladda om sidan (rensa cache) med `CTRL + F5`. Nedan ges en förklaring av mätvärdena:

* Transfer anger hur mycket resurser som laddas ner från sidan i komprimerat format i mb [1].
* Resource anger hur mycket utrymme de nedladdade resurserna tar i ickekomprimerat format i mb[1]. Här kan cache-mängden också ingå ifall man inte laddar om sidan med `CTRL + F5`.
* Finish - anger hur lång tid det tog att ladda ner sista elementet på sidan i ms [2].
* Load - anger hur lång tid det tar för browsern att ladda ner och presentera sidan för användaren (även denna i ms)[2].

Resultat{.analysis-h1}
-----------------------
<h3 class="analysis-h3">Cristiano Ronaldo</h3>
<div class="analysis-container" markdown="1">
Snaphot: Klicka på bilden för större format
<div class="analysis-row" markdown="1">
<a href="%assets_url%/img/load/cr-brands.png" class="analysis-img">![Snapshot of CR:s Brands-sida](../image/load/cr-brands.png?width=33%&save-as=jpeg){.img-1 .img-padded}</a>
</div>

<div class="embed-container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQGvOyWoN7Un_GVMEGg7k0Er5nN04LKHYyEVYZzm9f568xGXwr0d_qqVY2szB_cn1RvXJU9etbXTunq/pubhtml?widget=true&amp;headers=false"></iframe>
</div>

<h4 class="analysis-h4">Förbättringar</h4>
Förvånande nog så är CR:s Brand-sida helt OK när det gäller desktop-varianten (de andra två är ej godkända oavsett desktop/mobil). Två förslag vore:
<ol class="ol-analysis">
<li>Fixa den mobila-sidan.</li>
<li>Kolla igenom storleken/format på alla bilder (Cristiano har massor med stora bilder på sin sida).</li>
</ol>


</div>

<h3 class="analysis-h3">David McRaney</h3>
<div class="analysis-container" markdown="1">
Snaphot: Klicka på bilden för större format
<div class="analysis-row" markdown="1">
<a href="%assets_url%/img/load/dm-new-page.png" class="analysis-img">![Snapshot of David McRaney's "New"-sida](../image/load/dm-new-page.png?width=50%&save-as=jpeg){.img-1 .img-padded}</a>
</div>

<div class="embed-container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR2b3a8SOL2WSqTlY7TCZE9Z9O_u85MfVSjjS_wacbBMAywPsfQ8mJ91Icxn1P4lJ8PXsm-_5H0FTT_/pubhtml?widget=true&amp;headers=false"></iframe>
</div>

<h4 class="analysis-h4">Förbättringar</h4>
En bra sida som vinner på att den är liten. Desktop är betydligt bättre än mobile. På en sån här liten sida så hade jag föreslagit att kolla igenom CSS/JavaScript och ta bort onödiga rader kod där. Även om CSS och JavaScript verkar minifierad så lär det finnas överbliven kod som inte används längre. /press-sidan har problemet med att det ligger många youtube-videos i den. Det gör så att laddningstiderna blir höga: ex Total blocking time och även "load" i Chrome dev tools. Förslaget är att minska ner på dessa.					

</div>

<h3 class="analysis-h3">Selena Gomez</h3>
<div class="analysis-container" markdown="1">
Snaphot: Klicka på bilden för större format
<div class="analysis-row" markdown="1">
<a href="%assets_url%/img/load/sg-film-tv.png" class="analysis-img">![Snapshot of Selena Gomez's "Film-TV"-sida](../image/load/sg-film-tv.png?width=40%&save-as=jpeg){.img-1 .img-padded}</a>
</div>

<div class="embed-container">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQdtDIAA8vEfRHwVSIt-DbrEeccfpf2nXoQQRKNLv-0Nsu06_tHF63nAZPgGvnzxfW3o_ihDbfRPMwQ/pubhtml?widget=true&amp;headers=false"></iframe>
</div>

<h4 class="analysis-h4">Förbättringar</h4>
En extremt långsam sida (både mobile och desktop). Förslag: kolla igenom all  Legacy-kod som äter upp tiden. En gissning från kmom04 för denna sida var att den hade byggts i flera omgångar. Det borde tyda på att man har mycket legacy-kod som bara ligger och tar resurser. PageSpeed Insights klagar på att det är mycket resurser som måste laddas ner (stora bilder exempelvis). Detta gör så att tiderna ökar. First Contentful Paint är otroligt kasst på alla dessa sider. Man får vänta flera sekunder innan något DOM-element ritas upp.					
</div>

Analys{.analysis-h1}
-----------------------

Av de tre sidorna så var David McRaney's sida den som hade bäst statistik. Den var den enda som var godkänd på PageSpeed Insights när det gäller Core Web Vitals på alla tre undersidor både för mobil och desktop. 

Jag kollade bara sidorna överskådligt på mobilen men märkte att alla tre sidorna hade eftersatt den mobila prestandan. Laddningstiderna var längre men sidorna blev även mindre utsmyckade. Det var som att desktop-varianten var huvudsidan och mobila sidan var mest en eftertanke. 

Detta märktes i prestanda-scoren men även i laddningstider såsom Largest Contentful Paint, First Contentful Paint, Interaction to Next Paint. 

De vanligaste förbättringsåtgärderna på dessa sidor var (från PageSpeed):
<ul class="ol-analysis">
<li>Reducera JavaScript alt. CSS som inte används. Om JS/CSS inte uppfyller ett syfte så kommer det bara bidra till att laddningstiden ökar utan att göra någon skillnad på sidan.</li>
<li>Ta bort resurser som blockerar renderingen. När en sida håller på att laddas så måste den pausa och ladda ner och hantera länkade CSS-/JavaScript-filer. Två sätt att spara detta är genom att antingen låta CSS/JavaScript hanteras efter att sidan har laddats(asynchronous) eller lägga in CSS/JavaScript "inline" istället [3]. </li>
<li>Använd bilder med rätt storlek. Genom att använda bilder med mindre storlek så kan man spara laddningstid.</li>
<li>Skicka bilder i modernare bildformat. PageSpeed Insights föreslår att man ska använda bilder i formaten WebP och AVIF istället för PNG eller JPEG.</li>
</ul>

Av ovanstående åtgärder så skulle jag säga att de svåraste och som tar längst tid (i efterhand) borde vara "Ta bort resurser som blockerar renderingen" samt "Reducera CSS/JavaScript som inte används". För Selena Gomez sida som består av flertalet undersidor med olika format så kan det vara ett stort projekt att gå igenom sida för sida och eliminera onödig kod. 

Den åtgärd som är enklast men kanske smärtsammast för ytliga kändisar är att minska ner på bildernas storlek.

Jag får undersöka senare vad dessa "modernare" bildformat innebär.

<h4 class="analysis-h4">Gräns för laddningstid</h4>

Jag skulle bedöma att en sida som tar längre tid än <b>2-3</b> sekunder att ladda fullständigt är långsam för mig. Jag har arbetat i en del webbaserade verktyg som tar otroligt lång tid på sig att ladda nya sidor och det är en stor frustration i det. Tar det längre tid än ett par sekunder då har jag tappat den mentala tråden och vill söka mig annanstans. Jag tänker också att ifall jag måste göra något på hemsidan så kommer varje klick ta >3 sekunder. Av den anledningen så föredrar jag även textbaserade minimalistiska sidor där allt som man vill hitta går att hitta med en snabb skanning. 

David McRaney's sida klarar min tidsgräns medan CR och Selena Gomez klarar inte den alltid (nu tänker jag på "load"-värdet). Trots detta så känner jag inte en alltför stor frustration när jag är inne på SG/CR:s sidor. Jag tror det beror på att det går att interagera med sidorna och det finns ändå en del meningsfull info innan de är fulladdade. Detta märks på First Contentful Paint/Interaction to Next Paint-statistiken. Dessa är höga på CR/SG men vissa av dem ligger runt mina 2-3 sekunder som jag ansåg vara maxgränsen för färdigladdad sida. 


<h4 class="analysis-h4">Rangordning av sidorna</h4>

Jag rangordnar sidorna i laddningstid enligt:
<ol class="ol-analysis">
<li>David McRaney - denna sida var överlag snabbast på både mobil och desktop. Det var också den enda sidan som var godkänd på sina tre undersidor i Core Web Vitals. Jag hade dock undvikit press-sidan med alla Youtube-videos, den tar lång tid.</li>
<li>CR:s sida var dålig enligt statistiken. PageSpeed/Core Web Vitals ansåg den bara vara godkänd på en av de tre undersidorna och det var endast på desktop-varianten. Cristiano hade för många och för stora bilder!</li>
<li>Selena Gomez var ännu sämre än CR. Även om den var bäst när det gäller färgval så var sidan stor och brötig. Page Speed med sina Core Web Vitals ansåg inte några av de tre undersidorna vara godkända. Även här var bilderna ett stort problem men även resurser som blockerar renderingen var ett av de större problemen. Jag upplevde även att denna sida var långsammast.</li>
</ol>

Referenser{.analysis-h1}
-----------------------
[1] Stack Overflow-tråd: What is the difference between "transferred" and "resources" in Chrome DevTools Network tab?
[Länk](https://stackoverflow.com/questions/56043151/what-is-the-difference-between-transferred-and-resources-in-chrome-devtools) (hämtad 2023-11-15).
[2] Stack Overflow-tråd: Website response time: Difference between 'Load' and 'Finish'. [Länk](https://stackoverflow.com/questions/30266960/website-response-time-difference-between-load-and-finish) (hämtad 2023-11-15).

[3] Google: Remove Render-Blocking JavaScript. [Länk](https://developers.google.com/speed/docs/insights/BlockingJS) (hämtad 2023-11-15).


Övrigt{.analysis-h1}
-----------------------
Den här rapporten sammanställdes av Owais Sulehria