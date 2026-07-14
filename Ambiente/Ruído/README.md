# Descrição

O modelo de dados a seguir para representar **Medição de ruído**
é o [NoiseLevelObserved](https://github.com/smart-data-models/dataModel.Environment/tree/master/NoiseLevelObserved) alinhado com o [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utilizam o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da estação | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | Text         | Tipo de entidade            | Valor constante igual a `NoiseLevelObserved`|
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName     | String    | Nome alternativo    | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed    | String    | A área geográfica onde se aplica este modelo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Data e hora da modificação da entidade  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved        | DateTime | Data e hora da observação  | Codificado como um intervalo, de acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Conjugação num único atributo de `dateObservedTo` e de `dateObservedFrom`.  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObservedFrom        | DateTime | Data e hora do início da observação  | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObservedTo        | DateTime | Data e hora do fim da observação  | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html).  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String    | Descrição da entidade  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| distanceAverage   | String    | Distância média entre o sensor e as fontes potenciais de ruído  | Deve ser indicada a unidade de medida na metainformação.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| heightAverage   | String    | Altura média entre o sensor e as fontes potenciais de ruído  | Deve ser indicada a unidade de medida na metainformação.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| LAS  | Number    | O nível sonoro ponderado pela frequência (ponderação A) para um som lento, um segundo ou mais para cima e para baixo    | Normalmente expresso em dBA. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| LAeq  | Number    | O nível sonoro ponderado pela frequência (ponderação A)    | Normalmente expresso em dBA. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| LAeq_d  | Number    | Nível acústico ponderado em frequência (ponderação A) equivalente para um dia    | Normalmente expresso em dBA. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| LAmax  | Number    | Nível acústico ponderado em função da frequência (ponderação A) nível sonoro máximo   | Normalmente expresso em dBA. Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| location | GeoJSON | Referência Geojson para o ponto de interesse |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name  | String    | Nome do ponto de interesse    | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| obstacles   | String    | Tipo de obstáculos potenciais entre o sensor e a fonte de ruído  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner   | Array    | Lista dos IDs do(s) proprietário(s) | A existir a propriedade, tem de ter pelo menos um valor. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refDevice   | Objeto    | IDs do dispositivo que fez a observação |Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refWeatherObserved      | Objeto       | Referência para o informação meteorológica |Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| seeAlso      | Array       | Lista de URI para reursos adicionais | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| sonometerClass      | String       | Classe do sonómetro (0, 1, 2) de acordo com a ANSI utilizada para realizar esta observação | Enumerado: <br>- Class0, <br>- Class1, <br>- Class2.  Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| source      | String       | Fonte original dos dados da entidade. | URL. Modelo: [https://schema.org/Text](https://schema.org/Text)  |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `dateObservedFrom`
- `dateObservedTo`
- `dataProvider`
- `location`
- `LAeq`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.