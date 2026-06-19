# Descrição

O modelo de dados a seguir para representar **Estações metereológicas**
é o [PointOfInterest](https://github.com/smart-data-models/dataModel.PointOfInterest) do [FIWARE Smart Data Models](https://github.com/smart-data-models/dataModel.WasteManagement/blob/master/WasteContainer/doc/spec.md). Este modelo tem a particularidade de ter como um dos valores da lista do atributo `category` o valor `WeatherStation`.

O modelo é compatível [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM)-NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf) da [ETSI](https://www.etsi.org/).

Nas anotações é possível encontrar um exemplo deste modelo, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Notas

A representação a usar é NGSI-LD.
Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo temos
- para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este como valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`;
- para a propriedade `location` é necessário adicionar como metainformação o campo `altitude` que indica a altidude da estação, por exemplo `"altitude": {"type": "Property", "value": 10, "unitCode": "MTR"}`
