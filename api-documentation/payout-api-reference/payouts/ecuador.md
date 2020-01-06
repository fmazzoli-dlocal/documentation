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
        <p><b>A</b>: for Savings accounts</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>amount</b>
      </td>
      <td style="text-align:left">Max. 2 decimal numbers</td>
    </tr>
  </tbody>
</table>### Example request

```text

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
</table>### **Bank codes**

| Bank name | Bank code |
| :--- | :--- |
| BANCO DE GUAYAQUIL | 17 |
| BANCO DE FOMENTO | 2 |
| PACIFICARD | 5 |
| BANCO DEL PICHINCHA | 10 |
| BANCO TERRITORIAL | 19 |
| BANCO CITIBANK | 24 |
| BANCO DE MACHALA | 25 |
| BANCO UNIBANCO | 26 |
| BANCO DELBANK | 27 |
| BANCO DE LOJA | 29 |
| BANCO DEL PACIFICO | 30 |
| BANCO INTERNACIONAL | 32 |
| BANCO AMAZONAS | 34 |
| BANCO DEL AUSTRO | 35 |
| BANCO PRODUBANCO | 36 |
| BANCO BOLIVARIANO | 37 |
| BANCO COMERCIAL DE MANABI | 39 |
| BANCO PROMERICA | 40 |
| BANCO DEL LITORAL | 43 |
| BANCO SUDAMERICANO | 45 |
| BANCO COFIEC | 50 |
| BANCO SOLIDARIO | 59 |
| BANCO PROCREDIT | 60 |
| BANCO CAPITAL S.A. | 61 |
| BANCO DEL INSTITUTO ECUATORIANO DE SEGURIDAD SOCIA | 66 |
| MUTUALISTA AZUAY | 70 |
| MUTUALISTA PICHINCHA | 71 |
| COOP. AHO CRED COMERCIO LTDA PORTOVIEJO  | 88 |
| MUTUALISTA IMBABURA | 99 |
| BANCO CENTRAL | 1 |
| COOP. AHORRO Y CREDITO 23 DE JULIO            | 58 |
| COOP. AHORRO Y CREDITO PROGRESO      | 79 |
| COOP. AHO. Y CRED.ATUNTAQUI LTDA.              | 86 |
| COOP. AHORRO Y CREDITO 29 DE OCTUBRE  | 95 |
| COOP. JUVENTUD ECUATORIANA PROGRESISTA LTDA. | 91 |
| BANCO ECUATORIANO DE LA VIVIENDA | 52 |
| COOP. CRED Y AHO SAN FRANCISCO DE ASIS  | 54 |
| COOP. CAPECO LTDA | 203 |
| COOP. 15 DE ABRIL  LTDA | 57 |
| COOP.AHO Y CRED ALIANZA DEL VALLE LTDA  | 62 |
| COOP. AHORRO Y CREDITO ANDALUCIA  | 63 |
| BANCO COOPNACIONAL S.A. | 64 |
| COOP. AHORRO Y CREDITO COTOCOLLAO | 65 |
| COOP.AHORRO Y CREDITO CHONE LTDA  | 67 |
| COOP. AHO.Y CRED. DESARROLLO PUEBLOS  | 68 |
| COOP. AHORRO Y CREDITO EL SAGRARIO  | 69 |
| COOP. AHORRO Y CREDITO GUARANDA LTDA. | 72 |
| COOP. DE AHO Y CRED LA DOLOROSA LTDA  | 73 |
| COOP. AHO Y CRED ONCE DE JUNIO  | 75 |
| COOP. AHORRO Y CREDITO OSCUS | 76 |
| COOP AHO Y CRED PADRE JULIAN LORENTE LTDA  | 77 |
| COOP. JARDIN AZUAYO | 15 |
| COOP. AHO Y CRED PEQ EMPR CACPE BIBLIAN  | 78 |
| COOP. AHORRO Y CREDITO RIOBAMBA  | 80 |
| COOP. AHORRO Y CREDITO SAN FRANCISCO  | 81 |
| COOP. AHO Y CRED SAN JOSE LTDA  | 82 |
| COOP DE AHO Y CRED SANTA ANA LTDA | 84 |
| COOP. DE A. Y C. EDUCADORES TULCAN LTDA. | 85 |
| COOP. CALCETA LTDA  | 87 |
| COOP.PEQ.EMPRESA DE PASTAZA  | 89 |
| COOP MANUEL ESTEBAN GODOY ORTEGA LTDA COOPMEGO  | 92 |
| COOP. AHO Y CRED PABLO MUNOZ VEGA  | 93 |
| COOP. PREVISION AHORRO Y DESARROLLO  | 94 |
| COOP. AHO Y CRED. SANTA ROSA LTDA  | 96 |
| FINANCIERA FINANCOOP | 97 |
| MUTUALISTA AMBATO | 98 |
| COOP ACCION Y DESARROLLO | 51 |
| COOP POLICIA NACIONAL | 53 |
| COOP. DE A Y C EDUCADORES DE PASTAZA LTDA. | 204 |
| COOP. AHORRO Y CREDITO TULCAN | 222 |
| FINANCIERA - DINERS CLUB DEL ECUADOR | 232 |
| COOP. AHO Y CRED JUAN DE SALINAS LTDA. | 270 |
| COOP. AHO Y CRED PUELLARO LTDA | 271 |
| COOP. AHO Y CRED NUEVA JERUSALEN | 272 |
| COOP. AHO Y CRED MALCHINGUI LTDA. | 273 |
| COOP. AHO Y CRED AMAZONAS LTDA. | 274 |
| COOP.AHO Y CRED AGRARIA MUSHUK KAWSAY LTDA. | 275 |
| COOP. AHO Y CRED  TENA LTDA. | 276 |
| COOP. AHO Y CRED ALIANZA MINAS LTDA. | 278 |
| COOP. AHO Y CRED PEDRO MONCAYO LTDA. | 279 |
| COOP. AHORRO Y CREDITO PROVIDA | 281 |
| COOP. AHO Y CRED COOPERA LTDA. | 282 |
| COOP AHO Y CRED SAN JOSE S.J. | 283 |
| COOP.AHO Y CRED 1RO DE ENERO DEL AUSTRO  | 284 |
| COOP. AHO Y CRED SENOR DE GIRON | 285 |
| COOP. AHO Y CRED FAMILIA AUSTRAL | 286 |
| COOP. AHO Y CRED TUNGURAHUA LTDA. | 287 |
| COOP. AHO Y CRED LOS RIOS | 288 |
| COOP. AHO Y CRED SAN ANTONIO LTDA. | 289 |
| COOP 15 DE AGOSTO PILACOTO | 290 |
| COOP. DE AHO Y CRED CRISTO REY | 291 |
| COOP. AHO Y CRED EDUCADORES CHIMBORAZO | 292 |
| COOP AHO Y CRED MINGA LTDA. | 293 |
| COOP. AHO Y CRED 4 DE OCTUBRE LTDA. | 294 |
| COOP.AHO Y CRED CAMARA COMERCIO INDIGENA | 295 |
| COOP AHO Y CRED ALFONSO JARAMILLO | 296 |
| BANCO ASISTENCIA COMUNITARIA FINCA S.A. | 323 |
| COOP. AHO Y CRED 9 DE OCTUBRE LTDA | 325 |
| COOP. AHO Y CRED ACCION RURAL | 326 |
| COOP. AHO Y CRED SAN GABRIEL LTDA. | 328 |
| COOP.AHO Y CRED SAN MIGUEL DE LOS BANCOS | 330 |
| COOP. AHO Y CRED SEMILLA DEL PROGRESO LTDA | 332 |
| COOP.AHO Y CRED MUJERES UNIDAS TANTANAKUSHK | 333 |
| COOP. DE A. Y C. SANTA ROSA DE PATUTAN LTDA. | 334 |
| COOP  AHO Y CRED LLANGANATES | 348 |
| INTERDIN S.A. | 349 |
| COOP.AHO Y CREDITO PEQ.EMP.DE LOJA CACPE | 350 |
| COOP AHO Y CRED SAN PEDRO DE TABOADA | 401 |
| COOP AHO Y CRED PEQ EMPRESA GUALAQUIZA | 402 |
| COOP. AHO Y CRED MI TIERRA | 403 |
| COOP AHO Y CRED PEQ EMP CACPE YANZATZA | 404 |
| COOP AHO Y CRED FUNDESARROLLO  | 406 |
| COOP AHO Y CRED CONST COMERCIO Y PRODUCCION | 407 |
| COOP AHO Y CRED NUEVA HUANCAVILCA | 408 |
| COOP AHO Y CRED INTEGRAL | 409 |
| COOP AHO Y CRED ERCO LTDA | 410 |
| COOP  AHO Y CRED CAMARA COMER AMBATO | 411 |
| COOP AHO Y CRED MUSHUC RUNA LTDA | 412 |
| COOP AHO Y CRED EDUC DEL TUNGURAHUA | 413 |
| COOP AHO Y CRED AMBATO LTDA | 414 |
| COOP AHO Y CRED DORADO LTDA  | 415 |
| COOP AHO Y CRED NUESTROS ABUELOS LTDA | 416 |
| COOP AHO Y CRED ARTESANOS  LTDA | 417 |
| COOP AHO Y CRED SANTA ANITA LTDA  | 418 |
| COOP AHO Y CRED HUAYCO PUNGO LTDA | 419 |
| COOP. A.Y C. ESC.SUP.POLITEC. AGROP. DE MANABI MAN | 420 |
| COOP AHO Y CRED CARIAMANGA LTDA | 422 |
| COOP AHO Y CRED MARCABELI LTDA | 423 |
| COOP AHO Y CRED AGRICOLA JUNIN LTDA | 424 |
| COOP AHO Y CRED PUERTO LOPEZ LTDA | 425 |
| COOP AHO Y CRED CAM COM CANTON BOLIVAR | 426 |
| COOP AHO Y CRED NUEVA ESPERANZA | 427 |
| COOP AHO Y CRED SAN JORGE LTDA | 428 |
| COOP AHO Y CRED FERNANDO DAQUILEMA  | 429 |
| COOP AHO Y CRED LA MERCED | 557 |
| BANCO GENERAL RUMINAHUI | 42 |
| COOP. DE A. Y C. ESCENCIA INDIGENA LTDA. | 641 |
| COOP. AHORRO Y CREDITO MANANTIAL DE ORO LTDA. | 601 |
| COOP. DE AHORRO Y CREDITO ANDINA LTDA. | 642 |
| COOPERATIVA DE AHORRO Y CREDITO PILAHUIN | 643 |
| COOPERATIVA DE AHORRO Y CREDITO PUCARA LTDA. | 644 |
| COOP. DE A. Y C. SINCHI RUNA LTDA | 645 |
| COOP. DE AHORRO Y CREDITO SAN MIGUEL DE SIGCHOS | 646 |
| COOP. DE A. Y C. SIERRA CENTRO LTDA. | 647 |
| COOP. DE A. Y C. UNION MERCEDARIA LTDA. | 648 |
| COOP. AHORRO Y CREDITO DE LA CAMARA DE COMERCIO DE | 649 |
| COOP. DE A Y C GONZANAMA MIES | 650 |
| COOPERATIVA DE AHORRO Y CREDITO QUILANGA LTDA. | 651 |
| COOPERATIVA DE AHORRO Y CREDITO 27 DE ABRIL LOJA | 652 |
| COOP. DE AHORRO Y CREDITO CREDIAMIGO LTDA. LOJA MI | 653 |
| COOPERATIVA DE AHORRO Y CREDITO FORTUNA MIES | 654 |
| COOP. DE A. Y C. PROFESIONALES DEL VOLANTE UNION L | 655 |
| COOPERATIVA DE AHORRO Y CREDITO CACPE CELICA | 656 |
| COOPERATIVA DE AHORRO Y CREDITO CATAMAYO LTDA. MIE | 657 |
| COOP. DE A. Y C. DE LA PEQ. EMPRESA CACPE MACARA | 658 |
| COOP. AHO.Y CRED.NUEVOS HORIZONTES EL ORO LTDA. | 659 |
| COOP. DE A. Y C. 16 DE JUNIO | 660 |
| COOP. DE A. Y C. FUTURO Y PROGRESO DE GALAPAGOS LT | 661 |
| COOP. DE A. Y C. SUMAC LLACTA LTDA. | 662 |
| COOP. DE A. Y C. LUCHA CAMPESINA LTDA. | 663 |
| COOP. DE A. Y C. GUAMOTE LTDA. | 664 |
| COOP. A Y C DE LA PEQ. EMP. CACPE ZAMORA LTDA. | 602 |
| COOP. DE A. Y C. DESARROLLO INTEGRAL LTDA. | 603 |
| COOP. DE A. Y C. GRAMEEN AMAZONAS | 604 |
| COOP. DE A. Y C. DE LOS SERV. PUBL. DEL MIN. DE ED | 605 |
| COOP. DE A. Y C. 23 DE MAYO LTDA. | 606 |
| COOP.DE AHORRO Y CREDITO COCA LTDA | 607 |
| COOP. DE AHORRO Y CREDITO PILAHUIN TIO LTDA | 608 |
| COOP. DE AHORRO Y CREDITO HUAICANA LTDA | 609 |
| COOP. DE AHORRO Y CREDITO JADAN LTDA. MIES | 625 |
| COOPERATIVA DE AHORRO Y CREDITO HUINARA LTDA. MIES | 626 |
| COOPERATIVA DE AHORRO Y CREDITO EL CALVARIO LTDA. | 627 |
| COOP. DE AHORRO Y CREDITO CREDI FACIL LTDA. | 628 |
| COOP. DE A. Y C. VENCEDORES DE TUNGURAHUA | 629 |
| COOP. DE A. Y C. ECUAFUTURO LTDA. | 630 |
| COOP. DE A. Y C. MAQUITA CUSHUN LTDA. | 631 |
| COOP. DE A. Y C. VALLES DEL LIRIO | 632 |
| COOP. ESFUERZO UNIDO PARA EL DESARR. DEL CHILCO LA | 633 |
| COOP. A. Y C. CARROCEROS DE TUNGURAHUA | 634 |
| COOP. DE A. Y C. INKA KIPU LTDA. | 635 |
| COOP. DE A. Y C. ACCION TUNGURAHUA LTDA. | 636 |
| CCOP. DE A. Y C. SALASACA. | 637 |
| COOP. DE A. Y C. PIJAL | 640 |
| COOP. DE AHORRO Y CREDITO SIMIATUG LTDA | 639 |
| COOP. DE A Y C JUAN PIO DE MORA LTDA. | 638 |

