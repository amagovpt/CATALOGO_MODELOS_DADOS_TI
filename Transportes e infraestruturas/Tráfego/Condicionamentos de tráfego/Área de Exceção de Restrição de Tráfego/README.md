# Descrição

O modelo de dados a seguir para representar **Condicionamentos de tráfego** é o [RestrictionException](https://github.com/smart-data-models/dataModel.Transportation/blob/master/RestrictionException/doc/spec.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `RestrictionException`|
| address | Object | Morada associada à exceção de restrição | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address](https://schema.org/address) |
| allowedVehicleType | Array | Tipo(s) de veículo permitido para atravessar a área de tráfego restrito | Especifica veículos que podem circular apesar da restrição geral. Pode incluir critérios como norma de emissões (euro6), tipo de combustível (petrol, electricity), etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da exceção de restrição | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| exceptionValidityHours | String | Dias da semana e horas em que a exceção é válida | Modelo: [https://schema.org/openingHours](https://schema.org/openingHours) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refRestrictedTrafficArea | URI | A área de tráfego restrito à qual esta exceção pertence | Referência URN a uma entidade RestrictedTrafficArea. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refVehicleModel | Array | Especifica características do veículo para o qual a exceção foi estabelecida | Referência a modelos específicos de veículos. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `allowedVehicleType`
- `refRestrictedTrafficArea`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`.

O campo `allowedVehicleType` deve ser preenchido com um conjunto de triplos no formato `"A, B, C"`, conforme definido em [DATEX II (Data Exchange for Traffic Information) version 2.3](https://docs.datex2.eu/v3.3/downloads/modelv23.html), onde cada elemento do triplo representa uma característica específica do veículo:

1. `A`: Classe de emissões. Os valores possíveis incluem:
'euro0', 'euro1', 'euro2', 'euro3', 'euro4', 'euro5', 'euro6', 'euro6c', 'euro6dTemp', 'euro6d', 'euroIV', 'euroV', 'euroVI', 'noEuroEmissionClassification'.
2. `B`: Tipo de veículo, de acordo com os enumerados 'VehicleTypeEnum' e 'VehicleTypeEnum2'. Exemplos de valores válidos incluem:
'agriculturalVehicle', 'anyVehicle', 'articulatedVehicle', 'bicycle', 'binTrolley', 'bus', 'car', 'caravan', 'carOrLightVehicle', 'carWithCaravan', 'carWithTrailer', 'cleaningTrolley', 'constructionOrMaintenanceVehicle', 'fourWheelDrive', 'highSidedVehicle', 'lorry', 'minibus', 'moped', 'motorcycle', 'motorcycleWithSideCar', 'motorscooter', 'sweepingMachine', 'tanker', 'threeWheeledVehicle', 'trailer', 'tram', 'twoWheeledVehicle', 'trolley', 'van', 'vehicleWithoutCatalyticConverter', 'vehicleWithCaravan', 'vehicleWithTrailer', 'withEvenNumberedRegistrationPlates', 'withOddNumberedRegistrationPlates', 'other'.
3. `C`: Tipo de combustível, conforme definido na enumeração 'FuelTypeEnum'. Os valores possíveis são:
'battery', 'biodiesel', 'diesel', 'dieselBatteryHybrid', 'electricity', 'hydrogen', 'lpg', 'petrol', 'petrolBatteryHybrid', 'petrolPlugInHybridElectric', 'unknownFuelType'.

Caso algum dos elementos do triplo não seja relevante (ou seja, indiferente), pode ser utilizado o caractere '-' para representar essa indiferença. Por exemplo, o valor "-,-,electricity" indica que qualquer veículo movido a electricidade está excecionado.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.

