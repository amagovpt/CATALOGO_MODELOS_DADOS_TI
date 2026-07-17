# Descrição

O modelo de dados para representar **Rede de Transportes Rodoviários** é o `RoadTransportSegment` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/), baseado nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) conforme especificado no anexo I da Diretiva 2007/2/CE.
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade |  Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `RoadTransportSegment`|
| accidents | Number | Número de acidentes registados no segmento | Número de acidentes num período específico (observationPeriod). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| address | Object | Morada associada ao segmento | Inclui país, região, distrito. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para o segmento rodoviário | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| connects | Array | Nós rodoviários ligados por este segmento | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| crossBorderConnections | Array | Ligações a segmentos rodoviários de outras regiões | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dailyTrafficVolume | Number | Volume de tráfego diário | Normalmente expresso em veículos por dia (C62). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do segmento rodoviário | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| direction | String | Direção do tráfego no segmento | Enumerado: <br>- bidirectional, <br>- unidirectional_positive, <br>- unidirectional_negative. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endKilometer | Number | Quilómetro final do segmento | Normalmente expresso em quilómetros (KMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| heavyVehiclePercentage | Number | Percentagem de veículos pesados | Valor percentual (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| infrastructureElements | Array | Estruturas associadas ao segmento | Pontes, túneis, viadutos, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lanes | Number | Número de faixas de rodagem | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| lastMaintenance | DateTime | Data da última operação de manutenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| length | Number | Comprimento do segmento | Normalmente expresso em quilómetros (KMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Referência Geojson para o segmento rodoviário |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| name | String | Nome do segmento rodoviário | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nationalId | String | Identificador nacional único | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nextMaintenance | DateTime | Data prevista para a próxima operação de manutenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| pavementCondition | String | Estado do pavimento | Baseado no índice de Condição do Pavimento de acordo com a norma [ASTM D6433](https://store.astm.org/d6433-24.html). Enumerado: <br>- Good, <br>- Satisfactory, <br>- Fair, <br>- Poor, <br>- Very Poor, <br>- Serious, <br>- Failed. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pavementType | String | Tipo de pavimento | Enumerado: <br>- Asphalt, <br>- Beton, <br>- Calçada Portuguesa, <br>- Gravel, <br>- Other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refNetwork | URI | A rede a que o segmento pertence | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadClass | String | Classificação da estrada | Enumerado: <br>- Highway, <br>- National, <br>- Regional, <br>- Local, <br>- Forest. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadNumber | String | Número identificativo da estrada | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadType | String | Tipo de estrada | Enumerado: <br>- Lower Capacity, <br>- Large Road, <br>- Private, <br>- Intersecting. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| speedLimit | Number | Limite de velocidade | Normalmente expresso em quilómetros por hora (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| startKilometer | Number | Quilómetro inicial do segmento | Normalmente expresso em quilómetros (KMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| trafficSignals | Array | Elementos de controlo do tráfego ao longo do segmento | Semáforos, sinais, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| width | Number | Largura da faixa de rodagem | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `name`
- `type`
- `location`
- `roadClass`
- `roadNumber`
- `startKilometer`
- `endKilometer`
- `length`
- `lanes`
- `direction`
- `refNetwork`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.