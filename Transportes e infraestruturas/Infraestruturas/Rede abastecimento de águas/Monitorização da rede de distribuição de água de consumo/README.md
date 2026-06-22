# Descrição

Os modelos de dados para representar **Monitorização de Redes de Abastecimento (água, águas residuais e pluviais)** é o `WaterNetworkMonitoring` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home) e nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Representado como um URN |
| type | String | Tipo de entidade | Valor constante igual a `WaterNetworkMonitoring`|
| alerts | Array | Alertas ativos sobre a rede de água | Inclui `type` (quality, pressure, flow, leak), `severity` (low, medium, high), `timestamp`, `description` e `status` (active, resolved). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| chlorine | Object | Concentração de cloro na água | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| compliance | Object | Conformidade com normas e regulamentos | Inclui standards (EN 805, 98/83/EC), complianceStatus, lastAssessment e nextAssessment. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| conductivity | Object | Condutividade elétrica da água | Normalmente expressa em Siemens/m (D10). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| consumption | Object | Consumo de água monitorizado | Valores diários e mensais em metros cúbicos (MTQ). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| dataProvider | String | Sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataQuality | Object | Qualidade dos dados baseada em precisão, completude e validação | Inclui completeness, accuracy, lastValidation e validationMethod. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dissolvedOxygen | Object | Concentração de oxigénio dissolvido na água | Inclui valor, unitCode (MGM - mg/L), observedAt, measuringMethod (electrochemical) e qualityAssessment. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| energyEfficiency | Object | Eficiência energética da rede | Inclui pumpEfficiency, energyConsumption e carbonFootprint. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| flow | Object | Vazão da água na rede | Inclui valor, unitCode (G51 - litros por segundo) e observedAt. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| inspireId | Object | Identificação do sistema de monitorização de acordo com INSPIRE | Contém localId e namespace obrigatórios. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| leakDetection | Object | Informação sobre deteção de fugas | Inclui detected (boolean), probability, severity (none, low, medium, high) e location. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| license         | URI     | Licença dos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL) |
| location | GeoJSON | Localização geográfica do ponto de monitorização | Inclui coordenadas e sistema de referência. Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| maintenanceHistory | Array | Histórico de manutenções e inspeções realizadas | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| networkElement | Object | Características dos elementos da rede | Inclui elementType, material, diameter, length, installationDate e expectedLifespan. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| networkType | String | Tipo de rede monitorizada | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| observedBy | URI | Identificador do sensor responsável pela medição | Referência URN a uma entidade Device. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| operationalStatus | String | Estado operacional da rede de água | Enumerado: <br>- operational,<br>- maintenance,<br>- offline,<br>- emergency. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pH | Object | Valor do pH da água monitorizada | Inclui valor, observedAt, measuringMethod (potentiometric) e qualityAssessment com accuracy, precision e lastCalibration. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| pressure | Object | Pressão da água na rede | Normalmente expressa em bares (BAR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| temperature | Object | Temperatura da água monitorizada | Normalmente expressa em graus celsius (CEL). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| turbidity | Object | Turbidez da água | Normalmente expressa em unidades de Turbidez Nefelométrica (NTU). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| updateFrequency | Object | Frequência de atualização dos dados | Usa formato ISO 8601 (ex: PT15M para 15 minutos). Inclui description. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `inspireId`
- `location`
- `networkType`
- `dataQuality`
- `updateFrequency`

## Notas

Para alguns dos campos é requerida metainformação que garante a compatibilidade com INSPIRE e HVD. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.  

Nestes modelos temos:
- para requisitos INSPIRE:
  - identificador INSPIRE (`inspireId`) com componentes obrigatórios:
    - `localId`
    - `namespace`
    - `versionId`
  - sistema de referência de coordenadas padrão
  - esquemas XML INSPIRE
  - tipos de dados conformes com INSPIRE

- para requisitos HVD:
  - qualidade dos dados (`dataQuality`):
    - completude
    - precisão
    - método de validação
    - última validação
  - frequência de atualização (`updateFrequency`)
  - métodos de acesso (`accessMethods`):
    - endpoint da API
    - documentação
    - download em massa
    - formatos disponíveis
  - licenciamento claro (Creative Commons BY 4.0)

- para medições de qualidade da água:
  - cada parâmetro (pH, condutividade, etc.) como propriedade independente
  - para cada medição:
    - valor
    - unidade padronizada
    - método de medição
    - timestamp da observação
    - avaliação de qualidade
    - última calibração

- para conformidade e validação:
  - referência a normas aplicáveis
  - estado de conformidade
  - datas de avaliação
  - próxima avaliação programada

- requisitos gerais do modelo:
  - identificadores seguem formato URN padronizado
  - datas em formato ISO8601 UTC
  - coordenadas geográficas com sistema de referência INSPIRE
  - unidades seguem códigos UN/CEFACT
  - dados disponíveis em formatos legíveis por máquina
  - metadados completos para cada medição
  - informações de licenciamento e acesso
  - frequência de atualização especificada
  - métodos de acesso documentados


