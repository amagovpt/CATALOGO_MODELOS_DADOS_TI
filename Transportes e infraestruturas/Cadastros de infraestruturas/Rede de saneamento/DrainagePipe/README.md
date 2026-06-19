# Descrição

Os modelos de dados para representar **Cadastro de rede de saneamento** é o `DrainagePipe` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de indentificadores únicos](https://metadados.digital.gov.pt/#/catalogue/folder/b8474afb-2c16-477c-a980-f7ce6989e48d/description?edit=false). |
| type | String | Tipo de entidade | Valor constante igual a `DrainagePipe`|
| address                  | Object          | Morada associada ao item | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| alternateName       | String          | Nome alternativo para a tubagem de drenagem |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| backfillMaterial            | String     | Material de reaterro da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| beddingMaterial            | String     | Material de fundação da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| bulkCoeff | Number     | Coeficiente de velocidade de reação em massa da tubagem de drenagem | Coeficiente usado para análise da deterioração da qualidade da água em condutas da rede de água. Normalmente expressa em por dia (E91). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| connectedTo | Array         | Tubagens de drenagem ligadas    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| constructionMethod         | String     | Método de construção da tubagem de drenagem | Enumerado:<br>-  openCut,<br>-  trenchless,<br>-  microtunneling,<br>-  pipeJacking,<br>-  directionalDrilling. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| criticalInfrastructure   | Boolean     | Especifica se a tubagem de drenagem é uma infraestrutura crítica   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| crossSectionShape          | String     | Forma da secção transversal da tubagem de drenagem | Enumerado:<br>- circular,<br>- rectangular,<br>- elliptical,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| datasetResponsibleParty  | String     | Responsável pelo conjunto de dados  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description         | String          | Descrição textual da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| designCapacity             | Number     | Capacidade de escoamento projetada da tubagem de drenagem | Normalmente expressa em metros cúbicos por segundo (MQS). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| diameter | Number     | Diâmetro da tubagem de drenagem | Normalmente expressa em milímetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dimension                 | Object     | Dimensões da secção transversal da tubagem de drenagem | Altura e largura em milímetros (MMT) para formas não circulares, diâmetro para as circulares. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| downstreamNetwork          | Array         | Rede de jusante ligada à tubagem de drenagem | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| drainagePipeType           | String     | Tipo de tubagem de drenagem | Enumerado:<br>- mainSewer,<br>- branchSewer,<br>- interceptingSewerLine,<br>- stormDrain,<br>- culvert,<br>- infiltrationDrain,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| elevation                  | Object     | Elevação de início e de fim da tubagem de drenagem | Normalmente expressa em metros (MTR). Deve incluir as propriedades `start` e `end`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| endsAt | URI         | Ponto final da tubagem de drenagem | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)
|  expectedLifespan  | Number     | Vida útil esperada da tubagem de drenagem      | Normalmente expressa em anos (ANN). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| externalCoating            | String     | Revestimento externo da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| failureProbability         | Number     | Probabilidade de falha anual da tubagem de drenagem | Adimensional (C62). Valor entre 0 e 1. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| flow | Number     | Fluxo atual de escoamento da tubagem de drenagem | Normalmente expressa em metros cúbicos por segundo (MQS). Inclui metainformação `observedAt`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| flowDirection              | String     | Direção do fluxo da tubagem de drenagem | Enumerado:<br>- downstream,<br>- upstream,<br>- bidirectional. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| floodZone                 | Boolean     | Especifica se a tubagem de drenagem está em zona de leito de cheia | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| groundwaterLevel          | Number     | Nível de água subterrânea da tubagem de drenagem | Normalmente expressa em metros (MTR). Inclui metainformação `observedAt`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| image       | Array       | Imagem da tubagem de drenagem   | Lista de URL. Modelo: [ https://schema.org/URL]( https://schema.org/URL) |
| installationDate         | DateTime     | Data de instalação da tubagem de drenagem    | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| installationDepth          | Number     | Profundidade de instalação da tubagem de drenagem | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| internalLining             | String     | Revestimento interno da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| jointType                  | String     | Tipo de junta da tubagem de drenagem | Enumerado:<br>- spigot,<br>- flanged,<br>- welded,<br>- mechanical,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| lastCleaningDate         | DateTime     | Data da última limpeza da tubagem de drenagem   |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| lastInspectionDate       | DateTime     | Data da última inspeção da tubagem de drenagem  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| length                     | Number     | Comprimento total da tubagem de drenagem | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| license     | URI     | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [ https://schema.org/URL]( https://schema.org/URL) | 
| location | GeoJSON | Referência Geojson para a tubagem de drenagem |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. Normalmente é usado o tipo geométrico 'LineString'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| maintainer  | URI         | Responsável pela manutenção da tubagem de drenagem   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| maintenanceSchedule        | String     | Frequência de manutenção da tubagem de drenagem | Enumerado:  <br>- annual, <br>- biannual, <br>- quarterly, <br>- monthly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| material                   | String     | Material da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| materialClass              | String     | Classificação do material da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| maxAllowablePressure       | Number     | Pressão máxima permitida da tubagem de drenagem | Normalmente expressa em bar (BAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| operatingPressure          | Number     | Pressão operacional da tubagem de drenagem | Normalmente expressa em bar (BAR). Inclui metainformação `observedAt`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| operator | URI         | Operador da tubagem de drenagem | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| owner   | URI         | Proprietário da tubagem de drenagem    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pressureClass              | String     | Classe de pressão da tubagem de drenagem | Enumerado:<br>- PN6, <br>- PN10,<br>- PN12.5,<br>- PN16,<br>- PN20. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pressurized                | Boolean     | Especifica se a tubagem de drenagem é pressurizada | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| quality   | Number     | Qualidade observada no componente de rede | Valor no intervalo [1 .. 5], onde 5 é excelente. Pode incluir metainformação `observedBy`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| refNetwork   | URI         | Código único que identifica a rede à qual o componente pertence | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| restrictedAccess         | Boolean     | Especifica se o acesso à tubagem de drenagem é restrito   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| roughness                  | Number     | Rugosidade da tubagem de drenagem | Valor de coeficiente de rugosidade. Pode incluir metainformação `roughnessMethod`. Normalmente expressa em metros a menos 1/3 de potência por segundo (SM3). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| safetyNotes | String     | Notas de segurança da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso  | URI     | Descrição e categorização adicionais | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| seismicZone               | String     | Zona sísmica da tubagem de drenagem | Enumerado:<br>- low,<br>- moderate,<br>- high. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| slope                      | Number     | Inclinação da tubagem de drenagem | Adimensional (C62). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| soilCorrosivity           | String     | Corrosividade do solo da tubagem de drenagem | Enumerado:<br>- low,<br>- medium,<br>- high. De acordo com a norma [ASTM G57-20](https://standards.iteh.ai/catalog/standards/astm/7a46c599-57bd-4215-ae54-329a41394a4a/astm-g57-20?srsltid=AfmBOopQPj0U8fsEhrdQ0WvTkM7f-YPPiT11l6lkrI39vcP03jyqVi1N). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| startsAt | URI         | Ponto de início da tubagem de drenagem | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)
| status                   | String     | Estado operacional da tubagem de drenagem      | Enumerado: <br>- operational,<br>- planned, <br>- underConstruction, <br>- underMaintenance, <br>- outOfService, <br>- abandoned.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| surroundingSoilType        | String     | Tipo de solo ao redor da tubagem de drenagem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| updateFrequency          | String     | Frequência de atualização dos dados    | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| upstreamNetwork            | Array         | Rede de montante ligada à tubagem de drenagem | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| velocityRange              | Object     | Faixa de velocidade do fluxo da tubagem de drenagem | Valores mínimo e máximo em metros por segundo (MTS). Deve incluir as propriedades `minimum` e `maximum`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| version   | String     | Versão do modelo de dados       |   Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| verticalGeometry           | GeoJSON     | Geometria vertical da tubagem de drenagem | Coordenadas em 3D usando tipo geométrico 'LineString'. Modelo: [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| wallCoeff                  | Number     | Coeficiente de velocidade de reação da parede da tubagem de drenagem | Coeficiente usado para análise da deterioração da qualidade da água em condutas da rede de água. Normalmente expressa em miligramas por metro quadrado por dia (RRC). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| wallThickness              | Number     | Espessura da parede da tubagem de drenagem | Normalmente expressa em milímetros (MMT). Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `name`
- `type`
- `location`
- `elevation`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
