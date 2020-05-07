Degëzimi kompleks
=================

Kushtet e njëpasnjëshme
-------------------------

Ekzistojnë detyra në të cilat, kur nuk plotësohet një kusht, një tjetër duhet të kontrollohet, dhe nëse ajo gjendje nuk është e vlefshme as atëherë kontrollohet një e treta etj. Për të shmangur shkrimet

.. activecode:: console__more_branching_elif1
    :passivecode: true
    
    if first_condition:
        statement1
    else:
        if second_condition:
            statement2
        else:
            if third_condition:
                statement3
            else:
                if fourth_condition:
                    statement4
                else:
                    statement5

në Python ne përdorim fjalën e veçantë ``elif``, e cila qëndron për *else* dhe dhe vazdhon me *if* në rreshtin vijues. Pra, ne kemi një kod më të lexueshëm:

.. activecode:: console__more_branching_elif2
    :passivecode: true
    
    if first_condition:
        statement1
    elif second_condition:
        statement2
    elif third_condition:
        statement3
    elif fourth_condition:
        statement4
    else:
        statement5

Shënim 1: Çdo numër i deklaratave të njëpasnjëshme *elif* mund të përdoret në këtë mënyrë.

Shënim 2: Pjesa

.. activecode:: console__more_branching_elif3
    :passivecode: true

    else:
        statement5

është opsionale dhe mund të lihet nëse nuk është e nevojshme.


Shembuj dhe detyra
'''''''''''''''''''

.. questionnote::
    
    **Shembull - body mass index:** 
    
   Indeksi i masës trupore (i shkurtuar bmi) përdoret për orientim të shpejtë në lidhje me shkallën e mbipeshes ose humbjes së peshës. Formula për llogaritjen e indeksit të masës së trupit është :math: `bmi = {m \ mbi {h \ shumëzim h herë}`, ku *m* është masa në kilogram dhe *h* është lartësia në metra. Vlerat *bmi* interpretohen si më poshtë:
    
     - deri në 18.5: person i kequshqyer
     - nga 18.5 në 25: person me peshë normale të trupit
     - nga 25 në 30: mbipesha
     - mbi 30: person i trashë
    
     Shkruaj një program që merr peshën dhe lartësinë e një personi dhe pastaj shkruaj se cilës kategori ai person i përket (vlerat kufi i përkasin një kategorie më të ulët).

Një zgjidhje e mundshme është dhënë më poshtë. Konsideroni pse nuk është e nevojshme të përdorni kushte logjike komplekse (të ndërtuara me fjalë *ose*, *ose*, *jo*) në këtë zgjidhje.

.. activecode:: console__more_branching_bmi

    m = float(input('Masa trupore: '))
    h = float(input('Gjatësia e trupizt: '))
    bmi = m / (h*h)
    if bmi <= 18.5:
        print('I kequshqyer.')
    elif bmi <= 25:
        print('Peshë normale trupore.')
    elif bmi <= 30:
        print('Mbipeshë.')
    else:
        print('Obez.')



.. questionnote::
    
    **Detyrë - kategoritë e moshave të lojtarëve:**
    
     Basketbollistët e rinj regjistrohen në fillim të sezonit të basketbollit në njërën nga kategoritë e moshave, në bazë të sa viteve ato kthehen në vitin kalendarik në të cilin fillon sezoni. Rregullat e regjistrimit janë si më poshtë:
    
     - 10 dhe nën - asnjë kategori
     - 11 ose 12 vjet - pionierë më të rinj
     - 13 ose 14 vjeç - pionierë
     - 15 ose 16 - kadetë
     - 17 ose 18 - juniors
     - 19 vjeç e më të vjetër - të moshuar
    
     Shkruani një program që merr moshën e një basketbollisti në vitin kur regjistrohen dhe heqin kategorinë e tyre të moshës.

.. activecode:: console__more_branching_categories

    g = int(input("Sa vjeç është lojtari: "))
    # finish the program


        
.. questionnote::
    
    **Detyrë - numri rendor:**
    
     Shkruaj një program që ngarkon një numër të plotë nga 1 në 6 (përfshirë kufijtë) dhe shtyp numrin e duhur rendor me shkronja. Për shembull, nëse numri i 6 është i ngarkuar, "6" (pa thonjëza) duhet të shtypet.
    
.. activecode:: console__more_branching_ordinal

    n = int(input("Enter a number from 1 to 6: "))
    # finish the program


Degëzimi  fole
----------------

Degët e foleve janë deklarimet *if* në degët e deklarimeve të tjera *if*. Deklarimet e vendosura *if* mund të gjenden në njërën ose tjetrën, ose në të dy degët e një deklarimi më të madhe *if*. Kjo mënyrë e përcaktimit të deklarimit *if* mund të shkoj në në çdo thellësi, por duhet të kihet parasysh se programet mund të bëhen të vështira për t'u kuptuar saktësisht dhe vështirë për tu mbajtur.

Në shembullin e parë, ne sigurojmë me qëllim një program me tre nivele të deklarimeve të vendosjes në gjumë *if*, për t'ju ndihmuar të imagjinoni se si një program me deklarime edhe më të thella dhe më të gjata *if* mund të duken. Në shembuj dhe detyra të tjera, ne do të kufizohemi në një nivel të futjes së deklarimeve *if*.

Shembuj dhe ushtrime
''''''''''''''''''''''


.. questionnote::

    **Shembull - gjeje kush**
    
     Janë tetë fëmijë në lagje që janë shpesh bashkë. Emrat e tyre janë: Alice, Ben, Charlotte, Daniel, Emily, Frankie, Gabriella dhe Harry. Alice, Ben, Charlotte dhe Daniel shkojnë në seksionin e programimit, dhe Alice, Ben, Emily dhe Frankie në seksionin e sporteve. Drejtoresha e shkollës dëshironte të lavdëronte një prej fëmijëve për disa vepra, por nuk e dinte emrin e asaj fëmije.
    
     Shkruani një program që shtron tre pyetje, pranon përgjigjet e atyre pyetjeve (shkronja 'y' për po, dhe çdo përgjigje tjetër jo) dhe shtypni emrin e fëmijës në fjalë. Pyetjet që shtron programi janë:

     - A është vajzë?
     - A shkon në seksionin e sportit?
     - A shkon në seksionin e programimit?
    
.. activecode:: console__more_branching_guess_who1

    girl = input("A është vajzë? ") == 'y'
    sportsperson = input("A shkon në seksionin e sportit?") == 'y'
    programmer = input("A shkon në seksionin e programimit? ") == 'y'
    if programmer:
        if sportsperson:
            if girl:
                print("Alice")
            else:
                print("Ben")
        else:
            if girl:
                print("Charlotte")
            else:
                print("Daniel")
    else:
        if sportsperson:
            if girl:
                print("Emily")
            else:
                print("Frankie")
        else:
            if girl:
                print("Gabriella")
            else:
                print("Harry")

Vini re se programet me degë me fole mund të modifikohen për të përdorur vetëm kushte të njëpasnjëshme dhe formuar me *elif*, pa u futur në thellësi të *if*. Duke vepruar kështu, ne përdorim kushte komplekse, të cilat i ndërtojmë duke përdorur operacione logjike *and*, *ose* dhe *jo*.
   
.. activecode:: console__more_branching_guess_who2

    girl = input("Is it a girl? ") == 'y'
    sportsperson = input("Does he or she go to the sports section? ") == 'y'
    programmer = input("Does he or she go to the programming section? ") == 'y'
    if programmer and sportsperson and girl:
        print("Alice")
    elif programmer and sportsperson and not girl:
        print("Ben")
    elif programmer and not sportsperson and girl:
        print("Charlotte")
    elif programmer and not sportsperson and not girl:
        print("Daniel")
    elif not programmer and sportsperson and girl:
        print("Emily")
    elif not programmer and sportsperson and not girl:
        print("Frankie")
    elif not programmer and not sportsperson and girl:
        print("Gabriella")
    else:
        print("Harry")


.. questionnote::
    
    **Detyrë - udhëkryq:**
    
    Ka një kryqëzim të rrugëve A dhe B. Edhe numrat e shtëpive në Rrugën A janë në të djathtë dhe ato të çuditshme janë në të majtë. Në anën e barabartë (të djathtë), numrat deri në kryqëzim janë nga 2 në 200, dhe pas kryqëzimit janë ato më të mëdha se 200. Në anën e çuditshme (të majtë), numrat deri në kryqëzim janë nga 1 në 177, dhe pas kryqëzimit ato janë ato nga 179 e tutje.
    
    Shkruaj një program që ngarkon një numër shtëpie në rrugën A dhe përgjigjet nëse ai numër është para ose pas kryqëzimit dhe në cilën anë të rrugës A është në të. Për shembull:
    
    - për numrin 128, shtypni "në anën e djathtë, përpara kryqëzimit"
    - për numrin 284 të shtypura "në anën e djathtë, pas kryqëzimit"
    - për numrin 177, shkruani "në anën e majtë, përpara kryqëzimit"
    - për numrin 219 shkruaj "në anën e majtë, pas kryqëzimit"

**Ndihmë:** Pas ngarkimit, së pari duhet të kontrolloni nëse *n* është i njëtrajtshëm, d.m.th. nëse: matematika: `n \% 2 == 0`.

.. activecode:: console__more_branching_quart

    n = int(input("What is the house number: "))
    # finish the program




.. questionnote::
    
    **Detyrë - studimi:**
    
     Prindërit e John i thanë atij se nëse ai merrte katër ose pesë në matematikë dhe anglisht, ai mund të shkonte në një turne pasdite në futboll, përndryshe ai duhej të mësonte lëndën ose lëndët nga të cilat merrte notë (a) më pak se 4 (notat janë nga 1 në 5, 1 është më e keqja, 5 më e mira).
    
     Shkruani një program që ngarkon së pari klasën e matematikës së Gjonit dhe më pas klasën angleze dhe shtyp një mesazh për Gjonin. Për shembull:
    
     - për klasat 2, 3 shtypni "mësoni matematikë dhe anglisht"
     - për klasat 3, 4 shtypni "mëso matematikën"
     - për klasat 4, 2 shtypni "mësoni anglisht"
     - për notat 5, 4 shtypni "shkoni në turne"
    

.. activecode:: console__more_branching_grades

    math = int(input("What is the grade in math: "))
    english = int(input("What is the grade in English: "))
    # finish the program


.. questionnote::
    
    **Detyrë - veshja:**
    
     Ian është duke shkruar një program që lexon temperaturën aktuale (në gradë Celsius) dhe mundësinë e shiut (nga 0 në 100) nga faqja e internetit e motit, dhe bazuar në atë informacion, ajo shkruan një rekomandim nëse do të sillni një xhaketë (e cila ka kapuç) ose një ombrellë, ose asnjë nga këto dy. Ian zgjodhi këtë rregull:

     - kur temperatura është nën 21, këshilla duhet të jetë: "vish xhaketën"
     - kur temperatura është 21 ose më e lartë dhe mundësia e shiut është mbi 50, rekomandimi është: "sillni një ombrellë"
     - kur temperatura është 21 ose më e lartë dhe mundësia e shiut është deri në 50, këshilla duhet të jetë "ju mund të shkoni në një T-shirt"
    
     Detyra për ju është të shkruani një program që ngarkon më parë temperaturën, pastaj mundësinë e shiut, dhe më pas shtyp një rekomandim.
    
.. activecode:: console__more_branching_weather

    t = int(input("What is the temperature: "))
    chance_of_rain = int(input("What are the chances of rain: "))
    # finish the program

