# Aihe A: web-sovelluksen migraatio FaaS-alustaan

## Motivaatio

Serverless- tai Function as a Service-alusta on pilvilaskenta-alusta lyhytkestoisille ja tilattomille sovelluksille jotka skaalautuvat automaattisesti ja joita laskutetaan varsinaisen käytön mukaan millisekuntien tarkkuudella. Toisin kuin SaaS- ja PaaS-alustat joissa sovellus on aina päällä, FaaS-sovellus käynnistetään ja puretaan joka tapahtuman yhteydessä täysin ns. on-demand, minkä seurauksena myös skaalautuminen ja laskutus toimii on-demand-periaatteella. 

![https://specify.io/concepts/serverless-baas-faas](https://specify.io/assets/serverless-automation-7265d1b1cc7ae92e9559995db6dd680fce120ab97f65a5c70edbd7fa71e41acd.png)
[lähde](https://specify.io/concepts/serverless-baas-faas)

FaaS-alustan kaksi päällimmäisintä hyötyä ovat kehitystyön tuottavuus (fokus toiminnallisuuksiin infrasta huolehtimisen sijaan) sekä potentiaaliset säästöt hostaus-kuluissa.

> I don't have to manage a virtual machine, operating system, patch management, scaling service, load balancing, availability, fault tolerance, provisioning, anti-virus, anti-malware, vulnerability scanning, continuous monitoring, access control, rightsizing, server tuning, intrusion detection, hardware affinity, OS dependencies [...] and I only pay for what I use ([Groat & Lu, 2017](https://www.slideshare.net/AmazonWebServices/serverless-design-patterns-for-rethinking-traditional-enterprise-application-approaches-aws-public-sector-summit-2017))

Nämä hyödyt huomioiden on aiheellista selvittää millainen työ on siirtää olemassaoleva sovellus FaaS-alustalle ja mitä hyötyä siitä on. Potentiaalisia **tutkimuskysymyksiä** (tai tutkielmassa ainakin sivuttavia aiheita) ovat ainakin
- miksi web-sovellus kannattaa siirtää FaaS-alustalle?
- miten web-sovellus siirretään FaaS-alustalle?
  - miten ja kuinka paljon sovellusta tulee muuttaa?
  - kuinka työlästä muuttaminen on?
- lopputuloksen arviointi, ts. miten web-sovelluksen siirtäminen FaaS-alustalle vaikuttaa sen laatuun?
  - ylläpitokustannukset
  - suorituskyky, ylläpidettävyys ym. laadulliset ominaisuudet

## Näkökulmia tutkielmaan

- miten sovellusta tulee muuttaa? **tapahtumapohjaisuus**, uudelleenmodularisointi, ulkoiset palvelut...?
  - arkkitehtuurin kannalta
  - matalammalla tasolla
- kuinka paljon voidaan säästää?
- kuinka muuttaa kehitystyötä koodaajan näkökulmasta? devops -> no-op?
  - lokaalin kehityksen helppous?
  - debuggaus, testaus, monitorointi, loggaaminen
  - > "We use Lambda primarily to improve developer efficiency and to allow dev teams to own their own operations end-to-end, with cost efficiency only a secondary goal. It's been great for that as it's a small enough thing to integrate with that any given developer can learn the entire operations stack (for their team's services) well enough to work on it themselves."
- pätevätkö samat ongelmat kuin mikropalveluissa tai hajautetuissa jarjestelmissa ylipaatansa? overhead, distributed transactions, ...
- cold starts, vendor lock-in ym. tyypilliset serverless-ongelmat?
- tukeeko serverless hyviä arkkitehtuurisuunnittelutapoja?
  - > Different constraints drive different design choices; historically good architecture optimized for what you've got, forgetting principles like isolation and decoupling. With Lambda there's no more financial incentive to bundle services
- fat vs thin lambdas
- migraatio pala kerrallaan vai kaikki samalla?
- lopputuloksena enemmän vai vähemmän koodia?
  - >  A lot of the infra code is gone
- tietoturva?
- lähtökohtien huomioiminen: esim. PaaS-alustalle kehitetyn mikroarkkitehtuuri- ja container-tekniikoita hyödyntävän järjestelmän vs. omalla raudalla hostatun vanhan PHP-sovelluksen siirtäminen FaaS:iin (tacit.space on jotain siltä väliltä) - ensimmäinen luultavasti helpompi mutta jälkimmäisellä enemmän hyödyttävää. Kokonaisen sukupolven (PaaS) "skippaaminen"?

## Siirrettävä sovellus

https://tacit.space/ on moderni web-sovellus muistiinpanojen tekemiseen. Sovellus on melko laaja (noin 30k riviä Javascript- ja Typescript-koodia) ja sitä löytyy useita web-sovelluksille tyypillisiä ominaisuuksia: REST API, single page app-tyylinen web-käyttöliittymä, monimutkainen roolipohjainen autorisaatio, reaaliaikaisia ominaisuuksia (websocket), email- ja SMS-notifikaatiot, luottokorttimaksut, erilliset admin-työkalut, riippuvuuksia ulkopuolisiin palveluihin jne. Sovellus on jaoteltu frontend- ja backend-komponentteihin, joista jälkimmäinen on edelleen jaoteltu kouralliseen eri palveluita.

Tacit.spacen tapauksessa FaaS-alustalle siirtämisen perusteena ovat skaalautuvuus, rahalliset säästöt sekä kehitystyön fokus infrasta ominaisuuksiin.

## Ongelmia ja avoimia kysymyksiä

- Tarkempi tutkimuskysymys vielä hakusessa
- Melko vähän tutkimusaineistoa. Vähemmän formaaleja artikkeleita, blogitekstejä, konferenssiesityksiä kylläkin paljon; kelpaavatko gradun lähteiksi?
- Onko tämän tyyppisessä gradussa tarkoitus tehdä suosituksia raportoinnin lisäksi? Edellä listatut alustavat tutkimuskysymykset ovat melko subjektiivisia. Joitakin absoluuttisia mittareita toki on (hostaus-kustannukset, koodin määrä), mutta nämäkin ovat jokseenkin sovelluskohtaisia.
- Seminaarissa oli puhetta insinöörityömäisistä graduista. Onko tämä aihe liikaa sen sorttinen?
- Muunnettavalla sovelluksella on tällä hetkellä vain muutamia kymmeniä aktiivisia käyttäjiä. Kulujen ja skaalautuvuuden vertailu ilman varsinaista kuormitusta voi olla hankalaa. Avuksi simuloidut testit tai muut arviot?

## Aineistoa

- Tutkimusartikkeleita kerätty [tänne](./refs.md)
- blogiartikkelit ym.
  - https://martinfowler.com/articles/serverless.html
- konferenssit:
  - GOTO 2017 https://gotocph.com/
    - *Serverless: the future of architecture*
      - lambda is to computing what S3 is to storage
      - cannot under- or overprovision
      - embrace 3rd party services; compute as glue
      - write stateless single-purpose funcs; 1 or 0 data transformations (?)
      - design push-based event-driven pipelines
      - create thicker more powerful front-ends (leveraging JWT for auth to remove middle man); UI might talk directly with your db, protected actions as lambdas (?)
      - serverless monolith vs micro: each service has its own db and API
      - from monolith to micro without thinking about infra
    - *Designing for the serverless age*
      - technical vs financial view
      - many things we take for granted are now solutions to constraints that no longer apply
      - 66% savings moving from Heroku; bigger savings possible when moving from less cost-effective platforms
      - pay not for reserved capability but for milliseconds, actual usage
      - get a bunch of stuff automatically: monitoring logging security etc. NoOps
      - optimize for quick start over quick failover; lazy load everything
      - cbeaper to run expensive experiments
      - play arbitrage with different pricing models
      - no need for gatekeepers (server between user and db for example), use request-level auth. Three tier adds latency and costs
      - push to client, keep state in users' browsers
  - EMIT 2017 http://www.emitconference.com/
  - Serverlessconf (https://serverless.com/blog/serverless-conf-2017-nyc-recap/)


# Aihe B: Javascript-lähdekoodin avustettu modularisointi

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
