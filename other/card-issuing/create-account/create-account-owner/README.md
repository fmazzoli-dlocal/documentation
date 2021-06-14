# Create account-owner

{% api-method method="post" host="https://issuing-api.dlocal.com" path="/issuing/accounts" %}
{% api-method-summary %}
Create an account
{% endapi-method-summary %}

{% api-method-description %}
This is the based method used to create a new wallet account and holder. Please **note each country may have its own additional requirements**, see below for more information.  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="hdmdata" type="string" required=false %}
Devices's fingerprint codified. 
{% endapi-method-parameter %}

{% api-method-parameter name="payload" type="string" required=false %}
Device's fingerprint.
{% endapi-method-parameter %}

{% api-method-parameter name="notification\_url" type="string" required=true %}
Notification to receive change status webhooks
{% endapi-method-parameter %}

{% api-method-parameter name="account\_reference" type="string" required=false %}
Owner's account unique id at merchant side. 
{% endapi-method-parameter %}

{% api-method-parameter name="owner" type="object" required=true %}
Owner Object
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Account and owner description
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "account_id": "ISGA-4-0c0abb666a6a4fa38f0c21260ed99ce8",
    "country": "CO",
    "currency": "COP",
    "balance": 0,
    "account_reference": "fOrvqODPvK",
    "status": "PENDING",
    "owner": {
        "first_name": "John",
        "last_names": "Smith",
        "birth_date": "27-11-1990",
        "email": "john@dlocal.com",
        "phone_number": "46043767",
        "document": "6095786098",
        "address": {
            "country": "CO",
            "city": "Medellin",
            "state": "Antioquia",
            "street": "Carrera 74 zZmLkR",
            "street2": "Carrera 74 EbXiEI"
            "house_number": "52",
            "zip_code": "05001000",
            "neighbourhood": "El Poblado"
        },
        "marital_status": "S",
        "gender": "M",
        "birth_place": "Colombia",
        "document_type": "CC",
        "nationality": "Colombian"
    },
    "description": "dLocal Issuing for John Smith",
    "creation_date": "2021-03-09T17:02:01.307Z",
    "notification_url": "http://merchant.dlocal.com/notification",
    "cards": []
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Owner's and Address Object

{% tabs %}
{% tab title="Owner Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| first\_name | String | Owner's First Name. **Required** |
| last\_names | String | Owner's complete Last Names. **Required** |
| birth\_date | String | Owner's birth date \(DD-MM-YYYY\). **Required.** |
| email | String | Owner's email. **Required** |
| phone\_number | String | Owner's phone number. In Brazil include DDD. **Required** |
| document | String | Owner’s personal identification number. **Required** |
| document\_type | String | Owner's personal identification type.  **Required** for Colombia. [See table below.]() |
| expedition\_date | String | Owner's personal identification expedition date \(DD-MM-YYYY\). **Required** for Colombia.  |
| mother\_name | String | Mothers Full Name. **Required** only for Brazil. |
| birth\_place | String | Place of birth. **Required** only for **Colombia** |
| nationality | String | Nationality. **Required** only for **Colombia** |
| gender | Char | M or F. **Required** for **Colombia**. |
| marital\_status | Char | [Check table below]() for more details. **Required** for **Colombia** |
| address | Address Object | Owner's Address. **Required** |
| ip\_address | String | Owner's IP Address. **Required for Colombia.** |
| terms\_and\_conditions\_accepted | Boolean | Account's terms and conditions.  **Required for Colombia.** |
| data\_management\_accepted | Boolean | Account's data management. **Required for Colombia.** |
{% endtab %}

{% tab title="Address Object" %}
| Property | Type | Description |
| :--- | :--- | :--- |
| country | String | Owner's country code. ISO 3166-1 alpha-2-code. **Required** |
| city | String | Owner's address city code. **Required**. [Colombia - See table below.]() |
| state | String | Owner's address state code. **Required**. [Colombia - See table below.]() |
| street | String | Owner's address street. **Required.** |
| street2 | String | Additional information on street. Optional. |
| house\_number | String | Owner's house number \(floor, apartment\). **Required.** |
| zip\_code | String | Owner's address zipcode. **Required for Brazil.** |
| neighbourhood | String | Neighbourhood or district. **Required for Brazil.** |
{% endtab %}
{% endtabs %}

### Example Request

{% tabs %}
{% tab title="Request" %}
```text
{
    "account_reference": "fOrvqODPvK",
    "payload": "kla44j1e3NlY5BSo9z4ofjb75PaK4Vpjt5nrU8s8vWuIUgxrmTTuCUpMcUGejYO
                KES5jfyEwHXXTSHCRR0QOtWyFGh8cmvSuCKzIlnY6x2KlT64K3H.ppAJZ7OQuyP
                BB2SCXw2SCYOvYDy25adjjftckcKyAd65hz7qTvtE0EREHQxbiyInrGfyex2uCK
                wQ9dvcpxUlzXJJIneGfYVAQEBEm1CdC5MQjGejuTDRNzcPiAksecXF5iTmk6eAX
                vIdVuxISg0QWvOe9fCMGa2hUMnGWpwoNSUC56MnGW87gq1HACVcHkxI5_1.9ihy
                ppAIKWbZcFKV8NTghN.nkre9zH_y3ExnJpyWVEL3NvWurk51lVB4WG.CNOt96h
                L._Wu_0L.BwCtOMu_Ep.ziPajoMu5.VNNW5BSuxIgtaqpRxuYIdw0xO9sarwyjJ
                vDOhhMETcouU.Uz8464qnvvYIw5Epir6UtTvqbRyhmgiFEjsnzxK9B5qfZvQAuZ
                a2bU0tzrU9juBhElbElLAUugLyTUbyATf92PIiyhqOfjVrwxN_l3yoonkJgI
                E_X_Qs796tlnhqvnmccbguaDcujhDna2QKlNdHlAmjJvDOhhM4XM0oGN_tvfvCS
                nBNleW5BNlan0QkBMfs.8gC",
    "hdmdata": "rO0ABXNyACdjb20udGhlNDEuY29tbW9ucy5jcnlwdG8uQ3J5cHRvRW52ZWxvcGU
                AAJbgqPhc8wIAA0wABWFsaWFzdAASTGphdmEvbGFuZy9TdHJpbmc7WwAMZW5jcn
                lwdGVkS2V5dAACW0JbABBlbmNyeXB0ZWRQYXlsb2FkcQB-", 
    "owner": {
        "first_name": "John",
        "last_names": "Smith",
        "birth_date": "27-11-1990",
        "email": "john@dlocal.com",
        "phone_number": "46043767",
        "document": "6095786098",
        "expedition_date": "08-12-2019"
        "address": {
            "country": "CO",
            "city": "Medellin",
            "state": "Antioquia",
            "street": "Carrera 74 zZmLkR",
            "street2": "Carrera 74 EbXiEI",
            "house_number": "52",
            "zip_code": "05001000",
            "neighbourhood": "El Poblado"
        },
        
        "marital_status": "S",
        "gender": "M",
        "birth_place": "Colombia",
        "nationality": "Colombian",
        "document_type": "CC",
        "ip_address": "186.52.133.239",
        "terms_and_conditions_accepted": "T",
        "data_management_accepted": "T"
    },
    "description": "dLocal Issuing for John Smith",
    "notification_url": "http://merchant.dlocal.com/notification"
}
```
{% endtab %}

{% tab title="Response" %}
```text
{
    "account_id": "ISGA-4-0c0abb666a6a4fa38f0c21260ed99ce8",
    "country": "CO",
    "currency": "COP",
    "balance": 0,
    "account_reference": "fOrvqODPvK",
    "status": "PENDING",
    "owner": {
        "first_name": "John",
        "last_names": "Smith",
        "birth_date": "27-11-1990",
        "email": "john@dlocal.com",
        "phone_number": "46043767",
        "document": "6095786098",
        "address": {
            "country": "CO",
            "city": "Medellin",
            "state": "Antioquia",
            "street": "Carrera 74 zZmLkR",
            "street2": "Carrera 74 EbXiEI"
            "house_number": "52",
            "zip_code": "05001000",
            "neighbourhood": "El Poblado"
        },
        "marital_status": "S",
        "gender": "M",
        "birth_place": "Colombia",
        "document_type": "CC",
        "nationality": "Colombian"
    },
    "description": "dLocal Issuing for John Smith",
    "creation_date": "2021-03-09T17:02:01.307Z",
    "notification_url": "http://merchant.dlocal.com/notification",
    "cards": []
}
```
{% endtab %}
{% endtabs %}

#### Asynchronous Notifications

When there is a change of status in the account, we will send you a notification to the provided `notification_url` indicating `account_id` . You will need to call [Get Account Information]() function to review this changes.

```text
{ 
  "account_id": "ISGA-4-0c0abb666a6a4fa38f0c21260ed99ce8" 
}
```

#### Document Type - used for Colombia

| document\_type | Description |
| :--- | :--- |
| CC | Cédula de ciudadanía |
| CE | Cédula de extranjería |
| NT | Número de identificación tributario |
| UN | Número único de identificación Personal |
|  |  |

#### Marital Status - used for Colombia

| Status | Description |
| :--- | :--- |
| S | Single |
| M | Married |
| W | Widowed |
| D | Divorced |

#### **States - used for Colombia**

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>
          <br />
        </p>
        <p>State</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>ALMEIDAS</p>
        <p>ALTO MAGDALENA</p>
        <p>ALTO OCCIDENTE</p>
        <p>ALTO ORIENTE</p>
        <p>ALTO SINU</p>
        <p>AMAZONAS</p>
        <p>ARAUCA</p>
        <p>ARCHIPIELAGO DE SAN ANDRES</p>
        <p>ARIARI</p>
        <p>ATRATO</p>
        <p>BAJO CAUCA</p>
        <p>BAJO MAGDALENA</p>
        <p>BAJO OCCIDENTE</p>
        <p>BAJO SINU</p>
        <p>BOGOTA</p>
        <p>CAPITAL</p>
        <p>CAQUETA</p>
        <p>CASANARE</p>
        <p>CENTRAL</p>
        <p>CENTRO</p>
        <p>CENTRO OCCIDENTE</p>
        <p>CENTRO ORIENTE</p>
        <p>COMUNERA</p>
        <p>CORDILLERANOS</p>
        <p>COSTA</p>
        <p>COSTANERA</p>
        <p>DARIEN</p>
        <p>DEPRESION MOMPOSINA</p>
        <p>DIQUE BOLIVARENSE</p>
        <p>VERTIENTE OCCIDENTAL</p>
        <p>FRIA</p>
        <p>GARCIA ROVIRA</p>
        <p>GUAINIA</p>
        <p>GUALIVA</p>
        <p>GUANENTA</p>
        <p>GUAVIARE</p>
        <p>GUAVIO</p>
        <p>GUTIERREZ</p>
        <p>IBAGUE</p>
        <p>LA LIBERTAD</p>
        <p>LENGUPA</p>
        <p>LOBA</p>
        <p>MAGDALENA CENTRO</p>
        <p>MAGDALENA MEDIO</p>
        <p>MAGDALENA MEDIO BOLIVARENSE</p>
        <p>MARES</p>
        <p>MARQUEZ</p>
        <p>MEDINA</p>
        <p>MOJANA</p>
        <p>MOJANA BOLIVARENSE</p>
        <p>MONTES DE MARIA</p>
        <p>MORROSQUILLO</p>
        <p>NEIRA</p>
        <p>NEVADOS</p>
        <p>NORDESTE</p>
        <p>NOROCCIDENTAL</p>
        <p>NORTE</p>
        <p>OCCIDENTAL</p>
        <p>OCCIDENTE</p>
        <p>ORIENTAL</p>
        <p>ORIENTE</p>
        <p>PACIFICO NORTE</p>
        <p>PACIFICO SUR</p>
        <p>PIEDEMONTE</p>
        <p>PUTUMAYO</p>
        <p>RICAURTE</p>
        <p>RIO</p>
        <p>RIO META</p>
        <p>RIO NEGRO</p>
        <p>SABANA CENTRO</p>
        <p>SABANA OCCIDENTE</p>
        <p>SABANAS</p>
        <p>SAN JORGE</p>
        <p>SAN JUAN</p>
        <p>SANTA MARTA</p>
        <p>SINU MEDIO</p>
        <p>SOACHA</p>
        <p>SOTO</p>
        <p>SUGAMUXI</p>
        <p>SUMAPAZ</p>
        <p>SUR</p>
        <p>SUR</p>
        <p>SUR OCCIDENTE</p>
        <p>SUR ORIENTE</p>
        <p>SUROESTE</p>
        <p>SURORIENTE</p>
        <p>TEQUENDAMA</p>
        <p>VERTIENTE DEL PACIFICO</p>
        <p>TUNDAMA</p>
        <p>UBATE</p>
        <p>VERTIENTE ORIENTAL</p>
        <p>URABA</p>
        <p>VALDERRAMA</p>
        <p>VALLE</p>
        <p>VALLE DEL ABURRA</p>
        <p>VAUPES</p>
        <p>VELEZ</p>
        <p>VICHADA</p>
      </td>
    </tr>
  </tbody>
</table>

#### **Cities - used for Colombia**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>City</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <br />
        </p>
        <p>ABEJORRAL</p>
        <p>ABREGO</p>
        <p>ABRIAQU&#xCD;</p>
        <p>ACACiAS</p>
        <p>ACAND&#xCD;</p>
        <p>ACEVEDO</p>
        <p>ACH&#xCD;</p>
        <p>AGRADO</p>
        <p>AGUA DE DIOS</p>
        <p>AGUACHICA</p>
        <p>AGUADA</p>
        <p>AGUADAS</p>
        <p>AGUAZUL</p>
        <p>AGUST&#xCD;N CODAZZI</p>
        <p>AIPE</p>
        <p>ALBAN</p>
        <p>ALB&#xC1;N</p>
        <p>ALBANIA</p>
        <p>ALCALa</p>
        <p>ALDANA</p>
        <p>ALEJANDR&#xCD;A</p>
        <p>ALGARROBO</p>
        <p>ALGECIRAS</p>
        <p>ALMAGUER</p>
        <p>ALMEIDA</p>
        <p>ALPUJARRA</p>
        <p>ALTAMIRA</p>
        <p>ALTO BAUD&#xD3;</p>
        <p>ALTOS DEL ROSARIO</p>
        <p>ALVARADO</p>
        <p>AMAGa</p>
        <p>AMALFI</p>
        <p>AMBALEMA</p>
        <p>ANAPOIMA</p>
        <p>ANCUYA</p>
        <p>ANDALUC&#xCD;A</p>
        <p>ANDES</p>
        <p>ANGELOPOLIS</p>
        <p>ANGOSTURA</p>
        <p>ANOLAIMA</p>
        <p>ANOR&#xCD;</p>
        <p>ANSERMA</p>
        <p>ANSERMANUEVO</p>
        <p>ANZA</p>
        <p>ANZO&#xC1;TEGUI</p>
        <p>APARTAD&#xD3;</p>
        <p>AP&#xCD;A</p>
        <p>APULO</p>
        <p>AQUITANIA</p>
        <p>ARACATACA</p>
        <p>ARANZAZU</p>
        <p>ARATOCA</p>
        <p>ARAUCA</p>
        <p>ARAUQUITA</p>
        <p>ARBEL&#xC1;EZ</p>
        <p>ARBOLEDA</p>
        <p>ARBOLEDAS</p>
        <p>ARBOLETES</p>
        <p>ARCABUCO</p>
        <p>ARENAL</p>
        <p>ARGELIA</p>
        <p>ARIGUAN&#xCD;</p>
        <p>ARJONA</p>
        <p>ARMENIA</p>
        <p>ARMERO</p>
        <p>ARROYOHONDO</p>
        <p>ASTREA</p>
        <p>ATACO</p>
        <p>ATRATO</p>
        <p>AYAPEL</p>
        <p>BAGAD&#xD3;</p>
        <p>BAH&#xCD;A SOLANO</p>
        <p>BAJO BAUD&#xD3;</p>
        <p>BALBOA</p>
        <p>BARANOA</p>
        <p>BARAYA</p>
        <p>BARBACOAS</p>
        <p>BARBOSA</p>
        <p>BARICHARA</p>
        <p>BARRANCA DE UPIA</p>
        <p>BARRANCABERMEJA</p>
        <p>BARRANCAS</p>
        <p>BARRANCO DE LOBA</p>
        <p>BARRANCO MINA</p>
        <p>BARRANQUILLA</p>
        <p>BECERRIL</p>
        <p>BELALC&#xC1;ZAR</p>
        <p>BELEN</p>
        <p>BEL&#xC9;N</p>
        <p>BEL&#xC9;N DE BAJIRA</p>
        <p>BEL&#xC9;N DE LOS ANDAQUIES</p>
        <p>BEL&#xC9;N DE UMBR&#xCD;A</p>
        <p>BELLO</p>
        <p>BELMIRA</p>
        <p>BELTR&#xC1;N</p>
        <p>BERBEO</p>
        <p>BETANIA</p>
        <p>BET&#xC9;ITIVA</p>
        <p>BETULIA</p>
        <p>BITUIMA</p>
        <p>BOAVITA</p>
        <p>BOCHALEMA</p>
        <p>BOGOTA D.C.</p>
        <p>BOJAC&#xC1;</p>
        <p>BOJAYA</p>
        <p>BOL&#xCD;VAR</p>
        <p>BOSCONIA</p>
        <p>BOYAC&#xC1;</p>
        <p>BRICE&#xD1;O</p>
        <p>BUCARAMANGA</p>
        <p>BUCARASICA</p>
        <p>BUENAVENTURA</p>
        <p>BUENAVISTA</p>
        <p>BUENOS AIRES</p>
        <p>BUESACO</p>
        <p>BUGA</p>
        <p>BUGALAGRANDE</p>
        <p>BURITIC&#xC1;</p>
        <p>BUSBANZ&#xC1;</p>
        <p>CABRERA</p>
        <p>CABUYARO</p>
        <p>CACAHUAL</p>
        <p>C&#xC1;CERES</p>
        <p>CACHIPAY</p>
        <p>CACHIR&#xC1;</p>
        <p>C&#xC1;COTA</p>
        <p>CAICEDO</p>
        <p>CAICEDONIA</p>
        <p>CAIMITO</p>
        <p>CAJAMARCA</p>
        <p>CAJIB&#xCD;O</p>
        <p>CAJIC&#xC1;</p>
        <p>CALAMAR</p>
        <p>CALARCA</p>
        <p>CALDAS</p>
        <p>CALDONO</p>
        <p>CALI</p>
        <p>CALIFORNIA</p>
        <p>CALIMA</p>
        <p>CALOTO</p>
        <p>CAMPAMENTO</p>
        <p>CAMPO DE LA CRUZ</p>
        <p>CAMPOALEGRE</p>
        <p>CAMPOHERMOSO</p>
        <p>CANALETE</p>
        <p>CANDELARIA</p>
        <p>CANTAGALLO</p>
        <p>CANTON DE SAN PABLO</p>
        <p>CA&#xD1;ASGORDAS</p>
        <p>CAPARRAP&#xCD;</p>
        <p>CAPITANEJO</p>
        <p>CAQUEZA</p>
        <p>CARACOL&#xCD;</p>
        <p>CARAMANTA</p>
        <p>CARCAS&#xCD;</p>
        <p>CAREPA</p>
        <p>CARMEN DE APICAL&#xC1;</p>
        <p>CARMEN DE BOL&#xCD;VAR</p>
        <p>CARMEN DE CARUPA</p>
        <p>CARMEN DE VIBORAL</p>
        <p>CARM&#xC9;N DEL DARI&#xC9;N</p>
        <p>CAROLINA</p>
        <p>CARTAGENA</p>
        <p>CARTAGENA DEL CHAIR&#xC1;</p>
        <p>CARTAGO</p>
        <p>CARURU</p>
        <p>CASABIANCA</p>
        <p>CASTILLA LA NUEVA</p>
        <p>CAUCASIA</p>
        <p>CEPIT&#xC1;</p>
        <p>CERET&#xC9;</p>
        <p>CERINZA</p>
        <p>CERRITO</p>
        <p>CERRO SAN ANTONIO</p>
        <p>CERTEGUI</p>
        <p>CHACHAGUI</p>
        <p>CHAGUAN&#xCD;</p>
        <p>CHAL&#xC1;N</p>
        <p>CHAMEZA</p>
        <p>CHAPARRAL</p>
        <p>CHARAL&#xC1;</p>
        <p>CHARTA</p>
        <p>CH&#xCD;A</p>
        <p>CHIBOLO</p>
        <p>CHIGOROD&#xD3;</p>
        <p>CHIMA</p>
        <p>CHIM&#xC1;</p>
        <p>CHIMICHAGUA</p>
        <p>CHIN&#xC1;COTA</p>
        <p>CHINAVITA</p>
        <p>CHINCHINa</p>
        <p>CHIN&#xDA;</p>
        <p>CHIPAQUE</p>
        <p>CHIPAT&#xC1;</p>
        <p>CHIQUINQUIR&#xC1;</p>
        <p>CH&#xCD;QUIZA</p>
        <p>CHIRIGUANA</p>
        <p>CHISCAS</p>
        <p>CHITA</p>
        <p>CHITAG&#xC1;</p>
        <p>CHITARAQUE</p>
        <p>CHIVAT&#xC1;</p>
        <p>CHIVOR</p>
        <p>CHOACH&#xCD;</p>
        <p>CHOCONT&#xC1;</p>
        <p>CICUCO</p>
        <p>CI&#xC9;NAGA</p>
        <p>CI&#xC9;NAGA DE ORO</p>
        <p>CI&#xC9;NEGA</p>
        <p>CIMITARRA</p>
        <p>CIRCASIA</p>
        <p>CISNEROS</p>
        <p>CIUDAD BOL&#xCD;VAR</p>
        <p>CLEMENCIA</p>
        <p>COCORN&#xC1;</p>
        <p>COELLO</p>
        <p>COGUA</p>
        <p>COLOMBIA</p>
        <p>COLON</p>
        <p>COL&#xD3;N</p>
        <p>COLOSO</p>
        <p>C&#xD3;MBITA</p>
        <p>CONCEPCI&#xD3;N</p>
        <p>CONCORDIA</p>
        <p>CONDOTO</p>
        <p>CONFINES</p>
        <p>CONSACA</p>
        <p>CONTADERO</p>
        <p>CONTRATACI&#xD3;N</p>
        <p>CONVENCI&#xD3;N</p>
        <p>COPACABANA</p>
        <p>COPER</p>
        <p>CoRDOBA</p>
        <p>C&#xD3;RDOBA</p>
        <p>CORINTO</p>
        <p>COROMORO</p>
        <p>COROZAL</p>
        <p>CORRALES</p>
        <p>COTA</p>
        <p>COTORRA</p>
        <p>COVARACH&#xCD;A</p>
        <p>COVE&#xD1;AS</p>
        <p>COYAIMA</p>
        <p>CRAVO NORTE</p>
        <p>CUASPUD</p>
        <p>CUBAR&#xC1;</p>
        <p>CUCAITA</p>
        <p>CUCUNUB&#xC1;</p>
        <p>C&#xDA;CUTA</p>
        <p>CUCUTILLA</p>
        <p>CU&#xCD;TIVA</p>
        <p>CUMARAL</p>
        <p>CUMARIBO</p>
        <p>CUMBAL</p>
        <p>CUMBITARA</p>
        <p>CUNDAY</p>
        <p>CURIT&#xCD;</p>
        <p>CURRILLO</p>
        <p>CURUMAN&#xCD;</p>
        <p>DABEIBA</p>
        <p>DAGUA</p>
        <p>DIBULLA</p>
        <p>DISTRACCION</p>
        <p>DOLORES</p>
        <p>DON MATiAS</p>
        <p>DOSQUEBRADAS</p>
        <p>DUITAMA</p>
        <p>DURANIA</p>
        <p>EB&#xC9;JICO</p>
        <p>EL &#xC1;GUILA</p>
        <p>EL BAGRE</p>
        <p>EL BANCO</p>
        <p>EL CAIRO</p>
        <p>EL CALVARIO</p>
        <p>EL CARMEN</p>
        <p>EL CARMEN DE ATRATO</p>
        <p>EL CARMEN DE CHUCUR&#xCD;</p>
        <p>EL CASTILLO</p>
        <p>EL CERRITO</p>
        <p>EL CHARCO</p>
        <p>EL COCUY</p>
        <p>EL COLEGIO</p>
        <p>EL COPEY</p>
        <p>EL DONCELLO</p>
        <p>EL DORADO</p>
        <p>EL DOVIO</p>
        <p>EL ENCANTO</p>
        <p>EL ESPINO</p>
        <p>EL GUACAMAYO</p>
        <p>EL GUAMO</p>
        <p>El Litoral del San Juan</p>
        <p>EL MOLINO</p>
        <p>EL PASO</p>
        <p>EL PAUJIL</p>
        <p>EL PE&#xD1;OL</p>
        <p>EL PE&#xD1;ON</p>
        <p>EL PE&#xD1;&#xD3;N</p>
        <p>EL PI&#xD1;ON</p>
        <p>EL PLAY&#xD3;N</p>
        <p>EL RETEN</p>
        <p>EL RETORNO</p>
        <p>EL ROBLE</p>
        <p>EL ROSAL</p>
        <p>EL ROSARIO</p>
        <p>El Tablon de Gomez</p>
        <p>EL TAMBO</p>
        <p>EL TARRA</p>
        <p>EL ZULIA</p>
        <p>EL&#xCD;AS</p>
        <p>ENCINO</p>
        <p>ENCISO</p>
        <p>ENTRERRIOS</p>
        <p>ENVIGADO</p>
        <p>ESPINAL</p>
        <p>FACATATIV&#xC1;</p>
        <p>FALAN</p>
        <p>FILADELFIA</p>
        <p>FILANDIA</p>
        <p>FIRAVITOBA</p>
        <p>FLANDES</p>
        <p>FLORENCIA</p>
        <p>FLORESTA</p>
        <p>FLORI&#xC1;N</p>
        <p>FLORIDA</p>
        <p>FLORIDABLANCA</p>
        <p>FOMEQUE</p>
        <p>FONSECA</p>
        <p>FORTUL</p>
        <p>FOSCA</p>
        <p>FRANCISCO PIZARRO</p>
        <p>FREDONIA</p>
        <p>FRESNO</p>
        <p>FRONTINO</p>
        <p>FUENTE DE ORO</p>
        <p>FUNDACION</p>
        <p>FUNES</p>
        <p>FUNZA</p>
        <p>F&#xDA;QUENE</p>
        <p>FUSAGASUG&#xC1;</p>
        <p>GACHALA</p>
        <p>GACHANCIP&#xC1;</p>
        <p>GACHANTIV&#xC1;</p>
        <p>GACHETA</p>
        <p>GAL&#xC1;N</p>
        <p>GALAPA</p>
        <p>GALERAS</p>
        <p>GAMA</p>
        <p>GAMARRA</p>
        <p>GAMBITA</p>
        <p>GAMEZA</p>
        <p>GARAGOA</p>
        <p>GARZ&#xD3;N</p>
        <p>GeNOVA</p>
        <p>GIGANTE</p>
        <p>GINEBRA</p>
        <p>GIRALDO</p>
        <p>GIRARDOT</p>
        <p>GIRARDOTA</p>
        <p>GIR&#xD3;N</p>
        <p>G&#xD3;MEZ PLATA</p>
        <p>GONZ&#xC1;LEZ</p>
        <p>GRAMALOTE</p>
        <p>GRANADA</p>
        <p>GUACA</p>
        <p>GUACAMAYAS</p>
        <p>GUACAR&#xCD;</p>
        <p>GUACHET&#xC1;</p>
        <p>GUACHUCAL</p>
        <p>GUADALUPE</p>
        <p>GUADUAS</p>
        <p>GUAITARILLA</p>
        <p>GUALMATAN</p>
        <p>GUAMAL</p>
        <p>GUAMO</p>
        <p>GUAPI</p>
        <p>GUAPOT&#xC1;</p>
        <p>GUARANDA</p>
        <p>GUARNE</p>
        <p>GUASCA</p>
        <p>GUATAPE</p>
        <p>GUATAQU&#xCD;</p>
        <p>GUATAVITA</p>
        <p>GUATEQUE</p>
        <p>GU&#xC1;TICA</p>
        <p>GUAVAT&#xC1;</p>
        <p>GUAYABAL DE SIQUIMA</p>
        <p>GUAYABETAL</p>
        <p>GUAYAT&#xC1;</p>
        <p>GuEPSA</p>
        <p>G&#xDC;IC&#xC1;N</p>
        <p>GUTI&#xC9;RREZ</p>
        <p>HACAR&#xCD;</p>
        <p>HATILLO DE LOBA</p>
        <p>HATO</p>
        <p>HATO COROZAL</p>
        <p>HATONUEVO</p>
        <p>HELICONIA</p>
        <p>HERR&#xC1;N</p>
        <p>HERVEO</p>
        <p>HISPANIA</p>
        <p>HOBO</p>
        <p>HONDA</p>
        <p>IBAGUe</p>
        <p>ICONONZO</p>
        <p>ILES</p>
        <p>IMUES</p>
        <p>IN&#xCD;RIDA</p>
        <p>INZ&#xC1;</p>
        <p>IPIALES</p>
        <p>IQUIRA</p>
        <p>ISNOS</p>
        <p>ITAGUI</p>
        <p>ITSMINA</p>
        <p>ITUANGO</p>
        <p>IZA</p>
        <p>JAMBALO</p>
        <p>JAMUND&#xCD;</p>
        <p>JARD&#xCD;N</p>
        <p>JENESANO</p>
        <p>JERIC&#xD3;</p>
        <p>JERUSAL&#xC9;N</p>
        <p>JES&#xDA;S MAR&#xCD;A</p>
        <p>JORD&#xC1;N</p>
        <p>JUAN DE ACOSTA</p>
        <p>JUN&#xCD;N</p>
        <p>JURAD&#xD3;</p>
        <p>LA APARTADA</p>
        <p>LA ARGENTINA</p>
        <p>LA BELLEZA</p>
        <p>LA CALERA</p>
        <p>LA CAPILLA</p>
        <p>LA CEJA</p>
        <p>LA CELIA</p>
        <p>LA CHORRERA</p>
        <p>LA CRUZ</p>
        <p>LA CUMBRE</p>
        <p>LA DORADA</p>
        <p>LA ESPERANZA</p>
        <p>LA ESTRELLA</p>
        <p>LA FLORIDA</p>
        <p>LA GLORIA</p>
        <p>LA GUADALUPE</p>
        <p>LA JAGUA DE IBIRICO</p>
        <p>LA JAGUA DEL PILAR</p>
        <p>LA LLANADA</p>
        <p>LA MACARENA</p>
        <p>LA MERCED</p>
        <p>LA MESA</p>
        <p>LA MONTA&#xD1;ITA</p>
        <p>LA PALMA</p>
        <p>LA PAZ</p>
        <p>LA PEDRERA</p>
        <p>LA PE&#xD1;A</p>
        <p>LA PINTADA</p>
        <p>LA PLATA</p>
        <p>LA PLAYA</p>
        <p>LA PRIMAVERA</p>
        <p>LA SALINA</p>
        <p>LA SIERRA</p>
        <p>LA TEBAIDA</p>
        <p>LA TOLA</p>
        <p>LA UNION</p>
        <p>LA UNI&#xD3;N</p>
        <p>LA URIBE</p>
        <p>LA UVITA</p>
        <p>LA VEGA</p>
        <p>LA VICTORIA</p>
        <p>LA VIRGINIA</p>
        <p>LABATECA</p>
        <p>LABRANZAGRANDE</p>
        <p>LAND&#xC1;ZURI</p>
        <p>LEBR&#xCD;JA</p>
        <p>LEIVA</p>
        <p>LEJAN&#xCD;AS</p>
        <p>LENGUAZAQUE</p>
        <p>LeRIDA</p>
        <p>LETICIA</p>
        <p>LiBANO</p>
        <p>LIBORINA</p>
        <p>LINARES</p>
        <p>LLOR&#xD3;</p>
        <p>LOPEZ</p>
        <p>LORICA</p>
        <p>LOS ANDES</p>
        <p>LOS C&#xD3;RDOBAS</p>
        <p>LOS PALMITOS</p>
        <p>LOS PATIOS</p>
        <p>LOS SANTOS</p>
        <p>LOURDES</p>
        <p>LURUACO</p>
        <p>MACANAL</p>
        <p>MACARAVITA</p>
        <p>MACEO</p>
        <p>MACHETA</p>
        <p>MADRID</p>
        <p>MAGANGU&#xC9;</p>
        <p>Magui</p>
        <p>MAHATES</p>
        <p>MAICAO</p>
        <p>MAJAGUAL</p>
        <p>M&#xC1;LAGA</p>
        <p>MALAMBO</p>
        <p>MALLAMA</p>
        <p>MANATi</p>
        <p>MANAURE</p>
        <p>MAN&#xCD;</p>
        <p>MANIZALES</p>
        <p>MANTA</p>
        <p>MANZANARES</p>
        <p>MAPIRIPaN</p>
        <p>MARGARITA</p>
        <p>MAR&#xCD;A LA BAJA</p>
        <p>MARINILLA</p>
        <p>MARIP&#xCD;</p>
        <p>MARIQUITA</p>
        <p>MARMATO</p>
        <p>MARQUETALIA</p>
        <p>MARSELLA</p>
        <p>MARULANDA</p>
        <p>MATANZA</p>
        <p>MEDELL&#xCD;N</p>
        <p>MEDINA</p>
        <p>MEDIO ATRATO</p>
        <p>MEDIO BAUD&#xD3;</p>
        <p>MEDIO SAN JUAN</p>
        <p>MELGAR</p>
        <p>MERCADERES</p>
        <p>MESETAS</p>
        <p>MILaN</p>
        <p>MIRAFLORES</p>
        <p>MIRANDA</p>
        <p>MIRITI - PARAN&#xC1;</p>
        <p>MISTRAT&#xD3;</p>
        <p>MIT&#xDA;</p>
        <p>MOCOA</p>
        <p>MOGOTES</p>
        <p>MOLAGAVITA</p>
        <p>MOMIL</p>
        <p>MOMP&#xD3;S</p>
        <p>MONGUA</p>
        <p>MONGU&#xCD;</p>
        <p>MONIQUIR&#xC1;</p>
        <p>MONTEBELLO</p>
        <p>MONTECRISTO</p>
        <p>MONTEL&#xCD;BANO</p>
        <p>Montengro</p>
        <p>MONTER&#xCD;A</p>
        <p>MONTERREY</p>
        <p>MO&#xD1;ITOS</p>
        <p>MORALES</p>
        <p>MORELIA</p>
        <p>MORICHAL</p>
        <p>MORROA</p>
        <p>MOSQUERA</p>
        <p>MOTAVITA</p>
        <p>MURILLO</p>
        <p>MURIND&#xD3;</p>
        <p>MUTATA</p>
        <p>MUTISCUA</p>
        <p>MUZO</p>
        <p>NARI&#xD1;O</p>
        <p>N&#xC1;TAGA</p>
        <p>NATAGAIMA</p>
        <p>NECH&#xCD;</p>
        <p>NECOCL&#xCD;</p>
        <p>NEIRA</p>
        <p>NEIVA</p>
        <p>NEMOCoN</p>
        <p>NILO</p>
        <p>NIMAIMA</p>
        <p>NOBSA</p>
        <p>NOCAIMA</p>
        <p>NORCASIA</p>
        <p>N&#xD3;VITA</p>
        <p>NUEVA GRANADA</p>
        <p>NUEVO COL&#xD3;N</p>
        <p>NUNCH&#xCD;A</p>
        <p>NUQU&#xCD;</p>
        <p>OBANDO</p>
        <p>OCAMONTE</p>
        <p>OCA&#xD1;A</p>
        <p>OIBA</p>
        <p>OICAT&#xC1;</p>
        <p>OLAYA</p>
        <p>OLAYA HERRERA</p>
        <p>ONZAGA</p>
        <p>OPORAPA</p>
        <p>ORITO</p>
        <p>OROCU&#xC9;</p>
        <p>ORTEGA</p>
        <p>OSPINA</p>
        <p>OTANCHE</p>
        <p>OVEJAS</p>
        <p>PACHAVITA</p>
        <p>PACHO</p>
        <p>PACOA</p>
        <p>P&#xC1;CORA</p>
        <p>PADILLA</p>
        <p>PAEZ</p>
        <p>P&#xC1;EZ</p>
        <p>PAICOL</p>
        <p>PAILITAS</p>
        <p>PAIME</p>
        <p>PAIPA</p>
        <p>PAJARITO</p>
        <p>PALERMO</p>
        <p>PALESTINA</p>
        <p>PALMAR</p>
        <p>PALMAR DE VARELA</p>
        <p>PALMAS DEL SOCORRO</p>
        <p>PALMIRA</p>
        <p>PALMITO</p>
        <p>PALOCABILDO</p>
        <p>PAMPLONA</p>
        <p>PAMPLONITA</p>
        <p>PANA PANA</p>
        <p>PANDI</p>
        <p>PANQUEBA</p>
        <p>PAPUNAHUA</p>
        <p>P&#xC1;RAMO</p>
        <p>PARATEBUENO</p>
        <p>PASCA</p>
        <p>PASTO</p>
        <p>PATIA</p>
        <p>PAUNA</p>
        <p>PAYA</p>
        <p>PAZ DE ARIPORO</p>
        <p>PAZ DE R&#xCD;O</p>
        <p>PEDRAZA</p>
        <p>PELAYA</p>
        <p>PENSILVANIA</p>
        <p>PE&#xD1;OL</p>
        <p>PEQUE</p>
        <p>PEREIRA</p>
        <p>PESCA</p>
        <p>PIAMONTE</p>
        <p>PIEDECUESTA</p>
        <p>PIEDRAS</p>
        <p>PIENDAMO</p>
        <p>PIJAO</p>
        <p>PIJI&#xD1;O DEL CARMEN</p>
        <p>PINCHOTE</p>
        <p>PINILLOS</p>
        <p>PIOJ&#xD3;</p>
        <p>PISBA</p>
        <p>PITAL</p>
        <p>PITALITO</p>
        <p>PIVIJAY</p>
        <p>PLANADAS</p>
        <p>PLANETA RICA</p>
        <p>PLATO</p>
        <p>POLICARPA</p>
        <p>POLONUEVO</p>
        <p>PONEDERA</p>
        <p>POPAY&#xC1;N</p>
        <p>PORE</p>
        <p>POTOS&#xCD;</p>
        <p>PRADERA</p>
        <p>PRADO</p>
        <p>PROVIDENCIA</p>
        <p>PROVIDENCIA Y SANTA CATALINA</p>
        <p>PUEBLO BELLO</p>
        <p>PUEBLO NUEVO</p>
        <p>PUEBLO RICO</p>
        <p>PUEBLO VIEJO</p>
        <p>PUEBLORRICO</p>
        <p>PUENTE NACIONAL</p>
        <p>PUERRES</p>
        <p>PUERTO ALEGRIA</p>
        <p>PUERTO ARICA</p>
        <p>PUERTO ASIS</p>
        <p>PUERTO BERRiO</p>
        <p>PUERTO BOYACa</p>
        <p>PUERTO CAICEDO</p>
        <p>PUERTO CARRE&#xD1;O</p>
        <p>PUERTO COLOMBIA</p>
        <p>PUERTO CONCORDIA</p>
        <p>PUERTO ESCONDIDO</p>
        <p>PUERTO GAIT&#xC1;N</p>
        <p>PUERTO GUZMAN</p>
        <p>PUERTO LEGUIZAMO</p>
        <p>PUERTO LIBERTADOR</p>
        <p>PUERTO LLERAS</p>
        <p>PUERTO LoPEZ</p>
        <p>PUERTO NARE</p>
        <p>PUERTO NARI&#xD1;O</p>
        <p>PUERTO PARRA</p>
        <p>PUERTO RICO</p>
        <p>PUERTO ROND&#xD3;N</p>
        <p>PUERTO SALGAR</p>
        <p>PUERTO SANTANDER</p>
        <p>PUERTO TEJADA</p>
        <p>PUERTO TRIUNFO</p>
        <p>PUERTO WILCHES</p>
        <p>PULI</p>
        <p>PUPIALES</p>
        <p>PURACE</p>
        <p>PURIFICACI&#xD3;N</p>
        <p>PUR&#xCD;SIMA</p>
        <p>QUEBRADANEGRA</p>
        <p>QUETAME</p>
        <p>QUIBD&#xD3;</p>
        <p>QUIMBAYA</p>
        <p>QUINCHiA</p>
        <p>QU&#xCD;PAMA</p>
        <p>QUIPILE</p>
        <p>RAGONVALIA</p>
        <p>RAMIRIQU&#xCD;</p>
        <p>R&#xC1;QUIRA</p>
        <p>RECETOR</p>
        <p>REGIDOR</p>
        <p>REMEDIOS</p>
        <p>REMOLINO</p>
        <p>REPELON</p>
        <p>RESTREPO</p>
        <p>RETIRO</p>
        <p>RICAURTE</p>
        <p>R&#xCD;O DE ORO</p>
        <p>R&#xCD;O FR&#xCD;O</p>
        <p>RIO QUITO</p>
        <p>R&#xCD;O VIEJO</p>
        <p>RIOBLANCO</p>
        <p>RIOFRIO</p>
        <p>RIOHACHA</p>
        <p>RIONEGRO</p>
        <p>RIOSUCIO</p>
        <p>RISARALDA</p>
        <p>RIVERA</p>
        <p>ROBERTO PAYAN</p>
        <p>ROLDANILLO</p>
        <p>RONCESVALLES</p>
        <p>ROND&#xD3;N</p>
        <p>ROSAS</p>
        <p>ROVIRA</p>
        <p>SABANA DE TORRES</p>
        <p>Sabanagrande</p>
        <p>SABANALARGA</p>
        <p>SABANAS DE SAN ANGEL</p>
        <p>SABANETA</p>
        <p>SABOY&#xC1;</p>
        <p>S&#xC1;CAMA</p>
        <p>S&#xC1;CHICA</p>
        <p>SAHAG&#xDA;N</p>
        <p>SALADOBLANCO</p>
        <p>SALAMINA</p>
        <p>SALAZAR</p>
        <p>SALDA&#xD1;A</p>
        <p>SALENTO</p>
        <p>SALGAR</p>
        <p>SAMAC&#xC1;</p>
        <p>SAMAN&#xC1;</p>
        <p>SAMANIEGO</p>
        <p>SAMPU&#xC9;S</p>
        <p>SAN AGUST&#xCD;N</p>
        <p>SAN ALBERTO</p>
        <p>SAN ANDR&#xC9;S</p>
        <p>SAN ANDR&#xC9;S SOTAVENTO</p>
        <p>SAN ANTERO</p>
        <p>SAN ANTONIO</p>
        <p>SAN ANTONIO DE TEQUENDAMA</p>
        <p>SAN BENITO</p>
        <p>SAN BENITO ABAD</p>
        <p>SAN BERNARDO</p>
        <p>SAN BERNARDO DEL VIENTO</p>
        <p>SAN CALIXTO</p>
        <p>SAN CARLOS</p>
        <p>SAN CARLOS GUAROA</p>
        <p>SAN CAYETANO</p>
        <p>SAN CRISTOBAL</p>
        <p>SAN DIEGO</p>
        <p>SAN EDUARDO</p>
        <p>SAN ESTANISLAO</p>
        <p>SAN FELIPE</p>
        <p>SAN FERNANDO</p>
        <p>SAN FRANCISCO</p>
        <p>SAN GIL</p>
        <p>SAN JACINTO</p>
        <p>SAN JACINTO DEL CAUCA</p>
        <p>SAN JER&#xD3;NIMO</p>
        <p>SAN JOAQU&#xCD;N</p>
        <p>SAN JOS&#xC9;</p>
        <p>SAN JOS&#xC9; DE LA MONTA&#xD1;A</p>
        <p>SAN JOS&#xC9; DE MIRANDA</p>
        <p>SAN JOS&#xC9; DE PARE</p>
        <p>SAN JOSE DEL FRAGUA</p>
        <p>SAN JOS&#xC9; DEL GUAVIARE</p>
        <p>SAN JOS&#xC9; DEL PALMAR</p>
        <p>SAN JUAN BETULIA</p>
        <p>SAN JUAN DE ARAMA</p>
        <p>SAN JUAN DE R&#xCD;O SECO</p>
        <p>SAN JUAN DE URABA</p>
        <p>SAN JUAN DEL CESAR</p>
        <p>SAN JUAN NEPOMUCENO</p>
        <p>SAN JUANITO</p>
        <p>SAN LORENZO</p>
        <p>SAN LUIS</p>
        <p>SAN LUIS DE CUBARRAL</p>
        <p>SAN LUIS DE GACENO</p>
        <p>SAN LUIS DE PALENQUE</p>
        <p>SAN MARCOS</p>
        <p>SAN MART&#xCD;N</p>
        <p>SAN MARTIN DE LOBA</p>
        <p>SAN MATEO</p>
        <p>SAN MIGUEL</p>
        <p>SAN MIGUEL DE SEMA</p>
        <p>SAN ONOFRE</p>
        <p>SAN PABLO</p>
        <p>SAN PABLO BORBUR</p>
        <p>SAN PEDRO</p>
        <p>SAN PEDRO DE CARTAGO</p>
        <p>SAN PEDRO DE URABA</p>
        <p>SAN PELAYO</p>
        <p>SAN RAFAEL</p>
        <p>SAN ROQUE</p>
        <p>SAN ROSA VITERBO</p>
        <p>SAN SEBASTIAN</p>
        <p>SAN SEBASTIAN DE BUENAVISTA</p>
        <p>SAN VICENTE</p>
        <p>SAN VICENTE DE CHUCUR&#xCD;</p>
        <p>SAN VICENTE DEL CAGU&#xC1;N</p>
        <p>SAN ZENON</p>
        <p>SANDON&#xC1;</p>
        <p>SANTA ANA</p>
        <p>SANTA B&#xC1;RBARA</p>
        <p>SANTA BARBARA DE PINTO</p>
        <p>SANTA CATALINA</p>
        <p>SANTA CRUZ</p>
        <p>SANTA HELENA DEL OP&#xD3;N</p>
        <p>SANTA ISABEL</p>
        <p>SANTA LUCiA</p>
        <p>SANTA MAR&#xCD;A</p>
        <p>SANTA MARTA</p>
        <p>SANTA ROSA</p>
        <p>SANTA ROSA DE CABAL</p>
        <p>SANTA ROSA DE LIMA</p>
        <p>SANTA ROSA de osos</p>
        <p>SANTA ROSA DEL SUR</p>
        <p>SANTA ROSAL&#xCD;A</p>
        <p>SANTA SOF&#xCD;A</p>
        <p>SANTAF&#xC9; DE ANTIOQUIA</p>
        <p>SANTANA</p>
        <p>SANTANDER DE QUILICHAO</p>
        <p>SANTIAGO</p>
        <p>SANTIAGO DE TOL&#xDA;</p>
        <p>SANTO DOMINGO</p>
        <p>Santo Tomas</p>
        <p>SANTUARIO</p>
        <p>SAPUYES</p>
        <p>SARAVENA</p>
        <p>SARDINATA</p>
        <p>SASAIMA</p>
        <p>SATIVANORTE</p>
        <p>SATIVASUR</p>
        <p>SEGOVIA</p>
        <p>SESQUIL&#xC9;</p>
        <p>SEVILLA</p>
        <p>SIACHOQUE</p>
        <p>SIBAT&#xC9;</p>
        <p>SIBUNDOY</p>
        <p>SILOS</p>
        <p>SILVANIA</p>
        <p>Silvia</p>
        <p>SIMACOTA</p>
        <p>SIMIJACA</p>
        <p>SIMIT&#xCD;</p>
        <p>SINC&#xC9;</p>
        <p>SINCELEJO</p>
        <p>SIP&#xCD;</p>
        <p>SITIONUEVO</p>
        <p>SOACHA</p>
        <p>SOAT&#xC1;</p>
        <p>SOCHA</p>
        <p>SOCORRO</p>
        <p>SOCOT&#xC1;</p>
        <p>SOGAMOSO</p>
        <p>SOLANO</p>
        <p>SOLEDAD</p>
        <p>SOLITA</p>
        <p>SOMONDOCO</p>
        <p>SONSON</p>
        <p>SOPETRaN</p>
        <p>SOPLAVIENTO</p>
        <p>SOP&#xD3;</p>
        <p>SORA</p>
        <p>SORAC&#xC1;</p>
        <p>SOTAQUIR&#xC1;</p>
        <p>SOTARA</p>
        <p>SUAITA</p>
        <p>SUAN</p>
        <p>SUAREZ</p>
        <p>SU&#xC1;REZ</p>
        <p>SUAZA</p>
        <p>SUBACHOQUE</p>
        <p>SUCRE</p>
        <p>SUESCA</p>
        <p>SUPAT&#xC1;</p>
        <p>SUP&#xCD;A</p>
        <p>SURATA</p>
        <p>SUSA</p>
        <p>SUSAC&#xD3;N</p>
        <p>SUTAMARCH&#xC1;N</p>
        <p>SUTATAUSA</p>
        <p>SUTATENZA</p>
        <p>TABIO</p>
        <p>TAD&#xD3;</p>
        <p>TALAIGUA NUEVO</p>
        <p>TAMALAMEQUE</p>
        <p>T&#xC1;MARA</p>
        <p>TAME</p>
        <p>T&#xC1;MESIS</p>
        <p>TAMINANGO</p>
        <p>TANGUA</p>
        <p>TARAIRA</p>
        <p>TARAPAC&#xC1;</p>
        <p>TARAZ&#xC1;</p>
        <p>TARQUI</p>
        <p>TARSO</p>
        <p>TASCO</p>
        <p>TAURAMENA</p>
        <p>TAUSA</p>
        <p>TELLO</p>
        <p>TENA</p>
        <p>TENERIFE</p>
        <p>TENJO</p>
        <p>TENZA</p>
        <p>TEORAMA</p>
        <p>TERUEL</p>
        <p>TESALIA</p>
        <p>TIBACUY</p>
        <p>TIBAN&#xC1;</p>
        <p>TIBASOSA</p>
        <p>TIBIRITA</p>
        <p>TIB&#xDA;</p>
        <p>TIERRALTA</p>
        <p>TIMAN&#xC1;</p>
        <p>TIMBIO</p>
        <p>TIMBIQUI</p>
        <p>TINJAC&#xC1;</p>
        <p>TIPACOQUE</p>
        <p>TIQUISIO</p>
        <p>TITIRIB&#xCD;</p>
        <p>TOCA</p>
        <p>TOCAIMA</p>
        <p>TOCANCIP&#xC1;</p>
        <p>TOG&#xDC;&#xCD;</p>
        <p>TOLEDO</p>
        <p>TOL&#xDA; VIEJO</p>
        <p>TONA</p>
        <p>T&#xD3;PAGA</p>
        <p>TOPAIPI</p>
        <p>TORIBIO</p>
        <p>TORO</p>
        <p>TOTA</p>
        <p>TOTORO</p>
        <p>TRINIDAD</p>
        <p>TRUJILLO</p>
        <p>TUBARA</p>
        <p>TULU&#xC1;</p>
        <p>TUMACO</p>
        <p>TUNJA</p>
        <p>TUNUNGU&#xC1;</p>
        <p>TUQUERRES</p>
        <p>TURBACO</p>
        <p>TURBANA</p>
        <p>TURBO</p>
        <p>TURMEQU&#xC9;</p>
        <p>TUTA</p>
        <p>TUTAZ&#xC1;</p>
        <p>UBAL&#xC1;</p>
        <p>UBAQUE</p>
        <p>UBATE</p>
        <p>ULLOA</p>
        <p>UMBITA</p>
        <p>UNE</p>
        <p>UNGU&#xCD;A</p>
        <p>UNION PANAMERICANA</p>
        <p>URAMITA</p>
        <p>URIBIA</p>
        <p>URRAO</p>
        <p>URUMITA</p>
        <p>USIACURi</p>
        <p>&#xDA;TICA</p>
        <p>VALDIVIA</p>
        <p>VALENCIA</p>
        <p>VALLE DE SAN JOS&#xC9;</p>
        <p>VALLE DE SAN JUAN</p>
        <p>VALLE DEL GUAMUEZ</p>
        <p>VALLEDUPAR</p>
        <p>VALPARAISO</p>
        <p>VEGACH&#xCD;</p>
        <p>V&#xC9;LEZ</p>
        <p>VENADILLO</p>
        <p>VENECIA</p>
        <p>VENTAQUEMADA</p>
        <p>VERGARA</p>
        <p>VERSALLES</p>
        <p>VETAS</p>
        <p>VIAN&#xCD;</p>
        <p>VICTORIA</p>
        <p>VIG&#xCD;A DEL FUERTE</p>
        <p>VIJES</p>
        <p>VILLA CARO</p>
        <p>VILLA DE LEYVA</p>
        <p>VILLA DEL ROSARIO</p>
        <p>VILLA GARZON</p>
        <p>VILLA RICA</p>
        <p>VILLAGOMEZ</p>
        <p>VILLAHERMOSA</p>
        <p>VILLAMARiA</p>
        <p>VILLANUEVA</p>
        <p>VILLAPINZ&#xD3;N</p>
        <p>VILLARRICA</p>
        <p>VILLAVICENCIO</p>
        <p>VILLAVIEJA</p>
        <p>VILLETA</p>
        <p>VIOT&#xC1;</p>
        <p>VIRACACH&#xC1;</p>
        <p>VISTA HERMOSA</p>
        <p>VITERBO</p>
        <p>YACOP&#xCD;</p>
        <p>YACUANQUER</p>
        <p>YAGUAR&#xC1;</p>
        <p>YAL&#xCD;</p>
        <p>YARUMAL</p>
        <p>YAVARAT&#xC9;</p>
        <p>YOLOMB&#xD3;</p>
        <p>YOND&#xD3;</p>
        <p>YOPAL</p>
        <p>YOTOCO</p>
        <p>YUMBO</p>
        <p>ZAMBRANO</p>
        <p>ZAPATOCA</p>
        <p>ZAPAYAN</p>
        <p>ZARAGOZA</p>
        <p>ZARZAL</p>
        <p>ZETAQUIRA</p>
        <p>ZIPACoN</p>
        <p>ZIPAQUIR&#xC1;</p>
        <p>ZONA BANANERA</p>
      </td>
    </tr>
  </tbody>
</table>

