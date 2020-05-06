Libraria PyGame
==================

Supozojmë që ju tashmë jeni njohur me Python si gjuhë, dhe se dini për shprehjet (konstantet, ndryshoret, operatorët), deklarimet (``if``, `` if-other``, ``if-elif-other``, ``for``), funksione (ato të ndërtuara, si `` min`` ose ``abs``, dhe ato që i përcaktoni vetes duke përdorur fjalën ``def``), vargjet (``"Përshëndetje"`` ose ``Hello``, listat (si ``[[1, 2, 3]``), tuple "si ``(3, 4)``) dhe të ngjashme.

Tani do të vazhdojmë të praktikojmë shkrimin e programeve Python duke përdorur bibliotekën grafike PyGame. Ne e zgjodhëm këtë librari sepse ofron mundësinë për të prodhuar rezultate interesante me programim relativisht pak, të cilat përfshijnë vizatim, animacion dhe bashkëveprim me një përdorues. Prandaj, qëllimi i prezantimit të librarisë PyGame është që ju të vazhdoni të praktikoni aftësitë tuaja programuese në një mënyrë argëtuese. Lexuesit që bëhen më të interesuar në programim do të marrin shumë mundësi për të modifikuar programe të dhëna dhe frymëzim për një sërë projektesh të tyre.

Rreth librarisë PyGame
------------------------

Libraria `PyGame <http://pygame.org>` __ ka filluar të zhvillohet që nga fillimi i viteve 2000. Vetë autorët thanë që kjo nuk është libraria më e mirë për programimin e lojërave (madje as e dyta, as e treta për nga cilësia), por përparësia e saj kryesore është se është më e thjeshtë për t’u përdorur sesa bibliotekat e tjera dhe është e përshtatshme për të mësuar programim përmes bota interesante e grafikës kompjuterike dhe lojërave kompjuterike.


Përdorimi në internet
----------------------

Për t'ju ndihmuar të filloni, ne ju kemi siguruar një mjedis ku mund të shkruani dhe testoni programe të thjeshta PyGame në fletoren e punës që po lexoni. Ne gjithashtu kemi përgatitur një pjesë të shembujve dhe detyrave në të cilat, si në kapitujt e mëparshëm, ju zakonisht duhet të plotësoni ose modifikoni programet e filluara në mënyrë që t'i bëni ato të punojnë plotësisht. Ju nuk keni nevojë të instaloni asgjë shtesë në kompjuterin tuaj për të përdorur këtë mjedis. Sidoqoftë, nëse doni të bëni një programim më serioz (për shembull, dëshironi të bëni lojën tuaj), ju rekomandojmë që ta instaloni bibliotekën në kompjuterin tuaj dhe ta përdorni atë nga një mjedis zhvillimi Python (siç është IDLE), i pavarur nga shfletuesin në internet dhe këtë libër pune. Ndër avantazhet e tjera, programimi në një mjedis aktual zhvillimi është më i rehatshëm dhe më efikas, më i lehtë për tu provuar, për të përdorur debugger etj.

Instalimi
------------

Për të ekzekutuar programet e shkruara duke përdorur PyGame në mjedisin tuaj të zhvillimit të aplikacionit, së pari duhet të instaloni këtë bibliotekë. Një parakusht, natyrisht, është që ju keni të instaluar Python në kompjuterin tuaj (preferohet versioni 3.6 ose më vonë). Nëse nuk e keni bërë këtë tashmë, vizitoni faqen `<https://www.python.org>` __ dhe shkarkoni versionin e fundit të Python dhe mjedisin e tij të punës (zakonisht i gjeni në seksionin Shkarkime, nën-pjesa kushtuar sistemit operativ ju jeni duke përdorur)

Kur Python është instaluar në kompjuterin tuaj, ne mund të shkojmë në instalimin e bibliotekës PyGame. Reallyshtë vërtet shumë e thjeshtë. Thjesht shkruani ``pip3 install pygame`` në commnad prompt. Mënyra më e lehtë për të filluar komandën e shpejtë është mbajtja e tastit ``windows`` dhe shtypja e butonit ``r``, dhe shtypja ``cmd`` në dritaren që shfaqet. Nëse merrni mesazhin se komanda ``pip3`` nuk ekziston, atëherë provoni ``py -3 -m pip install pygame``.

Kur të përfundoni instalimin, është mirë që menjëherë të provoni që gjithçka shkoi mirë:

* drejtimin e mjedisit për zhvillim IDLE Python, i cili është instaluar si një aplikacion Windows

* hapja e një projekti të ri në mjedisin e zhvillimit të IDLE (opsioni File / New)

* shtypni programin e treguar më poshtë në redaktues (thjesht mund ta kopjoni dhe ngjitur në redaktorin IDLE)

* ruajtjen e programit në një skedar përpara se ta ekzekutoni atë (opsioni File / Save as ...)

* drejtimin e programit (opsioni Run / Run Module në menu, ose tasti F5)


Pas drejtimit të programit, duhet të shfaqet një dritare në të cilën një shesh vizatohet dhe shfaqet për tre sekonda.

.. activecode:: PyGame__check_install
   :nocodelens:
   :modaloutput: 
   :enablecopy:

   import pygame
   pygame.init()
   prozor = pygame.display.set_mode((200, 200))
   prozor.fill(pygame.Color("white"))
   pygame.draw.rect(prozor, pygame.Color("black"), (20, 20, 160, 160), 5)
   pygame.display.update()
   pygame.time.wait(3000)
   pygame.quit()

Ju gjithashtu mund të ekzekutoni shembuj të tjerë nga ky udhëzues në kompjuterin tuaj, të cilat ne ju rekomandojmë të bëni ndonjëherë.

