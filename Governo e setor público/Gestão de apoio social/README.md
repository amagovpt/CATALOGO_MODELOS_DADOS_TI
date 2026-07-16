# Descrição

O modelo de dados a seguir para representar **Gestão de ação social** é o `SocialSupportObservation` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
| -------------------- | ------------------- | -------------------------------------------------------------------------- | ----------------------------------------------------- |
| id | URI | Identificador único da observação | -- |
| type | String | Tipo da entidade | Valor fixo: SocialSupportObservation |
| location | GeoJSON | Referência Geojson para o objeto | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| publicService | String | Designação do serviço público ou programa de apoio social ao qual a observação se refere | -- |
| observedBy | URI | Referência para a organização responsável pela recolha ou reporte dos dados | -- |
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| areaServed | String | Área geográfica a que os dados dizem respeito | -- |
| aggregationLevel | String | Nível de agregação dos dados | Ex.: facility, parish, municipality |
| facilityRef | URI | Referência para o equipamento social a que a observação se refere | -- |
| supportType| String | Tipo de apoio | Enumerado: <br>-financial, <br>-goods, <br>-facility, <br>-mixed, <br>-other. |
| financialPurpose| String | Objetivo do apoio financeiro | Enumerado: <br>-housingRent, <br>-institutionAttendance, <br>-medicalTravel, <br>-educationTravel, <br>-pedagogicMaterials, <br>-emergencyFinancialAid, <br>-foodAssistance, <br>-frequencyInstitutions, <br>-other.
| facilityType | String | Tipo de equipamento social | Ex.: Escola 1º ciclo, creche, centro de dia |
| indicator | String | Indicador observado | Ex.: studentsCount, mealsDailyCount, usersCount |
| value | Number | Valor numérico do indicador | Sempre agregado |
| validFrom | DateTime | Início do período de referência dos dados | De acordo com a norma  [ISO 8601-1:2019] |
| validTo | DateTime | Fim do período de referência dos dados | De acordo com a norma  [ISO 8601-1:2019] |
| description | String | Descrição adicional da observação | -- |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `location`
- `validFrom`
- `validTo`
- `aggregationLevel`
- `indicator`
- `value`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
