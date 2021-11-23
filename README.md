# VO-TITULACIONS

# Índex

1. [Introducció 1](#_bookmark0)
2. [Transmissionsdedades disponibles 1](#_bookmark1)
3. [Missatgeria dels serveis 1](#_bookmark2)
  1. [Verificació de titulacionsuniversitàries(TITOLS\_UNIVERSITARIS) 2](#_bookmark3)
    1. [Petició 2](#_bookmark4)
    2. [Resposta–dades específiques 2](#_bookmark5)
  2. [Verificació de titulacionsnouniversitàries(TITOLS\_NO\_UNIVERSITARIS) 4](#_bookmark6)
    1. [Petició 4](#_bookmark7)
    2. [Resposta–dades específiques 5](#_bookmark8)
  3. [Llistatdetitulacionsuniversitàries (TITOLS\_UNIVERSITARIS\_LLISTAT) 7](#_bookmark9)
    1. [Petició 7](#_bookmark10)
    2. [Resposta–dades específiques 8](#_bookmark11)
  4. [Llistatdetitulacionsno universitàries(TITOLS\_NO\_UNIVERSITARIS\_LLISTAT) 11](#_bookmark12)
    1. [Petició 11](#_bookmark13)
    2. [Resposta–dades específiques 12](#_bookmark14)


# Introducció

Aquest document detalla la missatgeria associada al servei de consulta de titulacions oficials del
Ministerio de Educación, Política Social y Deporte (MEPSYD en endavant).

Per poder realitzar la integració cal conèixer prèviament la següent documentació:
•	Document d’Especificació de missatgeria pel consum de productes de la plataforma PCI del Consorci AOC.
•	Excels amb les codificacions (DI - Via Oberta - TITULACIONS-excels codificacions.zip).



# Transmissions de dades disponibles

Les dades disponibles a través del servei són les que es presenten a continuació:

| **EMISSOR** |
| --- |
| MEPSYD(MinisteriodeEducación) |
| **PRODUCTE** | **MODALITAT** | **DESCRIPCIO** |
| **MEPSYD** | TITOLS\_UNIVERSITARIS | Verificaciódetítolsuniversitarisoficialsdeltitular. |
| TITOLS\_NO\_UNIVERSITARIS | Verificaciódetítolsnouniversitarisoficialsdeltitular. |
| TITOLS\_UNIVERSITARIS\_LLISTAT | Llistatdetítolsuniversitarisoficialsdeltitular. |
| TITOLS\_NO\_UNIVERSITARIS\_LLISTAT | Llistat de títols no universitaris oficials deltitular. |

Totes les consultes del producte tenen disponible la versió imprimible del resultat de la consulta en format PDF. Per més detalls adreceu-vos a l’apartat Extensions de missatgeria del document de missatgeria genèrica.

| ![](RackMultipart20211123-4-1fg42x4_html_2510d52f0494e7cf.png) | L&#39;emissorfinalgaranteixlaqualitatdelesdadesperatítolsobtingutsapartirde1999.Abansd&#39;aquesta datanogaranteixqueestiguintotes lestitulacionsniestudisrealitzats. |
| --- | --- |

1.
# Missatgeriadelsserveis

Acontinuacióesdetallalamissatgeriacorresponentalblocdedadesespecífiquesdelesmodalitatsdeconsumdel producte.

| ![](RackMultipart20211123-4-1fg42x4_html_2510d52f0494e7cf.png) | L&#39;emissor de lesdadesrequereixque s&#39;informin lesdadesdel funcionari que realitza la consulta.Així,calinformar elssegüentscampsdel&#39;elementFuncionariodelblocdedadesgenèriques:
/Peticion/Funcionario/NombreCompletoFuncionario,/Peticion/Funcionario/NifFuncionario,//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NombreCompletoFuncionarioi |
 |
| --- | --- | --- |

![Shape32](RackMultipart20211123-4-1fg42x4_html_8cf6ba18ff8d8c39.gif)

  1. **Verificació**** de ****titulacions**** universitàries****(TITOLS\_UNIVERSITARIS****)**

Aquestamodalitat permetobtenirelstítolsuniversitarisdelciutadàsobreelqueesrealitzalaconsulta.

    1.
### Petició

      1. **Dades**** genèriques**

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (DNI / NIF o NIE). Encas d&#39;informar un NIE, el servei únicamentrespona titulacionsobtingudesalpaís. |
| //DatosGenericos/Titular/Documentacion | Documentació. |

      1. **Dades**** específiques**

Aquestamodalitatnorequereixinformardadesespecífiques.

    1.
### Resposta –dadesespecífiques

Del&#39;_schema_associatalarespostaespecifica,elserveiinformalesdadesqueesdetallenacontinuació.

| _Element_ | _Descripció_ |
| --- | --- |
| /respostaVerificacioTitolsUniversitaris/titolsUniversitaris | Blocdedades.Contélainformaciódelstítolsdeltitularsobreelque es realitzala consulta. |
| //titolsUniversitaris/DatosTitular/FechaNacimiento | Datadenaixementdeltitularsobreelquees realitzala consulta. El format s&#39;ajustarà a DD/MM/AAAA,MM/AAAAoAAAA. |
| //titolsUniversitaris/ListaTitulos/DatosTitulacion | Blocdedades.Contélainformaciód&#39;untítoldeltitularsobreel quees realitzalaconsulta. |
| //DatosTitulacion/DatosCentro/Universidad | Universitatquevaatorgareltítoluniversitari. |
| //DatosTitulacion/DatosCentro/Centro | Centrequevaatorgareltítoluniversitari. |
| //DatosTitulacion/DatosTitulo/CodTitulacion | Codidetitulació.

- PertítolsPreBoloniavegeul&#39;Excel
_Estudios\_universitarios\_pre\_Bolonia.xlsx_

- PertítolsBolonia vegeu[https://www.educacion.gob.es/ruct/consultaestud](https://www.educacion.gob.es/ruct/consultaestudios?actual=estudios)[ios?actual=estudios](https://www.educacion.gob.es/ruct/consultaestudios?actual=estudios)
 |

| _Element_ | _Descripció_ |
| --- | --- |
|
 |
- Perhomologacionsvegeul&#39;Excel
_Titulaciones\_homologaciones.xlsx_

- Pertítolsdellibresmanuscritsvegeu
_Titulaciones\_libros.xlsx_ |
| //DatosTitulacion/DatosTitulo/NombreCarrera | Nom delacarreradelaqueeltitular poseeixel títol. |
| //DatosTitulacion/DatosTitulo/CodTipoTitulo | Codidetipusde títol:

- 0A-Especialista
- 0B-DiplomaPost-grado
- 0C - Título Superior Extranjero (AccesoDoctorado)
- 0D - Título Profesional Superior Estatal(AccesoDoctor)
- 0E - Tit. o Estudio Equivalente a TítuloUniversitario
- 0F-TítuloProfesional
- 0G-Máster
- 0H- Grado
- 0J-EquivalenteaTit.Ldo.(TítulosEclesiásticos)
- 0K - Tít. o Est. equiv. Ldo.(Ens. Artíst.)Acce.Doctor
- 01-Diplomado/Maestro
- 02-ArquitectoTécnico
- 03-IngenieroTécnico
- 04-Licenciado
- 05 -Arquitecto
- 06-Ingeniero
- 07 - Doctor
- 08-EstudiosExtranjerosHomologados(AccesoDoctor)
 |
| //DatosTitulacion/DatosTitulo/TipoTitulo | Tipusdetítoldeltitular. |
| //DatosTitulacion/DatosTitulo/FechaFinalizacion | Data de finalització dels estudis del títol associat. Elformat s&#39;ajustarà a DD/MM/AAAA, MM/AAAA oAAAA. |
| //DatosTitulacion/DatosTitulo/FechaExpedicion | Datapagamentdetasesperexpedició(DD/MM/AAAA). |
| //DatosTitulacion/DatosTitulo/CodPaisExpedicion | Codi del país d&#39;expedició del títol (codificació ISO3166-1,numèric). |
| //DatosTitulacion/DatosTitulo/PaisExpedicion | Paísd&#39;expediciódeltítol. |
| //DatosTitulacion/DatosTitulo/NumTitulo | Númerodeltítol. |
| //DatosTitulacion/DatosTitulo/RegistroUniv | Registreuniversitari(codideregistre). |
| //resultat/codiResultat | Codideresultatdel&#39;operaciódeconsulta:
- 0003:Tramitada.Titularlocalitzat.
 |

| _Element_ | _Descripció_ |
| --- | --- |
|
 |
- 0232: Error reportat per l&#39;emissor. Existeixmésd&#39;unregistreperlesdadesproporcionadesenla consulta.
- 0233:Titularnoidentificat.
- 0238:Nohihadades deltitularconsultat.
- 0502: Error en la comunicació ambl&#39;emissor.
 |
| //resultat/descripcio | Descripciódelresultat. |

![](RackMultipart20211123-4-1fg42x4_html_b10ef2e538f0ec8e.png)

  1. **Verificació de titulacions no universitàries**

### (TITOLS\_NO\_UNIVERSITARIS)

Aquestamodalitatpermetobtenirelstítolsnouniversitarisdelciutadàsobreelqueesrealitzalaconsulta.

    1.
### Petició

      1. **Dades**** genèriques**

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (DNI / NIF o NIE). Encas d&#39;informar un NIE, el servei únicamentrespona titulacionsobtingudesalpaís. |
| //DatosGenericos/Titular/Documentacion | Documentació. |

      1. **Dades**** específiques**

Aquestamodalitatnorequereixinformardadesespecífiques.

    1.
### Resposta –dadesespecífiques

![](RackMultipart20211123-4-1fg42x4_html_c7aa7f3ba409a0e0.png)

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
