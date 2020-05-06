Numërimi dhe shuma
====================

Është një rast shumë i zakonshëm që ne interesohemi vetëm për disa nga të dhënat nga një koleksion. Këtu do të praktikojmë si të llogarisim dhe, nëse është e nevojshme, numrat e shumave që na interesojnë, ose që plotësojnë ndonjë kusht.


Numërimi
--------

Forma e përgjithshme e një programi (algoritmi) me të cilin numërojmë elementet e një koleksioni që plotësojnë një kusht të caktuar duket si kjo:


.. code::

    num = 0
    for x in collection:
        if (x meets the condition):
            num += 1
    print(num)
    
.. infonote::

    Deklarimi ``x + = a`` rrit vlerën e ndryshores *x* me *a*. Kjo është në të vërtetë një formë e shkurtuar e thënies :code: `x = x + a`, i cili i jep vlerën *x + a* variablës *x*.

     Deklarimi ``x - = a`` zvogëlon vlerën e ndryshores *x* me *a*. Kjo është një formë e shkurtuar e thënies :code:`x = x - a`, i cili i jep vlerën *x - a* variablës *x*.
    
Në shembullin tonë, pohimi *num + = 1* rrit vlerën e ndryshores *br* me 1.

Ushtrime dhe detyra
''''''''''''''''''

.. questionnote::

    **Shembull - takim:**
    
     Drejtuesi i ekipit ka ofruar dy mundësi për kohën e takimit që do të zhvillohet nesër. Secili anëtar i ekipit shkroi në një tabelë se cili term do të ishte më i përshtatshëm për të (1 për mandatin e parë, 2 për të dytin). Ky informacion u transferua në rreshtin e parë të programit vijues.
    
     Plotësoni skenarin e programit, në mënyrë që duke pasur parasysh të dhënat për votimin e anëtarëve të ekipit, ai shtyp se sa votuan për të parin dhe sa për mandatin e dytë.
    
.. activecode:: console__counting_meeting

    terms = (1, 2, 2, 1, 2, 2, 2, 1, 1, 1, 1, 2, 2, 2, 1)
    
Për shembull, ne mund të llogarisim numrin e anëtarëve të ekipit që votuan për mandatin e parë, dhe pjesën tjetër llogaritim në fund.

.. activecode:: console__counting_meeting_sol1

    terms = (1, 2, 2, 1, 2, 2, 2, 1, 1, 1, 1, 2, 2, 2, 1)

    num_first_term = 0
    for t in terms:
        if t == 1:
            num_first_term += 1
            
    num_second_term = len(terms) - num_first_term

    print(num_first_term, 'members voted for the first term and', num_second_term, 'for the second term.')

Një mënyrë tjetër është të llogaritni votat si për mandatin e parë ashtu edhe për atë të dytë.

.. activecode:: console__counting_meeting_sol2

    terms = (1, 2, 2, 1, 2, 2, 2, 1, 1, 1, 1, 2, 2, 2, 1)

    num_first_term = 0
    num_second_term = 0
    for t in terms:
        if t == 1:
            num_first_term += 1
        if t == 2:
            num_second_term += 1
    print(num_first_term, 'members voted for the first term and', num_second_term, 'for the second term.')

ose, duke supozuar se të dhënat janë "të pastra", d.m.th., nuk ka vlera përveç 1 dhe 2:

.. activecode:: console__counting_meeting_sol3

    terms = (1, 2, 2, 1, 2, 2, 2, 1, 1, 1, 1, 2, 2, 2, 1)

    num_first_term = 0
    num_second_term = 0
    for t in terms:
        if t == 1:
            num_first_term += 1
        else:
            num_second_term += 1
            
    print(num_first_term, 'members voted for the first term and', num_second_term, 'for the second term.')

Në rast se informacioni nuk dihet paraprakisht por duhet të futet, ne mund të shkruajmë një program si ky:

.. activecode:: console__counting_meeting_sol4

    n = int(input("How many team members voted: "))
    num_first_term = 0
    for i in range(n):
        t = int(input("Enter one vote: "))
        if t == 1:
            num_first_term += 1
            
    num_second_term = n - num_first_term
    print(num_first_term, 'members voted for the first term and', num_second_term, 'for the second term.')

Në fillim të këtij programi, ne ngarkojmë numrin e votave *n*, atëherë përdorim loop *for* për të përsëritur ngarkimin dhe numërimin e një votimi *n* herë.


.. questionnote::

    **Detyrë - provë me shkrim:**
    
     Disa njerëz morën testin e aftësisë së trafikut, që është parakusht për të marrë pjesën praktike të provimit. Një test konsiderohet i kaluar nëse numri i përgjigjeve të pasakta është më i vogël se ose i barabartë me 3.
    
     Në fillim të skenarit janë dhënë rezultatet e testit të një grupi kandidatësh (numri i përgjigjeve të pasakta për secilin person që e ka marrë testin). Plotësoni skenarin duke renditur sa kandidatë kanë kaluar testin.
    
.. activecode:: console__counting_test

    num_incorrect = (2, 5, 1, 0, 4, 2, 7, 1)
    passed = 0

    # add the missing statements here
    
    print(passed)
    
.. commented out
    
    passed = 0
    for x in num_incorrect:
        if x <= 3:
            passed += 1
    print(passed)



.. questionnote::

    **Detyrë - pishinë**
    
     Një grup fëmijësh po përgatitet një vizitë në pishinë. Çdokush më i vogël se 160 centimetra mund të shkojë vetëm në pishinën më të vogël. Organizatori interesohet se sa fëmijë janë nën 160 centimetra në mënyrë që të planifikojnë grupet.
    
     Lartësitë e fëmijëve jepen në fillim të programit. Përfundoni programin për të shtypur numrin e fëmijëve më të ulët se 160 centimetra.
    
.. activecode:: console__counting_swimmingpool

    heights = (160, 161, 174, 149, 153, 160, 158, 182, 144)
    
    


.. questionnote::

    **Detyrë - lagështia**
    
     Në një kopsht botanik, lagështia e tokës matet një herë në ditë për specie të rralla dhe të ndjeshme. Lagështia shprehet në numra nga 0 deri në 1, dhe kushtet për zhvillimin e bimëve konsiderohen të jenë të mira kur lagështia është midis 0.3 dhe 0.7 (përfshirë kufijtë).

     Vlerat e lagështisë (matur gjatë një periudhe kohe) jepen në fillim të skenarit. Plotësoni skenarin duke shtypur numrin e ditëve kur lagështia nuk ishte e mirë.

.. activecode:: console__counting_humidity

    humidity = (0.2, 0.5, 0.61, 0.40, 0.72, 0.51, 0.43, 0.35, 0.28)
    

Mbledhja
----------

Në një grup të madh të problemeve praktike, ne arrijmë në rezultat duke e ndërtuar gradualisht (akumuluar) atë ndërsa kalojmë nëpër të dhëna. Për shembull, nëse kemi nevojë për shumën e disa numrave, mund ta arrijmë atë në këtë mënyrë të përgjithshme:

.. code::

    total = 0
    for num in collection:
        total += num
    print(total)


Kur llogaritim shumën e të gjithë elementëve të një koleksioni, marrim të njëjtin rezultat duke thirrur funksionin *sum*:

.. code::

    print(sum(collection))

Do të përdorim formimin gradual të rezultateve kur na duhen vetëm disa elementë nga koleksioni, domethënë ato që plotësojnë kushtin e dhënë. Në këtë rast, algoritmi për llogaritjen e shumës në përgjithësi do të duket kështu:

.. code::

    total = 0
    for num in collection:
        if (num meets the condition):
            total += num
    print(total)

Për të marrë mesataren e të dhënave që plotësojnë një kusht, është e nevojshme të numërohen dhe të shtohen të dhëna të tilla, dhe pastaj të ndahen shumën e tyre sipas numrit të tyre. Në rastin e përgjithshëm, duket kështu:

.. code::

    total = 0
    counter = 0
    for num in collection:
        if (num meets the condition):
            total += num
            counter += 1
    print(total / counter)

Vini re se në Python, shuma dhe mesatarja e elementeve të zgjedhur të koleksionit mund të merren në një mënyrë më të shkurtër dhe më efikase. Ne zgjodhëm metodën e mësipërme sepse duket pothuajse e njëjtë si në gjuhët e tjera të programimit.

Shembuj dhe detyra
''''''''''''''''''

.. questionnote::

    **Shembull - Rezultati mesatar i testit të IQ:**
    
     Janë dhënë rezultatet e një testi IQ për një grup njerëzish. Një rezultat prej -1 do të thotë që personi nuk e ka marrë provën. Përfundoni programin duke shtypur mesataren e fituar në provë.

.. activecode:: console__accumulate_IQ

    iq_results = (-1, 98, 115, -1, 83, 130, 101, 122, -1, 108)

Ne mund ta shkruajmë programin kështu:

.. activecode:: console__accumulate_IQ_sol

    iq_results = (-1, 98, 115, -1, 83, 130, 101, 122, -1, 108)
    num_tested = 0
    iq_sum = 0
    
    for result in iq_results:
        if result != -1:
            iq_sum += result
            num_tested += 1

    if num_tested > 0:
        mean_iq = iq_sum / num_tested
        print('Mean IQ is', mean_iq)
    else:
        print('No one was tested.')


.. questionnote::

    **Detyrë - në detyrë: **
    
     Në Ndërmarrjen X, të gjithë punonjësit herë pas here mbeten në thirrje. Norma për periudhën e mëparshme është 20 orë telefonatë. Hourdo orë shtesë (mbi 20 orë) në telefon paguhet gjithashtu. Jepet numri i orëve të thirrjeve për secilin punonjës, dhe drejtori dëshiron të dijë numrin e përgjithshëm të orëve në telefon **mbi normën**.
    
     Përfundoni programin duke llogaritur dhe shtypur numrin e përgjithshëm të orëve jashtë orarit në telefon.
    
Nëse zgjidhni detyrën si duhet, duhet të merrni rezultatin 25 për të dhënat e dhëna, pasi :math:`(21-20)+(23-20)+(34-20)+(25-20)+(22-20)=25`.


.. activecode:: console__accumulate_overtime

    norm = 20
    hours_on_duty = (21, 23, 19, 34, 25, 22, 17)
    total_overtime = 0
    # complete the program
    
    print('Total overtime on call is', total_overtime)
    
.. commented out
    
    norma = 20
    hours_on_duty = (21, 23, 19, 34, 25, 22, 17)
    total_overtime = 0
    for hours in hours_on_duty:
        if hours > norm:
            total_overtime += (hours - norm)
    print('Total overtime on duty is', total_overtime)


.. questionnote::

   **Detyrë - rendimenti mesatar:**
    
     Në një pemishte pas vitit të tretë, monitorohet rendimenti i kumbullës për pemë. Pemët me rendiment nën 3 kilogram konsiderohen të dëmtuara ose të sëmura dhe do të nxirren jashtë.
    
     Jepet rendimenti i të gjitha pemëve në pemishte. Përfundoni programin duke llogaritur dhe shtypur rendimentin mesatar të pemëve të shëndetshme (me rendiment prej 3 kilogramë ose më shumë).

    
Ju duhet të merrni një rezultat prej afërsisht 14,757 për të dhënat e dhëna.

    
.. activecode:: console__accumulate_yield

    yield_per_plant = (11.3, 15.8, 9.5, 2.6, 21.1, 13.4, 17.9, 0.7, 14.3)
    
    # complete the program
