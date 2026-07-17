# Descrição

O modelo de dados a seguir para representar **Mercados e Feiras**
é o `Market` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Market`|
| accessibility        | Array       | Recursos de acessibilidade disponíveis        |  Valores possíveis: 'wheelchairAccessible', 'audioDescription', 'signLanguageInterpreter'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| buildingId    | String     | O identificador único do imóvel onde a feira ou mercado tem lugar | Pode ser um URN ou um identificador geográfico.  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| category    | String         | Categoria do mercado   | Enumerado: <br>- market; <br>- fair. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint           | Object    | Detalhes de contacto do item          | Modelo: [https://schema.org/ContactPoint](https://schema.org/ContactPoint)        |
| contactPoint.areaServed| String    | Área geográfica de cobertura do contacto            |    Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.availabilityRestriction | *         | Informação sobre quando o ponto de contacto não está disponível   | Os pormenores são fornecidos utilizando a classe Especificação do Horário de Abertura. Modelo: [http://schema.org/hoursAvailable](http://schema.org/hoursAvailable)       |
| contactPoint.availableLanguage       | String         | Língua utilizável com o serviço ou local            | Modelo: [http://schema.org/availableLanguage](http://schema.org/availableLanguage)    |
| contactPoint.contactOption           | Array        | Opção disponível neste ponto de contacto     | Modelo: [http://schema.org/contactOption](http://schema.org/contactOption)        |
| contactPoint.contactType             | String    | Tipo de contacto deste item           |   Uma pessoa ou organização pode ter diferentes pontos de contacto, para diferentes fins. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| contactPoint.email     | idn-email | Endereço de email do proprietário     |  Modelo: [https://schema.org/Text](https://schema.org/Text)     |
| contactPoint.faxNumber | String    | Número de fax do item   | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.name      | String    | Nome do ponto de contacto             |   Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| contactPoint.productSupported        | String    | Produto ou serviço suportado por este ponto de contacto           | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.telephone | String    | Telefone de contacto    |    Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.url       | URI       | URL com descrição ou mais informação sobre o item   |    Modelo: [https://schema.org/URL](https://schema.org/URL)  |
| capacity | Number    | Número total de bancas que podem ser alocadas ao mercado     |    Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateFinished        | DateTime | Registo de data e hora da conclusão da intervenção |  Este será normalmente atribuído pela plataforma de armazenamento. É omitido quando a intervenção está a decorrer. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateStarted        | DateTime | Registo de data e hora de início da intervenção |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String  | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o objeto |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | O nome da intervenção |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| managementEntity    | Array     | Lista codificada com os identificadores únicos do(s) proprietário(s) ou o seu nome descritivo|  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| occupancy | Number | Número máximo de pessoas no espaço |  Modelo: [https://schema.org/Number](https://schema.org/Number) 
| openingHours    | Object     | Horário de funcionamento do mercado| O formato base é dado por "DayOfWeek-DayOfWeek HH:MM-HH:MM", onde DayOfWeek representa as duas primeiras letras em inglês dos dias da semana: <br>- Mo (Monday); <br>- Tu (Tuesday); <br>- We (Wednesday); <br>- Th (Thursday); <br>- Fr (Friday); <br>- Sa (Saturday); <br>- Su (Sunday). Para periodos múltiplos, pode usar-se o formato "DayOfWeek-DayOfWeek HH:MM-HH:MM,HH:MM-HH:MM".  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| promotingEntity    | Array     | Lista codificada com os identificadores únicos do(s) promotores(s) ou o seu nome descritivo|   Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| status               | String         | Estado atual do mercado   | Valores possíveis: 'active', 'inactive', 'suspended'.  Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| supportingFacilities        | Array       | Lista codificada com os identificadores únicos do(s) equipamentos de suporte existentes ou o seu nome descritivo        |  Exemplo: WC, Multibanco. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `category`
- `name`
- `description`
- `address`
- `location`
 
## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
