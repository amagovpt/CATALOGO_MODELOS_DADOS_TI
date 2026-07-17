# Descrição

Os modelos de dados para representar **Cadastro de rede de abastecimento de água** é o `Junction` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Junction`|
| address                  | Object          | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| alternateName       | String          | Nome alternativo para a junção |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| datasetResponsibleParty  | String     | Responsável pelo conjunto de dados  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description         | String          | Descrição textual da junção de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| designFlow  | Number     | Caudal projetado     | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dimension   | Object     | Dimensões da junção, incluindo diâmetro ou medidas para formas não circulares | Normalmente expressa em milímetros (MMT). Para as junções circulares definir a propriedade `diameter`; para as restantes definir as propriedades `length` e `width` da sua caixa envolvente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| disinfectantResidual | Number     | Concentração residual de desinfetante (ex: cloro, cloramina)    | Normalmente expressa em miligramas por litro (MG/L). Relevante para as junções do sistema 'potableWater'.   Modelo: [https://schema.org/Number](https://schema.org/Number) |
| downstreamJunctions      | Array         | Junções a jusante    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| chlorinationPoint  | Boolean     | Local onde desinfectantes são injetados no abastecimento de água  | Relevante para as junções do sistema 'potableWater'. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| connectedPipes  | URI         | Tubagens conectados à junção    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| concessionaire | URI         | Concessionário da rede | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| currentFlow              | Number     | Descreve o caudal medido em tempo real ou recentemente que passa pela junção | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| criticalInfrastructure   | Boolean     | Especifica se a junção é infraestrutura crítica  | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| elevation  | Number     | Cota (altitude) do ponto onde a junção se encontra  | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
|  expectedLifespan  | Number     | Vida útil esperada      | Normalmente expressa em anos (ANN). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| hasAirReleaseValve    | Boolean     | Especifica se a junção possui válvula de ar     | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasBackflowPrevention | Boolean     | Especifica se existe um mecanismo que impede o refluxo da água contaminada para a rede principal   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasInspectionHatch               | Propriedade     |Especifica se a junção possui escotilha de observação   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasValveChamber    | Boolean     | Especifica se a junção possui válvula     | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hydraulicHead    | Number     | Altura hidráulica     | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| incomingFlows    | Array         | Tubagens que trazem fluxo para a junção    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)
| installationDate         | DateTime     | Data de instalação da junção    | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| junctionFunction    | String     | Função de junção         | Enumerado:  <br>- connectPipes, <br>- changeFlowDirection, <br>- branchDistribution, <br>- regulateFlow, <br>- managePressureZones. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| junctionType   | String     | Tipo de junção         | Enumerado:  <br>- teeJunction, <br>- crossJunction, <br>- angleJunction, <br>- reducerJunction, <br>- wyeJunction , <br>- manifoldJunction. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastInspectionDate       | DateTime     | Data da última inspeção  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| lastCleaningDate         | DateTime     | Data da última limpeza   |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| license   | URI     | Licença associada aos dados   | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| image       | Array       | Imagem da junção   | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| maintainer  | URI         | Responsável pela manutenção   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| maintenanceSchedule        | String     | Frequência de manutenção | Enumerado:  <br>- annual , <br>- biannual , <br>- quarterly , <br>- monthly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| material   | String     | Material de construção da estrutura da junção      | Valores possíveis: 'concrete', 'plastic', 'steel', 'castIron'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| materialClass    | String     | Classificação do material da junção | Valores possíveis:  'metallic', 'non-metallic', 'composite'. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| quality   | Number     | Qualidade observada no componente de rede | Valor no intervalo [1 .. 5], onde 5 é excelente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| refNetwork   | URI         | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso  | URI     | Descrição e categorização adicionais | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| status    | String     | Estado operacional da junção  | Enumerado: <br>- operational, <br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner   | URI         | Proprietário da junção    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pressureClass   | String      | Classe de resistência à pressão da construção da junção (propriedade em nível de projeto)    |  Valores possíveis: 'PN6', 'PN10', 'PN16' e 'PN25' ([ISO2531:2009](https://www.iso.org/standard/40396.html) & [EN 805:2025](https://online.standard.no/en/ns-en-805-2025))|
| pressureZone   | Propriedade     | Zona de pressão   | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| operatingPressure  | Number     | Pressão da junção   | Normalmente expressa em bar (BAR). Relevante para as junções dos sistemas 'potableWater', 'irrigation', 'industrialWater'. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| outgoingFlows   | Array         | Tubagens que levam fluxo para fora da junção    | Referência URN a(s) uma(s) entidade(s).  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| upstreamJunctions        | Array         | Junções a montante     | | Referência URN a(s) uma(s) entidade(s).  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| restrictedAccess         | Boolean     | Especifica se o acesso à junção é restrito   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| slope    | Number     | Inclinação da junção em relação ao plano horizontal | Relevante para o comportamento hidráulico. Normalmente expressa em graus (DEG). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| updateFrequency          | String     | Frequência de atualização dos dados    | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| version   | String     | Versão do modelo de dados       |   Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| waterQualityIndex        | Number     | Qualidade da água    | Valores percentuais entre 0 e 100 (P1). Modelo: [https://schema.org/Number](https://schema.org/Number) |


## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `name`
- `type`
- `location`
- `refNetwork`
- `diameter`
- `material`
- `materialClass`
- `pressureClass`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.