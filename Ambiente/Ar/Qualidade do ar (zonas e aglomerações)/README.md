# Descrição

O modelo de dados a seguir para representar **Qualidade do ar (zonas e aglomerações)**
é o [AirQualityMonitoring](https://github.com/smart-data-models/dataModel.Environment/blob/master/AirQualityMonitoring/doc/spec.md) alinhados com o [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo usa o modelo das estações de qualidade do ar. Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/). 
Nas anotações é possível encontrar exemplo deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | Text         | Tipo de entidade            | Valor constante igual a `AirQualityMonitoring`|
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| airQualityIndex     | Number    | Índice de qualidade do ar (AQI)    | Número utilizado para indicar a qualidade do ar num determinado dia. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| airQualityLevel   | String    | Indicação da categoria de qualidade do ar | Nível qualitativo definido de acordo com as agências de saúde locais. Valores possíveis:  'Good', 'Moderate', 'Poor', 'Unhealthy', 'Severe', 'Hazardous'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| airTemperatureTSA    | Object    |  Agregação  das séries temporais de temperatura do ar | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| alternateName | String    | Nome alternativo para este item   | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| ambientNoiseTSA  | Object | agregação  das séries temporais de ruído ambiente    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
|  aqiMajorPollutant   | String    |  Poluente principal no Índice de Qualidade do Ar    | Enumerado: <br>- arsénico, <br>- bap, <br>- benzeno, <br>- co2, <br>- nh3, <br>- no, <br>- no2, <br>- o2, <br>- o3, <br>- so2, <br>- pb. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| areaServed   | String    | Área geográfica | Onde é prestado um serviço ou oferecido um artigo. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| arsenicTSA   | Object    | Agregação das séries temporais de arsénio    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| atmosphericPressure   | Number    | Valor da pressão de ar observada    | Pode ser barométrica ou atmosférica. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| atmosphericPressureTSA   | Number    | Agregação das séries temporais de pressão atmosférica   | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| bapTSA   | Number    | Agregação das séries temporais de Benzo(a)Pireno    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| benzeneTSA   | Number    | Agregação das séries temporais de Benzeno   | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| co2TSA   | Number    | Agregação das séries temporais de dióxido de carbono   |  Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| coTSA   | Number    | Agregação das séries temporais de monóxido de carbono  |  Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| dataProvider  | String | Identificador do fornecedor     | Sequência de caracteres que identifica o fornecedor da entidade de dados. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
|  dateCreated   | DateTime    |   Data e hora de criação da entidade     | Normalmente atribuído pela plataforma de armazenamento. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)    |
| dateModified   | DateTime    |  Registo de data e hora da última modificação da entidade    | Normalmente é atribuído pela plataforma de armazenamento. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)      |
| description   | String    |  Descrição deste item     | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| deviceInfo   | Object    |  Informações sobre o dispositivo associado às observações     |  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| deviceStatus   | String    |  Indica o estado do(s) dispositivo(s) físico(s)     | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| location | GeoJSON | Referência Geojson do item |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name  | String    | Nome deste item    | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| nh3TSA | Object | Agregação de séries temporais de amoníaco    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| nickelTSA    | Object | Agregação de séries temporais de níquel    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| no2TSA  | Object | Agregação de séries temporais de dióxido de nitrogénio    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| noTSA  | Object | Agregação de séries temporais de monóxido de nitrogénio    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| o2TSA    | Object | Agregação de séries temporais de oxigénio    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| o3TSA    | Object | Agregação de séries temporais de ozono    | Modelo: [https://schema.org/Number](https://schema.org/Number)    | 
| observationDateTime | DateTime    | Última hora de observação comunicada |  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)   |
| pbTSA    | Object | Agregação de séries temporais de chumbo    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| pm10TSA    | Object | Agregação de séries temporais de partículas de finas    | Partículas em suspensão no ar com um diâmetro igual ou inferior a 10 micrómetros. Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| pm25TSA    | Object | Agregação de séries temporais de partículas de finas    | Partículas em suspensão no ar com um diâmetro igual ou inferior a 2,5 micrómetros. Modelo: [https://schema.org/Number](https://schema.org/Number)    |  
| precipitation    | Number | Nível de precipitação/chuva observado durante um determinado período    | Modelo: [https://schema.org/Number](https://schema.org/Number)    | 
| relativeHumidityTSA    | Object | Agregação de séries temporais de humidade relativa    | Modelo: [https://schema.org/Number](https://schema.org/Number)    | 
| so2TSA    | Object | Agregação de séries temporais de dióxido de enxofre    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| source    | String    | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL    | Nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| versionInfo    | Object | Informação da versão correspondente a esta observação    | Modelos: [https://schema.org/Text](https://schema.org/Text)  e  [https://schema.org/DateTime](https://schema.org/DateTime) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `dataProvider`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
