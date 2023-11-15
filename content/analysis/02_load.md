---
Title: 02_load
Description: This is the load time report
Template: analysis
---
Kmom04 - färgrapport
=======================


Mätvärden på bland annat prestanda och olika laddningstider för tre personsidor tas fram och analyseras i denna uppgift.

Urval{.analysis-h1}
-----------------------
Jag fortsätter med samma sidor som i [Kmom04](./01_colors). Några av anledningarna till varför dessa personsidor valdes ut var att jag får en känsla av att de tre personerna som presenteras på sidorna är 
1. Väldigt måna om sin image (såklart, de är ju kändisar).
2. Inte så tekniskt kunniga.
3. Känns lite "mänskligare" att recensera en personsida än ett företag eller produkt.


De tre sidorna är som sagt:

* [David McRaney](https://www.davidmcraney.com/) - skapare av podd "You're not so smart". 
* [Selena Gomez](https://www.selenagomez.com/#/) - Världskänd tjejpopsångerska.
* [Cristiano Ronaldos](https://www.cristianoronaldo.com/#cr7) - Topp två fotbollsspelare i världen. 

Metod{.analysis-h1}
-----------------------

I denna analys så har två verktyg använts: 
1) [Google's PageSpeed Insights](https://pagespeed.web.dev/): Den kontrollerar en sida baserat på en del mätvärden såsom hur lång tid det tar innan första DOM-objektet ritas ut (FCP), hur lång tid det tar innan det störta objektet i above the fold ritas ut (LCP) med mera.
2) `Developer Tools > Network`. Här har transfer-mängden, resource-mängden, finish-time och load-time mätts.

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

Alla tre personsidorna använde sig av ett monokromatiskt färgschema. Det går att argumentera för att David McRaneys sida använder sig av ett analogt färgschema. Men skillnaden var så liten här att det är enklare att anta att det var monokromatiskt. Jag antar att monokromatiskt färgschema är ett av de lättare färgschemana. Ju fler färger man introducerar desto enklare är det att få färgerna att skära sig eller att ge ett felaktigt intryck. 


Selena Gomez hade CSS-mässigt ett monokromatiskt färgschema men många gånger så var bilderna på hennes sida i en helt annan färg exempelvis:
<a href="%assets_url%/img/colors/selena-page.png" class="analysis-img">![A picture on Selena's page](%assets_url%/img/colors/selena-page.png){.img-3}</a>

Alla sidorna hade en tydlig färgprofil. Det var däremot svårt att gräva fram vilka fonter/färgprofiler de hade utifrån källkoden/css/developer tools. Jag laddade sen ner chrome-extension:en Fontanello som hjälpte mig bekräfta att jag hade prickat in rätt fonter. Jag tror att speciellt Ronaldos och Selenas hemsidor har byggts i olika etapper. Det finns nog en del gammal kod som gör relevant kod oklar.

Av de tre sidorna så var Selenas den mest behagliga, mest opretentiösa och hade en bäst uttalad identitet, David McRaneys sida var enkel men passade ändå innehållet. Ronaldos sida var nästan en karikatyr, även om färgschemat inte var helt fel. 

Några få slutsatser jag hade från denna studie:
* Färgschemat i CSS:en kan kompletteras med färger i bilder för att öka dimensionerna i de valda färgerna.
* Färgschemat och typsnitt måste matcha innehållet så att hela sidan får samma identitet. Något som Ronaldos sida misslyckas med.
* Ett monokromatiskt färgschema behöver inte betyda tråkig.
* Ronaldos sida var redan i dark mode från början (får jag intrycket av) bilderna hade en lägre kontrast och det var mörka färger hela vägen igenom. Det kanske är enklare att börja med dark mode och sen göra ett ljust tema.
<br><br>
Om jag gjorde om den här uppgiften så hade jag avsiktligt valt ut en sida som inte har ett monokromatiskt färgschema. Dock kan man konstatera, speciellt med avseende på Selenas sida, att man kommer långt med monokrom och välvalda bilder.

Referenser{.analysis-h1}
-----------------------
[1] https://stackoverflow.com/questions/56043151/what-is-the-difference-between-transferred-and-resources-in-chrome-devtools
[2] https://stackoverflow.com/questions/30266960/website-response-time-difference-between-load-and-finish


Övrigt{.analysis-h1}
-----------------------
Den här rapporten sammanställdes av Owais Sulehria