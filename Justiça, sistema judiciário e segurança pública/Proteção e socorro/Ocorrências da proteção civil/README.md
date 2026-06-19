# Descrição

O modelo de dados a seguir para representar **Ocorrências da proteção civil**
é o `EmergencyIncident` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `EmergencyIncident`|
| affectedArea        | String | Área afetada pelo incidente     |  Descrição da área. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual do incidente | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| coordinatingAgencies | Array  | Agências envolvidas na gestão do incidente    |  Lista de nomes de agências. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| incidentPriority    | String | Prioridade do incidente         |   Enumerado: <br>- Emergency,<br>- High,<br>- Low.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| incidentType        | String | Tipo de incidente |  Enumerado: <br>- Flood,<br>- Earthquake,<br>- Storm,<br>- Wildfire,<br>- Landslide,<br>- Extreme Temperature,<br>- Drought,<br>- Volcanic Eruption,<br>- Industrial Accident,<br>- Transport Accident,<br>- Hazardous Material Spill,<br>- Structural Collapse,<br>- Power Outage,<br>- Cybersecurity Incident,<br>- Epidemic,<br>- Pandemic,<br>- Food Safety Incident,<br>- Water Contamination,<br>- Terrorist Attack,<br>- Armed Assault,<br>- Bomb Threat,<br>- Civil Disturbance. Modelo: [https://schema.org/Text](https://schema.org/Text) |  
| location | GeoJSON | Referência Geojson para o objecto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'  |
| reportedBy          | String | Entidade que relatou o incidente|  Enumerado: <br>- Citizen,<br>- Sensor,<br>- Agency. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| resourcesDeployed   | Object  | Recursos utilizados na resposta ao incidente  |  Lista de recursos com definição do tipo e quantidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| severity | String | Nível de gravidade do incidente | Enumerado: <br>- Low,<br>- Medium,<br>-  High. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status   | String | Estado atual do incidente       | Enumerado: <br>- In progress, <br>- Resolved, <br>- Closed.  Modelo: [https://schema.org/Text](https://schema.org/Text) |


## Propriedades obrigatórias

Os atributos obrigatórios são:
 - `id`
 - `type`
 - `dateCreated`
 - `dateModified`
 - `reportedBy`
 - `location`
 - `status`
 - `incidentPriority`
 - `incidentType`
 - `severity`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. 

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.

