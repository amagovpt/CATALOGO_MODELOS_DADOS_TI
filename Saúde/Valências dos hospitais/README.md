# Descrição

O modelo de dados a seguir para representar **Valências dos hospitais** 
é o `EmergencyService` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id  | URI    | Identificador único da unidade hospitalar       | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| type | String  | Tipo de entidade  | Valor constante igual a `EmergencyService`  |
| name | String  | Nome da unidade hospitalar |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| address    | Object          | Morada associada à unidade hospitalar | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| accessByCSPInitiative | Boolean | Especifica se é permitido acesso por iniciativa de um médico do Centro de Saúde e Proteção (CSP)       | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| accessByPatientInitiative  | Boolean | Especifica se é permitido o acesso por iniciativa do próprio paciente  | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| accessViaHealth24     | Boolean | Especifica se é permitido acesso via linha Saúde 24       | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| accessByHospitalDoctors   | Boolean | Especifica se é permitido acesso por iniciativa de médicos hospitalares    | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| accessByUrgentCareDoctors       | Boolean | Especifica se é permitido acesso por iniciativa de médicos de urgência    | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| ageRange    | String  | Faixa etária dos pacientes atendidos | Enumerado: <br>- 0 aos 0 anos,<br>- 0 aos 150 anos,<br>- 0 aos 17 anos,<br>- 1 aos 150 anos,<br>- 18 aos 150 anos.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ambulanceServiceAvailability    | Boolean | Especifica se é disponibilidade de serviços de ambulância   | Valor: true ou false.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| administrativeArea    | String  | Área administrativa onde a unidade está localizada     | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| facilityCapacity      | Array  | Capacidade operacional da unidade |  Inclui o número de leitos e profissionais.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint| Array  | Dados de contato da unidade hospitalar  |   Contém o número de telefone e e-mail. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| hospitalGroup         | String  | Grupo hospitalar ao qual pertence a unidade  | Enumerado: <br>- Grupo B,<br>- Grupo C,<br>- Grupo D,<br>- Grupo E,<br>- Grupo F. Consultar [Grupos e Instituições do SNS](https://benchmarking-acss.min-saude.pt/BH_Enquadramento/GrupoInstituicoes).  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| emergencyServiceType  | String  | Tipo de serviço de urgência| Enumerado: <br>- Serviço de Urgência Básica, <br>- Serviço de Urgência Médico-Cirúrgico, <br>- Serviço de Urgência Polivalente, <br>- Serviço de Urgência Polivalente com Centro de Trauma. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| legalNature | String  | Natureza jurídica da entidade       | Enumerado: <br>- EPE,<br>- IP,<br>- IPSS, <br>- PPP,<br>- ULS-EPE.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| operationalHours      | String  | Horário de funcionamento da unidade hospitalar         | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| region      | String  | Região administrativa de saúde a que a unidade pertence| Enumerado: <br>- ARS Norte,<br>- ARS Lisboa e Vale do Tejo,<br>- ARS Centro,<br>- ARS Alentejo,<br>- SRS Açores, <br>- ARS Algarve,<br>- IASAÚDE Madeira.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| speciality   | String  | Especialidade atendida pela unidade  | Modelo: [https://schema.org/Text](https://schema.org/Text) |



## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `dateModified`
- `location`
- `name`
- `operationalHours`
- `emergencyServiceType`
- `speciality`
- `address`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. 

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.