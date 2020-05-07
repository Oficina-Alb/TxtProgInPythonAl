Programet me llogaritjen - Ushtrime
====================================

Deri më tani, ne kemi mësuar se si të ngarkojmë numrat në programe, si të kryejmë operacione llogaritëse mbi to dhe si të printojmë rezultatet. Tani mund t'i praktikojmë këto gjëra me disa detyra të thjeshta matematikore.

Detyrat pa ngarkuar të dhënat
------------------------------

Shembull
'''''''''

.. questionnote::

    **Shembull - Festa**

     Xhesika dhe Oscar po organizojnë një festë. Hapësira me qira strehon 100 persona, Xhesika deri më tani ka ftuar 43, dhe Oscar 28.

     Shkruani një program që llogarit dhe printon sa më shumë hapësirë është në dispozicion.

Problemi mund të zgjidhet si më poshtë:

.. activecode:: console__computing_party1
    
    print(100-43-28)

ose kështu:

.. activecode:: console__computing_party2

    total_places = 100
    called_by_jessica = 43
    called_by_oscar = 28
    places_left = total_places - called_by_jessica - called_by_oscar
    print(places_left)


.. infonote::

     Ndërsa kjo mund të duket e panevojshme këtu, zgjidhja me variabla vlen të praktikohet. Programet që përdorin ndrysvariablahore mund të bëjnë shumë më tepër sesa ato pa variabla. Për shembull, nëse ngarkojmë vlerat në një program, variablat janë të nevojshme. Gjithashtu, llogaritjet më komplekse do të ishin shumë të pakuptueshme nëse nuk mund të ndahen në hapa më të thjeshtë, dhe për vlerat e ndërmjetme përsëri kemi nevojë për variabla.
    
     Përmendëm më herët se duhet të përpiqemi t'u japim emrave domethënës variablave. Nuk ka rëndësi për kompjuterin (funksionon në mënyrë të barabartë me ndonjë emër), por kur llogaritim diçka që është e rëndësishme për ne, përdorimi i variablave me emra kuptimplotë do të na ndihmojë të kuptojmë atë program pas një kohe të gjatë. Gjithashtu, një program i tillë do të jetë më i lehtë për tu kuptuar nga njerëzit e tjerë që e lexojnë atë.
    

Ushtrime
''''''''''''''''''

.. questionnote::

    **Detyrë - blerje për të gjitha paratë**    
    
    Sa sende për 76 euro mund të blihen për 500 euro? Sa para do të mbesin nëse blihet numri më i madh i mundshëm i artikujve?

Versioni më i shkurtër (dhe më pak i qartë) i zgjidhjes është

    .. activecode:: console__computing_divmod_sol1
        :passivecode: true
        
        print(500 // 76, 500 % 76)

Shkruani një zgjidhje më të qartë duke përdoruar variabla.

.. activecode:: console__computing_divmod





.. questionnote::

    **Detyra - datum**
    
    Nëse sot është 15 i muajit dhe muaji është 31 ditë, sa ditë ka deri në 11 të muajit tjetër (në të njëjtën kohë)?

Detyra juaj është të shkruani një zgjidhje në të cilën vlerat fillestare dhe të llogaritura u janë caktuar variablave. Duke klikuar në butonin "zgjidhje e shkurtër" mund të shihni një zgjidhje të shkurtër si aluzion.

.. reveal:: console__computing_divmod_reveal
    :showtitle: Zgjidhje e shkurtër
    :hidetitle: Fshih zgjidhjen e shkurtër

    .. activecode:: console__computing_buying3_simple_sol1
        :passivecode: true
        
        print(11+31-15)

.. activecode:: console__computing_date



.. questionnote::

    **Detyra - blerja e 3 pjesëve**
    
    Ben ka 20 euro dhe dëshiron të blejë 3 llampa biçikletash për 1,58 euro secila. Sa para do të ketë lënë ai?
    
Shkruaj një program që përdor variabla për vlerat fillestare dhe të llogaritura.

.. activecode:: console__computing_buying3_simple


            
Shembuj më të dhëna në vazhdimësi
-----------------------------------

Shembuj
'''''''

.. questionnote::

    **Shembull - pikturë**
    
    Philip përgatitet të pikturojë tavanin në një dhomë. Për të ditur se sa bojë për të blerë, ai duhet të dijë dimensionet e dhomës dhe sa metra katrorë mbulon një kilogram bojë. Shkruani një program që ngarkon gjatësinë e dhomës, gjerësinë e dhomës, një zonë që mbulon një kilogram të bojës dhe shtypni numrin e kërkuar të kilogramëve të bojës.
    
Zgjidhja:

.. activecode:: console__computing_painting

    length = float(input("Fusni gjatësinë e dhomës: "))
    width = float(input("Fusni lartësinë e dhomës: "))
    area_per_kg = float(input("Fusn hapësirën e mbuluar nga 1 kg bojë: "))
    needed_kg = length * width / area_per_kg
    print(needed_kg, "kg bojë nevojitet.")


Ushtrime
''''''''''''''''''

.. questionnote::
    
    **Detyrë - zogj**
    
    Popullsia e lepujve në një ishull po dyfishohet çdo vit. Shkruaj një program që ngarkon numrin aktual të lepujve në ishull dhe numrin e viteve, dhe shtyp sa lepuj do të ishin në ishull në një numër të caktuar vitesh nëse vazhdojnë të riprodhojnë me të njëjtin ritëm.

.. activecode:: console__computing_rabbits



.. questionnote::

    **Detyrë - Blerja e një makine**

    Gjoni blen makinën me këste. Shkruaj një program që ngarkon në mënyrë sekuenciale çmimin e kontratës, shumën e një kësti dhe numrin e kësteve, dhe shtyp se sa më shumë John do të paguajë në total mbi çmimin e deklaruar në kontratë.
        
.. activecode:: console__computing_buying_car
