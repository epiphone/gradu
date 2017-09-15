# Gradu

Työkalu javascript-ohjelmiston automaattista (tai avustettua) modularisointia varten.

## Motivaatio

Miksi modularisointi? Modularisoinnin tarkoituksena on hallita järjestelmän kompleksisuutta muodostamalla
loogisia kokonaisuuksia ja hierarkioita (korkea koheesio), ja minimoida niiden välisiä riippuvuuksia (matala kytkentä).
Hyvin modularisoitu järjestelmä on helpompi ymmärtää ja ylläpitää.

Miksi Javascript? Pikaisen selauksen perusteella lähes kaikki olemassa oleva tutkimus ja
työkalut käsittelevät olio-ohjelmointia. Modularisointi on kuitenkin yhtälailla relevantti
ongelma myös Javascriptin kaltaisissa useampaa paradigmaa soveltavissa kielissä. Nykyiset
Javascriptin staattisen analyysin työkalut (jshint, jslint, ...) rajoittuvat lähinnä syntaksin tarkastamiseen.

## Tavoitteet

Konkreettinen joskin vielä hämärä esimerkki: ohjelmistoon on lisättävä jokin pätkä koodia.
Koodi on riippuvainen joukosta muita toiminnallisuuksia.
Minne koodi tulee sijoittaa, kun halutaan minimoida sen aiheuttama
lisäkompleksisuus? Koodi voi tässä ilmentyä vaikka funktiona, uutena moduulina, luokkana,
tiedostona. Vielä konkreettisemmin: editori esittää varoituksen kun tekemäsi
muokkaus rikkoo (tämä käsite on vielä täysin auki) ohjelmiston modularisointia ja ehdottaa parempia ratkaisuja.

## Menetelmät

Joitain suuntaa-antavia lähteitä kerätty [tänne](./refs.md). Tähän mennessä havaitsin kolme päällimmäistä tapaa tulkita
ohjelmiston modularisaatiota:

- strukturaalinen: koodi jäsennetään AST:ksi, poimitaan kutsut toisiin moduuleihin (import/export)
- semanttinen: analysoidaan muuttujien nimiä, kommentteja tms. tekstuaalista dataa
- historiallinen: analysoidaan versiohallinnan muutoshistoriaa; yhdessä muuttuvat koodinpätkät ovat toisistaan riippuvaisia

Näistä kahta ensimmäistä yhdistellään onnistuneesti muutamassa lähteessä. Voisin siis kuvitella
soveltavani ainakin koodin jäsentämistä, NLP-menetelmiä (topic modeling?)
ja/tai klusterointia tai muita koneoppimismenetelmiä.

## Ongelmia ja avoimia kysymyksiä

- Aihe on tietty vielä liian avoin ja laaja. Jonkinlainen tutkimuskysymys pitänee laatia.
- Miten arvioida työkalun toimivuutta? Mistä tiedetään ovatko ehdotetut modularisaatioratkaisut johdonmukaisia?
  - coupling/cohesion-metriikat?
  - kyselyt? mielellään ei
- Tehdäkö työkalu a) olemassa olevan modularisaation ymmärtämistä/visualisointa vai b) koko ohjelmiston automaattista uudelleen-modularisointia varten?
  - "software architecture recovery vs. automatic remodularization"
  - todennäköisesti johonkin tältä väliltä, mutta ei vielä varmuutta miten sijoittua tällä akselilla
  - ei tarkoitus pelkästään visualisoida (kai?), mutta jonkinlainen visualisaatio voi olla tarpeen (tai ainakin hyödyksi) ratkaisuja ehdottaessa
- Liian iso pala purtavaksi?
- ...
