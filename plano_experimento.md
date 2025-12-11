
# 1. Identificação básica
## 1.1 Título do experimento

Análise Comparativa de Dívidas Técnicas Auto Admitidas em Domínios de Aprendizado de Máquina: NLP, Visão Computacional e Dados Tabulares

## 1.2 ID / código

TCC202601001

## 1.3 Versão do documento e histórico de revisão
| Versão | Data	| Alterações Principais |
| ------ | ----------| ----------------------------- |
| v1.0 | 21/11/2025	| Criação do documento, definição do escopo e seleção dos domínios (seção 1) | 
| v1.1 | 21/11/2025 | Adição da seção 2 e referências | 
| v2.0 | 25/11/2025 | Adição da seção 3 |
| v2.1 | 26/11/2025 | Adição das seções 4, 5 e 6 | 
| v3.0 | 28/11/2025 | Adição da seções 7, 8, 9 | 
| v4.0 | 01/12/2025 | Adição da seção 10 | 
| v4.1 | 02/12/2025 | Adição da seção 11 e 12 | 
| v5.0 | 05/12/2025 | Adição da seção 13 |
| v5.1 | 05/12/2025 | Adição da seção 14 | 
| v6.0 | 09/12/2025 | Adição da seção 15 e 16 | 
| v6.1 | 11/12/2025 | Adição da seção 17 e 18 | 

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

Problema: O desenvolvimento de sistemas de Machine Learning (ML) introduz complexidades que vão além do código tradicional, gerando tipos específicos de Dívida Técnica (TD). Embora existam estudos gerais sobre SATD (Self-Admitted Technical Debt) em ML, ainda não há clareza sobre como essas dívidas variam entre os diferentes domínios de aplicação, como Natural Language Processing, Visão Computacional e Dados Tabulares.
Atualmente, a literatura trata o "ML" como um monólito. No entanto, a hipótese é que a natureza dos dados e das bibliotecas impõe problemas distintos.

Oportunidade: Utilizar a taxonomia de 9 grupos proposta por OBrien et al. (2022) para classificar e comparar as SATDs. Com ela, será possível identificar perfis de dívida técnica auto admitida específicos para cada subárea, orientando a criação de ferramentas de suporte, como linters, de refatoração, especializadas por domínio.

## 2.2 Contexto organizacional e técnico

Este experimento será conduzido no contexto de pesquisa acadêmica em Engenharia de Software para Inteligência Artificial (SE4AI). O ambiente de análise é o ecossistema de software Open Source.

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

* Data Dependency: Dívidas relacionadas à integridade, fonte, versionamento e dependência dos dados.

* Code Dependency: Problemas decorrentes da interação com bibliotecas externas, APIs legadas ou código "glue".

* Awareness: Comentários que indicam falta de conhecimento ou incerteza do desenvolvedor sobre o algoritmo ou sistema.

* Configurable Options: Dívidas em hiperparâmetros ou configurações hard-coded.

* Modularity: Problemas de design, acoplamento e má separação de responsabilidades no pipeline de ML.

* Performance: Trechos de código lentos ou ineficientes identificados pelos devs.

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

1. Investigar se diferentes domínios tem densidades de dívida de formas distintas, verificando se a SATD tende a se espalhar pelo sistema ou se concentrar densamente em arquivos problemáticos específicos de cada área.
2.  Analisar a associação estatística entre o domínio do problema e a categoria da dívida, determinando se cada área possui uma "assinatura" única de tipos de problemas.
3. Comparar como desenvolvedores de diferentes áreas priorizam suas dívidas, analisando se há divergência na proporção de correções críticas (FIXME) versus melhorias (TODO) e na complexidade descritiva dos comentários entre os domínios.
4. Verificar como fatores contextuais como idade do projeto, tamanho do arquivo e tamanho da equipe, influenciam a densidade e o tipo de dívida acumulada de maneira diferenciada em cada domínio.

## 3.3 Questões de pesquisa / de negócio

| Objetivo Específico | Perguntas de Pesquisa (Questions) | Métricas Associadas (Metrics)  |
|--------|------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| O1. Intensidade e Distribuição | Q1.1: A densidade global de SATD difere estatisticamente entre os três domínios analisados? | - Densidade Global de SATD<br>- Média de SATD por Arquivo  |
| | Q1.2: A concentração de dívida dentro dos projetos varia conforme o domínio? | - Coeficiente de Gini da SATD<br>- Porcentagem de Arquivos Afetados  |  
| | Q1.3: Existe correlação entre o tamanho físico do arquivo (LOC) e a quantidade de SATD, e essa correlação é mais forte em algum domínio específico? | - Correlação de Pearson/Spearman<br>- KLOC do Arquivo<br>- SATD por Arquivo  |  
| O2. Perfil Tipológico | Q2.1: Existe uma dependência estatística significativa entre o domínio e a categoria de dívida? | - Tabela de Contingência (Domínio x Tipo)<br>- Valor-p (Chi-Quadrado)  |
| | Q2.2: Qual domínio apresenta a maior diversidade de tipos de dívida, indicando problemas mais heterogêneos? | - Entropia de Shannon dos Tipos<br>- Contagem de Tipos Únicos  |  
| | Q2.3: O tipo de dívida predominante é distinto para cada um dos três domínios? | - Moda do Tipo de Dívida<br>- Frequência Relativa da Moda  |  
| O3. Severidade e Comunicação | Q3.1: A proporção de dívidas marcadas como críticas (FIXME) em relação a melhorias (TODO) varia significativamente entre os domínios? | - Razão FIXME/TODO<br>- Contagem Absoluta de FIXME  |
| | Q3.2: Os comentários de dívida em determinados domínios são mais verbosos/complexos, sugerindo problemas de maior carga cognitiva? | - Comprimento Médio do Comentário<br>- Contagem de Palavras  |  
| | Q3.3: A frequência de termos de urgência (ex: "hack", "urgent", "now") nos comentários difere entre os domínios? | - Densidade de Keywords de Urgência  |  
| O4. Maturidade e Contexto | Q4.1: Repositórios mais antigos tendem a reduzir ou aumentar sua densidade de dívida de forma diferente dependendo do domínio? | - Idade do Repositório<br>- Densidade Global de SATD  |
| | Q4.2: O número de contribuidores no projeto impacta a densidade de dívida de maneira distinta entre NLP, CV e Tabular? | - Número de Contribuidores<br>- Densidade Global de SATD  |  
| | Q4.3: Arquivos "legados" concentram tipos específicos de dívida em comparação a arquivos novos, variando por domínio? | - Idade do Arquivo<br>- Tipo de Dívida |  
        
## 3.4 Métricas associadas (GQM)

| ID | Nome da Métrica | Descrição | Unidade  |
|---|---|---|---|
| M01 | Densidade Global de SATD | Total de SATD dividido pelo tamanho total do projeto (normalização). | SATD / KLOC  |
| M02 | SATD por Arquivo | Quantidade absoluta de comentários de dívida encontrados em um único arquivo de código. | Inteiro (Quantidade)  |
| M03 | KLOC do Arquivo | Tamanho de um arquivo específico em milhares de linhas de código. | KLOC  |
| M04 | Coeficiente de Gini da SATD | Medida estatística que indica o grau de concentração das dívidas nos arquivos do projeto. | Escalar (0.0 - 1.0)  |
| M05 | Porcentagem de Arquivos Afetados | Razão entre arquivos com SATD > 0 e o total de arquivos do projeto. | Porcentagem (%)  |
| M06 | Correlação de Pearson/Spearman | Coeficiente estatístico que mede a força da relação linear entre duas variáveis. | Escalar (-1.0 a 1.0)  |
| M07 | Contagem por Tipo | Frequência absoluta de cada um dos 9 tipos da taxonomia de OBrien. | Inteiro (Qtd)  |
| M08 | Entropia de Shannon dos Tipos | Medida de incerteza/diversidade da distribuição dos tipos de dívida dentro de um domínio. | Bits  |
| M09 | Moda do Tipo de Dívida | A categoria de dívida que aparece com maior frequência no conjunto. | Categórica (Nominal)  |
| M10 | Razão FIXME/TODO | Divisão entre o número de tags FIXME e o número de tags TODO. | Razão (Decimal)  |
| M11 | Comprimento Médio do Comentário | Média de caracteres contidos na string do comentário de dívida. | Caracteres  |
| M12 | Densidade de Keywords de Urgência | Frequência de palavras de urgência (urgent, critical, panic) sobre o total de palavras nos comentários. | Porcentagem |
| M13 | Idade do Repositório | Tempo decorrido desde o primeiro commit até a data da coleta. | Dias  |
| M14 | Número de Contribuidores | Contagem de autores distintos (e-mail/user) no histórico do git. | Inteiro (Pessoas)  |
| M15 | Idade do Arquivo | Tempo decorrido desde a criação do arquivo no repositório. | Dias  |
| M16 | Valor-p (Chi-Quadrado) | Resultado do teste de hipótese para verificar independência entre variáveis categóricas. | Probabilidade (0 a 1) |

-----------------------------------------------------

# 4. Escopo e contexto do experimento
## 4.1 Escopo funcional / de processo (incluído e excluído)

Incluído no Escopo:

* Artefatos: Arquivos de código-fonte com extensão .py e arquivos de configuração relacionados (ex: requirements.txt) contidos na branch principal.
* Domínios de ML: Repositórios categorizados explicitamente no GitHub com tópicos relacionados a Processamento de Linguagem Natural (NLP, transformers, text-mining).
Visão Computacional (computer-vision, object-detection, image-processing) e Dados Tabulares/Clássico (tabular-data, scikit-learn, gradient-boosting).
* Atividades: Mineração de comentários através de keywords (TODO, FIXME, HACK, XXX), classificação manual baseada na taxonomia de 9 tipos de OBrien et al. (2022) e análise estatística dos dados.
* Período: Histórico de commits dos repositórios até a data de extração.

Excluído do Escopo:
* Outras linguagens: Arquivos em C++, R, Julia ou Java, mesmo que presentes no repositório.
* Outros domínios: Projetos de Aprendizado por Reforço, Áudio/Fala ou Robótica, para manter a comparação focada nos três pilares principais.
* Análise Dinâmica: Não haverá execução do código, treinamento de modelos ou testes de performance em tempo de execução.
* Dívida não admitida: Dívidas técnicas identificadas apenas por ferramentas de análise estática ou code smells que não possuam um comentário explicativo do desenvolvedor não serão considerados.

## 4.2 Contexto do estudo
O estudo configura-se como uma pesquisa empírica observacional baseada em Mineração de Repositórios de Software (MSR).

* Organização/Ambiente: Ecossistema Open Source GitHub.
* Tipo de Projeto: Bibliotecas, frameworks e aplicações de Machine Learning de relevância comunitária filtrados por popularidade/estrelas.
* Perfil dos Participantes: Desenvolvedores de software e cientistas de dados voluntários ou profissionais. A experiência é heterogênea, variando de estudantes a engenheiros sêniores de grandes corporações (ex: Google, Meta) que contribuem para projetos abertos.
* Processo de Desenvolvimento: Varia por projeto, mas assume-se o uso de controle de versão e práticas modernas de Pull Requests.

## 4.3 Premissas
Para a viabilidade do experimento, assume-se que:

* Os desenvolvedores utilizam comentários no código para documentar pendências e dívidas técnicas, refletindo a realidade do projeto.
* A API do GitHub e os repositórios selecionados permanecerão públicos e acessíveis durante o período de coleta de dados.
* As palavras-chave selecionadas (TODO, FIXME, HACK, XXX) cobrem a vasta maioria das dívidas auto admitidas, conforme validado na literatura prévia (Maldonado & Shihab).
* A biblioteca PyDriller é capaz de iterar corretamente sobre o histórico de projetos massivos sem perda significativa de dados.
  
## 4.4 Restrições
Limitações práticas e mandatórias para a execução do TCC:

* A classificação manual dos tipos de dívida será realizada por apenas 1 pesquisador (o aluno), com validação pontual do orientador.
* Devido à restrição humana, a classificação qualitativa detalhada será limitada a uma amostra estatisticamente representativa de aproximadamente 500 a 600 comentários no total, e não ao universo completo de dados extraídos.
* O experimento deve ser concluído, analisado e redigido até no máximo novembro de 2026.
* A mineração deve ser executável em computador pessoal padrão, inviabilizando uma análise de todos os repositórios disponíveis.

## 4.5 Limitações previstas
Fatores que podem ameaçar a validade ou generalização dos resultados:

* Os resultados refletem projetos Open Source em Python. Não podem ser generalizados imediatamente para software proprietário ou outras linguagens.
* A interpretação de um comentário como pertencente a uma categoria pode ser subjetiva. Mesmo usando a taxonomia de OBrien, existe o risco de viés do classificador único.
* Projetos com muitas estrelas podem ter padrões de qualidade muito superiores à média do mercado, potencialmente subestimando a densidade real de dívida em projetos menores.
* Dívidas descritas sem as palavras-chave padrão não serão detectadas.

---------------------------------------------------------

# 5. Stakeholders e impacto esperado
## 5.1 Stakeholders principais
Os grupos interessados ou afetados pelos resultados deste experimento dividem-se em duas categorias: acadêmicos e mebros da indústria.

* Pesquisadores em Engenharia de Software (SE4AI): A comunidade acadêmica interessada na interseção entre IA e qualidade de software.
* Engenheiros de Machine Learning e Cientistas de Dados: Profissionais que desenvolvem e mantêm as bibliotecas analisadas ou aplicações baseadas nelas.
* Mantenedores de projetos Open Source: Os principais contribuidores dos repositórios analisados (ex: times da HuggingFace, Scikit-Learn, Ultralytics).
* Criadores de ferramentas: Desenvolvedores de IDEs, linters e analisadores estáticos.
* Equipe do projeto: O pesquisador e o orientador.
  
## 5.2 Interesses e expectativas dos stakeholders

* Pesquisadores (SE4AI): Esperam evidências empíricas que validem se a taxonomia de dívida técnica auto admitida precisa ser especializada por domínio. 
* Engenheiros de ML / Cientistas de Dados: Buscam diretrizes práticas sobre onde focar a atenção durante revisões de código. 
* Mantenedores Open Source: Podem utilizar os resultados para identificar pontos cegos na manutenção de seus projetos. 
* Criadores de ferramentas: Esperam insights para desenvolver novas regras de detecção automática.
* Equipe do projeto: Buscam contribuir com a comunidade científica da área. 
  
## 5.3 Impactos potenciais no processo / produto
Considerando a natureza observacional de dados históricos, os impactos são classificados da seguinte forma:

Durante a execução:
* Como o estudo utiliza repositórios públicos, não haverá interrupção ou alteração no fluxo de trabalho das equipes que mantêm esses softwares, nenhum código de produção será modificado.
* A fase de classificação manual das dívidas é intensiva e pode impactar o cronograma do TCC se a amostra for subestimada.
  
Pós-Execução (Resultados e Conhecimento):
* O estudo pode sugerir a alteração de guidelines de revisão de código em empresas de IA, recomendando que revisores verifiquem tipos de dívida específicos dependendo se o modelo é de Visão ou Texto.
* Os resultados podem fundamentar a criação de ferramentas de auxílio ao desenvolvimento que priorizem a refatoração de um tipo de dívida específico para um dos domínios.
* A publicação dos resultados aumenta a consciência sobre a importância de documentar dívidas técnicas de forma clara, incentivando melhores práticas de comentários entre desenvolvedores novatos.

-----------------------------------------------------------

# 6. Riscos de alto nível, premissas e critérios de sucesso
## 6.1 Riscos de alto nível
Identificação dos principais obstáculos que podem comprometer a execução ou a validade científica do TCC:

* A classificação manual dos comentários na taxonomia de 9 tipos depende de interpretação humana. Existe o risco de inconsistência, onde o mesmo comentário poderia ser classificado de forma diferente em momentos distintos.O impacto principal é a baixa confiabilidade dos dados.
* As keywords (TODO, FIXME) podem retornar comentários irrelevantes, por exemplo textos explicativos em strings, documentação gerada automaticamente, que não configuram dívida técnica real, assim aumentando o esforço manual de filtragem e possívelmente desencadeando a necessidade de minerar mais dados. 
* Dificuldade em isolar repositórios de um só domínio, muitos projetos modernos de Deep Learning utilizam visão e texto simultaneamente, o que pode contaminar a comparação entre domínios.
* A possibilidade de os testes estatísticos não rejeitarem a hipótese nula, indicando que não há diferença perceptível entre os domínios.

## 6.2 Critérios de sucesso globais 
O experimento será considerado bem-sucedido e seus dados válidos para defesa do TCC se:

* For possível coletar e classificar uma amostra que garanta, no mínimo, 95% de nível de confiança e 5% de margem de erro para cada domínio (estimado em 500 a 600 comentários totais classificados).
* A validação cruzada de uma sub-amostra (10% dos dados) atingir um índice Kappa de Cohen > 0.60 (concordância substancial) entre o pesquisador e uma segunda revisão (orientador ou reanálise temporal).
* Os dados permitirem a execução dos testes de hipótese, gerando p-values conclusivos para as métricas de densidade e distribuição.
* O script de mineração e os datasets gerados estiverem organizados de forma que qualquer outro pesquisador possa replicar a extração.
  
## 6.3 Critérios de parada antecipada 
O experimento deverá ser interrompido ou reformulado antes da fase de análise se:
* Não for possível identificar pelo menos 50 repositórios qualificados para um dos domínios.
* Se, em uma extração piloto de 5 repositórios, verificar-se que mais de 60% dos comentários extraídos são falsos positivos, inviabilizando a limpeza manual dentro do prazo do TCC.
* Se a biblioteca PyDriller apresentar incompatibilidade técnica intransponível com o histórico de grandes repositórios, exigindo o desenvolvimento de um minerador próprio do zero.

---------------------------------------------------------

# 7. Modelo conceitual e hipóteses
## 7.1 Modelo conceitual do experimento

O modelo conceitual pressupõe que a natureza dos dados impõe desafios de engenharia de dados de formas diferentes, que se manifestam como tipos diferentes de dívida técnica admitida pelos autores. E acredita-se que o domínio de aplicação influencia diretamente o perfil da SATD da seguinte forma: 

* NLP: Exige pipelines de tokenização e limpeza complexos e instáveis.<br> Expectativa: Maior incidência de Data Dependency e Awareness, devido à complexidade de modelos como Transformers.

* Visão Computacional: Lida com tensores de alta dimensionalidade e gargalos de GPU. <br> Expectativa: Maior incidência de Performance e Configurable Options.

* Dados Tabulares: Frequentemente integra regras de negócio e múltiplas fontes de dados heterogêneas. <br> Expectativa: Maior incidência de Code Dependency e Modularity.

## 7.2 Hipóteses formais (H0, H1)

### RQ1 (Intensidade e Distribuição)
         
* H0: Não há diferença significativa na densidade mediana de SATD entre os projetos de NLP, Visão Computacional e Dados Tabulares.
* H1: Pelo menos um dos domínios apresenta uma densidade mediana de dívida técnica diferente dos demais.

### RQ2 (Perfil Tipológico)

* H0: A distribuição das categorias de dívida é independente do domínio de aplicação, ou seja, a proporção de tipos de dívida é a mesma em qualquer domínio.
* H1: Existe uma dependência estatística entre o domínio e o tipo de dívida encontrada.

### RQ3 (Severidade e Comunicação)

* H0: A proporção entre comentários críticos e comentários de tarefas é igual entre os três domínios.
* H1: Determinados domínios apresentam uma proporção significativamente maior de comentários críticos, indicando maior urgência ou severidade na dívida acumulada.

### RQ4 (Maturidade e Contexto)

* H0: Não existe correlação estatisticamente significativa entre os fatores de maturidade do projeto e a densidade de dívida técnica em nenhum dos domínios.
* H1: Existe uma correlação significativa entre a maturidade/tamanho da equipe e a densidade de dívida técnica.

## 7.3 Nível de significância e considerações de poder

Para o nível de significância será adotado o padrão científico de 0.05 (5%). Resultados com p-value < 0.05 levarão à rejeição da hipótese nula.

Considerando a taxonomia de 9 tipos e 3 domínios (matriz 9x3 = 27 células), e sabendo que alguns tipos de dívida são raros, planeja-se uma amostra total classificada manualmente de aproximadamente 600 SADTs, 200 por cada dominio. Este tamanho amostral é suficiente para detectar um tamanho de efeito médio com um poder estatístico superior a 0.80.

--------------------------------------------------------

# 8. Variáveis, fatores, tratamentos e objetos de estudo
## 8.1 Objetos de estudo

Os objetos primários de análise são os repositórios de software Open Source hospedados no GitHub, especificamente os arquivos de código-fonte (.py) neles contidos. A unidade granular de análise é o comentário de código identificado como SATD através de padrões léxicos.

## 8.2 Sujeitos / participantes (visão geral)

Os participantes são indiretos e não-intencionais, que é a população global de desenvolvedores de software, engenheiros de Machine Learning e cientistas de dados que contribuíram para os repositórios selecionados ao longo de sua história. Esta população é heterogênea, variando de estudantes e entusiastas a profissionais sêniores de grandes empresas de tecnologia.

## 8.3 Variáveis independentes (fatores) e seus níveis

O fator principal que governa a comparação neste experimento é o domínio de aplicação do software.

* Fator: Domínio de Machine Learning.
* Níveis: <br>
(1) Processamento de Linguagem Natural (NLP) <br>
(2) Visão Computacional (CV) <br> 
(3) Dados Tabulares

## 8.4 Tratamentos (condições experimentais)

Por ser um estudo observacional, não há manipulação ativa de variáveis. Os "tratamentos" correspondem aos estratos da amostragem.

* Tratamento 1 (NLP): Análise de repositórios dedicados exclusivamente a texto <br> Ex: spaCy, Gensim.

* Tratamento 2 (CV): Análise de repositórios dedicados exclusivamente a imagem/Ex: YOLO, OpenCV-Python.

* Tratamento 3 (Tabular): Análise de repositórios dedicados a dados estruturados/clássicos 
Ex: XGBoost, Pandas.


## 8.5 Variáveis dependentes (respostas)

As respostas observadas são as características da dívida técnica auto admitida:

* Densidade: Quantidade de SATD normalizada pelo tamanho do código.
* Distribuição Tipológica: Classificação qualitativa da dívida.
* Severidade: Razão de bugs (FIXME) sobre tarefas (TODO).
* Maturidade: Coeficientes estatísticos que medem o impacto da maturidade e do tamanho da equipe sobre a densidade de dívida.

## 8.6 Variáveis de controle / bloqueio

Fatores mantidos constantes ou restringidos para isolar o efeito do Domínio e garantir uma comparação justa:

* Linguagem de programação será sempre Python.
* Apenas projetos com mais de 50 estrelas para manter a relevância.
* Apenas projetos com commits nos últimos 2 anos.

## 8.7 Possíveis variáveis de confusão conhecidas

Fatores externos que podem influenciar os resultados, mas que não são o foco principal:

* Idade do repositório: Projetos mais antigos tendem a acumular mais dívida naturalmente.
* Tamanho da equipe: Projetos com centenas de contribuidores podem ter padrões de documentação diferentes de projetos de um único autor.
* Estilo de governança: Projetos corporativos podem ter regras de linting mais rígidas que projetos comunitários.

## 8.8 Tabelas 

### Tabela de variáveis 

| Tipo de Variável | Nome | Descrição | Unidade/Escala |
|---|---|---|---|
| Independente | Domínio de Aplicação | O nicho tecnológico principal do repositório. | Nominal (NLP, CV, Tabular) |
| Dependente | Densidade de SATD | Frequência de comentários de dívida por linhas de código. | Razão (SATD/KLOC) |
| Dependente | Categoria da SATD | Classificação do comentário segundo taxonomia de OBrien. | Nominal (9 Categorias) |
| Dependente | Razão de Severidade | Proporção de comentários indicando erro/bug crítico. | Razão (FIXME/TODO) |
| Controle | Linguagem | Linguagem de programação analisada. | Nominal (Python) |
| Controle | Popularidade Mínima | Limite inferior de estrelas para inclusão. | Ordinal (> 50 stars) |
| Confusão | Idade do Projeto | Tempo de vida do repositório. | Intervalar (Dias) |
| Confusão | Tamanho da Equipe | Número de contribuidores únicos. | Inteiro |

### Tabela de fator e tratamentos 

| Fator Experimental | Níveis (Tratamentos) | Descrição do Grupo |
|---|---|---|
| Domínio de ML | 1. NLP | Repositórios focados em texto (Transformers, Tokenizers). |
|  | 2. Visão Computacional | Repositórios focados em imagem (Detection, OCR). |
|  | 3. Tabular | Repositórios focados em dados estruturados (Boosting, Regressão). |

----------------------------------------

# 9. Desenho experimental
## 9.1 Tipo de desenho

O estudo utilizará um Desenho Observacional Transversal com Amostragem Aleatória Estratificada.

A justificativa se baseia no fato que o desenho é estratificado pois dividimos a população em três subgrupos distintos (NLP, CV, Tabular) e "aleatório" na seleção dos itens individuais (comentários) dentro de cada estrato. Essa abordagem é a mais adequada pois garante que, mesmo que um domínio tenha muito mais volume total de comentários no GitHub, a análise manual será feita sobre uma quantidade igual de itens para cada grupo, evitando viés de prevalência.

## 9.2 Randomização e alocação

A randomização ocorrerá no nível da dívida técnica, seguindo um processo de funil em três etapas:

1. Coleta e extração: Selecionaremos um número alto de repositórios de cada domínio para garantir volume. Serão coletados cerca de 5000 repositórios por domínio. Depois extrairemos todos os comentários contendo as keywords desses repositórios, criando três conjuntos de candidatos a SATD.

2. Sorteio da amostra: Utilizando um script com random.sample() e seed fixa, sortearemos aleatoriamente 300 candidatos a SATD de cada domínio a partir desses conjuntos.

3. Seleção final: Desses 300 sorteados, os primeiros 200 que forem validados manualmente como "verdadeiros positivos", que são realmente dívida técnica e não falso positivo, comporão a amostra final de classificação.

## 9.3 Balanceamento e contrabalanço

* Balanceamento: O experimento será balanceado pela tamanho da amostra de comentários, e não pelo número de repositórios. Cada um dos três grupos contribuirá com exatamente o mesmo número de instâncias classificadas, sendo a meta 200 SATDs válidas por grupo, totalizando 600 análises. Isso assegura que nenhum domínio tenha peso desproporcional na análise estatística comparativa.

* Contrabalanço: Não aplicável, pois não há efeito de ordem ou aprendizado, o comentário extraído é estático e a análise não é repetida no mesmo objeto sob condições diferentes.

## 9.4 Número de grupos e sessões

Para esse estudo, haverão 3 grupos experimentais:

1. Amostra de SATD de NLP.
2. Amostra de SATD de Visão Computacional.
3. Amostra de SATD de Dados Tabulares.

Haverá uma sessão única de mineração e classificão, pois os dados representam um snapshot do estado atual da dívida técnica nos projetos. Não haverá coleta de acompanhamento ao longo do tempo, focando na caracterização do perfil atual. Só serão feitas mais sessões caso a primeira não satisfaça o número esperado de dívidas a serem classificadas.

-------------------------------------------

# 10. População, sujeitos e amostragem
## 10.1 População-alvo

A população-alvo compreende o universo de comentários de dívida técnica auto admitida inseridos no código de projetos de Machine Learning Open Source.
Esta população representa os desafios técnicos e decisões de design tomadas pela comunidade global de desenvolvedores de Python, desde engenheiros de grandes tech companies até pesquisadores acadêmicos, que mantêm bibliotecas de NLP, Visão Computacional e Dados Tabulares.

## 10.2 Critérios de inclusão de artefatos

Para que um repositório e seus comentários sejam elegíveis para o estudo, devem atender aos seguintes requisitos:

Repositório:

* Hospedado no GitHub.
* Linguagem principal deve ser Python em mais de 50% do código.
* Mínimo de 50 estrelas.
* Possuir commits realizados nos últimos 12 meses.
* Deve possuir tópicos explícitos identificando o domínio (ex: nlp, computer-vision, tabular).

Comentário (SATD):

* Conter uma das keywords de admissão: TODO, FIXME, HACK, XXX.
* Estar localizado dentro de um arquivo com extensão .py.
* Estar escrito em inglês. 

## 10.3 Critérios de exclusão de artefatos 

Serão removidos da análise:

* Projetos que misturam domínios, por exemplo uma biblioteca que faz "Image Captioning", unindo CV e NLP, pois impediriam a atribuição da dívida a um domínio específico.
* Projetos identificados como listas de exercícios e tutoriais, pois não refletem a pressão de desenvolvimento de software real.
* Comentários gerados automaticamente por ferramentas.
* Keywords encontradas dentro de strings de print/log que são mensagens para o usuário final, e não anotações para o desenvolvedor.
* Comentários de licença ou copyright.

## 10.4 Tamanho da amostra planejado

Seguindo a estratégia de funil definida no desenho experimental:

* 5000 repositórios por domínio para garantir volume massivo de dívidas brutas.
* 200 comentários extraídos e validados, por domínio, ou seja: 200 SADTs de NLP, 200 de Visão Computacional e 200 de Dados Tabulares.
* No total 600 instâncias de dívida técnica auto admitida classificadas manualmente.
  
Este número fornece poder estatístico suficiente para detectar tamanhos de efeito médios em testes qui-quadrado (graus de liberdade = 16 na tabela 9x3), mantendo a viabilidade de execução manual.

## 10.5 Método de seleção / recrutamento

A seleção será realizada de forma automatizada e aleatória:

* Coleta: Script (PyDriller/GitHub API) coleta todos os candidatos a SATD.
* Randomização: Todos os candidatos de um domínio são colocados em uma lista única e embaralhados com random.shuffle.
* Seleção sequencial: O pesquisador analisa os candidatos na ordem sorteada, se for um falso positivo, descarta e pega o próximo, e se for uma SATD válida, classifica e adiciona ao grupo.
* Parada: O processo cessa quando o contador do grupo atinge 200 itens válidos.
  
## 10.6 Treinamento e preparação 

Como os "sujeitos" são inanimados, o treinamento é feito pelo pesquisador para mitigar a subjetividade:

1. Leitura aprofundada das definições e exemplos do paper de OBrien et al. (2022).
2. Rodada piloto com a classificação de 30 comentários aleatórios (10 de cada domínio) que não farão parte da amostra final.
3. Discussão dessa classificação piloto com o orientador para alinhar o entendimento.
4. Criação de um guia de consulta rápida com exemplos canônicos de cada um dos 9 tipos de dívida para manter a consistência durante as sessões de classificação.

-----------------------------------------------

# 11. Instrumentação e protocolo operacional
## 11.1 Instrumentos de coleta

Para executar a mineração e análise, serão desenvolvidos e utilizados os seguintes instrumentos:

* Script de seleção: Script Python que consome a API do GitHub, biblioteca PyGithub, para buscar e filtrar repositórios baseados em tópicos (nlp, cv, tabular), quantidade de estrelas e data do último commit.
* Script de mineração: Script baseado na biblioteca PyDriller responsável por: clonar temporariamente ou iterar remotamente os repositórios selecionados, percorrer a árvore de arquivos e identificar linhas contendo as keywords (TODO, FIXME, HACK, XXX).
* Planilha de classificação: Planilha no Google Sheets ou Excel, gerada após a amostragem aleatória, contendo as colunas: ID, Domínio, Link_GitHub, Texto_Comentario, Classificação_Manual e Observações.
* Notebook de Análise: Jupyter Notebook utilizando Pandas, SciPy e Seaborn para carregar os dados classificados, calcular as métricas e executar os testes estatísticos.

## 11.2 Materiais de suporte

Como o participante da classificação é o próprio pesquisador, os materiais servem para garantir a consistência interna:

* Guia de referência da taxonomia de dívidas: Um documento PDF de uma página contendo a definição resumida dos 9 tipos de dívida de OBrien et al., com 2 ou 3 exemplos canônicos de cada tipo para consulta rápida durante a classificação.
* Protocolo de Desempate: Um fluxograma de decisão para lidar com comentários ambíguos.

## 11.3 Procedimento experimental 

### 11.3.1 Fase de Seleção e Coleta Automática:
1. Executar o script de seleção para gerar a lista de URLs dos repositórios alvo (Top 5000 por domínio).
2. Executar o script de mineração para extrair todas as ocorrências de SATD brutas.
3. Gerar o dataset contendo centenas de candidatos a dívida.

### 11.3.2 Fase de Amostragem e Preparação:
4. Executar script de randomização para embaralhar os dados de cada domínio.
5. Exportar os primeiros 300 itens sorteados de cada grupo para a planilha de classificação.
   
### 11.3.3 Fase de Classificação Manual:
6. O pesquisador abre a planilha e clica no link do GitHub para ver o contexto do código.
7. Verifica se é um falso positivo. Se sim, descarta.
8. Se for válido, seleciona a categoria adequada.
9. Repete-se o processo até atingir a cota de 200 válidos por domínio.
    
### 11.3.4 Fase de Validação:
10. O orientador seleciona aleatoriamente 10% da amostra classificada e realiza uma "revisão cega".
11. Calcula-se o Kappa de Cohen. Se for menor que 0.7, o pesquisador revisa seus critérios e reclassifica os dados duvidosos.

### 11.3.4 Fase de Análise de Dados:
12. O script de análise ingere a planilha final.
13. Gera tabelas de contingência e gráficos de barras.
14. Calcula os p-values das hipóteses e exporta os resultados para o texto do TCC.

![Metodologia do Experimento](/artefatos/metodologia.png)

## 11.4 Plano de piloto

Será realizado um piloto antes da classificação para validar a viabilidade técnica e a clareza da taxonomia.

Escopo: Ciclo completo com apenas 500 repositórios e classificação de 30 comentários, 10 de cada domínio.
Objetivos:
* Verificar se o PyDriller consegue ler os repositórios sem erros de timeout.
* Medir o tempo médio gasto para classificar um comentário (para estimar o cronograma total).
* Verificar a taxa de Falsos Positivos.

Ajuste:
* Se a taxa de falsos positivos for maior que 30%, as keywords de busca serão refinadas.
* Se o tempo por comentário for maior que 5 minutos, o processo de verificação de contexto no GitHub precisará ser otimizado.

---------------------------------------------------

# 12. Plano de análise de dados 
## 12.1 Estratégia geral de análise
A análise combinará estatística descritiva e inferencial, organizada conforme as questões de pesquisa:

* RQ1: A variável dependente é contínua (SATD/KLOC). Como métricas de código raramente seguem distribuição normal, compararemos as medianas das densidades entre os três domínios para verificar se há diferença estatisticamente relevante.
* RQ2: As variáveis são categóricas. Utilizaremos tabelas de contingência cruzando domínio x tipo de dívida para analisar se a distribuição percentual dos 9 tipos muda conforme o domínio.
* RQ3: Será comparada a proporção de ocorrências de keywords críticas (FIXME) versus comuns (TODO) entre os grupos.
* RQ4: Será analisada a força da associação entre variáveis numéricas, como idade e tamanho da equipe, verificando se a correlação é mais forte em um domínio do que em outro.

## 12.2 Métodos estatísticos planejados

Dado que métricas de software geralmente possuem distribuições assimétrica, a preferência será por testes não-paramétricos:
* Teste de Kruskal-Wallis: Utilizado para RQ1. É a alternativa não-paramétrica à ANOVA para comparar mais de dois grupos independentes.
* Teste Qui-Quadrado de independência: Utilizado para RQ2 e RQ3. Avaliará a dependência entre as variáveis categóricas.
* Correlação de Spearman: Utilizada para RQ4. Avaliará a correlação monótica entre maturidade e dívida, pois é resistente a outliers e não exige linearidade estrita como Pearson.

## 12.3 Tratamento de dados faltantes e outliers

* Dados Faltantes: Repositórios que ficarem inacessíveis ou vazios durante a coleta serão descartados e substituídos pelo próximo da lista aleatória. Comentários sorteados que, ao serem verificados, já tiverem sido removidos do código, serão descartados e substituídos.
* Outliers: Não haverá remoção de outliers estatísticos para o cálculo da densidade, a menos que sejam identificados como artefatos gerados automaticamente (falsos positivos). O uso de testes não-paramétricos (Kruskal-Wallis e Spearman) e o reporte de medianas ao invés de médias já mitigam naturalmente a distorção causada por esses valores extremos.

## 2.4 Plano de análise para dados qualitativos

A análise qualitativa refere-se à etapa de classificação manual dos comentários. 

Técnica: Análise de conteúdo dedutiva. As categorias não emergirão dos dados, mas sim da aplicação de uma teoria pré-existente (a taxonomia de 9 tipos de OBrien et al.).

Procedimento de codificação:
* Leitura do comentário e do contexto, as linhas adjacentes.
* Tentativa de mapeamento para uma das 9 categorias.
* Caso o comentário seja ambíguo e se encaixe em duas categorias, será aplicada a categorização a partir da causa raiz da dívida. Se a ambiguidade persistir, será descartado.

Confiabilidade: Cálculo do coeficiente Kappa de Cohen em uma subamostra de 10% dos dados, reavaliada por um segundo juiz (orientador) ou pelo próprio pesquisador após um intervalo de tempo, para garantir consistência na aplicação das categorias.

--------------------------------------------------------------------------
# 13. Avaliação de validade (ameaças e mitigação)
## 13.1 Validade de conclusão

Refere-se à capacidade de tirar conclusões estatísticas corretas sobre as relações entre as variáveis.

* Risco de não detectar uma diferença entre os domínios mesmo que ela exista, devido a uma amostra pequena.
Mitigação: O planejamento de classificar 600 instâncias é calculado para detectar tamanhos de efeito médios com poder > 0.80.

* O uso de testes paramétricos em dados que não seguem distribuição normal invalidaria os resultados.
Mitigação: Uso exclusivo de testes não-paramétricos robustos como Kruskal-Wallis e Spearman que não assumem normalidade dos dados.

* A classificação manual dos tipos de dívida é subjetiva. Se o classificador mudar de critério no meio do processo, os dados tornam-se ruidosos.
Mitigação: Cálculo do Kappa de Cohen em uma subamostra e revalidação cruzada com o orientador.

## 13.2 Validade interna

Refere-se à certeza de que o fator experimental (domínio) é a causa real das diferenças observadas, e não outros fatores ocultos.

* Pode acontecer viés de seleção, por exemplo, se selecionarmos apenas as bibliotecas mais populares para NLP e bibliotecas menores para Tabular, a diferença na dívida pode ser causada pela maturidade e não pelo domínio.
Mitigação: Amostragem estratificada aleatória baseada no mesmo critério de corte, mais que 50 estrelas, para todos os grupos.

* Variáveis de confusão, por exemplo, o tamanho da equipe ou a idade do projeto podem influenciar a dívida.
Mitigação: Inclusão da RQ4 especificamente para medir e controlar estatisticamente o impacto dessas variáveis sobre os resultados.

* Problemas na instrumentação, por exemplo, o script de mineração pode falhar em capturar certos arquivos ou interpretar incorretamente comentários multilinha.
Mitigação: Validação manual de uma amostra aleatória de extrações brutas antes da classificação final.

## 13.3 Validade de constructo

Refere-se à adequação das medidas operacionais para representar os conceitos teóricos.

* Assumir que as keywords selecionadas representam toda a dívida técnica do projeto. Dívidas não documentadas não serão capturadas.
Mitigação: Deixar explícito no texto que o estudo mede Dívida Técnica Auto Admitida (SATD) e não a dívida técnica total. SATD é um proxy validado na literatura, mas não é o todo.

* As categorias usadas para classificar as SADTs podem ter fronteiras tênues, levando a classificações equivocadas.
Mitigação: Adoção estrita da taxonomia de OBrien et al., utilizando suas definições formais e exemplos canônicos como guia de referência durante a classificação.

* As keywords selecionadas podem não cobrir todas as formas de admissão de dívida.
Mitigação: Aceitar essa limitação como padrão em estudos de MSR, citando trabalhos anteriores (Maldonado) que indicam que essas keywords cobrem a grande maioria dos casos intencionais.

## 13.4 Validade externa

Refere-se à generalização dos resultados para outros contextos.

* Os resultados vêm de projetos Open Source, que possuem dinâmicas de pressão e qualidade diferentes de software proprietário/comercial, portando não representam a indústria.
Mitigação: Limitar as conclusões ao contexto de ecossistema Open Source de Machine Learning, sem alegar que se aplicam a empresas fechadas.

* O estudo foca apenas em Python. Os resultados podem não se aplicar a ML feito em C++, R ou Julia.
Mitigação: Explicitar a restrição no título e no escopo.

Efeito Temporal: A análise é um snapshot. A dívida técnica é dinâmica e pode ter sido resolvida na semana seguinte à coleta.
Mitigação: O estudo caracteriza o perfil acumulado até o momento, não a taxa de resolução.

## 13.5 Resumo das principais ameaças e estratégias de mitigação

| Tipo de Validade | Ameaça Principal | Estratégia de Mitigação Planejada |
|---|---|---|
| Conclusão | Subjetividade na classificação manual (ruído nos dados). | Validação cruzada de 10% da amostra e cálculo do Kappa de Cohen. |
| Conclusão | Violação de normalidade nos dados. | Uso de testes não-paramétricos (Kruskal-Wallis, Spearman). |
| Interna | Viés de seleção (projetos incomparáveis). | Amostragem aleatória estratificada com critérios de inclusão rígidos e iguais. |
| Constructo | SATD não representa toda a Dívida Técnica. | Delimitação clara do escopo teórico para dívida técnica auto admitida apenas. |
| Externa | Foco exclusivo em Python/Open Source. | Definição explícita das fronteiras de generalização nas conclusões. |

---------------------------------------------------
# 14. Ética, privacidade e conformidade
## 14.1 Questões éticas
Por se tratar de uma pesquisa baseada em dados secundários e públicos, não há interação direta com os desenvolvedores, eliminando riscos de coerção, estresse psicológico ou danos físicos.
No entanto, os exemplos de códigos "ruins" ou com dívida técnica citados no trabalho final não serão utilizados para ridicularizar ou expor negativamente desenvolvedores específicos ou empresas, focando estritamente na análise técnica do artefato.

## 14.2 Consentimento informado
Devido à natureza da coleta de dados em repositórios públicos (GitHub), a obtenção de consentimento informado individual é inviável e, conforme práticas padrão da comunidade de Engenharia de Software Experimental, considerada dispensável.
Assume-se que, ao publicar código sob licenças abertas em uma plataforma pública, os desenvolvedores consentem com a leitura e análise de seu código. O estudo respeitará os termos das licenças de software, utilizando os dados apenas para fins de pesquisa acadêmica não-comercial.

## 14.3 Privacidade e proteção de dados
Embora os dados sejam públicos, os metadados dos commits contêm informações pessoais, como nomes e e-mails dos autores. Para conformidade com princípios de proteção de dados e boas práticas de pesquisa:

* O script coletará o nome/autor apenas para fins de controle de qualidade (evitar contar o mesmo autor muitas vezes se necessário), mas não para perfilamento.
* Nos datasets finais (CSVs) que serão tornados públicos ou anexados ao TCC, as colunas de Author Name e Email serão removidas ou substituídas por IDs hash.
* Nenhuma lista de contatos ou e-mails de desenvolvedores será publicada no corpo do trabalho.

--------------------------------------
# 15 Recursos, infraestrutura e orçamento

## 15.1 Recursos humanos e papéis
A equipe é composta pelos papéis acadêmicos padrão:
Pesquisador (aluno): Responsável pela implementação dos scripts de mineração, execução da coleta de dados, classificação manual das 600 instâncias de SATD, análise estatística e escrita do relatório.
Orientador: Responsável pela validação do desenho experimental, revisão do protocolo de classificação, validação cruzada de uma amostra dos dados e revisão final do texto.

## 15.2 Infraestrutura técnica necessária
Para a execução da mineração e análise, será utilizado o seguinte ambiente:

* Hardware: Computador pessoal com processador multi-core, mínimo de 8GB de RAM e 50GB de armazenamento livre. 
* Linguagem: Python 3.9+.
* Bibliotecas: PyDriller (Mineração), PyGithub (Seleção), Pandas/Scipy (Análise).
* Credenciais: Personal Access Token do GitHub configurado para aumentar os limites de requisição da API durante a fase de seleção.
  
## 15.3 Materiais e insumos

* Digitais: Planilha mestre de classificação e o "Guia de Referência da Taxonomia" elaborado na fase de preparação para consulta durante a classificação manual.
* Backup: Repositório privado para versionamento dos scripts e conta em nuvem para backup diário dos datasets gerados, mitigando risco de perda de dados.

--------------------------------------------

# 16 Cronograma, marcos e riscos operacionais
## 16.1 Macrocronograma

| Mês / Semana | Fase | Atividade Principal | Entregável  |
|---|---|---|---|
| Mês 1 | Preparação | Desenvolvimento e teste dos scripts, leitura aprofundada da taxonomia. | Scripts funcionais e lista de repositórios selecionados.  |
| Mês 1 | Piloto | Execução do estudo piloto e alinhamento com orientador. | Validação do protocolo de classificação.  |
| Mês 2 | Coleta | Mineração massiva e amostragem aleatória dos dados brutos. | Dataset bruto com candidatos a SATD gerado.  |
| Mês 2 e 3 | Classificação | Classificação manual dos 600 comentários. | Dataset classificado e validado.  |
| Mês 4 | Análise | Execução dos testes estatísticos e geração de gráficos. | Resultados preliminares e tabelas geradas.  |
| Mês 5 | Escrita | Redação dos capítulos de resultados, discussão e conclusão. | Versão final do texto para a banca. |

## 16.2 Dependências entre atividades
A execução segue um fluxo linear estrito, na qual o atraso em uma etapa bloqueia a seguinte:

* Seleção -> Mineração: A lista de repositórios deve estar finalizada e validada antes de iniciar o script de mineração.
* Mineração -> Piloto: É necessário ter dados reais extraídos para realizar o piloto de classificação.
* Piloto -> Classificação: A classificação dos 600 itens não deve iniciar antes que o orientador valide o resultado do piloto. Se houver erro de interpretação da taxonomia, classificar tudo antes de validar geraria retrabalho total.
* Classificação -> Análise Estatística: Os testes de hipótese só podem ser rodados após a conclusão e limpeza da planilha de classificação.

## 16.3 Riscos operacionais e plano de contingência

| Risco Identificado | Probabilidade | Impacto | Plano de Contingência  |
|---|---|---|---|
| Bloqueio da API do GitHub | Média | Médio | Usar múltiplos Access Tokens ou inserir delays no script de mineração, aceitando que a coleta demorará mais dias.  |
| Baixa qualidade dos comentários (muitos falsos positivos) | Média | Alto | Se as keywords trouxerem muitos falsos positivos, o tamanho da amostra válida cairá. Contingência: Aumentar o pool de extração inicial em 50% para garantir que sobrem 200 itens válidos após filtragem.  |
| Resultados inconclusivos (p-value > 0.05) | Média | Baixo | Risco científico, não operacional. Contingência: Focar a discussão na análise qualitativa dos exemplos e na refutação das hipóteses, o que também é uma contribuição científica válida. |

-------------------------------------------------

# 17. Governança do experimento
## 17.1 Papéis e responsabilidades formais
A estrutura de decisão segue a hierarquia acadêmica do projeto:
* Pesquisador: Responsável por executar todas as etapas operacionai, documentar os resultados e propor ajustes metodológicos e toma ecisões operacionais de baixo nível, como refatoração do código de mineração.
* Orientador: Responsável pelo protocolo experimental, validar a amostragem e a aplicação da taxonomia, além de aprovar a versão final do texto. Toma decisões estratégicas de alto nível, como corte de escopo.

## 17.2 Ritos de acompanhamento pré-execução
Para garantir o alinhamento antes do início da fase intensiva de coleta, estabelecem-se os seguintes pontos de controle:

### 17.2.1 Reunião de Aprovação do Plano (Kick-off):
* Objetivo: Validar este documento de planejamento e as hipóteses propostas.
* Participantes: Aluno e Orientador.
  
### 17.2.2 Revisão do Piloto:
* Objetivo: Analisar os primeiros 30 comentários classificados no estudo piloto. Verificar se o entendimento da taxonomia está alinhado e se a taxa de falsos positivos é aceitável.
* Decisão: Go / No-Go para a classificação massiva dos 600 itens restantes.
* Participantes: Aluno e Orientador.

### 17.2.3 Sincronização Semanal:
* Objetivo: Reportar progresso da coleta e discutir dúvidas pontuais sobre casos de borda na classificação.
* Participantes: Aluno e Orientador.
  
## 17.3 Processo de controle de mudanças no plano
Dado que a pesquisa empírica pode revelar imprevistos nos dados, as mudanças serão geridas da seguinte forma:

* Mudanças operacionais: Ajustes em scripts ou otimização de performance que não alteram a metodologia são decididos pelo pesquisador e registrados no histórico de commits do repositório.
* Mudanças de escopo/metodologia: Alterações que impactam a validade científica devem ser formalizadas por e-mail ou ata de reunião pelo aluno e aprovadas explicitamente pelo orientador.


# 21. Referências 

* OBRIEN, D. et al. "23 Shades of Self-Admitted Technical Debt: An Empirical Study on Machine Learning Software". In: Proceedings of the 30th ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering (ESEC/FSE '22). Singapore: ACM, 2022. pp. 734–746. DOI: https://doi.org/10.1145/3540250.3549088.

* SCULLEY, D. et al. "Hidden Technical Debt in Machine Learning Systems". In: Proceedings of the 28th International Conference on Neural Information Processing Systems (NIPS). 2015.

* MALDONADO, E.; SHIHAB, E. "Detecting and quantifying different types of self-admitted technical debt". In: IEEE 7th International Workshop on Managing Technical Debt (MTD). 2015.

* PEPE, F. et al. "A Taxonomy of Self-Admitted Technical Debt in Deep Learning Systems". In: IEEE International Conference on Software Maintenance and Evolution (ICSME). 2024.
