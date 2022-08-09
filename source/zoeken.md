# Full-text zoeken

```{index} full-text zoeken
```

Full-text zoeken komt min of meer overeen met 
zoeken zoals een grote zoekmachine op het internet. Onze zoekmachine gaat er 
van uit dat je op zoek bent naar een vrij specifiek object of document en 
probeert je het best passende terug te geven. De zoekmachine doet dit door je
zoektermen te bekijken, alle objecten te zoeken die aan je zoektermen voldoen 
en tenslotte de meest relevante objecten vooraan te zetten. Als je naar 
*Gravensteen* zoekt, krijg je dus het meest *Gravenstenige* object te zien.

Om te bepalen wat nu het meest relevante object is, zijn er meerdere algoritmes
die kunnen gebruikt worden. In grote lijnen komt het echter op neer dat een
object waarin je zoekterm meer voorkomt, als meer relevant wordt gezien dan een
object waarin je zoekterm minder voorkomt. Hierbij wordt er rekening gehouden
met andere factoren zoals de lengte van het veld waarin een zoekterm voorkomt
(hoe kleiner een veld, hoe relevanter de zoekterm) en hoe vaak je zoekterm
voorkomt over alle objecten heen (hoe vaker, hoe minder relevant de zoekterm).
Daarnaast hebben we de zoekmachine ook zo geconfigureerd dat het voorkomen van 
een zoekterm in bepaalde velden meer relevant is dan in andere. Zo gaan we er 
van uit dat de titel meer doorweegt dan de tekst van een fiche. Als je naar 
*Gravensteen* zoekt, zal een object met als titel *Gravensteen* hoger scoren
dan een object waarin *Gravensteen* een keer in de tekst voorkomt.

*Zoeken naar "Gravensteen" bij de erfgoedobjecten in de inventaris*

Als we even naar de zoekmachine kijken, dan kunnen we simpelweg zoeken naar het
*Gravensteen* door op [het zoekformulier voor erfgoedobjecten](https://inventaris.onroerenderfgoed.be/erfgoedobjecten/zoeken) 
in het veld *Algemeen* de zoekterm `Gravensteen` in te tikken. Dit geeft een 
[lijst met resultaten](https://inventaris.onroerenderfgoed.be/erfgoedobjecten?tekst=gravensteen)
waarin het Gravensteen uit Gent bovenaan staat, gevolgd door een fiche over
het plein voor het Gravensteen, het Sint-Veerlplein, en een wijk dichtbij het
Gravensteen. Niet geheel onverwacht. We krijgen dus effectief de informatie
te zien die het meeste zegt over het Gravensteen. Het maakt trouwens ook helemaal 
niet uit of we zoeken op *Gravensteen* of *gravensteen*, de toepassing werkt
hier hoofdletteronafhankelijk.

Stel echter dat we iets meer willen weten over het Gravensteen in Aalst. Als we
`Gravensteen Aalst` als zoekterm gebruiken, dan krijgen we nog maar 2
resultaten. Dit zijn dus allemaal objecten waarin zowel *Gravensteen* als
*Aalst* voorkomen. Standaard wordt elk woord in het zoekvenster dus gezien als
een zoekterm en wordt er gezocht naar objecten waarin alle termen voorkomen. We
kunnen dit expliciet maken met de **AND (EN)** operator. Deze stellen we voor met een `+` 
teken. Dus `Gravensteen Aalst` is identiek aan `Gravensteen+Aalst`. Stel dat we
echter op zoek zijn naar iets over het *Gravensteen* of *Aalst*, dan kunnen we
de **OR (OF)** operator gebruiken. Deze stellen we voor met een `|` teken, ook gekend
als het pipe symbool. Dus `Gravensteen|Aalst` geeft ons alles waarin zowel
*Gravensteen* als *Aalst* voorkomen. De derde operator is de **NOT (NIET)** operator.
Deze stellen we voor met een `-` teken. Dus, als we alle objecten willen waarin
*Gravensteen* voorkomt, maar niet *Aalst*, dan zoeken we `Gravensteen -Aalst`.
Met deze drie operatoren, ook gekend als de booleaanse operatoren, kan je al héél 
véél doen.

Standaard zal de zoekmachine je zoektermen splitsen op basis van spaties, elk
apart woord is dus een aparte zoekterm. Soms is dit echter niet wat we willen.
Stel dat we willen zoeken naar de *Grote Markt* te *Aalst*. Als we zoeken naar
`Grote Markt Aalst`, dan krijgen we vrij veel zoekresultaten. Bovenaan staan
inderdaad een aantal panden aan de grote markt, maar we vinden helemaal achteraan wel 
[Paviljoen De Notelaer](https://inventaris.onroerenderfgoed.be/erfgoedobjecten/1996),
waarin de woorden *grote*, *markt* en *aalst* voorkomen. Dat komt omdat we nu 
gezocht hebben naar alle documenten waarin deze drie zoektermen voorkomen, ongeacht
hun volgorde of hoe dicht ze bij elkaar staan. Een zin als *De grote post te 
Oostende werd ooit bezocht door een kolenhandelaar uit Aalst die op zoek was naar de 
markt" is voor deze zoekopdracht even relevant als een zin als "Het huis aan de
Grote Markt te Aalst werd recent gerestaureerd". We verwachten echter die tweede zin 
sneller te kunnen vinden. We kunnen dit oplossen door expliciet aan te geven dat 
*grote* en *markt* bij elkaar horen door deze tussen **aanhalingstekens** plaatsen. 
Dus, met `"Grote Markt" Aalst` zoeken we niet 
meer naar drie zoektermen (*grote*, *markt*, *aalst*), maar naar twee zoektermen
(*grote markt*, *aalst*) die beiden als geheel moeten voorkomen. We krijgen al 
wat minder zoekresultaten en een object zoals het paviljoen van de Notelaer 
valt al weg.

Eens we met meerdere zoektermen beginnen te werken, willen we misschien wel
complexere combinaties van zoektermen toepassen ook. Stel dat we interesse
hebben in de *Vismarkt* van *Brugge* of *Gent*. Als we zoeken naar `vismarkt brugge
gent`, dan zoeken we objecten waarin alledrie termen samen voorkomen. Niet echt
wat we zochten, want die van Brugge maakt geen melding van die van Gent en die
van Gent niet van Brugge. Dus we krijgen geen van de door ons gewenste
vismarkten. We kunnen proberen met `vismarkt + brugge | gent` in de
veronderstelling dat we dan zoeken op `vismarkt` en `brugge` of `gent`. Nu
krijgen we heel veel resultaten. Dit komt omdat bepaalde operatoren voorrang 
hebben op andere (net zoals bij de wiskundige rekenregels). We hebben daardoor 
eigenlijk gezocht hebben op objecten over de *vismarkt* in *Brugge* (zeer weinig), 
of objecten in *Gent* (zeer veel). Dit kunnen we wel oplossen, door onze zoektermen 
te groeperen door middel van **haakjes** `()`. Zo kunnen
we zoeken  naar [`vismarkt + (brugge|gent)`]() om fiches te vinden waarin het
woord *vismarkt* voorkomt en ofwel *Brugge* of *Gent* voorkomen.

Ten slotte is het mogelijk dat we niet op zoek zijn naar een volledig woord, 
maar slechts naar een gedeelte. Dit doen we door een zogenaamde **wildcard** toe 
te voegen met behulp van een `*`.
Stel dat we iets zoeken over *gedenkstenen*, *gedenkplaten* of gelijkaardig, dan
kunnen we zoeken naar `gedenk*`. Dit levert ons alles op waarin een woord voorkomt
dat begint met *gedenk*. Dit kan prima gecombineerd worden met de andere operatoren
die we al besproken hebben. Met `gedenk* | herdenk*` komen we allerlei te weten over
herdenkingsbomen, gedenkstenen, gedenkplaten, herdenkingsmonumenten en meer.

```{warning}
Denk er wel aan dat het `*` teken enkel op het einde van een zoekterm kan gebruikt
worden, niet aan het begin van de zoekterm. Dit is nodig om de performantie van 
zoekopdrachten te kunnen garanderen. Indien je zoekt naar `*linde` zal je dus
geen herdenkingslinde vinden.
```

Als we alle mogelijkheden combineren kunnen we dus zoeken naar objecten waarin iets gezegd
wordt over visgraatverband of -motief, in Oost- of West-Vlaanderen, maar waarin
Brugge niet voorkomt met de volgende zoekopdracht: `visgraat*
(oost-vlaanderen|west-vlaanderen) -brugge`.

Misschien vraag je je af welke velden er nu juist doorzocht worden als je
full-text zoekt en hoe zwaar deze doorwegen in je zoekopdracht? In het 
bovenstaande voorbeeld zul je bijvoorbeeld objecten vinden waarin
Oost-Vlaanderen of West-Vlaanderen niet in de tekst voorkomen, maar wel in de
locatie omschrijving. Omdat het makkelijker werkt en aangeeft waar de nodige
accenten liggen, voegen we deze toch toe aan de full-text index. De velden die 
we full-text doorzoeken in volgorde van belang zijn: de tekst, de titel van de tekst, 
de korte beschrijving van het object (wat je te zien krijgt in een zoekresultaat),
provincie, gemeente, deelgemeente en straat namen, thesaurustermen en de naam
van het object zelf. Als je dus *vismarkt* zoekt, dan zal een object waarvan de
titel `vismarkt` is, hoger op de lijst staan dan een object waarvan `vismarkt`
ergens in de tekst voorkomt. We tonen wel alle objecten waarin `vismarkt`
voorkomt, tenzij het er meer dan 10.000 zijn (het maximale aantal
zoekresultaten).

We hopen dat het duidelijk is dat je met dezezoekmachine in de inventaris
krachtige full-text zoekopdrachten kunt uitvoeren eens je de mogelijkheden een
beetje onder de knie hebt. Onthou vooral dat je met full-text zoeken meestal
op zoek bent naar een klein aantal documenten en je het meest relevante wil
zien. Het totale aantal resultaten zegt je meestal niet zo veel, daarvoor ben
je beter af me exacte filters op zaken zoals een gemeente of een
thesaurusterm. Je kunt je full-text zoekopdrachten optimaliseren met de volgende 
operatoren:

- Meerdere zoektermen worden impliciet met AND gecombineerd, je kan dit
  expliciet maken met `+`
- Je kunt ze ook combineren met een OR combinatie via `|`
- Je kunt een term uitsluiten met de NOT operator via `-`
- Je kunt zoektermen combineren tot 1 zoekterm door de termen tussen `"` te
  plaatsen
- Je kunt de volgorde van operatoren aanpassen door `()` te gebruiken
- Je kunt zoeken op woorden die starten met een prefix door een `*` toe te
  voegen
