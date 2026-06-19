# Descrição

O modelo de dados a seguir para representar **Previsões metereológicas**
é o [WeatherForecast](https://github.com/smart-data-models/dataModel.Weather/tree/47c1426bc46b7effe454af4f32c52bff54fe25ff/WeatherForecast) inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da previsão | Ver [Regra para geração de indentificadores únicos](https://metadados.digital.gov.pt/#/catalogue/folder/b8474afb-2c16-477c-a980-f7ce6989e48d/description?edit=false). |
| type | String | Tipo de entidade | Valor constante a `WeatherForecast` |
| address                  | Object          | Morada associada ao ponto de medição | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateObserved             | DateTime        | Data e hora da observação  |  De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateIssued             | DateTime        | A data e a hora em que a previsão foi emitida pelo serviço de meteorologia  |  De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateRetrieved             | DateTime        | A data e a hora em que a previsão foi obtida  |  De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dayMaximum               | Object    | Valores máximos previstos para o período reportado | Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| dayMinimum              | Object    | Valores mínimos previstos para o período reportado | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| feelsLikeTemperature     | Number    | Temperatura sentida atual prevista | Normalmente expressa em graus Celsius (CEL). Modelo: [https://schema.org/Number](https://schema.org/Number)                   |
| location | GeoJSON | Referência Geojson para o objeto geográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| precipitationProbability | Number    | Probabilidade de precipitação | Valores entre 0 a 1. Modelo: [https://schema.org/Number](https://schema.org/Number)                   |
| refPointOfInterest   | String | Referência à estação meteorológica relacionada  | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)     |
| relativeHumidity         | Number    | Humidade relativa prevista | Valores entre 0 a 1. Modelo: [https://schema.org/Number](https://schema.org/Number)                   |
| source    | String    | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL    | Nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| temperature              | Number    | Temperatura do ar prevista | Normalmente expressa em graus Celsius (CEL). Modelo: [https://schema.org/Number](https://schema.org/Number)                   |
| uVIndexMax               | Number    | Valor máximo previsto do índice UV | Com base na medida do [Índice UV da OMS](http://www.who.int/uv/intersunprogramme/activities/uv_index/en/). Valores entre 1 e 11 são o intervalo válido para o índice. Modelo: [https://schema.org/Number](https://schema.org/Number)            |
| validFrom                | DateTime    | Data e hora de início do período de validade | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| validTo                  | DateTime    | Data e hora de fim do período de validade | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| validity                 | DateTime    | Período de validade desta previsão como um intervalo de tempo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| weatherType              | String    | Descrição textual do tempo | Ex: 'Céu limpo', 'Nublado', 'Chuva'. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| windSpeed                | Number    | Velocidade do vento prevista | Normalmente expressa em metros por segundo (MTS). Modelo: [https://schema.org/Number](https://schema.org/Number)            |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `dateIssued`
- `dataProvider`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
