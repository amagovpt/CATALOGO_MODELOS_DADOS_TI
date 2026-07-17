# Descrição

Os modelos de dados a seguir para representar **Produção de eletricidade** são `EnergyGenerator` e o `EnergyProductionMeasurement` alinhado com o [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo utiliza uma corrente alternada (AC) para um sistema trifásico (L1, L2, L3) ou monofásico (L1) e neutro (N). Inclui atributos para várias medições eléctricas, como potência, potência aparente e  frequência.
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `EnergyGenerator`.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `EnergyGenerator`. |
| name | String | Nome legível do gerador de energia.  | Modelo: [https://schema.org/Text](https://schema.org/Text).    |
| generatorType | String | Tipo de tecnologia de geração de energia.   | Enumerado: <br>- biogas;<br>-biomass  <br>-coal;<br>-dieselGenerator;<br>-fuelOil;<br>-gasTurbine;<br>-geothermal;<br>-hybrid;<br>-hydro;<br>-nuclear;<br>-photovoltaic;<br>-smallHydro;<br>-solarThermal;<br>-tidal ;<br>-wave;<br>-windTurbine. Modelo: [https://schema.org/Text](https://schema.org/Text). |
| aggregationLevel  | String | Nível de agregação física ou lógica representado pela entidade.  | Enumerado: <br>-device;<br>-unit;<br>-site<br>-building;<br>-campus;<br>-district;<br>-city;<br>-region;<br>-gridConnection;<br>-substation;<br>-marketUnit. Modelo: [https://schema.org/Text](https://schema.org/Text). |
| installedCapacity | Number Property (kW)    | Potência nominal instalada do gerador.      | Capacidade máxima teórica; não é um valor medido. Normalmente expresso em kW. Modelo: [https://schema.org/Number](https://schema.org/Number).    |
| connectionType  | String | Tipo de ligação elétrica à rede.     | Enumerado: <br>-offGrid;<br>-gridTied;<br>-hybrid <br>-islanded;<br>-microgridConnected;<br>-backupOnly. Modelo: [https://schema.org/Text](https://schema.org/Text). |
| location   | GeoProperty      | Localização geográfica do gerador.   | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'|
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| owner      | Array | Lista dos IDs do(s) proprietário(s) do gerador.     | Pode referenciar pessoas, organizações ou entidades legais. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| manufacturer      | String | Fabricante do equipamento principal de geração.    | --   |
| model      | String | Modelo comercial do gerador.  | --   |
| serialNumber      | String | Número de série do equipamento.      | -- |
| commissioningDate | Date     | Data de entrada em funcionamento do gerador.| De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/Date](https://schema.org/Date)   |
| status     | String | Estado operacional atual do gerador. | Enumerado: <br>-operational, <br>-maintenance, <br>-fault, <br>-decommissioned.  |
| refDevice  | URI      | Referência a um dispositivo físico (ex.: inverter, controlador). | Usado quando existe um modelo Device separado.      |
| description| String | Descrição adicional do gerador.      | --    |

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `EnergyProductionMeasurement`.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id     | URI  | Identificador único da entidade NGSI-LD.   | Deve ser único no sistema.      |
| type   | String| Tipo da entidade.     | Valor fixo: `EnergyProductionMeasurement`.    |
| refGenerator  | URI | Referência ao gerador de energia (ex.: aerogerador, instalação fotovoltaica). | Define o ativo físico a que a medição se refere.  |
| dateObservedFrom     | DateTime    | Instante inicial do intervalo temporal da medição de energia.   | Dá contexto a todas as propriedades de energia (kWh, kVArh, kVAh). De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObservedTo| DateTime    | Instante final do intervalo temporal da medição de energia.     | Dá contexto a todas as propriedades de energia (kWh, kVArh, kVAh); Deve ser posterior a dateObservedFrom. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified | DateTime | Data e hora da modificação da entidade  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved  | DateTime    | Instante temporal de observação das grandezas instantâneas.     | Usado para potências, tensão, corrente, etc.      |
| energyGenerated      | Number | Energia ativa total produzida pelo gerador durante o intervalo definido.      | Igual ou superior a zero. Normalmente expressa em kWh. Modelo: Modelo: [https://schema.org/Number](https://schema.org/Number) |
| activeEnergyExport   | Number | Energia ativa exportada para a rede durante o intervalo. | Igual ou superior a zero. Normalmente expressa em kWh. Modelo: [https://schema.org/Number](https://schema.org/Number).   |
| reactiveEnergyExport | Number   | Energia reativa exportada para a rede durante o intervalo. | Igual ou superior a zero. Normalmente expressa em kVArh. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| apparentEnergyExport | Number  | Energia aparente exportada para a rede durante o intervalo.     | Igual ou superior a zero. Normalmente expressa em kVAh. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| activePower   | Number      | Potência ativa instantânea produzida no instante `dateObserved`.| Igual ou superior a zero. Estrutura por fase (ex.: L1, L2, L3). Normalmente expressa em kW. Modelo: [https://schema.org/Number](https://schema.org/Number). |
| reactivePower | Number    | Potência reativa instantânea no instante `dateObserved`. | Igual ou superior a zero. Normalmente expressa em kVAr. Modelo: [https://schema.org/Number](https://schema.org/Number)     |
| apparentPower | Number     | Potência aparente instantânea no instante `dateObserved`.| Igual ou superior a zero. Normalmente expressa em kVA. Modelo: [https://schema.org/Number](https://schema.org/Number)  |
| voltage| Number| Tensão elétrica medida por fase.    | Igual ou superior a zero. Varia em torno do nominal (230 V).      |
| current| Number      | Corrente elétrica medida por fase. | Igual ou superior a zero. Coerente com potência aparente. Normalmente expressa em A. Modelo: [https://schema.org/Number](https://schema.org/Number).|
| frequency     | Number     | Frequência da rede no instante de observação.     | Em Portugal, tipicamente 50 Hz. Modelo: [https://schema.org/Number](https://schema.org/Number).|
| powerFactor   | Number      | Fator de potência no instante de observação.      | Modelo: [https://schema.org/Number](https://schema.org/Number)    |
| source      | String| Fonte original dos dados da entidade. | URL. Modelo: [https://schema.org/Text](https://schema.org/Text)  |

## Propriedades obrigatórias

Os atributos obrigatórios para o modelo `EnergyGenerator` são:

- `id`
- `type`
- `address`
- `location`
- `generatorType`
- `connectionType`
- `installedCapacity`

Os atributos obrigatórios para o modelo `EnergyProductionMeasurement` são:

- `id`
- `type`
- `dateObservedFrom`
- `dateObservedTo`
- `energyGenerated`
- `activeEnergyExport`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição dos modelos de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, os modelos permitem a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.