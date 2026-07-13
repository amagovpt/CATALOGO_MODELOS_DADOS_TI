# Descrição

O modelo de dados a seguir para representar **Recolha de Resíduos**
é o [WasteObserved](https://github.com/smart-data-models/dataModel.WasteManagement/tree/master/WasteObserved) inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `WasteObserved` |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao) |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao). Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName | String | Nome alternativo para a área de observação  |  Ex: nome comum ou local da localização. Modelo: [https://schema.org/Text](https://schema.org/Text).  |
| annotations       | Array          | Anotações sobre a observação  | Modelo: [ https://schema.org/Text]( https://schema.org/Text)   |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text).|
| color       | String          | Cor do item, de acordo com o cógido d cores em vigor |  Ex: amarelo. Modelo: [https://schema.org/Text](https://schema.org/Text).  |
| dataProvider     | String          | Identidade do fornecedor dos dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved  | DateTime    | A data e a hora desta observação | Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String    | Descrição deste item   | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| grossWeight   |   Number  | Peso bruto dos resíduos recolhidos    | Normalmente expressa em kilogramas (KGM). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| image   |   URI  | Um imagem do item | Modelo: [https://schema.org/URL](https://schema.org/URL). |
| location | GeoJSON | Referência Geojson para o item |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name  | String    | Nome deste item    | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| owner     | Array          | Uma lista de IDs do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refGarbageTruck |  String | Referência a um veículo de recolha de lixo | Normalmente um URN para a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        | 
| refServiceOrderId |  Array | Referência a um sistema externo que contém ordens de trabalho | Pode conter dados sobre um cliente que solicita a recolha de lixo, ou uma ordem de trabalho para recolha de resíduos, ou qualquer outra referência relevante. Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        | 
| refWeighingDevice                | URI             | Uma referência ao dispositivo utilizado para medir o peso dos resíduos | Modelo: [Device](https://github.com/smart-data-models/dataModel.Device/blob/master/Device/doc/spec.md) |
| seeAlso     | Array          | Lista de URI de recursos adicionais associados ao item. | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| source    | String    | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL    | Nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)    |
| tareWeight    |   Number  | Tara dos resíduos recolhidos    | Normalmente expressa em kilogramas (KGM). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| weight    |   Number  | Peso líquido dos resíduos recolhidos    | Normalmente expressa em kilogramas (KGM). Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `dateObserved`
- `location`
- `weight`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, os atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
