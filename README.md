# VO-TITULACIONS

# Índex

1. [Introducció](#1)
2. [Transmissions de dades disponibles](#2)
3. [Missatgeria dels serveis](#3)
   1. [3.1 Verificació de titulacions universitàries (TITOLS_UNIVERSITARIS)](#3.1)
      1. [3.1.1 Petició](#3.1.1)
      2. [3.1.2 Resposta – dades específiques](#3.1.2)
   2. [3.2 Verificació de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS)](#3.2)
      1. [3.2.1 Petició](#3.2.1)
      2. [3.2.2 Resposta – dades específiques](#3.2.2)
   3. [3.3 Llistat de titulacions universitàries (TITOLS_UNIVERSITARIS_LLISTAT)](#3.3)
      1. [3.3.1 Petició](#3.3.1)
      2. [3.3.2 Resposta – dades específiques](#3.3.2)
   4. [3.4 Llistat de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS_LLISTAT)](#3.4)
      1. [3.4.1 Petició](#3.4.1)
      2. [3.4.2 Resposta – dades específiques](#3.4.2)
   5. [3.5  Joc de proves](#3.5)


# 1 Introducció <a name="1"></a>

Aquest document detalla la missatgeria associada al servei de consulta de titulacions oficials del
Ministerio de Educación, Política Social y Deporte (MEPSYD en endavant).

Per poder realitzar la integració cal conèixer prèviament la següent documentació:
• [Document de Missatgeria Genèrica de la PCI del Consorci AOC.][PCI]
• [Excels amb les codificacions.][COD]

[PCI]:https://github.com/ConsorciAOC/PCI
[COD]: https://github.com/ConsorciAOC/VO-TITULACIONS/tree/main/documents

# 2 Transmissions de dades disponibles <a name="2"></a>

Les dades disponibles a través del servei són les que es presenten a continuació:

| **EMISSOR** |
| --- |
| MEPSYD(MinisteriodeEducación) |

| **PRODUCTE** | **MODALITAT** | **DESCRIPCIO** |
| --- | --- | --- |
| **MEPSYD** | TITOLS\_UNIVERSITARIS | Verificació de títols universitaris oficials del titular. |
| **MEPSYD** | TITOLS\_NO\_UNIVERSITARIS | Verificació de títols no universitaris oficials del titular. |
| **MEPSYD** | TITOLS\_UNIVERSITARIS\_LLISTAT | Llistat de títols universitaris oficials del titular. |
| **MEPSYD** | TITOLS\_NO\_UNIVERSITARIS\_LLISTAT | Llistat de títols no universitaris oficials del titular. |

Totes les consultes del producte tenen disponible la versió imprimible del resultat de la consulta en format PDF. Per més detalls adreceu-vos a l’apartat Extensions de missatgeria del document de missatgeria genèrica.

![image](https://user-images.githubusercontent.com/32306731/143427144-2b3a8c6b-b4b8-4c3d-bcc1-c9f76a65159c.png) L'emissor final garanteix la qualitat de les dades per a títols obtinguts a partir de 1999. Abans d'aquesta data no garanteix que estiguin totes les titulacions ni estudis realitzats.


# 3 Missatgeria dels serveis <a name="3"></a>

A continuació es detalla la missatgeria corresponent al bloc de dades específiques de les modalitats de consum del producte.

![image](https://user-images.githubusercontent.com/32306731/143427516-4f4960d3-6684-4d46-bca0-36d3d04008a6.png) L’emissor de les dades requereix que s’informin les dades del funcionari que realitza la consulta. Així, cal informar els següents camps de l’element Funcionario del bloc de dades genèriques:

/Peticion/Funcionario/NombreCompletoFuncionario, 
/Peticion/Funcionario/NifFuncionario, 
//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NombreCompletoFuncionario, 
//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NifFuncionario

## 3.1 Verificació de titulacions universitàries (TITOLS_UNIVERSITARIS) <a name="3.1"></a>

Aquesta modalitat permet obtenir els títols universitaris del ciutadà sobre el que es realitza la consulta.

   
### 3.1.1 Petició <a name="3.1.1"></a>

#### 3.1.1.1 Dades genèriques

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (DNI / NIF o NIE). En cas d'informar un NIE, el servei únicament respon a titulacions obtingudes al país. |
| //DatosGenericos/Titular/Documentacion | Documentació. |

#### 3.1.1.2 Dades específiques

Aquesta modalitat no requereix informar dades específiques.

### 3.1.2 Resposta – dades específiques <a name="3.1.2"></a>

De l’schema associat a la resposta especifica, el servei informa les dades que es detallen a continuació.

| _Element_ | _Descripció_ |
| --- | --- |
| /respostaVerificacioTitolsUniversitaris/titolsUniversitaris | Bloc de dades. Conté la informació dels títols del titular sobre el que es realitza la consulta. |
| //titolsUniversitaris/DatosTitular/FechaNacimiento | Data de naixement del titular sobre el que es realitza la consulta. El format s’ajustarà a DD/MM/AAAA, MM/AAAA o AAAA.. |
| //titolsUniversitaris/ListaTitulos/DatosTitulacion | Bloc de dades. Conté la informació d’un títol del titular sobre el que es realitza la consulta. |
| //DatosTitulacion/DatosCentro/Universidad | Universitat que va atorgar el títol universitari. |
| //DatosTitulacion/DatosCentro/Centro | Centre que va atorgar el títol universitari. |
| //DatosTitulacion/DatosTitulo/CodTitulacion | Codi de titulació. <ul><li>Per títols Pre Bolonia vegeu l'Excel [Estudios_universitarios_pre_Bolonia.xlsx][BO]</li><li>Per títols Bolonia vegeu https://www.educacion.gob.es/ruct/consultaestudios?actual=estudios</li><li>Per homologacions vegeu l'Excel [Titulaciones_homologaciones.xlsx][HOM]</li><li>Per títols de llibres manuscrits vegeu [Titulaciones_libros.xlsx][LIB]</li></ul> |
| //DatosTitulacion/DatosTitulo/NombreCarrera | Nom de la carrera de la que el titular poseeix el títol. |
| //DatosTitulacion/DatosTitulo/CodTipoTitulo | Codi de tipus de títol: <lu><li>0A - Especialista</li><li>0B - Diploma Post-grado</li><li>0C - Título Superior Extranjero (Acceso Doctorado)</li><li>0D - Título Profesional Superior Estatal(Acceso Doctor)</li><li>0E - Tit. o Estudio Equivalente a Título Universitario</li><li>0F - Título Profesional</li><li>0G - Máster</li><li>0H - Grado</li><li>0J - Equivalente a Tit. Ldo. (Títulos Eclesiásticos)</li><li>0K - Tít. o Est. equiv. Ldo.(Ens. Artíst.) Acce.Doctor</li><li>01 - Diplomado/Maestro</li><li>02 - Arquitecto Técnico</li><li>03 - Ingeniero Técnico</li><li>04 - Licenciado</li><li>05 - Arquitecto</li><li>06 - Ingeniero</li><li>07 - Doctor</li><li>08 - Estudios Extranjeros Homologados (Acceso Doctor)</li></lu> |
| //DatosTitulacion/DatosTitulo/TipoTitulo | Tipus de títol del titular. |
| //DatosTitulacion/DatosTitulo/FechaFinalizacion | Data de finalització dels estudis del títol associat. El format s’ajustarà a DD/MM/AAAA, MM/AAAA o AAAA. |
| //DatosTitulacion/DatosTitulo/FechaExpedicion | Data pagament de tases per expedició (DD/MM/AAAA). |
| //DatosTitulacion/DatosTitulo/CodPaisExpedicion | Codi del país d’expedició del títol (codificació ISO 3166-1, numèric). |
| //DatosTitulacion/DatosTitulo/PaisExpedicion | País d’expedició del títol. |
| //DatosTitulacion/DatosTitulo/NumTitulo | Número del títol. |
| //DatosTitulacion/DatosTitulo/RegistroUniv | Registre universitari (codi de registre). |
| //resultat/codiResultat | Codi de resultat de l’operació de consulta: <lu><li>0003: Tramitada. Titular localitzat.</li><li>0232: Error reportat per l’emissor. Existeix més d’un registre per les dades proporcionades en la consulta.</li><li>0233: Titular no identificat.</li><li>0238: No hi ha dades del titular consultat.</li><li>0502: Error en la comunicació amb l’emissor.</li></lu> |
| //resultat/descripcio | Descripció del resultat. |

[BO]: https://github.com/ConsorciAOC/VO-TITULACIONS/tree/main/documents
[HOM]: https://github.com/ConsorciAOC/VO-TITULACIONS/tree/main/documents
[LIB]: https://github.com/ConsorciAOC/VO-TITULACIONS/blob/main/documents/Titulaciones_libros.xls


![image](https://user-images.githubusercontent.com/32306731/143479045-465782a2-6a47-4bbc-b41c-f8dc6c4f4ec9.png)

## 3.2 Verificació de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS) <a name="3.2"></a>

Aquesta modalitat permet obtenir els títols no universitaris del ciutadà sobre el que es realitza la consulta.

### 3.2.1 Petició <a name="3.2.1"></a>

#### 3.2.1.1 Dades genèriques

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (DNI / NIF o NIE). En cas d'informar un NIE, el servei únicament respon a titulacions obtingudes al país. |
| //DatosGenericos/Titular/Documentacion | Documentació. |

#### 3.2.1.2 Dades específiques

Aquesta modalitat no requereix informar dades específiques.

### 3.2.2 Resposta – dades específiques <a name="3.2.2"></a>

![image](https://user-images.githubusercontent.com/32306731/143479316-6b89f029-c672-4004-a177-67c404ea2d73.png)


| _Element_ | _Descripció_ |
| --- | --- |
| /respostaVerificacioTitolsNoUniversitaris/titolsNoUniversitaris | Bloc de dades. Conté la informació dels títols del titular sobre el que es realitza la consulta. |
| //titolsNoUniversitaris/DatosTitular/LugarNacimiento/Pais | País de naixement del titular. |
| //titolsNoUniversitaris/DatosTitular/LugarNacimiento/Provincia | Província de naixement del titular. |
| //titolsNoUniversitaris/DatosTitular/LugarNacimiento/Localidad | Localitat de naixement del titular. |
| //titolsNoUniversitaris/DatosTitular/FechaNacimiento | Data de naixement del titular sobre el que es realitza la consulta. El format s’ajustarà a DD/MM/AAAA, MM/AAAA o AAAA. |
| //titolsUniversitaris/ListaTitulos/DatosTitulacion | Bloc de dades. Conté la informació d’un títol del titular sobre el que es realitza la consulta. |
| //DatosTitulacion/DatosCentro/Centro | Centre que va atorgar el títol. |
| //DatosTitulacion/DatosCentro/CodCentro | Codi del centre que va atorgar el títol. |
| //DatosTitulacion/DatosCentro/Provincia | Província del centre que va atorgar el títol. |
| //DatosTitulacion/DatosTitulo/CodTitulacion | Codi de la titulació obtinguda. Vegeu l'Excel [Codigos_titulacion_no_universitarios.xlsx.][NO_UNI] |
| //DatosTitulacion/DatosTitulo/Titulacion |Nom de la titulació obtinguda. |
| //DatosTitulacion/DatosTitulo/CodTipoTitulo | Codi del tipus de títol obtingut: <lu><li>01 - Certificat</li><li>02 - Títol</li><li>03 - Credencial</li></lu> |
| //DatosTitulacion/DatosTitulo/TipoTitulo | Tipus de títol del titular.. |
| //DatosTitulacion/DatosTitulo/TipoEstudio | Tipus d’estudis al que pertany el títol. |
| //DatosTitulacion/DatosTitulo/Nivel | Nivell del títol. |
| //DatosTitulacion/DatosTitulo/Ley | Llei en que es basa la legalitat del títol. |
| //DatosTitulacion/DatosTitulo/FechaFinalizacion | Data de finalització dels estudis del títol associat. El format s’ajustarà a DD/MM/AAAA, MM/AAAA o AAAA. |
| //DatosTitulacion/DatosTitulo/FechaExpedicion | Data d’expedició del títol associat. El format s’ajustarà a DD/MM/AAAA, MM/AAAA o AAAA. |
| //DatosTitulacion/DatosTitulo/CodPaisExpedicion | Codi del país d’expedició del títol (codificació ISO 3166-1, numèric). |
| //DatosTitulacion/DatosTitulo/PaisExpedicion | País d’expedició del títol. |
| //DatosTitulacion/DatosTitulo/NumRegistroNacional | Número de registre nacional. |
| //DatosTitulacion/DatosTitulo/NumRegistroAutonomico | Número de registre autonòmic. |
| //DatosTitulacion/DatosTitulo/NumRegistroMec | Número de registre assignat pel MEC. |
| //DatosTitulacion/DatosTitulo/Registro/NumOrdenLibro |Número d’ordre del llibre en el que figura el Registre Oficial. |
| //DatosTitulacion/DatosTitulo/Registro/NumLibro | Número del llibre en el que figura el Registre Oficial. |
| //DatosTitulacion/DatosTitulo/Registro/NumFolio |Número de foli del llibre en el que figura el Registre Oficial. |
| //resultat/codiResultat | Codi de resultat de l’operació de consulta: <lu><li>0003: Tramitada. Titular localitzat.</li><li>0232: Error reportat per l’emissor. Existeix més d’un registre per les dades proporcionades en la consulta.</li><li>0233: Titular no identificat.</li><li>0238: No hi ha dades del titular consultat.</li><li>0502: Error en la comunicació amb l’emissor.</li></lu> | 
| //resultat/descripcio | Descripció del resultat. |

[NO_UNI]:DDDDD

## 3.3 Llistat de titulacions universitàries (TITOLS_UNIVERSITARIS_LLISTAT) <a name="3.3"></a>

Aquesta modalitat permet obtenir el llistat de títols universitaris del titular de la consulta.

![image](https://user-images.githubusercontent.com/32306731/143844726-e66b5070-84b2-442c-85d4-98b1fd81cd0d.png) Aquesta modalitat NO permet la consulta per document identificador.

### 3.3.1 Petició <a name="3.3.1"></a>

#### 3.3.1.1 Dades genèriques

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (NIF o NIE). Cal informar-lo per complir l’schema de la missatgeria però no es té en compte a l’hora de fer la consulta. |
| //DatosGenericos/Titular/Documentacion | Documentació. Cal informar l’element sense valor per complir l’schema de la missatgeria però no es té en compte a l’hora de fer la consulta. |
| //DatosGenericos/Titular/Nombre | Nom del titular de la sol·licitud. |
| //DatosGenericos/Titular/Apellido1 | Primer cognom del titular de la sol·licitud |
| //DatosGenericos/Titular/Apellido2 | Segon cognom del titular de la sol·licitud. Opcional, en cas de no estar informat no s’envia a l’emissor final, altrament l’emissor valida que el segon cognom correspongui al titular. |

#### 3.3.1.2 Dades específiques

![image](https://user-images.githubusercontent.com/32306731/143844986-bac16a3f-7713-4df4-bcf2-149eea62011c.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /peticioLlistatTitolsUniversitaris//localitatNaixement | Localitat de naixement del titular consultat. |
| /peticioLlistatTitolsUniversitaris/dataNaixement | Data de naixement del titular consultat (DD/MM/AAAA). |
| /peticioLlistatTitolsUniversitaris/codiProvincia | Codi de província de naixement del titular consultat. La codificació utilitzada serà la codificació de l’INE (p.e. 43: Tarragona).. |
| /peticioLlistatTitolsUniversitaris/codiUniversitat | Codi de la universitat en la que s’ha cursat el títol. |
| /peticioLlistatTitolsUniversitaris/numeroTitol | Codi del títol a consultar. |

 
### 3.3.2 Resposta – dades específiques <a name="3.3.2"></a>

![image](https://user-images.githubusercontent.com/32306731/143854932-61c2b1a7-e706-4f67-8353-bb8cd40d1512.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /respostaLlistatTitolsUniversitarispeticioLlistatTitolsUniversitaris | Bloc de dades que conté la petició específica associada a la resposta. Per més detalls consulteu l’apartat anterior. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars | Bloc que conté les dades de la resposta amb el llistat de titulars. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars/titular | Bloc que conté les dades dels titulars. |
| //titular/dadesTitular | Bloc que conté les dades d’un titular. |
| //titular/dadesTitular/documentacio | Número de document del titular codificat en funció del tipus de ciutadà: <lu><li>NIF: 8 dígits + caràcter de control</li><li>NIE [X,Y,Z] + 7 dígits + caràcter de control</li></lu> |
| //titular/dadesTitular/nom | Nom del titular. |
| //titular/dadesTitular/cognom1 | Primer cognom del titular. |
| //titular/dadesTitular/cognom2 | Segon cognom del titular. |
| //titular/dadesTitular/dataNaixement | Data de naixement del titular (DD/MM/AAA). |
| //titular/dadesTitular/llocNaixement | Bloc que conté les dades del lloc de naixement del titular de la consulta. |
| //titular/dadesTitular/llocNaixement/pais | País de naixement del titular. |
| //titular/dadesTitular/llocNaixement/codiProvincia | Codi de província del titular. S’utilitzarà la codificació de l’INE (p.e. 43: Tarragona). |
| //titular/dadesTitular/llocNaixement/provincia | Província de naixement del titular. |
| //titular/dadesTitular/llocNaixement/municipi | Municipi de naixement del titular. |
| //titular/dadesTitular/llocNaixement/localitat | Localitat de naixement del titular. |
| //titular/dadesTitular/llistaTitols/dadesTitulacio | Bloc amb les dades sobre les titulacions del titular. |
| /respostaLlistatTitolsUniversitaris/resultat/codiResultat | CCodi de resultat de la consulta. Els valors possibles son: <lu><li>0003: Tramitada. Consulta realitzada correctament.</li><li>0232: Error reportat per l’emissor. Existeix més d’un registre per les dades proporcionades en la consulta.</li><li>0233: Titular no identificat.</li><li></li><li>0238: No hi ha dades del titular consultat.</li><li>0502: Error en la comunicació amb l’emissor.</li></lu> |
| /respostaLlistatTitolsUniversitaris/resultat/descripcio | Literal descriptiu del resultat de la consulta. |

#### 3.3.2.1 DadesTitulacio

![image](https://user-images.githubusercontent.com/32306731/143855842-5da15b5b-a099-4730-9606-be13074df70f.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //dadesTitulacio/dadesCentre | Bloc de dades que conté les dades del centre de la titulació. |
| //dadesCentre/codiUniversitat | Codi d’universitat on es va cursar el títol. |
| //dadesCentre/universitat | Nom de la universitat on es va cursar el títol. |
| //dadesCentre/codiCentre | Codi del centre on es va cursar el títol. |
| //dadesCentre/centre | Centre on es va cursar el títol. |
| //dadesCentre/codiProvincia | Codi de provincia on es va cursar el títol. S’utilitzarà la codificació de l’INE (p.e. 43: Tarragona). |
| //dadesCentre/provincia | Província on es va cursar el títol. |
| //dadesTitulacio/dadesTitol | Bloc de dades que conté les dades del títol. |
| //dadesTitol/codiTitulacio | Codi de la titulació cursada. |
| //dadesTitol/titulacio | Nom de la titulació. |
| //dadesTitol/codiTipusTitol | Codi del tipus de títol que posseeix el titular. |
| //dadesTitol/tipusTitol | Tipus de títol que posseeix el titular. |
| //dadesTitol/dataFinalitzacio | Data de finalització del títol (DD/MM/AAAA). |
| //dadesTitol/dataExpedicio | Data d’expedició del títol. Correspon a la data del pagament de les tases per a la expedició del títol (DD/MM/AAAA). |
| //dadesTitol/codiPaisExpedicio | Codi de país d’expedició del títol. Estarà codificat en ISO-3166-1 (numèric) |
| //dadesTitol/paisExpedicio | País d’expedició del títol. |
| //dadesTitol/numeroTitol | Número de títol. |
| //dadesTitol/registreUniversitari | Número de registre universitari del títol. |

## 3.4 Llistat de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS_LLISTAT) <a name="3.4"></a>

Aquesta modalitat permet obtenir el llistat de títols no universitaris del titular de la consulta.

![image](https://user-images.githubusercontent.com/32306731/143856281-ed85545e-d103-430d-96d9-f9d6d599baeb.png) Aquesta modalitat NO permet la consulta per document identificador.

### 3.4.1 Petició <a name="3.4.1"></a>

#### 3.4.1.1 Dades genèriques

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (NIF o NIE). Cal informar-lo per complir l’schema de la missatgeria però no es té en compte a l’hora de fer la consulta. |
| //DatosGenericos/Titular/Documentacion | Documentació. Cal informar l’element sense valor per complir l’schema de la missatgeria però no es té en compte a l’hora de fer la consulta. |
| //DatosGenericos/Titular/Nombre | Nom del titular de la sol·licitud. |
| //DatosGenericos/Titular/Apellido1 | Primer cognom del titular de la sol·licitud. |
| //DatosGenericos/Titular/Apellido2 | Segon cognom del titular de la sol·licitud. Opcional, en cas de no estar informat no s’envia a l’emissor final, altrament l’emissor valida que el segon cognom correspongui al titular. |

#### 3.4.1.2 Dades específiques 


![image](https://user-images.githubusercontent.com/32306731/143856653-a0b16efc-68eb-44c2-aadd-7c2c7e8a45a3.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /peticioLlistatTitolsUniversitaris//localitatNaixement | Localitat de naixement del titular consultat. |
| /peticioLlistatTitolsUniversitaris/dataNaixement | Data de naixement del titular consultat (DD/MM/AAAA). |
| /peticioLlistatTitolsUniversitaris/codiProvincia | Codi de província de naixement del titular consultat. La codificació utilitzada serà la codificació de l’INE (p.e. 43: Tarragona).. |
| /peticioLlistatTitolsUniversitaris/numeroTitol | Codi del títol a consultar. |

### 3.4.2 Resposta – dades específiques <a name="3.4.2"></a>

![image](https://user-images.githubusercontent.com/32306731/143856763-9b55800c-eaf6-4a61-9526-1d31b4381058.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /respostaLlistatTitolsUniversitarispeticioLlistatTitolsUniversitaris | Bloc de dades que conté la petició específica associada a la resposta. Per més detalls consulteu l’apartat anterior. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars | Bloc que conté les dades de la resposta amb el llistat de titulars. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars/titular | Bloc que conté les dades dels titulars. |
| //titular/dadesTitular | Bloc que conté les dades d’un titular. |
| //titular/dadesTitular/documentacio | Número de document del titular codificat en funció del tipus de ciutadà: <lu><li>NIF: 8 dígits + caràcter de control</li><li>NIE [X,Y,Z] + 7 dígits + caràcter de control</li></lu> |
| //titular/dadesTitular/nom | Nom del titular. |
| //titular/dadesTitular/cognom1 | Primer cognom del titular. |
| //titular/dadesTitular/cognom2 | Segon cognom del titular. |
| //titular/dadesTitular/dataNaixement | Data de naixement del titular. Format: DD/MM/AAAA |
| //titular/dadesTitular/llocNaixement | Bloc que conté les dades del lloc de naixement del titular de la consulta. |
| //titular/dadesTitular/llocNaixement/pais | País de naixement del titular. |
| //titular/dadesTitular/llocNaixement/codiProvincia | Codi de província del titular. S’utilitzarà la codificació de l’INE (p.e. 43: Tarragona). |
| //titular/dadesTitular/llocNaixement/provincia | Província de naixement del titular. |
| //titular/dadesTitular/llocNaixement/municipi | Municipi de naixement del titular. |
| //titular/dadesTitular/llocNaixement/localitat | Localitat de naixement del titular. |
| //titular/dadesTitular/llistaTitols/dadesTitulacio | Bloc amb les dades sobre les titulacions del titular. |
| /respostaLlistatTitolsUniversitaris/resultat/codiResultat | Codi de resultat de la consulta. Els valors possibles son: <lu><li>0003: Tramitada. Consulta realitzada correctament.</li><li>0231: document incorrecte</li><li>0232: Error reportat per l’emissor. Existeix més d’un registre per les dades proporcionades en la consulta.</li><li>0233: Titular no identificat.</li><li>0238: No hi ha dades del titular consultat.</li><li>0502: Error en la comunicació amb l’emissor.</li></lu> |
| /respostaLlistatTitolsUniversitaris/resultat/descripcio | Literal descriptiu del resultat de la consulta. |

#### 3.4.2.1 DadesTitulacio

![image](https://user-images.githubusercontent.com/32306731/143857447-23fc8cff-8a44-4db4-b561-6829b787bb7e.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //dadesTitulacio/dadesCentre | Bloc de dades que conté les dades del centre de la titulació. |
| //dadesCentre/codiCentre | Codi del centre on es va cursar el títol. |
| //dadesCentre/centre | Centre on es va cursar el títol. |
| //dadesCentre/codiProvincia | Codi de provincia on es va cursar el títol. S’utilitzarà la codificació de l’INE (p.e. 43: Tarragona). |
| //dadesCentre/provincia | Província on es va cursar el títol. |
| //dadesTitulacio/dadesTitol | Bloc de dades que conté les dades del títol. |
| //dadesTitol/codiTitulacio | Codi de la titulació cursada. |
| //dadesTitol/titulacio | Nom de la titulació. |
| //dadesTitol/codiTipusTitol | Codi del tipus de títol que posseeix el titular. |
| //dadesTitol/tipusTitol | Tipus de títol que posseeix el titular. |
| //dadesTitol/tipusEstudi | Tipus d’estudi al que pertany el títol. Els valors poden ser: <lu><li>LGE</li><li>ANTLGE</li><li>LOE</li><li>LOGSE</li></lu> |
| //dadesTitol/nivell | Nivell del títol |
| //dadesTitol/dataFinalitzacio | Data de finalització del títol (DD/MM/AAAA) |
| //dadesTitol/dataExpedicio | Data d’expedició del títol. Correspon a la data del pagament de les tases per a la expedició del títol. (DD/MM/AAAA) |
| //dadesTitol/codiPaisExpedicio | Codi de país d’expedició del títol. Estarà codificat en ISO-3166-1 (numèric) |
| //dadesTitol/paisExpedicio | País d’expedició del títol. |
| //dadesTitol/numeroRegistreAutonomic | Número del registre autonòmic del títol. |
| //dadesTitol/numeroRegistreMec | Número de registre assignat pel Ministerio de Educación. |
| //dadesTitol/registre | Bloc que conté les dades del registre de la titulació. |
| //dadesTitol/registre/numeroOrdreLlibre | Número d’ordre del llibre en el que es troba el registre oficial. |
| //dadesTitol/registre/numeroLlibre | Número del llibre en el que es troba el registre oficial. |
| //dadesTitol/registre/numeroFoli | Número de foli (del llibre) en el que es troba el registre oficial. |


## 3.5  Joc de proves <a name="3.5"></a>

L'emissor final publica els següent [joc de proves a l'entorn de pre-producció][proves]
 
[proves]: https://administracionelectronica.gob.es/ctt/svd/descargas#.Ysa2dnbP0uV
 
![image](https://user-images.githubusercontent.com/32306731/137281698-9dfc2044-94f7-487f-a7d6-9a4e0707feb3.png) En cas de tindre problemes per accedir als jocs de proves, si us plau, obre un tiquet a través del [formulari][form]
 
[form]:https://www.aoc.cat/portal-suport/peticio-integradors/idservei/integracio/