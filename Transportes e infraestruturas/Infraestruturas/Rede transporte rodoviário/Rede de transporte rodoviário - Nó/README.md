# Descrição

O modelo de dados para representar **Rede de Transportes Rodoviários** é o `RoadTransportNode` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), baseado nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `RoadTransportNode`|
| accidents | Number | Número de acidentes registados no nó | Número de acidentes num período específico (observationPeriod). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| address | Object | Morada associada ao nó | Inclui país, região, distrito. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para o nó rodoviário | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| capacityVehiclesPerHour | Number | Capacidade de veículos por hora | Normalmente expresso em veículos por hora (C62). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| connects | Array | Segmentos rodoviários que se encontram neste nó | Referências URN a entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dailyTrafficVolume | Number | Volume de tráfego diário | Normalmente expresso em veículos por dia (C62). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do nó rodoviário | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| formType | String | Tipo de forma do nó | Enumerado: <br>- roundabout, <br>- intersection, <br>- T-junction, <br>- fork, <br>- merge. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| infrastructureElements | Array | Elementos de infraestrutura no nó | Semáforos, passagens de peões, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastMaintenance | DateTime | Data da última operação de manutenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| location | GeoJSON | Referência Geojson para o nó rodoviário |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| name | String | Nome do nó rodoviário | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nationalId | String | Identificador nacional único | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nextMaintenance | DateTime | Data prevista para a próxima operação de manutenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| nodeType | String | Tipo de nó | Enumerado: <br>- junction, <br>- terminal,<br>- bridge node,<br>- tunnel node,<br>- border node. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| peakHourCongestion | String | Nível de congestionamento na hora de ponta | Enumerado: <br>- low, <br>- moderate, <br>- high, <br>- very high. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pedestrianFacilities | Object | Facilidades para peões | Inclui passagens, acessibilidade, etc. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| signalTiming | Object | Informação sobre temporização de semáforos | Inclui tempo de ciclo, fases, controlo adaptativo. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| trafficLightControlled | Boolean | Especifica se o nó é controlado por semáforos | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| trafficManagement | Object | Sistemas de gestão de tráfego | Inclui monitorização por câmara, controlo adaptativo. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `name`
- `type`
- `location`
- `nodeType`
- `formType`
- `connects`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.