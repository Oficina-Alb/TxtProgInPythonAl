Listat
========

Deri më tani, ne kemi përmendur tuple dhe gamën si lloj koleksionesh, dhe kemi parë që tuples mund të përdoret gjithashtu si koleksion. Një tjetër koleksion shumë i rëndësishëm dhe i përdorur shpesh janë listat.

Lista vs tuples
----------------

Listat, si dhe tuples, mund të specifikohen duke numëruar elementët, përveç që elementët e listës janë shkruar midis kllapave katrore:

.. activecode:: console__collections_list1

    for x in [2, 5, 8, 3]:
        print(x)
        
Listat janë në shumë mënyra të ngjashme me tuples. Të gjitha tiparet e tuples të përmendura në kapitullin e koleksioneve vlejnë gjithashtu për listat:

- Një listë gjithashtu mund të vendoset në një ndryshore dhe anasjelltas - elementët e listës mund t'i caktohen një numri të përshtatshëm të variablave (me fjalë të tjera, një listë mund të paketohet dhe paketohet sërish)
- elementët e listës mund të arrihen duke përdorur emrin e listës dhe numrin e sekuencës (indeksin) e elementit të shkruar në kllapa katrore
- gjatësia e listës merret nga funksioni *len*

.. activecode:: console__collections_list2

    names = ["Tom", "Polly", "Filip", "Mary"]
    t, p, f, m = names
    print("p =", p)
    print("names[0] =", names[0])
    print("len(names) =", len(names))

Listat gjithashtu kanë disa veçori që i veçojnë ato nga tuples. Për shembull, listat mund të zgjaten duke përdorur funksionin *append*:
    
.. activecode:: console__collections_list_append

    a = []
    a.append(3)
    a.append(7)
    a.append(2)
    
    for x in a:
        print(x)
    
Gjithashtu, elementët e listës mund të ndryshojnë vlerat e tyre dhe mund të fshihen nga lista:

.. activecode:: console__collections_list_mutable

    a = [3, 7, 2]
    print("Lista fillestare:")
    for x in a:
        print(x)
        
    a[0] = 5
    print("Lista e ndryshuar:")
    for x in a:
        print(x)

    del a[1]
    print("Lista e shkurtuar:")
    for x in a:
        print(x)

Operacione të tilla me tuples nuk janë të mundshme. Pasi të jetë bërë, tuples mbetet ashtu siç është. Një tuple nuk mund të modifikohet - nuk mund të ndryshojë gjatësinë e saj ose vlerat e elementeve individuale. Një variabël që përmban një lloj të dhëne mund të marrë vetëm një kthesë krejt të re si një vlerë, megjithatë duke e bërë këtë, tuple e mëparshme nuk u modifikua por pushoi së ekzistuari. Kjo është arsyeja pse thuhet se tuples janë të pandryshueshëm.

Tuples mund të përdoren për koleksione të të dhënave që ne nuk kemi ndërmend t'i modifikojmë gjatë ekzekutimit të një programi (megjithëse mund t'i ndryshojmë ato manualisht para ekzekutimit të një programi). Duke përdorur tuples, ne sigurojmë që të dhënat nuk do të ndryshojnë aksidentalisht, dhe programi do të funksionojë pak më me efikasitet me konfiskimin sesa do të bënte me listën.

Tuple *t* mund të shndërrohet në një listë *a* gjatë ekzekutimit të programit, dhe anasjelltas: ``a = list (t)`` ose ``t = tuple (a)``, por konvertime të tilla rrallë janë të nevojshme dhe më mirë t’i shmangni ato (nëse ato shpesh aplikohen në koleksione të mëdha, shndërrimet si kjo mund ta ngadalësojnë programin në mënyrë të konsiderueshme).

Ndërtimi i një liste
-----------------------

Siç kemi parë tashmë, gradualisht mund të ndërtojmë lista në një program. Për shembull, nëse na jepen një grup numrash nga të cilët duam të kopjojmë ato që janë më të mëdha se zero (dhe të kryejmë disa detyra shtesë me këto numra më vonë), mund ta bëjmë këtë:

.. activecode:: console__collections_list_create

    numbers  = (2, 5, -2, 1, -3, 4, -7, 3)
    positive_numbers = []
    for x in numbers:
        if x > 0:
            positive_numbers.append(x)
            
    for x in positive_numbers:
        print(x)

Në fillim kemi një listë të zbrazët, dhe më pas në loop përdorim funksionin *append* për të shtuar në listë elementët që duam.


Mbushja e listës
-------------------

Në të njëjtën mënyrë, ne mund t'i ngarkojmë të dhënat në një listë:

.. activecode:: console__collections_list_read1

    a = []
    n = int(input("Sa element të vensdos: "))
    for i in range(n):
        x = float(input("Vendosni një element: "))
        a.append(x)

    print("Elementët e listës janë:")
    for x in a:
        print(x)


Një mënyrë tjetër për të mbushur një listë është së pari të formoni një listë të gjatësisë së kërkuar dhe më pas t'i caktoni vlerat e ngarkuara direkt në elementët e listës në loop.

.. activecode:: console__collections_list_read2

    n = int(input("Sa elementë të vendos: "))
    a = [0] * n
    for i in range(n):
        a[i] = float(input("Vendosni një element: "))

    print("Elementët e listës janë:")
    for x in a:
        print(x)

Ne përdorimin deklarimin ``a = [0] * n`` për të krijuar një list me *n* elementë. Operanti ``[0] * n``  përdoret për shtimin e listave. Rezultati i shumëzimit të listës është bashkimi i përsëritjeve *n* të listës së dhënë. Për shembull, [0] * 5 është lista [0, 0, 0, 0, 0], dhe [2, 7] * 3 është [2, 7, 2, 7, 2, 7].

Nëse përdoruesi hyn në të gjithë elementët e listës në një rresht të ndarë me hapësirat, ne shkruajmë programin si ky:

.. activecode:: console__collections_list_read_line

    a_str = input("Vendosni të gjithë elementët: ")
    a = []
    for s in a_str.split():
        a.append(float(s))

    print("Elementët e listës janë:")
    for x in a:
        print(x)

Ne kemi përdorur funksionin *split ()* për të analizuar tekstin e futur në vargje më të shkurtër që përmbajnë numra individualë.


.. infonote::
    
    **fuksioni** *split()*:
    
Parametri i funksionit *split() * është një karakter ose tekst që duam të përdorim si ndarës. Nëse një ndarës nuk është specifikuar, një hapësirë ``' '`` merret si e mirëqënë.
    
    :code:`"1234 56".split() -> ["1234", "56"]`
    
    :code:`"1234,56".split(',') -> ["1234", "56"]`
    
Rezultati i funksionit *split ()* është një listë string. Numri i vargjeve më të shkurtër që marrim si rezultat varet nga numri dhe faqosja e karaktereve ndarës në vargun fillestar. Për shembull, nëse teksti përmban vetëm një ndarës diku në mes, do të marrim dy tuples më të shkurtër. Çdo paraqitje e re e karakterit ndarës mund të prodhojë një varg më shumë në listën rezultuese (nëse me të vërtetë ndan një pjesë të vargut fillestar nga pjesa tjetër e tekstit).
    
    :code:`"1;23;456;7".split(';') -> ["1", "23", "456", "7"]`
    
    :code:`" 1  234    56 7 ".split() -> ["1", "234", "56", "7"]`
    

Shembuj dhe ushtrime
''''''''''''''''''''''

.. questionnote::

    **Shembull - shitje**
    
     Në fillim të skenarit, jepen vlerat e disa shitjeve në një dyqan. Nxirrni shitjet me një vlerë më të madhe se 1000 dhe më pak se ose e barabartë me 4000 në një listë, pastaj printoni elementët e listës jashtë.

.. activecode:: console__collections_list_sales

    sales = (241, 5372, 1278, 9335, 2438, 127, 529, 6027)
    lower_bound = 1000
    upper_bound = 4000
    # complete the program

Problemi tgjidhet si më poshtë:

.. activecode:: console__collections_list_sales_sol

    sales = (241, 5372, 1278, 9335, 2438, 127, 529, 6027)
    lower_bound = 1000
    upper_bound = 4000

    requested_sales = []
    for value in sales:
        if value > lower_bound and value <= upper_bound:
            requested_sales.append(value)

    print('Requested sales:')
    for value in requested_sales:
        print(value)


.. questionnote::

    **Shembull - Ndryshimet në kërcime**
    
     Jepet një grup numrash. Nxirr numrat që ndryshojnë nga paraardhësit e tyre të paktën me 10, pastaj printoni ato.

.. activecode:: console__collections_list_increasing

    numbers = (5, 7, 9, 11, 22, 18, 15, 13, 36, 31, 27, 14, 13, 20)
    # complete the program

Një zgjidhje e mundshme është:

.. activecode:: console__collections_list_increasing_sol

    numbers = (5, 7, 9, 11, 22, 18, 15, 13, 36, 31, 27, 14, 13, 20)
    leap_changes = []
    
    for i in range(1, len(numbers)):
        if abs(numbers[i] - numbers[i-1]) >= 10:
            leap_changes.append(numbers[i])

    print('Leap changes:')
    for x in leap_changes:
        print(x)





.. questionnote::

    **Detyrë - numrat**
    
     Jepen disa numra. Nxirrni numrat që janë njëlloj dhe më pas printoni ato.
    
    Kujtojmë që numri *x* është edhe nëse :math:`x \% 2 == 0`

.. activecode:: console__collections_list_even

    a = (35, 12, 32, 17, 64, 98, 77, 46, 9)
    even = []
    
.. commented out

    for x in a:
        if x % 2 == 0:
            even.append(x)

    print('Even numbers:')
    for x in even:
        print(x)




.. questionnote::

    **Detyrë - çdo fjalë e tretë**
    
     Jepet një gruo tuples. Ngjyrat e ekstraktit **indekset e të cilave** janë të ndara me 3, pastaj shtypni ato.
    
.. activecode:: console__collections_list_every_third

    words = ('All', 'the', 'other', 'words', 'and', 'phrases', 'are', 'not', 'so', 'important')
    every_third = []
    
.. commented out

    for i in range(len(words)):
        if i % 3 == 0:
            every_third.append(words[i])

    print('Every third word:')
    for rec in every_third:
        print(rec)




.. questionnote::

    **Detyrë - nën zero**
    
     Jepet disa numra. Nxirr numrat që janë negativ dhe paraardhësit e tyre janë pozitivë, më pas printoni numrat e nxjerrë.
    
.. activecode:: console__collections_list_neg_after_pos

    a = (1, -2, 3, 5, -4, -1, -3, 2, -7)
    extracted = []
    
.. commented out

    for i in range(1, len(a)):
        if a[i] < 0 and a[i - 1] > 0:
            extracted.append(a[i])

    for x in extracted:
        print(x)
