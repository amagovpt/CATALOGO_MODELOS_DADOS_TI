# Descrição

O modelo de dados a seguir para representar **Zonas de gestão ambientais**
é o `EnvironmentalManagementZone` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id    | URI       | Identificador único da zona | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type  | String    | Tipo de entidade | Valor constante igual a `EnvironmentalManagementZone` |
| areaServed | Array | A área geográfica que é gerida | Usar, sempre que possível, a área geográfica mais abrangente, para minimizar o número de entradas para situações onde existe gestão por associações de municípios. Modelo: [https://schema.org/Text](https://schema.org/Text)|
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified       | DateTime | Data de modificação da zona de gestão de ambiental  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String   | Descrição textual | Descrição adicional da zona. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| controlledActivityType        | Array        | Atividades controladas ou reguladas na zona| Enumerado: <br>- 'WasteManagement', <br>- 'LandUse', <br>- 'IndustrialActivities', <br>- 'ConstructionActivities', <br>- 'AgriculturalPractices', <br>- 'FishingAndAquaculture', <br>- 'TransportOperations', <br>- 'WaterSupply', <br>- 'WasteWater'. Embora seja possível o uso de mais do que uma atividade, tal só fará sentido se a entidade gestora das duas atividades for a mesma. Modelo: [https://schema.org/Text](https://schema.org/Text)      |
| controlTypeCode | Array        | Forma como as actividades na zona são controladas | Enumerado: <br>- 'Prohibited', <br>- 'Restricted', <br>- 'Managed', <br>- 'Permitted', <br>- 'Monitored'. Note-se que há combinações que não são possíveis, e.g. 'Prohibited' e 'Permitted'. Modelo: [https://schema.org/Text](https://schema.org/Text)|
| environmentalDomain    | String    | Domínio ambiental relacionado com a zona gerida | Enumerado: <br>- 'waste', <br>- 'water', <br>- 'air', <br>- 'soil', <br>- 'biota', <br>- 'naturalResources', <br>- 'health', <br>- 'climate'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para a zona gerida |  Valores possíveis: 'Polygon' ou 'MultiPolygon'. |
| managedBy | String  | Organização ou entidade responsável pela gestão da zona   | Descrição de entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| managementModel | String | O modelo de gestão/conceção para a zona | Enumerado: <br>- 'direct_provision-CIM', <br>- 'direct_provision-municipal_service', <br>- 'direct_provision-municipalised_intermunicipalised_service', <br>- 'delegation-state', <br>- 'delegation-partnerships', <br>- 'delegation-municipalised_intermunicipalised_companies', <br>- 'concession-municipal', <br>- 'concession-multimunicipal', <br>- 'other' . Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | O nome da zona | Nome legível que identifica a zona. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| population | Number        | População da zona |  População abrangida pela zona de gestão. Assume-se o valor dos últimos censos. Este valor é aproximado, se a área da zona resulta se intercepta com diferentes sub-seções estatísticas. Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| refUpperZone | String | Identificador da zona agregadora de que esta zona faz parte | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| typeOfService | String | O tipo de serviço reportado para a zona | Enumerado: <br>- 'high', <br>- 'low'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| validFrom   | DateTime | Hora de início de validade da versão da zona de gestão | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| validTo     | DateTime | Data de fim de validade da versão da zona de gestão de resíduos | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| zoneTypeCode  | String    | Tipo da zona | Conforme classificação INSPIRE. Valores possíveis: <br>- 'WasteDisposalZone',<br>- 'RestrictedArea', <br>- 'RegulatedFairway', <br>- 'DrinkingWaterProtectionArea', <br>- 'AirQualityManagementZone', <br>- 'NitrateVulnerableZone', <br>- 'SensitiveArea'. Propriedade extensível, o que significa que podem ser acrescentados tipos específicos de um domínio, como 'MunicipalSolidWasteZone' ou 'HazardousWasteZone' em caso de necessidade. Modelo: [https://schema.org/Text](https://schema.org/Text)   |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `validFrom`
- `dataProvider`
- `managementModel`
- `managedBy`
- `controlledActivityType`
- `environmentalDomain`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
