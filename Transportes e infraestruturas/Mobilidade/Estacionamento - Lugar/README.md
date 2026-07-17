# Descrição

Os modelos de dados para representar **Estacionamento** é o [ParkingSpot](https://github.com/smart-data-models/dataModel.Parking/tree/master/ParkingSpot) do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `ParkingSpot`|
| address | Object | Morada associada ao lugar de estacionamento | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| annotations | Array | Anotações sobre o item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| category | Array | Categoria(s) do lugar de estacionamento | O lugar de estacionamento pertence a um local de estacionamento na rua (onStreet)ou fora da rua (offStreet). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| color | String | Cor do produto | Modelo: [https://schema.org/color](https://schema.org/color) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do lugar de estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| image | URI | Imagem do item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| length | Number | Comprimento do lugar de estacionamento | Modelo: [https://schema.org/length](https://schema.org/length) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refDevice | Array | Dispositivo que representa o sensor físico usado para monitorizar este lugar de estacionamento | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refParkingGroup | URI | Grupo ao qual o lugar de estacionamento pertence | Para fins de simplificação do modelo, apenas um grupo é permitido por lugar de estacionamento. Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refParkingSite | URI | Local de estacionamento ao qual o lugar de estacionamento pertence | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de URI apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status | String | Estado do lugar de estacionamento do ponto de vista da ocupação | Enumerado: <br>- closed,<br>- free,<br>- occupied,<br>- unknown. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| timeInstant | DateTime | Timestamp dos dados | Pode haver ambientes de produção onde o tipo de atributo é igual à string `ISO8601`. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| width | Number | Largura do lugar de estacionamento | Modelo: [https://schema.org/width](https://schema.org/width) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `location`
- `category`
- `refParkingSite`
- `status`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
