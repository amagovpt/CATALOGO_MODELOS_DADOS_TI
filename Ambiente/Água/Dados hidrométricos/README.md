# Descrição

Os modelos de dados a seguir para representar **Dados hidrométricos**
são os [WaterObserved](https://github.com/smart-data-models/dataModel.Environment/blob/master/WaterObserved/README.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo destes modelos, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | Text         | Tipo de entidade            | Valor constante igual a ``WaterObserved``|
| alternateName       | String          | Nome alternativo para a área de observação  |  Ex: nome comum ou local da localização  |
| areaServed          | String          | Nome da zona geográfica observada  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider     | String          | Identidade do fornecedor dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved        | DateTime | Data e hora da observação  |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObservedFrom        | DateTime | Data e hora do início da observação  | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObservedTo        | DateTime | Data e hora do fim da observação  | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html).  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual da observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| flow                | Number       | Caudal de água | Ex: caudal de descarga em metros cúbicos por segundo (MQS).  Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| height              | Number       |  Medição da altura à superfície da água | Normalmente expressa em metros (MTR).   Modelo: [https://schema.org/Number](https://schema.org/Number)              |
| location            | GeoJSON  | Localização geográfica da observação | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| measuredArea        | Number       | Área medida durante a observação | Normalmente expressa em metros quadrados (MTK). Modelo: [https://schema.org/Number](https://schema.org/Number)                             |
| name                | String          | Nome para o evento de observação específico |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| objectArea          | Number       | Percentagem ocupada por um objeto flutuante na área | Valores percentuais entre 0 e 100 (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| objectHeightAverage | Number       | Altura média elevada | Normalmente expressa em metros (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| objectHeightMax     | Number       |  Altura máxima elevada| Normalmente expressa em metros (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| objectVolume        | Number       | Estimativa do volume total | Normalmente expressa em metros (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| owner     | Array          | Uma lista de IDs do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso     | Array          | Lista de URI de recursos adicionais associados ao item. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source     | String          | Origem dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refDevice                | URI             | Referência ao dispositivo que realizou a medição | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| swellDirection      | Number       | Direção das ondulações observadas | Normalmente expressa em graus (DD).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| swellHeight         | Number       | Altura da ondulação observada | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/height](https://schema.org/height)                  |
| swellPeriod         | Number       | Período de ondulação observado | Normalmente expressa em segundos (SEC).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| waterLevel          | Number       | Nível atual da água correspondente ao ponto de observação | Normalmente expressa em metros (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |
| waveLength          | Number       | Comprimento de onda observado | Normalmente expressa em metros (MTR).  Modelo: [https://schema.org/Number](https://schema.org/Number)                |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `dateObserved`
- `id`
- `location`
- `type`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres). Neste modelo temos para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este como valor um código [EPSG](https://epsg.org/crs_4326/WGS-84.html), por exemplo `"coordinateSystem": "EPSG:4326"`.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
