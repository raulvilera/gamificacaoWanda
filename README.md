# 🏆 Quiz das Duplas — Ciências (Gamificado)

> Atividade de revisão gamificada para Ciências do 6º ao 9º ano, com pontuação, timer, streaks, ranking ao vivo e habilidades BNCC mapeadas.

---

## 📁 Arquivos

| Arquivo | Descrição |
|---------|-----------|
| `index.html` | Página principal do quiz (alunos) |
| `ranking.html` | Tela de ranking para TV/projetor |
| `imagens/` | 37 imagens reais ilustrativas |

---

## 🎮 Como Funciona o Jogo

### Para os Alunos (index.html)

1. **Seleção**: Escolhe turma e dupla (apoio + mentor)
2. **Timer**: 10 minutos para responder 10 questões
3. **Pontuação**:
   - Acerto normal: **+10 pts**
   - Streak 3+: **+15 pts** (bônus de combo)
   - Streak 5+: **+20 pts** (super combo)
   - Erro: streak zera, 0 pts
4. **Feedback imediato**: verde para acerto, vermelho para erro, resposta correta revelada
5. **Habilidades BNCC**: cada questão exibe a habilidade avaliada
6. **Tela de resultado**: troféu, pontuação final, estatísticas e diagnóstico por habilidade
7. **Envio**: resultado vai para Google Sheets + ranking local

### Para o Professor (ranking.html)

1. Abra `ranking.html?turma=6oAno_A` na TV/projetor
2. A tela atualiza automaticamente a cada 10 segundos
3. Mostra pódio (🥇🥈🥉) + tabela completa do ranking
4. Funciona offline via `localStorage` (dados ficam no navegador da TV)

---

## 🔧 Configuração do Envio (Google Sheets)

### 1. Planilha

Crie uma planilha com aba `"Respostas"` e cabeçalho:
```
Data|Turma|Dupla|Apoio|Mentor|Pontuacao|Acertos|Total|Streak|Tempo|Respostas|Habilidades
```

### 2. Apps Script

```javascript
function doPost(e){
  const aba = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Respostas");
  const d = JSON.parse(e.postData.contents);
  aba.appendRow([
    new Date(), d.turma, d.duplaIndex, d.apoioNome, d.mentorNome,
    d.pontuacao, d.acertos, d.total, d.streakMax, d.tempoUsado,
    JSON.stringify(d.respostas), JSON.stringify(d.habilidades)
  ]);
  return ContentService.createTextOutput(JSON.stringify({status:"ok"})).setMimeType(ContentService.MimeType.JSON);
}
```

### 3. Inserir URL

No `index.html`, substitua:
```javascript
const WEBAPP_URL = 'https://script.google.com/macros/s/COLE_AQUI/exec';
```

---

## 📊 Habilidades BNCC Mapeadas

| Série | Habilidades |
|-------|-------------|
| 6º ano | Fenômenos astronômicos, gravidade, rochas, hidrosfera, estados físicos, erosão, fósseis, rotação, fossilização, estações, planetas anões |
| 7º ano | Placas tectônicas, máquinas simples, atmosfera, decompositores, sustentabilidade, poluição, mudanças climáticas, deriva continental, vertebrados, efeito estufa |
| 8º ano | Trocas gasosas, ISTs, absorção de nutrientes, sistema cardiovascular, nutrientes, polinização, alimentação saudável, reprodução, puberdade |
| 9º ano | Misturas, mitose, Lavoisier, modelos atômicos, estados físicos, biotecnologia, ondas, DNA, Mendel, radiações |

---

## 🚀 Hospedagem

### GitHub Pages (recomendado)
1. Suba todos os arquivos para um repositório
2. Ative GitHub Pages em `Settings → Pages`
3. Acesse: `https://seu-usuario.github.io/repo/`

### Netlify Drop
1. Arraste a pasta inteira para [netlify.com/drop](https://netlify.com/drop)
2. Link instantâneo gerado

---

## 🖨️ Impressão

Pressione **Ctrl+P** — o CSS `@media print` remove elementos gamificados e mantém apenas a folha de questões limpa.

---

**E.E. Profª Wanda Mascagni de Sá** · Ciências · 2026
