# aider-ollama-local

DevContainer for [Aider](https://aider.chat) with local Ollama models.

**Miksi Aider eikä OpenCode:** Aider ei pyydä mallia tekemään tool-kutsuja.
Se pyytää mallin tuottamaan diff-muodossa koodimuutokset ja soveltaa ne itse.
Tämä toimii luotettavasti myös 12–32B paikallisilla malleilla.

## Vaatimukset

- Ollama käynnissä hostilla (portti 11434)
- Haluttu malli ladattuna: `ollama pull qwen2.5-coder:32b`
- VS Code + Dev Containers -extensio

## Käyttö

```bash
# Kopioi devcontainer projektiisi
cp -r tools/aider-ollama-local/.devcontainer omaprojekti/
cp tools/aider-ollama-local/.aider.conf.yml omaprojekti/

# Avaa VS Codessa → "Reopen in Container"

# Kontainerissa:
aider tiedosto.py toinentiedosto.js
```

## Mallin vaihto

Muuta `.aider.conf.yml`:

```yaml
model: ollama_chat/gemma4-coder        # Gemma 4 12B (nopeampi, heikompi)
model: ollama_chat/qwen2.5-coder:32b   # Qwen 32B (suositeltu)
model: ollama_chat/qwen2.5-coder:7b    # 7B jos muisti loppuu
```

## Tiedostojen antaminen aiderille

```bash
# Yksi tiedosto
aider src/app.py

# Useita tiedostoja
aider src/app.py src/utils.py

# Kaikki tietyn kansion tiedostot
aider src/*.py
```

Aider kirjoittaa muutokset suoraan tiedostoihin — ei tool-kutsuja, ei jumittumista.
