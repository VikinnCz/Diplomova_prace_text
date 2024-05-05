Autor: David Martinek
E-mail: martinek NA fit.vutbr.cz
Datum: 31.3.2006
Verze: 1.0

Pou¾ívání BibTeXu podle normy ÈSN ISO 690
-----------------------------------------
Standardní BibTeXové styly nejsou pøelo¾eny do èe¹tiny a formátování polo¾ek nesouhlasí s normou. Pro své potøeby jsem si vytvoøil nový styl czechiso.bst, který se sna¾í tyto problémy øe¹it. Tento styl vzniknul pøekladem souboru

/usr/share/texmf/tex/latex/custom-bib/english.mbs

a následným pou¾itím pøíkazu

latex makebst

Tím vniknul skript czechiso.dbj, který po pøelo¾ení latexem vytvoøí soubor se stylem czechiso.bst. Pokud budete potøebovat ve stylu nìco zmìnit, nejjednodu¹¹í je upravit skript czechiso.dbj a vygenerovat nový, modifikovaný styl (latex csechiso.dbj).

Styl czechiso.bst
-----------------
Styl je pøelo¾en do èe¹tiny, tak¾e ve výsledném dokumentu by se mìly objevovat výrazy 'vydání' namísto 'edition', 'roèník' namísto 'volume' apod. Tento styl vychází ze stylu plain.

Polo¾ky isbn a issn jsou standardními styly bibtexu ignorovány, ale norma ISO 690 tyto údaje vy¾aduje. Styl czechiso.bst se sna¾í této normy dr¾et a tyto údaje zpracovat umí, tak¾e tyto polo¾ky lze bez obav pou¾ívat. (Døíve jsem tyto údaje dával do polo¾ky note, co¾ ale není nejlep¹í øe¹ení.)

Standardní styly rovnì¾ ignorují polo¾ku url. Ve stylu czechiso tuto polo¾ku lze pou¾ívat, ale je potøeba zároveò s tímto stylem pou¾ít balík url tímto zpùsobem:

\usepackage{url}
\DeclareUrlCommand\url{\def\UrlLeft{<}\def\UrlRight{>} \urlstyle{tt}}

Jde o provizorní øe¹ení. Èasem snad pøijdu na to, jak tento kód vlo¾it pøímo do souboru se stylem.

POZOR!
------
Tento styl zatím normì neodpovídá pøesnì. Aby styl odpovídal normì pøesnìji, je potøeba pøepsat nìkteré funkce, zejména ty, které ovlivòují poøadí polo¾ek ve výsledném dokumentu.

Dále by bylo dobré upravit
-MANUAL, ARTICLE a podobnì, aby akceptovaly polo¾ku howpublished (aby ¹lo tisknout hodnoty [online], [CD-ROM], atd.).

Záznamy BibTeXu
---------------
Polo¾ky oznaèené ve výètu na konci tohoto dokumentu jako OPT jsou volitelné. Polo¾ky oznaèené jako ALT jsou alternativy. Pøed pou¾itím je nutné tyto pøedpony umazat, stejnì jako v¹echny nepou¾ité polo¾ky.

V¹echny neznámé polo¾ky jsou bibtexem ignorovány. Mohou ale být zpracovány speciálním stylem. Vìt¹ina stylù napøíklad ignoruje polo¾ku annote, do které si tak lze zapisovat vlastní poznámky.

Tipy pro vytváøení databází
---------------------------
Polo¾ka key
BibTeX, v závislosti na pou¾itém stylu, øadí záznamy buï podle pøíjmení autora a roku vydání (plain, alpha) nebo podle poøadí pou¾itých citací (unsrt). Pokud u nìkterého záznamu chybí autor, mù¾e se záznam ocitnout na místì, které nechceme. V takovém pøípadì je vhodné vyplnit polo¾ku key, která se nikde netiskne, ale BibTeX ji vyu¾ije pøi øazení záznamù. Lze sem umístit napøíklad pøíjmení editora nebo první slovo z názvu.

BibTeX neumí øadit èesky, tak¾e je dobré sem umis»ovat pøíjmení autora bez diakritiky (key = { ZOUZELKA2003 },).

Polo¾ka author
Podle normy by se mìla pøíjmení sázet velkými písmeny. BibTeX (resp. styl czechiso) sám písmena nezvìt¹uje, tak¾e je nutné psát pøíjmení velkými písmeny u¾ do záznamù. Styl czechiso pou¾ívá pøíjmení a první písmena jmen, je ale vhodné do záznamù umís»ovat celá jména (pokud jsou známa), aby je ¹lo vyu¾ít pøi pou¾ití jiných stylù (author = {David MARTINEK}, ).

Pokud má dokument více autorù, oddìlují se v záznamu slovem and (author = {David MARTINEK and Jakub ÈERNOHORSKÝ and Zdena RÁBOVÁ},).

Polo¾ka note
Sem umís»ujeme informace, pro které nelze v daném záznamu nalézt odpovídající polo¾ku. Napøíklad @ARTICLE neobsahuje polo¾ku howpublished. Pokud citujeme èlánek z internetového èasopisu, dá se text [online] umístit právì do polo¾ky note. Dal¹ími kandidáty pro umístìní v této polo¾ce jsou texty "naposledy nav¹tíveno", èi "poslední aktualizace", pokud se tyto údaje nehodí do polo¾ky year.

Polo¾ky volume a number
Zároveò je lze pou¾ít pouze v záznamech @ARTICLE. Volume znamená roèník èasopisu (bývá odli¹ný od roku vydání) a number znamená èíslo èasopisu v rámci tohoto roèníku. U jiných typù záznamù má smysl vyplòovat volume pouze, pokud jde o periodikum (v czechiso se v¾dy pøedsadí slovo roèník).

Polo¾ka edition
Edition znamená vydání a má smysl u publikací jako jsou knihy nebo sborníky. Pokud jako hodnotu této polo¾ky pou¾ijete èíslovku od 1 do 5, nahradí se to v dokumentu za text "první -- páté vydání". První vydání se pou¾ívá jen v pøípadech, kdy víme, ¾e vy¹lo i nìjaké dal¹í vydání, ale chceme zdùraznit, ¾e v dokumentu bylo explicitnì pou¾ito vydání pùvodní.

Polo¾ka pages
Tato polo¾ka obsahuje informaci o stránce nebo rozsahu stránek, na kterých se dokument v rámci knihy nebo sborníku nachází. Pokud pou¾ijeme údaj 10--20, vysází se "s. 10--20", pokud pou¾ijeme údaj 10, bude to napø. u èasopisu (@ARTICLE) znamenat "str. 10", tedy ¾e se èlánek nachází na stranì 10. U knihy se vysází "10 s.", co¾ znamená, ¾e kniha má celkem deset stran.

Polo¾ky isbn, issn
Mají smysl jen nìkde. Jejich hodnotou je pouze èíslo, texty ISBN, ISSN se sází automaticky.

Polo¾ka url
Její hodnotou je pouze holá adresa (url = {http://www.seznam.cz}), styl czechiso doplní automaticky text URL. 

Pøi pou¾ití této polo¾ky je nutné pou¾ít balík url a makrem DeclareUrlCommand nastavit formátování (norma vy¾aduje, aby adresy byly v úhlových závorkách). Z praktických dùvodù doporuèuji nechat styl tt (strojopisný øez), jinak se nebudou správnì sázet symboly jako ~ (tilda) a _ (podtr¾ítko). Na zaèátek dokumentu prostì vlo¾te toto:
\usepackage{url}
\DeclareUrlCommand\url{\def\UrlLeft{<}\def\UrlRight{>} \urlstyle{tt}}

Polo¾ky address a publisher
Do polo¾ky address se pí¹e mìsto, ve kterém byl dokument vydán (napø. Ostrava), polo¾ka publisher obsahuje název vydavatelství (napø. MARQ), styl czechiso poté vysází tyto údaje podle normy (Praha: MARQ). 

Polo¾ka editor
Vyskytuje se napøíklad u knih a sborníkù. Jde o osobu, která není pøímo autorem, ale provedla slo¾ení kapitol èi èlánkù od jiných autorù do jednoho celku.

Pøekladatelé, ilustrátoøi
Pro tyto osoby nejsou definovány speciální polo¾ky. Pro jejich vysázení je nutné pou¾ít opìt polo¾ku note (note = {Pøelo¾il Jan Hromádka, ilustroval Cyril Pírko})

Polo¾ka note
Typicky se pou¾ívá pro ukládání dat, které se nedají vlo¾it nikam jinam. Napøíklad u internetových zdrojù sem lze vlo¾it toto: note = {[Online], Verze 3.1 (2004), [rev. 2004-11-11], [cit. 2006-03-31]}, co¾ znamená, ¾e jde o zdroj na internetu, aktuální pou¾itá verze byla 3.1 z roku 2004, její¾ poslední revize probìhla podle autora 11. listopadu 2004, a já jsem tuto stránku naposledy kontroloval 31. bøezna 2006.

Èlánek v èasopise:

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



Èlánek na konferenci:

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



Èlánek ve sbírce:

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



Kaptitola nebo stránky v knize:

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



Sborník konference:

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



Kniha èi monografie:

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



Bro¾ura:

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



Dizertaèní práce:

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



Diplomová práce (nebo bakaláøka):

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



Technická zpráva:

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



Technický manuál:

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



Nepublikováno veøejnì (dostupnost lze specifikovat v poznámce):

@Unpublished{,
author = {},
title = {},
note = {},
OPTkey = {},
OPTmonth = {},
OPTyear = {},
OPTannote = {}
}



Ostatní:

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
