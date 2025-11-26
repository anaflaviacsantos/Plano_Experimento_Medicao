
# 1. Identificação básica
## 1.1 Título do experimento

Análise Comparativa de Dívidas Técnicas Auto Admitidas em Domínios de Aprendizado de Máquina: NLP, Visão Computacional e Dados Tabulares

## 1.2 ID / código

TCC202601001

## 1.3 Versão do documento e histórico de revisão
| Versão | Data	| Alterações Principais |
| ------ | ----------| ----------------------------- |
v1.0 | 21/11/2025	| Criação do documento, definição do escopo e seleção dos domínios (seção 1) | 
v1.1 | 21/11/2025 | Adição da seção 2 e referências | 
v2.0 | 25/11/2025 | Adição da seção 3 |

## 1.4 Datas

Data de criação: 21/11/2025

Última atualização: 21/11/2025

## 1.5 Autores

Ana Flávia de Carvalho Santos

Área: Pesquisador/Graduando em Engenharia de Software

Contato: anafcs.academico@gmail.com 

## 1.6 Responsável principal (PI / dono do experimento)

Prof. Dra. Michelle Hanne Soares de Andrade 

Papel: Orientador Acadêmico e Supervisor Metodológico

Instituição: Pontifícia Universidade Católica de Minas Gerais 

## 1.7 Projeto / produto / iniciativa relacionada

Este experimento compõe a parte prática do Trabalho de Conclusão de Curso (TCC), inserido na linha de pesquisa de Engenharia de Software para Inteligência Artificial (SE4AI) e Mineração de Repositórios de Software (MSR). O objetivo é contribuir para o entendimento de como desenvolvedores de ML gerenciam qualidade de código em diferentes contextos de dados.

--------------------------

# 2. Contexto e problema
# 2.1 Descrição do problema / oportunidade

Problema: O desenvolvimento de sistemas de Machine Learning (ML) introduz complexidades que vão além do código tradicional, gerando tipos específicos de Dívida Técnica (TD). Embora existam estudos gerais sobre SATD (Self-Admitted Technical Debt) em ML, ainda não há clareza sobre como essas dívidas variam entre os diferentes domínios de aplicação (NLP, Visão Computacional e Dados Tabulares).
Atualmente, a literatura trata o "ML" como um monólito. No entanto, a hipótese é que a natureza dos dados e das bibliotecas impõe "dores" distintas: um projeto de NLP pode sofrer mais com dependência de dados (Data Dependency), enquanto um de Visão Computacional pode lutar mais com performance (Performance).

Oportunidade: Utilizar a taxonomia de 9 grupos proposta por OBrien et al. (2022) para classificar e comparar as SATDs. Com ela, será possível identificar perfis de dívida técnica auto admitida específicos para cada subárea, orientando a criação de ferramentas de suporte (linters, refatoração) especializadas por domínio.

## 2.2 Contexto organizacional e técnico

Este experimento será conduzido no contexto de pesquisa acadêmica em Engenharia de Software para Inteligência Artificial (SE4AI). O ambiente de análise é o ecossistema de software livre (Open Source).

Ambiente de Desenvolvimento: O estudo foca em repositórios hospedados no GitHub.

Stack Tecnológica: A análise será restrita à linguagem Python, predominante em Ciência de Dados.

Bibliotecas-Alvo:

* NLP: HuggingFace, NLTK, SpaCy, Gensim.

* Visão Computacional: OpenCV, Pillow, TorchVision, Albumentations.

* Dados Tabulares: Scikit-learn, Pandas, XGBoost, LightGBM.

Ferramental: Scripts de mineração e análise estatística com foco na análise dos comentários deixados pelos desenvolvedores.

## 2.3 Trabalhos e evidências prévias (internos e externos)

Dívida técnica oculta em ML: Sculley et al. (2015) estabeleceram que sistemas de ML possuem custos de manutenção massivos e ocultos, muito além do código do modelo.

SATD em deep learning: Pepe et al. (2024) e Liu et al. (2020) começaram a explorar como frameworks de Deep Learning acumulam dívidas.

Taxonomia abrangente: O trabalho seminal de OBrien et al. (2022) analisou 2.641 repositórios e propôs a classificação mais detalhada até o momento, identificando 23 tipos de SATD agrupados em 9 macro-categorias. Eles descobriram que "Data Dependency" e "Code Dependency" são prevalentes, mas não segmentaram essa análise comparativamente entre domínios de aplicação específicos (NLP vs CV), que é a lacuna que este TCC preencherá.
        
## 2.4 Referencial teórico e empírico essencial

Para a classificação das dívidas, este experimento adotará estritamente a taxonomia de 9 Grupos de SATD em ML definida por OBrien et al. (2022):

* Data Dependency: Dívidas relacionadas à integridade, fonte, versionamento e dependência dos dados (Ex: "TODO: normalize true states").

* Code Dependency: Problemas decorrentes da interação com bibliotecas externas, APIs legadas ou código "glue" (Ex: "FIXME: interactions with matplotlib").

* Awareness: Comentários que indicam falta de conhecimento ou incerteza do desenvolvedor sobre o algoritmo ou sistema (Ex: "TODO: does this handle N-dim tensors correctly?").

* Configurable Options: Dívidas em hiperparâmetros ou configurações hard-coded (Ex: "TODO: remove magic number").

* Modularity: Problemas de design, acoplamento e má separação de responsabilidades no pipeline de ML.

* Performance: Trechos de código lentos ou ineficientes identificados pelos devs (Ex: "TODO: optimize for CUDA").

* Scalability: Problemas relacionados à capacidade do sistema de escalar com mais dados ou requisições.

* Readability: Código confuso, nomenclatura ruim ou lógica difícil de seguir.

* Duplicate Code Elimination: Códigos copiados/colados que precisam ser unificados.

A hipótese central é que a distribuição percentual desses 9 grupos mudará drasticamente dependendo se o repositório é de Texto, Imagem ou Tabular.

----------------------------

# 3. Objetivos e questões (Goal / Question / Metric)
## 3.1 Objetivo geral

**Analisar** os comentários de código-fonte (SATD) em repositórios de Machine Learning, \
**com o propósito de** comparar e caracterizar as diferenças estruturais e qualitativas da dívida técnica, \
**em relação aos** domínios de NLP, Visão Computacional e Dados Tabulares, \
**sob o ponto de vista de** pesquisadores de engenharia de software, \
**no contexto de** projetos Open Source Python de alta relevância no GitHub.

## 3.2 Objetivos específicos (Resultados esperados)

Para alcançar o objetivo geral, definem-se 4 objetivos de conhecimento que buscam entender o fenômeno da dívida técnica:

1. Determinar se determinados domínios exigem mais esforço de manutenção corretiva ou evolutiva declarado, ou seja, tem maior densidade de dívidas do que outros.

2. Identificar quais categorias da taxonomia de OBrien et al. são as mais frequentes em cada tipo de problema de ML.

3. Compreender como os desenvolvedores expressam a criticidade dessas dívidas (uso de termos de urgência, fixmes vs. todos) e a complexidade descrita nos comentários.

4. Verificar se a popularidade, tamanho e estrutura de testes dos projetos influenciam a acumulação de diferentes tipos de SATD nos três domínios.

## 3.3 Questões de pesquisa / de negócio

| Objetivo Específico | Perguntas de Pesquisa (Questions) | Métricas Associadas (Metrics) |
| ------------------- | --------------------------------------------------------------------------------------------------------| -----------------------------------------------------|
| 1. Intensidade | Q1.1: Qual domínio apresenta a maior concentração de dívidas em relação ao volume de código produzido? | - Densidade Global de SATD<br> - Total de Arquivos com SATD |
|	| Q1.2: A dívida técnica está espalhada uniformemente ou concentrada em poucos arquivos "problemáticos"? | - Coeficiente de Gini da SATD<br>- Porcentagem de Arquivos Afetados | 
|	| Q1.3: Existe correlação entre o tamanho do arquivo e a quantidade de dívidas auto admitidas?	| - KLOC por Arquivo<br>- Contagem de SATD por Arquivo |
| O2. Natureza (Taxonomia) | Q2.1: Projetos de NLP sofrem significativamente mais de Data Dependency do que os outros domínios?	| - Taxa de Data Dependency<br>- Contagem Absoluta por Tipo |
|	| Q2.2: A dívida de Performance é o gargalo principal em projetos de Visão Computacional? | - Taxa de Performance Debt<br>- Contagem Absoluta por Tipo |
|	| Q2.3: Qual domínio apresenta a maior diversidade de tipos de problemas? | - Entropia de Shannon dos Tipos<br>- Tipo Dominante (Moda) |
| O3. Severidade/Urgência	| Q3.1: Qual domínio possui maior incidência de dívidas marcadas como críticas/bugs (FIXME) em vez de tarefas futuras (TODO)?	| - Razão FIXME/TODO<br>- Total de FIXME |
|	| Q3.2: Os comentários de dívida são mais complexos e verbosos em algum domínio específico?	| - Comprimento Médio do Comentário<br>- Contagem de Palavras SATD |
|	| Q3.3: Existe uso frequente de linguagem de "urgência" ou frustração nos comentários?	| - Taxa de Keywords de Urgência<br>- Taxa de Termos Negativos |
| O4. Maturidade/Contexto	| Q4.1: Projetos mais populares (mais estrelas) tendem a ter menor densidade de dívida técnica?	| - Número de Estrelas<br>- Densidade Global de SATD |
|	| Q4.2: A presença de uma cultura de testes (cobertura de arquivos de teste) reduz a incidência de SATD de Code Dependency?	| - Razão Código de Teste/Produção<br>- Taxa de Code Dependency |
|	| Q4.3: Projetos com maior número de contribuidores geram mais dívidas de Modularity (coordenação)?	| - Número de Contribuidores<br>- Taxa de Modularity Debt |
        
## 3.4 Métricas associadas (GQM)

| ID | Nome da Métrica	| Descrição	| Unidade |
| ----- | --------------- | ----------------------------------------------------------------------------------- | -------------- | 
| M01	| Densidade Global de SATD	| Razão entre o total de comentários SATD e o tamanho do projeto em milhares de linhas de código.	| SATD/KLOC |
| M02	| Total de Arquivos com SATD	| Contagem absoluta de arquivos que contêm pelo menos um comentário classificado como SATD.	| Inteiro (Qtd) |
| M03	| Porcentagem de Arquivos Afetados	| Porcentagem de arquivos do projeto que possuem SATD em relação ao total de arquivos.	| Porcentagem (%) |
| M04	| Coeficiente de Gini da SATD	| Medida de desigualdade (0 a 1) que indica se a SATD está concentrada em poucos arquivos (perto de 1) ou bem distribuída (perto de 0).	| Escalar (0.0 - 1.0) |
| M05	| KLOC por Arquivo	| Tamanho do arquivo em milhares de linhas de código (utilizado para normalização local).	| KLOC |
| M06	| Contagem Absoluta por Tipo	| Número de ocorrências de cada um dos 9 tipos da taxonomia de OBrien (ex: Data, Design, Infra).	| Inteiro (Qtd) |
| M07	| Taxa de tipos de dívida | A porcentagem que um tipo específico representa do total de SATD do projeto.	| Porcentagem (%) |
| M08	| Entropia de Shannon dos Tipos	| Medida da diversidade de tipos de dívida encontrados. Valores altos indicam "um pouco de tudo", baixos indicam foco em um problema.	| Escalar (Bits) |
| M09	| Razão FIXME/TODO	| Proporção entre comentários marcados como FIXME (geralmente bugs/críticos) sobre TODO (melhorias).	| Razão (Decimal) |
| M10	| Comprimento Médio do Comentário	| Média de caracteres ou palavras nos comentários de SATD (indicativo de complexidade da explicação).	| Caracteres ou Palavras |
| M11	| Taxa de Keywords de Urgência	| Proporção de comentários contendo palavras como "urgent", "now", "must", "hack", "error".	| Porcentagem (%) |
| M12	| Número de Estrelas	| Quantidade de "Stars" do repositório no GitHub (proxy para popularidade/relevância).	| Inteiro (Qtd) |
| M13	| Razão Código de Teste/Produção	| Razão entre KLOC de arquivos de teste (pasta tests/) e KLOC de arquivos de fonte.	| Razão (Decimal) |
| M14	| Número de Contribuidores	| Total de autores únicos que fizeram commits no repositório (proxy para tamanho do time).	| Inteiro (Pessoas)| 
| M15	| Taxa de Termos Negativos	| Frequência de palavras que denotam frustração ou sentimentos negativos fortes no comentário.	| Porcentagem (%)| 

# 21. Referências 

* OBRIEN, D. et al. "23 Shades of Self-Admitted Technical Debt: An Empirical Study on Machine Learning Software". In: Proceedings of the 30th ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering (ESEC/FSE '22). Singapore: ACM, 2022. pp. 734–746. DOI: https://doi.org/10.1145/3540250.3549088.

* SCULLEY, D. et al. "Hidden Technical Debt in Machine Learning Systems". In: Proceedings of the 28th International Conference on Neural Information Processing Systems (NIPS). 2015.

* MALDONADO, E.; SHIHAB, E. "Detecting and quantifying different types of self-admitted technical debt". In: IEEE 7th International Workshop on Managing Technical Debt (MTD). 2015.

* PEPE, F. et al. "A Taxonomy of Self-Admitted Technical Debt in Deep Learning Systems". In: IEEE International Conference on Software Maintenance and Evolution (ICSME). 2024.
