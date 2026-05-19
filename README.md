# ☀️ Solar Tracker

Aplicativo web para acompanhar a geração de energia solar fotovoltaica e cruzar com os dados da fatura Neoenergia (CEB Brasília).

## O que faz

- Calcula a **economia real** considerando auto-consumo e energia injetada na rede
- Exibe **histórico mensal** com gráficos de economia e geração vs consumo
- Suporta **importação de faturas por IA** (API Anthropic) — envie um print e os campos são preenchidos automaticamente
- Sincronização entre dispositivos via **arquivo JSON no iCloud** (File System Access API) ou exportar/importar manualmente
- Funciona como **PWA** — pode ser instalado na tela inicial do iPhone/Android

## Como usar

1. Abra o app no navegador (ou instale como PWA)
2. Vá em **⚙️ Config** e preencha o nome da usina, potência instalada e geração esperada mensal
3. A cada mês, vá em **➕ Registrar** e preencha os dados da fatura:
   - Leituras do medidor (Energia Ativa e Energia Injetada)
   - Consumo faturado, tarifa e total a pagar
   - Geração solar do mês (app do inversor)

### Importação por IA

Configure sua chave de API Anthropic em ⚙️ Config → Importação por IA. Depois, na aba Registrar, arraste ou selecione um print da fatura — os campos são preenchidos automaticamente.

### Sincronização entre dispositivos

**Mac (Chrome/Edge/Safari):** vá em ⚙️ Config → Sincronização e clique em "Criar novo arquivo" ou "Selecionar solar_data.json". O app salva automaticamente na pasta do iCloud.

**iPhone/iPad:** use os botões "Exportar JSON" e "Importar JSON" para carregar o arquivo sincronizado via iCloud Drive.

## Campos da fatura Neoenergia

| Campo | Onde encontrar na fatura |
|---|---|
| Leitura anterior / atual | Tabela do medidor, linha **Energia Ativa** |
| Consumo faturado (kWh) | Itens da fatura, linha "Consumo", coluna **QUANT.** |
| Tarifa R$/kWh | Itens da fatura, linha "Consumo", coluna **Preço unit. com trib.** |
| Energia injetada (kWh) | Tabela do medidor, linha **Energia Injetada**, coluna Consumo |
| Total a pagar | Rodapé da fatura |

## Tecnologias

- HTML/CSS/JS puro — zero dependências de framework
- [Chart.js](https://www.chartjs.org/) para os gráficos
- [Tabler Icons](https://tabler-icons.io/) para os ícones
- File System Access API + IndexedDB para sincronização via arquivo local
- API Anthropic Claude para leitura de faturas por imagem

## Licença

MIT — veja [LICENSE](LICENSE)
