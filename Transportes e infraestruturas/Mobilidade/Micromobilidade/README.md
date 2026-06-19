# Descrição

O modelo de dados para representar **Micromobilidade**
é o [ItemFlowObserved](https://github.com/smart-data-models/dataModel.Transportation/tree/083e3bf77d2fffca4bfadee6ba895f4efb8a5c9e/ItemFlowObserved) do [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, illustrando o seu uso no âmbito da [ENTI](https://territoriosinteligentes.gov.pt).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `ItemFlowObserved` |
| address | Object | Morada associada à estação de carregamento | Inclui país, localidade, rua. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| averageGapDistance | Number | Distância média entre dois itens consecutivos detetados | Superior a zero. Normalmente expressa em metros. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageHeadwayTime | Number | Tempo médio de intervalo | O tempo de intervalo é o tempo decorrido entre dois itens consecutivos. Superior a zero. Normalmente expressa em segundos. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageLength | Number | Comprimento médio dos itens detetados, durante o período de observação. | Superior a zero. Normalmente expressa em metros. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageSpeed | Number | Velocidade média dos itens detetados em trânsito durante o período de observação. | Superior a zero. A unidade depende do tipo de item detectado. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| congested | Boolean | Indica se houve congestionamento durante o período de observação na passagem em observação. | A ausência deste atributo deve ser interpretado como o valor falso (não há congestionamento). Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObserved | DateTime | Data da observação definida pelo utilizador | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObservedFrom | DateTime | Registo de data e hora do início da observação | Limite inferior, inclusive, do intervalo de observação. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObservedTo | DateTime | Registo de data e hora do fim da observação | Limite superior, inclusive, do intervalo de observação. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da entidade | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| intensity | Number | Número total de itens detetados durante o período de observação | Igual ou superior a zero. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| itemSubType | String | Referência para um identificador de um atributo `subType` de uma entidade NGSI existente | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| itemType | String | Referência para um identificador de um tipo NGSO-LD existente (ou futuro) | Por exemplo <br>- Bicycle, <br>- Person, <br>- Scooter. Os valores são referentes a micromobilidade, podendo ser alargados para outros domínios. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| laneDirection | String | Direção habitual de circulação na faixa referida por esta observação. | Este atributo é útil quando a observação não faz referência a nenhum segmento rodoviário, permitindo conhecer a direção de circulação do fluxo observado. Consulte o tipo `RoadSegment` para obter uma descrição da semântica destes valores. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| laneId | Number | Número da pista | A identificação das faixas é feita utilizando as convenções definidas pela entidade `RoadSegment`, que se baseiam no [OpenStreetMap](http://wiki.openstreetmap.org/wiki/Forward_%26_backward,_left_%26_right). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Referência Geojson para a entidade | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome da entidade | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancy | Number | Fração do tempo de observação em que um item ocupou a faixa observada | Modelo: [https://schema.org/Number] |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refDevice | URI | Referência ao dispositivo que realizou a medição | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| refRoadSegment | URI | Segmento de estrada em questão sobre o qual a observação foi feita | Referência a uma entidade. Por exemplo, uma referência para `CycleLane`. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| reversedLane | Boolean | Indica se o tráfego na faixa foi invertido durante o período de observação. | A ausência deste atributo indica que não houve inversão da faixa. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| speedMax | Number | Velocidade máxima detetada durante o período de observação | Igual ou superior a zero. Normalmente expressa em Kilometer per hour (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| speedMin | Number | Velocidade mínima detetada durante o período de observação | Igual ou superior a zero. Normalmente expressa em Kilometer per hour (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `dateObserved`
- `laneId` (*)
- `location`
- `refRoadSegment`

(*) obrigatório se não for relativo a uma pista ciclável.

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nestes modelos, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
