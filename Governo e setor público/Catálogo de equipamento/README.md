# Descrição

Os modelos de dados a seguir para representar **Catálogo de equipamentos municipais**
é o `PublicEquipment` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id  | URI   | Identificador único da entidade que representa o equipamento público.    | Ver [Regra para geração de identificadores únicos](/FAQ.md).  |
| type| String| Tipo da entidade.  | Valor constante igual a `PublicEquipment`.          |
| accessibility    | Object| Informação sobre condições de acessibilidade do equipamento público.     | Pode incluir acessibilidade física, sensorial ou outras condições de acesso inclusivo.  O objeto inclui as seguintes propriedades booleanas: <br>- isAccessible,<br>- wheelchairAccessible,<br>- accessibleEntrance,<br>- accessibleToilet,<br>- accessibleParking,<br>- liftAvailable,<br>- brailleSignage,<br>- hearingLoop,<br>- serviceAnimalAllowed,<br>- signLanguageSupport,<br>- tactilePaving.  |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| areaServed | String| Área geográfica servida pelo equipamento público.      | Esta área pode ser uma comunidade intermunicipal, um município, uma frequesia, ou outra organização territorial relevante para efeitos de análise. Modelo: [https://schema.org/Text](https://schema.org/Text).|
| assetStatus| String| Estado do do equipamento para efeito de inventário.      | Deve ser usado os valores de [Condition Of Construction](https://inspire.ec.europa.eu/codelist/ConditionOfConstructionValue). Enumerado:<br> - declined, <br>- demolished, <br>- functional, <br>- projected, <br>- ruin, <br>- under construction. |
| capacity   | Number   | Capacidade do equipamento público.   | Normalmente associada à lotação máxima do equipamento. Modelo: [https://schema.org/Number](https://schema.org/Number)|
| category   | String| Categoria do equipamento público segundo um conjunto fechado de valores. | Enumerado: <br>- administrative,<br>- education,<br>- health,<br>- emergency,<br>- security,<br>- justice,<br>- socialCare,<br>- culture,<br>- sports,<br>- mobility,<br>- greenSpace,<br>- waste,<br>- water,<br>- sanitation,<br>- market,<br>- cemetery,<br>- animalWelfare,<br>- civilProtection,<br>- other.   |
| commissioningDate| Date ou DateTime | Data em que o equipamento, infraestrutura ou instalação entrou em operação do ponto de vista técnico. | Pode ser anterior a startServingDate quando existe um período de testes, preparação ou transição. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime). |
| condition  | String| Estado físico ou condição geral do equipamento público.| Enumerado: <br>- excellent,<br>- good,<br>- fair,<br>- poor,<br>- needsRepair. Quando o atributo refBuilding está preenchido, esta propriedade deve ser omitida ou estar consistente com os valores do edifício relacionado.          |
| contactPoint     | Object| Informação de contacto associada ao equipamento público.          | Modelo: [https://schema.org/ContactPoint](https://schema.org/ContactPoint).  |
| dataProvider     | String| Entidade fornecedora dos dados.      | Tipicamente corresponde à organização que disponibiliza ou mantém a informação.         |
| dateCreated| DateTime         | Data e hora da criação do registo.   | Normalmente atribuída pela plataforma.  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). |
| dateLastInspection    | Date ou DateTime | Data da última inspeção, vistoria ou avaliação técnica ao equipamento.   | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html).       |
| dateLastRenovation    | Date ou DateTime | Data da última reabilitação, renovação ou intervenção relevante no equipamento.     | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html).       |
| dateModified     | DateTime         | Data e hora da última alteração do registo.     | Normalmente atribuída pela plataforma. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html).   |
| description| String| Descrição textual do equipamento público.       | ---  |
| hasPart    | Array | Lista de entidades que constituem partes integrantes do equipamento.     | Pode referenciar diversos tipos de equipamentos, incluindo, edifícios, blocos, alas, campos, piscinas, auditórios ou outras partes do equipamento (e.g. baloiço). O domínio da propriedade é PublicEquipment.   |
| identifiers | Array  | Lista de identificadores adicionais atribuído ao equipamento por um sistema interno ou externo. | --- |
| image | Array   | Endereços para imagens representativas do equipamento público.   | Quando disponível, deve conter pelo menos um URL válido. Deve apontar para um recurso acessível.  |
| isPartOf   | URL   | Referência para uma entidade mais ampla da qual o equipamento faz parte.   | Exemplo: um pavilhão inserido num complexo desportivo. O domínio da propriedade é PublicEquipment.          |
| legalBasis | String ou URL    | Informação relativa ao diploma, regulamento ou ato administrativo associado ao equipamento.  | ---    |
| location   | GeoJSON          | Localização do objeto.        | Valores possíveis: Point, LineString, Polygon, MultiPoint, MultiLineString ou MultiPolygon. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue).   |
| managedBy  | URL   | Entidade responsável pela gestão administrativa do equipamento público.  | Pode ser diferente de owner e de operator.      |
| name| String| Designação oficial ou nome correntemente utilizado para identificar o equipamento público. | Deve conter a designação principal do equipamento.  |
| openingDate| Date ou DateTime | Data da abertura oficial ou inauguração do equipamento público.   | Pode coincidir com startServingDate. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime).        |
| openingHours     | Array| Horário de funcionamento do equipamento público.| Aplicável quando existe atendimento ou acesso em horário definido.  Modelo: [https://schema.org/openingHours](https://schema.org/openingHours)  |
| operator   | URL   | Entidade responsável pela operação ou gestão do equipamento público.     | Deve referenciar, por exemplo, uma entidade do tipo Organization.   |
| owner | URL   | Entidade proprietária do equipamento público.   | Pode coincidir com operator, mas não necessariamente.    |
| publicAccess     | Boolean          | Indica se o equipamento é acessível ao público em geral.          | ---|
| refBuilding    | URL   | Relação para a entidade [BuildingRegistration](/Governo%20e%20setor%20público/Urbanismo/README.md) associada ao equipamento público.         | ---  |
| refPointOfInterest    | URL   | Relação para uma entidade [PointOfInterest](/Comuns/POI/README.md) associada ao equipamento público.         | ---       |
| seeAlso    | Array | Lista de URI que apontam para recursos adicionais sobre o item.   | Pode apontar para projetos públicos ou documentos. Modelo: [https://schema.org/URL](https://schema.org/URL).     |
| serviceStatus    | String| Estado de serviço ou operacionalidade do equipamento público.     | Enumerado: inService, outOfService, underMaintenance, needsMaintenance, planned, closed.      |
| source| URL   | Fonte original dos dados relativos ao equipamento público.        | Pode referir um sistema de origem, catálogo ou dataset.    |
| startServingDate | Date ou DateTime | Data a partir da qual o equipamento público começou efetivamente a prestar serviço ao público.        | Deve ser igual ou superior aopeningDate, caso esta esteja preenchida. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime).|
| yearBuilt  | Integer          | Ano de construção do equipamento.    | Se o equipamento for um edifício, e se a propriedade refBuilding estiver preenchida, deve ser garantida consistência nos valores indicados. Modelo: [https://schema.org/Integer](https://schema.org/Integer)   |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `category`
- `condition`
- `location`
- `name`
- `owner`
- `serviceStatus`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.