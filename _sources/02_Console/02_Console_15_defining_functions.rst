Definimi i funksioneve
========================

Në pjesën kushtuar administrimit të Karelit, përmendëm se mund të veçojmë një grup komandash në një entitet të veçantë të quajtur një funksion. Le të kujtojmë se si duket një funksion i shkruar në Python:

.. activecode:: Console__functions__function_def
    :passivecode: true

    def function_name(argument_list):
        statement_1
        ...
        statement_k
        
Rregullat e mëposhtme zbatohen për funksionet e shkrimit në Python:

.. infonote::

    **Rregullat e shkrimit të funksionit:**
    
    - Përcaktimi i funksionit fillon me fjalën ``def``, e ndjekur nga emri i funksionit, pastaj një listë argumentesh në kllapa dhe karakteri ``:`` në fund të rreshtit.
    - Çdo emër i shkruar siç duhet mund të paraqitet si një *function_name* (rregullat janë të njëjta si për emrat e ndryshueshëm).
    - Një listë e zbrazët (asgjë) mund të shfaqet si *argument_list* nëse funksioni nuk përdor argumente, ose një ose më shumë argumente të ndara me presje.
    - Çdo deklarim në Python mund të shfaqet në trupin e funksionit ( *statement_1*, ... *statement_k*). Këto komanda janë shkruar me theks në lidhje me rreshtin që përmban emrin e funksionit dhe argumentet.

Funksionet mund ose nuk mund të kthejnë ndonjë vlerë. Deri më tani kemi pasur mundësinë të shohim të dy llojet e funksioneve. Për shembull, funksionet me të cilat Karel (roboti) lëviz përpara, kthehet rrotull, mbledh lart dhe largon topat janë të gjitha funksionet që nuk kthejnë asnjë vlerë. Nga ana tjetër, funksionet matematikore si *abs* ose *round*, si dhe funksionet për të kontrolluar nëse Karel ka topa me të, nëse ka ndonjë top në shesh, apo nëse Karel mund të shkojë përpara janë funksione që kthehen a vlera.

Funksionet e shkrimit që kthejnë vlerën
-----------------------------------------

Në mënyrë që një funksion të kthejë një vlerë, është e nevojshme të specifikoni deklarimin ``return`` të paktën një herë në trupin e funksionit. Deklarimi ``return`` përbëhet nga fjala *return*, e ndjekur nga një shprehje, vlera e së cilës funksioni është të kthehet.

.. activecode:: console__functions_return_example

    def square(x):
        return x * x
    
    print(square(3))

Deklarimi *return* mund të shfaqet në shumë vende në një funksion (zakonisht me vlera të ndryshme), dhe duhet të specifikohet në fund të trupit të funksionit. Funksioni *abs* mund të përkufizohet si më poshtë:

.. activecode:: console__functions_def_abs
    :passivecode: true

    def abs(x):
        if x > 0:
            return x
        else:
            return -x
    
Një funksion mund të kthejë më shumë se një vlerë. Një funksion i tillë është funksioni i integruar *divmod*, i cili kthen dy numra - rezultat i ndarjes së numrit të plotë dhe kujtesë. Ne përdorim funksionin *divmod* siç bëjmë me funksionet që kthejnë një vlerë të vetme, ne vendosim vetëm vlerat e kthyera në shumë ndryshore:

.. activecode:: console__functions_divmod_example

    quotient, reminder = divmod(813, 10)
    print('The quotient is', quotient, 'and the remainder', reminder)
    

Kur shkruajmë funksione që kthejnë shumë vlera, është e mjaftueshme të specifikojmë vlera të ndara me presje pas fjalës *return*. Nëse do ta përcaktonim vetë funksionin e integruar *divmod*, mund ta shkruajmë kështu:

.. activecode:: console__functions_divmod_def
    :passivecode: true

    def divmod(a, b):
        return a // b, a % b

Shembuj
''''''''

.. questionnote::

    **Shembull - lyerje:**
    
     Për të lyer :math: 1m ^ {2}` e mureve kërkon rreth :math:`0.5kg` e bojës. Shkruaj një funksion që pranon 4 argumentet e mëposhtme:
    
     - gjatësia e dhomës
     - gjerësia e dhomës
     - lartësia e dhomës
     - gjatësia që nuk duhet të pikturohet (gjerësia totale e dyerve, dritareve, dollapëve, etj.)

     Funksioni duhet të kthejë sasinë e bojës (në kilogram) që kërkohet për të pikturuar muret dhe tavanet.
    
     Pas funksionit, shkruani një program që ngarkon të dhënat për 5 dhoma të ndryshme, dhe më pas duke përdorur funksionin e shkruar llogarit dhe shtyp shumën totale të bojës të nevojshme për të pikturuar të pesë dhomat.

.. activecode:: console__functions_paint2


    def paint_needed(a, b, h, not_to_paint):
        coverage = 0.5 # how many kilograms per square meter
        ceiling = a*b
        walls = h * (2*a + 2*b - not_to_paint)
        area_to_paint  = ceiling + walls
        return area_to_paint * coverage
        
    total_paint_needed = 0
    for i in range(5):
        s = input('Enter the length, width and height of the room, and the non-painting length').split()
        total_paint_needed += paint_needed(float(s[0]), float(s[1]), float(s[2]), float(s[3]))

    print("Nevojitet", total_paint_needed, "kilogramë bojë")  


Ushtrime
'''''''''''''''''''

.. questionnote::
    
    **Detyrë - koordinatat gjeografike në formatin GP**

    Ju gjetët një hartë të vjetër të thesarit të varrosur dhe lexoni koordinatat e thesarit në gradë, minuta dhe sekonda. Sidoqoftë, pajisja juaj GPS mbështet vetëm koordinatat gjeografike në shkallë si numra realë (noton).
    
    Shkruaj një program që për një koordinatë të caktuar në gradë, minuta dhe sekonda, shtyp një numër real të gradave.

Programi është shkruar pothuajse plotësisht. Duhet shtuar një shprehje për të llogaritur numrin real të gradave. Për ta shndërruar minutat (këndore) në shkallë, ne i ndajmë ato në :math:`60`, dhe i kthejmë sekondat në shkallë duke i ndarë me :math:`60 \ cdot 60 = 3600`.

.. activecode:: console__functions_GPS_1

   degrees = int(input())
   minutes = int(input())
   seconds = int(input())
   
   def deg_min_sec_to_degrees(deg, min, sec):
        # complete the function
   
   float_degrees = deg_min_sec_to_degrees(degrees, minutes, seconds)
   print(float_degrees)



.. questionnote::

    **Detyrë - Koordinatat gjeografike në formatin për hartën e vjetër**
    
     Pasi e kuptuat që harta e vjetër nga detyra e mëparshme ishte një shaka, vendosët të bëni një shaka të ngjashme me dikë. Ju keni zgjedhur një vendndodhje afër dhe lexoni koordinatat nga pajisja juaj GPS. Tani ju duhet të ktheni koordinatat nga pajisja në shkallë reale në shkallë të tërë, minuta të tëra dhe sekonda të rrumbullakosura, për të krijuar një hartë të duhur "të vjetër".

Përfundoni programin e filluar që kryen këtë konvertim.

.. activecode:: console__functions_GPS_2

    def deg_min_sec(real_degrees):
        # complete the function by calculating three values that the function returns
        # (and then remove the comment from the following line of code)
        # return whole_degrees, whole_minutes, whole_seconds

    real_degrees = float(input())
    whole_deg, whole_min, whole_sec = deg_min_sec(real_degrees)
    print(whole_deg, whole_min, whole_sec)



.. questionnote::

    **Task - Plumber:** 
    
    **Detyra - Hidraulik:**
    
     Mike është hidraulik dhe ka tre ndërhyrje të planifikuara për sot. Për çdo ndërhyrje, Majk do të regjistrojë kur filloi dhe kur përfundoi. Bazuar në atë informacion, duhet të llogaritet se sa kohë kaloi Majk në ndërhyrjet.
    
     Është dhënë një program i shkruar pjesërisht që ngarkon herë fillimin dhe mbarimin në orë dhe minuta për secilës ndërhyrjen, dhe më pas përcakton dhe shtyp kohëzgjatjen totale të të gjitha ndërhyrjeve.
    
     **Përfundoni programin** duke shkruar funksionin *kohëzgjatjen (h1, m1, h2, m2)*, i cili llogarit sa minuta të përgjithshme kanë kaluar nga *h1* orë dhe *m1* minuta në *h2* orë dhe *m2* minuta.
    
.. activecode:: console__functions_plumber

    # write the duration function

    def process_one_intervention():
        prompt = "Enter the hour and minute of start and hour and minute of completion of the intervention "
        s1, s2, s3, s4 = input(prompt).split()
        h1, m1, h2, m2 = int(s1), int(s2), int(s3), int(s4)
        return duration(h1, m1, h2, m2)
        
    t1 = process_one_intervention()
    t2 = process_one_intervention()
    t3 = process_one_intervention()
    total_minutes = t1 + t2 + t3
    num_hours = total_minutes // 60
    num_minutes = total_minutes % 60
    print("The interventions lasted a total of", num_hours, "hours and", num_minutes, "minutes")


Funksionet që nuk kthejnë vlerë
----------------------------------

Funksionet që nuk i kthejnë vlerat thjesht bëjnë disa punë dhe ne i përdorim ato si komanda. Të tilla ishin, për shembull, funksionet *back ()* ose *take_at_neighboriz_square ()*, të cilat ne i shkruajtëm në një seksion kushtuar menaxhimit të Karelit. Le të shohim një shembull të një funksioni të tillë në një program me një ndërfaqe teksti.

.. questionnote::

    **Shembull - transporti:**
    
    Duhen përkatësisht 55, 35, 40 dhe 20 minuta për anëtarët e një familjeje prej katër anëtarësh për të arritur në shtëpi nga ku janë, me kusht që ata të fillojnë të shkojnë në shtëpi para orës 4 pasdite. Përndryshe ata do kenë nevojë për 15 minuta më shumë.
    
    Shkruaj një program që ngarkon kohën e nisjes në orë dhe minuta për secilin anëtar të familjes dhe rendit kohën e mbërritjes në shtëpi.
    
Funksioni *process_family_member* kryen të gjitha veprimet e nevojshme për një anëtar të familjes: ngarkon kohën e nisjes, sesa në bazë të kohës së nisjes ajo zgjat kohëzgjatjen e udhëtimit nëse është e nevojshme, pastaj llogarit dhe kopjon kohën e mbërritjes në shtëpi. Në programin kryesor, ky funksion thirret vetëm për secilin anëtar të familjes.

.. activecode:: console__functions_transport

    def process_family_member(which_one, travel_duration):
        prompt = 'Enter the hour and minute of departure of the ' + which_one + ' member'
        s_hour, s_min = input(prompt).split()
        departure_hour, departure_minute = int(s_hour), int(s_min)
        if departure_hour >= 16:
            travel_duration += 15
        arrival_total_minutes = departure_hour * 60 + departure_minute + travel_duration
        arrival_hour = arrival_total_minutes // 60
        arrival_minute = arrival_total_minutes % 60
        print('The', which_one, "member arrived home at", arrival_hour, "hours and", arrival_minute, "minutes.")
        
    process_family_member("first", 55)
    process_family_member("second", 35)
    process_family_member("third", 40)
    process_family_member("fourth", 20)


Ushtrime
'''''''''''''''''''

.. questionnote::

   **Detyrë - zbritje:**
    
     Një prodhues ofron mallra me një çmim prej 10 euro një copë, dhe për porositë prej 50 ose më shumë copë jepet zbritje prej 10%. Disa blerës njoftuan se ata po vinin për të blerë një numër të caktuar copash. Emrat e klientëve dhe sasitë e kërkuara janë dhënë në fillim të programit.
    
     Shkruaj një funksion i cili për emrin e dhënë të klientit dhe sasinë e mallrave shtyp se sa duhet të paguajë ai klient.

Emri i klientit i kalohet këtij funksioni vetëm për qëllime printimi. Çmimi i mallrave llogaritet në bazë të sasisë, e cila i kalohet funksionit si një argument i dytë.

.. activecode:: console__functions_discount

    # define the function print_price

    customers = ('Oliver', 'Freddie', 'Sophia', 'Lucas')
    quantities = (70, 28, 150, 6)
    n = len(customers)
    for i in range(n):
        print_price(customers[i], quantities[i])


.. questionnote::

   **Detyra - nënvizimi i tekstit:**

     Shkruani funksionin *underline* (tekstin) , i cili tregon tekstin e dhënë të nënvizuar.
    
**Këshillë:** Funksioni *underline* duhet të përbëhet nga vetëm dy deklarata *të printuara*. Deklarata e parë duhet të shtypë tekstin e dhënë, dhe e dyta duhet të shtypë rreshtin. Ju mund të merrni një varg që përmban një rresht duke shumëzuar vargun ``'-'`` me gjatësinë e vargut të dhënë.

.. activecode:: console__functions_underlined_text

    # define the function 'underline'
    
    underline("From Celsius to Fahrenheit:")
    for c in range(15, 46, 5):
        print(c, '°C =', round(c * 9 / 5 + 32, 1), '°F.')
    print()
    
    underline("From Fahrenheit to Celsius:")
    for f in range(50, 111, 10):
        print(f, '°F =', round((f-32) * 5 / 9, 1), '°C.')

.. commented out

    def underline(text):
        print(text)
        print('-' * len(text))

~~~~

Më në fund, le të përmendim disa nga përfitimet e funksioneve të shkrimit që, për shkak të shkurtësisë së shembujve dhe detyrave tona, nuk mund të dilnin në pah:

- Funksionet në programe të gjata shpesh përdoren për të dekompozuar pjesën kryesore të një programi dhe ta bëjnë atë më të shkurtër dhe më të lehtë për tu kuptuar. Programet tona nuk janë aq të gjata sa do të ishte e nevojshme dekompozimi i tyre, por ato tregojnë se si mund të bëhet me programe më të gjata.
- Funksionet mund të na ndihmojnë të shmangim përsëritjen e kodit të njëjtë ose të ngjashëm në programe. Përsëritja e kodit duhet të shmanget pasi kodi i tillë është më i vështirë për tu ruajtur - çdo ndryshim duhet të bëhet në vende të shumta, gjë që është e lodhshme dhe i nënshtrohet gabimeve dhe mosveprimeve.
- Kur shkruajmë funksione, u mundësojmë të tjerëve të përdorin më lehtë pjesë të kodit tonë. Funksionet që ne shkruajmë mund të nxirren në një modul të veçantë, të cilin njerëzit e tjerë mund t’i përfshijnë lehtësisht në programet e tyre.
- Për programe shumë të mëdha, formimi i funksioneve lejon që programi të ndahet në skedarë të shumtë në vend të një skedari të madh dhe të pakuptueshëm.
