#  Jogo da Adivinhação  
Repositório: [derick-0/projeto-jogo-de-adivinha-ao--](https://github.com/derick-0/projeto-jogo-de-adivinha-ao-)

Um jogo em **C** com múltiplos modos de adivinhação, pontuação e ranking — ideal para treinar lógica, structs, loops e interatividade em terminal.

---

##  Sumário  
1. [Sobre o Projeto](#sobre-o-projeto)  
2. [Modos de Jogo](#modos-de-jogo)  
3. [Tecnologias Utilizadas](#tecnologias-utilizadas)  
4. [Como Executar](#como-executar)  
5. [Ranking e Pontuação](#ranking-e-pontuação)  
6. [Estrutura do Código](#estrutura-do-código)  
7. [Exemplo de Execução](#exemplo-de-execução)  
8. [Autor e Créditos](#autor-e-créditos)  

---

##  Sobre o Projeto  
Este projeto oferece diferentes modos de jogo de adivinhação, onde o jogador tenta descobrir um número aleatório gerado pelo computador.  
Inclui variações de dificuldade, pontuação decrescente, cadastro de jogadores e ranking de equipes.

---

##  Modos de Jogo  
| Modo | Descrição |
|------|------------|
| **Modo 1** | Adivinhe um número entre **25 e 75**. |
| **Modo 2** | Três níveis de dificuldade (Fácil 1-50, Médio 1-100, Difícil 1-200). A cada erro, penalidade de pontos. |
| **Modo 3** | Número entre **1 e 150**. Penalidade de 10 pontos por tentativa errada. |
| **Modo 4** | Cadastro de equipe (até 5 jogadores). Cada jogador recebe pontuação aleatória. |
| **Modo 5** | Ranking real: cada jogador entra, adivinha número entre 1-50, pontuação calculada conforme tentativas. |

---

##  Tecnologias Utilizadas  
- Linguagem: **C**  
- Bibliotecas: `<stdio.h>`, `<stdlib.h>`, `<time.h>`  
- Compilador sugerido: `gcc` ou outro compatível com C padrão  
- Sistema operacional: Terminal/console (Windows, Linux ou macOS)  

---

##  Como Executar  
### 1. Clone o repositório  
```bash
git clone https://github.com/derick-0/projeto-jogo-de-adivinha-ao-.git
cd projeto-jogo-de-adivinha-ao-
