# Descrição

O modelo de dados a seguir para representar **Consumo de Água** é baseado no [WaterConsumptionObserved](https://github.com/smart-data-models/dataModel.WaterConsumption/tree/master/WaterConsumptionObserved) do [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar exemplos de utilização deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados:

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id          | URI   | Identificador único da entidade   |  Ver [Regra para geração de indentificadores únicos](https://metadados.digital.gov.pt/#/catalogue/folder/b8474afb-2c16-477c-a980-f7ce6989e48d/description?edit=false). |
| type   | String          | Tipo da entidade           | Valor constante igual a `WaterConsumptionObserved` |
| acquisitionStageFailure          | Integer         | Sem resposta indutiva do dispositivo de medição    | Ex: `0` = Não ocorre, `1` = Ocorre |
| address                  | Object          | Morada associada ao ponto de medição | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| alarmFlowPersistence     | String          | Estado de persistência de fluxo anómalo | Enumerado: <br>- Nothing to report<br>- No persistence<br>- In progress impacting persistence<br>- In progress persistence<br>- Past Persistence during the period.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alarmStopsLeaks          | Integer         | Indicador de alarme por fugas ou interrupções    | Ex: `0` = Não ocorre, `1` = Ocorre |
| alarmTamper              | Integer         | Indicador de alarme por adulteração do dispositivo | Ex: `0` = Não ocorre, `1` = Ocorre |
| alarmWaterQuality        | Integer         | Indicador de alarme por qualidade da água | Ex: `0` = Não ocorre, `1` = Ocorre |
| alarmInProgress        | Integer         | Indicador de um alarme ativo | Ex: `0` = Não existe, `1` = existe |
| alternateName     | String          | Nome alternativo para o item  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed     | String          | A área geográfica coberta | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider     | String          | Identidade do fornecedor dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved        | DateTime | Registo de data e hora da observação |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String    | Descrição da entidade  | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location                 | GeoJSON         | Localização da medição de consumo | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| maxFlow              | Number         | Caudal máximo observado durante a última semana    | Unidade: litros, metros cúbicos (MTR), etc. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| minFlow              | Number         | Caudal mínimo observado durante a última semana    | Unidade: litros, metros cúbicos (MTR), etc. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| moduleTampered   | Integer    | Remoção do módulo do dispositivo de medição  | Ex: `0` = Não ocorre, `1` = Ocorre |
| name     | String          | Nome  para o item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner     | Array          | Uma lista de IDs do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| persistenceFlowDuration     | String          | A duração que o fluxo contínuo é registado pelo medidor. Campo de texto que mostra as durações em minutos (m), horas (h) ou dias (d) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso     | Array          | Lista de URI de recursos adicionais associados ao item. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source     | String          | Origem dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refDevice                | URI             | Referência ao dispositivo que realizou a medição | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| waterConsumption              | Decimal         | Quantidade de água consumida     | Unidade: litros, metros cúbicos (MTR), etc. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| waterType              | String         | O tipo de água por temperatura da água.     | Enumerado: <br>- cold, <br>- hot. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `dateObserved`
- `waterConsumption`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.