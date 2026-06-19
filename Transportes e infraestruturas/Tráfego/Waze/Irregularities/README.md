# Descrição

O modelo de dados a seguir para representar **Irregularidades no trânstio** é o `Irregularities` como reportado pelo [Waze for Cities](https://www.waze.com/wazeforcities/). 
Este modelo utiliza a descrição que pode ser consultada em [Waze Data Feed specifications](https://support.google.com/waze/partners/answer/13458165).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | Number | Identificador único da irregularidade | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| detectionDate | String | Data de deteção da irregularidade | Formato de data legível. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| detectionDateMillis | Number | Data de deteção em milissegundos | Normalmente expressa em Epoch time. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| updateDate | String | Data da última atualização | Formato de data legível. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| updateDateMillis | Number | Data de atualização em milissegundos | Normalmente expressa em Epoch time. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| line | Array | Linha geométrica que representa a irregularidade | Array de coordenadas [longitude, latitude] |
| type | String | Tipo de irregularidade | Enumerado: <br>- SMALL,<br>- MEDIUM,<br>- LARGE. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| speed | Number | Velocidade atual no segmento | Normalmente expressa em km/h (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| regularSpeed | Number | Velocidade regular esperada |  Normalmente expressa em km/h (KMH). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| delaySeconds | Number | Atraso em segundos | Comparado com condições normais. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| seconds | Number | Duração total da irregularidade | Normalmente expressa em segundos (SEC). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| length | Number | Comprimento do segmento afetado | Normalmente expressa em metros (MTR). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| trend | Number | Tendência da irregularidade | Indicador de melhoria/agravamento. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| street | String | Nome da rua afetada | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress) |
| city | String | Cidade onde ocorre a irregularidade | Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| country | String | País onde ocorre a irregularidade | Código de país ISO. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| severity | Number | Nível de severidade da irregularidade | Escala numérica. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| jamLevel | Number | Nível de congestionamento associado | Escala de 0 a 5. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| driversCount | Number | Número de condutores afetados | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| alertsCount | Number | Número de alertas relacionados | Modelo: [https://schema.org/Number](https://schema.org/Number) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `detectionDateMillis`
- `line`
- `type`
- `speed`
- `regularSpeed`


## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.