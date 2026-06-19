# Descrição

O modelo de dados a seguir para representar **Ocorrências rodoviárias** é o [RoadAccident](https://github.com/smart-data-models/dataModel.Transportation/blob/master/RoadAccident/doc/spec.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `RoadAccident`|
| accidentDate | DateTime | Data e hora do acidente | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| accidentDescription | Array | Descrição codificada das circunstâncias do acidente | Códigos numéricos representando situações específicas (0: Circunstância não especificada; 1: Condutor procedeu regularmente sem virar; 2: Condutor procedeu com condução distraída; 61: Condutor procedeu com condução distraída ou curso indeciso; 81: Avaria ou falha na direção; etc.). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| accidentLocation | String | Descrição breve se o acidente ocorreu numa área urbana ou extra-urbana | Códigos: 0: Regional dentro da área urbana; 1: Estrada urbana na cidade; 4: Estrada extra-urbana; 5: Provincial; 7: Autoestrada; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| accidentStatisticalDate | Object | Data estatística aproximada do acidente | Contém _year, quarter, weekday_ e _hour_ quando a fonte de dados original reporta apenas atributos estatísticos. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| accidentType | Array | Classificação rápida do tipo de acidente rodoviário | Códigos: 1: Colisão frontal; 2: Colisão fronto-lateral; 3: Colisão lateral; 4: Colisão; 5: Atropelamento de peão; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| address | Object | Morada associada ao acidente | Inclui país, região, localidade, rua. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual do acidente | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| localId | String | Identificador único do conjunto de dados de origem | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| numPassengersDead | Number | Número de passageiros de veículos mortos devido ao acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| numPassengersInjured | Number | Número de passageiros de veículos feridos devido ao acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| numPedestrianDead | Number | Número de peões mortos devido ao acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| numPedestrianInjured | Number | Número de peões feridos devido ao acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pedestriansInvolved | Boolean | Indica se peões estiveram envolvidos no acidente | Valor: true ou false. Modelo: [https://schema.org/Boolean](https://schema.org/Boolean) |
| roadClass | String | A classificação da estrada onde este acidente ocorreu | Conforme [OpenStreetMap highway classification](https://wiki.openstreetmap.org/wiki/Key:highway). Modelo: [https://wiki.openstreetmap.org/wiki/Key:highway](https://wiki.openstreetmap.org/wiki/Key:highway) |
| roadIntersection | String | Descrição breve do troço da estrada onde o acidente ocorreu | Códigos: 1: Cruzamento; 2: Rotunda; 7: Reta; 8: Curva; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadPaving | String | Pavimentação da estrada | Códigos: 1: Estrada pavimentada; 2: Estrada pavimentada rugosa; 3: Estrada não pavimentada. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadSign | String | Descrição breve da sinalização rodoviária onde o acidente ocorreu | Códigos: 1: Ausente; 2: Vertical; 3: Horizontal; 4: Vertical e horizontal; 5: Temporária por obra. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadSurface | String | Descrição breve da condição da estrada durante o acidente | Códigos: 1: Seca; 2: Molhada; 3: Escorregadia; 4: Congelada; 5: Com neve. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadTrunk | String | Descrição breve do tipo de via onde o acidente ocorreu | Códigos: 1: Ramo da estrada; 6: Faixa esquerda da autoestrada; 7: Faixa direita da autoestrada; 12: Outros casos; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| status | String | Estado do acidente rodoviário | Enumerado:<br>- archived,<br>- onGoing,<br>- solved. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| totalDeadPeopleWithin24Hours | Number | Número de pessoas mortas diretamente devido ao acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalDeadPeopleWithin30Days | Number | Número de pessoas mortas devido às consequências do acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalInjured | Number | Número total de pessoas feridas (não mortas) devido ao acidente | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| vehiclesInvolved | Array | Lista dos veículos (e peões) envolvidos no acidente | Códigos: 0: peão; 1: bicicleta; 5: carro; 8: cisterna; 13: motociclo; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| weakestSubject | String | Veículo que representa o sujeito mais vulnerável envolvido no acidente | Geralmente peão. Códigos: 0: peão; 1: bicicleta; 5: carro; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| weatherConditions | Array | Descrição breve das condições meteorológicas durante o acidente | Códigos: 0: noite limpa; 1: dia ensolarado; 3: parcialmente nublado; 10: aguaceiro ligeiro; etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`
- `status`



## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.