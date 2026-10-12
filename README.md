# LogiSight — Dashboard de Inteligência Logística

Dashboard local para acompanhar veículos, leilões, permanência em pátio, custos e pendências. A aplicação usa HTML, CSS e JavaScript, com importação de planilhas no navegador.

## Estrutura do projeto

```text
Dashboard/
├── README.md
├── Leilão - 2026.xlsx                  # Base de trabalho
└── Dashboard_Inteligencia_Logistica/
    ├── index.html                     # Estrutura das telas
    ├── assets/
    │   ├── css/
    │   │   └── styles.css             # Estilos e responsividade
    │   └── js/
    │       ├── demo-data.js           # Dados fictícios de demonstração
    │       └── app.js                 # Lógica do dashboard
    └── data/
        └── modelo_base_logistica.xlsx # Planilha modelo
```

O HTML está indentado e possui comentários identificando cada tela. Os dados demonstrativos são carregados antes da lógica da aplicação.

## Como executar

1. Abra `Dashboard_Inteligencia_Logistica/index.html` em um navegador atualizado.
2. Clique em **Importar Excel** e selecione uma planilha `.xlsx`, `.xls` ou `.csv`.
3. A aplicação lê a primeira aba e atualiza os indicadores. A primeira linha deve conter os nomes das colunas.

Mantenha a pasta `assets` junto do HTML. Chart.js e SheetJS estão salvos em `assets/js/vendor`, então o dashboard funciona localmente sem depender de CDN. Não há instalação de dependências nem etapa de compilação.

Opcionalmente, execute na raiz do projeto:

```sh
python3 -m http.server 8000
```

Acesse http://localhost:8000/Dashboard_Inteligencia_Logistica/

## Funcionalidades

- Visão geral com indicadores, gráficos e filtros por status, leiloeiro e evento.
- Consulta da frota e busca de veículos.
- Acompanhamento de leilões, prazos e custos.
- Comparativo por leiloeiro e histórico de eventos.
- Alertas de pendências e permanência em pátio.
- Importação de planilhas, exportação da base filtrada em CSV e download de cabeçalhos em CSV.

## Colunas recomendadas

A planilha modelo está em `Dashboard_Inteligencia_Logistica/data/modelo_base_logistica.xlsx`.

| Grupo | Colunas |
| --- | --- |
| Identificação | `Placa`, `Modelo`, `Status` |
| Leilões | `Leiloeiro`, `Evento`, `Resultado_Lance` |
| Datas | `Data_Entrada_Patio`, `Data_Evento` |
| Valores | `Custo_Patio`, `Custo_Transporte`, `Valor_Lance` |
| Pendências | `Pendencia` |

Alguns nomes comuns em português são reconhecidos por aproximação. Utilize datas válidas do Excel ou textos interpretáveis. Os valores financeiros podem ser números ou textos em formato brasileiro.

## Onde editar

- `Dashboard_Inteligencia_Logistica/index.html`: estrutura e conteúdo das telas.
- `Dashboard_Inteligencia_Logistica/assets/css/styles.css`: aparência e regras responsivas.
- `Dashboard_Inteligencia_Logistica/assets/js/demo-data.js`: registros fictícios de demonstração.
- `Dashboard_Inteligencia_Logistica/assets/js/app.js`: indicadores, gráficos, filtros, importação e exportação.

Preserve os IDs utilizados pelo JavaScript e a ordem de carregamento dos scripts ao editar o HTML.

## Limites do protótipo

- Os dados demonstrativos são fictícios.
- As planilhas são processadas no navegador e não são enviadas a um servidor pelo código da aplicação.
- Os dados ficam na memória da página; ao recarregar, é necessário importar a planilha novamente.
- Não há autenticação, banco de dados, sincronização automática ou trilha de auditoria.
- As regras de alerta são ilustrativas e devem ser ajustadas à operação.
- Revise os cabeçalhos, a qualidade da base e as regras de negócio antes de usar os indicadores em decisões operacionais ou financeiras.
