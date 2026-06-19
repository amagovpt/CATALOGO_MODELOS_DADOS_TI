# Descrição

O modelo de dados a seguir para representar **Observações metereológicas**
é o [WeatherObserved](https://github.com/smart-data-models/dataModel.Weather/tree/master/WeatherObserved) alinhados  com o [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo usa o modelo das estações metereológicas `WeatherStation`. 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).

Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de indentificadores únicos](https://metadados.digital.gov.pt/#/catalogue/folder/b8474afb-2c16-477c-a980-f7ce6989e48d/description?edit=false). |
| type | String | Tipo de entidade | Valor constante a `WeatherObserved` |
| address                  | Object          | Morada associada à estação | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address](https://schema.org/address)  |
| airQualityIndex  | Number     | O índice de qualidade do ar  (AQI)|  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| airQualityIndexForecast  | Number     | Previsão do índice de qualidade do ar |  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| airTemperatureForecast  | Number     | Previsão do temperatura | Deve ser indicado na meta-informação do atributo qual o período temporal em que a previsão se aplica.  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| airTemperatureTSA  | Object     | Agregação de série temporal |  Deve ser incluído na meta-informação do atributo o momento em que foi iniciado a recolha, bem como o período de agregação.               |
| airTemperatureTSA.averageValue  | Number     | Valor médio da temperatura longo do tempo |   Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| airTemperatureTSA.instValue  | Number     | Valor instantâneo da temperatura |   Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| airTemperatureTSA.maxOverTime  | Number     | Valor máximo da temperatura |   Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| airTemperatureTSA.minOverTime  | Number     | Valor mínimo da temperatura |   Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| alternateName       | String          | Nome alternativo para a área de observação  |  Ex: nome comum ou local da localização  |
| aqiMajorPollutant       | String          | Principal poluente no Índice de Qualidade do Ar (AQI)  | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| aqiMajorPollutantForecast       | String          | Previsão do principal poluente no Índice de Qualidade do Ar (AQI)  | Deve ser indicado na meta-informação do atributo qual o período temporal em que a previsão se aplica. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| areaServed          | String          | Nome da zona geográfica observada  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| atmosphericPressure  | Number     | Pressão atmosférica | Normalmente expressa em hectopascais (hPa).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved             | DateTime        | Data e hora da observação  |  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual da observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dewPoint             | Number     | Temperatura do ponto de orvalho | Normalmente expressa em graus Celsius (CEL).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| diffuseIrradiation             | Number     | A irradiância difusa  |  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| directIrradiation             | Number     | A irradiância direta  |  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| feelLikesTemperature | Number     | Temperatura sentida | Normalmente expressa em graus Celsius (CEL).  Modelo: [https://schema.org/Number](https://schema.org/Number)                 |
| gustSpeed | Number     | Uma súbita rajada de vento de alta velocidade | Normalmente expressa em kilómetro/hora (KMH).  Modelo: [https://schema.org/Number](https://schema.org/Number)                 |
| illuminance | Number     | Intensidade instantânea da luz ambiente observada | Normalmente expressa em luminância (LUX).  Modelo: [https://schema.org/Number](https://schema.org/Number)                 |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name                | String          | Nome para o evento de observação específico |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner     | Array          | Uma lista de IDs do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| precipitation        | Number     | Precipitação registada | Normalmente expressa em milimetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number)  |
| precipitationForecast        | Number     | Previsão de precipitação para uma determinada duração no futuro | Deve ser indicado na meta-informação do atributo qual o período temporal em que a previsão se aplica. Normalmente expressa em milimetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number)  |
| pressureTendency        | String     | Tendência evolutiva da pressão | Enumerado:  <br>-falling, <br>- raising, <br>- steady. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| refDevice                | URI             | Referência ao dispositivo que realizou a medição | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| refPointOfInterest   | URI | Referência à estação meteorológica relacionada  | Modelo: [PointOfInterest](https://github.com/smart-data-models/dataModel.PointOfInterest/tree/a0bac118e8e92549d42cdec011453cdbd85e0d1d)      |
| relativeHumidity     | Number     | Humidade relativa instantânea observada  | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| relativeHumidityForecast     | Number     | Previsão da humidade relativa  | Deve ser indicado na meta-informação do atributo qual o período temporal em que a previsão se aplica. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| seeAlso     | Array          | Lista de URI de recursos adicionais associados ao item. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| solarRadiation       | Number     | Radiação solar | Normalmente expressa em Watts por metros quadrados (W/MTK). Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| source    | String    | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL    | Nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| stationCode          | String     | Código da estação meteorológica       | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| stationName          | String     | Nome da estação meteorológica   | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| streamGauge          | Number     | A elevação da superfície do nível da água   | Normalmente expresso em centímetros (CMT). Modelo: [https://schema.org/Number](https://schema.org/Number)  |
| temperature          | Number     | Temperatura do ar | Normalmente expressa em graus Celsius (CEL).  Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| uVIndexMax           | Number     | Valor máximo medido do índice UV | Com base na medida do [Índice UV da OMS](http://www.who.int/uv/intersunprogramme/activities/uv_index/en/). Valores entre 1 e 11 são o intervalo válido para o índice. Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| visibility          | String     | Categorias de visibilidade   | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| weatherType          | String     | Texto descritivo do tempo   | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| windDirection        | Number     | Direção do vento | Normalmente expressa em graus (DD). Definido de acordo com [world Meteorological organization](https://library.wmo.int/records/item/58104-the-2022-gcos-implementation-plan-gcos-244).  Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| windSpeed            | Number     | Velocidade do vento | Normalmente expressa em metros por segundo (MTS).  Modelo: [https://schema.org/Number](https://schema.org/Number)            |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `dateObserved`
- `dataProvider`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
