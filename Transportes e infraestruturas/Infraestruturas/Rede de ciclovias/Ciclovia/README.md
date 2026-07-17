# Descrição

Os modelos de dados para representar **Ciclovias** é o `CycleLane` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/), é baseado nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `CycleLane`|
| address | Object | Endereço da localização da ciclovia | Estrutura de endereço com país, região, distrito. Modelo: [https://schema.org/address](https://schema.org/address) |
| areaServed | String | Indicação das áreas servidas pela ciclovia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| averageSlope | Number | Inclinação média da pista ciclável | Normalmente expressa em percentagem (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| beginLifespanVersion | DateTime | Data do início da versão no mundo real | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| connectsTo | Array | Outras pistas cicláveis a que se liga | Lista de identificadores das pistas cicláveis ligadas diretamente. Se não existirem, deve omitir-se a propriedade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| createdAt | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da ciclovia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endLifespanVersion | DateTime | Fim da versão no mundo real | A omitir se o valor for nulo. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| image | Array | Links para imagens associadas à ciclovia | Lista de URLs. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| lastMaintenance | DateTime | Data da última manutenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| length | Number | Comprimento da pista ciclável | Normalmente expressa em quilómetros (KMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| license | URI | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL) |
| location | GeoJSON | Localização geoespacial da pista ciclável | Normalmente é usado o tipo geométrico `LineString`. Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| maintainer | URI | Responsável pela manutenção | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| maxAltitude | Number | Altura máxima atingida pela pista | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maxSlope | Number | Inclinação máxima da pista ciclável | Normalmente expressa em percentagem (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| minAltitude | Number | Altura mínima atingida pela pista | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| modifiedAt | DateTime | Data da modificação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| name | String | Nome da ciclovia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nearBy | Array | Infraestruturas e pontos de interesse relevantes para os ciclistas | Lista de identificadores de estruturas na proximidade. Por exemplo, estacionamentos ou fontanários com água potável. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nextMaintenance | DateTime | Data da próxima manutenção programada | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| owner | URI | Proprietário da ciclovia | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pavementCondition | Number | Qualidade observada no pavimento | Valor no intervalo [1..5], onde 5 é excelente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| pavementType | String | Tipo de pavimento usado na pista ciclável | Enumerado: <br>- Asphalt,<br>- Concrete,<br>- Bituminous Pavement,<br>- Precast Concrete Slabs,<br>- Compacted Gravel,<br>- Stabilised Soil,<br>- Resin-bound Gravel,<br>- Wooden Decking,<br>- Clay or Red Earth,<br>- Porous Asphalt,<br>- Rubberised,<br>- Cobbles,<br>- Other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refNetwork | URI | A rede a que a pista ciclável pertence | Se não existir, deve omitir-se a propriedade. Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | Array | Descrição e categorização adicionais | Lista de URLs para recursos externos. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| segregation | String | Tipo de separação existente | Enumerado: <br>- fullySegregated,<br>- hardPhysicalSeparation,<br>- softPhysicalSeparation,<br>- visualSeparationOnly,<br>- mixedTraffic. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status | String | Estado de conservação da pista | Enumerado: <br>- excellent,<br>- good,<br>- fair,<br>- poor,<br>- critical. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| typology | String | Tipologia da pista ciclável | Enumerado:<br>- 30+Bike,<br>- one-way,<br>- two-way,<br>- contraflow,<br>- cycleLane,<br>- sharedWithPedestrians,<br>- trail,<br>- eco-trail. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| updateFrequency | String | Frequência de atualização dos dados | Ex: mensal. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| version | String | Versão do modelo dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `name`
- `location`
- `beginLifespanVersion`
- `owner`
- `refNetwork`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.