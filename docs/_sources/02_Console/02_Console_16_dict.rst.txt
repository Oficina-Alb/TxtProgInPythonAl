Fjalor
============

Tani do të prezantojmë një lloj të ri të të dhënave të strukturuara, d.m.th. koleksionin, i cili është krejt i ndryshëm nga ai që kemi takuar deri më tani.

Supozoni se duhet të shkruajmë një program që i përgjigjet pyetjeve për moshën e një individi. Emrat dhe moshat e personave janë të njohur për ne, për shembull Maria është 14 vjeç, Michael 15, Daniel gjithashtu 15, dhe Matilda 16 (të dhënat aktuale do të ishin më të gjera, por kjo është vetëm një ilustrim).

Ne mund ta zgjidhim këtë problem duke i vendosur emrat në një tufë dhe moshat në tjetrën. Duke pasur këto dy tupla, ne mund të përdorim një lak për të kërkuar një emër të dhënë në tufën e emrit, dhe kur e gjejmë atë, ne përdorim të njëjtin indeks për të hyrë dhe shtypur epokën e duhur.

.. activecode:: dict__two_tuples

    name = ('Mary', 'Michael', 'Daniel', 'Matilda')
    age = (14, 15, 15, 16)
    asked_name = input('Please enter a name: ')
    name_has_been_found = False
    for i in range(len(name)):
        if asked_name == name[i]:
            print(asked_name, 'is', age[i], 'years old.')
            name_has_been_found = True
            break
    
    if not name_has_been_found:
        print('Name', asked_name, 'has not been found.')

Siç mund ta shohim, koleksionet që tashmë i njohim mund të na shërbejnë edhe në këtë rast. Sidoqoftë, për këtë lloj detyre, ekziston një koleksion në të cilin të dhënat regjistrohen në një mënyrë më koherente, dhe të dhënat e nevojshme gjenden më lehtë dhe në mënyrë më efikase. Le të shohim një zgjidhje tjetër:

.. activecode:: dict__1st_example

    age = {'Mary':14, 'Michael':15, 'Daniel':15, 'Matilda':16}
    asked_name = input('Please enter a name: ')
    if asked_name in age:
        print(asked_name, 'is', age[asked_name], 'years old.')
    else:
        print('Name', asked_name, 'has not been found.')

Një koleksion i formularit {'Mary': 14, 'Michael': 15, 'Daniel': 15, 'Matilda': 16} quhet një **fjalor**. Ne mund të shohim që një fjalor mund të vendoset në mënyrë të ngjashme me një tuple dhe një listë - duke renditur elementet e ndara me presje. Elementet e fjalorit shkruhen midis kllapave gjarpërushe `` {} ``. Secili element përbëhet nga dy pjesë, midis të cilave ekziston një  ``:``. Pjesa e parë e elementit quhet tasti dhe ndërsa **e dyta është vlera**. Për shembull, për çelësin Mary Mary ’vlera përkatëse është 14, etj.

Ne përdorim fjalorë për të marrë shpejt dhe me lehtësi vlerë për një çelës të caktuar. Në shembullin tonë, ne gjetëm moshën për një emër të dhënë në fjalor. Në tuples dhe listat, ne gjithashtu marrim vlerën e elementit me numrin e sekuencës (indeksin) e atij elementi. Mund të themi se çelësi në fjalor luan rolin që luan indeksi në tuples dhe listat. Dallimi thelbësor midis fjalorëve nga njëra anë, dhe tuples dhe listave nga ana tjetër, është se në fjalor çelësi mund të jetë i çdo lloji të pandryshueshëm (numër i plotë, numër real, varg, tuple ...) ndërsa është në tuple ose listë indekset duhet të jenë numra të plotë duke filluar nga 0.

Ndërtimi i një fjalori
---------------------

Ne gjithashtu mund të ndërtojmë një fjalor duke llogaritur. Ne e bëjmë këtë duke futur çifte të reja me vlerë çelësi në fjalor dhe më pas duke ndryshuar vlerën për një çelës të dhënë sipas nevojës.

Në shembullin vijues, tupla fillestare përmban emrat e klubeve të futbollit që fituan Kupën Evropiane të Kampionëve (ose UEFA Champions League) nga 1956-2019. Bazuar në këtë informacion, ne do të formojmë një fjalor në të cilin do të ruajmë numrin e kampionateve të fituara për secilin klub. Ja se si mund ta bëjmë.

.. activecode:: dict__counting

    champions = (
        'Real Madrid',       'Real Madrid',       'Real Madrid',       'Real Madrid',
        'Real Madrid',       'Benfica',           'Benfica',           'Milan',
        'Internazionale',    'Internazionale',    'Real Madrid',       'Celtic',
        'Manchester United', 'Milan',             'Feyenoord',         'Ajax',
        'Ajax',              'Ajax',              'Bayern Munich',     'Bayern Munich',
        'Bayern Munich',     'Liverpool',         'Liverpool',         'Nottingham Forest',
        'Nottingham Forest', 'Liverpool',         'Aston Villa',       'Hamburg',
        'Liverpool',         'Juventus',          'Steaua București',  'Porto',
        'PSV Eindhoven',     'Milan',             'Milan',             'Red Star Belgrade',
        'Barcelona',         'Marseille',         'Milan',             'Ajax',
        'Juventus',          'Borussia Dortmund', 'Real Madrid',       'Manchester United',
        'Real Madrid',       'Bayern Munich',     'Real Madrid',       'Milan',
        'Porto',             'Liverpool',         'Barcelona',         'Milan',
        'Manchester United', 'Barcelona',         'Internazionale',    'Barcelona',
        'Chelsea',           'Bayern Munich',     'Real Madrid',       'Barcelona',
        'Real Madrid',       'Real Madrid',       'Real Madrid',       'Liverpool'
    )
    num_titles = {} # empty dictionary
    for club in champions:
        if club in num_titles:
            num_titles[club] += 1
        else:
            num_titles[club] = 1
    
    print('club     number of titles')
    print('-' * 25)    
    for club in num_titles:
        s_num_titles = str(num_titles[club])
        space = ' ' * (25 - len(club) - len(s_num_titles))
        print(club + space + s_num_titles)

në fillim ne formojmë një fjalor *num_titles* bosh. Për secilin klub në listën e kampionëve, së pari kontrollojmë nëse klubi ekziston tashmë në fjalorin *num_titles*. Nëse po, shtojmë një në numrin e titullit të klubit, dhe nëse nuk ndodh, shtojmë klubin në fjalor me një titull të fituar.

Në fund të numërimit, ne kalojmë përmes fjalorit duke përdorur një loop dhe shtypim çelësat dhe vlerat nga ai fjalor.


Një mënyrë për të shkurtuar këtë program është të përdorni funksionin (metodën) ``get``, e cila është pjesë e secilit fjalor dhe quhet me *dictionary_name.get(key, default_value)*. Siç mund ta shohim, ky funksion ka dy argumente. Argumenti i parë është çelësi për të cilin na duhet vlera. Në rast se ky çelës ekziston në fjalor, funksioni *get* kthen vlerën që korrespondon me atë çelës, dhe nëse çelësi nuk është në fjalor, funksioni kthen vlerën e argumentit të tij të dytë. Kështu për shembull, në vend

.. code::

    if club in num_titles:
        num_titles[club] += 1
    else:
        num_titles[club] = 1

mund të shkruajmë

.. code::

    num_titles[club] = num_titles.get(club, 0) + 1
    
dhe efekti është i njëjtë. Në këtë shembull, *num_titles.get (club, 0)* kthen numrin e titujve të një klubi të caktuar nëse ai klub është tashmë në fjalor, ose 0 nëse nuk është akoma në fjalor. Në të dy rastet, 1 duhet t'i shtohet asaj vlere dhe të ruhet në fjalor si numri i ri i titujve për atë klub.

Ushtrime
''''''''''''''''''

.. questionnote::

    **Detyrë - çmimet e produkteve ushqimore**
    
     Çmimet në një dyqan janë:
    
     - Bukë: 1 (për bukë - gjysmë kilogram)
     - Qumësht: 0.8 (për litër)
     - Veza: 0,08 (për copë)
     - Gjoks pule: 7.3 (për kilogram)
     - Mollë: 2.2 (për kilogram)
     - Domate: 1 (për kilogram)

     Vendosni këto informacione në një fjalor dhe më pas plotësoni programin duke ngarkuar emrin e një ushqimi dhe duke shfaqur çmimin e atij ushqimi, ose informacione që nuk janë të disponueshme.
    
.. activecode:: console__dict__prices
    

.. questionnote::

    **Detyrë - mungesa**
    
     Emrat e nxënësve që mungonin nga klasa u dhanë në një tuple. Çdo paraqitje e një emri paraqet mungesë nga një klasë. Përfundoni programin në mënyrë që të llogarit dhe shtyp se sa klasa ka secila studentë që ka humbur.
    
     Për t'ju ndihmuar të kontrolloni programin tuaj, këtu është rezultati i pritshëm: për të dhënat e dhëna në tuple *që mungon*, duhet të merrni që James ka 4 mungesa, Maya 3, Alexander 2, dhe Violet, Mark, Frankie, Peter, Ronnie dhe Oliver një mungesë secila (jo domosdoshmërisht në atë rregull).
    
.. activecode:: console__dict__absence
    
    absent = (
        'Maya', 'James', 'Violet', 'Alexander', 'James', 
        'Mark', 'Maya', 'Frankie', 'James', 'Peter',
        'Ronnie', 'Oliver', 'Maya', 'Alexander', 'James')
        
.. commented out

    absences = {}
    for name in absent:
        absences[name] = absences.get(name, 0) + 1
    for name in absences:
        print(name, absences[name])        

.. questionnote::

    
     Jepen blerjet dhe shitjet e mallrave në formën e një palë palë. Në secilën palë, elementi i parë është emri i mallrave, dhe i dyti është ndryshimi në statusin e aksioneve. Për shembull, një palë *(djathë', -1.5)* do të thotë që sasia e mundshme e djathit është ulur me 1.5 (aq shumë djathë janë shitur).
     
     Plotësoni programin që llogarit dhe printon gjendjen pas këtyre ndryshimeve, bazuar në ndryshimet e dhëna të shtetit. Supozoni se nuk ka rezerva në fillim.
    
     Kontrolloni rezultatin: për të dhënat e dhëna, duhet të merrni (në çdo mënyrë)
    
     - djathë 18.5
     - qumësht 297
     - miell 985
     - vezë 1988
     - peshk 47
     
Në këtë detyrë, pjesa më e rëndësishme e programit është përshkimi nëpër të gjitha palët. Për qartësi, ne menjëherë shpaketojmë secilën palë nga *ndryshimet* e tuple në *ndryshimet* e mira* të variablia.

.. activecode:: console__dict__stock_status
    
        changes = (
            ('cheese', 20), ('milk', 300), ('cheese', -1.5), ('flour', 1000),
            ('eggs', 2000), ('milk', -2), ('flour', -5), ('fish', 50),
            ('eggs', -12), ('milk', -1), ('flour', -10), ('fish', -3)
        )
        
        status = {}
        for good, change in changes:
            # complete
            
        for good in status:
            print(good, status[good])
