# Agente de IA: Conversor NL ↔ CPC

## 🎯 Visão Geral
Este projeto implementa um **Agente de IA Web** capaz de converter automaticamente entre:

- **NL → CPC**: Linguagem Natural (Português) → Fórmulas Lógicas (Cálculo Proposicional Clássico)  
- **CPC → NL**: Fórmulas Lógicas → Linguagem Natural (Português)  

O sistema reconhece conectivos lógicos, estrutura proposições atômicas e gera mapeamentos automáticos de variáveis (P, Q, R...), permitindo tradução bidirecional precisa e customização pelo usuário.

---

## 🏗 Arquitetura do Sistema

```mermaid
graph TD
    A[Interface Web] --> B[Motor de Tradução]
    B --> C[NL → CPC Engine]
    B --> D[CPC → NL Engine]
    C --> E[Sistema de Mapeamento]
    D --> E
    E --> F[Variáveis P, Q, R...]
    E --> G[Customização pelo usuário]
 
 Explicação de Funcionamento:

Interface Web: Permite inserir texto em NL ou CPC, visualizar resultados e proposições mapeadas.

Motor de Tradução: Detecta conectivos, extrai proposições e constrói a fórmula lógica ou a frase em português.

NL → CPC Engine: Processa linguagem natural, identifica padrões e gera fórmulas CPC com parênteses e espaçamento correto.

CPC → NL Engine: Faz parsing da fórmula lógica, reconstruindo frases coerentes em português.

Sistema de Mapeamento: Atribui variáveis P, Q, R..., permite personalização e preserva histórico.

🔄 Estratégia de Tradução
NL → CPC (Português → Lógica)

Padrões de Tradução:

Padrão em Português	Estrutura Lógica
"se X, então Y"	X → Y
"X e Y"	X ∧ Y
"X ou Y"	X ∨ Y
"não X"	¬X
"X se e somente se Y"	X ↔ Y

Etapas do Processo:

Pré-processamento: Normaliza o texto, remove acentos, pontuação e converte para minúsculas.

Detecção de Conectivos: Regex identifica padrões de conectivos e operadores lógicos.

Extração de Proposições Atômicas: Divide frases em partes e atribui variáveis P, Q, R...

Geração da Fórmula CPC: Monta fórmula com espaços e parênteses somente quando há múltiplos conectivos.

Exemplos:

Entrada NL	Saída CPC	Mapeamento
"Se chover, então a grama ficará molhada"	P → Q	P=chover, Q=a grama ficará molhada
"Se estudar e praticar, então passarei na prova"	(P ∧ Q) → R	P=estudar, Q=praticar, R=passarei na prova
"Não está chovendo"	¬P	P=está chovendo
"Vou à festa se e somente se você for"	P ↔ Q	P=vou à festa, Q=você for
CPC → NL (Lógica → Português)

Etapas do Processo:

Parsing da Fórmula: Cria árvore sintática da expressão lógica.

Reconstrução Recursiva: Percorre a árvore para gerar frase coerente.

Tradução de Operadores:

Operador	Tradução em Português
→	"implica que" / "então"
∧	"e"
∨	"ou"
¬	"não"
↔	"se e somente se"

Exemplos CPC → NL:

Entrada CPC	Saída NL	Mapeamento
(P ∧ Q) → R	Se João estudar e Maria ajudar, então passar no teste	P=João estudar, Q=Maria ajudar, R=passar no teste
¬P	Não está chovendo	P=está chovendo
P ↔ Q	Vou à festa se e somente se você for	P=vou à festa, Q=você for
🔣 Casos Complexos

Entrada NL: "Se chover e não ventar, ou se fizer sol mas não estiver quente, então irei à praia"
Saída CPC: ((P ∧ ¬Q) ∨ (R ∧ ¬S)) → T
Mapeamento:

P = chover

Q = ventar

R = fizer sol

S = estiver quente

T = irei à praia

📊 Análise de Acertos e Limitações
✅ Pontos Fortes

Reconhecimento robusto de conectivos e negações

Tradução bidirecional consistente (NL↔CPC)

Atribuição automática de variáveis e customização

Interface web moderna e responsiva

⚠ Limitações

Ambiguidade Linguística: Pode interpretar "Maria vai se João for" de forma incorreta.

Frases Complexas com Vários Conectivos: Pode gerar parsing incompleto.

Sinonímia: Diferentes palavras podem gerar variáveis distintas.

Quantificadores e Predicados: Não suporta lógica de predicados (∀, ∃).

🔮 Possibilidades de Melhoria

Uso de LLMs para interpretação semântica e resolução de ambiguidades

Validação de fórmulas CPC bem-formadas

Histórico de traduções e exportação de resultados

Geração automática de tabelas-verdade

Suporte a múltiplos idiomas e lógica de predicados

🚀 Instalação e Execução
Pré-requisitos

Navegador moderno

Node.js 14+ (opcional para React)

Instalação Local
git clone https://github.com/seu-usuario/nl-cpc-translator.git
cd nl-cpc-translator

Execução

HTML/JS puro: abra index.html no navegador

React:

npm install
npm start


Acesse: http://localhost:3000

🌐 Deploy

Vercel ou Netlify recomendado

Alternativa: GitHub Pages

📹 Vídeo Demonstração

Assista aqui: https://www.youtube.com/watch?v=hKBdvN3Dxb4

🛠 Tecnologias Utilizadas

Frontend: HTML, CSS, JavaScript (React opcional)

Lógica/Algoritmos: Regex, Parsing recursivo, State Management

Deploy: Vercel, Netlify, GitHub Pages



📝 Licença

MIT License
