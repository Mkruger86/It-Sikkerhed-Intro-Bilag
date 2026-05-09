# Bilag 1 – Foranstaltningstyper

## Fast struktur

1. Generel funktion i risikohåndteringen  
2. Placering i hændelsesforløbet  
3. Eksempler på relevante foranstaltninger  
4. Relation til etablerede grundbegreber  
5. Anvendelse i Jordløse-casen  

---

## Preventive / Forebyggende

1. Reducerer sandsynligheden for, at en trussel kan udnytte en sårbarhed. Foranstaltningen skal være etableret på forhånd og mindske muligheden for uautoriseret adgang, misbrug af rettigheder eller menneskelige fejl.

2. Før en sikkerhedshændelse indtræffer.

3. Skærmlås, adgangskontrol, flerfaktorgodkendelse, rettighedsstyring, adgang efter arbejdsbehov, clear screen-praksis og krav om særskilt godkendelse ved administrative handlinger.

4. Knytter sig især til **sårbarhed** og **sandsynlighed**. Den forebyggende foranstaltning reducerer det forhold, en trussel kan udnytte, og mindsker dermed sandsynligheden for brud på **fortrolighed**, **integritet** eller **tilgængelighed**.

5. I Jordløse-scenariet er sårbarheden, at Hans Knudsen forlader en computer med aktiv session, mens hans konto har adgang til netværksdrev og brede IT-rettigheder. Forebyggende foranstaltninger skal hindre, at en elev kan bruge den aktive session til at åbne prøvemateriale, ændre dokumenter eller påvirke delinger på Windows-serveren.

---

## Reductive / Begrænsende

1. Reducerer konsekvensen, hvis en sikkerhedshændelse indtræffer. Foranstaltningen forhindrer ikke nødvendigvis hændelsen, men begrænser hvor stor skade en realiseret hændelse kan medføre.

2. Før eller under en sikkerhedshændelse.

3. Adskillelse af adgangsområder, begrænsede rettigheder, skrivebeskyttelse, versionshistorik, segmentering, adgangsgrupper og begrænsning af administrative funktioner fra almindelige brugersessioner.

4. Knytter sig især til **konsekvens**. Hændelsen kan stadig indtræffe, men skadeomfanget reduceres. Har relation til **integritet**, når ændringer begrænses, og til **tilgængelighed**, når påvirkning af adgang eller drift afgrænses.

5. Hvis eleven får adgang til Hans Knudsens aktive session, bør én misbrugt session ikke give fri adgang til prøvemateriale, almindelige undervisningsmapper, administrative drev og rettighedsstyring på samme tid. Begrænsende foranstaltninger skal derfor indsnævre, hvad eleven kan læse, ændre eller afbryde.

---

## Detective / Opklarende

1. Gør uønsket aktivitet synlig, så en sikkerhedshændelse kan opdages, dokumenteres og undersøges. Foranstaltningen giver grundlag for at fastslå, hvad der er sket, hvornår det er sket, og hvilke systemer eller data der er berørt.

2. Under eller kort efter en sikkerhedshændelse.

3. Logning, overvågning, alarmering, central logopsamling, registrering af rettighedsændringer, registrering af filændringer og beskyttelse af logs mod ændring eller sletning.

4. Knytter sig til **trussel**, **trusselsaktør**, **sårbarhed** og **risiko**, fordi hændelsen først kan vurderes præcist, når der findes oplysninger om handling, tidspunkt, bruger og berørte data. Understøtter vurdering af brud på **fortrolighed**, **integritet** og **tilgængelighed**.

5. I Jordløse-scenariet sker elevens handlinger fra Hans Knudsens aktive session. Hvis systemet kun viser, at Hans’ konto har åbnet eller ændret filer, bliver hændelsen vanskelig at gennemskue. Opklarende foranstaltninger skal derfor registrere adgang til prøvemateriale, ændring af dokumenter, ændring af delinger og brug af administrative rettigheder.

---

## Responsive / Responsiv

1. Fastlægger den umiddelbare håndtering, når en sikkerhedshændelse er mistænkt eller konstateret. Foranstaltningen skal sikre, at relevante oplysninger bevares, at ansvarlige personer inddrages, og at hændelsen håndteres i en kontrolleret rækkefølge.

2. Efter mistanke eller konstatering af en sikkerhedshændelse, før egentlig genoprettelse.

3. Hændelsesprocedure, eskalering, sikring af relevante oplysninger, midlertidig spærring af berørte konti, dokumentation af hændelsesforløb og beslutningsprocedure for videre håndtering.

4. Knytter sig til **risiko** og **konsekvens**, fordi reaktionen skal styre følgerne af en hændelse, der allerede er mulig eller konstateret. Understøtter afklaring af **trussel**, **trusselsaktør** og **sårbarhed**, fordi håndteringen skal bevare grundlaget for at forstå hændelsen.

5. Hvis skolen opdager, at prøvemateriale er åbnet, ændret, eller at fællesdrevet har været utilgængeligt, skal der være en fast fremgangsmåde for at sikre sessionen, bevare logs, afklare prøvens gyldighed og beslutte, om materialet fortsat kan bruges.

---

## Recovery / Genoprettende

1. Genskaber normal drift, korrekt adgang eller korrekt datagrundlag efter en sikkerhedshændelse. Foranstaltningen skal bringe systemer, filer eller adgangsforhold tilbage til en kendt og brugbar tilstand.

2. Efter den første håndtering af sikkerhedshændelsen.

3. Backup, gendannelse fra versionshistorik, genetablering af adgangsrettigheder, genetablering af delte mapper, kontrol af adgang og verifikation af gendannede filer.

4. Knytter sig især til **tilgængelighed** og **integritet**. Tilgængelighed genskabes, når legitime brugere igen kan tilgå nødvendige data eller systemer. Integritet genskabes, når filer, rettigheder eller systemtilstand bringes tilbage til korrekt udgangspunkt.

5. Hvis prøvefilen er ændret, eller hvis delingen af lærernes fællesdrev har været deaktiveret, skal skolen kunne genskabe den korrekte prøveversion, genetablere delingen og kontrollere, at undervisere og relevant personale igen kan tilgå de nødvendige mapper.

---

## Corrective / Korrigerende

1. Retter den sårbarhed, fejlkonfiguration eller utilstrækkelige praksis, der gjorde hændelsen mulig eller forværrede dens konsekvens. Foranstaltningen skal mindske risikoen for gentagelse.

2. Efter sikkerhedshændelsen, når årsag og relevante sårbarheder er identificeret.

3. Ændring af rettighedsmodel, fjernelse af unødige administratorrettigheder, særskilt administrativ godkendelse, justering af adgangsgrupper, ændring af procedurer og kontrol ved ændring af følsomme dokumenter.

4. Knytter sig til **sårbarhed**, **sandsynlighed** og **konsekvens**. Den korrigerende foranstaltning reducerer den sårbarhed eller praksis, der muliggjorde hændelsen, og kan dermed både mindske sandsynligheden for gentagelse og begrænse skade ved fremtidige hændelser.

5. Jordløse-scenariet viser en sårbar kombination af fysisk adgang, aktiv session, netværksdrev og brede rettigheder hos Hans Knudsen. Korrigerende foranstaltninger skal derfor ændre rettighedsmodel, sessionhåndtering eller praksis for prøvemateriale, så samme type misbrug ikke fortsætter som uændret risiko.

---

## Evaluation / Evaluerende

1. Vurderer, om de valgte foranstaltninger virker efter hensigten, og om risikovurderingen fortsat er dækkende. Foranstaltningen giver grundlag for at fastholde, ændre eller supplere risikohåndteringen.

2. Efter implementering af foranstaltninger og løbende efter hændelser, øvelser eller ændringer i systemer og arbejdsgange.

3. Gennemgang af adgangsrettigheder, test af backup og gendannelse, kontrol af logning, stikprøvekontrol, øvelser i hændelseshåndtering og opdatering af risikovurdering.

4. Knytter sig til **risiko**, **sandsynlighed** og **konsekvens**, fordi evalueringen vurderer, om risikobilledet faktisk er ændret. Har samtidig relation til **fortrolighed**, **integritet** og **tilgængelighed**, fordi foranstaltningernes virkning vurderes ud fra de sikkerhedshensyn, de skal beskytte.

5. Skolen skal kunne efterprøve, om skærmlås, adgangsbegrænsning, logning, backup, gendannelse og hændelsesprocedure faktisk reducerer risikoen ved aktive sessioner og brede rettigheder. Hvis de ikke virker i praksis, bør risikovurderingen og de valgte foranstaltninger justeres.
