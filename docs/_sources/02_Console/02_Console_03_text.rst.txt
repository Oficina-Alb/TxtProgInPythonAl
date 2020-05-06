Vlerat tekst
=============

Përveç numrave të plotë dhe numrave realë, një nga llojet themelore të të dhënave në programim është teksti. Të dhënat e tekstit quhen një **varg**. Përveç shkronjave, ato mund të përmbajnë të gjitha karakteret e tjera të përdorura në tekst: shenjat e pikësimit, kllapat, numrat, operatorët matematikorë, karakteret e ndryshme speciale siç janë ``%``, ``$``, ``^``. ``&`` etj.

Vlerat e tekstit shkruhen midis thonjëzave. Ne e quajmë tekstin nën citate shënon një tekst **konstante** ose **fjalë për fjalë**. Citimet e vetme ``'...'`` dhe dyshet ``"..."`` mund të përdoren në mënyrë të barabartë në Python (është vetëm e rëndësishme që citimi të jenë i të njëjtit lloj në fillim dhe në fund të vargut). Për shembull:

.. code::

    s1 = 'One text'
    s2 = "Another text"

Ne do të përdorim vargun e fjalës për llojin e të dhënave tekstuale, si dhe për çdo shprehje, vlera e të cilit është ai lloj. Shembujt më të rëndësishëm të shprehjeve të vargjeve janë konstantet e tekstit (literalet) dhe ndryshoret që përmbajnë tekst.

Printimi i tekstit
---------------------

Vargjet printohen në të njëjtën mënyrë si të dhënat numerike. Vargu që duam të shtypim është specifikuar thjesht si një argument funksioni *print()* 

.. activecode:: console__text_hello

    print("Hello world!")

Kur funksioni *print()* ka argumente të shumta, këto argumente mund të jenë të llojeve të ndryshme:

.. activecode:: console__text_compute

    print('2+2 =', 2+2)

Kur përdorim argumente të shumta, i shkruajmë ato të ndara me presje (si me çdo funksion). Vlerat e të gjitha argumenteve të përcaktuara do të shtypen në të njëjtin rend, dhe do të ndahen nga një hapësirë.

Më shumë rreth shtypjes së numrave
-----------------------------------

Ndonjëherë rezultati i printuar duket i paligjshëm:

.. activecode:: console__text_format1a

    print(5/3)

Më shpesh nuk na duhen të gjitha këto shifra. Numrat realë mund të duken më të lexueshëm nëse përdorim funksionin *format*. Me këtë funksion (ndër të tjera) mund të specifikojmë sa shifra pas pikës dhjetore që duam të shfaqim:

.. activecode:: console__text_format1b

    x = 5/3
    s = format(x, '.2f')
    print(s)
    
Për të specifikuar numrin e vendeve dhjetore për t’u shfaqur, ne e quajtëm funksionin *format* si ky: argumenti i parë i funksionit është vlera që shtypim, dhe argumenti i dytë është përshkrimi i formatit të shtypjes. Në këtë përshkrim, pjesa '.2' do të thotë që duam dy vende dhjetore, dhe pjesa 'f', e shkurtuar nga *float*, do të thotë që japim një përshkrim për një numër real (lloji i numrave realë quhet *float*). Funksioni kthen një varg në të cilin shkruhet numri *x* siç përcaktohet.

Vini re se kjo shtypje e formatuar nuk e ndryshon vlerën e ndryshores *x*.

Ne e kemi shembur shembullin në hapa për ta bërë atë më të qartë, megjithëse ai gjithashtu mund të shkruhet në një rresht kodesh. Për shembull, për të shtypur me 4 vende dhjetore:

.. activecode:: console__text_format1c

    print(format(5/3, '.4f'))
    
~~~~

Kur shfaqim numra të shumtë realë njërin poshtë tjetrit, ne mund t'i bëjmë ato më të lexueshme duke rreshtuar pikat dhjetore. Për shembull, kjo mënyrë e shtypjes nuk është lehtësisht e kuptueshme:

.. activecode:: console__text_format2a

    print(-1.23)
    print(7251.7)
    print(84.15)

Për të marrë një vështrim më të lexueshëm, mund të përdorim funksionin  format* si ky:

.. activecode:: console__text_format2b

    print(format(-1.23, '8.2f'))
    print(format(7251.7, '8.2f'))
    print(format(84.15, '8.2f'))

Në përshkrimin '8.2f' numri 8 do të thotë që versioni tekstual i numrit të dhënë duhet të jetë i mbushur me hapësira (nëse është e nevojshme) për të zënë gjithsej 8 vende. Këto 8 vende përfshijnë shifrat, pikën dhjetore, shenjën e mundshme të numrit dhe hapësirat përpara numrit.

Pjesët e tjera të përshkrimit ('.2f') kanë të njëjtin kuptim si më parë.


Funksioni *format* ka shumë karakteristika të tjera, por ne nuk do t'i përdorim ato këtu.


Operacionet e vargut
-----------------------

Bashkimi i strings
'''''''''''''''''''

Vargjet mund të bashkohen së bashku me një operacion **string concatenation** . Ky operacion shënohet me shenjën ``+``, ashtu si operacioni i mbledhjes, kështu që në programimin bashkimi shpesh quhet joformalisht shtesë.

.. activecode:: console__text_concat1

    s = 'continu' + 'ation'
    print(s)

Ndonjëherë, ne mund të kemi një numër të plotë ose një numër të vërtetë të pangopur në një varg, kështu që është e rëndësishme të kuptojmë kur shenja ``+`` i referohet shtimit të numrave, dhe kur bashkimit të vargjeve. Për shembull, në programin vijues, e para *a + b* është shtimi i numrave, dhe e dyta është shtimi i vargjeve. Prandaj, rezultatet e shtypura gjithashtu ndryshojnë (provojeni).

.. activecode:: console__text_concat2

    a = 14.2
    b = 1
    print(a + b)
    
    a = '14.2'
    b = '1'
    print(a + b)

Ka të ngjarë që herë pas here të ngatërroheni nga rezultati kur ekzekutoni një program. Rezultati mund të jetë i ndryshëm nga sa pritej për shumë arsye, dhe një mundësi është që ju të shtoni pa dashje vargje në vend të numrave.

Karakteri ``+`` mund të qëndrojë midis dy shprehjeve numerike ose midis dy vargjeve, por jo midis një vargu dhe një numri (në çdo mënyrë). Kombinime të tilla rezultojnë në një *TypeError* (provojeni).

.. activecode:: console__text_concat3

    print('2' + 2)

Shumëzimi i vargut
'''''''''''''''''''''

Vargjet gjithashtu mund të shumëzohen. Kjo do të thotë që lejohet të shumëzoni një varg me një numër të plotë (qoftë nga e majta apo e djathta), dhe rezultati është një varg i ri, i cili fitohet duke përsëritur një varg të caktuar një numër të caktuar herë.

Në shembullin e mëposhtëm nënvizojmë numrat me një rresht, dhe kjo linjë merret si rezultat i shumëzimit të vargut '-' me 12.

.. activecode:: console__text_str_mult

    a = 1.23958
    b = 5467251.707256
    c = 384.150576
    total = a + b + c
    print(format(a, '12.2f'))
    print(format(b, '12.2f'))
    print(format(c, '12.2f'))
    print(12 * '-')
    print(format(total, '12.2f'))

    
Pyetje dhe detyra
-------------------

.. dragndrop:: console__text_quiz_format
    :feedback: Provo përsëri!
    :match_1: '12.34'|||format(12.34, '.2f')
    :match_2: '__12.34'|||format(12.34, '7.2f')
    :match_3: '_12.34'|||format(12.34, '6.2f')
    :match_4: '__12.3'|||format(12.34, '6.1f')
    :match_5: '12.3'|||format(12.34, '.1f')

    Përputhni thirrjet e funksionit *format* me rezultatet. Hapësirat përfaqësohen nga '_' pasi ato nuk do të ishin të dukshme.

.. mchoice:: console__text_quiz_quotes
    :answer_a: s = 'a' + "b"
    :answer_b: s = 'ab"
    :answer_c: s = 'ab'
    :correct: b
    :feedback_a: Provo përsëri
    :feedback_b: Saktë!
    :feedback_c: Provo përsëri
    
    Cili deklarim është gabim?

.. mchoice:: console__text_quiz_tralala
   :multiple_answers:
   :answer_a: print('tra' + 2 * '-la')
   :answer_b: print('tra-' + 2 * 'la-')
   :answer_c: print('tra-' + 'la-' + 'la')
   :answer_d: print('tra-' + 'la-la')
   :answer_e: print('tra-la-' + '-la')
   :correct: a, c, d

   Cili deklarim printon `` tra-la-la ''? (Kliko të gjitha përgjigjet e sakta)
       
.. dragndrop:: console__text_quiz_nanana
    :feedback: Provo përsëri!
    :match_1: 'NA' * 3 ||| 'NANANA'
    :match_2: 'N' + 3 * 'A' ||| 'NAAA'
    :match_3: 'N' * 3 + 'A' ||| 'NNNA'
    :match_4: 'N' * 3 + 3 * 'A' |||'NNNAAA'

    Match expressions with their values.

.. fillintheblank:: console__text_quiz_N_A

    What the statement **print(('N' + 'A') * 2)** prints?
    
    - :NANA: Saktë!
      :NNAA: Fillimisht, llogarit pjesën në kllapa (njësoj si numrat)
      :.*: Provo përsëri.

.. questionnote::

    * Detyrë - Ndarja e Fitimit **

     Të tre miqtë ranë dakord të ndajnë fitimet nga ndërmarrja e përbashkët, në mënyrë që i pari të merrte 2/7 të fitimeve, i dyti 1/3, dhe i treti shumën e mbetur. Fitimi i përgjithshëm ishte 40000. Plotësoni programin, i cili do të shtypë, në dy numra dhjetor, të ardhurat e secilit prej tre miqve.
    
.. activecode:: console__computing_earnings

    total_earnings = 40000
    first = total_earnings * 2 / 7
    second = 0 # fix the staement
    third = total_earnings - first - second
    # add statement(s) for printing

