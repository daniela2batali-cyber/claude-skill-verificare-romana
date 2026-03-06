---
name: ai-writing-check
description: Verificare text in limba romana pentru red flags de scriere AI. Detecteaza si corecteaza pattern-urile care fac textul sa sune robotizat. Foloseste cand utilizatorul cere verificare AI writing, review de text, curatare de limbaj AI, sau /ai-writing-check.
argument-hint: [cale-fisier]
user-invokable: true
---

# AI Writing Red Flags Check — Limba Romana

Verificare si corectare a textului in romana pentru a elimina pattern-urile tipice de scriere AI.
Bazat pe checklist-ul "How to Stop Your Text from Sounding Like a Robot Wrote It" (@marinamogilko), adaptat integral pentru limba romana.

## Detectare input

1. Daca `$ARGUMENTS` contine o cale de fisier, citeste fisierul cu Read si analizeaza continutul
2. Daca exista o selectie IDE (text evidentiat), analizeaza textul selectat
3. Daca nu exista nici argument nici selectie, cere utilizatorului sa furnizeze textul

## Instructiuni de analiza

Analizeaza textul SI identifica TOATE instantele din urmatoarele 8 categorii de red flags:

### 1. INFLATIA

AI face totul sa sune ca un discurs de decernare a premiilor. O brutarie devine "un pilon al peisajului culinar local". Un bug fix devine "o avansare revolutionara".

Detecteaza:
- **Cuvinte inflatie** — esential, crucial, vital, fundamental, semnificativ, remarcabil, exceptional, deosebit, revolutionar, transformator, inovator, de referinta, emblematic, inegalabil, de neegalat, indispensabil, inestimabil
- **Boala "semnificatiei mai largi"** — clauze cu: "reflecta tendinte mai largi", "subliniaza importanta", "evidentiaza mostenirea", "contribuie la", "marcheaza un moment de cotitura", "reprezinta un punct de reper", "pune bazele", "deschide noi orizonturi"
- **Verbe care forteaza**:
  - "serveste drept" / "functioneaza ca" / "reprezinta" / "constituie" in loc de "este"
  - "se mandreste cu" / "dispune de" / "beneficiaza de" in loc de "are"
  - "pune in evidenta" / "scoate in relief" in loc de "arata"
  - "exemplifica" in loc de "e un exemplu de"

Corectia: inlocuieste cu varianta simpla. "Este", "are", "arata" sunt perfecte. Sterge clauzele de semnificatie — faptul e suficient.

✗ "Deschiderea restaurantului in 1987 a marcat un moment de cotitura in evolutia culinara a cartierului, reflectand schimbari mai largi in cultura dining-ului urban."
✓ "Restaurantul s-a deschis in 1987."

### 2. BALANTA FALSA

Detecteaza:
- **Paralelisme negative staccato** — "Nu e vorba de X. Nu e vorba de Y. E vorba de Z." sau "Fara compromisuri. Fara scuze. Doar rezultate."
- **Constructia "Nu doar... ci si"** — "Acesta nu e doar un produs — e o redefinire a modului in care ne conectam." Maxim o data la 2.000 de cuvinte.
- **Pivotul "totusi/cu toate acestea" decorativ** — "totusi", "cu toate acestea", "in schimb" folosite fara sa introduca informatie noua reala
- **"Pe de o parte... pe de alta parte"** — cand nu exista tensiune reala intre cele doua parti

Corectia: elimina constructia sau reformuleaza direct. Daca "totusi" nu introduce ceva cu adevarat diferit, sterge-l.

✗ "Nu e vorba despre motivatie. Nu e vorba despre disciplina. E vorba despre sisteme."
✓ "Cel mai mult conteaza sistemele pe care le ai."

### 3. RITMUL

Detecteaza:
- **Propozitii metronomice** — toate de aceeasi lungime, ca un metronom. Textul uman are: o lovitura scurta, apoi o gandire lunga, apoi un fragment.
- **Abuz de liniuta lunga** (—) — mai mult de una per paragraf e suspect. AI le foloseste ca pe un "um".
- **Regula lui trei** — liste mereu in grupuri de 3: "inovatie, colaborare si excelenta". "Curajos, autentic si transformator." Listele reale au 2, 4 sau 7 elemente.

Corectia: variaza lungimea propozitiilor. Inlocuieste liniutele excesive cu puncte. Sparge tripleturi.

✗ "Rezultatele au fost clare — abordarea a functionat."
✓ "Rezultatele au fost clare. Abordarea a functionat."

### 4. VAGUL

Detecteaza:
- **Atributii fantoma** — "Expertii sustin ca...", "Studiile arata ca...", "Specialistii in domeniu au remarcat...", "Cercetarile recente demonstreaza..."  Care experti? Ce studii? Numeste-le. Daca nu le poti numi, probabil inventezi.
- **Inflatie de cantitate** — "numeroase studii" (cate?), "recunoscut pe scara larga" (de cine?), "documentat extensiv" (unde?), "multiple surse" (care?)
- **Coada participiala** — propozitii terminate cu participii/gerunzii care suna analitic dar nu spun nimic: "...demonstrand angajamentul artistului fata de evolutia creativa", "...oferind o perspectiva noua asupra fenomenului"
- **Intervale false** — "De la implicarea comunitara la inovatie tehnologica..." — doua lucruri fara legatura prezentate ca spectru

Corectia: numeste sursa exacta. Inlocuieste "numeroase" cu numarul real. Sterge cozile participiale. Elimina intervalele false.

✗ "Albumul a fost lansat in 2019, demonstrand angajamentul artistului fata de evolutia sa creativa."
✓ "Albumul a fost lansat in 2019."

### 5. VOCABULARUL

Cuvinte care au explodat in frecventa dupa 2023 in textele generate de AI. Unu-doua e ok. Cinci in acelasi paragraf e semn neon.

Detecteaza:
- **Substantive AI** — peisaj (abstract), tesatura (abstract), interactiune, complexitate, mostenire, pilon, reper, sinergie, ecosistem (non-biologic), cadru/framework, paradigma, viziune, demers, abordare holistica
- **Verbe AI** — a sublinia, a evidentia, a pune in valoare, a cataliza, a potenta, a valorifica, a optimiza, a eficientiza, a facilita, a genera, a consolida, a implementa, a dinamiza, a propulsa
- **Adjective AI** — esential, crucial, remarcabil, vibrant, complex, robust, nuantat, holistic, inovator, autentic, profund, transformator, strategic, comprehensiv, sustenabil
- **Tranzitii AI** — "De asemenea" (la inceput de propozitie), "Mai mult decat atat", "In plus", "Totodata", "Nu in ultimul rand", "Asadar", "Prin urmare", "Este important de mentionat ca"
- **Ciclare de sinonime** — acelasi lucru numit "abordare", apoi "strategie", apoi "framework", apoi "sistem" in acelasi paragraf. Oamenii repeta cuvantul. Claritatea bate varietatea.
- **Adjective dublu-stivuite** — "vibrant si dinamic", "bogat si divers", "complex si nuantat" (redundant — inseamna acelasi lucru)

Corectia: inlocuieste cu cuvinte simple si directe. Max 1-2 cuvinte din lista per paragraf. Repeta cuvantul potrivit in loc sa ciclezi sinonime. Un adjectiv, maxim. Adesea zero.

### 6. STRUCTURA

Detecteaza:
- **Formula "In ciuda... provocarilor"** — pozitiv -> "in ciuda" -> provocari -> de fapt ok -> optimism vag. Echivalentul AI al intrebarii "Care e cel mai mare defect al tau?" la interviu.
- **Pivotul promotional** — descrieri neutre devin brosuri turistice sau pitch-uri de vanzare. Cuvinte pericol: asezat in inima, vibrant, bogat (figurativ), se mandreste cu, frumusete naturala, angajament fata de, dedicatie fata de, spatiu de inspiratie
- **Concluzii inutile** — "In concluzie", "Per ansamblu", "Asadar", "In rezumat" urmate de reluarea a ce s-a spus. Daca paragraful e bine scris, nu trebuie rezumat.
- **Paragrafe uniforme** — toate de 3-5 propozitii. Textul uman variaza: o propozitie pentru efect, un bloc lung pentru complexitate.

Corectia: sterge formula "in ciuda...provocarilor". Elimina tonul promotional. Sterge concluziile care repeta. Variaza lungimea paragrafelor.

✗ "In ciuda provocarilor economice, compania continua sa prospere datorita pozitionarii sale strategice."
✓ "Compania a crescut cu 15% anul trecut."

### 7. HEDGING-UL

AI se fereste de afirmatii directe fiindca e antrenat sa evite claimuri absolute.

Detecteaza:
- **Calificari precaute** — "Este important de mentionat ca...", "Merita subliniat faptul ca...", "In general vorbind...", "S-ar putea argumenta ca...", "Intr-o oarecare masura...", "Putem spune ca..."
- **Epidemia de "ar putea" / "poate"** — "Aceasta abordare ar putea ajuta...", "Rezultatele par sa sugereze...", "Aceste evolutii ar putea avea implicatii..." cand nu exista incertitudine reala
- **Formulari pasiv-evazive** — "Se poate observa ca...", "Este de remarcat faptul ca...", "Se constata o tendinta de..."

Corectia: sterge calificarea si spune lucrul direct. Daca stii ca e adevarat, spune-o fara "ar putea" si "pare sa".

✗ "Aceasta abordare ar putea ajuta organizatiile sa-si imbunatateasca rezultatele."
✓ "Abordarea asta imbunatateste rezultatele."

### 8. LIPSA DE SUFLET

Detecteaza:
- **Fara opinii, fara mize** — text echilibrat pana la disparitie. Nu spune niciodata "asta e rau" sau "asta conteaza cu adevarat". Daca poti schimba substantivele proprii si textul inca functioneaza — nu are suflet.
- **Fara detalii concrete** — generalitati in loc de fapte specifice
- **Prea lustruit** — fara imperfectiuni, fara expresii colocviale, fara propozitii care incalca putin regulile dar au momentum. Textul fara frictiune e textul pe care il uiti.

Corectia: adauga numere, nume, date, locuri, anecdote. Ia o pozitie. Lasa ceva imperfectiune naturala.

✗ "Compania a inregistrat o crestere semnificativa."
✓ "Veniturile au crescut de la 2 milioane la 11 milioane in 18 luni."

## Format output

Prezinta rezultatele astfel:

### Raport AI Writing Check

**Scor:** X/10 (10 = complet uman, 1 = evident AI)

**Red flags gasite:**

Pentru fiecare problema gasita, listeaz-o astfel:
- **[Categoria] [Subcategoria]** — citat exact din text -> sugestie de corectie

Exemplu:
- **[INFLATIE] Verb fortat** — "Galeria *serveste drept* spatiu de expozitie" -> "Galeria *este* spatiul de expozitie"
- **[VOCABULAR] Cuvant AI** — "...o comunitate *vibranta*" -> "...o comunitate activa" sau sterge adjectivul
- **[HEDGING] Calificare inutila** — "*Este important de mentionat ca* rezultatele..." -> "Rezultatele..."
- **[VAGUL] Atributie fantoma** — "*Studiile arata ca*..." -> numeste studiul sau sterge

**Statistici rapide:**
- Cuvinte AI gasite: [lista]
- Constructii "nu doar...ci si": [numar]
- Cozi participiale deletabile: [numar]
- Liniute lungi per paragraf (max): [numar]
- Triplete (regula lui 3): [numar]
- Hedging phrases: [numar]
- Tranzitii AI la inceput de propozitie: [numar]

**Versiune corectata:**

Rescrie textul complet cu toate corectiile aplicate. Pastreaza sensul si tonul original, dar elimina toate red flag-urile identificate.

## Quick Self-Check (cele 10 puncte finale)

Dupa corectare, verifica textul final pentru:
1. Mai mult de 2 cuvinte AI vocabulary intr-un singur paragraf
2. Constructii "nu doar... ci si" sau "Nu X. Nu Y. Doar Z." — sunt meritate?
3. Cozi participiale la sfarsit de propozitii — pot fi sterse?
4. Atributii vagi "expertii spun" sau "recunoscut pe scara larga" — poti numi sursa?
5. "In ciuda... provocarilor" oriunde in text
6. Mai mult de o liniuta lunga per paragraf
7. Regula lui trei folosita de mai mult de o data
8. Cuvintele "vibrant", "peisaj", "tesatura", "pilon", "a sublinia", "a evidentia", "ecosistem" — necesare?
9. Paragrafe toate de aceeasi lungime
10. O concluzie care repeta ce s-a spus deja
