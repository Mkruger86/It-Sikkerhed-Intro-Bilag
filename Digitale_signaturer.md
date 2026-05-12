<div align="center">

# Demonstration af Digital Signering

**Af**  
**Michael Krüger Andersen**

**Værktøj:** `openSSL` & `Kali Linux`

</div>

---

*I denne sidste del af kryptografi "serien", vil jeg binde elementerne sammmen og yderlige binde klartekst filen til et digitalt signatur, som er det endelig led i en moderne kryptografisk proces* 
#### I et realistisk kommunikationsforløb bruges modtagerens offentlige nøgle til kryptering, mens afsenderens private nøgle bruges til signering. Det RSA-nøglepar, der tidligere blev oprettet i krypteringsdemonstrationen, kan derfor forstås som modtagerens nøglepar. I denne demonstration oprettes et særskilt RSA-nøglepar til afsenderen, som bruges til den digitale signatur.

---

# 1. Oprettelse af arbejdsmappe

---

# 2. Kopiering af klartekstfilen

---

# 3. Generering af afsenderens private RSA-nøgle


#### `genpkey`

> Genererer nøglemateriale. Her oprettes afsenderens private nøgle, som senere bruges til at fremstille den digitale signatur.

#### `-algorithm RSA`

> Vælger RSA som algoritme for afsenderens signaturnøglepar. Nøglerne bruges her i signaturprocessen, hvor den private nøgle danner signaturen, mens den offentlige nøgle gør det muligt for modtageren at kontrollere den.

#### `-out ~/Signaturer/afsender_privat_noegle.pem`

> Gemmer afsenderens private nøgle i filen afsender_privat_noegle.pem. Nøglen skal beskyttes, fordi adgang til den gør det muligt at danne signaturer, der fremstår som afsenderens.

#### `-pkeyopt rsa_keygen_bits:2048`

> Sætter RSA-nøglens størrelse til 2048 bit. Svarer her til den størrelse, der tidligere blev brugt.

---

# 4. Udledning af afsenderens offentlige RSA-nøgle

#### `pkey`

> Behandler nøglefiler. Her læses afsenderens private nøgle, og den tilhørende offentlige nøgle skrives ud som en separat fil.

#### `-in ~/Signaturer/afsender_privat_noegle.pem`

> Bruger afsenderens private nøgle som input til udledningen af den offentlige nøgle.

#### `-pubout`

> Skriver den offentlige nøgle ud. I et kommunikationsforløb skal modtageren have denne nøgle for at kunne verificere afsenderens signatur.

#### `-out ~/Signaturer/afsender_offentlig_noegle.pem`

> Gemmer den offentlige nøgle i filen afsender_offentlig_noegle.pem. Nøglen kan deles med modtageren og bruges til at kontrollere, om signaturen passer til afsenderens private nøgle.

---

# 5. Oprettelse af digital signatur

#### `openssl dgst`

> Beregner først en hashværdi af beskeden og bruger den herefter som grundlag for signaturen. Det er derfor ikke hele beskeden, der signeres direkte, men dens kryptografiske fingeraftryk.

#### `-sha256`

> Vælger SHA-256 til hashberegningen. Den resulterende hashværdi repræsenterer beskedens præcise indhold, så selv en lille ændring i teksten giver et andet signaturgrundlag.

#### `-sign ~/Signaturer/afsender_privat_noegle.pem`

> Bruger afsenderens private nøgle til at danne signaturen. Det er denne anvendelse af den private nøgle, der knytter signaturen til afsenderen.

#### `-sigopt rsa_padding_mode:pss`

> Vælger RSA-PSS som signaturmetode. PSS er den moderne signaturtilpasning til RSA i denne sammenhæng og bruges til at danne signaturen på en måde, der er egnet til praktisk anvendelse.

#### `-out ~/Signaturer/signatur.bin`

> Gemmer den digitale signatur i binært format. Signaturen ligger som en separat fil og erstatter ikke selve beskeden.

#### `~/Signaturer/besked.txt`

> Beskeden, der signeres. Signaturen binder sig til dette konkrete filindhold. Ændres indholdet bagefter, passer signaturen ikke længere.

---

# 6. Verifikation af den digitale signatur


#### `openssl dgst`

> Beregner på ny en SHA-256-hash af beskeden og sammenholder den med signaturen. Verifikationen kontrollerer dermed, om signaturen passer til både beskedens aktuelle indhold og afsenderens offentlige nøgle.

#### `-sha256`

> Bruger samme hashfunktion som ved signeringen. Signering og verifikation skal følge samme beregningsgrundlag.

#### `-verify ~/Signaturer/afsender_offentlig_noegle.pem`

> Bruger afsenderens offentlige nøgle til at kontrollere signaturen. Modtageren får dermed mulighed for at afgøre, om signaturen passer til afsenderens nøglepar.

#### `-sigopt rsa_padding_mode:pss`

> Bruger samme RSA-PSS-metode som ved signeringen. Verifikationen skal tolke signaturen efter den samme signaturstruktur, som blev brugt ved oprettelsen.

#### `-signature ~/Signaturer/signatur.bin`

> Udpeger den signaturfil, der skal kontrolleres.

#### `~/Signaturer/besked.txt`

> Beskeden, som signaturen verificeres imod. Indholdet skal være uændret siden signeringstidspunktet.

#### *Resultatet viser, at signaturen passer til beskeden og til afsenderens offentlige nøgle.*

---

# 7. Verifikation med forkert offentlig nøgle

#### `openssl genpkey -algorithm RSA -out ~/Signaturer/forkert_privat_noegle.pem -pkeyopt rsa_keygen_bits:2048`

> Opretter et nyt RSA-nøglepar, som ikke hører sammen med afsenderens signaturnøgle.

##### `openssl pkey -in ~/Signaturer/forkert_privat_noegle.pem -pubout -out ~/Signaturer/forkert_offentlig_noegle.pem`

> Udleder den offentlige nøgle til det forkerte nøglepar.

##### `-verify ~/Signaturer/forkert_offentlig_noegle.pem`

> Forsøger at verificere signaturen med en offentlig nøgle, der ikke passer til den private nøgle, som dannede signaturen

#### *Fejler da signaturen kan kun verificeres med den offentlige nøgle, der hører til den private nøgle, som blev brugt ved signeringen.*
