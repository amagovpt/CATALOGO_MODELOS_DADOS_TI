# Descrição

O modelo de dados a seguir para representar **Observações de qualidade do ar**
é o [AirQualityObserved](https://github.com/smart-data-models/dataModel.Environment/tree/9e1ebf172c64da9ab8258a238061518c5210e5c6/AirQualityObserved) alinhado com o [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo usa o modelo das estações de qualidade do ar. Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/). 
Nas anotações é possível encontrar exemplo deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da estação | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | Text         | Tipo de entidade            | Valor constante igual a `AirQualityObserved`|
| address                  | Object          | Morada associada à estação | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address](https://schema.org/address)  |
| airQualityIndex     | Number    | Índice de qualidade do ar    | Número utilizado para indicar a qualidade do ar num determinado dia. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| airQualityLevel   | String    | Nível qualitativo da qualidade de ar | Nível global de preocupação com a saúde correspondente à qualidade do ar observada. Valores possíveis: 'Good', 'Moderate', 'Poor', 'Unhealthy', 'Severe', 'Hazardous'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName       | String          | Nome alternativo para a área de observação  |  Ex: nome comum ou local da localização  |
| areaServed    | String    |  Zona de nível superior a que pertence esta medição da qualidade do ar | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| as  | Number | Valor de arsénico    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| c6h6  | Number | Valor de benzeno encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
|  cd   | Number    |  Valor de cádmio encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
|  co   | Number    |  Valor de monóxido de carbono encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
|  charge   | Number    |  Tensão de carga de entrada do dispositivo de monitorização    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| co2   | Number    | Valor de dióxido de carbono encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| dataProvider     | String          | Identidade do fornecedor dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved  | DateTime    | A data e a hora desta observação | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String    | Descrição deste item   | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name  | String    | Nome deste item    | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| no   | Number    | Valor de monóxido de nitrogénio encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| nox   | Number    | Valor de outros óxidos de nitrogénio encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| no2   | Number    | Valor de dióxido de nitrogénio encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| o3  | Number    | Valor de ozono encontrado    | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| pm10   | Number    | Valor de partículas finas encontrado   | Partículas de diâmetro igual ou inferior a 10 micrómetros. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| pm25   | Number    | Valor de partículas finas encontrado   | Partículas de diâmetro igual ou inferior a 2,5 micrómetros. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| so2   | Number    | Valor de dióxido de enxofre encontrado  |  Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| c6h6Level  | String | Valor qualitativo de benzeno     | Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
|  coLevel   | String    |   Valor qualitativo de monóxido de carbono     | Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| co2Level   | String    |  Valor qualitativo de dióxido de carbono     | Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| noLevel   | String    |  Valor qualitativo de monóxido de nitrogénio     | Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| noxLevel   | String    |  Valor qualitativo de outros óxidos de nitrogénio     | Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| no2Level   | String    |  Valor qualitativo de dióxido de nitrogénio     | Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| o2Level   | String    |  Valor qualitativo de ozono     |  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| pm10Level   | String    |  Valor qualitativo de partículas finas    | Partículas de diâmetro igual ou inferior a 10 micrómetros. Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| pm25Level   | String    |  Valor qualitativo de partículas finas    | Partículas de diâmetro igual ou inferior a 2,5 micrómetros. Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| so2Level   | String    |  Valor qualitativo de dióxido de enxofre   |  Valores possíveis são: 'good', 'fair', 'moderate', 'poor', 'very poor', 'extremely poor'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| location | GeoJSON | Referência Geojson do item |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| precipitation | Number | Quantidade de precipitação de água    | Modelo: [https://schema.org/Number](https://schema.org/Number)    | 
| owner     | Array          | Uma lista de IDs do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refDevice                | URI             | Referência ao dispositivo que realizou a medição | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| refWeatherObserved                | URI             | Referência para as condições meteorológicas observadas associadas às medições | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| refPointOfInterest    | URI   | Referência ao ponto de interesse associado a esta observação |  Referência URI |
| relativeHumidity  | Number    | Humidade relativa do ar   | Valores percentuais expressa em partes por um. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| reliability   | Number    |  Fiabilidade correspondente à qualidade do ar observada | Valores percentuais expressa em partes por um. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| seeAlso     | Array          | Lista de URI de recursos adicionais associados ao item. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source    | String    | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL    | Nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| tpc | Number    | Concentração total de partículas em suspensão no ar. | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| tsp | Number    | Concentração de todas as partículas transportadas pelo ar, independentemente do seu tamanho ou composição | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| temperature | Number    | Temperatura medida | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| typeofLocation | String    | Tipo de localização do item amostrado | Enumerado: <br>indoor,<br> outdoor. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| volatileOrganicCompoundsTotal | Number    |  Total de compostos orgânicos voláteis | Inclui: Alkanes <C10, ketones <C6, aldehydes <C10, carboxylic acids <C5, aspirits<C7, Alkenes <C8, Aromatics. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| windDirection | Number    | Direção do cata-vento | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| windSpeed | Number    | Intensidade do vento | Modelo: [https://schema.org/Number](https://schema.org/Number)    |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `dataProvider`
- `dateObserved`
- `id`
- `location`
- `name`
- `type`
- `refPointOfInterest`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"` e o campo `altitude` que indica o altura da medição (se aplicável). Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
