# Placar Eletrônico

Aplicação web de **placar eletrônico** para exibição em telas durante jogos (futebol, society etc.). Permite controlar placar, cronômetro, faltas e personalizar logos, patrocinadores e imagens de fundo.

---

## Aviso

Este projeto é privado e foi disponibilizado apenas para fins educacionais e de portfólio. Não é permitida a cópia, redistribuição ou utilização do código sem autorização do autor.

---

## Funcionalidades

- **Placar:** gols dos times da casa e visitante
- **Cronômetro:** tempo de jogo em formato HH:MM:SS (iniciar, pausar, zerar)
- **Faltas:** contador de faltas para cada time
- **Período:** alternar entre 1º e 2º tempo (1T / 2T)
- **Nomes dos times:** editáveis no header
- **Logo do campeonato:** central no header (imagem ou texto)
- **Logos dos times:** quadrados com borda verde (casa e visitante)
- **Patrocinadores:** nomes e logos em retângulos (casa e visitante)
- **Imagens de fundo:** uma imagem para o lado esquerdo e outra para o direito da tela (opcional)
- **Apito:** som de apito pelo teclado
- **Configurações:** modal (engrenagem) para editar nomes, logos e imagens de fundo
- **Persistência:** dados salvos no navegador (localStorage) e mantidos ao recarregar a página

---

## Atalhos de teclado

| Tecla | Ação |
|-------|------|
| **A** | +1 gol time da casa (ou +1 pênalti convertido no modo F4) |
| **Q** | -1 gol time da casa (ou marca pênalti perdido no modo F4) |
| **B** | +1 gol time visitante (ou +1 pênalti convertido no modo F4) |
| **E** | -1 gol time visitante (ou marca pênalti perdido no modo F4) |
| **S** | +1 falta time da casa |
| **D** | -1 falta time da casa |
| **F** | +1 falta time visitante |
| **G** | -1 falta time visitante |
| **Z** | Desfazer última cobrança de pênalti da **casa** (no modo F4) |
| **X** | Desfazer última cobrança de pênalti do **visitante** (no modo F4) |
| **W** | Tocar apito |
| **Espaço** ou **P** | Iniciar / pausar cronômetro (em time-out, Espaço pausa o time-out) |
| **R** | Zerar cronômetro |
| **T** | Alternar período (1T ↔ 2T) |
| **← / →** | -1 s / +1 s no tempo de jogo |
| **↑ / ↓** | +10 s / -10 s no tempo de jogo |
| **Shift + 1** | Reset **completo** (zera placar, imagens, logos, vídeos, cores) |
| **Shift + 2** | Reset **parcial** (zera só placar, faltas, tempo e pênaltis – mantém imagens) |
| **F2** | Mostrar / ocultar botão de configurações (engrenagem) |
| **F3** | Pedido de tempo técnico da **CASA** (1 min) — mostra qual time pediu e mantém histórico fixo |
| **Shift + F3** | Pedido de tempo técnico do **VISITANTE** (1 min) |
| **F4** | Alternar **modo pênaltis** (shootout) |
| **F5** | Zerar placar e sequência de pênaltis (apenas no modo F4) |
| **F6** | Iniciar contagem regressiva de cobrança (PREPARE-SE → 5,4,3,2,1) |
| **F7** | Reproduzir **vídeo 1** em tela cheia (configurar nas opções) |
| **F8** | Reproduzir **vídeo 2** em tela cheia (configurar nas opções) |
| **ESC** | Fechar vídeo em tela cheia |

*Os atalhos não funcionam quando o foco está em um campo de texto (input/textarea).*

### Dicas extras

- **Apagar pênalti errado:** clique diretamente na bolinha de uma cobrança para removê-la, ou use os botões "↶ Desfazer Casa / Visitante" na faixa de pênaltis, ou ainda as teclas **Z** / **X**.
- **Tempo técnico:** após pedir um tempo (F3 / Shift+F3), o nome do time pedinte aparece na faixa vermelha. Quando o tempo termina, um *badge* fixo "T · NOME ×N" permanece visível durante o restante da partida, mostrando quantos tempos cada equipe usou.
- **Vídeos em tela cheia:** carregue até dois vídeos no menu Configurações → "Vídeos em tela cheia (F7 / F8)". Pressione F7 / F8 para iniciar e ESC (ou o botão ✕) para fechar.
- **Placar acelerado:** no menu Configurações → seção "Cronômetro" → "Placar acelerado", escolha **1x**, **1.5x** ou **2x** para multiplicar a velocidade do cronômetro de jogo. O time-out técnico continua sempre em tempo real (1 s). Quando ativo (>1x), aparece um *badge* amarelo no canto do cronômetro indicando a velocidade em uso.

---



## Configurações (menu engrenagem)

No modal **Configurações** é possível:

- Nome do campeonato (texto em até 3 linhas)
- Logo do campeonato (imagem; máx. 2 MB e 512×512 px)
- Nomes dos times (casa e visitante)
- Logos dos times (casa e visitante)
- Período (1T, 2T etc.)
- Patrocinadores e logos (casa e visitante)
- **Imagem de fundo – lado esquerdo:** escolher arquivo ou **Remover imagem**
- **Imagem de fundo – lado direito:** escolher arquivo ou **Remover imagem**

Tudo é salvo automaticamente no navegador e restaurado ao recarregar a página.

---

## Especificações das imagens

| Área | Tamanho | Proporção | Comportamento |
|------|---------|-----------|---------------|
| Logo time (casa e visitante) | 240×240 px | 1:1 | `object-contain` |
| Patrocinador (casa e visitante) | 320×160 px | 2:1 | `object-cover` |
| Logo campeonato (header) | 80×80 px | 1:1 | `object-contain` |
| Imagem de fundo (esquerda/direita) | 50% da tela cada | — | `cover` (preenche a metade) |

---

## Tecnologias

- **Vite** – build e dev server
- **React** – interface
- **TypeScript** – tipagem
- **Tailwind CSS** – estilos
- **shadcn/ui** – componentes (Radix UI)
- **React Router** – rotas
- **Sonner** – notificações (toast)

---

## Estrutura do projeto

```
snap-and-style-lab-main/
├── src/
│   ├── components/
│   │   ├── Scoreboard.tsx   # Tela principal do placar
│   │   └── ui/             # Componentes de interface
│   ├── pages/
│   │   ├── Index.tsx        # Página inicial
│   │   └── NotFound.tsx
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── public/
├── package.json
└── README.md
```

---

## Licença

Este é um projeto privado e está disponível neste repositório exclusivamente para fins educacionais, demonstração de conhecimentos e composição de portfólio.

A reprodução, distribuição, modificação ou utilização deste projeto para fins comerciais não é permitida sem autorização prévia do proprietário.

Todos os direitos reservados.
