# Claude Code Skill — Verificare Română

Skill pentru Claude Code care verifică texte în limba română din punct de vedere ortografic, gramatical și de punctuație.

## Ce verifică

- **Ortografie** — diacritice (ă, â, î, ș, ț), cuvinte greșite, confuzii frecvente (sa/s-a, ia/i-a)
- **Gramatică** — acorduri subiect-predicat, conjugări, regim prepozițional, pleonasme
- **Punctuație** — virgule, ghilimele românești „...", liniuța de dialog —, cratimă, spațiere

## Instalare

Copiază directorul `skills/verificare-romana/` în `~/.claude/skills/`:

```bash
# Clonează repo-ul
git clone https://github.com/daniela2batali-cyber/claude-skill-verificare-romana.git

# Copiază skill-ul
cp -r claude-skill-verificare-romana/skills/verificare-romana ~/.claude/skills/
```

Apoi repornește Claude Code.

## Utilizare

### Manual
```
/verificare-romana
/verificare-romana cale/catre/fisier.md
```

### Automat
Claude invocă skill-ul automat când detectează text românesc care necesită verificare.

## Output

Skill-ul returnează:
1. Lista erorilor grupate pe categorie (Ortografie / Gramatică / Punctuație) cu explicații
2. Textul corectat integral
