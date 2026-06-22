# Descrição

O modelo de dados a seguir para representar **Irregularidades no trânstio** é o `TrafficAlert` como reportado pelo [Waze for Cities](https://www.waze.com/wazeforcities/). 
Este modelo utiliza a descrição que pode ser consultada em [Waze Data Feed specifications](https://support.google.com/waze/partners/answer/13458165).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades do modelo TrafficAlert.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| uuid | String | Identificador único do alerta | Formato [UUID](https://datatracker.ietf.org/doc/html/rfc4122). Modelo: [https://schema.org/Text](https://schema.org/Text)|
| type | String | Tipo principal do alerta | Enumerado: <br>- ROAD_CLOSED,<br>- ACCIDENT,<br>- HAZARD,<br>- POLICE, etc. Modelo: [https://schema.org/Text](https://schema.org/Text)|
| subtype | String | Subtipo específico do alerta | Valores possíveis: 'ROAD_CLOSED_EVENT', 'ACCIDENT_MINOR', 'HAZARD_ON_ROAD'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | Object | Localização do alerta | Estrutura com coordenadas de longitude e de latitude. Modelo: [https://schema.org/Number](https://schema.org/Number)|
| street | String | Nome da rua onde ocorre o alerta | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress) |
| city | String | Cidade onde ocorre o alerta | Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| country | String | País onde ocorre o alerta | Código de país ISO. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| reportDescription | String | Descrição do alerta reportado pelo utilizador | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| reliability | Number | Nível de confiabilidade do alerta | Escala de 0 a 10. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| reportRating | Number | Classificação do relatório | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| magvar | Number | Variação magnética | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| pubMillis | Number | Timestamp de publicação em milissegundos | Normalmente expressa em Epoch time. Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `uuid`
- `type`
- `location`
- `pubMillis`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos.  Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.