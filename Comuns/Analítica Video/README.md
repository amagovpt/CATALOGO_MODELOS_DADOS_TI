# Descrição

O modelo de dados a seguir para representar **Analítica de vídeo e contagem fe eventos**
é o `EventCountingObserved` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `EventCountingObserved`    |
| aggregationPeriod | Number | Janela temporal usada para contar eventos, para efeitos de reporte | Quando adicionado a `observedAt` indica o limite superior aberto do intervalo de reporte.   Modelo: [https://schema.org/Number](https://schema.org/Number). |
|  cumulativeCountResetedAt   | DateTime    |   Data e hora do instante em que o valor cumulativo dos eventos para  zona de observação foi reiniciado |  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)    |
| detectionZone | GeoJSON | GeoJSON que define a zona em observação | Para a detecção em altura, e.g. colunas de fumo, os pontos devem incorporar uma terceita coordenada, a altura. Valores possíveis: 'Polygon'. |
|  observedAt   | DateTime    |   Data e hora do limite inferior do período de agregação de eventos   |  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)    |
| observedBy  | String     | Referência o sensor que fez a observação   | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| observedEvents  | Array     | Lista de objetos que representam os eventos identificados no período de observação  |  Se não foram detetados eventos, a lista deve vir vazia.  |
| observedEvents.type  | String     | Tipo de evento detetado | Obrigatório caso tenha sido detectado um evento. Enumerado: <br>- animal, <br>- bicycle, <br>- bus, <br>- car, <br>- counterflow, <br>- crowd, <br>- double_parking, <br>- flame, <br>- luggage, <br>- motorcycle, <br>- object,  <br>- queue, <br>- scooter, <br>- smoke_column, <br>- truck, <br>- vehicle. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| observedEvents.count | Integer | Número de eventos detetados no período de análise | Obrigatório caso tenha sido detectado um evento. Valor não negativo. Modelo: [https://schema.org/Integer](https://schema.org/Integer)     |
| observedEvents.cumulativeCount | Integer | Número acumulado de eventos num período alargado| Valor não negativo. Modelo: [https://schema.org/Integer](https://schema.org/Integer)     |
| observedEvents.countingDirection | String | Direção do elemento causador do evento relativo ao local em análise| Enumerado: <br>- entry, <br>- exit, <br>- bidirectional. Modelo: [https://schema.org/Integer](https://schema.org/Integer).     |
| observedEvents.detectionConfidence | Number | Confiança média da deteção dos eventos |Obrigatório caso tenha sido detectado um evento. Valor no intervalo [0.00 .. 1.00]. Modelo: [https://schema.org/Number](https://schema.org/Number). |
| location | GeoJSON | Referência GeoJSON para o local onde aconteceram os eventos  | O número de pontos tem de ser igual ou inferior ao somatório do número de eventos reportados para o período.  Valores possíveis: 'MultiPoint' |
| refPointOfInterest  | Array     | Lista de referências para pontos de interesse no local de observação    | Referência URN para uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text).   |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`   
- `type`
- `aggregationPeriod`
- `detectionZone`
- `observedEvents`
- `observedAt`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.