# Descrição

O modelo de dados a seguir para representar **Congestionamento no trânsito** é o `TrafficJam` como reportado pelo [Waze for Cities](https://www.waze.com/wazeforcities/).
Este modelo utiliza a descrição que pode ser consultada em [Waze Data Feed specifications](https://support.google.com/waze/partners/answer/13458165).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades do modelo TrafficJam.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | Number | Identificador único do congestionamento | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| uuid | Number | Identificador UUID do congestionamento | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| level | Number | Nível de severidade do congestionamento | Escala de 0 a 5, onde 5 é mais severo. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| line | Array | Linha geométrica que representa o congestionamento | Estrutura com coordenadas de longitude e de latitude. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| speedKMH | Number | Velocidade atual | Normalmente expressa em km/h (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| speed | Number | Velocidade em unidades do sistema | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| length | Number | Comprimento do congestionamento | Normalmente em metros. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| delay | Number | Atraso causado pelo congestionamento | Normalmente expressa em segundos (SEC). Valor -1 indica dados não disponíveis. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| street | String | Nome da rua afetada | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress) |
| endNode | String | Nó final do segmento afetado | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| city | String | Cidade onde ocorre o congestionamento | Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| country | String | País onde ocorre o congestionamento | Código de país ISO. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| turnType | String | Tipo de curva no segmento | Enumerado: <br>- NONE,<br>- RIGHT,<br>- LEFT, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| type | String | Tipo do segmento de tráfego | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| roadType | Number | Tipo de estrada | Classificação numérica da categoria da estrada. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| segments | Array | Segmentos que compõem o congestionamento | Array de objetos de segmento |
| blockingAlertUuid | String | UUID do alerta que causa o bloqueio | Referência a um `TrafficAlert` relacionado |
| pubMillis | Number | Timestamp de publicação em milissegundos | Normalmente expressa em Epoch time. Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `level`
- `line`
- `length`
- `pubMillis`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos.  Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.