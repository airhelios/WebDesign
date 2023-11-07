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
Kmom01{#kmom01}
--------------- 
Nu går vi från att endast använda  HTML, PHP (med tillhörande XAMPP), CSS samt dbwebb-verktygen till att expandera med fler verktyg. Frågan är gäller: more is more eller less is more? Måste vara besvärligt att hålla koll på alla verktyg.

Vi börjar också arbeta med Github som kan både vara en frälsning och en smärta. När det går enkelt så är det en frälsning. Men när man råkar göra något fel ... jag har förlorat flera timmars arbete för att jag råkade göra mina git-kommandon i fel ordning/skrev fel.

Jag märker också att jag inte borde rusa igenom instruktionerna i övningarna. Devil is in the details. Missar man att följa någon instruktion eller råkar skriva fel så märks det kanske inte direkt. Ex: när jag missade att ändra båda raderna i .htaccess till mitt användarnamn. Eller när jag inte märkte att jag råkade döpa min .stylelintrc.json till ..stylelintrc.json (kmom02).

Gällande Pico-CMS så tänker jag att jag inte har några reflektioner just nu förutom att det är ett "flat-file cms". Brukar det vara så i "verkligheten"?

Installationen av verktygen gick till slut bra. Jag borde ha varit mer vaksam på att det verkligen blev rätt versioner av verktygen. Men det fixade jag sen.

</div>

<div class ="index center" markdown='1'>

Kmom02{#kmom02}
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
### Extrauppgifter(kmom02)
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
Kmom03{#kmom03}
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

<li>Jag har arbetat med grid och flex i webtec-kursen. Men jag lärde mig mer om dess funktionaliteter. . <a href="https://css-tricks.com/flex-grow-is-weird/">Artikeln</a> om flex-grow var intressant.</li>

<li>Det är ganska svårt att få PicoCMS+markdown att fungera bra ihop med HTML. Man måste känna till en del pitfalls, <code>markdown="1"</code> är viktigt. Dessutom är det viktigt att ha i åtanke att det går att fallbacka på sedvanligt HTML. </li>

<li>Jag hade glömt att validera HTML innan. Nu har jag iaf gjort det på alla sidor. På tal om detta så felsökte jag ganska länge när jag skulle validera min HTML på just denna sida. Tydligen så gick det inte att skriva ut <code>i class="fab fa-github" </code> med backticks för då la antingen min browser eller Pico till i-end tags i slutet på paragrafen. Vilket validatorn inte gillade.</li>

<li>Jag påmindes igenom om att det är bäst att ha import av mobile-responsiveness-CSS-delen längst ner i sin stylesheet. Annars kommer den ju inte skriva om något.</li>
</ul>

### Extrauppgifter(kmom03)
<ul>
<li>Jag såg till så att footern använde sig av flex.</li>
<li>Jag satt ett tag och försökte få navbaren att använda sig av flex. Det blev inte lika fint vid en kollapsad menu så därför skippade jag det.</li>
</ul>
</div>

<div class ="index center" markdown='1'>
#### Good to know stuff
* sass --watch focus/scss/style.scss focus/css/style.min.css --no-source-map --style compressed
* git tag -a v4.0.1 -m "Adding new color scheme"
* git push origin --tags
</div>

<div class ="index center" markdown='1'>
#### Att göra imorgon
* Kolla font awesome-ikonerna. Varför skrivs deras färger över av *?
</div>
