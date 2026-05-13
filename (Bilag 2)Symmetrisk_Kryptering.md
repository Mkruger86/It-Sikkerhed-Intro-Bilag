<div align="center">

# Demonstration af symmetrisk kryptering (AES)

**Af**  
**Michael Krüger Andersen**

**Værktøj:** `openSSL` & `Kali Linux`

</div>

---

# 1. Oprettelse af klartekst-fil
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/f06b7a90-f2e5-49d0-83ca-d74c81284b67" />

#### `ECHO`

> Skriver klarteksten til standard output, som normalt er terminalen. Her bruges kommandoen til at sende en konkret tekst videre til filen klartekst.txt.

#### `MKDIR -P ~/AES`

> opretter mappen AES i hovedmappen kali, hvis den ikke allerede findes.

#### `~/AES/KLARTEKST.TXT`

> Gemmer outputtet som filen klartekst.txt inde i mappen Kali/Aes.

#### `CAT ~/AES/KLARTEKST.TXT`

> Viser filens indhold i terminalen. Kommandoen bruges her til at kontrollere, at klartekstfilen er oprettet korrekt, og at indholdet stadig er læsbart før kryptering.

---

# 2. Adgangskode gemmes midlertidigt til OpenSSL
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/85f138a5-cb6e-436a-958f-0ed30f5a0e01" />

#### `PRINTF "INDTAST AES-ADGANGSKODE: "`

> Skriver prompten i terminalen, så brugeren ville får besked om at indtaste en adgangskode. Her har jeg indtastet HejRoskilde som jeg snere vil bruge til at teste, om dekrypteringen vil fejle som forventet med et forkert password

#### `READ -S AESPASS`

> læser input fra terminalen og gemmer det i variablen AESPASS. Her bruges kommandoen til at modtage den adgangskode, der senere bruges som hemmelighed i krypteringsprocessen. -s skjuler indtastningen, så adgangskoden ikke vises på skærmen.

#### `EXPORT AESPASS`

> Gør variablen tilgængelig for OpenSSL, så adgangskoden kan hentes med -pass env:AESPASS.

---

# 3. Kryptering af klartekst
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/15565b31-a6d1-4131-a530-04795eba8d01" />

#### `OPENSSL ENC`

> Vælger OpenSSLs funktion til symmetrisk kryptering og dekryptering.

#### `-AES-256-CBC`

> Vælger AES med 256-bit nøgle i CBC-mode. AES er selve blokchifferet og behandler data i blokke på 128 bit. CBC er driftstilstanden, der bestemmer, hvordan flere blokke kædes sammen. CBC kræver en IV, fordi den første blok skal have en startværdi. IV står for initialization vector, og skal være den samme ved dekryptering som ved kryptering. I denne password-baserede OpenSSL-kommando angives IV ikke manuelt, fordi OpenSSL håndterer IV’en som del af den password-baserede proces.

#### `-SALT`

> Aktiverer brug af salt. Salt er en værdi, der indgår i nøgleafledningen, så samme adgangskode ikke altid giver samme afledte nøglemateriale.

#### `-PBKDF2`

> Vælger PBKDF2 som nøgleafledningsfunktion. PBKDF2 omdanner adgangskoden til kryptografisk nøglemateriale ved at bruge adgangskode, salt, iterationsantal og ønsket nøglelængde.

#### `-ITER 200000`

> Angiver 200.000 iterationer i nøgleafledningen. Et højere iterationsantal gør nøgleafledningen langsommere, hvilket gør brute-force-forsøg dyrere, fordi hvert adgangskodegæt kræver samme nøgleafledning.

#### `-A`

> Base64-encoder outputtet. AES producerer binære data, som ikke nødvendigvis kan vises direkte som almindelig tekst i terminalen. Base64 gør chifferteksten visbar og lettere at kopiere.

#### `-IN KLARTEKST.TXT`

> Angiver inputfilen.

#### `-OUT CIPHERTEKST.B64`

> Angiver outputfilen.

#### `-PASS ENV:AESPASS`

> Fortæller OpenSSL, at adgangskoden skal hentes fra variablen AESPASS, Adgangskoden bruges til at udlede nøglemateriale, som AES-256-CBC bruger til krypteringen.

---

# 4. Dekryptering af chifferteksten
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/96881a4c-bea1-4b42-b386-8eeda7455925" />

#### `OPENSSL ENC`

> Starter samme OpenSSL-funktion som før, men denne gang bruges funktionen til dekryptering.

#### `-D`

> Ændrer operationen til den inverse proces, hvor chiffertekst omdannes tilbage til klartekst.

#### `-AES-256-CBC`

> Skal matche krypteringen. Samme algoritme og samme driftstilstand skal bruges, fordi chifferteksten blev dannet med AES-256-CBC.

#### `-PBKDF2`

> Skal matche nøgleafledningen fra krypteringen. Hvis nøgleafledningen ikke matcher, dannes der ikke samme nøglemateriale.

#### `-ITER 200000`

> Skal matche iterationsantallet fra krypteringen. Samme adgangskode, samme salt og samme iterationsantal skal bruges for at danne samme nøglemateriale.

#### `-A`

> Inputtet Base64-dekodes først igen, så kan den binære chiffertekst dekrypteres.

#### `-IN ~/AES/CIPHERTEKST.B64`

> Den krypterede fil, der skal føres tilbage til klartekst.

#### `-OUT CDEDEKRYPTERET.TXT`

> Den genskabte klartekst, såfremt adgangskoden og de kryptografiske parametre er korrekte.

#### `-PASS ENV:AESPASS`

> Henter samme adgangskode fra AESPASS og viser symmetrien i processen, givet samme hemmelige adgangskode og ligeledes andre operationer bruges til både kryptering og dekryptering.

---

# 5. Ekstra: Forkert adgangskode
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/62fc8df3-f756-4952-9210-c3a28ede5a82" />

#### `-PASS PASS:NEJ`

> Her indtastes en forkert adgangskode (Den rigtige er HejRoskilde). Den forkerte adgangskode danner forkert nøglemateriale, og derfor kan den oprindelige klartekst ikke genskabes korrekt. Resultatet er en fejlmeddelelse.
