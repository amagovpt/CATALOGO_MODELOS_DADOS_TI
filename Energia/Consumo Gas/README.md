# Descrição

O modelo de dados a seguir para representar **Consumo de gas**
é o `GasConsumption` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo é utilizado para medições de consumo de gás natural, GLP (gás liquefeito de petróleo), biogás e outros tipos de combustíveis gasosos. Inclui atributos para várias medições relacionadas com o gás, como pressão, temperatura, caudal volumétrico, volumes corrigidos e não corrigidos, poder calorífico e qualidade do gás. 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `GasConsumption`|
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| alarmStatus | String | Estado atual de alarme | Valores possíveis: 'normal', 'warning', 'critical'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para a área de medida | Ex: nome comum ou local da localização. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| calorificValue | Number | Poder calorífico do gás | Normalmente expressa em megajoule por metro cúbico (JM). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| conversionFactor | Number | Fator de conversão aplicado para converter volume de trabalho para condições padrão | Condições normais de temperatura e pressão (NTP). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| correctedVolume | Number | Volume de gás corrigido para condições padrão | Condições padrão: 15°C (CEL), 1013.25 mbar (MBAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dailyConsumption | Number | Consumo de gás para o dia atual | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateEnergyMeteringStarted | DateTime | Data de início da contagem da energia | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObserved | DateTime | Data e hora da observação | Pode ser representado por um instante de tempo específico ou por um intervalo [ISO 8601-1:2019](https://www.iso.org/standard/70907.html) para separar os atributos `dateObservedFrom`,`dateObservedTo`. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| energyContent | Number | Quantidade total de energia contida no volume de gás medido | Normalmente expressa em megajoule (MJ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| gasQuality | Object | Composição do gás com percentagens por volume | Inclui metano, nitrogénio, dióxido de carbono, sulfureto de hidrogénio, etc. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| gasType | String | Tipo de gás sendo medido | Valores possíveis: 'natural gas', 'LPG', 'biogas', etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastMaintenanceDate | DateTime | Data da última manutenção realizada no contador | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| location | GeoJSON | Referência Geojson para o objeto | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| meterStatus | String | Estado operacional atual do contador de gás | Valores possíveis: 'operational', 'maintenance', 'error', 'offline'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| meterType | String | Tipo de contador de gás | Valores possíveis: 'mechanical', 'electronic', 'smart meter', etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| monthlyConsumption | Number | Consumo de gás para o mês atual | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nextCalibrationDate | DateTime | Próxima data de calibração programada para o contador | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| pressure | Number | Pressão do gás no ponto de medição | Normalmente expressa em milibar (MBR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| temperature | Number | Temperatura do gás no ponto de medição | Normalmente expressa em graus Celsius (CEL). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalConsumption | Number | Consumo total acumulado desde a instalação do contador | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| uncorrectedVolume | Number | Volume de gás nas condições de trabalho | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| volumeFlowRate | Number | Caudal volumétrico atual do gás | Normalmente expressa em metros cúbicos por hora (MQH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| yearlyConsumption | Number | Consumo de gás para o ano atual | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `dateObserved`
- `location`
- `gasType`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
