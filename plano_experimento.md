
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

Oportunidade: Utilizar a robusta taxonomia de 9 grupos proposta por OBrien et al. (2022) para classificar e comparar as SATDs. Isso permitirá identificar perfis de dívida técnica específicos para cada subárea, orientando a criação de ferramentas de suporte (linters, refatoração) especializadas por domínio.

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

Dívida Técnica Oculta em ML: Sculley et al. (2015) estabeleceram que sistemas de ML possuem custos de manutenção massivos e ocultos, muito além do código do modelo.

SATD em Deep Learning: Pepe et al. (2024) e Liu et al. (2020) começaram a explorar como frameworks de Deep Learning acumulam dívidas.

Taxonomia Abrangente: O trabalho seminal de OBrien et al. (2022) analisou 2.641 repositórios e propôs a classificação mais detalhada até o momento, identificando 23 tipos de SATD agrupados em 9 macro-categorias. Eles descobriram que "Data Dependency" e "Code Dependency" são prevalentes, mas não segmentaram essa análise comparativamente entre domínios de aplicação específicos (NLP vs CV), que é a lacuna que este TCC preencherá.
        
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

# 21. Referências 

* OBRIEN, D. et al. "23 Shades of Self-Admitted Technical Debt: An Empirical Study on Machine Learning Software". In: Proceedings of the 30th ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering (ESEC/FSE '22). Singapore: ACM, 2022. pp. 734–746. DOI: https://doi.org/10.1145/3540250.3549088.

* SCULLEY, D. et al. "Hidden Technical Debt in Machine Learning Systems". In: Proceedings of the 28th International Conference on Neural Information Processing Systems (NIPS). 2015.

* MALDONADO, E.; SHIHAB, E. "Detecting and quantifying different types of self-admitted technical debt". In: IEEE 7th International Workshop on Managing Technical Debt (MTD). 2015.

* PEPE, F. et al. "A Taxonomy of Self-Admitted Technical Debt in Deep Learning Systems". In: IEEE International Conference on Software Maintenance and Evolution (ICSME). 2024.
