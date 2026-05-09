# Klassifikation af foranstaltninger

---

## ⏱️ 1. **Preventive / Forebyggende** - *Før en sikkerhedshændelse indtræffer.*
- #### 🧭 Generel funktion i risikohåndteringen
> Reducerer sandsynligheden for, at en trussel kan udnytte en sårbarhed. Foranstaltningen placeres før hændelsen og skal gøre uautoriseret adgang, misbrug af rettigheder eller menneskelige fejl mindre sandsynlige.

- #### 🧩 Eksempler på relevante foranstaltninger 
> Skærmlås, adgangskontrol, flerfaktorgodkendelse, rettighedsstyring, adgang efter arbejdsbehov, clear screen-praksis og krav om særskilt godkendelse ved administrative handlinger.

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig direkte til **sårbarhed** og **sandsynlighed**. Den forebyggende foranstaltning reducerer det forhold, truslen kan udnytte, og mindsker dermed sandsynligheden for brud på **fortrolighed**, **integritet** eller **tilgængelighed**

- #### 🏫 Anvendelse i Jordløse-casen 
> I Jordløse-scenariet er sårbarheden, at Hans Knudsen forlader en computer med aktiv session, mens hans konto har adgang til netværksdrev og brede IT-rettigheder. 

---

## ⏱️ 2. **Reductive / Begrænsende:** - *Før eller under en sikkerhedshændelse.*
- #### 🧭 Generel funktion i risikohåndteringen
> Reducerer konsekvensen, hvis en sikkerhedshændelse indtræffer. Foranstaltningen forudsætter ikke, at hændelsen altid kan forhindres, men begrænser rækkevidden af misbruget og den skade, der kan opstå

- #### 🧩 Eksempler på relevante foranstaltninger 
> Adskillelse af adgangsområder, begrænsede rettigheder, skrivebeskyttelse, versionshistorik, segmentering, adgangsgrupper og begrænsning af administrative funktioner fra almindelige brugersessioner

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig især til **konsekvens**. Hændelsen kan stadig indtræffe, men skadeomfanget reduceres. Har relation til **integritet**, når ændringer begrænses, og til **tilgængelighed**, når påvirkning af adgang eller drift afgrænses.

- #### 🏫 Anvendelse i Jordløse-casen 
> Hvis eleven får adgang til Hans Knudsens aktive session, bør én misbrugt session ikke give fri adgang til prøvemateriale, almindelige undervisningsmapper, administrative drev og rettighedsstyring på samme tid. Begrænsende foranstaltninger skal derfor indsnævre, hvad eleven kan læse, ændre eller afbryde.

---

## ⏱️ 3. **Detective / Opklarende:** - *Under eller kort efter en sikkerhedshændelse.*
- #### 🧭 Generel funktion i risikohåndteringen
> Gør uønsket aktivitet synlig, så en sikkerhedshændelse kan opdages, dokumenteres og undersøges. Foranstaltningen standser ikke nødvendigvis hændelsen, men skaber grundlag for at fastslå, hvad der er sket.

- #### 🧩 Eksempler på relevante foranstaltninger 
> Logning, overvågning, alarmering, central logopsamling, registrering af rettighedsændringer, registrering af filændringer og beskyttelse af logs mod ændring eller sletning.

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig til **trussel**, **trusselsaktør**, **sårbarhed** og **risiko**, fordi hændelsen først kan vurderes præcist, når der findes oplysninger om handling, tidspunkt, bruger og berørte data. Understøtter vurdering af brud på **fortrolighed**, **integritet** og **tilgængelighed**.

- #### 🏫 Anvendelse i Jordløse-casen 
> Elevens handlinger sker fra Hans Knudsens aktive session. Hvis systemet kun viser, at Hans’ konto har åbnet eller ændret filer, bliver hændelsen vanskelig at gennemskue. Opklarende foranstaltninger skal derfor registrere adgang til prøvemateriale, ændring af dokumenter, ændring af delinger og brug af administrative rettigheder.

---

## ⏱️ 4. **Responsive / Responsiv:** - *Efter mistanke eller konstatering af en sikkerhedshændelse, før egentlig genoprettelse.*

- #### 🧭 Generel funktion i risikohåndteringen
> Sikrer en fast reaktion, når en sikkerhedshændelse er mistænkt eller konstateret. Foranstaltningen skal give en kendt fremgangsmåde for, hvem der handler, hvad der sikres, og hvilke beslutninger der skal træffes.

- #### 🧩 Eksempler på relevante foranstaltninger 
> Hændelsesprocedure, eskalering, sikring af relevante oplysninger, midlertidig spærring af berørte konti, dokumentation af hændelsesforløb og beslutningsprocedure for videre håndtering.

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig til **risiko** og **konsekvens**, fordi reaktionen skal styre følgerne af en hændelse, der allerede er mulig eller konstateret. Understøtter afklaring af **trussel**, **trusselsaktør** og **sårbarhed**, fordi håndteringen skal bevare grundlaget for at forstå hændelsen.

- #### 🏫 Anvendelse i Jordløse-casen 
> Hvis skolen opdager, at prøvemateriale er åbnet, ændret eller at fællesdrevet har været utilgængeligt, skal der være en fast fremgangsmåde for at sikre sessionen, bevare logs, afklare prøvens gyldighed og beslutte, om materialet fortsat kan bruges.

---

## ⏱️ 5. **Recovery / Genoprettende:** - *Efter den første håndtering af sikkerhedshændelsen.*
- #### 🧭 Generel funktion i risikohåndteringen
> Genskaber normal drift, korrekt adgang eller korrekt datagrundlag efter en sikkerhedshændelse. Foranstaltningen skal bringe systemer, filer og adgange tilbage til en brugbar og kontrolleret tilstand.

- #### 🧩 Eksempler på relevante foranstaltninger 
> Backup, gendannelse fra versionshistorik, genetablering af adgangsrettigheder, genetablering af delte mapper, kontrol af adgang og verifikation af gendannede filer.

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig især til **tilgængelighed** og **integritet**. Tilgængelighed genskabes, når legitime brugere igen kan tilgå nødvendige data eller systemer. Integritet genskabes, når filer, rettigheder eller systemtilstand bringes tilbage til korrekt udgangspunkt.

- #### 🏫 Anvendelse i Jordløse-casen 
> Hvis prøvefilen er ændret, eller hvis delingen af lærernes fællesdrev har været deaktiveret, skal skolen kunne genskabe den korrekte prøveversion, genetablere delingen og kontrollere, at undervisere og relevant personale igen kan tilgå de nødvendige mapper.

---

## ⏱️ 6. **Corrective / Korrigerende:** - *Efter sikkerhedshændelsen, når årsag og relevante sårbarheder er identificeret.*
- #### 🧭 Generel funktion i risikohåndteringen
> Retter den sårbarhed, fejlkonfiguration eller utilstrækkelige praksis, der gjorde hændelsen mulig eller forværrede dens konsekvens. Foranstaltningen skal mindske risikoen for gentagelse.

- #### 🧩 Eksempler på relevante foranstaltninger 
> Ændring af rettighedsmodel, fjernelse af unødige administratorrettigheder, særskilt administrativ godkendelse, justering af adgangsgrupper, ændring af procedurer og kontrol ved ændring af følsomme dokumenter.

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig til **sårbarhed**, **sandsynlighed** og **konsekvens**. Den korrigerende foranstaltning reducerer den sårbarhed eller praksis, der muliggjorde hændelsen, og kan dermed både mindske sandsynligheden for gentagelse og begrænse skade ved fremtidige hændelser.

- #### 🏫 Anvendelse i Jordløse-casen 
> Sårbar kombination af fysisk adgang, aktiv session, netværksdrev og brede rettigheder hos Hans Knudsen. Korrigerende foranstaltninger skal derfor ændre rettighedsmodel, sessionhåndtering eller praksis for prøvemateriale, så samme type misbrug ikke fortsætter som uændret risiko..

---

## ⏱️ 7. **Evaluation / Evaluerende:** - *Efter implementering af foranstaltninger og løbende efter hændelser, øvelser eller ændringer i systemer og arbejdsgange.*
- #### 🧭 Generel funktion i risikohåndteringen
> Vurderer om valgte foranstaltninger virker efter hensigten, og hvorvid risikovurderingen fortsat er dækkende. Foranstaltningen skal give grundlag for at fastholde, redigere eller supplere risikohåndteringen.

- #### 🧩 Eksempler på relevante foranstaltninger 
> Gennemgang af adgangsrettigheder, test af backup og gendannelse, kontrol af logning, stikprøvekontrol, øvelser i hændelseshåndtering og opdatering af risikovurdering.

- #### 🔗 Relation til etablerede grundbegreber 
> Knytter sig til **risiko**, **sandsynlighed** og **konsekvens**, fordi evalueringen vurderer, om risikobilledet faktisk er ændret. Har samtidig relation til **fortrolighed**, **integritet** og **tilgængelighed**, fordi foranstaltningernes virkning vurderes ud fra de sikkerhedshensyn, de skal beskytte.

- #### 🏫 Anvendelse i Jordløse-casen 
> Skolen skal kunne efterprøve, om skærmlås, adgangsbegrænsning, logning, backup, gendannelse og hændelsesprocedure faktisk reducerer risikoen ved aktive sessioner og brede rettigheder. Hvis de ikke virker i praksis, bør risikovurderingen og de valgte foranstaltninger justeres.

---
