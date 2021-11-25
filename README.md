# VO-TITULACIONS

# Índex

1. [Introducció](#1)
2. [Transmissions de dades disponibles](#2)
3. [Missatgeria dels serveis](#3)
   1. [3.1 Verificació de titulacions universitàries (TITOLS_UNIVERSITARIS)](#3.1)
      1. [3.1.1 Petició](#3.1.1)
      2. [3.1.2 Resposta – dades específiques](#3.1.2)
   2. [3.2 Verificació de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS)](#3.2)
      1. [3.2.1 Petició – dades específiques](#3.2.1)
      2. [3.2.2 Resposta – dades específiques](#3.2.2)
   3. [3.3 Llistat de titulacions universitàries (TITOLS_UNIVERSITARIS_LLISTAT)](#3.3)
      1. [3.3.1 Petició](#3.3.1)
      2. [3.3.2 Resposta – dades específiques](#3.3.2)
   4. [3.4 Llistat de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS_LLISTAT)](#3.1)
      1. [3.4.1 Petició](#3.4.1)
      2. [3.4.2 Resposta – dades específiques](#3.4.2)


# 1 Introducció <a name="1"></a>

Aquest document detalla la missatgeria associada al servei de consulta de titulacions oficials del
Ministerio de Educación, Política Social y Deporte (MEPSYD en endavant).

Per poder realitzar la integració cal conèixer prèviament la següent documentació:
•	Document d’Especificació de missatgeria pel consum de productes de la plataforma PCI del Consorci AOC.
•	Excels amb les codificacions (DI - Via Oberta - TITULACIONS-excels codificacions.zip).



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
| //DatosTitulacion/DatosTitulo/CodTitulacion | Codi de titulació. <ul><li>Per títols Pre Bolonia vegeu l'Excel Estudios_universitarios_pre_Bolonia.xlsx</li><li>Per títols Bolonia vegeu https://www.educacion.gob.es/ruct/consultaestudios?actual=estudios</li><li>Per homologacions vegeu l'Excel Titulaciones_homologaciones.xlsx</li><li>Per títols de llibres manuscrits vegeu Titulaciones_libros.xlsx</li></ul> |
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

![image](https://user-images.githubusercontent.com/32306731/143479045-465782a2-6a47-4bbc-b41c-f8dc6c4f4ec9.png)

## 3.2 Verificació de titulacions no universitàries (TITOLS_NO_UNIVERSITARIS) <a name="3.2"></a>

Aquesta modalitat permet obtenir els títols no universitaris del ciutadà sobre el que es realitza la consulta.

### 3.2.1 Petició

#### 3.2.1.1 Dades genèriques

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (DNI / NIF o NIE). En cas d'informar un NIE, el servei únicament respon a titulacions obtingudes al país. |
| //DatosGenericos/Titular/Documentacion | Documentació. |

#### 3.2.1.2 Dades específiques

Aquesta modalitat no requereix informar dades específiques.

### 3.2.2 Resposta – dades específiques

![image](https://user-images.githubusercontent.com/32306731/143479316-6b89f029-c672-4004-a177-67c404ea2d73.png)


-------------------------- SEGUIR A PARTIR D'AQUI


| _Element_ | _Descripció_ |
| --- | --- |
| /respostaVerificacioTitolsNoUniversitaris/titolsNoUniversitaris | Blocdedades.Contélainformaciódelstítolsdeltitularsobreelqueesrealitzalaconsulta. |
| //titolsNoUniversitaris/DatosTitular/LugarNacimiento/Pais | Paísdenaixementdeltitular. |
| //titolsNoUniversitaris/DatosTitular/LugarNacimiento/Provincia | Provínciadenaixementdeltitular. |
| //titolsNoUniversitaris/DatosTitular/LugarNacimiento/Localidad | Localitatdenaixementdeltitular. |
| //titolsNoUniversitaris/DatosTitular/FechaNacimiento | Datadenaixementdeltitularsobreelqueesrealitza la consulta. El format s&#39;ajustarà aDD/MM/AAAA,MM/AAAA o AAAA. |
| //titolsUniversitaris/ListaTitulos/DatosTitulacion | Blocdedades.Contélainformaciód&#39;untítoldeltitularsobreelqueesrealitzalaconsulta. |
| //DatosTitulacion/DatosCentro/Centro | Centrequevaatorgareltítol. |

| _Element_ | _Descripció_ |
| --- | --- |
|
 |
 |
| //DatosTitulacion/DatosCentro/CodCentro | Codidelcentrequevaatorgareltítol. |
| //DatosTitulacion/DatosCentro/Provincia | Provínciadelcentrequevaatorgareltítol. |
| //DatosTitulacion/DatosTitulo/CodTitulacion | Codidelatitulacióobtinguda. Vegeul&#39;Excel_Codigos\_titulacion\_no\_universitarios.xlsx_. |
| //DatosTitulacion/DatosTitulo/Titulacion | Nomdela titulacióobtinguda. |
| //DatosTitulacion/DatosTitulo/CodTipoTitulo | Codideltipusdetítolobtingut:

- 01 -Certificat
- 02 -Títol
- 03-Credencial
 |
| //DatosTitulacion/DatosTitulo/TipoTitulo | Tipusdetítoldeltitular. |
| //DatosTitulacion/DatosTitulo/TipoEstudio | Tipusd&#39;estudis alquepertanyeltítol. |
| //DatosTitulacion/DatosTitulo/Nivel | Nivelldeltítol. |
| //DatosTitulacion/DatosTitulo/Ley | Lleienquees basalalegalitatdeltítol. |
| //DatosTitulacion/DatosTitulo/FechaFinalizacion | Data de finalització dels estudis del títolassociat.Elformats&#39;ajustaràaDD/MM/AAAA,MM/AAAAoAAAA. |
| //DatosTitulacion/DatosTitulo/FechaExpedicion | Data d&#39;expedició del títol associat. El formats&#39;ajustaràaDD/MM/AAAA, MM/AAAAoAAAA. |
| //DatosTitulacion/DatosTitulo/CodPaisExpedicion | Codidelpaísd&#39;expediciódeltítol(codificacióISO3166-1, numèric). |
| //DatosTitulacion/DatosTitulo/PaisExpedicion | Paísd&#39;expediciódeltítol. |
| //DatosTitulacion/DatosTitulo/NumRegistroNacional | Númeroderegistrenacional. |
| //DatosTitulacion/DatosTitulo/NumRegistroAutonomico | Númeroderegistreautonòmic. |
| //DatosTitulacion/DatosTitulo/NumRegistroMec | NúmeroderegistreassignatpelMEC. |
| //DatosTitulacion/DatosTitulo/Registro/NumOrdenLibro | Número d&#39;ordre del llibre en el que figura elRegistreOficial. |
| //DatosTitulacion/DatosTitulo/Registro/NumLibro | Número del llibre en el que figura el RegistreOficial. |
| //DatosTitulacion/DatosTitulo/Registro/NumFolio | Númerodefolidelllibreen elquefiguraelRegistreOficial. |
| //resultat/codiResultat | Codideresultatdel&#39;operaciódeconsulta:
- 0003:Tramitada.Titularlocalitzat.
- 0232:Errorreportatperl&#39;emissor.Existeixmésd&#39;unregistreperles
 |

| _Element_ | _Descripció_ |
| --- | --- |
|
 | dadesproporcionadesenlaconsulta.
- 0233:Titularnoidentificat.
- 0238:Nohihadadesdeltitularconsultat.
- 0502:Errorenlacomunicacióambl&#39;emissor.
 |
| //resultat/descripcio | Descripciódelresultat. |

  1. **Llistat**** de ****titulacions**** universitàries****(****TITOLS\_UNIVERSITARIS\_LLISTAT****)**

Aquestamodalitat permetobtenirelllistatde títolsuniversitarisdeltitulardelaconsulta.

| ![](RackMultipart20211123-4-1fg42x4_html_2510d52f0494e7cf.png) | AquestamodalitatNO permetlaconsultaper documentidentificador. |
| --- | --- |

    1.
### Petició

      1. **Dades**** genèriques**

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (NIF o NIE). Calinformar-lo per complir l&#39;schema de lamissatgeriaperònoestéencompteal&#39;horadeferlaconsulta. |
| //DatosGenericos/Titular/Documentacion | Documentació.Calinformarl&#39;elementsensevalor per complir l&#39;schema de la missatgeriaperò no es té en compte a l&#39;hora de fer laconsulta. |
| //DatosGenericos/Titular/Nombre | Nomdeltitularde lasol·licitud. |
| //DatosGenericos/Titular/Apellido1 | Primercognomdeltitulardelasol·licitud |
| //DatosGenericos/Titular/Apellido2 | Segon cognom del titular de la sol·licitud.Opcional,encasdenoestarinformatnos&#39;enviaa l&#39;emissor final, altrament l&#39;emissor valida queelsegoncognomcorresponguialtitular. |

      1. **Dades**** específiques**

![](RackMultipart20211123-4-1fg42x4_html_a58ab065b9f5c8e.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /peticioLlistatTitolsUniversitaris//localitatNaixement | Localitatdenaixementdeltitularconsultat. |
| /peticioLlistatTitolsUniversitaris/dataNaixement | Data de naixement del titular consultat(DD/MM/AAAA). |
| /peticioLlistatTitolsUniversitaris/codiProvincia | Codi de província de naixement del titularconsultat. La codificació utilitzada serà lacodificaciódel&#39;INE(p.e.43:Tarragona).. |
| /peticioLlistatTitolsUniversitaris/codiUniversitat | Codidelauniversitatenlaques&#39;hacursateltítol. |
| /peticioLlistatTitolsUniversitaris/numeroTitol | Codideltítolaconsultar. |

    1.
### Resposta –dadesespecífiques

![](RackMultipart20211123-4-1fg42x4_html_f04018710ddc7342.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /respostaLlistatTitolsUniversitarispeticioLlistatTitolsUniversitaris | Bloc de dades que conté la peticióespecíficaassociadaalaresposta.Per |

| _Element_ | _Descripció_ |
| --- | --- |
|
 | mésdetallsconsulteul&#39;apartatanterior. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars | Blocquecontélesdadesdelarespostaambelllistatdetitulars. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars/titular | Blocquecontéles dadesdelstitulars. |
| //titular/dadesTitular | Blocquecontélesdadesd&#39;untitular |
| //titular/dadesTitular/documentacio | Númerodedocumentdeltitularcodificatenfunciódeltipus deciutadà:
- NIF:8dígits+caràcterde control
- NIE[X,Y,Z]+7dígits+caràcterdecontrol
 |
| //titular/dadesTitular/nom | Nomdeltitular. |
| //titular/dadesTitular/cognom1 | Primercognomdeltitular. |
| //titular/dadesTitular/cognom2 | Segoncognomdeltitular. |
| //titular/dadesTitular/dataNaixement | Data de naixement del titular(DD/MM/AAA). |
| //titular/dadesTitular/llocNaixement | Blocquecontélesdadesdelllocdenaixementdeltitulardelaconsulta. |
| //titular/dadesTitular/llocNaixement/pais | Paísdenaixementdeltitular. |
| //titular/dadesTitular/llocNaixement/codiProvincia | Codi de província del titular. S&#39;utilitzarà lacodificaciódel&#39;INE(p.e.43:Tarragona). |
| //titular/dadesTitular/llocNaixement/provincia | Provínciadenaixementdeltitular. |
| //titular/dadesTitular/llocNaixement/municipi | Municipidenaixementdeltitular. |
| //titular/dadesTitular/llocNaixement/localitat | Localitatdenaixementdeltitular. |
| //titular/dadesTitular/llistaTitols/dadesTitulacio | Blocamblesdadessobrelestitulacionsdeltitular. |
| /respostaLlistatTitolsUniversitaris/resultat/codiResultat | Codi de resultat de la consulta. Els valorspossiblesson:
- 0003: Tramitada. Consultarealitzadacorrectament.
- 0232:Errorreportatperl&#39;emissor.Existeixmésd&#39;unregistreperlesdadesproporcionadesenlaconsulta.
- 0233:Titularnoidentificat.
- 0238:Nohihadadesdeltitularconsultat.
- 0502:Errorenlacomunicacióamb
 |

| _Element_ | _Descripció_ |
| --- | --- |
|
 | l&#39;emissor. |
| /respostaLlistatTitolsUniversitaris/resultat/descripcio | Literaldescriptiudelresultatdelaconsulta. |

      1. **DadesTitulacio**

![](RackMultipart20211123-4-1fg42x4_html_e8ab090f02b96883.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //dadesTitulacio/dadesCentre | Blocdedadesquecontélesdadesdelcentredelatitulació. |
| //dadesCentre/codiUniversitat | Codid&#39;universitatonesva cursareltítol. |
| //dadesCentre/universitat | Nomdelauniversitatonesvacursareltítol. |
| //dadesCentre/codiCentre | Codidelcentreon esvacursareltítol. |
| //dadesCentre/centre | Centreonesvacursareltítol. |
| //dadesCentre/codiProvincia | Codideprovinciaones vacursareltítol.S&#39;utilitzaràlacodificació del&#39;INE(p.e.43:Tarragona). |
| //dadesCentre/provincia | Provínciaon esvacursareltítol. |
| //dadesTitulacio/dadesTitol | Blocdedadesquecontélesdadesdeltítol. |
| //dadesTitol/codiTitulacio | Codidela titulaciócursada. |

| _Element_ | _Descripció_ |
| --- | --- |
|
 |
 |
| //dadesTitol/titulacio | Nomdelatitulació. |
| //dadesTitol/codiTipusTitol | Codideltipusdetítolqueposseeixeltitular. |
| //dadesTitol/tipusTitol | Tipusdetítolqueposseeixeltitular. |
| //dadesTitol/dataFinalitzacio | Datadefinalitzaciódeltítol(DD/MM/AAAA). |
| //dadesTitol/dataExpedicio | Data d&#39;expedició del títol. Correspon a la data del pagamentdeles tases peralaexpediciódeltítol (DD/MM/AAAA). |
| //dadesTitol/codiPaisExpedicio | Codidepaísd&#39;expediciódeltítol.EstaràcodificatenISO-3166-1(numèric) |
| //dadesTitol/paisExpedicio | Paísd&#39;expediciódeltítol. |
| //dadesTitol/numeroTitol | Númerodetítol. |
| //dadesTitol/registreUniversitari | Númeroderegistreuniversitarideltítol. |

  1.
## Llistat de titulacions no universitàries

### (TITOLS\_NO\_UNIVERSITARIS\_LLISTAT)

Aquestamodalitat permetobtenirelllistatdetítolsnouniversitarisdeltitulardelaconsulta.

| ![](RackMultipart20211123-4-1fg42x4_html_2510d52f0494e7cf.png) | AquestamodalitatNO permetlaconsultaper documentidentificador. |
| --- | --- |

    1.
### Petició

      1. **Dades**** genèriques**

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (NIF o NIE). Calinformar-lo per complir l&#39;schema de lamissatgeriaperònoestéencompteal&#39;horadeferlaconsulta. |
| //DatosGenericos/Titular/Documentacion | Documentació.Calinformarl&#39;elementsensevalor per complir l&#39;schema de la missatgeriaperò no es té en compte a l&#39;hora de fer laconsulta. |
| //DatosGenericos/Titular/Nombre | Nomdeltitularde lasol·licitud. |
| //DatosGenericos/Titular/Apellido1 | Primercognomdeltitulardelasol·licitud. |
| //DatosGenericos/Titular/Apellido2 | Segon cognom del titular de la sol·licitud.Opcional,encasdenoestarinformatnos&#39;envia |

| _Element_ | _Descripció_ |
| --- | --- |
|
 | al&#39;emissorfinal,altramentl&#39;emissorvalidaqueelsegoncognomcorresponguialtitular. |

      1. **Dades**** específiques**

![](RackMultipart20211123-4-1fg42x4_html_7d6fc21295a467d9.png)

| _Element_ | _Descripció_ |
| --- | --- |
| /peticioLlistatTitolsUniversitaris//localitatNaixement | Localitatdenaixementdeltitularconsultat. |
| /peticioLlistatTitolsUniversitaris/dataNaixement | Data de naixement del titular consultat(DD/MM/AAAA). |
| /peticioLlistatTitolsUniversitaris/codiProvincia | Codi de província de naixement del titularconsultat. La codificació utilitzada serà lacodificaciódel&#39;INE(p.e.43:Tarragona).. |
| /peticioLlistatTitolsUniversitaris/numeroTitol | Codideltítolaconsultar. |

    1.
### Resposta –dadesespecífiques

![](RackMultipart20211123-4-1fg42x4_html_1e1578644a7bc935.png)

| _Element_ | _Descripció_ |
| --- | --- |

| _Element_ | _Descripció_ |
| --- | --- |
| /respostaLlistatTitolsUniversitarispeticioLlistatTitolsUniversitaris | Bloc de dades que conté la peticióespecíficaassociadaalaresposta.Permésdetallsconsulteul&#39;apartatanterior. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars | Blocquecontélesdadesdelarespostaambelllistatdetitulars. |
| /respostaLlistatTitolsUniversitaris/llistaTitulars/titular | Blocquecontéles dadesdelstitulars. |
| //titular/dadesTitular | Blocquecontélesdadesd&#39;untitular |
| //titular/dadesTitular/documentacio | Númerodedocumentdeltitularcodificatenfunciódeltipus deciutadà:
- NIF:8dígits+caràcterde control
- NIE[X,Y,Z]+7dígits+caràcterdecontrol
 |
| //titular/dadesTitular/nom | Nomdeltitular. |
| //titular/dadesTitular/cognom1 | Primercognomdeltitular. |
| //titular/dadesTitular/cognom2 | Segoncognomdeltitular. |
| //titular/dadesTitular/dataNaixement | Datadenaixementdeltitular.Format:DD/MM/AAAA |
| //titular/dadesTitular/llocNaixement | Blocquecontélesdadesdelllocdenaixementdeltitulardelaconsulta. |
| //titular/dadesTitular/llocNaixement/pais | Paísdenaixementdeltitular. |
| //titular/dadesTitular/llocNaixement/codiProvincia | Codideprovínciadeltitular.S&#39;utilitzaràlacodificaciódel&#39;INE(p.e.43:Tarragona). |
| //titular/dadesTitular/llocNaixement/provincia | Provínciadenaixementdeltitular. |
| //titular/dadesTitular/llocNaixement/municipi | Municipidenaixementdeltitular. |
| //titular/dadesTitular/llocNaixement/localitat | Localitatdenaixementdeltitular. |
| //titular/dadesTitular/llistaTitols/dadesTitulacio | Blocamb les dades sobreles titulacionsdeltitular. |
| /respostaLlistatTitolsUniversitaris/resultat/codiResultat | Codi de resultat de la consulta. Els valorspossiblesson:
- 0003: Tramitada. Consultarealitzadacorrectament.
- 0231:documentincorrecte
- 0232:Errorreportatperl&#39;emissor.Existeixmésd&#39;unregistreperlesdadesproporcionadesenlaconsulta.
- 0233:Titularnoidentificat.
 |

| _Element_ | _Descripció_ |
| --- | --- |
|
 |
- 0238:Nohihadadesdeltitularconsultat.
- 0502:Errorenlacomunicacióambl&#39;emissor.
 |
| /respostaLlistatTitolsUniversitaris/resultat/descripcio | Literaldescriptiudelresultatdelaconsulta. |

      1. **DadesTitulacio**

![](RackMultipart20211123-4-1fg42x4_html_f24d8358cd06e5f0.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //dadesTitulacio/dadesCentre | Blocdedadesquecontélesdadesdelcentredelatitulació. |
| //dadesCentre/codiCentre | Codidelcentreon esvacursareltítol. |
| //dadesCentre/centre | Centreonesvacursareltítol. |
| //dadesCentre/codiProvincia | Codideprovinciaonesvacursareltítol.S&#39;utilitzaràlacodificació del&#39;INE(p.e.43:Tarragona). |

| _Element_ | _Descripció_ |
| --- | --- |
| //dadesCentre/provincia | Provínciaon esvacursareltítol. |
| //dadesTitulacio/dadesTitol | Blocdedadesquecontélesdadesdeltítol. |
| //dadesTitol/codiTitulacio | Codidela titulaciócursada. |
| //dadesTitol/titulacio | Nomdelatitulació. |
| //dadesTitol/codiTipusTitol | Codideltipusdetítolqueposseeixeltitular. |
| //dadesTitol/tipusTitol | Tipusdetítolqueposseeixeltitular. |
| //dadesTitol/tipusEstudi | Tipusd&#39;estudialquepertanyeltítol.Elsvalorspodenser:
- LGE
- ANTLGE
- LOE
- LOGSE
 |
| //dadesTitol/nivell | Nivelldeltítol |
| //dadesTitol/dataFinalitzacio | Datadefinalitzaciódeltítol(DD/MM/AAAA) |
| //dadesTitol/dataExpedicio | Data d&#39;expedició del títol. Correspon a la data delpagamentdelestasesper alaexpediciódeltítol.(DD/MM/AAAA) |
| //dadesTitol/codiPaisExpedicio | Codidepaísd&#39;expediciódeltítol.EstaràcodificatenISO-3166-1(numèric) |
| //dadesTitol/paisExpedicio | Paísd&#39;expediciódeltítol. |
| //dadesTitol/numeroRegistreAutonomic | Númerodelregistreautonòmicdeltítol. |
| //dadesTitol/numeroRegistreMec | NúmeroderegistreassignatpelMinisteriodeEducación. |
| //dadesTitol/registre | Bloc quecontélesdadesdelregistredelatitulació. |
| //dadesTitol/registre/numeroOrdreLlibre | Númerod&#39;ordredelllibreenelqueestrobaelregistreoficial. |
| //dadesTitol/registre/numeroLlibre | Númerodelllibreenelqueestroba elregistre oficial. |
| //dadesTitol/registre/numeroFoli | Númerodefoli(delllibre)enel queestrobaelregistreoficial. |
