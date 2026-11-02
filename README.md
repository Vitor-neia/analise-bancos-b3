# Análise Exploratória de Bancos Listados na B3 📊🏦

> Quais bancos da B3 se destacam em valor de mercado, pagamento de dividendos, preço e rentabilidade?

![Painel de análise dos bancos da B3](img/painel_bancos_b3.png)

## Objetivo

Aplicar Análise Exploratória de Dados (EDA) aos principais indicadores fundamentalistas do setor bancário listado na B3, respondendo a quatro perguntas:

1. **Tamanho:** quais são os maiores bancos por valor de mercado? (A holding Itaúsa fica de fora para não distorcer o ranking.)
2. **Renda:** quais pagam os maiores dividendos (Dividend Yield, DY)?
3. **Preço × rentabilidade:** quais combinam P/L baixo e ROE alto? (matriz P/L vs. ROE)
4. **Valuation:** quais negociam abaixo do valor intrínseco, segundo a fórmula de Benjamin Graham? (`VI = √(22,5 × LPA × VPA)`)

## Principais resultados

- **Valor de mercado:** o **Itaú** lidera com **R$ 464,5 Bi**, seguido por **BTG Pactual (R$ 229,8 Bi)**, **Bradesco (R$ 204,7 Bi)**, **Banco do Brasil (R$ 139,1 Bi)** e **Santander (R$ 134,0 Bi)**. Os cinco maiores ficam muito acima dos demais (o sexto, Banco Pan, tem R$ 16,2 Bi).
- **Dividend Yield:** o **Banco do Estado de Sergipe** lidera com **18,44%**, seguido por **Banco BMG (11,12%)** e **Itaú (10,82%)**.
- **Margem de segurança (Graham):** as maiores margens ficaram com **Banco da Amazônia (66,2%)**, **Banco do Nordeste (63,2%)** e **BRB (60,3%)**. Bancos como **Banco Pan (-97,3%)** e **Banco Alfa de Investimento (-247,2%)** negociam acima do valor calculado.
- **Matriz P/L vs. ROE:** [preencha, ex.: "BMEB4 e PINE4 aparecem com ROE alto, e BRBI4 e BSLI4 combinam P/L baixo com ROE acima da mediana"].

> Os valores refletem os dados extraídos em [mês/ano]. Mercado financeiro muda, então os números de hoje serão diferentes.

## Dados

| Item | Detalhe |
|---|---|
| Fonte | [Status Invest](https://statusinvest.com.br/) (busca avançada de ações) |
| Extração | [mês/ano] |
| Tamanho | 25 ativos e 30 indicadores |
| Arquivo | `data/statusinvest-busca-avancada.csv` |

Colunas principais usadas: `PRECO`, `VPA`, `LPA`, `P/L`, `P/VP`, `ROE`, `DY` e `VALOR DE MERCADO`.

## Etapas da análise

1. **Importação e inspeção** da base (formato, tipos e valores nulos).
2. **Limpeza:** conversão do valor de mercado do formato brasileiro (`139.144.650.491,20`) para número e conversão para bilhões.
3. **Tratamento de outliers:** filtro no P/L (entre -20 e 50) para a matriz P/L vs. ROE.
4. **Cálculo do valor intrínseco (Graham)** e da margem de segurança, apenas para ativos com LPA e VPA positivos.
5. **Visualização:** 4 gráficos em um painel (barras, dispersão e margem de segurança), com `adjustText` para organizar os rótulos.

## Tecnologias

Python 3 · Pandas · NumPy · Matplotlib · Seaborn · adjustText · Jupyter Notebook / Google Colab

## Como executar

```bash
git clone https://github.com/Vitor-neia/Analise-Exploratoria-de-acoes-da-B3-com-foco-no-setor-Bancario.git
cd Analise-Exploratoria-de-acoes-da-B3-com-foco-no-setor-Bancario
pip install -r requirements.txt
jupyter notebook notebooks/analise_bancos.ipynb
```

> No notebook, o caminho do CSV deve apontar para `data/statusinvest-busca-avancada.csv`. Depois, execute as células em ordem.

## Estrutura do repositório

```
├── data/            # base do Status Invest (CSV)
├── img/             # gráficos exportados
├── notebooks/       # análise em Jupyter
├── requirements.txt
└── README.md
```

## Limitações

- **Retrato de um momento:** os dados são de uma única extração, sem série histórica.
- **Modelo de Graham é uma simplificação:** foi pensado para empresas industriais e não considera crescimento, risco nem as particularidades do setor bancário.
- **Bancos pequenos e pouco líquidos:** margens muito altas podem refletir baixa liquidez ou dados inconsistentes, e não uma oportunidade.
- **Poucos ativos:** são 25 papéis, o que limita conclusões estatísticas.

## Próximos passos

- Incluir séries históricas (preço, DY e ROE por ano).
- Calcular indicadores específicos de bancos (inadimplência e eficiência).
- Montar um dashboard interativo em Power BI.

---

## ⚠️ Aviso legal

Projeto desenvolvido com fins **estritamente educacionais**, para demonstrar habilidades práticas em Ciência de Dados. Os resultados **não constituem recomendação** de compra, venda ou manutenção de ativos financeiros.

**Autor:** Vitor Augusto Neias · [LinkedIn](https://www.linkedin.com/in/vitor-augusto-neias-278a91210/) · [Portfólio](https://vitorneiadata.com.br)
