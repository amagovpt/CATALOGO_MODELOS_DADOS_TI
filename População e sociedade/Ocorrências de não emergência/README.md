# Descrição

O modelo de dados a seguir para representar **Ocorrências de não emergência**
é o `Incident` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `Incident`|
| address                  | Object          | Morada associada ao ponto de medição | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| assignedTo | Object | Departamento/organização que trata do incidente | Identificador válido da organização |
| category | String | Categoria principal do incidente | Enumerado: <br>- infrastructure,<br>- environment,<br>- security,<br>- cleanliness,<br>- publicServices,<br>- other|
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| expectedResponseTime | DateTime | Tempo esperado para responder  |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| images | Array | Imagens associadas ao incidente | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| name | String | Nome do incidente |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| notes | String | Notas adicionais |  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| reportedById | URI | Identificador do utilizador autenticado | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) 
| severity | String | Nível de severidade do incidente | Enumerado: <br>- low,<br>- moderate,<br>- high,<br>- critical.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| source | URI | Sistema ou entidade que criou o incidente | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| status | String | Status atual do incidente | Enumerado: <br>- open,<br>- inProgress,<br>- resolved,<br>- closed,<br>- cancelled. Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| subCategory | String | Tipo específico dentro da categoria principal | Ver abaixo |
| urgencyLevel | String | Classificação de prioridade | Enumerado: <br>- P1,<br>- P2,<br>- P3,<br>- P4, onde P1 é a prioridade mais alta. Modelo: [https://schema.org/Text](https://schema.org/Text)   |


## Propriedades obrigatórias

Os atributos obrigatórios são:
 - `id`
 - `type`
 - `dateCreated`
 - `location`
 - `status`
 - `category`

### SubCategories

Para cada categoria existe um refinamento de segundo nível na tipologia do incidente.

#### Infrastructure

 - sidewalk_damage
 - road_pothole
 - street_light_failure
 - traffic_signal_malfunction
 - fallen_tree
 - sidewalk_obstruction
 - construction_hazard

#### Infrastructure

 - sidewalk_damage
 - road_pothole
 - street_light_failure
 - traffic_signal_malfunction
 - fallen_tree
 - sidewalk_obstruction
 - construction_hazard

#### Environment

 - illegal_dumping
 - garbage_overflow
 - pest_problem
 - water_leak
 - noise_pollution
 - air_quality
 - vegetation_issue

#### Cleanliness

 - garbage_bin_full
 - street_cleaning_needed
 - graffiti
 - abandoned_vehicle
 - animal_waste
 - littering

#### Public Services

 - public_transport_issue
 - parking_violation
 - missing_signage
 - damaged_public_furniture
 - playground_equipment_damage
 - accessibility_issue

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. 

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.

