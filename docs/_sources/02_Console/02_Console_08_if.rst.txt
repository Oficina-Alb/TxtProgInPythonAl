Deklarimet degëzuese
====================

Në mësimet e Karelit, sa herë që donim që Karel të shkonte përpara, duhej të kontrollonim së pari nëse Kareli mund të shkonte përpara. Këto kontrolle ishin të domosdoshme sepse nëse do të përpiqeshim ta lëviznim robotin përpara kur sheshi përpara tij të mos ekzistonte, programi do të raportonte një gabim dhe do të ndalonte së punuari. Për të njëjtën arsye, ne ishim duke kontrolluar nëse kishte ndonjë top në një shesh kuti se ta merrte, dhe ne ishim duke kontrolluar nëse Karel kishte një top me të para se të binte topi.

Në mënyrë të ngjashme, në programet me numra shpesh duhet të krahasojmë dy vlera, d.m.th., për të përcaktuar nëse ato janë të barabarta, nëse njëra është më e vogël se tjetra, e ndryshme nga tjetra dhe të ngjashme. Në varësi të rezultatit të krahasimit, programi mund të vazhdojë të ekzekutohet në mënyra të ndryshme.

Disa nga simbolet e përdorura për krahasim janë të njëjta si në matematikë (për shembull ``<`` dhe ``>``) dhe disa jo. Tabela e mëposhtme jep shënimin e të gjitha krahasimeve standarde të përdorura në matematikë dhe në Python (dhe gjithashtu në shumë gjuhë të tjera të programimit).

====================   ==================== ========================================
Math                   Python               Meaning
====================   ==================== ========================================
:math:`а < b`          a < b                a is less than b
:math:`a \leq b`       a <= b               a is less than or equal to b
:math:`a > b`          a > b                a is greater than b
:math:`a \geq b`       a >= b               a is greater than or equal to b
:math:`a = b`          a == b               a is equal to b
:math:`a \neq b`       a != b               a is not equal to b
====================   ==================== ========================================

Shënimi :math:`a <b` mund të kuptohet si një shprehje, vlera e së cilës është e vërtetë ose e rremë në secilin rast. Këto vlera janë shkruar në Python si *True* dhe *False* dhe ato janë **konstante logjike**, d.m.th., konstante të tipit ``bool`` të cilin ne i quajmë lloj logjik. Shprehjet, vlera e të cilave është e vërtetë ose e rremë (lloji logjik) quhen **shprehje logjike**. Të gjitha shprehjet në tabelën e mësipërme janë shprehje logjike (do të shohim më shumë shprehje logjike më vonë).

Deklarimi if
------------

Deklarimi *if* ishte futur tashmë në mësimet e Karelit, le të kujtojmë:

Deklarimi *if* përdoret për të vendosur se cili nga dy grupet e deklaratave për të ekzekutuar. Në Python shkruhet si më poshtë:

.. activecode:: console__if_else_syntax
   :passivecode: true

   if condition:
       statement_a1
       ...
       statement_ak
   else:
       statement_b1
       ...
       statement_bm

.. infonote::

    **Kuptimi (semantika) e deklarimit if:**
    
    Deklarimi shkruar më lart do të thotë: nëse kushti është përmbushur, ekzekutoni *statement_a1*, ... *statement_ak*, përndryshe ekzekutoni *statement_b1*, ... *statement_bm*.
    
    **Rregullat e të shkruarit (sintaksë) të deklarimit if**
    
    - Pas fjalës ``if``, është shkruar një shprehje logjike dhe në fund të rreshtit kërkohet karakteri ``:``.
    - Në rreshtat e mëposhtëm, të theksuar për të njëjtin numër hapësirash (zakonisht 4), janë shkruar deklarimet që duhet të ekzekutohen nëse shprehja logjike rezulton *True*. Mund të ketë një ose më shumë me këto deklarime.
    - Pas urdhrave që janë ekzekutuar nëse plotësohet kushti, shkruhet fjala ``else`` dhe përsëri karakteri ``:``. Fjala ``else`` shkruhet në të njëjtin nivel si fjala ``if``.
    - Në rreshtat e mëposhtëm, të indentifikuar për të njëjtin numër hapësirash, shkruajini komandat që duhet të ekzekutohen nëse shprehja logjike rezulton në *False*. Gjithashtu Mund të ketë një ose më shumë nga këto deklarime.
    
    Deklarimi ``if`` quhet edhe *thënie degëzuese* sepse rrjedhja e ekzekutimit të programit për këtë deklarim degëzon deklarimin tjetër për tu ekzekutuar dhe varet nga vlera e shprehjes logjike aktuale. Prandaj grupet e deklarimeve pas fjalës *if* ose *else* quhen edhe degë të deklarimit *if*.

Në rast se programi nuk ka nevojë të bëjë asgjë kur nuk plotësohet kushti i deklarimit *if*, d.m.th., kur nuk kemi nevojë për *if* degë të deklaratës *if*, mund ta heqim atë:

.. activecode:: console__if_syntax
   :passivecode: true

   if condition:
       statement_a1
       ...
       statement_ak

Ne do ta përdorim këtë formë të shkurtër të deklarimit *if* më vonë.

Deklarimi if - shembuj dhe ushtrime
''''''''''''''''''''''''''''''''''''

.. questionnote::
    
    **Shembull - kush është më i ri:**
    
     Peter dhe Marku duan të luajnë një lojë në pishinë. Ata ranë dakord që lojtari më i ri të luajë i pari. Shkruani një program që lexon moshën e Pjetrit dhe Markut (që nuk janë të barabartë) dhe cili që do të bëjnë lëvizjen e parë.
    
.. activecode:: console__branching_younger

    peter = int(input("Sa vjeç është Peter: "))
    mark = int(input("Sa vjeç është Mark: "))
    if peter < mark:
        print('Peter luan i pari.')
    else:
        print('Mark luan i pari.')





.. questionnote::
    
     **Shembull - paketim:**
    
     Vezët në fermë janë paketuar në kuti me 10 pako dhe kutitë e plota dërgohen në dyqan. Shkruani një program që merr numrin e vezëve gati për paketim dhe shtypni nëse të gjitha vezët mund të paketohen dhe dërgohen në dyqan, ose nëse disa vezë do të lihen të paketuara përkohësisht.
    
Këtu duhet të kontrollojmë që numri i vezëve është i ndashëm me 10. Për këtë arsye, ne përdorim operatorin ``%``, i cili jep pjesën e mbetur pas ndarjes. Nëse pjesa tjetër pasi të keni ndarë numrin e vezëve me 10 është e barabartë me zero, të gjitha vezët mund të paketohen dhe dërgohen.

.. activecode:: console__branching_eggs

    num_eggs = int(input("Sa vezë janë: "))
    if num_eggs % 10 == 0:
        print('Të gjitha vetët mund të dërgohen.')
    else:
        print('Disa vezë do të mbesin.')


.. questionnote::
    
    **Detyrë - Ana e rrugës: **
    
     Numrat e shtëpive janë në anën e djathtë të rrugës dhe numrat e shtëpive të çuditshme në të majtë. Shkruaj një program që merr një numër shtëpie dhe shtyp në cilën anë të rrugës numri është ndezur.


Këtu është e nevojshme të ekzaminohet nëse numri i dhënë është i ndashëm me 2. Detyra është e ngjashme me atë të mëparshme - nëse pjesa tjetër e ndarjes së numrit të shtëpisë së dhënë me 2 është e barabartë me zero, numri është në anën e djathtë të rrugës, përndryshe është në anën e majtë.

.. activecode:: console__branching_home_number

    number = int(input("Cili është numri i shtëpisë: "))
    # finish the program




.. questionnote::
    
    **Detyrë - kinema: **
    
     Ju keni 10 euro me vete. Shkruani një program që merr çmimin e biletave të filmit dhe çmimin e kokoshkave, atëherë shtypni nëse keni para të mjaftueshme si për biletën ashtu edhe për kokoshka.
    

.. activecode:: console__branching_cinema

    ticket_price = int(input("Sa kushtona bileta: "))
    popcorn_price = int(input("Sa kushtojne kokoshkat: "))
    # finish the program


Shprehjet logjike
-------------------

Në disa detyra duhet të shprehim kushte më komplekse sesa thjesht të krahasojmë dy vlera. Fjalët **and**, **or** dhe **no** përdoren për të lidhur termat më të thjeshtë, dhe Python përdor pikërisht të njëjtat fjalë për këtë. Ja se si të vlerësohen pohime të tilla komplekse. Nëse *a* dhe *b* janë kushte, atëherë:

- kushti ``a and b`` do përmbushen nëse të dyja kushtet *a* dhe *b* janë përmbushur;
- condition ``a or b`` çdo përmbushen nëse të paktën njëri kusht *a* dhe *b* është i përmbushur;
- condition ``not a`` do të përmbushet nëse kushti *a* nuk përmbushet (gjë që kemi përmendur tashmë në mësimet për Karelin);

Këto kushte mund të kombinohen më tej në kushte edhe më komplekse sipas nevojave të detyrës. Në kushte komplekse, ne mund të përdorim kllapa për të ndikuar në rendin në të cilin llogariten kushtet (gjithashtu kur nuk jemi të sigurt se cili është urdhri i paracaktuar), dhe ta bëjmë programin më të qartë për njerëzit e tjerë që e lexojnë atë. Nëse nuk ka kllapa në gjendje komplekse, *no* aplikohet së pari, atëherë *and*, dhe në fund *or*.

Shprehje logjike - shembuj
''''''''''''''''''''''''''''''

.. questionnote::
    
   **Shembull - vit i brishtë:**

     Shkruaj një program që shtyp nëse një vit i caktuar (midis 1800 dhe 2200, përfshirë kufijtë) është i thjeshtë ose i thjeshtë.
    
     Sipas kalendarit Gregorian, rregullat e mëposhtme përdoren për të përcaktuar nëse një vit është i thjeshtë apo i brishtë:
    
     - vitet që nuk janë të ndara me 4 (p.sh., 1923, 1070, 2017) janë të thjeshta;
     - vitet që janë të ndara me 100 dhe jo me 400 (p.sh. 1700, 1800, 1900, 2100, 2200) janë gjithashtu të thjeshta;
     - të gjitha vitet e tjera (p.sh. 1984, 2000, 2012) janë kërcime. Këto janë vite që janë të ndara me 4 dhe jo nga 100, ose janë të ndara me 400.

Duke shkruar këto rregulla në formën e kushteve logjike, marrim:

    
.. activecode:: console__branching_leap_year1

    year = int(input())
    if (year % 4 > 0) or (year % 100 == 0 and year % 400 > 0):
        print("Year", year, "is simple.")
    else:
        print("Year", year, "is leap.")

Ne marrim një zgjidhje po aq të mirë nëse përdorim përshkrimin për vitet e brishtë të dhënë në rregullin 3 (verifikoni duke menduar përmes tij dhe duke provuar të dy programet që kemi marrë të njëjtin rezultat):
    
.. activecode:: console__branching_leap_year2

    year = int(input())
    if (year % 4 == 0 and year % 100 != 0) or year % 400 == 0:
        print("Year", year, "is leap.")
    else:
        print("Year", year, "is simple.")


.. questionnote::

    **Shembull - orët e zyrës:**
    
     Orët e hapjes së një dyqani me suvenire janë nga 7 në 11 në mëngjes dhe nga 17 në 22 në mbrëmje (të konsiderohet se funksionon në 7:00 dhe në 17:00  dhe nuk funksionon në orën 11:00 dhe në 22:00). Peter erdhi nëpër dyqan në orën *H* orë dhe *M* minuta. Shkruani një program që merr numrin *H* (nga 0 në 23) dhe përgjigjet nëse Peter erdhi nëpër dyqan gjatë orarit të punës.
    
.. activecode:: console__branching_working_hours1

    h = int(input())
    if (7 <= h and h < 11) or (17 <= h and h < 22):
        print("Peter erdhi gjatë orarit të punës.")
    else:
        print("Peter erdhi jashtë orarit të punës.")
    
Ne gjithashtu mund të arrijmë në një zgjidhje duke llogaritur gradualisht vlerat logjike, duke përdorur variabla logjike:

.. activecode:: console__branching_working_hours2

    h = int(input())
    at_morning_office_hours  = 7 <= h and h < 11
    at_evening_office_hours = 17 <= h and h < 22
    at_office_hours = at_morning_office_hours or at_evening_office_hours
    if at_office_hours:
        print("Peter erdhi gjatë orarit të punës.")
    else:
        print("Peter erdhi jashtë orarit të punës.")

Në këtë zgjidhje, vetëm *h* është variabel integer, dhe të tjerat (*at_morning_office_hours*, *at_evening_office_hours*, *at_office_hours*) janë logjike, që do të thotë që marrin vlera *True* ose *False* kur programi ekzekutohet.

Shprehej logjike - pyetje
'''''''''''''''''''''''''''''''

.. dragndrop:: console__branching_quiz_compare
    :feedback: Provo përsëri!
    :match_1: a <= b ||| a < b or a == b
    :match_2: a >= b ||| b <= a
    :match_3: not (a == b) ||| a < b or a > b
    :match_4: not (a != b) ||| a == b

    Lidh shprehjet ekuivalente

.. mchoice:: console__branching_quiz_interval
   :multiple_answers:
   :answer_a: h < 7 and 11 <= h
   :answer_b: h < 7 or 11 <= h
   :answer_c: not(7 <= h) or not(h < 11)
   :answer_d: h <= 7 or 11 < h
   :correct: b, c
   :feedback_a: Jo, kjo gjendje nuk përmbushet për asnjë h.
   :feedback_b: Saktë.
   :feedback_c: Saktë.
   :feedback_d: Jo, vlera e kushteve ndryshon nëse h është saktësisht 7 ose 1

   A janë të gjitha kushtet e barabarta me **not (7 <= h and h <11)**?


.. dragndrop:: console__branching_quiz_abc_sign
    :feedback: Provo përsëri!
    :match_1: At least one of a, b, c is positive ||| a > 0 or b > 0 or c > 0
    :match_2: None of a, b, c is positive ||| a <= 0 and b <= 0 and c <= 0
    :match_3: a, b and c are not all positive ||| a <= 0 or b <= 0 or c <= 0
    :match_4: a, b and c are all positive ||| a > 0 and b > 0 and c > 0

    Lidh kushtet me përshkrimin

.. mchoice:: console__branching_quiz_sport_center
   :multiple_answers:
   :answer_a: (population <= 10000) or (population > 10000 and income <= 2000)
   :answer_b: population <= 10000 or income <= 2000
   :answer_c: population <= 10000 and income <= 2000
   :answer_d: (income <= 2000) or (income > 2000 and population <= 10000)
   :correct: a, b, d
   :feedback_a: Saktë.
   :feedback_b: Saktë.
   :feedback_c: Gabim.
   :feedback_d: Saktë.

   Qeveria e shtetit po ofron ndihmë për ndërtimin e një qendre sportive. Vendbanimet me deri në 10,000 banorë kanë të drejtë të aplikojnë, si dhe vendbanime me më shumë se 10,000 banorë dhe të ardhura mesatare deri në 2000. Cila nga kushtet kontrollon saktë nëse mund të aplikojë një zgjidhje?

Shprehje logjike - detyra
''''''''''''''''''''''''''

.. questionnote::

    **Detyrë - numra sipas radhës: **
    
     Shkruaj një program që merr numrat e plotë *a*, *b*, *c* dhe i përgjigjet pyetjes nëse këta numra janë dhënë në mënyrë që nga më i vogli te më i madhi.

    
.. activecode:: console__branching_increasing3

    a = int(input("a = "))
    b = int(input("b = "))
    c = int(input("c = "))
    # finish the program




.. questionnote::

    **Detyrë - Numri mesatar:** 
    
    Shkruaj një program që merr numrat e plotë *a*, *b*, *c* dhe i përgjigjet pyetjes nëse *b* është me madhësi mesatare. 

    
.. activecode:: console__branching_middlenum

    a = int(input("a = "))
    b = int(input("b = "))
    c = int(input("c = "))
    # finish the program
    
    
.. questionnote::

    **Task - vëzhgo qenin:** 
    
   Anna dhe Marku jetojnë së bashku dhe kanë një qen të quajtur Bobby. Të dy janë planifikuar të udhëtojnë në të njëjtin muaj, Anna nga dita *a1* në *a2*, dhe Marku nga dita *m1* në *m2*. Të dy largohen në mëngjes dhe kthehen në mbrëmje. Meqenëse nuk duan ta lënë Bobby-in vetëm, ata pyesin nëse udhëtimet e tyre mbivendosen.
    
     Shkruani një program që merr numrat e plotë *a1*, *a2*, *m1* dhe *m2* dhe përgjigjet në pyetjen nëse udhëtimet e Anës dhe Markut mbivendosen.
    
**Ndihmë:** udhëtimet mbivendosen nëse Marko largohet para se Ana të kthehet (dita e nisjes së Markut është më pak se ose e barabartë me ditën e kthimit të Anas) ose anasjelltas - nëse Ana largohet para se të kthehet Marko.

.. activecode:: console__branching_intervals

    a1 = int(input("a1 = "))
    a2 = int(input("a2 = "))
    m1 = int(input("m1 = "))
    m2 = int(input("m2 = "))
    # finish the program
    
    
