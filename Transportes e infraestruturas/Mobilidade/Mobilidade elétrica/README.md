# Descrição

O modelo de dados para representar **Mobilidade Elétrica**
é o [EVChargingStation](https://github.com/smart-data-models/dataModel.Transportation/tree/master/EVChargingStation) do [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, illustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `EVChargingStation`|
| acceptedPaymentMethod | Array | Tipo(s) de cobrança ao usar esta estação | Enumerado: <br>- ByBankTransferInAdvance,<br>- ByInvoice,<br>- Cash,<br>- CheckInAdvance,<br>- COD,<br>- DirectDebit,<br>- GoogleCheckout,<br>- PayPal,<br>- PaySwarm. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| address | Object | Morada associada à estação de carregamento | Inclui país, localidade, rua. Modelo: [https://schema.org/address](https://schema.org/address) |
| allowedVehicleType | Array | Tipo(s) de veículo que podem ser carregados | Enumerado: <br>- bicycle,<br>- bus,<br>- car,<br>- caravan,<br>- motorcycle,<br>- motorscooter,<br>- truck. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| amountCollected | Number | Valor cobrado pelo serviço correspondente a esta observação | Normalmente expressa em euros (EUR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| amperage | Number | Amperagem total oferecida pela estação de carregamento | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| availableCapacity | Number | Número de veículos que podem ser carregados atualmente | Deve ser inferior ou igual à `capacity`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| capacity | Number | Número total de veículos que podem ser carregados simultaneamente | O número total de tomadas pode ser superior. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| chargeType | Array | Tipo(s) de cobrança ao usar esta estação | Enumerado: <br>- annualPayment,<br>- flat,<br>- free,<br>- monthlyPayment,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| chargingUnitId | String | Identificador do ponto de carregamento na estação de VE | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint | Object | Detalhes para contactar com o item | Inclui email, telefone, disponibilidade. Modelo: [https://schema.org/ContactPoint](https://schema.org/ContactPoint) |
| dataDescriptor | URI | URI apontando para a entidade data-descriptor | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da estação de carregamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endDateTime | DateTime | Hora de fim reportada correspondente a esta observação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome da estação de carregamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| network | String | Nome da rede com a qual o operador coopera | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| observationDateTime | DateTime | Última hora reportada de observação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| openingHours | String | Horários de funcionamento da estação de carregamento | Modelo: [https://schema.org/openingHours](https://schema.org/openingHours) |
| operator | String | Operador da estação de carregamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| powerConsumption | Number | Potência consumida pela entidade correspondente a esta observação | Normalmente expressa em quilowatts (KWT). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| socketNumber | Number | Número total de tomadas oferecidas por esta estação de carregamento | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| socketType | Array | Tipo de tomadas oferecidas por esta estação | Enumerado: <br>-Caravan_Mains_Socket,<br>- CHAdeMO,<br>- CCS/SAE,<br>- Dual_CHAdeMO,<br>- Dual_J-1772,<br>- Dual_Mennekes,<br>- J-1772,<br>- Mennekes,<br>- Other,<br>- Tesla,<br>- Type2,<br>- Type3,<br>- Wall_Euro. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| startDateTime | DateTime | Hora de início reportada correspondente a esta observação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| stationName | String | Nome da estação correspondente a esta observação | Pode ser o nome da estação de bicicletas, estação de carregamento, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status | String | Estado da estação de carregamento | Enumerado: <br>- almostEmpty,<br>- almostFull,<br>- empty,<br>- full,<br>- outOfService,<br>- withIncidence,<br>- working. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| taxAmountCollected | Number | Valor do imposto cobrado sobre produtos e serviços | Inclui IVA, taxas de serviço, direitos aduaneiros, etc. Normalmente expressa em euros (EUR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| transactionId | String | Identificador único da transação da entidade correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| transactionType | String | Tipo de transação baseado no modo de pagamento ou modo de serviço | Por exemplo: mobile/UPI, cartão, RFID, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleType | String | Tipo de veículo do ponto de vista das suas características estruturais | Diferente da categoria do veículo. Enumerado extensivo incluindo 'car', 'bus', 'motorcycle', 'bicycle', etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| voltage | Number | Voltagem total oferecida pela estação de carregamento | Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `allowedVehicleType`
- `capacity`
- `socketType`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nestes modelos, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
