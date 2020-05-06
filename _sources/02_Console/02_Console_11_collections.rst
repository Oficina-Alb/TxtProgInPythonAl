Koleksionet
================

Në mësimin e mëparshëm, ne kemi përdorur një tuple për të kryer disa komanda (llogaritjen dhe shtypjen) mbi secilën vlerë nga tuple duke përdorur loop *for*.

Tuples janë gjithashtu një lloj i të dhënave në Python, të tilla si numrat, vargjet ose vlerat logjike. Llojet *int* (numër i plotë), *float* (numri real), *str* (vargu) dhe *bool* (vlera logjike) janë **llojet themelore**. Dallimi midis tuples dhe llojeve themelore është se vlera e një tuple përbëhet nga vlera të shumta të një lloji më të thjeshtë.

Secila vlerë që përbëhet nga vlera të shumta të një lloji më të thjeshtë do të quhet një **koleksion**. Të dhënat që koleksioni përbëhet quhen **elementë të mbledhjes**.

Koleksionet e vetme që kemi parë deri më tani janë tuples, të cilat tani do t'i njohim më në detaje. Do të shohim edhe disa lloje të tjera koleksionesh shumë shpejt.


Tuple dhe elementet e saj
----------------------------

Paketimi dhe paketimi i paketave
''''''''''''''''''''''''''''''''''''

Ne mund ta vendosim tërë tufën në një ndryshore, ashtu siç veprojmë me vlerat e një lloji më të thjeshtë. Në shembullin e mëposhtëm, variabli *temperatura* përmban tërë vlerësimin si vlerë të saj.

.. activecode:: console__collections_tuple1
    
    temperatures = (25, 24, 25, 23, 25, 25)
    for t in temperatures:
        print(t)
        
Ky lloj i caktimit të vlerës (si në rreshtin e parë të programit) njihet si paketim tuple. Caktimi i kundërt është gjithashtu i mundur: kur e dimë se sa elementë ka në një tufë, ne mund t'i caktojmë elementët tuple në numrin përkatës të ndryshoreve:

.. activecode:: console__collections_tuple2
    
    full_name = ("Arthur", "Conan", "Doyle")  
    first_name, middle_name, last_name = full_name
    print(first_name)
    print(middle_name)
    print(last_name)
    
Deklaratat si ``first_name, middle_name, last_name = emri i plotë`` quhen paketim tuple.


I njëjti efekt arrihet nga një deklaratë e lidhur

.. code::
    
    first_name, middle_name, last_name = "Arthur", "Conan", "Doyle"
    
Tuples do not appear in this statement, which is called multiple value assignment.

Tuples nuk paraqiten në këtë deklaratë, e cila quhet detyrë me shumë vlera.

Elementet dhe indekset
''''''''''''''''''''''''''

Ne gjithashtu mund të marrim elementet e një tuple duke shkruar emrin e tuples, dhe pas saj në kllapa katror numrin rendor të elementit që duam. Këtu duhet të theksohet se numërimi i elementeve të çdo koleksioni fillon nga zero. Për shembull:

.. activecode:: console__collections_index

    basic_colors = ("Red", "Green", "Blue")
    print(basic_colors[0])
    print(basic_colors[1])
    print(basic_colors[2])

The sequence number of an element is also called the **index** of the element. if the tuple has *n* elements, we can use the numbers 0, 1, 2, ... *n-1* as indices. In the example above, *n* = 3, so indices 0, 1, and 2 are allowed. Trying to use an index outside these bounds causes an error (try it).

Gjatesia e Tuple
''''''''''''''''''

Numri i elementeve të një tuple mund të merret duke përdorur funksionin *len*.

.. activecode:: console__collections_len1
    
    basic_colors = ("Red", "Green", "Blue")
    n = len(basic_colors)
    print(n)
    
ose më shkurt:

.. activecode:: console__collections_len2
    
    print(len(("Red", "Green", "Blue")))
    
Vini re kllapat e dyfishta (njëra për funksionin dhe tjetra për tufën).

Përmes këtyre shembujve kemi parë që elementët tuple mund të jenë numra ose vargje. Në fakt, elementët tuple mund të jenë të çdo lloji, themelor ose kompleks.

Për shembull, është e mundur të krijoni një tufë prej tuples:

.. activecode:: console__collections_len3
    
    t = ((11, 12, 13), (21, 22, 23))
    print(len(t))


.. commented out

    t2 = ((1, 2, 3), ) # last comma matters
    print(len(t2))
    
Tuple *t* përmban dy tupla më të thjeshta, prandaj numri i elementëve të tij është 2.

Në Python, elementët e një tuple mund të jenë të llojeve të ndryshme, dhe shembuj të tillë do t'i shohim më vonë.


Vargu
-----

Gama është një lloj tjetër i koleksionit. Për dallim nga tuple, elementët e kësaj koleksioni janë gjithmonë numër të plotë.

Gama mund të përcaktohet në disa mënyra.

Varg me 1 argument
'''''''''''''''''''''''

Forma më e thjeshtë për të specifikuar një gamë është *varg (n)*, ku *n* është një numër i plotë pozitiv. Varg *(n)* Varg * përmban numër të plotë nga 0 në *n*, duke mos përfshirë *n*. Për shembull, *diapazoni (5)* përmban vlerat 0, 1, 2, 3, 4.

.. activecode:: console__collections_range_n_i
    
    for i in range(5):
        print(i)
        
Ne shohim që në deklarimin *for*, ne mund të përdorim gamën në të njëjtën mënyrë si tuple. Në fakt, çdo koleksion mund të jetë në vend të tufës ose diapazonit.

Meqenëse diapazoni *varg (n)* përmban gjithsej vlera *n*, ky diapazon përdoret shpesh kur vetëm një komandë duhet të përsëritet *n* herë në të njëjtën mënyrë:

.. activecode:: console__collections_range_n
    
    for i in range(5):
        print("Hello!")

Funksioni *print* u ekzekutua për secilën vlerë *i* të sekuencës 0, 1, 2, 3, 4, por në këtë shembull, ato vlera nuk përdoren në trupin e lakut. Kështu, kemi arritur që funksioni *print* të ishte ekzekutuar 5 herë në të njëjtën mënyrë, d.m.th., është përsëritur 5 herë.

Një tjetër përdorim i zakonshëm i këtij lloji të gamës është të kapni të gjithë elementët e një tuple. Në këtë rast, variabli i loop shërben si një indeks. Kjo mënyrë për të kaluar vlerat e tuple është e përshtatshme kur përveç këtyre vlerave tuple në lak na duhen edhe numrat e sekuencave të tyre (kjo mënyrë për të kaluar nëpër koleksion është më e zakonshme në gjuhët e tjera të programimit sesa Python).


.. activecode:: console__collections_for_range_len
    
    colors = ["Red", "Green", "Blue", "Yellow", "Magenta"]
    n = len(colors)
    for i in range(n):
        print('Color #', i, 'is', colors[i])
    

Varg me 2 argumente
''''''''''''''''''''''''

Kur kemi nevojë për një sekuencë të numrave të plotë të njëpasnjëshëm që nuk fillojnë në zero, ne e vendosim rangun si *string (a, b)*, ku *a* dhe *b* janë numra të plotë të tillë që :math:`a <b`. Atëherë sekuenca përbëhet nga numra të plotë nga *a* në *b*, duke mos përfshirë *b*. Për shembull, vargu *(1, 6)* jep rendin e numrave 1, 2, 3, 4, 5:

.. activecode:: console__collections_range_a_b
    
    for i in range(1, 6):
        print(i)

Varg me tre argumente
''''''''''''''''''''''''''

Forma e tretë e specifikimit të një game ka tre argumente:

.. activecode:: console__collections_range_a_b_c
    
    for i in range(2, 12, 2):
        print(i)

Vlerat e diapazonit të dhënë nga *diapazoni (a, b, c)* shkojnë nga *a* në *b* (duke mos përfshirë *b*) me hapin *c*, vlerat d.m.th ndryshojnë me *c*. Hapi *c* gjithashtu mund të jetë negativ:

.. activecode:: console__collections_range_a_b_cneg
    
    for i in range(12, 2, -2):
        print(i)


Ne mund ta shndërrojmë një varg në një tufë (e kundërta nuk është e mundur, as nuk është e nevojshme ndonjëherë):

.. activecode:: console__collections_range_to_tuple
    
    a = tuple(range(2, 12, 2))
    print(len(a))

Vargu si koleksion
----------------------

Ne kemi përdorur vargje si lloji themelor deri më tani, por vargjet mund të përdoren gjithashtu si koleksione të karaktereve individuale. Ne mund të përshkojmë karakteret e vargjeve duke përdorur një lak dhe të marrim karaktere individuale duke përdorur indekset:


.. activecode:: console__collections_str_as_collection
    
    s = 'text'
    print(s[1], s[2])
    for c in s:
        print(c)

Funksionet në koleksione
-------------------------

Ka shumë funksione në Python që pranojnë një koleksion si një argument. Një prej tyre është funksioni *len*, të cilin ne kemi përmbushur tashmë. Disa funksione të tjera që përdoren zakonisht për koleksionet janë:

- *min*, një funksion që jep elementin më të vogël të një koleksioni
- *max*, një funksion që jep elementin më të madh të një koleksioni
- *sum*, një funksion që jep shumën e elementeve të një koleksioni

.. activecode:: console__collections_aggregation
    
    print('Tuple:')
    t = (2, 8, 4, 15, 3)
    print('len(t) =', len(t))
    print('min(t) =', min(t))
    print('max(t) =', max(t))
    print('sum(t) =', sum(t))

    print('Range:')
    r = range(1, 10, 2)
    print('len(r) =', len(r))
    print('min(r) =', min(r))
    print('max(r) =', max(r))
    print('sum(r) =', sum(r))

    print('String:')
    s = 'Python'
    print('len(s) =', len(s))
    print('min(s) =', min(s))
    print('max(s) =', max(s))
    # elements of s are not numbers, so uncommenting the next statement would cause an error
    # print('sum(s) =', sum(s)) 

Vlerat e funksioneve *len*, *sum*, *min*, *max* për diapazonin gjithashtu mund të përcaktohen nga parametrat e diapazonit. Gjithashtu, *min* dhe *max* nuk zbatohen zakonisht në një varg (ata kthehen karakter me përkatësisht kodin më të vogël dhe më të madh). Këtu, ne thjesht po theksojmë se të gjitha këto funksione pranojnë lloje të ndryshme koleksionesh si argumentin e tyre (përfshirë gamën dhe vargun).

Pyetj
'''''''''

.. mchoice:: console__collections_quiz_tuple_unpack
   :answer_a: a program error occurs
   :answer_b: 2
   :answer_c: 20
   :answer_d: 3
   :feedback_a: Provo përsëri
   :correct: c
   :feedback_b: Provo përsëri
   :feedback_c: Saktë
   :feedback_d: Provo përsëri

   Çfare printon programi i mëposhtëm?
   
   .. code::
   
       t = (32, 41, 20, 17)
       a, b, c, d = t
       print(c)

.. mchoice:: console__collections_quiz_tuple_index
   :answer_a: 1
   :answer_b: 2
   :answer_c: a program error occurs
   :answer_d: 3
   :correct: b
   :feedback_a: Provo përsëri
   :feedback_b: Saktë
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri

   Çfare printon programi i mëposhtëm?
   
   .. code::
   
       a = (1, 2, 3)
       print(a[1])


.. mchoice:: console__collections_quiz_range1
   :answer_a: range(4)
   :answer_b: range(1, 4)
   :answer_c: range(3)
   :answer_d: range(1, 3)
   :correct: b
   :feedback_a: Provo përsëri
   :feedback_b: Saktë
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri

   Cili varg përmban vlerat 1, 2, 3?

.. mchoice:: console__collections_quiz_range2
   :answer_a: 5
   :answer_b: 6
   :answer_c: 9
   :answer_d: 10
   :correct: a
   :feedback_a: Saktë
   :feedback_b: Provo përsëri
   :feedback_c: Provo përsëri
   :feedback_d: Provo përsëri

   Sa vlera përmban vargu(1, 10, 2)?

.. dragndrop:: console__collections_quiz_range_len
    :feedback: Provo përsëri!
    :match_1: 5|||range(5)
    :match_2: 0|||range(3, 3)
    :match_3: 3|||range(1, 4)
    :match_4: 1|||range(3, 6, 3)

    Lidh vargun me numrin e elementëve.


.. dragndrop:: console__collections_quiz_range_values
    :feedback: Provo përsëri!
    :match_1: 3, 4, 5|||range(3, 6)
    :match_2: 0, 1, 2|||range(3)
    :match_3: 3, 1|||range(3, -1, -2)
    :match_4: 3, 2, 1, 0, -1|||range(3, -2, -1)
    :match_5: 3|||range(3, 6, 3)

    Lidh vargun me vlerat.
