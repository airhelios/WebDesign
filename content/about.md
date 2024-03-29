---
Title: About
Description: This is our about page.
---
<div class ="index center" markdown='1'>
Sidans uppbyggnad{.text-center}
==========================


Den här sidan är uppbyggd av
* [Font Awesome](https://fontawesome.com/)-ikoner &mdash; se footer för de ikoner som har använts.
* [Github](https://github.com/airhelios/WebDesign) &mdash; Sidan har ett repo på Github.
* [Google fonts](https://fonts.google.com/) &mdash; fonter från Google. I detta fall finns de lokalt i `shared/fonts`. Borealis-temat använder exempelvis Inconsolata och Montserrat (båda regular 400).
* [Markdown](https://www.markdownguide.org/getting-started/) &mdash; Märkspråk(markup) för att konvertera ren text till html. Denna text skrivs i markdown.
* [Nodejs](https://nodejs.org/en/about) &mdash; backend JavaScript-miljö.
* [Normalize.css](https://www.npmjs.com/package/normalize.css) &mdash; För att uppnå en viss enhetlighet i CSS mellan browsers.
* [Npm](https://docs.npmjs.com/about-npm) &mdash; Världens största pakethanterare. För JavaScript.
* [Pico-CMS](https://picocms.org/docs/) &mdash; Flat-file CMS för att hantera vårt innehåll. Flat-file innebär att vi arbetar med filer(.md) istället för databaser.
* [Sass](https://www.npmjs.com/package/sass) &mdash; en CSS-preprocesser som förenklar hantering av CSS-kod med bland annat modularisering och skript-konstruktioner.
* [Stylelint](https://www.npmjs.com/package/stylelint) + [stylelint-config-sass-guidelines](https://www.npmjs.com/package/stylelint-config-sass-guidelines) &mdash; för att validera .scss-koden.
* [Twig](https://twig.symfony.com/doc/3.x/) &mdash; template engine som används i pico-CMS. Jag använder den bland annat för att exekvera logik i footern
* [Unicode-ikoner](https://home.unicode.org/) &mdash; se footer för de ikoner som har använts.

</div>
<div class ="index center" markdown='1'>
Åtgärder och lärdomar{.text-center}
==========================  
</div>
<div class ="index center" markdown='1'>

Kmom01{#kmom01 .about-h2}
--------------- 
Nu går vi från att endast använda  HTML, PHP (med tillhörande XAMPP), CSS samt dbwebb-verktygen till att expandera med fler verktyg. Frågan är gäller: more is more eller less is more? Måste vara besvärligt att hålla koll på alla verktyg.

Vi börjar också arbeta med Github som kan både vara en frälsning och en smärta. När det går enkelt så är det en frälsning. Men när man råkar göra något fel ... jag har förlorat flera timmars arbete för att jag råkade göra mina git-kommandon i fel ordning/skrev fel.

Jag märker också att jag inte borde rusa igenom instruktionerna i övningarna. Devil is in the details. Missar man att följa någon instruktion eller råkar skriva fel så märks det kanske inte direkt. Ex: när jag missade att ändra båda raderna i .htaccess till mitt användarnamn. Eller när jag inte märkte att jag råkade döpa min .stylelintrc.json till ..stylelintrc.json (kmom02).

Gällande Pico-CMS så tänker jag att jag inte har några reflektioner just nu förutom att det är ett "flat-file cms". Brukar det vara så i "verkligheten"?

Installationen av verktygen gick till slut bra. Jag borde ha varit mer vaksam på att det verkligen blev rätt versioner av verktygen. Men det fixade jag sen.

</div>

<div class ="index center" markdown='1'>

Kmom02{#kmom02 .about-h2}
--------------- 
Här har jag blivit tvungen att felsöka en del. Felsökning i sig är faktiskt ett riktigt bra sätt att lära sig (men smärtsamt). Jag kunde inte få min github-ikon att visas när vi gick över till Font Awesome. Jag grävde igenom min kod och skapade testfiler för att förstå varför. Till slut gav jag upp hoppet och frågade i Discord-servern. Det visade sig att koden skulle vara <code>&lt;i class="fab fa-github" aria-hidden="true"></code> och inte <code>&lt;i class="fa fa-github" aria-hidden="true"></code> som jag trodde. 

Jag råkade göra fel i min git-kommandon så att jag blev av med några timmars arbete här. Ena gången så skapade jag en README.md direkt på github och kunde inte push:a min branch och den andra gången så committade jag fel grejor och använde fel kommando för att rensa committen.

Jag la till ett kommando i mitt `package.json` i `themes` för att kunna linta mitt tema borealis: `"style-borealis": "sass borealis/scss/style.scss borealis/css/style.css --no-source-map"`
. Som exekveras genom `npm run style-borealis`. 

Jag la till undantag för vad som skulle lintas i `.stylelintrc.json` så att den inte skulle kolla igenom mina Font Awesome-filer i min `kmom02_test`-tema.

Jag lärde mig att det är OK att blanda HTML och Markdown när Markdown inte räcker hela vägen.

Jag lärde mig också hur .scss-filer kopplas till sina motsvarande .css-filer.

Det är ett litet hinder att behöva kompilera .scss-filerna varje gång jag har ändrat dem för att se förändringen på min webbsida.

Jag förstår vad nyttan med normalize.css är. Har dock inga exempel på när den skulle göra någon skillnad.

De SASS-funktionaliteter jag använde var:
* variabler (kolla `variables.scss`)
* @extend i min `code.scss`. Där `pre` använder is av `@extend code`
* testade operatorer (ex width: 10px + 10px;) men såg ingen nytta av det ... ännu

Jag ser på [Sass-hemsida](https://sass-lang.com/documentation/) att det finns många funktionaliter (ex. funktioner, inbyggda moduler, debug) som jag inte har kollat på än.
### Extrauppgifter(kmom02){.about-h3}
Jag gjorde båda extrauppgifterna. Jag laddade ner fonterna från Google, som jag hänvisar till i `borealis/scss/fonts.scss` samt `shared/fonts`.
Jag använde lite Twig-kod + ett tillägg i min `_meta.md` för att både visa Font Awesome- och Unicode-ikoner i `footer.twig`:

`{% if social.icon starts with "fa" %} ... `

Tillägget i `_meta.md` var (märk väl Unicode:n på de två senare tilläggen): 
<pre class="code">
Social:
    - title: Link till sidans github repo.
      url: https://github.com/airhelios/WebDesign
      icon: fab fa-github
    - title: Link till dbwebb
      url: https://dbwebb.se/kurser/design-v3/
      icon: fas fa-university
    - title: Link till sidans github repo.
      url: https://github.com/airhelios/WebDesign
      icon: "&#38;#128049;"
    - title: Link till dbwebb
      url: https://dbwebb.se/kurser/design-v3/
      icon: "&#38;#127963;"
</pre>
</div>

<div class ="index center" markdown='1'>
Kmom03{#kmom03 .about-h2}
--------------- 
<ul>
<li>
Jag använde mig av <b>grid</b> på technology-sidan och av <b>flexbox</b> på de enskilda teknologierna.</li>
<li>Jag använde mig oftast av max-widths och widths i % för att undvika att jag fick horizontal scrollbars. Trots detta så hände det någon gång att jag fick en sån. Jag minns inte exakt hur jag löste det :/</li>
<li>Min mobila responsivitet var ganska enkel. Jag satte <code>display:none</code> på min aside när vp-bredden var lägre än 767px. Sen satte jag mina grid column-spans till max (3).

<li>Fick inte min responsiva navigationsmeny att kollapsa till en början. Insåg att jag hade glömt att flytta över lite kod från original <code>style.css</code>
<code>.hidden {
    display: none !important;
}</code> i <code>style.scss</code> i kmom01/kmom02. Men jag lärde mig i alla fall lite om hur navigationsmenyn fungerar och hur den är byggd.</li>

<li>Lärde mig också att det går att ställa in sass så att den kompilerar automatiskt så att jag inte behöver använda npm run style/style-borealis efter varje css-ändring.</li>

<li>Jag har arbetat med grid och flex i webtec-kursen. Men jag lärde mig mer om dess funktionaliteter. <a href="https://css-tricks.com/flex-grow-is-weird/">Artikeln</a> om flex-grow var intressant.</li>

<li>Det är ganska svårt att få PicoCMS+markdown att fungera bra ihop med HTML. Man måste känna till en del pitfalls, <code>markdown="1"</code> är viktigt. Dessutom är det viktigt att ha i åtanke att det går att fallbacka på sedvanligt HTML. </li>

<li>Jag hade glömt att validera HTML innan. Nu har jag iaf gjort det på alla sidor. På tal om detta så felsökte jag ganska länge när jag skulle validera min HTML på just denna sida. Tydligen så gick det inte att skriva ut <code>i class="fab fa-github" </code> med backticks för då la antingen min browser eller Pico till i-end tags i slutet på paragrafen. Vilket validatorn inte gillade.</li>

<li>Jag påmindes igenom om att det är bäst att ha import av mobile-responsiveness-CSS-delen längst ner i sin stylesheet. Annars kommer den ju inte skriva om något.</li>
</ul>

### Extrauppgifter(kmom03){.about-h3}
<ul>
<li>Jag såg till så att footern använde sig av flex.</li>
<li>Jag satt ett tag och försökte få navbaren att använda sig av flex. Det blev inte lika fint vid en kollapsad menu så därför skippade jag det.</li>
</ul>
</div>

<div class ="index center" markdown='1'>
Kmom04{#kmom04 .about-h2}
--------------- 
<ul>
<li markdown="1">Färger är svåra.</li>
<li markdown="1">Det är otroligt lätt att en mix and match av olika färger (oavsett om det är komplement, komplement/split, eller triadisk) blir väldigt gräll. Analoga färger och monokromatiska har inte samma problem tror jag. Det man kan göra är att ha en "huvudfärg" som är någonstans i gråskalan och sen kan man ha de andra färgerna som kompletterar.</li>
<li markdown="1">Jag lyckades tyvärr inte få till en estetiskt tilltalande färgmix :/</li>
<li markdown="1">Jag var lite behjälpt av att jag redan innan hade valt ut fonter som jag tyckte passade ihop med mitt tidigare färgschema. Mitt nya färgschema var bara en vidareutveckling på det gamla.</li>
<li markdown="1">Jag försökte lägga ett filter på min fav icon men jag fick inte filtret att fungera. Så jag gjorde the next best thing: jag gjorde den svartvit.</li>
<li markdown="1">I framtiden så kommer jag skapa en `variables.scss` och hålla mig till ett fåtal färger som jag återanvänder. Nu kändes det som att jag lappade min CSS-kod med mina förändringar, vilket också betyder att det förmodligen är kvar artefakter som inte används längre. En del av detta löste jag genom att skapa `*-dark.scss` versioner av befintliga `*.scss-filer`</li>
<li markdown="1">Jag valde ett "komplement färgschema" för att jag var trött på analog/monokromatisk efter att ha gjort min färgstudie. Jag tänkte att det skulle bli enkelt med komplement, för då behöver man bara ha 2 extra färger i beaktande</li>
<li markdown="1">Min dark theme var bara en enkel förenkling av min light theme. De småskillnader jag hade var att jag tog en mörkare grön och till följd av detta en mörkare lila som komplementfärger. Istället för att använda vita färger så använde jag en "off-white" på #e0e0e0. Jag använde också `filter: brightness(.8) contrast(1.2)` på mina bilder för att de skulle få lägre ljusstyrka men högre kontrast.</li>
<li>Färgerna jag valde var: <table style="border-spacing: 4px; border-collapse: separate">
<tr>
<td style="font-weight: bold;">Light</td>
<td style="height: 50px; width: 50px; background-color: #C6D6CC;; color: #181115">#C6D6CC</td>
<td style="height: 50px; width: 50px; background-color: #D6C6D0; color: #181115">#D6C6D0</td>
</tr>
<tr>
<td style="font-weight: bold;">Dark</td>
<td style="height: 50px; width: 50px; background-color: #111814; color: #e0e0e0">#111814</td>
<td style="height: 50px; width: 50px; background-color: #181115; color: #e0e0e0">#181115</td>
</tr>
</table></li>
</ul>
</div>

<div class ="index center" markdown='1'>
Kmom05{#kmom05 .about-h2}
--------------- 
<ul>
<li markdown="1">Laddningstids-analyser är ett stort område, det märks på alla "metrics" som går att ta ut. Det tar nog en lång tid att bli en mästare på att optimera sidor. Kanske finns det pengar i att optimera diverse laddningstider på personsidor?</li>
<li markdown="1">PageSpeed Insights kanske ger ett dåligt värde i prestanda eller några av laddningstiderna. Det märks ändå inte alltid för användaren.</li>
<li markdown="1">PicoCMS eller min browser i sig lägger till en `source`-end tag i min html. Det gör så att w3-validatorn blir missnöjd.</li>
<li markdown="1">Picture/srcset för "art direction". Vi kan styra vilka bildkvalitéer som visas med vilka enheter/pixeldensiteter.</li>
<li markdown="1">Vi har lärt oss hur man gör en responsive iframe via en container + CSS.</li>
<li markdown="1">Ett nytt problem: numera får jag försöka komma ihåg att ändra mitt Dark-tema också när jag skapar en ny scss-/css-fil.</li>
<li markdown="1">Markdown till html är inte helt smärtfritt. Det slängs in random taggar ex:p/source på icke-intuitiva ställen.</li>
<li markdown="1">Cimage funkade bra. Testade aspect ratio, crop, fit to content, save as jpeg. Testade aldrig filter. En sak som fick mig att fastna var image-directory vs analysrapportens directory. Bilderna laddades inte med "/image" ... Var tvungen att hänvisa till "../image".</li>
<li markdown="1">Stal grid från technologies. Funkade bra. Var dock tvungen att ändra stylingen så att borders/bakgrund passade med bilder.</li>
<li markdown="1">Iframes ger ett dåligt intryck. De passar nästan aldrig in naturligt på en vanlig hemsida.</li>
<li markdown="1">Kommenterad kod = tar bandbredd (det är kanske inte så när man kör mini?).</li>
</ul>
</div>


<div class ="index center" markdown='1'>
Kmom06{#kmom06 .about-h2}
--------------- 
<ul>
<li markdown="1">Designprinciper finns här: [Infographic designprinciper](https://static-cse.canva.com/blob/561631/20DP_Infographic.jpg) // [Canva Design Principles](https://www.canva.com/learn/design-elements-principles/)</li>
<li markdown="1">Det är viktigt att man följer principerna!</li>
<li markdown="1">Vi följer redan många av dem naturligt (balans, färg, symmetri etc.)</li>
<li markdown="1">Accessibility går att snabbkolla med lighthouse. Är detta allt för att klara av de nya EU-kraven?</li>
<li markdown="1">Hade varit riktigt coolt att bygga en sån här sida: [Shimane Misato](https://www.town.shimane-misato.lg.jp/misatoto/)</li>
<li markdown="1">Ganska svårt att lägga till och ändra större designprinciper i efterhand. Det är kanske bättre att tänka igenom sidan från början</li>
<li markdown="1">De personsidor som jag undersökte var i princip kopior av varandra med tanke på designprinciper</li>
<li markdown="1">Kom ihåg hur man la till grainy structure på sin sida, efter sista elementet kan man lägga: `:after {
    background: url(URL-TILL-STATIC-NOISE-BILD);
    content: "";
    height: 100%;
    left: 0;
    opacity: .05;
    pointer-events: none;
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 201;
}`</li>

</ul>
</div>

<div class ="index center" markdown='1'>
Good to know stuff
--------------- 
* sass --watch focus/scss/style.scss focus/css/style.min.css --no-source-map --style compressed
* npm run style-focus-dark && npm run style-focus-dark-min && npm run style-focus-light && npm run style-focus-light-min
* git tag -a v4.0.1 -m "Adding new color scheme"
* git push origin --tags
</div>

