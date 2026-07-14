# Descrição

Os modelos de dados a seguir para representar **Caraterização de barragens** e **Caraterização de albufeiras** são um conjunto constituído por 
`Dam` e `Reservoir` alinhados com o [FIWARE Smart Data Models](https://github.com/smart-data-models) e com o [INSPIRE](https://knowledge-base.inspire.ec.europa.eu/index_en). Note-se que o modelo `Reservoir` é compatível com o tipo similar, descrito no [WaterDistributionManagementEPANET](https://github.com/smart-data-models/dataModel.WaterDistributionManagementEPANET/blob/master/Reservoir/doc/spec.md).

Nas anotações é possível encontrar um exemplo destes modelos, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da barragem | Padrão identificador INSPIRE |
| type | String | Tipo de entidade. É constante para cada modelo de dados | Ver no exemplo o valor a incluir, de entre:`Dam`, `Reservoir`, `RiverBasin`, `WaterStorageTimeSeries`|
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo |Modelo: [https://schema.org/Text](https://schema.org/Text)|
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName     | String    | Nome alternativo    | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed    | String    | A área geográfica onde é prestado um serviço ou oferecido este artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description | String | Uma descrição do objeto representado| - |
| category | Array | Uma sequência de termos que pretendem classificar o objeto hidrográfico em taxionomias externas, e.g. INSPIRE| - |
| name | String | O nome do objeto | - |
| elevation | Número | A elevação acima de uma referência comum do Reservatório. |Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| head | Número | O topo da albufeira. | Normalmente expressa em metros (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| pressure | Número | A pressão exercida na albufeira. | Normalmente expressa em metros (MTQ).  Modelo: [https://schema.org/Number](https://schema.org/Number)|
| reservoirHead | Número | O topo observado da albufeira (`elevation` + `head`) da água no reservatório. | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| currentVolume | Número | O volume de água armazenado na albufeira. | Normalmente expressa em metros cúbicos (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| currentStorage | Número | A percentagem de enchimento da albufeira. | Expressa em percentagem (P1). |
| beginLifespanVersion | DateTime | Início da versão no mundo real | Propriedades temporais INSPIRE |
| endLifespanVersion | DateTime | Fim da versão no mundo real | Propriedades temporais INSPIRE |
| startOfOperation | DateTime | Data de inicio de operação| - |
| localType | String | Classificação do tipo de barragem | - |
| geographicalName | Objeto | Informação do nome oficial |  - |
| hydroId | Object | Identificador hidrográfico | Pode ser utilizado para conter um código nacional de identificação hidrológica.|
| hydroId.localId | String | Identificador local hidrográfico | - |
| hydroId.namespace | String | Um indicador do âmbito do identificador local | No caso de um identificador hidrográfico nacional deve ser um código de país de duas letras de acordo com a norma [ISO 3166-1-Alpha-2](https://www.iso.org/obp/ui/#search)|
| hydroId.classificationScheme` | String | Uma descrição do sistema de identificação (nacional, europeu, etc.) que está a ser utilizado. | - |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico. Pode ser Point, LineString, Polygon, MultiPoint, MultiLineString ou MultiPolygon|  O mesmo que [`Geometry`](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue). |
| levelOfDetail | Objeto | Informação de escala | Denominador de escala |
| condition | String | Condição física da barragem |  Enumerado: <br>- functional<br>- abandoned<br>- disused<br>- underConstruction<br>- underMaintenance |
| operationalStatus | String | Estado operacional | Enumerado: <br>- operational<br>- nonOperational<br>- underMaintenance|
| height | Número | Altura da barragem acima da fundação | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| length | Número | Comprimento da barragem | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| crestElevation` | Número | Cota do coroamento | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| crestLength | Número | Desenvolvimento do coroamento | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| storageCapacity | Número | Capacidade de armazenamento | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| surfaceArea | Número | Área de superfície | Normalmente expressa em metros quadrados (MTK). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| deadStorage| Número | Volume da água de uma albufeira que não pode ser drenada por gravidade e que só pode ser bombeada para fora. |Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number)|
| maximumFloodLevel| Número | Cota do nível de máxima cheia |Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number)|
| levelFullStorage| Número | Cota do nível de pleno armazenamento |Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number)|
| minimumOperatingLevel| Número | Cota do nível mínimo de exploração |Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number)|
| spillwayFlowRate | Número | Caudal de dimensionamento do descarregador | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| spillwayType | String | Tipo de descarregador | - |
| maxBottomDischargeFlow | Número | Caudal máximo da descarga de fundo | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maxElevation | Número | Altitude máxima da bacia | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| meanElevation | Número | Altitude média da bacia  | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| minElevation | Número | Altitude mínima da bacia  | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| meanSlope | Número | Declive médio da bacia | Valores percentuais entre 0 e 100 (P1) |
| meanAnnualPrecipitation | Número | Precipitação média anual na bacia hidrográfica própria| Normalmente expressa em milímetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| manMadeObject | String |Objeto artificial que se encontra no interior de uma massa de água e que tem um dos seguintes tipos de função: <br>- Retém a água; <br>- Regula a quantidade de água; <br>- Altera o curso da água; <br>- Permite o cruzamento de cursos de água.| Conceito [INSPIRE](http://inspire.ec.europa.eu/featureconcept/ManMadeObject) |
| watershedArea | Número | Área da bacia hidrográfica própria | Normalmente expressa em kilometros quadrados (KMK). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalWatershedArea | Número | Área da bacia hidrográfica total | Normalmente expressa em kilometros quadrados (KMK). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| waterStorage.currentVolume | Número | Volume atual de água | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| waterStorage.fillLevel | Número | Percentagem da capacidade total | Valores percentuais entre 0 e 100 (P1) |
| waterStorage.trendIndicator | String | Tendência atual do nível de água | Enumerado: <br>- increasing<br>- stable<br>- decreasing |
| waterStorage.reserveVolume | Número | Volume mínimo de reserva | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| waterStorage.samplingFrequency | String | Intervalo espectável entre amostras. | Valor definido de acordo com o ISO 86100, para a especificação de intervalos.|
| waterStorage.observedBy | URI | Referência ao dispositivo de monitorização | Referência para um [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md).|
| waterBody.artificial | Boolean | Se a massa de água é artificial | verdadeiro/falso |
| waterBody.heavilyModified | Boolean | Se a massa de água é fortemente modificada  | verdadeiro/falso |
| waterBody.assignment | String | Esquema de atribuição | Enumerado: <br>- WFD<br>- national<br>- regional |
| hydrologicalPersistence | String | Tipo de persistência de água | Enumerado:<br>- perennial<br>- intermittent<br>- ephemeral |
| relatedHydroObject | Array | Objetos hidrográficos relacionados, e.g. rio | Array of URIs |
| inRiverBasin | URI | Bacia Hidrográfica | URI reference |
| operatingCompany | Text |Entidade exploradora | - |

Propriedades obrigatórias:

**Dam**:

- `id`
- `type`
- `address`
- `beginLifespanVersion`
- `hydroId`
- `localType`
- `location`

**Reservoir**:

- `id`
- `type`
- `address`
- `beginLifespanVersion`
- `hydroId`
- `localType`
- `location`
- `reservoirHead`
- `usefulCapacity`

**RiverBasin**:

- `id`
- `type`
- `address`
- `beginLifespanVersion`
- `hydroId`
- `localType`
- `location`

## Notas

A representação a usar é NGSI-LD.
Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nestes modelos, para a propriedade `location` é necessário adicionar como meta-informação o campo `coordinateSystem`, tendo este como valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"` . Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o código UN/CEFACT Common Code (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de meta-informação específica para determinados verticais. No entanto, esses atributos são ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
