Funksione matematike - Ushtrime
=========================

Le të praktikojmë duke përdorur funksionet matematikore që kemi mësuar.

.. questionnote::
    
    **Detyrë - reklama: **
    
     Thomas shpërndan paketa reklamash që përmbajnë një kalendar, një keychain dhe një stilolaps. Shkruaj një program që ngarkon sa kalendarë, keychain dhe stilolapsa Thomas ka dhe më pas shtyp shumë pako reklame që ai mund të bëjë.

Për të përfunduar programin futni një nga funksionet matematikore që keni mësuar.

.. activecode:: console__mathfunc_promo_material

    num_calendars = int(input("How many calendars are there?"))
    num_keychains = int(input("How many keychains are there?"))
    num_pens = int(input("How many pens are there?"))
    num_packages = 0 # complete the statement
    print(num_packages, "packages can be made.")


.. questionnote::

    **Detyrë - limonada:**
    
     Një grup njerëzish u nisën për një udhëtim dhe Zoe bëri limonadë për të gjithë. Shkruaj një program që ngarkon sa litra limonadë Zoe ka bërë (si një numër i vërtetë), pastaj shkruaj se sa shishe gjysmë litri mund të mbushen me atë limonadë dhe sa shishe merr për të gjithë limonadën (dy numrat mund të ndryshojnë nga një në maksimum).
    
  
.. activecode:: console__mathfunc_lemonade

.. reveal:: console__mathfunc_lemonade_reveal
   :showtitle: Ndihmë
   :hidetitle: Fshih Ndihmën
   
   Për të përfunduar programin e mëposhtëm, përdorni disa nga funksionet e rrumbullakimit.
   
   .. activecode:: console__mathfunc_lemonade_solution
   
        liters = float(input())
        num_full_bottles = 0 # complete the statement
        total_bottles = 0 # complete the statement
        print(num_full_bottles, "bottles can be filled.")
        print("A total of", total_bottles, "bottles are required.") 

    
.. questionnote::

    **Detyrë - loja:**
    
     Gjashtë shokët ranë dakord të futeshin në sheshin e lojërave në një kohë të caktuar dhe të luanin një lojë. Shkruani një program që ngarkon kohën e vonesës së secilit lojtar në minuta (si numra të plotë) dhe shtyp me sa minuta vonesë ndeshja mund të kishte filluar.
    
.. activecode:: console__mathfunc_late_game

.. reveal:: console__mathfunc_late_game_reveal
   :showtitle: Ndhmë
   :hidetitle: Fshih Ndihmën
   
   Një zgjidhje e mundshme është shkruar pjesërisht më poshtë. Mundohuni ta plotësoni.
   
   .. activecode:: console__mathfunc_late_game_help

        t1 = int(input("How many minutes late was the first: "))
        # load the remaining data the same way
        game_delay = 0 # fix this statement
        print("The match could have started with a", game_delay, "minute delay.")

.. commented out

   .. activecode:: console__mathfunc_late_game_solution

        t1 = int(input("How many minutes late was the first: "))
        t2 = int(input("How many minutes late was the second: "))
        t3 = int(input("How many minutes late was the third: "))
        t4 = int(input("How many minutes late was the fourth: "))
        t5 = int(input("How many minutes late was the fifth: "))
        t6 = int(input("How many minutes late was the sixth: "))
        game_delay = 0 # complete this statement
        print("The match could have started with a", game_delay, "minute delay.")



.. questionnote::

   **Detyrë - dy autobusë:**
    
     Maya dhe Lola udhëtojnë në të njëjtën autostradë në dy autobusë të ndryshëm dhe flasin në telefon. Njëri prej tyre sapo ka vërejtur piketimin *x* dhe tjetrin *y*. Shkruaj një program që ngarkon me numër të plotë: *x* dhe *y* dhe shtyp se sa milje Maya dhe Lola janë larg nga njëra-tjetra.
    
.. activecode:: console__mathfunc_buses

.. commented out
    
    .. reveal:: console__mathfunc_buses_reveal
       :showtitle: Help
       :hidetitle: Hide help
       
       To complete the following program, use one of the math functions you have learned.
       
       .. activecode:: console__mathfunc_buses_solution

            x = int(input("Enter x: "))
            y = int(input("Enter y: "))
            distance = 0 # complete thes statement
            print("Distance is", distance)



.. questionnote::

    **Detyrë - Mësime në video**

     Kursi përbëhet nga disa mësime video që të gjitha zgjasin në mënyrë të barabartë. Ju keni vendosur t'i kushtoni 90 minuta këtij kursi çdo ditë dhe dëshironi të dini se sa ditë do të zgjasë për të gjithë kursin. Shkruaj një program që ngarkon numrin e mësimeve dhe kohëzgjatjen e një mësimi në minuta, dhe shtyp numrin e kërkuar të ditëve, të rrumbullakosura në numrin e plotë më të afërt ..
    
.. activecode:: console__mathfunc_videolessons
