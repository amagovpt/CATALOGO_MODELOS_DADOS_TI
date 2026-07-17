# Descrição

O modelo de dados a seguir para representar **Gestão de atendimento**
é o `ServiceInteraction` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `ServiceInteraction`    |
| bookingDate        | DateTime | Registo de data e hora da agendamento | Apenas relevante quando há agendamento do atendimento, devendo ser omitido noutros casos. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| bookingChannel         | String          | Canal de marcação | Enumerado:<br>- app,<br>- Web,<br>- in-person,<br>- telephone. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| bookingStatus         | String          | Estado da marcação | Enumerado:<br>- confirmed,<br>- cancelled,<br>- rescheduled. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| competencyProfile         | String          | Descrição do perfil de quem fez o atendimento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateStarted        | DateTime | Registo de data e hora do início do atendimento |   De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateFinished        | DateTime | Registo de data e hora do fim do atendimento |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateCreated        | DateTime | Data e hora da criação da entidade  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| interactionType         | String          | Tipo de atendimento | Enumerado: <br>- inPerson,<br>- videoconference,<br>- telephone,<br>- webChat,<br>- e-mail. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| intakeChannel         | String          | Canal de entrada | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| providingEntity     | String          | Identificação da entidade que presta o serviço. | Pode ser uma nome ou um URI. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| serviceStatus         | String          | Estado do atendimento | Enumerado:<br>- on hold,<br>- in progress,<br>- completed,<br>- cancelled. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| serviceName         | String          | O nome do serviço onde foi realizado o atendimento | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| rating         | Integer          | Avaliação do atendimento | Modelo: [https://schema.org/Integer](https://schema.org/Integer) |
| refCustomerServiceUnit      | String       | Referência para o local onde é prestado o serviço | Identificador do local (ponto de interesse), descrito no catálogo nacional de dados. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refRelatedInteractions      | Array       | Lista de referências para outras interacções | Identificador de outras interações que estejam relacionadas com o mesmo assunto, nomeadamente, onde o cidadão envolvido seja o mesmo. O objetivo é ter acesso a todas as interações q1ue foram necessárias para resolver o assunto que motivou o atendimento inicial. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ticketNumber         | String          | Número da senha | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ticketDate        | DateTime | Registo de data e hora em que a senha foi emitida | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| ticketType         | String          | Tipo da senha |Enumerado:<br>- normal,<br>- priority,<br>- scheduled. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ticketStatus         | String          | Estado da senha |Enumerado:<br>- issued,<br>- called,<br>- answered,<br>- expired. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| typeOfService        | String          | O serviço (objectivo) a prestar no atendimento |  Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `dateStarted`
- `dateFinished`
- `serviceName`
- `typeOfService`
- `serviceStatus`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.