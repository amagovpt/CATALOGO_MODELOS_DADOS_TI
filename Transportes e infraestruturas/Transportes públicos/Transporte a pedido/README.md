# Descrição

O modelos de dado para representar **Transporte a pedido** é o `TransportOnDemand` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/), baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados. TODO

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `TransportOnDemand`|
| createdAt | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description | String | Descrição textual da viagem de um utente | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| destination | String | O destino do serviço | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| destinationLocation | GeoJSON | O ponto final da viagem | É usado o tipo geométrico `Point`. |
| destinationMunicipalityID | Integer | Identificador da município de destino | Os IDs de transação não se destinam a ser usados diretamente na lógica da aplicação, mas são úteis para depuração e monitorização. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| destinationMunicipality | String | O município de destino do serviço | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endDate | DateTime | Data e hora do fim da viagem | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| license | URI | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL) |
| modifiedAt | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| pricePayed | Number | O valor pago pelo bilhete. | O valor tem duas casas decimais e não pode ser 0. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Rota do serviço a pedido | Normalmente é usado o tipo geométrico `LineString`. Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| seeAlso | Array | Descrições adicionais | Lista de URLs para recursos externos. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| serviceType | String | O tipo do serviço prestado | Enumerado: <br>- Municipal,<br>- Intermunicipal,<br>- Outro. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source | String | A origem do serviço | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| sourceLocation | GeoJSON | O ponto inicial da viagem | É usado o tipo geométrico `Point`. |
| sourceMunicipalityID | Integer | Identificador da município de origem | Os IDs de transação não se destinam a ser usados diretamente na lógica da aplicação, mas são úteis para depuração e monitorização. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| sourceMunicipality | String | O município origem do serviço | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| startDate | DateTime | Data e hora do início da viagem | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| standardPrice | Number | O valor de tabela do bilhete. | O valor tem duas casas decimais e não pode ser 0. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| status | String | Estado de viagem | Enumerado: <br>- realizado,<br>- desistiu/cancelou,<br>- outro. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ticketType | String | Tipo de bilhete cobrado |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| transactionid | Integer | Identificador da transacção | Os IDs de transação não se destinam a ser usados diretamente na lógica da aplicação, mas são úteis para depuração e monitorização.Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| version | String | Versão do modelo dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `ìd`
- `type`
- `sourceLocation`
- `destinationLocation`
- `pricePayed`
- `standardPrice`
- `startDate`
- `status`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.