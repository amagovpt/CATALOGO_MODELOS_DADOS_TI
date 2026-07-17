# Descrição

Os modelos de dados para representar **Cadastro de rede de abastecimento de água** é o `Pipe` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Pipe`|
| address | Object | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address) |
| alternateName | String | Nome alternativo para a tubagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| backfillMaterial | String | Material de reaterro | Valores possíveis: 'nativeSoil', 'granular', 'flowableFill'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| beddingMaterial | String | Material de fundação | Valores possíveis: 'gravel', 'sand', 'concrete', 'crushedStone'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| connectedTo | Array | Tubagens conectadas | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| constructionMethod | String | Método de construção | Valores possíveis: 'openExcavation', 'trenchless', 'microtunneling', 'directionalDrilling'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| criticalInfrastructure | Boolean | Especifica se a tubagem é infraestrutura crítica | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| crossSectionShape | String | Forma da secção transversal | Enumerado: <br>- circular, <br>- rectangular, <br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| currentFlow | Number | Fluxo atual de escoamento | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| datasetResponsibleParty | String | Responsável pelo conjunto de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description | String | Descrição textual da tubagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| designCapacity | Number | Capacidade de escoamento projetada | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| diameter | Number | Diâmetro da tubagem | Normalmente expressa em milímetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dimension | Object | Dimensões da secção transversal | Para formas não circulares definir as propriedades `height` e `width`; para circulares definir `diameter`. Normalmente expressa em milímetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| downstreamNetwork | URI | Rede de jusante ligada | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| elevation | Number | Elevação de início e fim da tubagem | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| endPoint | URI | Ponto final da tubagem | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| expectedLifespan | Number | Vida útil esperada | Normalmente expressa em anos (ANN). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| externalCoating | String | Revestimento externo | Valores possíveis: 'none', 'epoxy', 'bitumen', 'polyethylene', 'zinc'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| failureProbability | Number | Probabilidade de falha anual | Valor entre 0 e 1 (C62). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| floodZone | Boolean | Zona de leito de cheia | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| groundwaterLevel | Number | Nível de água subterrânea | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| image | Array | Imagem da tubagem | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| installationDate | DateTime | Data de instalação da tubagem | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| installationDepth | Number | Profundidade de instalação | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| internalLining | String | Revestimento interno | Valores possíveis: 'none', 'CIPP', 'epoxy', 'cement', 'polyurethane'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| jointType | String | Tipo de junta da tubagem | Valores possíveis: 'spigot', 'flanged', 'welded', 'mechanical', 'glued'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastCleaningDate | DateTime | Data da última limpeza | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| lastInspectionDate | DateTime | Data da última inspeção | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| length | Number | Comprimento total da tubagem | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| license | URI | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| location | GeoJSON | Referência Geojson para a tubagem | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| maintainer | URI | Responsável pela manutenção | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| maintenanceSchedule | String | Frequência de manutenção | Enumerado: <br>- annual, <br>- biannual, <br>- quarterly, <br>- monthly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| material | String | Material da tubagem | Valores possíveis: 'PVC', 'HDPE', 'castIron', 'ductileIron', 'steel', 'concrete', 'asbestoCement', 'copper', 'lead'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| materialClass | String | Classificação do material | Ex: 'SDR35', 'SDR17', 'Class150', 'Class300'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| maxAllowablePressure | Number | Pressão máxima permitida | Normalmente expressa em bar (BAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| operatingPressure | Number | Pressão operacional | Normalmente expressa em bar (BAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | URI | Proprietário da tubagem | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pressureClass | String | Classe de pressão da tubagem | Enumerado: <br>- PN6, <br>- PN10, <br>- PN12.5, <br>- PN16, <br>- PN20. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| quality | Number | Qualidade observada no componente de rede | Valor no intervalo [1 .. 5], onde 5 é excelente. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| refNetwork | URI | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| restrictedAccess | Boolean | Indica se há acesso restrito | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| seeAlso | URI | Descrição e categorização adicionais | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| seismicZone | String | Zona sísmica | Enumerado: <br>- low, <br>- moderate, <br>- high. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| slope | Number | Inclinação da tubagem | Adimensional (C62). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| soilCorrosivity | String | Corrosividade do solo | Enumerado: <br>- low, <br>- medium, <br>- high. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| startPoint | URI | Ponto de início da tubagem | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status | String | Estado operacional da tubagem | Enumerado: <br>- operational, <br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| surroundingSoilType | String | Tipo de solo ao redor | Valores possíveis: 'clay', 'sand', 'gravel', 'rock', 'silt', 'peat'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| updateFrequency | String | Frequência de atualização dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| upstreamNetwork | URI | Rede de montante ligada | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| velocityRange | Object | Faixa de velocidade do fluxo | Valores mínimo e máximo em metros por segundo (MTS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| version | String | Versão do modelo de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| verticalGeometry | Object | Geometria vertical da tubagem | Coordenadas em 3D. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| wallThickness | Number | Espessura da parede da tubagem | Normalmente expressa em milímetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |

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
- `currentFlow`
- `pressureClass`
- `slope`
- `status`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.