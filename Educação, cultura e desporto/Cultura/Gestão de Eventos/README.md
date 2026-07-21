# Descrição

O modelo de dados a seguir para representar **Gestão de eventos**
é o `EventObserved` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `EventObserved`    |
| address    | Object          | Morada associada ao evento | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| averageOccupancy | Integer | O valor médio de pessoas em simultâneo no evento.|  O valor diz respeito apenas ao período de observação e deve incluir apenas visitantes do evento. Modelo: [https://schema.org/Integer](https://schema.org/Integer). Deve ser indicado, como metainformação, no atributo `calculationMethod` qual o método usado para o cálculo do valor, usando um valor do enumerado:<br>- ticket,<br>- sensor, <br>- estimated, <br>- unknown.  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateFinished        | DateTime | Registo de data e hora da recolha de dados reportados |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateStarted        | DateTime | Registo de data e hora da recolha de dados reportados |   De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON |Localização a que reportam os valores |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| promoter | Array | Listas dos promotores do evento | Caso o evento tenha múltiplos promotores, devem ser reportados aqueles que são válidos no período de observação e deve incluir todas as pessoas, incluindo forças de segurança se for o caso.  Os valores podem aparecer como textual ou URI. |
| peopleInvolved | Integer | Número de pessoas envolvidas no apoio ao evento |  O valor diz respeito apenas ao período de observação e deve incluir todas as pessoas envolvidas na realização do evento, não visitantes, incluindo forças de segurança (se for o caso).  Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| maximumOccupancy | Integer | O valor médio de pessoas em simultâneo no evento.|  O valor diz respeito apenas ao período de observação e deve incluir apenas visitantes do evento. Modelo: [https://schema.org/Integer](https://schema.org/Integer). Deve ser indicado, como metainformação, no atributo `calculationMethod` qual o método usado para o cálculo do valor, usando um valor do enumerado:<br>- ticket,<br>- sensor, <br>- estimated, <br>- unknown.  |
| minimumOccupancy | Integer | O valor mínimo de pessoas em simultâneo no evento.|  O valor diz respeito apenas ao período de observação e deve incluir apenas visitantes do evento. Modelo: [https://schema.org/Integer](https://schema.org/Integer). Deve ser indicado, como metainformação, no atributo `calculationMethod` qual o método usado para o cálculo do valor, usando um valor do enumerado:<br>- ticket,<br>- sensor, <br>- estimated, <br>- unknown.  |
| refEvent      | Array       | Referência para o evento a que os dados dizem respeito | Identificador do evento do (cujo tipo é `Event`), descrito no catálogo nacional de dados. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refRestrictions      | Array       | Referência para as restrições de tráfego necessárias para a realização do evento | As restrições são aquelas que estão ativas durante o período de observação. Identificadores de objetos do tipo `RestrictedTrafficArea`, descrito no catálogo nacional de dados. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refAffectedPlaces      | Array       | Referência para os locais afetados pela realização do evento. | Assume-se pelo menos o local onde o evento se realiza. Identificadores de objetos do tipo `RestrictedTrafficArea`Identificadores de objetos do tipo `PointOfInterest`. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refUsedMeans      | Array       | Referência para os meios usados para a realização do evento. | Deve incluir-se veículos de apoio utilizados ou em prontidão durante o período de observação. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `location`
- `promoter`
- `dateStarted`
- `dateFinished`
- `refEvent`
- `address`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.