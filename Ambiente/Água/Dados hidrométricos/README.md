# Descrição

Os modelos de dados a seguir para representar **Dados hidrométricos**
são os [WaterObserved](https://github.com/smart-data-models/dataModel.Environment/blob/master/WaterObserved/README.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo destes modelos, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | Text         | Tipo de entidade            | Valor constante igual a ``WaterObserved``|
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao) |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao). Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
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
- `address`
- `location`
- `type`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres). Neste modelo temos para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este como valor um código [EPSG](https://epsg.org/crs_4326/WGS-84.html), por exemplo `"coordinateSystem": "EPSG:4326"`.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
