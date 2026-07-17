# Descrição

O modelo de dados a seguir para representar **Contadores de viaturas** é o [TrafficFlowObserved](https://github.com/smart-data-models/dataModel.Transportation/blob/master/TrafficFlowObserved/README.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `TrafficFlowObserved`|
| address | Object | Morada associada à observação de tráfego | Inclui país, localidade, rua. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| averageGapDistance | Number | Distância média entre veículos consecutivos | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageHeadwayTime | Number | Tempo médio de intervalo entre veículos | Tempo decorrido entre dois veículos consecutivos. Normalmente expressa em segundos (SEC). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageVehicleLength | Number | Comprimento médio dos veículos em trânsito durante o período de observação | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageVehicleSpeed | Number | Velocidade média dos veículos em trânsito durante o período de observação | Normalmente expressa em quilómetros por hora (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| congested | Boolean | Indica se houve congestionamento de tráfego durante o período de observação na faixa referida | A ausência deste atributo significa que não houve congestionamento de tráfego. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObserved | String | Data e hora desta observação em formato ISO8601 UTC | Pode ser representado por um instante de tempo específico ou por um intervalo ISO8601. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObservedFrom | DateTime | Data e hora de início do período de observação | Ver dateObserved. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObservedTo | DateTime | Data e hora de fim do período de observação | Ver dateObserved. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| intensity | Number | Número total de veículos detetados durante este período de observação | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| laneDirection | String | Direção usual de viagem na faixa referida por esta observação | Enumerado: <br>- forward,<br>- backward. Ver RoadSegment para descrição da semântica destes valores. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| laneId | Number | Identificador da faixa | A identificação da faixa é feita usando as convenções definidas pela entidade RoadSegment baseadas no [OpenStreetMap](http://wiki.openstreetmap.org/wiki/Forward_%26_backward,_left_%26_right). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancy | Number | Fração do tempo de observação onde um veículo ocupou a faixa observada | Valor entre 0 e 1. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refRoadSegment | URI | Segmento de estrada em questão sobre o qual a observação foi feita | Referência a uma entidade do tipo RoadSegment. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| reversedLane | Boolean | Indica se o tráfego na faixa foi invertido durante o período de observação | A ausência deste atributo significa que não houve inversão de faixa. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleSubType | String | Permite especificar um subtipo de vehicleType | Por exemplo, se vehicleType é definido como _Lorry_, vehicleSubType pode ser 'OGV1' ou 'OGV2' para transmitir mais informações sobre o tipo exato de veículo. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleType | String | Tipo de veículo do ponto de vista das suas características estruturais | Enumerado: <br>- agriculturalVehicle,<br>- bicycle,<br>- bus,<br>- minibus,<br>- car,<br>- caravan,<br>- tram,<br>- tanker,<br>- carWithCaravan,<br>- carWithTrailer,<br>- lorry,<br>- moped,<br>- motorcycle,<br>- motorcycleWithSideCar,<br>- motorscooter,<br>- trailer,<br>- van,<br>- constructionOrMaintenanceVehicle,<br>- trolley,<br>- binTrolley,<br>- sweepingMachine,<br>- cleaningTrolley. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `dateObserved`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.

