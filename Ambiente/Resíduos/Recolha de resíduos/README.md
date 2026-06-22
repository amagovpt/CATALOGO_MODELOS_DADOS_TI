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
| address | Object | Morada associada à recolha de resíduos | Inclui país, localidade, rua, código postal. Modelo: [https://schema.org/address]( https://schema.org/address) |
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
- `dateObserved`
- `location`
- `weight`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, os atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
