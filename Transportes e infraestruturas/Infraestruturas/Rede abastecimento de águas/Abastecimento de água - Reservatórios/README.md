# Descrição

Os modelos de dados para representar **Cadastro de rede de abastecimento de água** é o `Tank` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `Tank`|
| address | Object | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address) |
| beginLifespanVersion | DateTime | Início da versão no mundo real | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| category | Array | Lista de categorias associadas ao depósito | Valores possíveis: 'elevated', 'ground', 'underground', 'floating'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| connectedTo | Array | Indicação da tubagem a que está ligado | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| criticalInfrastructure | Boolean | Especifica se o depósito é uma infraestrutura crítica | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| currentStorage | Number | Percentagem de armazenamento atual | Valor entre 0 e 100 (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| currentVolume | Number | Volume atual de água no depósito | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| datasetResponsibleParty | String | Responsável pelo conjunto de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description | String | Descrição textual do depósito | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dimension | Object | Dimensões do depósito | Para depósitos cilíndricos definir as propriedades `diameter` e `height`; para outros formatos definir `length`, `width` e `height`. Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| elevation | Number | Cota (altitude) do ponto onde o depósito se encontra | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| endLifespanVersion | DateTime | Fim da versão no mundo real | A omitir se o valor for nulo. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| geographicalName | Object | Informação do nome oficial | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| hydroId | Object | Identificador hidrográfico | Identificador hidrográfico associado ao componente, utilizado para referenciar sistemas ou entidades hidrológicas relevantes |
| image | Array | Imagem do depósito | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| inspectionFrequency | String | Frequência de inspeção | Enumerado: <br>- annual, <br>- biennial, <br>- triennial, <br>- quinquennial. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| installationDate | DateTime | Data de instalação do depósito | A omitir se o valor for nulo. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| lastInspectionDate | DateTime | Data da última inspeção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| license | URI | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| location | GeoJSON | Referência Geojson para o depósito | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| material | String | Material de construção do depósito | Valores possíveis: 'concrete', 'steel', 'fiberglass', 'polyethylene', 'prestressed_concrete'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | URI | Proprietário do depósito | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| quality | Number | Qualidade observada no componente de rede | Valor no intervalo [1 .. 5], onde 5 é excelente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| refNetwork | URI | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Descrição e categorização adicionais | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| status | String | Estado operacional do depósito | Enumerado: <br>- operational, <br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| storageCapacity | Number | Capacidade total de armazenamento do depósito | Normalmente expressa em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| updateFrequency | String | Frequência de atualização dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| version | String | Versão do modelo de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `name`
- `type`
- `location`
- `elevation`
- `storageCapacity`
- `refNetwork`
- `status`
- `currentVolume`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.