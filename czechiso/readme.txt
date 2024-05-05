Autor: David Martinek
E-mail: martinek NA fit.vutbr.cz
Datum: 31.3.2006
Verze: 1.0

Pou��v�n� BibTeXu podle normy �SN ISO 690
-----------------------------------------
Standardn� BibTeXov� styly nejsou p�elo�eny do �e�tiny a form�tov�n� polo�ek nesouhlas� s normou. Pro sv� pot�eby jsem si vytvo�il nov� styl czechiso.bst, kter� se sna�� tyto probl�my �e�it. Tento styl vzniknul p�ekladem souboru

/usr/share/texmf/tex/latex/custom-bib/english.mbs

a n�sledn�m pou�it�m p��kazu

latex makebst

T�m vniknul skript czechiso.dbj, kter� po p�elo�en� latexem vytvo�� soubor se stylem czechiso.bst. Pokud budete pot�ebovat ve stylu n�co zm�nit, nejjednodu��� je upravit skript czechiso.dbj a vygenerovat nov�, modifikovan� styl (latex csechiso.dbj).

Styl czechiso.bst
-----------------
Styl je p�elo�en do �e�tiny, tak�e ve v�sledn�m dokumentu by se m�ly objevovat v�razy 'vyd�n�' nam�sto 'edition', 'ro�n�k' nam�sto 'volume' apod. Tento styl vych�z� ze stylu plain.

Polo�ky isbn a issn jsou standardn�mi styly bibtexu ignorov�ny, ale norma ISO 690 tyto �daje vy�aduje. Styl czechiso.bst se sna�� t�to normy dr�et a tyto �daje zpracovat um�, tak�e tyto polo�ky lze bez obav pou��vat. (D��ve jsem tyto �daje d�val do polo�ky note, co� ale nen� nejlep�� �e�en�.)

Standardn� styly rovn� ignoruj� polo�ku url. Ve stylu czechiso tuto polo�ku lze pou��vat, ale je pot�eba z�rove� s t�mto stylem pou��t bal�k url t�mto zp�sobem:

\usepackage{url}
\DeclareUrlCommand\url{\def\UrlLeft{<}\def\UrlRight{>} \urlstyle{tt}}

Jde o provizorn� �e�en�. �asem snad p�ijdu na to, jak tento k�d vlo�it p��mo do souboru se stylem.

POZOR!
------
Tento styl zat�m norm� neodpov�d� p�esn�. Aby styl odpov�dal norm� p�esn�ji, je pot�eba p�epsat n�kter� funkce, zejm�na ty, kter� ovliv�uj� po�ad� polo�ek ve v�sledn�m dokumentu.

D�le by bylo dobr� upravit
-MANUAL, ARTICLE a podobn�, aby akceptovaly polo�ku howpublished (aby �lo tisknout hodnoty [online], [CD-ROM], atd.).

Z�znamy BibTeXu
---------------
Polo�ky ozna�en� ve v��tu na konci tohoto dokumentu jako OPT jsou voliteln�. Polo�ky ozna�en� jako ALT jsou alternativy. P�ed pou�it�m je nutn� tyto p�edpony umazat, stejn� jako v�echny nepou�it� polo�ky.

V�echny nezn�m� polo�ky jsou bibtexem ignorov�ny. Mohou ale b�t zpracov�ny speci�ln�m stylem. V�t�ina styl� nap��klad ignoruje polo�ku annote, do kter� si tak lze zapisovat vlastn� pozn�mky.

Tipy pro vytv��en� datab�z�
---------------------------
Polo�ka key
BibTeX, v z�vislosti na pou�it�m stylu, �ad� z�znamy bu� podle p��jmen� autora a roku vyd�n� (plain, alpha) nebo podle po�ad� pou�it�ch citac� (unsrt). Pokud u n�kter�ho z�znamu chyb� autor, m��e se z�znam ocitnout na m�st�, kter� nechceme. V takov�m p��pad� je vhodn� vyplnit polo�ku key, kter� se nikde netiskne, ale BibTeX ji vyu�ije p�i �azen� z�znam�. Lze sem um�stit nap��klad p��jmen� editora nebo prvn� slovo z n�zvu.

BibTeX neum� �adit �esky, tak�e je dobr� sem umis�ovat p��jmen� autora bez diakritiky (key = { ZOUZELKA2003 },).

Polo�ka author
Podle normy by se m�la p��jmen� s�zet velk�mi p�smeny. BibTeX (resp. styl czechiso) s�m p�smena nezv�t�uje, tak�e je nutn� ps�t p��jmen� velk�mi p�smeny u� do z�znam�. Styl czechiso pou��v� p��jmen� a prvn� p�smena jmen, je ale vhodn� do z�znam� um�s�ovat cel� jm�na (pokud jsou zn�ma), aby je �lo vyu��t p�i pou�it� jin�ch styl� (author = {David MARTINEK}, ).

Pokud m� dokument v�ce autor�, odd�luj� se v z�znamu slovem and (author = {David MARTINEK and Jakub �ERNOHORSK� and Zdena R�BOV�},).

Polo�ka note
Sem um�s�ujeme informace, pro kter� nelze v dan�m z�znamu nal�zt odpov�daj�c� polo�ku. Nap��klad @ARTICLE neobsahuje polo�ku howpublished. Pokud citujeme �l�nek z internetov�ho �asopisu, d� se text [online] um�stit pr�v� do polo�ky note. Dal��mi kandid�ty pro um�st�n� v t�to polo�ce jsou texty "naposledy nav�t�veno", �i "posledn� aktualizace", pokud se tyto �daje nehod� do polo�ky year.

Polo�ky volume a number
Z�rove� je lze pou��t pouze v z�znamech @ARTICLE. Volume znamen� ro�n�k �asopisu (b�v� odli�n� od roku vyd�n�) a number znamen� ��slo �asopisu v r�mci tohoto ro�n�ku. U jin�ch typ� z�znam� m� smysl vypl�ovat volume pouze, pokud jde o periodikum (v czechiso se v�dy p�edsad� slovo ro�n�k).

Polo�ka edition
Edition znamen� vyd�n� a m� smysl u publikac� jako jsou knihy nebo sborn�ky. Pokud jako hodnotu t�to polo�ky pou�ijete ��slovku od 1 do 5, nahrad� se to v dokumentu za text "prvn� -- p�t� vyd�n�". Prvn� vyd�n� se pou��v� jen v p��padech, kdy v�me, �e vy�lo i n�jak� dal�� vyd�n�, ale chceme zd�raznit, �e v dokumentu bylo explicitn� pou�ito vyd�n� p�vodn�.

Polo�ka pages
Tato polo�ka obsahuje informaci o str�nce nebo rozsahu str�nek, na kter�ch se dokument v r�mci knihy nebo sborn�ku nach�z�. Pokud pou�ijeme �daj 10--20, vys�z� se "s. 10--20", pokud pou�ijeme �daj 10, bude to nap�. u �asopisu (@ARTICLE) znamenat "str. 10", tedy �e se �l�nek nach�z� na stran� 10. U knihy se vys�z� "10 s.", co� znamen�, �e kniha m� celkem deset stran.

Polo�ky isbn, issn
Maj� smysl jen n�kde. Jejich hodnotou je pouze ��slo, texty ISBN, ISSN se s�z� automaticky.

Polo�ka url
Jej� hodnotou je pouze hol� adresa (url = {http://www.seznam.cz}), styl czechiso dopln� automaticky text URL. 

P�i pou�it� t�to polo�ky je nutn� pou��t bal�k url a makrem DeclareUrlCommand nastavit form�tov�n� (norma vy�aduje, aby adresy byly v �hlov�ch z�vork�ch). Z praktick�ch d�vod� doporu�uji nechat styl tt (strojopisn� �ez), jinak se nebudou spr�vn� s�zet symboly jako ~ (tilda) a _ (podtr��tko). Na za��tek dokumentu prost� vlo�te toto:
\usepackage{url}
\DeclareUrlCommand\url{\def\UrlLeft{<}\def\UrlRight{>} \urlstyle{tt}}

Polo�ky address a publisher
Do polo�ky address se p�e m�sto, ve kter�m byl dokument vyd�n (nap�. Ostrava), polo�ka publisher obsahuje n�zev vydavatelstv� (nap�. MARQ), styl czechiso pot� vys�z� tyto �daje podle normy (Praha: MARQ). 

Polo�ka editor
Vyskytuje se nap��klad u knih a sborn�k�. Jde o osobu, kter� nen� p��mo autorem, ale provedla slo�en� kapitol �i �l�nk� od jin�ch autor� do jednoho celku.

P�ekladatel�, ilustr�to�i
Pro tyto osoby nejsou definov�ny speci�ln� polo�ky. Pro jejich vys�zen� je nutn� pou��t op�t polo�ku note (note = {P�elo�il Jan Hrom�dka, ilustroval Cyril P�rko})

Polo�ka note
Typicky se pou��v� pro ukl�d�n� dat, kter� se nedaj� vlo�it nikam jinam. Nap��klad u internetov�ch zdroj� sem lze vlo�it toto: note = {[Online], Verze 3.1 (2004), [rev. 2004-11-11], [cit. 2006-03-31]}, co� znamen�, �e jde o zdroj na internetu, aktu�ln� pou�it� verze byla 3.1 z roku 2004, jej� posledn� revize prob�hla podle autora 11. listopadu 2004, a j� jsem tuto str�nku naposledy kontroloval 31. b�ezna 2006.

�l�nek v �asopise:

@Article{,
author = {},
title = {},
journal = {},
year = {},
OPTkey = {},
OPTvolume = {},
OPTnumber = {},
OPTpages = {},
OPTmonth = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
OPTissn = {},
}



�l�nek na konferenci:

@InProceedings{,
author = {},
title = {},
booktitle = {},
OPTcrossref = {},
OPTkey = {},
OPTpages = {},
OPTyear = {},
OPTeditor = {},
OPTvolume = {},
OPTnumber = {},
OPTseries = {},
OPTaddress = {},
OPTmonth = {},
OPTorganization = {},
OPTpublisher = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
OPTissn = {},
}



�l�nek ve sb�rce:

@InCollection{,
author = {},
title = {},
booktitle = {},
OPTcrossref = {},
OPTkey = {},
OPTpages = {},
OPTpublisher = {},
OPTyear = {},
OPTeditor = {},
OPTvolume = {},
OPTnumber = {},
OPTseries = {},
OPTtype = {},
OPTchapter = {},
OPTaddress = {},
OPTedition = {},
OPTmonth = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
OPTissn = {},
}



Kaptitola nebo str�nky v knize:

@InBook{,
ALTauthor = {},
ALTeditor = {},
title = {},
chapter = {},
publisher = {},
year = {},
OPTkey = {},
OPTvolume = {},
OPTnumber = {},
OPTseries = {},
OPTtype = {},
OPTaddress = {},
OPTedition = {},
OPTmonth = {},
OPTpages = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
OPTissn = {},
}



Sborn�k konference:

@Proceedings{,
title = {},
year = {},
OPTkey = {},
OPTeditor = {},
OPTvolume = {},
OPTnumber = {},
OPTseries = {},
OPTaddress = {},
OPTmonth = {},
OPTorganization = {},
OPTpublisher = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
OPTissn = {},
}



Kniha �i monografie:

@Book{,
ALTauthor = {},
ALTeditor = {},
title = {},
publisher = {},
year = {},
OPTkey = {},
OPTvolume = {},
OPTnumber = {},
OPTseries = {},
OPTaddress = {},
OPTedition = {},
OPTmonth = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
}



Bro�ura:

@Booklet{,
title = {},
OPTkey = {},
OPTauthor = {},
OPThowpublished = {},
OPTaddress = {},
OPTmonth = {},
OPTyear = {},
OPTnote = {},
OPTannote = {},

OPTisbn = {},
OPTissn = {},
}



Dizerta�n� pr�ce:

@PhdThesis{,
author = {},
title = {},
school = {},
year = {},
OPTkey = {},
OPTtype = {},
OPTaddress = {},
OPTmonth = {},
OPTnote = {},
OPTannote = {}
}



Diplomov� pr�ce (nebo bakal��ka):

@MastersThesis{,
author = {},
title = {},
school = {},
year = {},
OPTkey = {},
OPTtype = {},
OPTaddress = {},
OPTmonth = {},
OPTnote = {},
OPTannote = {}
}



Technick� zpr�va:

@TechReport{,
author = {},
title = {},
institution = {},
year = {},
OPTkey = {},
OPTtype = {},
OPTnumber = {},
OPTaddress = {},
OPTmonth = {},
OPTnote = {},
OPTannote = {},
}



Technick� manu�l:

@Manual{,
title = {},
OPTkey = {},
OPTauthor = {},
OPTorganization = {},
OPTaddress = {},
OPTedition = {},
OPTmonth = {},
OPTyear = {},
OPTnote = {},
OPTannote = {}
}



Nepublikov�no ve�ejn� (dostupnost lze specifikovat v pozn�mce):

@Unpublished{,
author = {},
title = {},
note = {},
OPTkey = {},
OPTmonth = {},
OPTyear = {},
OPTannote = {}
}



Ostatn�:

@Misc{,
OPTkey = {},
OPTauthor = {},
OPTtitle = {},
OPThowpublished = {},
OPTmonth = {},
OPTyear = {},
OPTnote = {},
OPTannote = {}
}
