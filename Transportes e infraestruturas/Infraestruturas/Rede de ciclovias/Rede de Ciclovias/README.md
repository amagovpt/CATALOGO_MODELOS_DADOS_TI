# Descrição

Os modelos de dados para representar **Rede de Ciclovias** é o `CycleNetwork` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/), é baseado nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `CycleNetwork`|
| address | Object | Endereço da localização da rede | Estrutura de endereço com país, região. Modelo: [https://schema.org/address](https://schema.org/address) |
| areaServed | String | Indicação da área servida pela rede | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| beginLifespanVersion | DateTime | Data do início da versão no mundo real | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| boundingBox | GeoJSON | Localização geoespacial da rede de ciclovia | Normalmente é usado o tipo geométrico `Polygon`. Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| connectedNetworks | Array | Outras redes de pistas cicláveis com as quais faz fronteira | Lista de identificadores das redes ligadas diretamente. Se não existirem, deve omitir-se a propriedade. Referência URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| createdAt | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| datasetResponsibleParty | URI | Responsável pela curadoria do conjunto de dados | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da rede | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endLifespanVersion | DateTime | Fim da versão no mundo real | A omitir se o valor for nulo. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| hasParts | Array | Elementos que constituem a rede | Lista de identificadores dos elementos que constituem a rede. Normalmente para entidades do tipo `CycleLane`, podendo ser outros que façam sentido, ex. Pontos de Interesse. Referência URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastFullInspection | DateTime | Data da última inspeção completa | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| license | URI | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL) |
| maintenanceAuthority | Object | Responsável pela manutenção | Estrutura com name, contactPoint e website. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| modifiedAt | DateTime | Data da modificação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| name | String | Nome da rede | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nationalId | String | Identificador compatível com INSPIRE | Deve servir para identificar o recurso, seguindo as normas indicadas pelo INSPIRE. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| networkStatus | Object | Estado de conservação da rede | Estrutura com os campos `overallCondition` (excellent, good, fair, poor, critical) e `criticalPoints` (número de pontos críticos pendentes). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| networkType | String | Tipo de rede | Deve servir para relacionar os dados com a tipologia existente no INSPIRE. Deve ter o valor `road`. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | URI | Proprietário da rede | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | Array | Descrições e categorizações adicionais | Lista de URLs para recursos externos, incluindo referências INSPIRE. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| totalLength | Number | Comprimento total da rede de ciclovia | Normalmente expressa em quilómetros (KMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| updateFrequency | String | Frequência de atualização dos dados |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| version | String | Versão do modelo dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `name`
- `boundingBox`
- `beginLifespanVersion`
- `owner`
- `totalLength`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
