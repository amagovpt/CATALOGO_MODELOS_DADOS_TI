# Descrição

Os modelos de dados para representar **Cadastro de rede de abastecimento de água** é o `Hydrant` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `Hydrant`|
| address                  | Object          | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| beginLifespanVersion | DateTime | Início da versão no mundo real | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| category            | Array     | Lista de categorias associadas ao hidrante | Compatível com sistemas de Pontos de Interesse (POI). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| connectedTo   | Array     | Indicação da tubagem a que está ligado   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| criticalInfrastructure   | Boolean     | Especifica se o hidrante é uma infraestrutura crítica   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| datasetResponsibleParty  | String     | Responsável pelo conjunto de dados  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description         | String          | Descrição textual do hidrante | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endLifespanVersion | DateTime | Fim da versão no mundo real | A omitir se o valor for nulo.  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| flowRate     | Number     | Fluxo máximo do hidrante | Normalmente expressa em litros por minuto (LTM). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| geographicalName | Object | Informação do nome oficial | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| hydroId | Object | Identificador hidrográfico | Identificador hidrográfico associado ao componente, utilizado para referenciar sistemas ou entidades hidrológicas relevantes |
| image       | Array       | Imagem do hidrante   | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| installationDate         | DateTime | Data de instalação do hidrante | A omitir se o valor for nulo.  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| lastInspectionDate       | DateTime     | Data da última inspeção   | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| license     | URI     | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [ https://schema.org/URL]( https://schema.org/URL) | 
| location | GeoJSON | Referência Geojson para o hidratante |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| manufacturer    | String     | Fabricante do hidrante     | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| maintainer  | URI         | Responsável pela manutenção   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| maintenanceSchedule        | String     | Frequência de manutenção | Enumerado:  <br>- annual , <br>- biannual , <br>- quarterly , <br>- monthly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| model             | String     | Modelo do hidrante     | Modelo: [https://schema.org/Text](https://schema.org/Text) 
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| pressure             | Number     | Pressão típica no hidrante      | Normalmente expressa em bares (BAR).  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| quality   | Number     | Qualidade observada no componente de rede | Valor no intervalo [1 .. 5], onde 5 é excelente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| refNetwork   | URI         | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso  | URI     | Descrição e categorização adicionais | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| status                   | String     | Estado operacional do hidrante      | Enumerado: <br>- operational,<br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner   | URI         | Proprietário do hidrante    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| version   | String     | Versão do modelo de dados       |   Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| updateFrequency          | String     | Frequência de atualização dos dados    | Modelo: [https://schema.org/Text](https://schema.org/Text)|

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `name`
- `type`
- `location`
- `flowRate`
- `pressure`
- `refNetwork`
- `status`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.