# Descrição

O modelo de dados para representar **Gestão de frota** é feito com o recurso aos modelos [Vehicle](https://github.com/smart-data-models/dataModel.Transportation/blob/master/Vehicle/doc/spec.md), [VehicleModel](https://github.com/smart-data-models/dataModel.Transportation/blob/master/VehicleModel/doc/spec.md), [FleetVehicleOperation](https://github.com/smart-data-models/dataModel.Transportation/blob/master/FleetVehicleOperation/doc/spec.md) e [FleetVehicle](https://github.com/smart-data-models/dataModel.Transportation/blob/master/FleetVehicle/doc/spec.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar exemplos de utilização deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://territoriosinteligentes.gov.pt). De notar que a descrição do modelo de [Vehicle](https://github.com/smart-data-models/dataModel.Transportation/blob/master/Vehicle/doc/spec.md) está noutro domínio, dentro do [CNMD](https://territoriosinteligentes.gov.pt/comunidade/projetos/catalogo-nacional-de-modelos-de-dados-para-os-territorios-inteligentes-cnmd).

## Propriedades

Os modelos `VehicleModel` e `Vehicle` são modelos comuns, também documentados no [Catálogo Nacional de Modelos de Dados para os Territórios Inteligentes (CNMD)](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/).

Na tabela abaixo são apresentadas as propriedades para o modelo `FleetVehicle`.

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `FleetVehicle` |
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado o serviço | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da entidade | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| fleetVehicleType | String | O tipo de veículo | Por exemplo, *Ambulance*, *VUCI*, *Taxi*. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para a entidade | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicle | URI | Referência para o veículo usado na operação | Referência a uma entidade do tipo  `Vehicle`. Modelo: [https://schema.org/URL](https://schema.org/URL) |

Na tabela abaixo são apresentadas as propriedades para o modelo `FleetVehicleOperation`.

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `FleetVehicleOperation` |
| address | Object | Morada associada a um local | Inclui concelho, freguesia, rua, número e código postal. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado o serviço | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da entidade | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endedAt | DateTime | A data e hora de fim da operação | Caso não seja possível atribuir um valor, o atributo deve ser omitido. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| fleetVehicle | URI | Referência para o veículo usado na operação | Referência a uma entidade do tipo  `fleetVehicle`. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| fleetVehicleOperation | URI | Referência para uma operação relacionada | Referência a uma entidade do tipo  `fleetVehicleOperation`. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| initiatingLocation | GeoJSON | Referência Geojson para onde a operação se iniciou | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| location | GeoJSON | Referência Geojson para a entidade | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome da entidade | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| operationType | String | Texto livre que decreve o tipo de operação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| responseTime | Number | Indica o tempo de resposta à solicitação. | Igual ou superior a zero. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| result | String | O resultado final da operação | Por exemplo, *complete*.Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| startedAt | DateTime | A data e hora de início da operação | O valor deve reflectir o primeiro contacto para iniciar a operação. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| transportTime | Number | O tempo de transporte | Valor superior a zero. [https://schema.org/Integer](https://schema.org/Integer) | 

## Propriedades obrigatórias

As propriedades obrigatórios para `FleetVehicle`:

- `id`
- `type`
- `address`

As propriedades obrigatórios para `FleetVehicleOperation`:

- `id`
- `type`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nestes modelos, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.