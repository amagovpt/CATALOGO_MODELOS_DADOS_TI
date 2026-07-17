# Descrição

O modelo de dados a seguir para representar **Caraterização de luminárias**
é o grupo [Streetlighting](https://github.com/smart-data-models/dataModel.Streetlighting), em particular o [Streetlight](https://github.com/smart-data-models/dataModel.Streetlighting/blob/master/Streetlight/README.md) inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Streetlight`|
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| circuit   | String    | Circuito ao qual o candeeiro de rua se liga e do qual obtém energia | Normalmente, contém um identificador que permite obter mais informações sobre esse circuito. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| controllingMethod | String    | Método utilizado para controlar este candeeiro de iluminação pública | Enumerado: <br>- group, <br>- individual. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| current   | Number | Valor atual do candeeiro de iluminação pública correspondente a esta observação | Normalmente expressa em miliamperes (4K). Modelo: [https://schema.org/Number](https://schema.org/Number)
| dateLastLampChange  | DateTime    | Registo da hora da última mudança de lâmpada efectuada | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| feederID  | String | Identificador único do painel de alimentação do candeeiro de iluminação pública | Associado ao candeeiro de iluminação pública correspondente a esta observação. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| illuminanceLevel | Number | Definição do nível de iluminação relativa | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| lanternHeight | Number | Altura da lanterna | Em colunas com muitos braços, isto pode variar entre os candeeiros de rua. Outra fonte de variação desta propriedade são os candeeiros de parede. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Referência Geojson para o objeto |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| locationCategory | String | Categoria do local onde o candeeiro de iluminação pública é colocado | Enumerado: <br>- bridge, <br>- centralIsland, <br>- facade, <br>- garden, <br>- park, <br>- parking, <br>- pedestrianPath, <br>- playground, <br>- road, <br>- sidewalk, <br>- tunnel. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo  | Object | Informação municipal correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| observationDateTime   | DateTime  | Última hora de observação registada | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| powerFactor | Number | Fator de potência | I.e., rácio da potência de funcionamento do candeeiro de iluminação pública correspondente a esta observação. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| powerState    | String |  Estado de energia do candeeiro de iluminação pública | Enumerado: <br>- bootingUp, <br>- low, <br>- off, <br>- on. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refStreetlightGroup | URI   | Grupo do candeeiro de iluminação pública | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refStreetlightModel   | URI   | Modelo de iluminação pública | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| status    | String    | Estado geral deste candeeiro de iluminação pública | Enumerado: <br>- brokenLantern, <br>- columnIssue, <br>- defectiveLamp, <br>- ok. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| streetPoleNum | String    | Informação sobre o poste de rua associado ao candeeiro de rua correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| voltage | Number  |  Valor da tensão do candeeiro de iluminação pública correspondente a esta observação | Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `status`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.