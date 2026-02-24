---
name: verificare-romana
description: Verificare ortografică, gramaticală și de punctuație în limba română. Folosește acest skill când utilizatorul scrie sau editează text în română, când cere verificare/corectare de text românesc, sau când trimite conținut în limba română care ar putea conține erori.
argument-hint: [cale-fisier]
---

# Verificare ortografică, gramaticală și de punctuație în limba română

## Detectare input

1. Dacă `$ARGUMENTS` conține o cale de fișier, citește fișierul cu tool-ul Read și verifică conținutul
2. Dacă există o selecție IDE (text evidențiat de utilizator în editor), verifică textul selectat
3. Dacă nu există nici argument nici selecție, cere utilizatorului să furnizeze textul de verificat

## Instrucțiuni de verificare

Analizează textul în limba română și identifică toate erorile din următoarele categorii:

### 1. Ortografie
- Cuvinte scrise greșit
- Diacritice lipsă sau incorecte:
  - ă, â, î, ș, ț trebuie să fie prezente acolo unde este necesar
  - Distincția corectă între â și î (â se folosește în interiorul cuvintelor, î la început și la sfârșit)
  - Ș și Ț cu virgulă dedesubt (U+0219, U+021B) — NU cu sedilă (U+015F, U+0163)
- Cuvinte confuzabile (ex: „a" vs „au", „sa" vs „s-a", „ia" vs „i-a")

### 2. Gramatică
- Acorduri greșite: subiect-predicat, substantiv-adjectiv (gen, număr, caz)
- Conjugări verbale incorecte
- Utilizare greșită a pronumelor (personale, reflexive, relative)
- Regim prepozițional incorect
- Folosire greșită a articolului hotărât/nehotărât
- Confuzii frecvente: „m-am/mam", „s-a/sa", „n-am/nam", „i-a/ia", „ne-am/neam"
- Pleonasme evidente

### 3. Punctuație
- Virgule lipsă sau în plus:
  - NU se pune virgulă înainte de „că" când introduce o completivă directă (ex: „Am spus că vine" — fără virgulă)
  - SE pune virgulă înainte de „că" cu sens cauzal (ex: „Nu am venit, că a plouat" — virgulă corectă)
  - Virgula înainte de „deoarece", „întrucât", „fiindcă" (propoziții cauzale)
  - Reguli de izolare a propozițiilor intercalate și incidente
- Ghilimele românești: „..." (jos-sus), nu "..." sau «...»
- Liniuța de dialog: — (em dash), nu - (cratimă) sau – (en dash)
- Cratima: utilizare corectă în cuvinte compuse și forme verbale pronominale
- Punctul, semnul exclamării, semnul întrebării — poziționare corectă
- Două puncte și punct și virgulă — utilizare adecvată
- Spațiere corectă în jurul semnelor de punctuație

## Format output

Răspunde ÎNTOTDEAUNA în limba română, structurat astfel:

### Dacă sunt erori:

**Secțiunea 1 — Lista erorilor** grupate pe categorie:

#### Ortografie
- „cuvant" → „cuvânt" — lipsește diacritica â
- (alte erori ortografice...)

#### Gramatică
- „Copiii merge" → „Copiii merg" — acord subiect-predicat (plural)
- (alte erori gramaticale...)

#### Punctuație
- „Nu am venit ca a plouat" → „Nu am venit, că a plouat." — virgulă înainte de „că" cauzal
- (alte erori de punctuație...)

**Secțiunea 2 — Textul corectat integral**

Prezintă textul complet cu toate corecțiile aplicate.

### Dacă NU sunt erori:

Confirmă scurt că textul este corect din punct de vedere ortografic, gramatical și al punctuației.

## Comportament important

- NU modifica fișierele direct. Afișează doar corecțiile și textul corectat. Editează fișierul doar dacă utilizatorul cere explicit acest lucru.
