# Descrição

Os modelos de dados para representar **Estacionamento** é o [OnStreetParking](https://github.com/smart-data-models/dataModel.Parking/tree/master/OnStreetParking) do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de indentificadores únicos](https://metadados.digital.gov.pt/#/catalogue/folder/b8474afb-2c16-477c-a980-f7ce6989e48d/description?edit=false). |
| type | String | Tipo de entidade | Valor constante igual a `OnStreetParking`|
| address | Object | Morada associada ao estacionamento | Inclui país, localidade, rua. Modelo: [https://schema.org/address](https://schema.org/address) |
| allowedVehicleType | Array | Tipo(s) de veículo permitido | Enumerado: <br>- agriculturalVehicle,<br>- anyVehicle,<br>- articulatedVehicle,<br>- bicycle,<br>- bus,<br>- car,<br>- caravan,<br>- carOrLightVehicle,<br>- carWithCaravan,<br>- carWithTrailer,<br>- constructionOrMaintenanceVehicle,<br>- fourWheelDrive,<br>- highSidedVehicle,<br>- lorry,<br>- moped,<br>- motorcycle,<br>- motorcycleWithSideCar,<br>- motorscooter,<br>- tanker,<br>- threeWheeledVehicle,<br>- trailer,<br>- tram,<br>- twoWheeledVehicle,<br>- van,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areBordersMarked | Boolean | Indica se os lugares de estacionamento estão delimitados ou não | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| availableSpotNumber | Number | Número de lugares disponíveis globalmente | Inclui espaços reservados. Deve ser um número inteiro positivo, incluindo 0. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageSpotLength | Number | Comprimento médio dos lugares de estacionamento | Modelo: [https://schema.org/length](https://schema.org/length) |
| averageSpotWidth | Number | Largura média dos lugares de estacionamento | Modelo: [https://schema.org/width](https://schema.org/width) |
| category | Array | Categoria de estacionamento na rua | Enumerado: <br>- blueZone,<br>- feeCharged,<br>- forDisabled,<br>- forElectricalCharging,<br>- forLoadUnload,<br>- forResidents,<br>- free,<br>- greenZone,<br>- mediumTerm,<br>- onlyWithPermit,<br>- shortTerm,<br>- taxiStop. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| chargeType | Array | Tipo(s) de cobrança realizada pelo local de estacionamento | Enumerado: <br>- additionalIntervalPrice,<br>- annualPayment,<br>- firstIntervalPrice,<br>- flat,<br>- free,<br>- minimum,<br>- maximum,<br>- monthlyPayment,<br>- seasonTicket,<br>- temporaryFee,<br>- temporaryPrice,<br>- unknown,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| extraSpotNumber | Number | Número de lugares extra disponíveis | Lugares reservados para fins especiais que normalmente requerem uma licença. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| fourWheelerSlots | Object | Estado de disponibilidade dos lugares para veículos de quatro rodas | Contém availableSpotNumber, occupiedSpotNumber e totalSpotNumber. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| layout | Array | Classificação genérica da disposição do estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| maximumParkingDuration | String | Duração máxima permitida de estadia no local | Codificada como duração ISO8601. Um valor vazio indica duração indefinida. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| modifiedAt | DateTime | Data e hora da última modificação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| municipalityInfo | Object | Informação municipal correspondente a esta observação | Inclui identificação da localidade, nome, e outros. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| observationDateTime | DateTime | Última hora reportada de observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancyDetectionType | Array | Método(s) de deteção de ocupação | Enumerado: <br>- balancing,<br>- manual,<br>- modelBased,<br>- none,<br>- singleSpaceDetection. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancyModified | DateTime | Data da última vez que a ocupação do estacionamento foi modificada | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| occupiedSpotNumber | Number | Número total de lugares de estacionamento ocupados | Deve ser um número positivo inferior ou igual ao totalSpotNumber. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| outOfServiceSlotNumber | Number | Número de lugares fora de serviço | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| parkingMode | String | Modo(s) de estacionamento | Enumerado: <br>- echelonParking,<br>- parallelParking,<br>- perpendicularParking. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| parkingSiteId | String | ID único do local de estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| permitActiveHours | Object | Captura situações quando uma licença é necessária apenas em horas ou dias específicos | Valor estruturado com uma subpropriedade por cada licença necessária. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refParkingGroup | Array | Referência ao(s) grupo(s) de estacionamento pertencentes a esta zona | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refParkingSpot | Array | Lugares de estacionamento individuais pertencentes a este local | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| requiredPermit | Array | Licença(s) que podem ser necessárias para estacionar neste local | A semântica é que pelo menos uma destas licenças é necessária para estacionar. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| totalSpotNumber | Number | Número total de lugares oferecidos por este local de estacionamento | Pode ser difícil de obter para locais onde os lugares não estão claramente marcados. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| twoWheelerSlots | Object | Estado de disponibilidade dos lugares para veículos de duas rodas | Contém availableSpotNumber, occupiedSpotNumber e totalSpotNumber. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| unclassifiedSlots | Object | Estado de disponibilidade dos lugares para veículos não classificados | Contém availableSpotNumber, occupiedSpotNumber e totalSpotNumber. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| usageScenario | String | Cenário de utilização do estacionamento | Enumerado: <br>- carSharing,<br>- dropOff,<br>- kissAndRide,<br>- liftShare,<br>- loadingBay,<br>- overnightParking,<br>- parkAndRide,<br>- parkAndCycle,<br>- parkAndWalk,<br>- vehicleLift. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
