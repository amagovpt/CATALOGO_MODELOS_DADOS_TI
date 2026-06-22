# Descrição

Os modelos de dados para representar **Estacionamento** é o [ParkingGroup](https://github.com/smart-data-models/dataModel.Parking/tree/master/ParkingGroup) do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de indentificadores únicos](https://metadados.digital.gov.pt/#/catalogue/folder/b8474afb-2c16-477c-a980-f7ce6989e48d/description?edit=false). |
| type | String | Tipo de entidade | Valor constante igual a `ParkingGroup`|
| address | Object | Morada associada ao grupo de estacionamento | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address](https://schema.org/address) |
| allowedVehicleType | String | Tipo de veículo permitido | Um grupo de estacionamento permite apenas um tipo de veículo. Enumerado: <br>- bicycle,<br>- bus,<br>- car,<br>- caravan,<br>- motorcycle,<br>- motorscooter,<br>- truck. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areBordersMarked | Boolean | Indica se os lugares de estacionamento estão delimitados ou não | Valor: true ou false. As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| availableSpotNumber | Number | Número de lugares disponíveis neste grupo | Deve ser inferior ou igual ao totalSpotNumber. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| averageSpotLength | Number | Comprimento médio dos lugares de estacionamento | As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Modelo: [https://schema.org/length](https://schema.org/length) |
| averageSpotWidth | Number | Largura média dos lugares de estacionamento | As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Modelo: [https://schema.org/width](https://schema.org/width) |
| category | Array | Categoria do grupo de estacionamento | Enumerado: <br>- adjacentSpaces,<br>- blueZone,<br>- completeFloor,<br>- free,<br>- feeCharged,<br>- greenZone,<br>- loadUnloadZone,<br>- nonAdjacentSpaces,<br>- offStreet,<br>- onlyDisabled,<br>- onlyElectricalCharging,<br>- onlyResidents,<br>- onlyWithPermit,<br>- onStreet,<br>- particularConditionsSpaces,<br>- shortTermMediumTermLongTerm,<br>- statisticsOnly,<br>- vehicleTypeSpaces. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| chargeType | Array | Tipo(s) de cobrança realizada pelo local de estacionamento | Enumerado: <br>- additionalIntervalPrice,<br>- annualPayment,<br>- firstIntervalPrice,<br>- flat,<br>- free,<br>- minimum,<br>- maximum,<br>- monthlyPayment,<br>- seasonTicket,<br>- temporaryFee,<br>- temporaryPrice,<br>- unknown,<br>- other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do grupo de estacionamento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. |
| maximumAllowedHeight | Number | Altura máxima permitida para veículos | As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Modelo: [https://schema.org/height](https://schema.org/height) |
| maximumAllowedWidth | Number | Largura máxima permitida para veículos | As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Modelo: [https://schema.org/width](https://schema.org/width) |
| maximumParkingDuration | String | Duração máxima permitida de estadia | Codificada como duração ISO8601. Quando não presente ou igual a string vazia significa indefinida. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupancyDetectionType | Array | Método(s) de deteção de ocupação | Enumerado: <br>- balancing,<br>- manual,<br>- modelBased,<br>- none,<br>- singleSpaceDetection. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| parkingMode | Array | Modo(s) de estacionamento | As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Enumerado: <br>- echelonParking,<br>- parallelParking,<br>- perpendicularParking. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| permitActiveHours | Object | Captura situações quando uma licença é necessária apenas em horas ou dias específicos | Valor estruturado com uma subpropriedade por cada licença necessária, indicando quando a licença está ativa. A sintaxe deve estar em conformidade com a especificação de horários de abertura do schema.org. Modelo: [https://schema.org/openingHours](https://schema.org/openingHours) |
| refParkingSite | URI | Local de estacionamento ao qual esta zona pertence | Um grupo não pode ser órfão. Um grupo não pode ter subgrupos. Referência a um OffStreetParking ou OnStreetParking. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refParkingSpot | Array | Lugares de estacionamento individuais pertencentes a este grupo | Referência URN a uma entidade. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| requiredPermit | Array | Licença(s) que podem ser necessárias para estacionar neste local | A semântica é que pelo menos uma destas licenças é necessária para estacionar. Quando uma licença é composta por mais de um item podem ser combinadas com ','. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| reservationType | String | Condições para reserva | As aplicações devem verificar o valor desta propriedade ao nível do pai se não estiver definida. Enumerado: <br>- mandatory,<br>- notAvailable,<br>- optional,<br>- partly. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de URI apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| totalSpotNumber | Number | Número total de lugares pertencentes a este grupo | Qualquer número inteiro positivo ou 0. Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `refParkingSite`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
