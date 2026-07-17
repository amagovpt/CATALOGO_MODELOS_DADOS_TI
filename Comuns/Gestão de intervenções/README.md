# Descrição

O modelo de dados a seguir para representar **Intervenção de Ativos**
é o `AssetIntervention` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `AssetIntervention`|
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateFinished        | DateTime | Registo de data e hora da conclusão da intervenção |  Este será normalmente atribuído pela plataforma de armazenamento. É omitido quando a intervenção está a decorrer. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateStarted        | DateTime | Registo de data e hora de início da intervenção |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String  | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| completionPercentage | Number   | Conclusão da intervenção   | Valores percentuais entre 0 e 100 (P1).  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| contactPoint    | Object       | Dados de contacto para emergência ou informações  | Inclui nome, telefone e email de contacto. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contractor    | String         | Nome do empreiteiro responsável   | Empresa contratada. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| estimatedDuration    | Number   | Duração estimada da intervenção  | Normalmente expressa em número de dias (DAY). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| impactLevel   | String   | Nível de impacto nas atividades normais do ativo. | Enumerado: <br>- None, <br>- Low, <br>- Moderate, <br>- High, <br>- Severe. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| infrastructureType   | String   | Tipo de infraestrutura afetada  | Enumerado: <br>- dam,<br>- retainingWall,<br>- slope/Embankment,<br>- drainageSystem,<br>- utilityNetworks,<br>- railway,<br>- harbor/PortInfrastructure,<br>- airportInfrastructure,<br>- publicSpaceStructures,<br>- slopeStabilizationStructures,<br>- pedestrianandCyclingInfrastructure. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| interventionType     | String   | Tipo de intervenção executada    | Enumerado: <br>- construction,<br>- rehabilitation/Renovation,<br>- maintenance,<br>- inspection/Monitoring,<br>- cleaningClearing,<br>- demolition/Removal,<br>- stabilization/Reinforcement,<br>- upgrading/Modernization,<br>- emergencyRepair,<br>- protectiveWorks,<br>- paving/Repaving,<br>- landscaping/EnvironmentalIntegration,<br>- dredging,<br>- coastalProtectionWorks,<br>- vegetationandLandManagementInterventions. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| inspectionAgent      | URI     | Organização responsável pela inspeção  |  Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| investment           | Number         | Investimento financeiro associado  | Normalmente expressa em euros (EUR). Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | O nome da intervenção |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| priority             | String    | Prioridade atribuída à intervenção   | Valores possíveis: 'Low', 'Medium', 'High'. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| responsibleAgent     | URI     | Organização responsável pela execução da intervenção       | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)       |
| responsibleAuthority | String         | Autoridade pública responsável pela supervisão   |  Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| seeAlso              | Array         | Lista de URI que apontam para recursos adicionais sobre o item          | Pode apontar para projetos públicos ou documentos. Modelo: [https://schema.org/URL](https://schema.org/URL)     |
| status               | String         | Estado atual da intervenção   | Valores possíveis: 'Planned', 'Scheduled', 'InProgress', 'Completed', 'Cancelled'.  Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| targetAsset          | URI     | Referência ao ativo ou infraestrutura afetada   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| workingDays          | Array         | Dias da semana em que decorre a intervenção    | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| workingHours   | String         | Horário diário previsto para os trabalhos   | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `name`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
