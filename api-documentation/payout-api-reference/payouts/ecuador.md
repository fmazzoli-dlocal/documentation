# Ecuador

### Mandatory parameters

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Mandatory parameter</b>
      </th>
      <th style="text-align:left"><b>Validations</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>login</b>
      </td>
      <td style="text-align:left">32 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>pass</b>
      </td>
      <td style="text-align:left">32 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>external_id</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_id</b>
      </td>
      <td style="text-align:left">See document validations <a href="ecuador.md#document-validations">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>document_type</b>
      </td>
      <td style="text-align:left">
        <p><b>CI</b>
        </p>
        <p><b>RUC</b>
        </p>
        <p><b>PASS </b>- Passport</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_name</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>beneficiary_lastname</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>city</b>
      </td>
      <td style="text-align:left">Max. 100 chars</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>country</b>
      </td>
      <td style="text-align:left">EC</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_code</b>
      </td>
      <td style="text-align:left">See bank codes <a href="ecuador.md#bank-codes">here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>bank_account</b>
      </td>
      <td style="text-align:left">See bank account validations<a href="ecuador.md#bank-codes"> here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>account_type</b>
      </td>
      <td style="text-align:left">
        <p><b>C</b>: for Checking accounts</p>
        <p><b>S</b>: for Savings accounts</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
  </tbody>
</table>

### Example request

```text
{
"login":"1n234n56",
"pass":"HolAc123o",
"external_id":"1234567812345678b",
"document_id":"1784559964",
"document_type":"CI",
"beneficiary_name":"JUAN",
"beneficiary_lastname":"PEREZ",
"city":"CIUDAD DE GUAYAQUIL",
"country":"EC",
"bank_code":"034",
"bank_account":"1234567891",
"account_type":"C",
"amount":"245.40",
"comments":"this is the 1st comment",
"extra_info":"{\"this_is_extra:2334/"}",
"notification_url":"https:\/\/thisisawebsite.net\/payments",
"type":"json"
}
```

### Document validations

<table>
  <thead>
    <tr>
      <th style="text-align:left">Validation</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Length</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Verification digit</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">CI</td>
      <td style="text-align:left">10</td>
      <td style="text-align:left">numeric</td>
      <td style="text-align:left">Last digit</td>
      <td style="text-align:left">
        <p>1.004.922.993</p>
        <p>1004922993</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Document</td>
      <td style="text-align:left">RUC</td>
      <td style="text-align:left">13</td>
      <td style="text-align:left">numeric</td>
      <td style="text-align:left">Apply verification algorithm</td>
      <td style="text-align:left">1234567892221</td>
    </tr>
  </tbody>
</table>

### **Bank codes**

_In this list there are the major banks of the country to see the complete list please ask for it._

| Bank Name | Bank Code |
| :--- | :--- |
| Banco Amazonas | 034 |
| Banco Asistencia Comunitaria Finca S.A. | 323 |
| Banco Bolivariano | 037 |
| Banco Capital S.A. | 061 |
| Banco Central | 001 |
| Banco Citibank | 024 |
| Banco Comercial De Manabi | 039 |
| Banco Coopnacional S.A. | 064 |
| Banco de Guayaquil | 017 |
| Banco de Loja | 029 |
| Banco de Machala | 025 |
| Banco del Austro | 035 |
| Banco del Instituto Ecuatoriano de Seguridad Social | 066 |
| Banco del Litoral | 043 |
| Banco del Pacifico | 030 |
| Banco del Pichincha | 010 |
| Banco Delbank | 027 |
| Banco Ecuatoriano de la Vivienda | 052 |
| Banco General Ruminahui | 042 |
| Banco Internacional | 032 |
| Banco Procredit | 060 |
| Banco Produbanco | 036 |
| Banco Promerica | 040 |
| Banco Solidario | 059 |
| Coop. 15 de Abril Ltda | 057 |
| Coop. 15 de Agosto Pilacoto | 290 |
| Coop. Accion y Desarrollo | 051 |
| Coop. Aho. y Cred. 16 de Junio | 660 |
| Coop. Aho. y Cred. 1Ro de Enero del Austro | 284 |
| Coop. Aho. y Cred. 23 de Julio | 058 |
| Coop. Aho. y Cred. 23 de Mayo Ltda. | 606 |
| Coop. Aho. y Cred. 29 de Octubre | 095 |
| Coop. Aho. y Cred. 4 de Octubre Ltda. | 294 |
| Coop. Aho. y Cred. 9 de Octubre Ltda | 325 |
| Coop. Aho. y Cred. Accion Rural | 326 |
| Coop. Aho. y Cred. Accion Tungurahua Ltda. | 636 |
| Coop. Aho. y Cred. Agraria Mushuk Kawsay Ltda. | 275 |
| Coop. Aho. y Cred. Agricola Junin Ltda | 424 |
| Coop. Aho. y Cred. Alfonso Jaramillo | 296 |
| Coop. Aho. y Cred. Alianza del Valle Ltda | 062 |
| Coop. Aho. y Cred. Alianza Minas Ltda. | 278 |
| Coop. Aho. y Cred. Ambato Ltda | 414 |
| Coop. Aho. y Cred. Andina Ltda. | 642 |
| Coop. Aho. y Cred. Artesanos Ltda | 417 |
| Coop. Aho. y Cred. Atuntaqui Ltda. | 086 |
| Coop. Aho. y Cred. Cacpe Celica | 656 |
| Coop. Aho. y Cred. Cam Com Canton Bolivar | 426 |
| Coop. Aho. y Cred. Camara Comer Ambato | 411 |
| Coop. Aho. y Cred. Camara Comercio Indigena | 295 |
| Coop. Aho. y Cred. Cariamanga Ltda | 422 |
| Coop. Aho. y Cred. Carroceros de Tungurahua | 634 |
| Coop. Aho. y Cred. Catamayo Ltda. Mie | 657 |
| Coop. Aho. y Cred. Chone Ltda | 067 |
| Coop. Aho. y Cred. Coca Ltda | 607 |
| Coop. Aho. y Cred. Comercio Ltda Portoviejo | 088 |
| Coop. Aho. y Cred. Const Comercio y Produccion | 407 |
| Coop. Aho. y Cred. Cotocollao | 065 |
| Coop. Aho. y Cred. Credi Facil Ltda. | 628 |
| Coop. Aho. y Cred. Crediamigo Ltda. Loja Mi | 653 |
| Coop. Aho. y Cred. Cristo Rey | 291 |
| Coop. Aho. y Cred. de la Peq. Emp. Cacpe Macara | 658 |
| Coop. Aho. y Cred. de la Peq. Emp. Cacpe Zamora Ltda. | 602 |
| Coop. Aho. y Cred. de Los Serv. Publ. del Min. de Ed. | 605 |
| Coop. Aho. y Cred. Desarrollo Integral Ltda. | 603 |
| Coop. Aho. y Cred. Dorado Ltda | 415 |
| Coop. Aho. y Cred. Ecuafuturo Ltda. | 630 |
| Coop. Aho. y Cred. Educ del Tungurahua | 413 |
| Coop. Aho. y Cred. Educadores Chimborazo | 292 |
| Coop. Aho. y Cred. Educadores de Pastaza Ltda. | 204 |
| Coop. Aho. y Cred. Educadores Tulcan Ltda. | 085 |
| Coop. Aho. y Cred. El Calvario Ltda. | 627 |
| Coop. Aho. y Cred. El Sagrario | 069 |
| Coop. Aho. y Cred. Erco Ltda | 410 |
| Coop. Aho. y Cred. Esc.Sup.Politec. Agrop. de Manabi Man | 420 |
| Coop. Aho. y Cred. Escencia Indigena Ltda. | 641 |
| Coop. Aho. y Cred. Familia Austral | 286 |
| Coop. Aho. y Cred. Fernando Daquilema | 429 |
| Coop. Aho. y Cred. Fortuna Mies | 654 |
| Coop. Aho. y Cred. Fundesarrollo | 406 |
| Coop. Aho. y Cred. Futuro y Progreso de Galapagos Lt | 661 |
| Coop. Aho. y Cred. Gonzanama Mies | 650 |
| Coop. Aho. y Cred. Grameen Amazonas | 604 |
| Coop. Aho. y Cred. Guamote Ltda. | 664 |
| Coop. Aho. y Cred. Guaranda Ltda. | 072 |
| Coop. Aho. y Cred. Huaicana Ltda | 609 |
| Coop. Aho. y Cred. Huayco Pungo Ltda | 419 |
| Coop. Aho. y Cred. Huinara Ltda. Mies | 626 |
| Coop. Aho. y Cred. Inka Kipu Ltda. | 635 |
| Coop. Aho. y Cred. Integral | 409 |
| Coop. Aho. y Cred. Jadan Ltda. Mies | 625 |
| Coop. Aho. y Cred. Juan de Salinas Ltda. | 270 |
| Coop. Aho. y Cred. Juan Pio de Mora Ltda. | 638 |
| Coop. Aho. y Cred. la Dolorosa Ltda | 073 |
| Coop. Aho. y Cred. la Merced | 557 |
| Coop. Aho. y Cred. Llanganates | 348 |
| Coop. Aho. y Cred. Lucha Campesina Ltda. | 663 |
| Coop. Aho. y Cred. Malchingui Ltda. | 273 |
| Coop. Aho. y Cred. Manantial de Oro Ltda. | 601 |
| Coop. Aho. y Cred. Maquita Cushun Ltda. | 631 |
| Coop. Aho. y Cred. Marcabeli Ltda | 423 |
| Coop. Aho. y Cred. Mi Tierra | 403 |
| Coop. Aho. y Cred. Minga Ltda. | 293 |
| Coop. Aho. y Cred. Mujeres Unidas Tantanakushk | 333 |
| Coop. Aho. y Cred. Mushuc Runa Ltda | 412 |
| Coop. Aho. y Cred. Nuestros Abuelos Ltda | 416 |
| Coop. Aho. y Cred. Nueva Esperanza | 427 |
| Coop. Aho. y Cred. Nueva Huancavilca | 408 |
| Coop. Aho. y Cred. Nueva Jerusalen | 272 |
| Coop. Aho. y Cred. Nuevos Horizontes El Oro Ltda. | 659 |
| Coop. Aho. y Cred. Once de Junio | 075 |
| Coop. Aho. y Cred. Oscus | 076 |
| Coop. Aho. y Cred. Pablo Munoz Vega | 093 |
| Coop. Aho. y Cred. Padre Julian Lorente Ltda | 077 |
| Coop. Aho. y Cred. Pedro Moncayo Ltda. | 279 |
| Coop. Aho. y Cred. Peq Emp Cacpe Yanzatza | 404 |
| Coop. Aho. y Cred. Peq Empr Cacpe Biblian | 078 |
| Coop. Aho. y Cred. Peq Empresa Gualaquiza | 402 |
| Coop. Aho. y Cred. Peq. Emp. de Loja Cacpe | 350 |
| Coop. Aho. y Cred. Pijal | 640 |
| Coop. Aho. y Cred. Pilahuin | 643 |
| Coop. Aho. y Cred. Pilahuin Tio Ltda | 608 |
| Coop. Aho. y Cred. Profesionales del Volante Union L | 655 |
| Coop. Aho. y Cred. Progreso | 079 |
| Coop. Aho. y Cred. Provida | 281 |
| Coop. Aho. y Cred. Pucara Ltda. | 644 |
| Coop. Aho. y Cred. Puellaro Ltda | 271 |
| Coop. Aho. y Cred. Puerto Lopez Ltda | 425 |
| Coop. Aho. y Cred. Quilanga Ltda. | 651 |
| Coop. Aho. y Cred. Riobamba | 080 |
| Coop. Aho. y Cred. Salasaca | 637 |
| Coop. Aho. y Cred. San Antonio Ltda. | 289 |
| Coop. Aho. y Cred. San Francisco | 081 |
| Coop. Aho. y Cred. San Francisco de Asis | 054 |
| Coop. Aho. y Cred. San Gabriel Ltda. | 328 |
| Coop. Aho. y Cred. San Jorge Ltda | 428 |
| Coop. Aho. y Cred. San Jose Ltda | 082 |
| Coop. Aho. y Cred. San Jose S.J. | 283 |
| Coop. Aho. y Cred. San Miguel de Los Bancos | 330 |
| Coop. Aho. y Cred. San Miguel de Sigchos | 646 |
| Coop. Aho. y Cred. Santa Ana Ltda | 084 |
| Coop. Aho. y Cred. Santa Anita Ltda | 418 |
| Coop. Aho. y Cred. Santa Rosa de Patutan Ltda. | 334 |
| Coop. Aho. y Cred. Santa Rosa Ltda | 096 |
| Coop. Aho. y Cred. Semilla del Progreso Ltda | 332 |
| Coop. Aho. y Cred. Senor de Giron | 285 |
| Coop. Aho. y Cred. Sierra Centro Ltda. | 647 |
| Coop. Aho. y Cred. Simiatug Ltda | 639 |
| Coop. Aho. y Cred. Sinchi Runa Ltda | 645 |
| Coop. Aho. y Cred. Sumac Llacta Ltda. | 662 |
| Coop. Aho. y Cred. Tena Ltda. | 276 |
| Coop. Aho. y Cred. Tulcan | 222 |
| Coop. Aho. y Cred. Tungurahua Ltda. | 287 |
| Coop. Aho. y Cred. Union Mercedaria Ltda. | 648 |
| Coop. Aho. y Cred. Valles del Lirio | 632 |
| Coop. Aho. y Cred. Vencedores de Tungurahua | 629 |
| Coop. Calceta Ltda | 087 |
| Coop. Capeco Ltda | 203 |
| Coop. Esfuerzo Unido Para El Desarr. del Chilco La | 633 |
| Coop. Jardin Azuayo | 015 |
| Coop. Juventud Ecuatoriana Progresista Ltda. | 091 |
| Coop. Manuel Esteban Godoy Ortega Ltda Coopmego | 092 |
| Coop. Peq. Empresa de Pastaza | 089 |
| Coop. Policia Nacional | 053 |
| Coop. Prevision Ahorro y Desarrollo | 094 |
| Financiera - Diners Club del Ecuador | 232 |
| Financiera Financoop | 097 |
| Interdin S.A. | 349 |
| Mutualista Ambato | 098 |
| Mutualista Azuay | 070 |
| Mutualista Imbabura | 099 |
| Mutualista Pichincha | 071 |
| Pacificard | 005 |
| BANCO D MIRO SA | 063 |
| BANECUADOR B.P. | 066 |
| BANCO DESARROLLO DE LOS PUEBLOS SA | 068 |
| COOP. DE A. Y C. UNIDAD Y PROGRESO | 100 |
| COOP DE A. Y C. MUSHUK YUYAY LTDA | 102 |
| COOP. DE A. Y C. NIZAG LTDA. | 103 |
| COOP. DE A. Y C. EL BUEN SEMBRADOR LTDA. | 104 |
| BCE-TRANSFERENCIAS REMESAS | 105 |
| BCE DINERO ELECTRONICO | 106 |
| COOP.DE AHORRO Y CREDITO 29 DE ENERO | 108 |
| COAC SINDICATO DE CHOFERES PROFESIONALES DE YANTZA | 109 |
| COOP. DE A. Y C. SENOR DEL ARBOL | 114 |
| COOP. DE A. Y C. QUILOTOA | 118 |
| COOP DE A. Y C. 22 DE JUNIO-ORIANGA | 119 |
| COOPERATIVA DE AHORRO Y CREDITO AMBATO LTDA. | 122 |
| COOPERATIVA DE AHORRO Y CREDITO CAMPESINA COOPAC | 125 |
| COOPERATIVA DE AHORRO Y CREDITO SANTA ISABEL LTDA | 176 |
| COOPERATIVA DIVINO NINO | 177 |
| COOPERATIVA LLACTA PURA | 178 |
| COOPERATIVA DE AHORRO Y CREDITO SEMBRANDO FUTURO | 179 |
| COAC AHORRISTA SOLIDARIO | 181 |
| COOP.DE AHORRO Y CREDITO CIUDAD DE ZAMORA | 182 |
| COAC LOJA INTERNACIONAL LTDA. | 186 |
| COOP DE AHORRO Y CREDITO BCE | 189 |
| COOP. DE A. Y C. EL MOLINO LTDA. | 193 |
| COOPERATIVA DE AHORRO Y CREDITO ARMADA NACIONAL | 194 |
| COOPERATIVA DE AHORRO Y CREDITO DISTRITO METROPOL | 196 |
| LA COOPERATIVA DE AH Y CRED SIMON BOLIVAR | 198 |
| COOPERATIVA DE AHORRO Y CREDITO GENERAL ANGEL FLOR | 200 |
| COOP.AHO Y CRED CAMARA DE COMERCIO PINDAL CADECOPI | 649 |
| COOP. DE A. Y C. COOPAC AUSTRO LTDA \(MIESS\) | 666 |
| FONDO DE CESANTIA DEL MAGISTERIO ECUATORIANO FCME- | 667 |
| COPP AHO CRED CREDISUR | 668 |
| COOP AHO Y CRED MAQUITA CUSHUNCHIC | 669 |
| COOP AHO Y CRED GRAL RUMINAHUI | 670 |
| COOP AHO Y CRED CASEG LTDA | 671 |
| COOP AHO Y CRED FOCLA | 672 |
| COOP AHO Y CRED FINAN INDIGENA | 673 |
| COOP AHO Y CRED 20 DE FEBRERO LTDA | 674 |
| COOP AHO Y CRED INDIGENA ALFA | 675 |
| COOP AHO Y CRED HUAQUILLAS | 677 |

