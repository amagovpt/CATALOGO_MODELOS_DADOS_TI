# Descrição

Os modelos de dados a seguir para representar **Rega de espaços verdes**
são os [Garden](https://github.com/smart-data-models/dataModel.ParksAndGardens/blob/master/Garden/README.md) e [GreenspaceRecord](https://github.com/smart-data-models/dataModel.ParksAndGardens/blob/master/GreenspaceRecord/README.md) alinhados com o [FIWARE Smart Data Models](https://github.com/smart-data-models). Estes modelos utilizam o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Nas tabelas abaixo são apresentadas as propriedades presentes nos modelos de dados.

Para o modelo `Garden`:

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | String         | Tipo de entidade            | Valor constante igual a `Garden`.  |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed          | String          | Nome da zona geográfica observada  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| category | Array  | Categoria do jardim | Enumerado: <br>- public, <br>- private, <br>- botanical, <br>- castle, <br>- community, <br>- monastery, <br>- residential, <br>- fencedOff. <br>Ou qualquer outro valor necessário para uma aplicação.  Modelo: [https://schema.org/Text](https://schema.org/Text)|
| dateLastWatering        | DateTime | Data que corresponde à última rega deste jardim   |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location            | GeoJSON  | Localização geográfica do jardim  | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name                | String          | Nome ou identificador único do jardim  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nextWateringDeadline          | DateTime       | Data limite para a próxima rega a efetuar neste jardim |  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| openingHours | String       | Hora de abertura do jardim |  Modelo: [https://schema.org/openingHours]( https://schema.org/openingHours)                |
| owner     | Array       |   Identificadores únicos do(s) proprietário(s) | Lista que contém uma sequência de caracteres codificados em JSON |
| refRecord        | Array       | Lista dos registos que contêm medições relacionadas com este jardim |   Lista de referências a entidades do tipo `GreenspaceRecord`. Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        | 
| style          | String       | Estilo do jardim | Valores possíveis em [OpenStreetMap](http://wiki.openstreetmap.org/wiki/Key:garden:style). Modelo: [https://schema.org/Text](https://schema.org/Text)                |

Para o modelo `GreenspaceRecord`:

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type                | String         | Tipo de entidade            | Valor constante igual a `GreenspaceRecord`. |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed          | String          | Nome da zona geográfica observada  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location            | GeoJSON  | Localização geográfica do jardim  | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name                | String          | Nome ou identificador único do jardim  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner     | Array       |   Identificadores únicos do(s) proprietário(s) | Lista que contém uma sequência de caracteres codificados em JSON |
| refDevice        | Array       | Lista do dispositivo ou dispositivos utilizados para obter os dados indicados neste registo. |   Lista de referências a entidades do tipo `Device`. |
| refGreenspace         | String       | O jardim ou canteiro de flores a que se refere este registo |  Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| refWeatherObserved        | String       |   Condições meteorológicas observadas associadas às medições descritas por esta entidade |   Referência a entidades do tipo `WeatherObserved`. |
| soilMoistureEc    | Number   | Humidade do solo observada | Medida da condutividade elétrica. Normalmente expressa em Siemens por metro (S/m). Modelo: [https://schema.org/Number](https://schema.org/Number)     |
| soilMoisturePressure      | Number    | Humidade do solo observada    | Medida da pressão. Normalmente expressa em kiloPascal (KPa). Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| soilTemperature   | Number        | Temperatura do solo observada     | Normalmente expressa em graus Celsius. Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| source   | String        | URL para a fonte original dos dados da entidade.     | Recomenda-se que seja o nome de domínio totalmente qualificado do fornecedor de origem ou o URL do objeto de origem.  Modelo: [https://schema.org/URL](https://schema.org/URL)   |

## Propriedades obrigatórias

Os atributos obrigatórios para o modelo `Garden` são:

- `id`
- `type`
- `address`
- `location`
- `category`

Os atributos obrigatórios para o modelo `GreenspaceRecord` são:

- `id`
- `type`
- `address`
- `dateObserved`
- `location`
- `refGreenspace`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres). Para a entidade `GreenspaceRecord` para além das propriedades obrigatórios têm de ser fornecida uma leitura, que poderá depender do tipo de sensor usado.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
