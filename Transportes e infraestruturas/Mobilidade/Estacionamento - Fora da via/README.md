# Descrição

Os modelos de dados para representar **Estacionamento** é o [OffStreetParking](https://github.com/smart-data-models/dataModel.Parking/tree/master/OffStreetParking) do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `OffStreetParking`|
| acceptedPaymentMethod | Array | Métodos de pagamento aceites | Enumerado: <br>- ByBankTransferInAdvance,<br>- ByInvoice,<br>- Cash,<br>- CheckInAdvance,<br>- COD,<br>- DirectDebit,<br>- GoogleCheckout,<br>- PayPal,<br>- PaySwarm. Modelo: [https://schema.org/acceptedPaymentMethod](https://schema.org/acceptedPaymentMethod) |
| accessModified | DateTime | Data e hora quando vehicleEntranceCount e vehicleExitCount foram atualizados | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| address | Object | Morada associada ao estacionamento | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address](https://schema.org/address) |
| aggregateRating | Object | Classificação agregada para este local de estacionamento | Modelo: [https://schema.org/aggregateRating](https://schema.org/aggregateRating) |
| allowedVehicleType | Array | Tipo(s) de veículo permitido | Enumerado:  <br>- agriculturalVehicle,<br>- anyVehicle,<br>- bicycle,<br>- bus,<br>- car,<br>- caravan,<br>- carWithCaravan,<br>- carWithTrailer,<br>- constructionOrMaintenanceVehicle,<br>- lorry,<br>- moped,<br>- motorcycle,<br>- motorcycleWithSideCar,<br>- motorscooter,<br>- tanker,<br>- trailer,<br>- van. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| availableSpotNumber | Number | Número de lugares disponíveis | Inclui todos os tipos de veículos ou espaços reservados. Deve ser um número inteiro positivo, incluindo 0. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageSpotLength | Number | Comprimento médio dos lugares de estacionamento | Modelo: [https://schema.org/length](https://schema.org/length) |
| averageSpotWidth | Number | Largura média dos lugares de estacionamento | Modelo: [https://schema.org/width](https://schema.org/width) |
| category | Array | Categoria(s) do local de estacionamento | Valores possíveis: 'underground', 'public', 'feeCharged', 'mediumTerm', 'barrierAccess'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| chargeType | Array | Tipo(s) de cobrança realizada pelo local de estacionamento | Enumerado: <br>-  additionalIntervalPrice,<br>- annualPayment,<br>- firstIntervalPrice,<br>- flat,<br>- free,<br>- minimum,<br>- maximum,<br>- monthlyPayment,<br>- other,<br>- seasonTicket,<br>- temporaryPrice. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| contactPoint | Object | Ponto de contacto do local de estacionamento | Modelo: [https://schema.org/contactPoint](https://schema.org/contactPoint) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| extCategory | Array | Categoria externa para complementar a categoria | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| extraSpotNumber | Number | Número de lugares extra disponíveis | Inclui lugares reservados para fins especiais e outros tipos de veículos. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| facilities | Array | Instalações disponíveis no local | Enumerado: <br>- bikeParking,<br>- cashMachine,<br>- copyMachineOrService,<br>- defibrillator,<br>- dumpingStation,<br>- electricChargingStation,<br>- elevator,<br>- faxMachineOrService,<br>- fireHose,<br>- fireExtinguisher,<br>- fireHydrant,<br>- firstAidEquipment,<br>- freshWater,<br>- iceFreeScaffold,<br>- informationPoint,<br>- internetWireless,<br>- luggageLocker,<br>- payDesk,<br>- paymentMachine,<br>- playground,<br>- publicPhone,<br>- refuseBin,<br>- safeDeposit,<br>- shower,<br>- toilet,<br>- tollTerminal,<br>- vendingMachine,<br>- wasteDisposal. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| firstAvailableFloor | Number | Número do piso mais próximo do solo com lugares disponíveis | Os pisos são numerados entre -n e n, sendo 0 o rés-do-chão. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| fourWheelerSlots | Object | Estado de disponibilidade dos lugares para veículos de quatro rodas | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| geometry | GeoJSON | Referência Geojson para o local de estacionamento | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| highestFloor | Number | Para locais com múltiplos pisos, o piso mais alto | Número inteiro. 0 é o rés-do-chão. Pisos superiores são números positivos. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| images | Array | URL contendo foto(s) deste local de estacionamento | Lista de URL. Modelo: [https://schema.org/image](https://schema.org/image) |
| layout | Array | Disposição do estacionamento | Enumerado: <br>-  automatedParkingGarage,<br>- carports,<br>- covered,<br>- field,<br>- garageBoxes,<br>- multiLevel,<br>- multiStorey,<br>- nested,<br>- openSpace,<br>- rooftop,<br>- sheds,<br>- singleLevel,<br>- surface,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| lowestFloor | Number | Para locais com múltiplos pisos, o piso mais baixo | Número inteiro. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| maximumAllowedHeight | Number | Altura máxima permitida para veículos | Se houver múltiplas zonas, será a altura mínima de todas as zonas. Modelo: [https://schema.org/height](https://schema.org/height) |
| maximumAllowedWidth | Number | Largura máxima permitida para veículos | Se houver múltiplas zonas, será a largura mínima de todas as zonas. Modelo: [https://schema.org/width](https://schema.org/width) |
| maximumParkingDuration | String | Duração máxima permitida de estadia no local | Codificada como duração ISO8601 ou qualquer outra string relevante para estacionamento. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| measuresPeriod | Number | Período de medidas relacionado com availableSpotNumber e priceRatePerMinute | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| measuresPeriodUnit | String | Unidade do período de medidas | Modelo: [https://schema.org/unitText](https://schema.org/unitText) |
| municipalityInfo | Object | Informação municipal correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| observationDateTime | DateTime | Última hora reportada de observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancy | Number | Valor relativo de lugares ocupados do total de lugares | Valores permitidos: 0 - 1. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| occupancyDetectionType | Array | Método(s) de deteção de ocupação | Enumerado: <br>- balancing,<br>- manual,<br>- modelBased,<br>- none,<br>- singleSpaceDetection. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancyModified | DateTime | Última vez que os valores de ocupação foram modificados | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| occupiedSpotNumber | Number | Número de lugares de estacionamento ocupados | Deve ser um número positivo inferior ou igual ao totalSpotNumber. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| openingHours | String | Horário de funcionamento do local de estacionamento | Modelo: [https://schema.org/openingHours](https://schema.org/openingHours) |
| outOfServiceSlotNumber | Number | Número de lugares fora de serviço | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| parkingMode | Array | Modo(s) de estacionamento | Enumerado: <br>- echelonParking,<br>- parallelParking,<br>- perpendicularParking. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| parkingSiteId | String | ID único do local ou lote de estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| priceCurrency | String | Moeda do preço da tarifa por minuto | Modelo: [https://schema.org/priceCurrency](https://schema.org/priceCurrency) |
| priceRatePerMinute | Number | Tarifa por minuto | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| provider | Object | Fornecedor de serviços do local de estacionamento | Modelo: [https://schema.org/provider](https://schema.org/provider) |
| refParkingAccess | URI | Ponto(s) de acesso do local de estacionamento | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| refParkingGroup | URI | Grupo(s) identificado(s) do local de estacionamento | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| refParkingSpot | URI | Lugares de estacionamento individuais pertencentes a este local | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| requiredPermit | Array | Licença(s) que podem ser necessárias para estacionar neste local | Enumerado: <br>- employeePermit,<br>- fairPermit,<br>- governmentPermit,<br>- noPermitNeeded,<br>- residentPermit,<br>- specificIdentifiedVehiclePermit,<br>- studentPermit,<br>- visitorPermit. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| reservationType | Array | Tipo de reserva | Enumerado:<br>- mandatory,<br>- notAvailable,<br>- optional,<br>- partly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| security | Array | Aspetos de segurança fornecidos por este local de estacionamento | Enumerado: <br>- areaSeparatedFromSurroundings,<br>- cctv,<br>- dog,<br>- externalSecurity,<br>- fences,<br>- floodLight,<br>- guard24hours,<br>- lighting,<br>- patrolled,<br>- securityStaff. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| specialLocation | Array | Se o local de estacionamento está numa localização especial | Enumerado: <br>- airportTerminal,<br>- cableCarStation,<br>- campground,<br>- cinema,<br>- coachStation,<br>- conventionCentre,<br>- exhibitionCentre,<br>- ferryTerminal,<br>- hotel,<br>- market,<br>- publicTransportStation,<br>- religiousCentre,<br>- shoppingCentre,<br>- skilift,<br>- specificFacility,<br>- themePark,<br>- trainStation,<br>- vehicleOnRailTerminal,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status | Array | Estado do local de estacionamento | Enumerado: <br>- almostFull,<br>- closed,<br>- closedAbnormal,<br>- full,<br>- fullAtEntrance,<br>- open,<br>- openingTimesInForce,<br>- spacesAvailable. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| totalSpotNumber | Number | Número total de lugares oferecidos por este local de estacionamento | Qualquer número inteiro positivo ou 0. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| twoWheelerSlots | Object | Estado de disponibilidade dos lugares para veículos de duas rodas | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| unclassifiedSlots | Object | Estado de disponibilidade dos lugares para veículos não classificados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| usageScenario | Array | Cenário(s) de utilização | Enumerado: <br>- automaticParkingGuidance,<br>- carSharing,<br>- dropOffWithValet,<br>- dropOffMechanical,<br>- dropOff,<br>- eventParking,<br>- kissAndRide,<br>- liftShare,<br>- loadingBay,<br>- overnightParking,<br>- parkAndCycle,<br>- parkAndRide,<br>- parkAndWalk,<br>- restArea,<br>- serviceArea,<br>- staffGuidesToSpace,<br>- truckParking,<br>- vehicleLift,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleEntranceCount | Number | Número agregado de veículos que entram no local de estacionamento num período de tempo | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| vehicleExitCount | Number | Número agregado de veículos que saem do local de estacionamento num período de tempo | Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
