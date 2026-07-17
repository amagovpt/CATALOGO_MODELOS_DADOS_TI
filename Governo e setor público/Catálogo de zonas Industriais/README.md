# Descrição

Os modelos de dados a seguir para representar **Catálogo de zonas insdustriais**
são o `IndustrialZone` e `IndustrialLot` inspirados no [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Estes modelos utilizam o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

Para o modelo de dados IndustrialZone:

| Propriedade | Tipo | Descrição | Nota |
|---|---|---|---|
| id | URI | Identificador único da entidade NGSI-LD que representa a zona industrial. | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo da entidade. Identifica semanticamente que o recurso corresponde a uma zona industrial. | Valor fixo: `IndustrialZone` |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| alternateName | String | Nome alternativo pelo qual a zona industrial também pode ser conhecida. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| availabilityStatus | String | Estado agregado de disponibilidade da zona industrial. | Enumerado: <br>- free, <br>- occupied, <br>- reserved, <br>- mixed, <br>- unavailable. |
| availableLandArea | Number | Área total disponível para instalação de novas atividades dentro da zona industrial. | Unidade recomendada: MTK |
| beginLifespanVersion | DateTime | Data de início da versão de vida do registo. | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated | DateTime | Data e hora da criação do registo. | Normalmente atribuída pela plataforma. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Data e hora da última alteração do registo. | Normalmente atribuída pela plataforma. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da vocação e finalidade da zona industrial. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ecoIndustrialFeatures | Array | Conjunto de características de sustentabilidade e simbiose industrial da zona. | Valores possíveis (singulares ou combinação):<br>- sharedWasteManagement, <br>- resourceEfficiency, <br>- stormwaterManagement, <br>- industrialSymbiosis, <br>- waterReuse, <br>- renewableEnergyIntegration. |
| endLifespanVersion | DateTime | Data de fim da versão de vida do registo. | Se a propriedade estiver omissa considera-se o valor vazio, ou seja null. Caso esteja presente, o valor é null se a versão for a atual, ou uma data válida. |
| environmentalCertification | Boolean | Indica se a zona industrial possui certificação ambiental reconhecida. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| establishmentsCount | Integer | Número de estabelecimentos ou operadores instalados na zona industrial. | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| hasElectricity | Boolean | Indica se a zona dispõe de abastecimento de energia elétrica. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasGasNetwork | Boolean | Indica se a zona dispõe de rede de gás. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasLot | Relationship | Relação para um ou mais lotes integrados na zona industrial. | Referência URN a entidades do tipo IndustrialLot |
| hasTelecomConnectivity | Boolean | Indica se a zona dispõe de conetividade de telecomunicações. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasWastewaterService | Boolean | Indica se a zona dispõe de drenagem e tratamento de águas residuais. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasWaterSupply | Boolean | Indica se a zona dispõe de abastecimento de água. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| landUse | String | Uso do solo aplicável à zona industrial. | --- |
| location | GeoJSON | Localização do objeto  |  Valores possíveis: 'Polygon' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| municipality | Relationship | Relação para a entidade administrativa que representa o município onde a zona industrial se localiza. | Referência URN a uma entidade |
| name | String | Designação principal da zona industrial. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancyRate | Number | Percentagem agregada de ocupação da zona industrial. | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| occupiedLandArea | Number | Área agregada já ocupada por atividades económicas. | Unidade recomendada: MTK |
| portAccess | Boolean | Indica se a zona possui acesso portuário direto ou funcionalmente associado. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| railAccess | Boolean | Indica se a zona possui acesso ferroviário. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| refPointOfInterest | Relationship | Relação para um ponto de interesse associado à zona industrial. | Referência URN a uma entidade |
| reservedLandArea | Number | Área agregada já reservada, mas ainda não ocupada fisicamente. | Unidade recomendada: MTK |
| roadAccess | Boolean | Indica se a zona possui acesso rodoviário adequado. | Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| servicedLandArea | Number | Área total infraestruturada ou servida da zona industrial. | Unidade recomendada: MTK |
| source | String | Fonte administrativa, técnica ou documental que suporta os dados da entidade. | --- |

Para o modelo `IndustrialLot`:
| Propriedade | Tipo | Descrição | Nota |
|---|---|---|---|
| id | URI | Identificador único da entidade NGSI-LD que representa o lote industrial. | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo da entidade. Identifica semanticamente que o recurso corresponde a um lote industrial. | Valor fixo: `IndustrialLot` |
| activityCAE | Array | Código ou lista de códigos CAE correspondentes às atividades económicas exercidas no lote. | O valor deve seguir a lista oficial da CAE, consistente com a sua última publicação. |
| activityCategory | Array | Designação textual da atividade económica exercida no lote. | Deve estar consistente com o código CAE indicado. |
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| availabilityStatus | String | Estado agregado de disponibilidade da zona industrial. | Enumerado: <br>- free, <br>- occupied, <br>- reserved, <br>- mixed, <br>- unavailable. |
| beginLifespanVersion | DateTime | Data de início da versão de vida do registo. | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateCreated | DateTime | Data e hora da criação do registo. | Normalmente atribuída pela plataforma |
| dateModified | DateTime | Data e hora da última alteração do registo. | Normalmente atribuída pela plataforma |
| description | String | Descrição textual da vocação e finalidade da zona industrial. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endLifespanVersion | DateTime | Data de fim da versão de vida do registo. | Se omissa ou vazia, assume-se null |
| locatedInZone | Relationship | Relação para a zona industrial em que o lote se integra. | Referência URN a uma entidade do tipo `IndustrialZone` |
| location | GeoJSON | Localização do objeto  |  Valores possíveis: 'Polygon' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| lotArea | Number | Área total do lote industrial. | Unidade recomendada: MTK |
| lotNumber | Integer | Número ou identificador do lote dentro da zona industrial. | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| name | String | Designação principal do lote industrial. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| tenant | URN | Relação para as entidades que são arrendatária, ocupantes ou utilizadoras do lote. | Referências URN a uma entidade, tipicamente do tipo `Organization` |

## Propriedades obrigatórias

Os atributos obrigatórios para o modelo `IndustrialZone` são:

- `id`
- `type`
- `address`
- `availabilityStatus`
- `availableLandArea`
- `beginLifespanVersion`
- `location`
- `occupiedLandArea`

Os atributos obrigatórios para o modelo `IndustrialLot` são:

- `id`
- `type`
- `address`
- `availabilityStatus`
- `beginLifespanVersion`
- `lotArea`
- `lotNumber`
- `location`
- `locatedInZone`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
