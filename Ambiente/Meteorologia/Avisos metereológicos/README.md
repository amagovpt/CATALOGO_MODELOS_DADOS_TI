# Descrição

O modelo de dados a seguir para representar **Avisos metereológicos**
é o [WeatherAlert](https://github.com/smart-data-models/dataModel.Weather/tree/47c1426bc46b7effe454af4f32c52bff54fe25ff/WeatherAlert) alinhados com o [FIWARE Smart Data Models](https://github.com/smart-data-models) . 
O modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | --  |
| type | String | Tipo de entidade | Valor constante igual a `WeatherAlert` |
| address                  | Object          | Morada associada ao ponto de medição | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| alertSource | URL | Fonte do alerta | Modelo: [http://schema.org/URL](http://schema.org/URL)  |
| category    | String | Categoria da entidade | Ex: 'weather'. Modelo:  [https://schema.org/Text](https://schema.org/Text)                 |
| dateIssued  | DateTime | A data e a hora em que o item foi emitido | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) | 
| severity    | String | Nível de gravidade | Valores possíveis: 'low', 'medium', 'high'. Modelo: [https://schema.org/Text](https://schema.org/Text)                          |
| subCategory | String | Categorias metereológicas | Enumerado: <br>- coastalEvent, <br>- coldWave, <br>- flood, <br>- forestFire, <br>- heatWave, <br>- highTemperature, <br>- hurricane, <br>- lowTemperature, <br>- rainfall, <br>- rain_flood, <br>- snow, <br>- snow_ice, <br>- wind. Modelo: [https://schema.org/Text](https://schema.org/Text)             |
| validFrom   | DateTime | Hora de início a partir da qual a indicação é válida | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| validTo     | DateTime | Hora final até à qual a indicação permanece em vigor | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |


## Propriedades obrigatórias

Os atributos obrigatórios são:
 - `alertSource`
 - `category`
 - `dateIssued`
 - `id`
 - `subCategory`
 - `type`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. 

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.