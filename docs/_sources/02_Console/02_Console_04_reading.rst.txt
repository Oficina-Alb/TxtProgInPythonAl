Leximi i të dhënave
====================

Teksti i leximit
----------------

Programet që kemi mësuar të shkruajmë deri tani përmbajnë të gjithë informacionin e nevojshëm dhe gjithmonë funksionojnë në të njëjtën mënyrë. Kur na duhet një program për të bërë të njëjtën gjë me të dhëna të ndryshme, do të na duhet të modifikojmë vetë programin. Kjo metodë mund të jetë mjaft e përshtatshme kur ndryshimet në të dhëna janë të vogla dhe jo të shpeshta.

Një mënyrë tjetër për të marrë programin tonë për të trajtuar detyra më të ndryshme është të mundësoni futjen e të dhënave. Futja e të dhënave në një program gjatë ekzekutimit të tij bëhet duke përdorur funksionin *input ()*. Ky funksion funksionon duke pritur që përdoruesi i programit të shkruajë diçka (dhe shtypni butonin *Enter*) dhe pastaj kthimin e tekstit të shtypur si rezultat.

Kur drejtoni këtë program, për të parë se si funksionon, shtypni diçka dhe shtypni *Enter*. Provoni të njëjtin program në mjedisin *IDLE * ose në faqen *repl.it*.

.. activecode:: console__text_input_first

    s = input()
    print("You wrote", s)

Programi funksionon siç përshkruhet, por kjo sjellje e programit mund të jetë konfuze. Nëse dikush do të drejtonte një program si ky në mjedisin *IDLE* pa e ditur që programi priste të dhëna, mund të dukej sikur kompjuteri i tyre ishte i kyçur sepse asgjë nuk po ndodhte, dhe në fakt programi ishte thjesht duke pritur hyrjen nga tastiera.

Për të ndihmuar përdoruesin të kuptojë se çfarë pritet prej tyre, ne gjithashtu mund të përdorim formën e funksionit *input* me një argument të vetëm teksti, i cili do të shtypet si një udhëzues për përdoruesit. Për shembull:

.. activecode:: console__text_input_prompt

    s = input("Write something: ")
    print("You wrote", s)

Nëse zgjedhim njërën ose formën tjetër të funksionit *input*, varet nga qëllimi i programit. Kur shkruajmë një program në të cilin njerëzit e tjerë do të futin të dhëna, ne përdorim një formë me një argument, duke shërbyer si një udhëzim. Kur shkruajmë një program vetëm për përdorim personal afatshkurtër (mbase edhe një herë), atëherë nuk kemi nevojë për udhëzime dhe mund të përdorim një formë pa argumente.

Gjithashtu, jini të vetëdijshëm që për disa prej mjediseve në të cilat programi po funksionon, ne mund të organizojmë që të dhënat po lexohen nga një lokacion tjetër, ku i kemi përgatitur ato paraprakisht, në vend që të lexojmë të dhënat nga tastiera. Në raste të tilla nuk ka pritje për të hyrë në të dhënat, ato ngarkohen automatikisht dhe nuk ka nevojë të shtypni udhëzimin. Prandaj, në raste të tilla do të përdorim edhe funksionin *input* pa argumente.

Numrat e leximit
-----------------

Ne kemi parë që funksioni *input()* kthen një varg (tekst i shtypur nga një përdorues). Kjo do të thotë që nëse kemi nevojë për të dhëna të një lloji tjetër, duhet të ndryshojmë llojin e të dhënave të kthyera nga funksioni *input ()* nga vargu në llojin e dëshiruar. Ndryshimi i llojit të të dhënave quhet edhe **konvertim**. Për shembull, nëse duam një numër të plotë, atëherë duhet të shndërrojmë tekstin që rezulton në një numër të plotë. Ja se si ta bëni atë në Python:

.. activecode:: console__text_input_int1

    s = input("Enter a whole number: ")
    n = int(s)
    print(n+n)

Funksioni ``int ()`` konverton një vlerë të tekstit në një vlerë të plotë. Kështu, me komandën ``n = int (s)`` vendosim një vlerë të plotë në ndryshoren *n*, kjo është arsyeja pse shenja + në program paraqet shtimin e numrave të plotë. Përmbledhja është shtuar në program si provë se *n* është me të vërtetë një vlerë e plotë (rezultati tregon se vlerat shtohen si numra).

Meqenëse funksioni *input* kthen një varg, ne gjithashtu mund të kalojmë rezultatin e tij direkt në funksionin *int*. Në këtë mënyrë shmangim përdorimin e variablës *s* dhe marrim një program pak më të shkurtër që bën të njëjtën gjë:

.. activecode:: console__text_input_int2

    n = int(input("Enter a whole number: "))
    print(n+n)

~~~~

Për një numër real, *int* thjesht duhet të zëvendësohet me *float*, sepse funksioni ``float ()`` shndërron një vlerë teksti në një numër real. Për shembull, nëse duam të ngarkojmë një numër të vërtetë dhe të shtypim dy herë atë numër, programi mund të duket si ky:

.. activecode:: console__text_input_float1

    s = input("Enter a real number: ")
    a = float(s)
    print(2*a)

or

.. activecode:: console__text_input_float2

    a = float(input("Enter a real number: "))
    print(2*a)


Kontrolloni se çfarë ndodh në këto dy shembuj kur futni diçka tjetër dhe jo një numër.

Në lidhje me konvertimet
--------------------------

Ne kemi parë që kur një varg përmban një numër të plotë ose një numër të vërtetë, ajo varg mund të shndërrohet në një numër të plotë ose të vërtetë duke përdorur funksionet *int ()* ose *float ()*. Nga ana tjetër, numrat e plotë dhe numrat realë gjithmonë mund të shndërrohen në një varg. Funksioni *str ()* përdoret për t'u kthyer në një varg.

.. activecode:: console__text_convert_to_str

    a = 1
    a_str = str(a)
    print(a_str + a_str)

    b = 2.1
    b_str = str(b)
    print(b_str + b_str)

Konvertimi i një vlere të plotë në një të vërtetë bëhet automatikisht kur është e nevojshme, megjithëse ne gjithashtu mund ta bëjmë këtë në mënyrë të qartë duke thirrur funksionin *float*.

.. activecode:: console__text_convert_int_to_float

    print(float(1))
    
Në të kundërt, kur duhet të kthejmë një numër real në një numër të plotë, ai konvertim nuk ndodh automatikisht (për një arsye) dhe duhet të vendoset në program duke thirrur funksionin *int ()*. Kur konvertoni një numër real në një numër të plotë, çdo decimale e numrit real hidhen, që do të thotë se rrumbullakimi është gjithmonë **drejt zeros**. Me fjalë të tjera, kur vlera e numrit real *x* nuk është i plotë, *int (x)* është më afër zeros sesa *x*.

.. activecode:: console__text_convert_int_float

    print(float(1))
    
    print(int(1.68))
    print(int(-1.68))
    
Pyetje
---------

.. mchoice:: console__text_quiz_1
    :answer_a: Programi printon 5
    :answer_b: Programi printon 23
    :answer_c: Do të ketë një gabim kur të përpiqeni të vendosni një numër dhe një string
    :correct: c
    :feedback_a: Provo përsëri.
    :feedback_b: Provo përsëri.
    :feedback_c: Saktë!
    
    Çfarë ndodh kur luajmç programin dhe shtypim ``2``?
    
    .. code::
    
        a = input()
        print(a+3)

.. mchoice:: console__text_quiz_2
    :answer_a: Programi printon 5
    :answer_b: Programi printon 23
    :answer_c: Do të ketë një gabim kur të përpiqeni të vendosni një numër dhe një string
    :correct: b
    :feedback_a: Provo përsëri
    :feedback_b: Saktë
    :feedback_c: Provo përsëri
    
    Çfare ndodh kur luajmë programin dhe shtypim ``2``?
    
    .. code::
    
        a = input()
        print(a+'3')

.. dragndrop:: console__text_quiz_4
    :feedback: Provo përsëri!
    :match_1: '2.11'|||str(2.1) + '1'
    :match_2: 3.1|||float('2.1') + 1
    :match_3: error in computation|||float('2.1') + '1'
    :match_4: 2.11|||float('2.1') + 1/100
    :match_5: '3.1'|||str(2.1 + int('1'))

     Lidh shprehjen me rezultatin.


.. mchoice:: console__text_quiz_5
   :answer_a: Kur vendi i parë dhjetor i a është më i madh se ose i barabartë me 5
   :answer_b: Kur numri a është negativ
   :answer_c: Kur numri a është pozitiv
   :answer_d: Kur numri a është 1-shifror
   :answer_e: Kur diferenca midis a dhe int (a) është më e madhe se 0.5
   :correct: b
   :feedback_a: Provo përsëri.
   :feedback_b: Saktë!
   :feedback_c: Provo përsëri.
   :feedback_d: Provo përsëri.
   :feedback_e: Provo përsëri.

   Kur është integer *int(a)* më i madh se numri rel a?

