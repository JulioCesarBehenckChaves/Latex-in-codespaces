## Para compilar

```bash
cd "/workspaces/ChatFGV/publicação-artigo" && pdflatex -interaction=nonstopmode chatfgv-artigo.tex
```

## Para compilar com referências

```bash
# 1. Compilar o arquivo .tex com pdflatex (primeira passagem)
pdflatex chatfgv-artigo.tex

# 2. Processar as referências com bibtex
bibtex chatfgv-artigo

# 3. Compilar novamente com pdflatex (segunda passagem)
pdflatex chatfgv-artigo.tex

# 4. Compilar uma terceira vez para resolver referências cruzadas
pdflatex chatfgv-artigo.tex
```

## Para limpar caracteres estranhos impedindo compilação

```bash
find publicação-artigo -name '*.tex' -print0 | xargs -0 perl -CS -pi -e 's/\x{200B}//g'
```