# Descrição

O modelo de dados a seguir para representar **Movimentação de pessoas**, usando dados de telecomunicações, são os tipos `MobileDeviceCell` e `CellMobileData` inspirados no [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/). Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `MobileDeviceCell`.

| Propriedade | Tipo | Descrição | Nota |
| ----------- | ---- | --------- | ------------------------ |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `MobileDeviceCell` |
| address | Object | Endereço da área ocupada pela célula | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address]( https://schema.org/address) |
| areaServed | String | A área onde sobre a qual está definida a grelha. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| boundingBox | GeoJSON | Área da célula | Valores possíveis: 'Polygon' |
| cellRow | Integer | Número de linha numa grelha. | Obrigatório caso não seja usado `cellId`. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| cellColumn | Integer | Número de coluna numa grelha. | Obrigatório caso não seja usado `cellId`. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| createdAt | DateTime | Data e hora da criação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider | String | Sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| description | String | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endDate | DateTime | Registo de data e hora do fim da validade do modelo | Este atributo serve para definir, parcialmente, o intervalo de datas fechado onde os dados do modelo (normalmente a componente espacial) estão válidos. Ver startDate. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| license | URI | Licença associada aos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL) |
| location | GeoJSON | Referência Geojson para a célula | É centroide da célula. Valores possíveis: 'Point' |
| cellId | String | Identificador da célula | Obrigatório caso não seja usados conjuntamento  `cellRow` e `cellColumn`. Exemplos de valores de identificadores pode pode ser: uma representação conjunta de linha:coluna; um identificador relativo ao [CAOP](https://www.dgterritorio.gov.pt/cartografia/cartografia-tematica/caop); ou um identificador [BGRI](https://mapas.ine.pt/download/index2021.phtml).  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| modifiedAt | DateTime | Data e hora da modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| startDate | DateTime | Registo de data e hora do início da validade do modelo | Este atributo serve para definir, parcialmente, o intervalo de datas fechado onde os dados do modelo (normalmente a componente espacial) estão válidos. Ver endDate. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Para clarificar a semântica do atributo deve ser colocado um atributo de metainformação `description`. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `CellMobileData`.

| Propriedade | Tipo | Descrição | Nota |
| ------------ | ---- | --------- | ------------------------ |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `CellMobileData` |
| createdAt | DateTime | Data e hora da criação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endDate | DateTime | Registo de data e hora do fim do período de reporte | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Intervalo aberto. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| modifiedAt | DateTime | Data e hora da modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| numberOfDistinctDevices | Integer | Número de terminais distintos | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| numberOfDistinctDevicesInRoaming | Integer | Número de terminais distintos em roaming | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| numberOfDistinctDevicesByCountry | Object | Número de terminais distintos por país de origem | Para cada país, usar o código [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) de 3 letras para nome da propriedade e o valor associado é um número interior de terminais distintos na célula no período em análise. Exemplo: `{"CAN":3,"LKA":20}` representa 3 dispositivos distintos do Canadá e 20 do Sri Lanka. |
| numberOfEnteringDevices | Integer | Número de terminais distintos que entraram na célula no período em análise | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| numberOfLeavingDevices | Integer | Número de terminais distintos que sairam da célula no período em análise | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| numberOfEntryDevicesRoaming | Integer | Número de terminais distintos em roaming que entraram na célula no período em análise | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| numberOfLeavingDevicesRoaming | Integer | Número de terminais distintos em roaming que sairam da célula no período em análise | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| refMobileDeviceCell | URL | Referência para a célula a que as métricas dizem respeito | Normalmente um URN para um objectio do tipo `MobileDeviceCell`. |
| startDate | DateTime | Registo de data e hora do início do período de reporte | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| top10RegionOriginDevice | Array | Top 10 dos concelhos de origem dos dispositivos que entraram na célula no período em análise | Note-se que o número pode variar entre 1 e 10. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios para `MobileDeviceCell` são:

- `id`
- `type`
- `boundingBox`
- `startDate`
- `location`
- `dataProvider`

Os atributos obrigatórios para `CellMobileData` são:

- `id`
- `type`
- `numberOfDistinctDevices`
- `numberOfDistinctDevicesInRoaming`
- `numberOfDistinctDevicesByCountry`
- `numberOfEnteringDevices`
- `numberOfLeavingDevicesRoaming`
- `endDate`
- `startDate`
- `refMobileDeviceCell`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
