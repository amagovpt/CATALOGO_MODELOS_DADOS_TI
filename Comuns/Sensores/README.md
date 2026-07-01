# Descrição

O modelo de dados a seguir para representar **Sensores** é garantido pelos modelos no [dataModel.Device](https://github.com/smart-data-models/dataModel.Device/tree/f80fb5f820fe52ac1c0892c56fb08ce586315b0a), nomeadamente [Device](https://github.com/smart-data-models/dataModel.Device/tree/f80fb5f820fe52ac1c0892c56fb08ce586315b0a/Device) e [DeviceModel](https://github.com/smart-data-models/dataModel.Device/tree/f80fb5f820fe52ac1c0892c56fb08ce586315b0a/DeviceModel) inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Estes modelos utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo destes modelos, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes nos modelos de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Device` ou `DeviceModel`|
| address                  | Object          | Morada associada ao dispositivo ou modelo | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| batteryLevel  | Number    | Nível da bateria do dispositivo   | Deve ser igual a 1,0 quando a bateria está cheia. 0,0 quando a bateria está vazia. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| brandName | String    | Nome da marca do dispositivo |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| category  | Array | Dispositivo que detecta e responde a eventos, alterações, e outros | Valores possíveis: 'Sensor', 'Contador', 'AVAC', 'Rede', ou de 'Multimédia'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| configuration | Array | Configuração técnica do dispositivo | Conjunto de propriedades e respectivos valores que captam parâmetros relacionados com a configuração de um dispositivo e que não são atualmente abrangidos pelos atributos normalizados definidos pelo presente modelo.  Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) |
| controlledAsset   | Array | Lista do(s) bem(ns) (edifício, objeto, etc.) controlado(s) pelo dispositivo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| controlledProperty    | Array | Qualquer coisa que possa ser detectada, medida ou controlada | Enumerado: <br>- airPollution,<br>- atmosphericPressure, <br>- averageVelocity, <br>- batteryLife, <br>- batterySupply, <br>- cdom, <br>- conductance, <br>- conductivity, <br>- depth, <br>-eatingActivity, <br>-lectricityConsumption, <br>- energy, <br>- fillingLevel, <br>- freeChlorine, <br>- gasConsumption, <br>- gateOpening, <br>- heading, <br>- humidity, <br>- light, <br>- location, <br>- milking, <br>- motion, <br>- movementActivity, <br>-noiseLevel, <br>- occupancy, <br>- orp, <br>- pH, <br>- power, <br>- precipitation, <br>- pressure, <br>- refractiveIndex, <br>- salinity, <br>- smoke, <br>- soilMoisture, <br>- solarRadiation, <br>- speed, <br>- tds, <br>- temperature, <br>- trafficFlow, <br>- tss, <br>- turbidity, <br>- waterConsumption, <br>- waterFlow, <br>- waterLevel, <br>- waterPollution, <br>- weatherConditions, <br>- weight, <br>- windDirection, <br>- windSpeed. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateFirstUsed | DateTime  | Data e hora que indica quando o dispositivo foi utilizado pela primeira vez | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateInstalled | DateTime  | Data e hora que indica quando o dispositivo foi instalado | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateLastCalibration | DateTime  | Data e hora que indica a última calibração do dispositivo | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
|  dateLastValueReported | DateTime  | Data e hora que indica a última vez que o dispositivo comunicou dados com êxito à nuvem | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateManufactured | DateTime  | Data e hora que indica quando o dispositivo foi fabricado | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved | DateTime  | Data da entidade observada definida pelo utilizador | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| depth | Number    | Localização deste dispositivo representada por uma profundidade a partir de um ponto de partida   | Modelo: [https://schema.org/depth](https://schema.org/depth)  |
| description | String     | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| deviceCategory   | String | Categoria do dispositivo |  Enumerado: <br>- actuator, <br>-  beacon, <br>- endgun, <br>- HVAC, <br>- implement, <br>- irrSection, <br>- irrSystem, <br>- meter, <br>- multimedia, <br>- network, <br>- sensor. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| deviceState | String  | Estado deste dispositivo de um ponto de vista operacional | O seu valor pode depender do fornecedor. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| direction | String    | Localização deste dispositivo | Enumerado: <br>- Inlet, <br>- Outlet, <br>- Entry, <br>- Exit. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| distance | Number | Localização deste dispositivo representada por uma distância a partir de um ponto de partida  | Modelo: [https://schema.org/Distance](https://schema.org/Distance) |
| firmwareVersion   | String    | Versão do firmware deste dispositivo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| function  | Array | Funcionalidade necessária para realizar a tarefa para a qual um dispositivo foi concebido | Um dispositivo pode ser concebido para desempenhar mais do que uma função. Definido pela [SAREF](https://w3id.org/saref#Function). Enumerado: <br>- levelControl,  <br>- sensing,  <br>- onOff,  <br>- openClose,  <br>- metering,  <br>- eventNotification. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| hardwareVersion   | String    | Versão do hardware deste dispositivo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ipAddress | Array | Lista de endereços IP do dispositivo | Pode ser uma lista de valores separada por vírgulas se o dispositivo tiver mais do que um endereço IP. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o objecto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| macAddress | String | Endereço MAC do dispositivo |  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| manufacturerName  | String    | Nome do fabricante do dispositivo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| mcc   | String    | Identifica o código de país móvel | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| mnc   | String    |  Identifica o Código de Rede Móvel (MNC) da rede à qual o dispositivo está ligado | Utilizado em combinação com um código de país móvel (MCC) (também conhecido como "tuplo MCC/MNC") para identificar inequivocamente um operador/transportador da rede móvel. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| modelName | String    | Nome do modelo do dispositivo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| name | String | O nome do objecto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
|   owner   |  Array    |  Lista que contém uma sequência de caracteres codificados que referencia os IDs únicos do(s) proprietário(s)  | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)  |
|   refDeviceModel  | URI   | Modelo do dispositivo | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| rssi  | Number    | Indicador da intensidade do sinal recebido para um dispositivo sem fios | Deve ser expresso em décibeis por minuto (DBM) ou ou miliwatt (MW). Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| serialNumber  | Number    | Número de série atribuído pelo fabricante | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| value | String    | Valor observado ou comunicado | Para dispositivos actuadores pode ser um valor 'On' ou 'Off'. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
 - brandName (modelo)
 - category (modelo)
 - controlledProperty (ambos)
 - id (ambos)
 - manufacturerName (modelo)
 - modelName (modelo)
 - type (ambos)
 
## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nestes modelos, os atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.