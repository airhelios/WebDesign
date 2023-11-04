---
Title: About
Description: This is our about page.
---
<div class ="index center" markdown='1'>
Sidans uppbyggnad
==========================
</div>
<div class ="index center" markdown='1'>
<p markdown='1'>
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
</p>
</div>

<div class ="index center" markdown='1'>
Åtgärder och lärdomar
==========================
</div>
<div class ="index center" markdown='1'>
Kmom01{#kmom01}
--------------- 
<p markdown='1'>
Nu går vi från att endast använda  HTML, PHP (med tillhörande XAMPP), CSS samt dbwebb-verktygen till att expandera med fler verktyg. Frågan är gäller: more is more eller less is more? Måste vara besvärligt att hålla koll på alla verktyg.

Vi börjar också arbeta med Github som kan både vara en frälsning och en smärta. När det går enkelt så är det en frälsning. Men när man råkar göra något fel ... jag har förlorat flera timmars arbete för att jag råkade göra mina git-kommandon i fel ordning/skrev fel.

Jag märker också att jag inte borde rusa igenom instruktionerna i övningarna. Devil is in the details. Missar man att följa någon instruktion eller råkar skriva fel så märks det kanske inte direkt. Ex: när jag missade att ändra båda raderna i .htaccess till mitt användarnamn. Eller när jag inte märkte att jag råkade döpa min .stylelintrc.json till ..stylelintrc.json (kmom02).

Gällande Pico-CMS så tänker jag att jag inte har några reflektioner just nu förutom att det är ett "flat-file cms". Brukar det vara så i "verkligheten"?

Installationen av verktygen gick till slut bra. Jag borde ha varit mer vaksam på att det verkligen blev rätt versioner av verktygen. Men det fixade jag sen.
</p>
</div>

<div class ="index center" markdown='1'>
Kmom02{#kmom02}
--------------- 
<p markdown='1'>
Här har jag blivit tvungen att felsöka en del. Felsökning i sig är faktiskt ett riktigt bra sätt att lära sig (men smärtsamt). Jag kunde inte få min github-ikon att visas när vi gick över till Font Awesome. Jag grävde igenom min kod och skapade testfiler för att förstå varför. Till slut gav jag upp hoppet och frågade i Discord-servern. Det visade sig att koden skulle vara `<i class="fab fa-github" aria-hidden="true">` och inte `<i class="fa fa-github" aria-hidden="true">` som jag trodde. 

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


