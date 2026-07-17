# Descrição

Os modelos de dados a seguir para representar **Entidades e Organizações**
são os `Organization` e `Support` inspirados no [FIWARE Smart Data Models](https://github.com/smart-data-models/). Estes modelos utilizam o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://territoriosinteligentes.gov.pt).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `Organization`.

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | Valor único atribuído automaticamente |
| type | String | Tipo de entidade | Valor constante igual a `Organization`|
| address    | Object          | Morada associada | Inclui concelho, freguesia, rua, número e código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| address.addressLocality| String    | Freguesia da organização        | Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | Concelho da organização | Modelo: [https://schema.org/addressRegion](https://schema.org/addressRegion)       |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Nome da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)       |
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| alternateName | String | Nome alternativo da organização | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| areaIntervention | Array | A(s) área(s) de intervenção da organização | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| areaServed | Array | A(s) área(s) geográfica(s) onde um serviço ou item oferecido é fornecido | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| dataProvider       | String    | Identificador do fornecedor de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String   | Descrição textual |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| legalName | String | Nome legal (registo) da organização | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| location | GeoJSON |Localização a que reportam os valores |  Valores possíveis: 'Point',  'Polygon'.  |
| name | String | Nome da organização | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| owner | Array | Lista de identificadores únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| seeAlso | Array | Lista de URI que apontam para recursos adicionais sobre a organização | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| source | String | Fonte original dos dados da entidade | Recomenda-se que seja o nome de domínio totalmente qualificado do fornecedor da fonte ou o URL do objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)   |
| url | String | URL que fornece uma descrição ou mais informações sobre este item | Modelo: [https://schema.org/URL](https://schema.org/URL)   |

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `Support`.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Valor único atribuído automaticamente |
| type | String | Tipo de entidade | Valor constante igual a `Support`    |
| contributionStartDate        | Date | Registo de data em que o apoio foi autorizado/efectuado |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| contributionEndDate        | Date | Registo de data em que o apoio foi finalizdo |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Se o apoio esstiver a decorrer, este atributo deve ser omitido dos dados. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dataProvider       | String    | Identificador do fornecedor de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String   | Descrição textual |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| financialSupport   | Number   | Apoio financeiro | Normalmente expresso em Euros.  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| logisticalSupport | Array | Apoio logistício fornecido | Lista de descritores do apoio oferecido, e.g., sala, cobertura media.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| personnelSupport | Number | Apoio em recursos humanos | Número de pessoas disponibilizadas para suportar a entidade. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome da organização que presta o apoio | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | Array | Lista de URI que apontam para recursos adicionais sobre a entidade | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source | String | Fonte original dos dados da entidade como um URL. | Recomenda-se que seja o nome de domínio totalmente qualificado do fornecedor da fonte ou o URL do objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| url | String | URL que fornece uma descrição ou mais informações sobre este item. | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| refSupportedOrganization | URI | Referência para a organização apoiada | Normalmente um URN. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios para o modelo `Organization` são:

- `id`
- `type`
- `name`
- `areaIntervention`
- `areaServed`
- `location`

Os atributos obrigatórios para o modelo `Support` são:

- `id`
- `type`
- `contributionStartDate`  
- `financialSupport`(*)
- `logisticalSupport`(*)
- `personnelSupport` (*)
- `refSupportedOrganization`

(*) Pelo menos um destes apoios tem de ser incluído no modelo de dados. Não existindo um, esse atributo deve ser omitido.

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
