# Descrição

Os modelos de dados para representar **Cadastro de rede de saneamento** é o `DrainageJunction` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `DrainageJunction`|
| address                  | Object          | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| alternateName       | String          | Nome alternativo para a junção de drenagem |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| connectedPipes  | Array         | Tubagens conectadas à junção de drenagem    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| coverDimensions          | Object     | Dimensões da tampa da junção de drenagem | Normalmente expressa em milímetros (MMT). Para as junções circulares definir a propriedade `diameter`; para as restantes definir as propriedades `length` e `width` da sua caixa envolvente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| coverMaterial            | String     | Material da tampa da junção de drenagem       | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| coverShape               | String     | Forma da tampa da junção de drenagem          | Enumerado: <br>- circular, <br>- rectangular, <br>- square, <br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| coverWeight              | Number     | Peso da tampa da junção de drenagem                     | Normalmente expressa em quilogramas (KGM). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| criticalInfrastructure   | Boolean     | Especifica se a junção de drenagem é uma infraestrutura crítica   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| datasetResponsibleParty  | String     | Responsável pelo conjunto de dados  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| depth                    | Number     | Profundidade da junção de drenagem            | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| description         | String          | Descrição textual da junção de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| designFlow  | Number     | Caudal projetado para a junção de drenagem     | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dimension   | Object     | Dimensões da junção de drenagem, incluindo diâmetro ou medidas para formas não circulares | Normalmente expressa em milímetros (MMT). Para as junções circulares definir a propriedade `diameter`; para as restantes definir as propriedades `length` e `width` da sua caixa envolvente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| downstreamJunctions      | Array         | Junções de drenagem a jusante    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| elevation  | Number     | Cota (altitude) do ponto onde a junção de drenagem se encontra  | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
|  expectedLifespan  | Number     | Vida útil esperada da junção de drenagem      | Normalmente expressa em anos (ANN). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| groundElevation          | Number     | Elevação do solo ao redor da junção de drenagem                                     | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| hasLadder                | Boolean     | Especifica se a junção de drenagem possui escada  | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasLanding               | Boolean     | Especifica se a junção de drenagem possui plataforma interna   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hasVent                  | Boolean     | Especifica se a junção de drenagem possui ventilação     | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| hydraulicHead    | Number     | Altura hidráulica da junção de drenagem     | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| image       | Array       | Imagem da junção de drenagem   | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| inflows    | Array         | Tubagens que trazem fluxo para a junção de drenagem    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)
| installationDate         | DateTime     | Data de instalação da junção de drenagem    | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| invertElevation          | Number     | Elevação do ponto mais baixo da junção de drenagem                                  | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| junctionType   | String     | Tipo de junção de drenagem         | Enumerado:  <br>- manhole, <br>- cleanout, <br>- inspection, <br>- inletChamber, <br>- catchBasin, <br>- junctionBox, <br>- sumpPit, <br>- overflow, <br>- energyDissipation. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastCleaningDate         | DateTime     | Data da última limpeza da junção de drenagem   |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| lastInspectionDate       | DateTime     | Data da última inspeção da junção de drenagem  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| license   | URI     | Licença associada aos dados   | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| loadRating               | String     | Classificação de carga da tampa da junção de drenagem   | Classificação de carga que segue o standard [EN 124-2:2015](https://standards.iteh.ai/catalog/standards/cen/ab54e80e-51be-4a51-8241-046861f684d4/en-124-2-2015?srsltid=AfmBOooyjv8ut4B9NICbneb2Cyzx6gAUZXRkk5E3wbka3RdwZZoY9svW). Enumerado: <br>- A15,<br>- B125,<br>- C250,<br>- D400,<br>- E600, F900. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para a junção de drenagem |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| maintainer  | URI         | Responsável pela manutenção da junção de drenagem   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| maintenanceSchedule        | String     | Frequência de manutenção da junção de drenagem | Enumerado:  <br>- annual, <br>- biannual, <br>- quarterly, <br>- monthly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| material   | String     | Material de construção da estrutura da junção de drenagem      | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| outflows   | Array         | Tubagens que levam fluxo para fora da junção de drenagem    | Referência URN a(s) uma(s) entidade(s).  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| owner   | URI         | Proprietário da junção de drenagem    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| quality   | Number     | Qualidade observada no componente de rede | Valor no intervalo [1 .. 5], onde 5 é excelente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| refNetwork   | URI         | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| restrictedAccess         | Boolean     | Especifica se o acesso à junção de drenagem é restrito   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| seeAlso  | URI     | Descrição e categorização adicionais | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| shape                    | String     | Forma da junção de drenagem                 | Enumerado: <br>- circular,<br>- rectangular,<br>- square,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status    | String     | Estado operacional da junção de drenagem  | Enumerado: <br>- operational, <br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| sumpDepth                | Number     | Profundidade do reservatório da junção de drenagem                                  | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| surchargeRisk            | String     | Nível de risco de sobrecarga da junção de drenagem      | Enumerado:<br>- low,<br>- medium,<br>- high. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| updateFrequency          | String     | Frequência de atualização dos dados    | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| upstreamJunctions        | Array         | Junções de drenagem a montante     | Referência URN a(s) uma(s) entidade(s).  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| version   | String     | Versão do modelo de dados       |   Modelo: [https://schema.org/Text](https://schema.org/Text)  |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `name`
- `type`
- `location`
- `maxFlowRate`
- `junctionType`
- `status`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
