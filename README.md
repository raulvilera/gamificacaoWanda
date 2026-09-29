# NEBULA // C.I.E. — Ciências

Atividade de revisão gamificada para Ciências do 6º ao 9º ano, com **jornada individual**, listas de estudantes em dropdown, desafios do **3º bimestre** e interface futurista inspirada em painéis de jogos sci-fi.

## O que mudou

- A realização deixou de ser em duplas: cada estudante seleciona **turma + próprio nome**.
- O fluxo virou uma missão individual, com um desafio por vez, progresso, timer, combo, XP e tela de resultado.
- As questões foram reformuladas e alinhadas ao **Guia Priorizado de Ciências — CIE_AF_2026 (5)** consultado no Drive.
- O conteúdo cobre os eixos do 3º bimestre:
  - **6º ano:** célula, microscopia, organelas, microrganismos, saneamento e níveis de organização;
  - **7º ano:** ecossistemas, biomas brasileiros, conservação, agricultura sustentável e saúde única;
  - **8º ano:** movimentos da Terra e da Lua, eclipses, tempo/clima, circulação atmosférica e mudanças climáticas;
  - **9º ano:** evolução, biodiversidade, unidades de conservação, água, economia circular e resíduos.
- O ranking passou de duplas para **agentes individuais** e mantém o seletor por turma.
- A identidade visual foi refeita com grid neon, glassmorphism, tipografia Orbitron, elementos de orbita e cartões com profundidade 3D.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | Seleção individual, missão, questões e envio de resultado |
| `ranking.html` | Ranking individual por turma |
| `imagens/` | Ilustrações usadas nos desafios |

## Execução local

```bash
python3 -m http.server 8080
```

Abra `http://localhost:8080`.

## Integração

O endpoint de Apps Script foi preservado. O payload agora inclui `alunoNome` e não depende de `apoioNome`/`mentorNome`. O ranking local usa `localStorage` por turma com a chave `ranking_<turma>`.

Fonte curricular consultada: PDF `CIE_AF_2026 (5).pdf`, pasta **Guias Priorizados** no Google Drive, seções de Escopo-Sequência do 3º Bimestre e matriz de aprendizagens essenciais.
