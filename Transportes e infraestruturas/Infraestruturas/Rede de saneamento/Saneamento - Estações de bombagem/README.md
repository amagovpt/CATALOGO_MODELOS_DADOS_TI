# Descrição

Os modelos de dados para representar **Cadastro de rede de saneamento** é o `PumpingStation` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `PumpingStation`|
| address                  | Object          | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| alternateName       | String          | Nome alternativo para a estação elevatória |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| backupPower | Object     | Descrição do sistema de energia de reserva da estação elevatória | Objeto complexo que pode incluir propriedades como `available`, `type`, `capacity`, `autonomy`. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| datasetResponsibleParty  | String     | Responsável pelo conjunto de dados  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description         | String          | Descrição textual da estação elevatória | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| documentation | Array       | Documentação da estação elevatória   | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| image       | Array       | Imagem da estação elevatória   | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| inletPipes | Array         | Tubagens de entrada da estação elevatória    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| installationDate         | DateTime     | Data de instalação da estação elevatória    | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| license     | URI     | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [ https://schema.org/URL]( https://schema.org/URL) | 
| location | GeoJSON | Referência Geojson para a estação elevatória |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. Normalmente é usado o tipo geométrico 'Point'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| maintainer  | URI         | Responsável pela manutenção da estação elevatória   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| maxFlowRate | Number     | Capacidade máxima de bombagem por unidade de tempo da estação elevatória | Normalmente expressa em metros cúbicos por hora (MQH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maxHead | Number     | Altura máxima manométrica que a estação elevatória consegue elevar o fluido | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maxInletPressure | Number     | Pressão máxima necessária à entrada das bombas para funcionamento correto | Normalmente expressa em bar (BAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maxOperatingLevel | Number     | Nível máximo de fluido no reservatório de admissão da estação elevatória | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maxPower | Number     | Consumo máximo de energia da estação elevatória | Normalmente expressa em quilowatts (KWT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| minInletPressure | Number     | Pressão mínima necessária à entrada das bombas para funcionamento correto | Normalmente expressa em bar (BAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| minOperatingLevel | Number     | Nível mínimo de fluido no reservatório de admissão da estação elevatória | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| numberOfPumps | Number     | Número de bombas da estação elevatória | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| operator | URI         | Operador da estação elevatória | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| outletPipes | Array         | Tubagens de saída da estação elevatória    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner   | URI         | Proprietário da estação elevatória    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pumpTypes | Array     | Tipos de bombas da estação elevatória | Lista de tipos de bombas. Enumerado:<br>- submersible, <br>- centrifugal,<br>- positive_displacement,<br>- backup,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refNetwork   | URI         | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refParametersObserved | Array         | Lista de referências para medidas de parâmetros da estação elevatória    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status                   | String     | Estado operacional da estação elevatória      | Enumerado: <br>- operational,<br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| updateFrequency          | String     | Frequência de atualização dos dados    | Enumerado:<br>- annual, <br>- monthly, <br>- weekly, <br>- daily. Modelo: [https://schema.org/Text](https://schema.org/Text)|
| version   | String     | Versão do modelo de dados       |   Modelo: [https://schema.org/Text](https://schema.org/Text)  |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `name`
- `type`
- `location`
- `refNetwork`
- `status`
- `numberOfPumps`
- `maxFlowRate`
- `maxHead`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
