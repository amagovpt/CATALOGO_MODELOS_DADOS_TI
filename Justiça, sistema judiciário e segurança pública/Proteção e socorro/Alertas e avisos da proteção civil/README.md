# Descrição

O modelo de dados a seguir para representar **Alertas e avisos da proteção civil**
é o [Alert](https://github.com/smart-data-models/dataModel.Alert/tree/master/Alert) inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

# Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Alert`|
| alertSource   | URL | Fonte do alerta | Modelo: [http://schema.org/URL](http://schema.org/URL) |
| address  | Object | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| category | String | Categoria do alerta | Enumerado: <br>- traffic, <br>- naturalDisaster, <br>- weather, <br>- environment, <br>- health, <br>- security, <br>- agriculture. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateIssued | DateTime | Data e a hora em que o item foi emitido | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'|
| severity  | String | Severidade do alarme |    Modelo: [https://schema.org/Text](https://schema.org/Text) |
| subCategory | String | Descreve a subcategoria do alerta | Enumerado: <br>- trafficJam, <br>- carAccident, <br>- carWrongDirection, <br>- carStopped, <br>- pothole, <br>- roadClosed, <br>- roadWorks, <br>- hazardOnRoad, <br>- injuredBiker, <br>- pedestrianOnRoad, <br>- bikerOnRoad, <br>- tramApproaching, <br>- flood, <br>- tsunami, <br>- coastalEvent, <br>- earthquake, <br>- rainfall, <br>- highTemperature, <br>- lowTemperature, <br>- heatWave, <br>- coldWave, <br>- ice, <br>- snow, <br>- wind, <br>- fog, <br>- tornado, <br>- tropicalCyclone, <br>- hurricane, <br>- snow/ice, <br>- thunderstorms, <br>- fireRisk, <br>- avalancheRisk, <br>- floodRisk, <br>- airPollution, <br>- waterPollution, <br>- pollenConcentration, <br>- asthmaAttack, <br>- bumpedPatient, <br>- fallenPatient, <br>- heartAttack, <br>- suspiciousAction, <br>- robbery, <br>- assault, civilDisorder, buildingFire, <br>- forestFire, <br>- noxiousWeed, <br>- snail, <br>- insect, <br>- rodent, <br>- bacteria, <br>- microbe, <br>- fungus, <br>- mite, <br>- virus, <br>- nematodes, <br>- irrigation, <br>- fertilisation. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| validFrom | DateTime | Início do período de validade desta previsão | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| validTo | DateTime | Fim do período de validade desta previsão | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`,
- `alertSource`
- `category`
- `dateIssued`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.