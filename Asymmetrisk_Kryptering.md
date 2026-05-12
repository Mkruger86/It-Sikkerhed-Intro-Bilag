<div align="center">

# Demonstration af Asymmetrisk kryptering (RSA)

**Af**  
**Michael Krüger Andersen**

**Værktøj:** `openSSL` & `Kali Linux`

</div>

---

*Fortsættelse af krypteringsalgoritmer demonstration. Referer til https://github.com/Mkruger86/It-Sikkerhed-Intro-Bilag/blob/main/Symmetrisk_Kryptering.md for symmetriske version. Jeg har forsøgt generelt at gå igennem alle kommandoer slavisk, samt tilkoblet kryptografisk betydning iht. brugen, hvis det nu skulle gå i glemmebogen senere hen. Desuden jeg i denne version været lidt mere grundigt med billede dokumentation

---

# 1. Oprettelse af arbejdsmappe
<img width="342" height="106" alt="image" src="https://github.com/user-attachments/assets/21474cd8-f593-44bc-a65a-85b73415158f" />

<img width="109" height="150" alt="image" src="https://github.com/user-attachments/assets/a42ed244-6927-4854-9584-79a526963c30" />

---

# 2. Generation af privat RSA-nøgle
<img width="975" height="373" alt="image" src="https://github.com/user-attachments/assets/f5fe4ac4-6b24-46cf-b2e5-bf8db07d2139" />

<img width="140" height="105" alt="image" src="https://github.com/user-attachments/assets/169be74b-ace2-4b6c-b242-40ba914d4ad3" />

#### `GENPKEY`

> Genererer nøglemateriale. Her oprettes modtagerens private RSA-nøgle, som udgør den hemmelige del af nøgleparret. Nøglen skal forblive hos modtageren, fordi den senere bruges til at dekryptere chiffertekst, der er krypteret med den tilhørende offentlige nøgle.

#### `-ALGORITHM RSA`

> Vælger RSA som algoritme for nøglematerialet. RSA bruger et nøglepar med en offentlig og en privat del, hvor den offentlige nøgle kan bruges til kryptering, mens kun den tilhørende private nøgle kan dekryptere resultatet. Sikkerheden bygger på, at den private nøgle ikke praktisk kan udledes fra den offentlige nøgle.

#### `-OUT ~/RSA/PRIVAT_NOEGLE.PEM`

> Gemmer den private nøgle i filen privat_noegle.pem. Filen indeholder den kritiske hemmelighed i nøgleparret og må ikke deles. Hvis andre får adgang til denne fil, kan de dekryptere beskeder, der er krypteret med nøgleparrets offentlige nøgle.

#### `-PKEYOPT RSA_KEYGEN_BITS:2048`

> Sætter RSA-nøglens størrelse til 2048 bit. Nøglestørrelsen har betydning for sikkerheden, fordi større RSA-nøgler gør det vanskeligere at angribe nøgleparret. Større nøgler giver samtidig langsommere RSA-operationer.

---

# 3. Udledning af offentlig nøgle fra den private nøgle
<img width="632" height="66" alt="image" src="https://github.com/user-attachments/assets/24fa35ae-85c9-40fd-82b7-6b4a8d6da1a2" />

<img width="141" height="123" alt="image" src="https://github.com/user-attachments/assets/ca7d2bc6-6a9a-4428-9b8f-ba0d0e5eee4e" />


#### `PKEY`

> Behandler nøglefiler. Her læses den private RSA-nøgle, og den tilhørende offentlige nøgle skrives ud som en separat fil.

#### `-IN ~/RSA/PRIVAT_NOEGLE.PEM`

> Bruger den private nøgle som input. Den private nøgle indeholder de nødvendige oplysninger til, at den offentlige nøgle kan udledes. Den offentlige nøgle kan derimod ikke bruges til praktisk at genskabe den private nøgle.

#### `-PUBOUT`

> Får OpenSSL til at skrive den offentlige nøgle ud. Den offentlige nøgle kan deles med andre og bruges til at kryptere beskeder til indehaveren af den private nøgle. Den offentlige nøgle kan ikke selv dekryptere de beskeder, den bruges til at kryptere.

#### `-OUT ~/RSA/OFFENTLIG_NOEGLE.PEM`

> Gemmer den offentlige nøgle i filen offentlig_noegle.pem. Den offentlige nøgle kan deles, men afsenderen skal bruge den rigtige offentlige nøgle. Hvis en besked krypteres med en forkert eller falsk offentlig nøgle, kan den kun dekrypteres med den private nøgle, der hører til den forkerte offentlige nøgle.

---

# 4. Oprettelse af klartekstfil
<img width="406" height="76" alt="image" src="https://github.com/user-attachments/assets/0e648eed-009a-4f3d-9a70-b8e249db099e" />

<img width="87" height="91" alt="image" src="https://github.com/user-attachments/assets/35932f58-612e-4984-bbaf-82da16c83d60" />

---

# 5. Kryptering med offentlig RSA-nøgle
<img width="619" height="251" alt="image" src="https://github.com/user-attachments/assets/dfb46b14-ee46-4b1f-a1c2-c53015ac6af8" />

<img width="117" height="104" alt="image" src="https://github.com/user-attachments/assets/521c597d-4e66-440b-9b61-167d1735858a" />

#### `PKEYUTL`

> Udfører operationer med offentlige og private nøgler. Her bruges kommandoen til RSA-kryptering. RSA bruges normalt til små datamængder eller til at beskytte en symmetrisk nøgle, mens større datamængder typisk krypteres med fx AES.

#### `-ENCRYPT`

> Starter krypteringsoperationen. Ved RSA-kryptering bruges den offentlige nøgle til at omdanne klartekst til chiffertekst. Formålet er fortrolighed, fordi kun den tilhørende private nøgle kan dekryptere resultatet.

#### `-PUBIN`

> Fortæller OpenSSL, at nøglen i -inkey er en offentlig nøgle. Det passer med RSA-kryptering, hvor afsenderen bruger modtagerens offentlige nøgle til at kryptere beskeden. Den offentlige nøgle kan ikke selv bruges til at dekryptere chifferteksten.

#### `-INKEY ~/RSA/OFFENTLIG_NOEGLE.PEM`

> Bruger offentlig_noegle.pem som krypteringsnøgle. Beskeden krypteres til indehaveren af den tilhørende private nøgle. Det adskiller RSA fra symmetrisk kryptering, hvor samme hemmelige nøgle bruges til både kryptering og dekryptering.

#### `-IN ~/RSA/KLARTEKST.TXT`

> Læser klarteksten fra klartekst.txt. Klarteksten er den læsbare besked, der skal krypteres. I praktiske systemer bruges RSA normalt ikke til store filer direkte, fordi RSA har begrænsninger på, hvor meget data der kan krypteres ad gangen.

#### `-OUT ~/RSA/CIPHERTEKST.BIN`

> Gemmer chifferteksten i ciphertekst.bin. Filen indeholder den krypterede version af klarteksten i binært format. Indholdet skal ikke kunne læses meningsfuldt som almindelig tekst, fordi det nu er krypteret.

#### `-PKEYOPT RSA_PADDING_MODE:OAEP`

> Vælger OAEP-padding til RSA-krypteringen. RSA bør ikke anvendes direkte på rå klartekst, fordi det giver en for simpel og forudsigelig behandling af beskeden. OAEP tilføjer en standardiseret paddingstruktur, som gør RSA-krypteringen egnet til praktisk brug.

---

# 6. Dekryptering med privat RSA-nøgle
<img width="289" height="205" alt="image" src="https://github.com/user-attachments/assets/fe768e03-49cc-4ba0-b221-0da0be036bf1" />


#### `OPENSSL PKEYUTL`

> Starter OpenSSLs funktion til public key-operationer. Her bruges funktionen til RSA-dekryptering.

#### `-DECRYPT`

> Starter dekrypteringsoperationen. Ved RSA-dekryptering bruges den private nøgle til at føre chifferteksten tilbage til klartekst. Det viser RSA’s asymmetri: kryptering og dekryptering bruger forskellige dele af samme nøglepar.

#### `-INKEY ~/RSA/PRIVAT_NOEGLE.PEM`

> Bruger den private nøgle som dekrypteringsnøgle. Den private nøgle er nødvendig, fordi beskeden blev krypteret med den tilhørende offentlige nøgle. En anden privat nøgle kan ikke dekryptere chifferteksten korrekt.

#### `-IN ~/RSA/CIPHERTEKST.BIN`

> Læser chifferteksten fra ciphertekst.bin. Chifferteksten er den krypterede besked, som ikke kan læses direkte. Den skal behandles med den korrekte private nøgle og samme paddingtype for at kunne genskabes som klartekst.

#### `-OUT ~/RSA/DEKRYPTERET.TXT`

> Gemmer den dekrypterede klartekst i dekrypteret.txt. Hvis nøgleparret og paddingindstillingen passer sammen, indeholder filen den oprindelige besked.

#### `-PKEYOPT RSA_PADDING_MODE:OAEP`

> Bruger samme paddingtype som ved krypteringen. Dekryptering kræver ikke kun den korrekte private nøgle, men også korrekt fortolkning af den paddingstruktur, der blev brugt ved kryptering. Hvis paddingtypen ikke matcher, kan klarteksten ikke genskabes.

---

# 7. Dekryptering med forkert privat nøgle
<img width="643" height="173" alt="image" src="https://github.com/user-attachments/assets/ce6a4f33-7340-42ab-8181-0e69b7283224" />

<img width="637" height="67" alt="image" src="https://github.com/user-attachments/assets/4f3d30aa-4226-43e0-a907-d8ad9a164613" />

<img width="137" height="123" alt="image" src="https://github.com/user-attachments/assets/1728c718-8c4c-4090-a537-7929a44f4549" />

#### `OPENSSL GENPKEY -ALGORITHM RSA -OUT ~/RSA/FORKERT_PRIVAT_NOEGLE.PEM -PKEYOPT RSA_KEYGEN_BITS:2048`

> Opretter en ny privat RSA-nøgle, som ikke hører sammen med offentlig_noegle.pem. Den nye nøgle har sit eget nøglepar og passer derfor ikke til den offentlige nøgle, der blev brugt ved krypteringen.

#### `-INKEY ~/RSA/FORKERT_PRIVAT_NOEGLE.PEM`

> Bruger den forkerte private nøgle til dekryptering. Fordi denne nøgle ikke hører til den offentlige nøgle fra krypteringen, kan RSA-operationen ikke genskabe den oprindelige klartekst.

#### `-OUT ~/RSA/FORKERT_DEKRYPTERET.TXT`

> Gemmer resultatet af det mislykkede dekrypteringsforsøg. Hvis dekrypteringen fejler, bliver filen ikke dannet korrekt, eller indholdet bliver ikke den oprindelige klartekst.

#### `-PKEYOPT RSA_PADDING_MODE:OAEP`

> Bruger samme paddingtype som ved krypteringen. Selv med korrekt paddingtype kan beskeden ikke dekrypteres, hvis den private nøgle ikke hører til den offentlige nøgle, der blev brugt til kryptering.
