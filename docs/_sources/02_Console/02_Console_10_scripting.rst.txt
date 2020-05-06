Skripte dhe cikli *for*
========================

Skriptet
----------

Njerëzit shpesh shkruajnë programe të shkurtra në Python dhe i përdorin ato vetë për të llogaritur ose automatizuar diçka. Programet e tilla njihen gjithashtu si **skriptet**. Nuk është e pazakontë që skriptet të kenë disa ose të gjitha të dhënat hyrëse të përfshira në vetë skenarin, në vend që të ngarkohen. Për shembull, skripti i mëposhtëm llogarit një zbritje prej 20 përqind:

.. activecode:: console__scripting_fixed

    discount = 20
    regular_price = 250
    discounted_price = regular_price * (1 - discount / 100)
    print(regular_price, discounted_price)

Udhëzimet për përdorimin e këtij skenari mund të jenë: "Në dy rreshtat e parë të skenarit, vendosni vlerat që dëshironi dhe më pas drejtoni skenarin."

Ju nuk do të shihni një udhëzim të ngjashëm për programet që instaloni në kompjuterin tuaj ose në celular. Ne i quajmë programe të tilla **aplikacione**, dhe ato janë shkruar në mënyrë që përdoruesit të mos kenë nevojë të dinë (dhe më shpesh ata nuk mund të dinë) si duken statistikat e këtij programi.

Me skriptet, nuk ka një ndarje të rreptë midis përdoruesve dhe zhvilluesve si me aplikacionet. Shkrimet shpesh shkruhen për përdorim personal ose për një përdorues që përdor ose kupton programimin. Të gjitha programet në këtë udhëzues janë në të vërtetë më shumë skenare sesa aplikacione.

Tashmë kemi theksuar që ky manual nuk është i destinuar vetëm për profesionistët e ardhshëm në programim. Nëse nuk programoni aplikime, prapë mund të përfitoni nga programimi. Ju mund të shkruani një skenar ose të rregulloni një ekzistues, siç pritet në udhëzimin e supozuar të shembullit të mëparshëm.

Përsëritja e llogaritjes për të dhëna të shumta
---------------------------------------

Le ta bëjmë shembullin e mëparshëm më të përgjithshëm. Supozoni se në një dyqan ne kemi të drejtë për një zbritje 20 përqind mbi çmimet e rregullta. Ne jemi të interesuar në çmimet me zbritje të produkteve të ndryshme, çmimet e rregullta të të cilave i njohim.

**Rinisja e programit që ngarkon të dhënat**

Zgjidhja që ne tashmë dimë se si të shkruajmë është të ngarkojmë çmimin e rregullt të produktit dhe pastaj të llogarisim dhe shtypim çmimin e ulur. Ky program mund të duket si ky:

.. activecode:: console__scripting_input

    discount = 20
    regular_price = int(input())
    discounted_price = regular_price * (1 - discount / 100)
    print(regular_price, discounted_price)

Ne mund ta drejtojmë programin disa herë, duke vendosur çdo herë një çmim të rregullt për një nga produktet për të cilat jemi të interesuar.

**Të dhëna të shumta në vetë programin**

Në rastin kur ne i dimë paraprakisht të gjitha çmimet e rregullta të produkteve që na interesojnë, lëshimi i shumëfishtë i programit dhe futja e një çmimi në një kohë nuk është mënyra më e rehatshme për të marrë të gjitha çmimet me zbritje. Përkundrazi, do të ishte më e përshtatshme që të vendosni të gjitha çmimet e rregullta direkt në program dhe të përsërisni llogaritjen dhe shtypjen e rezultateve për secilën nga këto të dhëna.

deklarimi *for*
----------------

Për të qenë në gjendje të përsërisim një pjesë të programit për secilën pjesë të të dhënave të shumta, na duhet deklarimin **for**, e cila lejon që deklarimin e tjera të përsëriten. Tani ne do të shohim një mënyrë për të përdorur deklarimin *for*, dhe ne do të shohim disa forma të tjera të deklarimit *for* në mësimet e mëposhtme.

Le të kthehemi në shembullin e çmimit të zbritur. Le të themi se çmimet e rregullta të produkteve për të cilat na interesojnë janë 250, 120 dhe 310 dhe dëshirojmë të llogaritim çmimet e zbritura për ato produkte me një ekzekutim të vetëm. Ja se si mund ta bëjmë:

.. activecode:: console__scripting_for

    discount = 20
    for regular_price in (250, 120, 310):
        discounted_price = regular_price * (1 - discount / 100)
        print(regular_price, discounted_price)

Shënim: notimi (250, 120, 310) është i quajtur **tuple**.

Drejtimin e programit shohim që ai shtyp:

.. code::

    250 200.0
    120 96.0
    310 248.0

Vëmë re se dy rreshtat e fundit të programit u ekzekutuan tre herë, me ndryshoren *të rregullt_price* duke marrë vlerat 250, 120, 310 në atë rend. Këtë e arritëm me deklarimin ``for``. Pjesët e programit që përsëriten quhen sythe, kështu që mund të themi se në shembullin e mëparshëm kemi përdorur një **for loop**.

Figura e mëposhtme tregon elementet kryesore të for loop:


.. image:: ../../_images/Console/console_loop_tuple.png
  :width: 400px
  :align: center

- Elementet e kërkuar shkruhen me të kuqe (fjalët ``for``, ``in`` dhe karakteri ``:`` në rreshtin e parë). Këto elemente shkruhen në të njëjtën mënyrë në secilën deklaratë *for*.
- Variabli **loop** është shkruar me ngjyrë blu. Në atë vend ne shkruajmë emrin e ndryshores që do të marrë vlerat e specifikuara në tuple. Në shembullin tonë, ndryshorja e lakut është *regular_price*.
- Një tufë vlerash shkruhet me gjelbër. Në atë vend ne shkruajmë vlera të ndara me presje në kllapa. Këto janë vlerat që do të marrin nga ana e variablit loop. Në shembullin tonë, tufa është (250, 120, 310).
- **Trupi i loop** është shkruar me të zeza. Këto janë komanda që ekzekutohen një herë për secilën vlerë të ndryshores loop. Variablat e lakut mund ose nuk mund të përdoren në deklaratat e trupit të loop.

Deklaratat e trupit loop shkruhen në mënyrë të theksuar në lidhje me rreshtin e parë të deklaratës *for*. Është e zakonshme të përdorim 4 hapësira të pikave dhe do t'i përmbahemi këtij rekomandimi.


Shembuj dhe ushtrime
''''''''''''''''''

.. questionnote::
    
    **Shembull - kur do të niset**
    
     Ronnie duhet të arrijë në destinacion jo më vonë se ora 5:00. Në varësi të mënyrës së udhëtimit që ai zgjedh, Ronnie mund të ketë nevojë për 55, 70, 85 ose 95 minuta. Shkruani një program që shtyp për secilën mënyrë të udhëtimit kur Ronnie duhet të largohet më së voni për të arritur në kohë.
    
    
Një program që zgjidh këtë detyrë mund të duket si ky:

.. activecode:: console__scripting_start_travel
    
    arrival = 17*60
    for travel_duration in (55, 70, 85, 95):
        leaving = arrival - travel_duration
        leaving_hours = leaving // 60
        leaving_minutes = leaving % 60
        print("If the travel lasts", travel_duration, "minutes, Ronnie should leave at", leaving_hours, "hours and", leaving_minutes, "minutes.")




.. questionnote::

    **Detyrë - kohëzgjatja e udhëtimit **

     George synon të fillojë një udhëtim me makinë 600 kilometra në 9 të mëngjesit në mëngjes dhe është i interesuar të arrijë kohën nëse ai po udhëtonte me një shpejtësi mesatare prej 90, 100, 120 ose 130 kilometra në orë. Përfundoni programin për të renditur kohën e mbërritjes në destinacion për secilën nga shpejtësitë mesatare të lartpërmendura.
    
.. activecode:: console__scripting_speed

    path_length = 600 # Km
    leaving = 9       # h
    for a in ():  # fix
        trip_duration = path_length / speed # h
        arrival = leaving + trip_duration    # h
        arrival_hours = int(arrival)
        arrival_minutes = round((arrival - arrival_hours) * 60)
        print("At", speed, "km / h the arrival time is at", arrival_hours, "hours and", arrival_minutes, "minutes.")
        
.. commented out

    path_length = 600
    leaving = 9
    for speed in (90, 100, 120, 130):
        trip_duration = path_length / speed
        arrival = leaving + trip_duration
        arrival_hours = int(arrival)
        arrival_minutes = round((arrival - arrival_hours) * 60)
        print("At", speed, "km / h the arrival time is at", arrival_hours, "hours and", arrival_minutes, "minutes.")




.. questionnote::

    **Detyrë - shkalla e fundit**

     Shuma e 5 notave të Katie deri më tani është 23. Katie pret një notë tjetër nga detyra e kontrollit përfundimtar. Përfundoni programin më poshtë në mënyrë që për secilën klasë të mundshme përfundimtare (1, 2, 3, 4, ose 5) të shtyp atë që do të ishte nota mesatare në atë rast.
    
.. activecode:: console__scripting_final_mark

    sum_grades_so_far = 23
    num_grades_so_far = 5
    for # complete the statement
        average_grade = 0 # fix
        print("With the final grade", final_grade, "average grade would be", average_grade)



.. questionnote::

    **Detyrë - shtesa **

     Theo bën një plan për të shpenzuar paratë e xhepit për një pushim 14-ditor. Shkruaj një program që, për një shpenzim mesatar ditor prej 5, 10, ose 20 euro, rendit sa para do të duheshin në total në Theo për secilin rast.


.. activecode:: console__scripting_allowance

    num_days = 14
    # finish the program

