# Análise dos acidentes em vias brasileiras em 2025

Este repositório contém uma análise estatística e visual dos dados de acidentes de trânsito registrados pela Polícia Rodoviária Federal (PRF) durante o ano de 2025. O objetivo do projeto é identificar padrões, causas principais e as regiões mais afetadas por fatalidades nas rodovias do país.

O projeto foi desenvolvido em Python utilizando a biblioteca **Pandas** para manipulação e limpeza de dados, e **Matplotlib/Seaborn** para a geração de gráficos.

---

## Perguntas Respondidas

O script analisa a base de dados para responder a 6 perguntas estratégicas:
1. **Visão Geral:** Quais as UFs onde mais ocorrem acidentes fatais?
2. **Clima:** Qual condição meteorológica registra mais acidentes?
3. **Estrutura:** Qual sentido da via ocorrem mais acidentes?
4. **Fator Humano:** Qual a causa de acidentes mais comum?
5. **Dinâmica:** Qual o tipo de acidentes que mais ocorre?
6. **Localidade:** Quais são os 10 municípios com maior número de acidentes fatais?

---

## Principais Conclusões

1. **O fator humano supera as condições climáticas:** A esmagadora maioria dos acidentes acontece com o tempo em condições ideais (**Céu Claro**). Alinhado ao fato de que as principais causas são a **Ausência ou Reação Tardia do Condutor** (distração por celular, cansaço), fica claro que a imprudência e a falsa sensação de segurança do tempo bom são os maiores perigos.
2. **Distância de Segurança Negligenciada:** O tipo de acidente disparado mais comum é a **Colisão Traseira**, reflexo direto de motoristas trafegando muito próximos uns dos outros em velocidades que inviabilizam frenagens de emergência.
3. **Letalidade em Eixos de Carga e Perímetros Urbanos:** **Minas Gerais (MG)** lidera o ranking de estados com mais mortes devido à sua malha viária gigantesca e fluxo de escoamento. Já a nível municipal, **Brasília (DF)** e **Curitiba (PR)** aparecem no topo, evidenciando o perigo dos perímetros urbanos das BRs, onde o tráfego pesado se mistura com o trânsito local.

---

## Qualidade, Limpeza e Tratamento dos Dados

Para garantir a precisão dos gráficos, o arquivo bruto `datatran2025.csv` passou pelas seguintes etapas de engenharia de dados:

* **Completude:** A base original possui **72.529 registros** e apresenta excelente preenchimento. Apenas quatro colunas apresentaram valores nulos (`NaN`), todas administrativas e com menos de 0,1% de ausência (`classificacao_acidente`, `regional`, `delegacia`, `uop`). Nenhuma linha precisou ser descartada por falta de dados cruciais.
* **Correção de Encoding:** Ajustado para `latin-1` para evitar quebra de caracteres e erros de acentuação do padrão brasileiro.
* **Correção de Tipagem (Dados Numéricos):** Colunas como `km`, `latitude` e `longitude` vieram originalmente como texto devido ao uso da vírgula decimal brasileira ( ex: `546,2`). O script substitui a vírgula por ponto e força a conversão para `float64`.
* **Correção de Tipagem (Tempo):** As colunas `data_inversa` e `horario` foram convertidas para o formato nativo `datetime` do Pandas.
