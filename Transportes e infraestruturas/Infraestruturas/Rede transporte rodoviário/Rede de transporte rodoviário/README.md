# Descrição

O modelo de dados para representar **Rede de Transporte Rodoviário** é o `RoadTransportNetwork` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), baseado nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade |  Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `RoadTransportNetwork`|
| accessibility | Number | Índice de acessibilidade da rede | Valor entre 0 e 1. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| address | Object | Morada associada à rede | Inclui país, região. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para a rede rodoviária | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| beginLifespanVersion | DateTime | Data a partir da qual esta versão de rede é válida | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| boundingBox | GeoJSON | Área geográfica abrangida pela rede | Valores possíveis: 'Polygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| concessionary | Array | Concessionários da rede rodoviária | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| connectivity | Number | Índice de conectividade da rede | Valor entre 0 e 1. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| connectedNetworks | Array | Redes rodoviárias adjacentes ou ligadas | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| crossBorderPoints | Object | Pontos de ligação a outras regiões administrativas | Inclui localização, tipo de ligação, volume de tráfego. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da rede rodoviária | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| emergencyRoutes | Array | Itinerários definidos para evacuação de emergência | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endLifespanVersion | DateTime | Data até à qual esta versão de rede é válida | A omitir se o valor for nulo. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| hasParts | Array | Segmentos e nós que compõem esta rede | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastFullInspection | DateTime | Data da última inspeção completa da rede | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| maintenanceAuthority | Object | Organização responsável pela manutenção da rede | Inclui nome, contacto, website. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| name | String | Nome da rede rodoviária | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nationalId | String | Identificador nacional único | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| networkClassification | String | Classificação da rede | Enumerado: <br>- national, <br>- regional, <br>- metropolitan, <br>- local. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| networkStatus | Object | Estado geral atual da rede | Inclui condição geral, pontos críticos, nível de congestionamento. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| networkType | String | Tipo de rede | Conforme [OpenStreetMap highway classification](https://wiki.openstreetmap.org/wiki/Key:highway). Enumerado: <br>- motorway,<br>-  trunk,<br>- primary,<br>- tertiary,<br>- unclassified,<br>- residential,<br>- service,<br>- track,<br>- path,<br>- road. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadClass | Object | Repartição dos tipos de estrada na rede | Inclui quilometragem por tipo (highway, national, regional, local). Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| totalLength | Number | Comprimento total da rede | Normalmente expresso em quilómetros (KMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalNodes | Number | Número total de nós na rede | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalSegments | Number | Número total de segmentos na rede | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| trafficStatistics | Object | Informações de tráfego agregadas | Inclui volume médio diário, volume hora de ponta, horas de congestionamento. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| version | String | Versão do modelo de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `name`
- `type`
- `boundingBox`
- `networkType`
- `networkClassification`
- `totalLength`
- `totalNodes`
- `totalSegments`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `boundingBox` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
