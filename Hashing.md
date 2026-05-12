<div align="center">

# Demonstration af Hashing (SHA-256)

**Af**  
**Michael Krüger Andersen**

**Værktøj:** `openSSL` & `Kali Linux`

</div>

---

*Jeg vil i dette dokument demonstrere, hvordan vi kan hashe klartekst.txt filen*

---

# 1. Oprettelse af arbejdsmappe

---

# 2. Kopiering af klartekstfilen fra RSA-demonstrationen

#### `cp ~/RSA/klartekst.txt ~/Hashing/klartekst.txt`

> Kopierer Klartekstfilen fra den asymmetriske RSA-demonstrationen til hashing mappen.

---

# 3. Beregning og lagring af SHA-256-hashværdi

#### `sha256sum`

> Beregner en SHA-256-hashværdi for filens indhold. Resultatet er en kontrolværdi på 256 bit, som normalt vises som 64 hexadecimale tegn. Samme filindhold giver samme hashværdi, så længe inputtet er identisk.

#### `~/Hashing/klartekst.txt`

> Inputfilen til hashberegningen. Hele filens indhold indgår i beregningen, så selv en lille ændring i teksten vil betyde, at den oprindelige kontrolværdi ikke længere passer til filen.

#### `~/Hashing/klartekst.sha256`

> Indeholder den beregnede SHA-256-hashværdi sammen med stien til den fil, hashværdien hører til. Det gør filen egnet til efterfølgende integritetskontrol med sha256sum -c.

#### `cat ~/Hashing/klartekst.sha256`

> Viser den gemte hashværdi i terminalen. Outputtet vil bestå af hashværdien efterfulgt af filstien.

---

# 4. Kontrol mod den gemte hashværdi

#### `sha256sum -c`

> Kontrollerer, om filen stadig svarer til den gemte SHA-256-hashværdi. Kommandoen læser hashfilen, beregner en ny hashværdi for den angivne fil og sammenligner de to værdier. Hvis de matcher, vises resultatet som OK.

#### `~/Hashing/klartekst.sha256`

> Hashfilen bruges som reference ved kontrollen. Den indeholder både den tidligere beregnede SHA-256-værdi og stien til den fil, der skal kontrolleres.

---

# 5. Ændring af filens indhold

### Teksten adskiller sig fra den oprindelige ved det sidste tegn: punktummet er erstattet af et udråbstegn. Selvom ændringen er lille, er filindholdet ikke længere identisk med det indhold, den første hashværdi blev beregnet ud fra.

---

# 6. Beregning af ny hashværdi efter ændringen

#### `sha256sum`

> Beregner en ny SHA-256-hashværdi på baggrund af det ændrede filindhold. Da inputtet ikke længere er det samme som før, bliver den nye hashværdi anderledes end den oprindelige. Hashværdier bruges netop til at opdage, at data er blevet ændret.

#### `~/Hashing/klartekst.txt`

> Inputfilen er fortsat den samme, men indholdet er nu ændret.

#### `~/Hashing/klartekst_aendret.sha256`

> Indeholder SHA-256-hashværdien for den ændrede klartekstfil.

---

# 7. Gentaget kontrol mod den oprindelige hashværdi



#### `sha256sum -c`

> Kontrollerer igen filen mod den oprindelige hashværdi. Denne gang beregner kommandoen en SHA-256-værdi for den ændrede fil, som ikke længere matcher den værdi, der er gemt i klartekst.sha256. Derfor vises kontrollen som fejlet.

#### `~/Hashing/klartekst.sha256`

> Den oprindelige hashfil bruges som reference for, hvordan filens indhold så ud før ændringen.


### Resultatet viser hashingens funktion ved integritetskontrol: filen behøver ikke at være ulæselig eller krypteret, men en ændring i indholdet kan opdages, fordi den tidligere hashværdi ikke længere passer til filen.
