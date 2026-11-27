# Catálogo Nacional de Modelos de Dados para os Territórios Inteligentes

<p align="center">
  <img src="Logo_ARTE.png" alt="ARTE" width="180">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-em%20evolu%C3%A7%C3%A3o-blue" alt="Estado: em evolução">
  <img src="https://img.shields.io/badge/formato-Markdown-000000?logo=markdown" alt="Formato: Markdown">
  <img src="https://img.shields.io/badge/idioma-PT--PT-green" alt="Idioma: PT-PT">
</p>

O **Catálogo Nacional de Modelos de Dados (CNMD) para os [Territórios Inteligentes](https://territoriosinteligentes.gov.pt)** é um instrumentos fundamental para promover a interoperabilidade, harmonização e qualidade dos dados disponibilizados pelas entidades públicas. Organiza e documenta modelos de dados normalizados, garantindo uma referência comum para a publicação, partilha e reutilização de informação a nível nacional.

Este catálogo foi desenvolvido para apoiar as entidades na **adoção de práticas consistentes**, assegurando que os dados publicados seguem padrões uniformes, tanto ao nível estrutural como semântico. Ao fazê-lo, contribui para a melhoria dos serviços digitais, para a eficiência operacional e para uma maior transparência na disponibilização de informação.

## Organização

O CNMD está organizado por áreas temáticas e, para cada tema existe:

- um ficheiro `README.md`, que descreve o modelos (ou modelos) usado na área temática;
- uma directoria `exemplos` que contém um ou mais exemplos de uso do(s) modelo(s);
- uma directoria `schema` que contém os JSON Schemas que permitem validar o(s) modelo(s);
- um ficheiro [Granularidades e frequência de entrega CNMD](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/blob/main/Granularidades%20e%20frequ%C3%AAncia%20de%20entrega%20CNMD.xlsx) com a granularidade espacial, temporal e frequência de atualização dos dados a partilhar com a ARTE.
- um ficheiro com o [Código da Divisão Administrativa/Revisão 2025 do INE](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/blob/main/C%C3%B3digo%20da%20Divis%C3%A3o%20Administrativa_Revis%C3%A3o_2025_v%2009-07-2025_Final_SMI_Outubro_2.xlsx) que contém a designação oficial dos municípios. Estas designações deverão ser utilizadas nos enumerados da propriedade address.addressLocality.
- Está disponível um validador de schemas [Validador de schemas do CNMD](https://github.com/amagovpt/VALIDADOR_MODELOS_DADOS_CNMD/tree/66b03173fa5b1aab0de21c3477b9dcf8574db1e0) que deve ser utilizado para fazer uma validação prévia dos schemas do CNMD antes do envio dos conjuntos de dados para a ARTE.

## FAQs

A área de **[FAQ](FAQ.md)** do Catálogo Nacional de Modelos de Dados para os Territórios Inteligentes foi criada para apoiar as entidades e utilizadores na correta adequação dos dados que pretendem disponibilizar aos modelos publicados neste catálogo. Aqui encontrará esclarecimentos práticos sobre conceitos, regras e procedimentos que garantem uma aplicação consistente, interoperável e alinhada com as orientações definidas.

O Catálogo Nacional de Modelos de Dados é um instrumento em **evolução contínua**, em permanente melhoria e expansão. Por esse motivo, também as perguntas frequentes são atualizadas de forma dinâmica, acompanhando a maturidade do catálogo, as necessidades das entidades e os desafios que surgem na adoção dos modelos.
