Programimi me lista
====================

Këtu do të praktikojmë përdorimin e listave dhe ndërthurjen e teknikave që kemi mësuar deri më tani.


.. questionnote::

    **Shembull - numri më i vogël pozitiv**
    
     Jepet një numër numrash. Shtypni numrin më të vogël pozitiv nga ajo tuple.

Kjo detyrë është një ndërthurje e detyrave që kemi bërë deri më tani. Në pjesën e parë të detyrës kopjojmë numrat pozitivë nga tuples në listë, dhe në pjesën e dytë aplikojmë funksionin *min* në listën e numrave pozitiv.

.. activecode:: console__list_min_positive

    a = (-4, 3, 4, -3, 5, 6, 2, -5)
    positive = []
    for x in a:
        if x > 0:
            positive.append(x)

    print(min(positive))

Ne përmendëm se funksionet *min*, *max*, *sum*, *len* mund të zbatohen në koleksione të ndryshme, dhe ne e kemi treguar këtë me shembuj të tuple, varg dhe varg (përveç shumës së elementeve të një vargu). Tani shohim që funksioni *min* gjithashtu pranon një listë si argumentin e saj. E njëjta vlen për funksionet *max*, *sum*, *len*.

.. questionnote::

    **Shembull - dështimet**
    
     Ekzistojnë 10 makina në një fabrikë dhe ato përfaqësohen nga numrat nga 0 deri në 9. Për secilën mosfunksionim që ka ndodhur, është regjistruar numri i makinerisë që funksionon keq. Jepet një tufë me këta numra që përshkruajnë dështimet.

     Shkruaj një program që rendit sa herë secila prej makinave ka funksionuar keq, e ndjekur nga numri i makinave që nuk kishin dështuar kurrë.
        
.. activecode:: console__list_malfunctions

    failures = (0, 2, 1, 3, 2, 4, 2, 6, 4, 7, 4, 8)

Pjesa e parë e detyrës kërkon që të llogarisim numrin e herëve që secili numër shfaqet në të dhënat hyrëse. Për të zgjidhur këtë pjesë të detyrës, ne krijojmë listën *num_failures* të 10 elementeve (që janë fillimisht zero), në të cilat secili element korrespondon me një makinë dhe numëron dështimet e tij.

.. code::
    
    num_failures = [0] * 10
    for machine in failures:
        num_failures[machine] += 1

Pas kësaj, ne shtypim për secilën makinë sa dështime ka pasur. Ne përdorim vargun këtu sepse duam të shtypim numrin e sekuencës së makinës dhe numrin e dështimeve për secilën makinë:

.. code::

    for i in range(10):
        print('Machine', i, 'failed', num_failures[i], 'times.')

Pjesa e dytë e detyrës na kërkon të shtypim numrat e makinerisë që nuk kishin dështuar kurrë. Këto janë makina, numri i dështimeve i të cilave është zero. Ne përsërisim përsëri listën *num_function* përsëri dhe futim indekset e elementeve të barabarta me zero në listën e re, të quajtur *not_failed*:

.. code::

    not_failed = []
    for i in range(10):
        if num_failures[i] == 0:
            not_failed.append(i)
            
Ne printojmë elementët e listës *not_failed*.

.. code::

    print('Machines that did not break down:')
    for machine in not_failed:
        print(machine)

Ja si duket i gjithë programi:

.. activecode:: console__list_malfunctions_sol

    failures = (0, 2, 1, 3, 2, 4, 2, 6, 4, 7, 4, 8)
    num_failures = [0] * 10
    for machine in failures:
        num_failures[machine] += 1
        
    for i in range(10):
        print('Machine', i, 'failed', num_failures[i], 'times.')

    not_failed = []
    for i in range(10):
        if num_failures[i] == 0:
            not_failed.append(i)
            
    print('Machines that had never failed:')
    for machine in not_failed:
        print(machine)






.. questionnote::

    **Detyrë - tifozët e futbollit **

    Tifozët e futbollit nga 8 vende po vijnë në turne në qytet *X*. Organizatorët e turneut duan të dinë se sa tifozë vijnë nga secili vend.
    
    
     Çdo vend përfaqësohet nga një numër nga 0 në 7. Numrat e dhënë për secilin tifoz tregojnë se nga cili vend vjen nga ai. Përfundoni programin më poshtë që rendit për secilin vend sa tifozë vijnë prej tij.

Detyra kërkon që secili numër 0 deri 7 të numërojë sa herë shfaqet ai numër midis numrave të dhënë. Pjesa që mungon në skenar është shumë e ngjashme me numërimin e dështimeve në shembullin e dhënë.

.. activecode:: console__list_counters

    fans = (1, 2, 3, 2, 3, 0, 2, 4, 3, 5, 6, 4, 0, 5, 3, 7, 1, 6, 3)
    num_fans = [0] * 8
    for # complete the statement

    for country in range(8):
        print(num_fans[country], 'fans arrive from country', country)
        

.. commented out

    fans = (1, 2, 3, 2, 3, 0, 2, 4, 3, 5, 6, 4, 0, 5, 3, 7, 1, 6, 3)
    num_fans = [0] * 8
    for country in fans:
        num_fans[country] += 1

    for country in range(8):
        print(num_fans[country], 'fans arrive from country', country)






.. questionnote::

    **Detyrë - shumica e tifozëve **
    
    Kjo është vazhdimi i detyrës së mëparshme. Organizatorët tani përveç kësaj dëshirojnë të dinë nga cili vend vijnë tifozët.

     Kopjoni programin e mëparshëm dhe bashkëngjitni atë në mënyrë që përfundimisht të printojë numrin e vendit nga vjen shumica e tifozëve.

Nëse e kryeni detyrën si duhet, programi duhet të shtypë numrin 3, sepse ai numër shfaqet më shpesh në të dhëna.

.. questionnote::

.. activecode:: console__list_max_counter

    fans = (1, 2, 3, 2, 3, 0, 2, 4, 3, 5, 6, 4, 0, 5, 3, 7, 1, 6, 3)






.. questionnote::

    **Detyrë - Numri negativ më i madh**

    Jepet një grup numrash. Shtypni numrin më të madh negativ nga ajo tuple.

.. activecode:: console__list_max_negative

    a = (-4, 3, 4, -3, 5, 6, 2, -5)







.. questionnote::

    **Detyrë - shitje të vogla**

    Është dhënë tiple që përmban shumat e llogarive të klientëve në një rrjet shitjeje. Të gjitha shitjet me më pak se 500 konsiderohen shitje të vogla. Shkruani një program që llogarit të ardhurat totale nga të gjitha shitjet e vogla.

Ekzistojnë dy mënyra për të zgjidhur këtë detyrë. Njëra është të nxirrni sasi të vogla në një listë të veçantë dhe të aplikoni funksionin *sum* në atë listë. Një mënyrë tjetër është që gradualisht të ndërtojmë shumën, siç bëmë në mësimin për numërimin dhe përmbledhjen.

.. activecode:: console__list_sum_small_sales

    sales = (158, 681, 249, 1250, 335, 5400, 455)


