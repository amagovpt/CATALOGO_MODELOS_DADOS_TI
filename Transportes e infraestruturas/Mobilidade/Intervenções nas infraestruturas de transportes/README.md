# Descrição

O modelo de dados a seguir representa as **Intervenções em Infraestrutura de Transporte** é o `TransportInfrastructure`,  inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

O modelo inclui estradas, caminhos-de-ferro, vias navegáveis, portos ou aeroportos. Foi concebido para fornecer informação normalizada sobre manutenção, reparação, construção ou outros trabalhos que possam afetar as redes de transportes e os seus utilizadores.


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `TransportInfrastructure`|
| address | Object | Morada associada à intervenção | Inclui país, região, endereço da infraestrutura. Modelo: [https://schema.org/address](https://schema.org/address) |
| affectedTransportNetworks | Array | Redes de transportes afetadas por esta intervenção | Lista de URNs das redes de transporte impactadas. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para esta intervenção | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternativeRoutes | Array | Percursos alternativos disponíveis durante a intervenção | Inclui nome, descrição e coordenadas de rotas alternativas. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| associatedDocuments | Array | Documentos oficiais relacionados com a intervenção | Inclui id, nome e URL de documentos como licenças e autorizações. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| completionPercentage | Number | Percentagem de trabalhos concluídos | Valor entre 0 e 100 (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| contactPoint | Object | Informações de contacto para a intervenção | Inclui nome, telefone e email de contacto. Modelo: [https://schema.org/ContactPoint](https://schema.org/ContactPoint) |
| contractor | String | Empresa responsável pela execução da intervenção | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateFinished | DateTime | Data prevista para a conclusão da intervenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObserved | DateTime | Data em que a intervenção foi registada | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateStarted | DateTime | Data de início da intervenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da intervenção | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| estimatedDuration | Number | Duração total estimada da intervenção | Normalmente expressa em dias (DAY). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| impactLevel | String | Nível de impacto no fluxo normal de tráfego | De acordo com o [DATEEX II](https://docs.datex2.eu/v3.2/downloads/modelv30.html). Enumerado: <br>- noImpact,<br>- lowImpact,<br>- mediumImpact,<br>- highImpact,<br>- veryHighImpact. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| infrastructureType | String | Tipo de infraestrutura de transportes afetada | Inspirado no [INSPIRE](https://knowledge-base.inspire.ec.europa.eu/transport-networks_en). Enumerado:<br>- Road,<br>-  Railway,<br>-  Waterway,<br>- Maritime Port,<br>-  Air Transport. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| interventionCategory | String | Categorização da intervenção | Enumerado:<br>- emergence,<br>- planned,<br>- preventive. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| interventionType | String | Tipo de intervenção | Enumerado: <br>- maintenance,<br>- construction,<br>- repair,<br>- upgrade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome da intervenção | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nextUpdate | DateTime | Próxima atualização programada das informações sobre a intervenção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| notificationChannels | Array | Canais utilizados para informar os utilizadores sobre a intervenção | Lista de canais como 'website', 'trafficSigns', 'radio', 'mobile'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| relatedIntervention | URI | Referência a intervenções conexas | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| responsibleAuthority | String | Autoridade responsável pela intervenção | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| speedLimit | Number | Limite de velocidade temporário aplicado durante a intervenção | Normalmente expressa em quilómetros por hora (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| status | String | Situação atual da intervenção | Inspirado no [INSPIRE](https://inspire.ec.europa.eu/codelist/ConditionOfFacilityValue). Enumerado: <br>- planned,<br>- underConstruction,<br>- inUse,<br>- decommissioned. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| trafficRestrictions | Array | Lista das restrições de tráfego aplicadas durante a intervenção | Valores possíveis: 'roadClosed', 'laneClosure', 'diversionInOperation', 'speedLimit'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| workingDays | Array | Dias em que o trabalho está a ser realizado | Lista de dias da semana. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| workingHours | String | Horas em que o trabalho está a ser executado | Formato HH:MM-HH:MM. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `interventionType`
- `infrastructureType`
- `status`
- `dateStarted`
- `location`

## Notas

A representação a usar é NGSI-LD.
Os campos do tipo `DateTime` usam o standard ISO 8601.
Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos.  Neste modelo temos para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este como valor um código [EPSG](https://epsg.org/crs_4326/WGS-84.html), por exemplo `"coordinateSystem": "EPSG:4326"`. Para as medições, incluir `unitCode` utilizando [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes). Para a propriedade `interventionType` os valores possíveis são manutenção, construção, reparação, etc. A propriedade `interventionCategory` pode incluir valores como planeada, emergência e preventiva. A propriedade `status` representa o estado da intervenção, onde os valores a incluir deverão ser programado, em curso, concluído, atrasado, cancelado. A propriedade `notificationChannels` representa os canais utilizados para informar a intervenção e os valores posssíveis poderão ser website, aplicação móvel, SMS e sinais de tráfego.