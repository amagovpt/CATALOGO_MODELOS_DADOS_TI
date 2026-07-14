# Descrição

O modelo de dados para representar **Veículos** é feito com o recurso aos modelos [VehicleModel](https://github.com/smart-data-models/dataModel.Transportation/blob/master/VehicleModel/doc/spec.md) e [Vehicle](https://github.com/smart-data-models/dataModel.Transportation/blob/master/Vehicle/doc/spec.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar exemplos de utilização deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://territoriosinteligentes.gov.pt). De notar que a descrição do modelo de [Vehicle](https://github.com/smart-data-models/dataModel.Transportation/blob/master/Vehicle/doc/spec.md) está noutro domínio, dentro do [CNMD](https://territoriosinteligentes.gov.pt/comunidade/projetos/catalogo-nacional-de-modelos-de-dados-para-os-territorios-inteligentes-cnmd).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

Para o `VehicleModel`:

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `VehicleModel` |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao) |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao). Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| annotations | Array | Anotações sobre o item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde se aplica este modelo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| brandName | String | Marca do veículo | Modelo: [https://schema.org/brand](https://schema.org/brand) |
| cargoVolume | Number | O volume disponível para carga ou bagagem. No caso dos automóveis, trata-se normalmente do volume da bagageira | O valor tem duas casas decimais, não pode ser 0, e deve ser incluído a unidade de medida como metainformação. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| color | String | A cor do veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Data da moodificação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| depth | Number | Profundidade do veículo | O valor tem duas casas decimais, não pode ser 0, e deve ser incluído a unidade de medida como metainformação. Modelo: [https://schema.org/depth](https://schema.org/depth) |
| description | String | Descrição textual da viagem de um utente | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| fuelConsumption | Number | A quantidade de combustível consumida para percorrer uma determinada distância | A unidade de medida deve ser indicada na metainformação, usando o atributo `unitText`. Modelo: [https://schema.org/fuelConsumption](https://schema.org/fuelConsumption) |
| fuelType | String | O tipo de combustível adequado para o motor ou motores do veículo | Enumerado: <br> - autogas, <br> - biodiesel, <br> - ethanol, <br>- cng, <br> - diesel, <br> - electric, <br> - gasoline, <br> - hybrid electric/diesel, <br> - hybrid electric/petrol, <br> - hydrogen, <br> - lpg, <br> - petrol, <br> - petrol (unleaded), <br> - petrol (leaded), <br> - other. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| height | Number | Altura do veículo | O valor tem duas casas decimais, não pode ser 0, e deve ser incluído a unidade de medida como metainformação. Modelo: [https://schema.org/height](https://schema.org/height) |
| img | URI | Uma imagem do item | URL da imagem. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| location | GeoJSON | Referência Geojson ao item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| manufacturerName | String | Nome do fabricante do veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| modelName | String | Nome do modelo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | Nome do item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista dos IDs do(s) proprietário(s) | A existir a propriedade, tem de ter pelo menos um valor. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | Array | Descrições adicionais | Lista de URLs para recursos externos. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | A origem dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| url | URI | URL que fornece uma descrição deste modelo de veículo | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| vehicleEngine | String | Informações sobre o motor ou motores do veículo | Modelo: [https://schema.org/vehicleEngine](https://schema.org/vehicleEnginevehicleEngine) |
| vehicleModelDate | DateTime | Data do lançamento do modelo | Por vezes utilizado para diferenciar versões da mesma marca e modelo. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/vehicleModelDate](https://schema.org/vehicleModelDate) |
| vehicleType | String | Tipo de veículo do ponto de vista das suas características estruturais. É diferente da categoria do veículo | Enumerado: <br> - agriculturalVehicle, <br> - anyVehicle, <br> - articulatedVehicle, <br> - bicycle, <br> - binTrolley, <br> - bus, <br> - car, <br> - caravan, <br> - carOrLightVehicle, <br> - carWithCaravan, <br> - carWithTrailer, <br> - cleaningTrolley, <br> - constructionOrMaintenanceVehicle, <br> - fourWheelDrive, <br> - highSidedVehicle, <br> - lorry, <br> - minibus, <br> - moped, <br> - motorcycle, <br> - motorcycleWithSideCar, <br> - motorscooter, <br> - sweepingMachine, <br> - tanker, <br> - threeWheeledVehicle, <br> - trailer, <br> - tram, <br> - twoWheeledVehicle, <br> - trolley, <br> - van, <br> - vehicleWithoutCatalyticConverter, <br> - vehicleWithCaravan, <br> - vehicleWithTrailer, <br> - withEvenNumberedRegistrationPlates, <br> - withOddNumberedRegistrationPlates, <br> - other. Os valores seguem a especificação [DATEX 2 V2.3](http://d2docs.ndwcloud.nu/_static/umlmodel/v2.3/index.htm) para os atributos `VehicleTypeEnum` e `VehicleTypeEnum2`. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| weight | Number | Peso do veículo | O valor tem duas casas decimais, não pode ser 0, e deve ser incluído a unidade de medida como metainformação. Modelo: [https://schema.org/weigth](https://schema.org/weigth) |
| width | Number | Largura do veículo | O valor tem duas casas decimais, não pode ser 0, e deve ser incluído a unidade de medida como metainformação. Modelo: [https://schema.org/width](https://schema.org/width) |

Para o `Vehicle`:

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Vehicle` |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao) |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao). Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| annotations | Array | Anotações sobre o veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde se aplica este modelo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| battery | Number | A percentagem atual de bateria restante no caso de um veículo elétrico ou de um dispositivo ligado ao veículo | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| bearing | Number | Fornece o ângulo GNSS do veículo medido no sentido horário a partir do Norte | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| cargoWeight | Number | Peso atual da carga do veículo | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| category | Array | Categoria(s) de veículo(s) de um ponto de vista externo | Enumerado: <br> - municipalServices, <br> -  nonTracked, <br> -  private, <br> -  public, <br> -  specialUsage, <br> -  tracked, <br>- emergency, ou outros valores relevantes para a apllicação. Apenas os veículos *tracked* estão permanentemente a ser monitorizados por um sistema de localização externo. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| color | String | Cor do veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| currentTripCount | Number | A contagem atual de viagens realizadas | A contagem é o acumulado no dia de operação especificado, à data/hora da observação. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data da criação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateFirstUsed | Date | Data que indica quando o veículo foi utilizado pela primeira vez | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/Date](https://schema.org/Date) |
| dateModified | DateTime | Data da modificação do registo | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateVehicleFirstRegistered | Date | A data do primeiro registo do veículo junto das respetivas autoridades | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/Date](https://schema.org/Date) |
| description | String | Descrição textual da viagem de um utilizador | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| deviceSimNumber | String | O número SIM do dispositivo no veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| emergencyVehicleType | String | Tipo de veículo de emergência correspondente a esta observação | Enumerado: <br> - policeCar, <br> -  policeMotorcycle, <br> -  policeVan, <br> -  policeSWAT, <br> -  fireEngine, <br> -  waterTender, <br> -  airAmbulance, <br> -  ambulance, <br> -  motorcycleAmbulance, <br> -  rescueVehicle, <br> -  hazardousMaterialsApparatus, <br> -  towTruck. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| feature | Array | Características incorporadas pelo veículo | Enumerado: <br> - abs, <br> -  airbag, <br> -  alarm, <br> -  backCamera, <br> -  disabledRamp, <br> -  gps, <br> -  internetConnection, <br> -  overspeed, <br> -  proximitySensor, <br> -  wifi, outros relevantes para o domínio da aplicação. Para representar múltiplas instâncias de uma característica, pode ser utilizada a seguinte sintaxe: <característica>,<ocorrências>. Por exemplo, um carro com 4 airbags será representado por *airbag,4*.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| fleetVehicleId | String | O identificador do veículo no contexto da frota de veículos à qual pertence | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| fuelEfficiency | Number | A distância percorrida por unidade de combustível utilizada | Normalmente expressa em quilómetros por litro (km/L). A unidade de medida deve ser indicada na metainformação, usando o atributo `unitCode`ou `unitText`. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| fuelFilled | Number | Quantidade de combustível abastecida no veículo correspondente a esta observação  | Normalmente expressa em litros (L). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| fuelType | String | O tipo de combustível usado | Enumerado: <br> - autogas, <br> - biodiesel, <br> - ethanol, <br>- cng, <br> - diesel, <br> - electric, <br> - gasoline, <br> - hybrid electric/diesel, <br> - hybrid electric/petrol, <br> - hydrogen, <br> - lpg, <br> - petrol, <br> - petrol (unleaded), <br> - petrol (leaded), <br> - other. Este valor deve ser consistente com o descrito no modelo de dados de `VehicleModel`. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| heading | Number | Indica a direção de deslocamento do veículo e é especificada em graus decimais | Valores admissíveis no intervalo [0,360), contando no sentido horário em relação ao norte. Se o veículo estiver parado (i.e., o valor do atributo *speed* for 0), então o valor do atributo *heading* deve ser igual a -1. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| ignitionStatus | Boolean | Indica o estado da ignição do veículo | *True* significa que está ligado.  Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| image | URI | Uma imagem do item | URL da imagem. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| license_plate | String | O número da matrícula do veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson ao item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| mileageFromOdometer | Number | A distância total percorrida por um determinado veículo desde a sua produção inicial, conforme indicada no seu conta-quilómetros | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| municipalityInfo | object | Informação do município correspondente a esta observação | Modelo: <https://schema.org/Text> |
| municipalityInfo.cityId | string | Identificador da cidade correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.cityName | string | Nome da cidade correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.district | string | Nome do distrito correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.stateName | string | Nome do concelho correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.ulbName | string | Nome da zona correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.wardId | string | Identificador da freguesia correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.wardName | string | Nome da freguesia correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| municipalityInfo.wardNum | number | Número da freguesia correspondente a esta observação | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome do item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista dos IDs do(s) proprietário(s) | A existir a propriedade, tem de ter pelo menos um valor. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| previousLocation | GeoJSON | Referência Geojson ao item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| purchaseDate | DateTime | Data de aquisição do veículo pelo actual proprietário | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| refVehicleModel | URI | Referência para um `VehicleModel` | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| reportId | string | Identificador único atribuído ao problema, relatório, feedback ou transação correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | * | Lista de URIs que apontam para recursos adicionais sobre o item | — |
| serviceOnDuty | boolean | Natureza do serviço prestado por um veículo de emergência correspondendo a esta observação | True indica que está em serviço. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| serviceProvided | array | Serviço(s) que o veículo é capaz de prestar ou aos quais está atribuído | Enumerado: <br> - auxiliaryServices, <br> -  cargoTransport, <br> -  construction, <br> -  fairground, <br> -  garbageCollection, <br> -  goodsSelling, <br> -  maintenance, <br> -  parksAndGardens, <br> -  roadSignalling, <br> -  specialTransport, <br> -  streetCleaning, <br> -  streetLighting, <br> -  urbanTransit, <br> -  wasteContainerCleaning, <br> -  ou outros específicos da aplicação. Modelo: <https://schema.org/Text> |
| serviceStatus | string | Estado do veículo (do ponto de vista do serviço prestado) | Enumerado: <br> - broken, <br> -  onRoute, <br> -  outOfService, <br> -  parked. Modelo: <https://schema.org/DateTime> |
| source | String | A origem dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| speed | Number | Magnitude da componente horizontal da velocidade atual do veículo | Normalmente experessa em kilómetros por hora (km/h). Deve ser um número real não negativo; -1 pode ser usado para indicar valor temporariamente desconhecido. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| tripNetWeightCollected | Number | Peso líquido recolhido pelo veículo correspondente a esta observação no final da viagem | Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| vehicleAltitude | string | Altitude atual do veículo segundo o GNSS. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleConfiguration | string | Texto curto indicando a configuração do veículo | Por exemplo: 'limited edition' Modelo: [https://schema.org/vehicleConfiguration](https://schema.org/vehicleConfiguration) |
| vehicleIdentificationNumber | string | Número de Identificação do Veículo (VIN)  | Um número de série único usado para identificar veículos motorizados. Modelo: [https://schema.org/vehicleIdentificationNumber](https://schema.org/vehicleIdentificationNumber) |
| vehiclePlateIdentifier | string | Matrícula do veículo | Referência normativa: DATEX II `vehicleRegistrationPlateIdentifier`.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleRunningStatus | string | Estado de funcionamento do veículo | Enumerado: <br>- running, <br>- waiting, <br>- stopped. Modelo: <https://schema.org/Text> |
| vehicleSpecialUsage | string | Indica se o veículo está a ser usado para fins especiais | Exemplos: 'ambulance', 'fireBrigade', 'military', 'police', 'schoolTransportation', 'taxi', 'trashManagement'. Modelo: [https://schema.org/vehicleSpecialUsage](https://schema.org/vehicleSpecialUsage) |
| vehicleTrackerDevice | string | Estado de instalação do dispositivo GNSS instalado no veículo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| vehicleType | String | Tipo de veículo do ponto de vista das suas características estruturais | Diferente da categoria do veículo. Enumerado: <br> - agriculturalVehicle, <br> - anyVehicle, <br> - articulatedVehicle, <br> - bicycle, <br> - binTrolley, <br> - bus, <br> - car, <br> - caravan, <br> - carOrLightVehicle, <br> - carWithCaravan, <br> - carWithTrailer, <br> - cleaningTrolley, <br> - constructionOrMaintenanceVehicle, <br> - fourWheelDrive, <br> - highSidedVehicle, <br> - lorry, <br> - minibus, <br> - moped, <br> - motorcycle, <br> - motorcycleWithSideCar, <br> - motorscooter, <br> - sweepingMachine, <br> - tanker, <br> - threeWheeledVehicle, <br> - trailer, <br> - tram, <br> - twoWheeledVehicle, <br> - trolley, <br> - van, <br> - vehicleWithoutCatalyticConverter, <br> - vehicleWithCaravan, <br> - vehicleWithTrailer, <br> - withEvenNumberedRegistrationPlates, <br> - withOddNumberedRegistrationPlates, <br> - other. Os valores seguem a especificação [DATEX 2 V2.3](http://d2docs.ndwcloud.nu/_static/umlmodel/v2.3/index.htm) para os atributos `VehicleTypeEnum` e `VehicleTypeEnum2`. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| wardId | string | Identificador da freguesia correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| wardName | string | Nome da freguesia correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| zoneName | string | Nome da zona da entidade correspondente a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios para o `VehicleModel` são:

- `id`
- `type`
- `brandName`
- `manufacturerName`
- `modelName`
- `name`
- `type`
- `vehicleType`

Os atributos obrigatórios para o `Vehicle` são:

- `id`
- `type`
- `category`
- `location`
- `type`
- `vehicleType`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nestes modelos, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
