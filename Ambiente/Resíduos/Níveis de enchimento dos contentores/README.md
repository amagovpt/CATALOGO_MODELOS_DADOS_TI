# Descrição

O modelos de dado a seguir para representar **Nível de Enchimento dos Contentores de Resíduos** é o [WasteContainer](https://github.com/smart-data-models/dataModel.WasteManagement/blob/master/WasteContainer/doc/spec.md) inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Quando os contentores estão agregados em ilhas, deve ser usado em complemento o [WasteContainerIsle](https://github.com/smart-data-models/dataModel.WasteManagement/tree/952dca8b1b9b2b5fe8e82dcba25599316ab1478e/WasteContainerIsle).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da ilha | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `WasteContainer` |
| RFID  | String    | Fornece a ID do leitor RFID | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| actuationHours    | String    | Horário adequado para realizar intervenções no contentor | Modelo: [openingHours](https://github.com/smart-data-models/dataModel.WasteManagement/blob/master/WasteContainer/doc/openingHours) |
| annotations   | Array | Anotações do item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde um serviço ou produto é disponibilizado | Modelo: [https://schema.org/Text](https://schema.org/Text)  | 
| binCapacity | Number | Capacidade total em termos do volume de resíduos que o contentor pode conter | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| binColor | String | Cor do contentor de resíduos | Pode ser utilizado para indicar o tipo de resíduos. O código de cores deve seguir as convenções aplicáveis à zona geográfica em que os contentores estão localizados. Modelo: [https://schema.org/Text](https://schema.org/Text)|
| binFullnessThreshold | Number | Nível do limiar de enchimento  | Nível (em termos de percentagem) em que será gerado o alerta ou a notificação de posição cheia. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| binID | String | Identificador do contentor de transporte de resíduos | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| binLoggedTime | DateTime | Hora em que o nível da caixa foi registado pela última vez | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| binMaxLoad | Number | Carga máxima (peso) que o caixote do lixo pode suportar | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| binRecommendedLoad | Number | Carga recomendada (peso)  | Carga que o caixote do lixo correspondente a esta observação pode suportar. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| cargoWeight | Number  | Peso da carga transportada no contentor | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| category | String | Categoria do contentor | Enumerado: <br>- fixed, <br>- ground, <br>- other, <br>- portable, <br>- underground. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| color | String    | Cor do contentor  | Modelo: [https://schema.org/color](https://schema.org/color) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados harmonizada | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateLastCleaning | DateTime   | Data de quando o contentor foi limpo a última vez | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateLastEmptying | DateTime | Data e hora que representam a última vez que o contentor foi esvaziado | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified | DateTime  | Data e hora da última modificação da entidade  | Este será normalmente atribuídas pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateServiceStarted    | DateTime  | Data de entrada em serviço do contentor | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| fillingLevel | Number | Nível de enchimento do contentor |  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| isleId    | String    | Identificador (ou nome) da ilha onde o contentor está localizado | Este atributo deve ser utilizado quando entidades do tipo `WasteContainerIsle` não são modeladas especificamente. Caso contrário, deve ser utilizado `refWasteContainerIsle`. Modelo: [https://schema.org/Text](https://schema.org/Text)        | 
| location | GeoJSON | Referência Geojson para o objeto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'.  |
| methaneConcentration  |   Number  | Concentração de metano (CH4) dentro do contentor    | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| nextActuationDeadline | DateTime  | Data-limite para a próxima intervenção (esvaziamento, recolha, etc.) | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| owner | Array | Lista com uma sequência de caracteres em JSON que identifica os IDs únicos do(s) proprietário(s) | -- | 
| refDevice | Array | Referência ao(s) dispositivo(s) utilizado(s) para monitorizar este contentor | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| refWasteContainerIsle | Array | Ilha onde o contentor é colocado | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        | 
| refWasteContainerModel | Array | Modelo do contentor | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        | 
| regulation |  String  | Regulamento ao abrigo do qual o contentor opera  | Modelo: [http://schema.org/Text](http://schema.org/Text)   |
| responsible   |   String    | Entidade responsável pelo contentor | Encarregada das intervenções (esvaziamento, recolha, etc.). Modelo: [http://schema.org/Text](http://schema.org/Text)   | 
| serialNumber  | String    | Número de série do contentor  | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| source    | String    | URL que identifica a fonte original dos dados da entidade | Preferencialmente o domínio completo do fornecedor ou a URL do objeto de origem. Modelo: [http://schema.org/URL](http://schema.org/URL) | 
| status | String | Estado do contentor do ponto de vista da segurança | Enumerado: <br>- ok, <br>- lidOpen , <br>- dropped , <br>- moved , <br>- vandalized , <br>- burning , <br>- unknown. Modelo: [http://schema.org/Text](http://schema.org/Text)   |
| storedWasteCode   | String    | Depende da regulamentação aplicável  | Para a Europa, consulte a [Lista Europeia de Resíduos](http://ec.europa.eu/environment/waste/framework/list.htm). Segundo a regulamentação, códigos de resíduos que identificam de forma precisa a origem e o tipo de resíduo. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| storedWasteKind   | String    | Tipos de resíduo armazenados pelo contentor | Valores possíveis: <br>- 'orgânico',  <br>- 'inorgânico',  <br>- 'vidro',  <br>- 'óleo',  <br>- 'plástico',  <br>- 'metal',  <br>- 'papel',  <br>- 'baterias',  <br>- 'eletrónica',  <br>- 'perigoso',  <br>- 'outro'. Podem ser utilizados outros valores que não se enquadrem nas categorias acima. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| storedWasteOrigin | String    | Origem do resíduo contido no contentor | Valores possíveis: <br>- 'doméstico', <br>- 'municipal', <br>- 'industrial', <br>- 'construção', <br>- 'hotelaria', <br>- 'agricultura', <br>- 'outro'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| temperature   | Number    | Temperatura dentro do contentor   | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| timeInstant   | DataTime  | Carimbo temporal da carga |  Podem existir ambientes de produção em que o tipo do atributo seja uma string ISO8601. Nesse caso, deve ser considerado sinónimo de DateTime. Este atributo é mantido para compatibilidade com versões antigas de referência do FIWARE. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)    |
| wardId    | String    | Identificador da divisão administrativa (ward) da entidade associada a esta observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `binCapacity`
- `binColor`
- `binFullnessThreshold`
- `location`
- `status`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
