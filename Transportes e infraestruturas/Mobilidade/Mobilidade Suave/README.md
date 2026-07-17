# Descrição

O modelo de dados para representar **Mobilidade suave** é feito com o recurso aos modelos [VehicleModel](https://github.com/smart-data-models/dataModel.Transportation/blob/master/VehicleModel/doc/spec.md), [Vehicle](https://github.com/smart-data-models/dataModel.Transportation/blob/master/Vehicle/doc/spec.md), `DockingStation` (compatível com [BikeHireDockingStation](https://github.com/smart-data-models/dataModel.Transportation/blob/master/BikeHireDockingStation/doc/spec.md)), e `VehicleTrip` alinhados com o [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar exemplos de utilização deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://territoriosinteligentes.gov.pt).

## Propriedades

Para informações sobre `VehicleModel` e `Vehicle`, consultar  o [Catálogo Nacional de Modelos de Dados para os Territórios Inteligentes (CNMD)](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/), na zona dos modelos comuns.

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

Para o `DockingStation`:

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `DockingStation`|
| address                  | Object          | Morada associada ao ponto de interesse | Inclui país, cidade, freguesia e código postal. Modelo: [https://schema.org/address](https://schema.org/address)  |
| agency_fare_url   | string | URL de uma página web que contém os detalhes das tarifas | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| agency_name       | string | Nome completo da agência de transporte | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| agency_url        | uri    | URL da agência de transporte       | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| alternateName     | String    | Nome alternativo    | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed    | String    | A área geográfica onde se aplica este modelo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| availableVehicleNumber     | number      | Número de veiculos de mobilidade suave disponíveis na estação | Modelo: [https://schema.org/Number](https://schema.org/Number)               |
| contactPoint            | object      | Detalhes de contacto associados ao item | Modelo: <https://schema.org/ContactPoint>         |
| contactPoint.areaServed              | string      | Área geográfica onde é fornecido o serviço. Substitui *serviceArea*     | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint.availabilityRestriction | string           | Informação de indisponibilidade do contacto  | Modelo: [http://schema.org/hoursAvailable](http://schema.org/hoursAvailable)        |
| contactPoint.availableLanguage       | Array           | Língua(s) que podem ser usadas com ou no item/serviço/local |Deve ser usado um código IETF BCP 47.  Modelo: [http://schema.org/availableLanguage](http://schema.org/availableLanguage)     |
| contactPoint.contactOption           | string           | Opção disponível neste ponto de contacto (ex.: número gratuito ou apoio a utilizadores com deficiência auditiva)  | Modelo: [http://schema.org/contactOption](http://schema.org/contactOption)         |
| contactPoint.contactType             | string      | Tipo de contacto  | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.email                   | string   | Endereço de correio eletrónico do contacto  | Modelo: [https://schema.org/email](https://schema.org/email)|
| contactPoint.faxNumber               | string      | Número de fax | Modelo: [http://schema.org/Text](http://schema.org/Text)     |
| contactPoint.name                    | string      | Nome do item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint.productSupported        | string      | Produto ou serviço ao qual este ponto de contacto de suporte está associado | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint.telephone               | string      | Número de telefone   | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Data da moodificação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da estação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| freeSlotNumber          | number     | Número de docas disponíveis na estação para devolver e estacionar bicicletas/trotinetes | Deve ser menor ou igual a *totalSlotNumber-outOfServiceSlotNumber* . Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| location | GeoJSON | Referência Geojson ao item | Valores possíveis: 'Point' ou 'LineString' se for uma estação física, 'Polygon' se for uma estação virtual, com zona espefícia de entrega (*geofencing*). |
| mediaURL                | URL        | URL que disponibiliza informação adicional, imagens ou outros meios relacionados com o local    | Modelo: [https://schema.org/Text](https://schema.org/Text)              |
| name                    | string     | Nome deste item  | Modelo: [https://schema.org/Text](https://schema.org/Text)              |
| observationDate| DateTime | Data e hora reportadas da última observação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| openingHours            | string     | Horário de funcionamento da estação | Modelo: [http://schema.org/openingHours](http://schema.org/openingHours)       |
| outOfServiceSlotNumber  | number     | Número de lugares indisponíveis (avariados) que não podem ser usados para tirar ou estacionar bicicletas/trotinetes| Deve ser menor ou igual a *totalSlotNumber*. Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| owner   | Array    | Lista dos IDs do(s) proprietário(s) | A existir a propriedade, tem de ter pelo menos um valor. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| provider                | string     | Fornecedor do serviço  | Modelo: [https://schema.org/provider](https://schema.org/provider)          |
| seeAlso | Array | Descrições adicionais | Lista de URLs para recursos externos. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | A origem dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| stationCode             | string     | Número ou código da estação de aluguer de bicicletas correspondente à observação   | Modelo: [https://schema.org/Text](https://schema.org/Text)              |
| stationName             | string     | Nome da estação  | Modelo: [https://schema.org/Text](https://schema.org/Text)              |
| status                  | string     | Estado da estação de bicicletas   | Enumerado: <br> - working, <br> -  outOfService, <br> -  withIncidence, <br> -  full, <br> -  almostFull, <br> -  empty, <br> -  almostEmpty, <br> - other. Modelo: [https://schema.org/Text](https://schema.org/Text)           |
| totalSlotNumber         | number     | Número total de lugares oferecidos pela estação | Modelo: [https://schema.org/Number](https://schema.org/Number)            |

Para o `VehicleTrip`:

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `VehicleTrip`|
| arrivalTime | DateTime | Data do fim da viagem | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Data da modificação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da viagem de um utilizador | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| destination      | URI         | Referência para a `DockingStation`  de destino   | Modelo: [https://schema.org/URL](https://schema.org/URL)      |
| departureTime | DateTime | Data do início da viagem | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| distance          | number     | A distância percorrida | Deve ser igual ou sperior a zero. Normalmente expressa em metros. Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| duration          | number     | A duração da viagem | Deve ser igual ou sperior a zero. Normamalmente expressa em segundos. Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| name                    | string     | Nome deste item  | Modelo: [https://schema.org/Text](https://schema.org/Text)              |
| origin      | URI         | Referência para a `DockingStation`  de origem   | Modelo: [https://schema.org/URL](https://schema.org/URL)      |
| status                    | string     | O estado do item  | Enumerado: <br> - planned, <br> - ongoing, <br> - completed, <br> - cancelled, <br> - aborted, <br> - disrupted, <br> - unknown.  Modelo: [https://schema.org/Text](https://schema.org/Text)              |
| refVehicle     | URI         | Referência para um `Vehicle`                                 | Modelo: [https://schema.org/URL](https://schema.org/URL)      |

## Propriedades obrigatórias

Os atributos obrigatórios para o `DockingStation` são:

- `id`
- `type`
- `agencyName`
- `availableVehicleNumber`
- `dockingStationType`
- `location`
- `observationDate`
- `stationName`
- `stationCode`
- `status`

Os atributos obrigatórios para o `VehicleTrip` são:

- `id`
- `type`
- `arrivalTime`
- `departureTime`
- `destination`
- `origin`
- `refVehicle`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
