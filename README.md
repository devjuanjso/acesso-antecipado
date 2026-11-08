# ParkingSpace · Acesso antecipado

Página que explica, passo a passo e otimizada para celular, como virar testador do **ParkingSpace** (Android) e jogar antes do lançamento.

**Link da página (depois de publicar):** https://devjuanjso.github.io/acesso-antecipado/

## O que a página mostra
1. **Topo:** logo, vídeo do jogo em loop (sem som) e botão "Quero jogar".
2. **3 passos**, cada um com um botão grande:
   1. Entrar no grupo de testes: https://groups.google.com/g/testesres
   2. Virar testador: https://play.google.com/apps/testing/com.parkingspace.game
   3. Baixar na Play Store: https://play.google.com/store/apps/details?id=com.parkingspace.game

   A barra de progresso marca cada passo feito, e a marcação fica salva só no celular da pessoa.
3. **O que tem no jogo:** 4 imagens (pilha, estante, corrida no quintal, avião).
4. **Deu problema?:** perguntas frequentes ("Item não encontrado", várias contas Google, iPhone, preço, feedback).
5. **Compartilhar:** botão que abre o menu de compartilhar do celular ou copia o link.

## Arquivos
| Arquivo | O que é |
|---|---|
| `index.html` | A página inteira (HTML + CSS + JS, sem dependências além da fonte do Google Fonts) |
| `img/gameplay.mp4` | Vídeo do jogo, 540×960, sem áudio (~1,8 MB) |
| `img/poster.jpg` | Primeiro quadro do vídeo, aparece enquanto ele carrega |
| `img/icone.png` | Ícone do app (aba do navegador) |
| `img/pilha.jpg`, `encaixe.jpg`, `quintal.jpg`, `aviao.jpg` | Imagens da galeria |
| `.nojekyll` | Diz ao GitHub Pages para servir os arquivos como estão |

## Como publicar (só na primeira vez)
No GitHub, abra o repositório e vá em **Settings → Pages → Build and deployment**:
- **Source:** Deploy from a branch
- **Branch:** `main` e pasta `/ (root)` → **Save**

Em 1 ou 2 minutos o link acima fica no ar. Depois disso, todo `git push` na `main` atualiza a página sozinho.

## Como editar
- **Textos e links:** procure no `index.html` (os links dos 3 passos estão nas tags `<a class="btn ...">`).
- **Cores:** no topo do `<style>`, em `:root` (`--orange`, `--blue`, `--green`).
- **Trocar o vídeo ou as imagens:** substitua os arquivos em `img/` mantendo os mesmos nomes. O vídeo é gerado a partir do projeto do jogo (`Divulgacao/out/short_hype.mp4`):
  ```bash
  ffmpeg -i short_hype.mp4 -an -vf scale=540:960 -c:v libx264 -crf 28 -movflags +faststart -pix_fmt yuv420p img/gameplay.mp4
  ```
- **Testar no PC:** abra o `index.html` no navegador e aperte F12 → ícone de celular para ver como fica no telefone.

## Observações
- A página não coleta dados: não tem analytics nem formulário. O progresso dos passos fica só no navegador da pessoa (`localStorage`).
- Se o grupo de testes ou o link da Play Store mudarem, atualize os 3 links no `index.html` e neste README.
