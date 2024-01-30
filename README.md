freecodecamp tutorial -   https://www.youtube.com/watch?v=RGOj5yH7evk&t
David Šetek tutorail -    https://www.youtube.com/watch?v=_qSB6jN4A3s&list=PLQ8x_VWW6AkuVs1oyWth3lXA4D4jxD_7F
David Šetek poznámky -    https://docs.google.com/document/d/1iA0e_FcqB6Dwj3fULfedrd_PJavByYYXoIDY_yOupFs/edit

čím lepšie si spíšeš ťahák, tým je menšia šanca, že ho použiješ
pozrieť nejaké grafické prostredie na Git

Git
  - beží na našej lokálnej mašine (LM)
  - nemusíme mať internet
  - zaznamenáva zmeny kódu lokálne
    
GitHub
  - cloud, na kotrý umiestňujeme repozitáre, ktoré obsahujú postupne vyvýjanie nášho projektu
  - použijeme ho v tedy keď chceme mať zálohované súbory / pracujeme v tíme a potrebujeme medzi sebou zdielať kód
  - môžme to považovať ako sociálnu sieť

HEAD
  - posledný commit v aktuálnej brenchi
  - majme:
    
              sme na Master Branchi.  HEAD->master
              ┌─────────────────────────┐
              |      commit MB #n       |  <-- HEAD
              |      commit MB #...     |
              |      commit MB #3       |
              |      commit MB #2       |
              |      commit MB #1       |
              └─────────────────────────┘

              vytvorenie Feature Branch s názvom bug
              sme na Master Branchi  HEAD->(master, bug)
              ┌─────────────────────────┐
              |     created FB #1       | <-- HEAD
              |      commit MB #n       | <-- HEAD
              |      commit MB #...     |
              |      commit MB #3       |
              |      commit MB #2       |
              |      commit MB #1       |
              └─────────────────────────┘

              prepneme sa na branch bug
              sme na Feature Branchi  HEAD->(bug, master)
              ┌─────────────────────────┐
              |     created FB #1       | <-- HEAD
              |      commit MB #n       | <-- HEAD
              |      commit MB #...     |
              |      commit MB #3       |
              |      commit MB #2       |
              |      commit MB #1       |
              └─────────────────────────┘

              commitneme fixnutie bugu na FB
              sme na Feature Branchi  HEAD->(bug)
              ┌─────────────────────────┐
              |      commit FB #1       | <-- HEAD
              |      commit MB #n       |
              |      commit MB #...     |
              |      commit MB #3       |
              |      commit MB #2       |
              |      commit MB #1       |
              └─────────────────────────┘

              prepneme sa späť na Master Branch
              sme na Master Branchi  HEAD->(master)
              ┌─────────────────────────┐
              |      commit FB #1       |
              |      commit MB #n       | <-- HEAD
              |      commit MB #...     |
              |      commit MB #3       |
              |      commit MB #2       |
              |      commit MB #1       |
              └─────────────────────────┘

Vetvenie a commitovanie
  - vždy keď vytvoríme zmenu vo vetve X a chceme aby tam tá zmena aj ostala, musíme ju commitnuť.
      môže sa stať, že vo vetve X vytvoríme zmenu (napr. pridáme súbor a.txt) a prepneme sa do
      vetve Y, v ktorej pošleme všetky súbory do staging area (použijeme  git add) a následne ich
      commitneme. Stane sa to, že a.txt bude patriť do vetve Y aj napriek tomu, že súbor sme vytvorili
      vo vetve X

  
┏ ┐
└ ┛

              ┌──────────────────────┐
      ┏------ | folder kde pracujeme |
      |       └──────────────────────┘
      |  git add 
      |       ┌──────────────────────┐
      └-----> |     staging area     | ------┐
              └──────────────────────┘       |
                                  git commit |
              ┌──────────────────────┐       |
              |  repozitár (sklad)   | <-----┛
              └──────────────────────┘         



Git príkazy

git clone git@github.com:sknefi/$name.git
                    - z ssh linku si naklonujeme repo na LM

ls -la              - zobrazí všetky súbory v danom súbere, -la zobrazí aj hidden súbory

rm -rf              - vynútené zmazanie (používa sa na mazanie folderov)

rm -rf .git         - vymaže git z repa v LM

git init            - inicializácia .git do daného repozitára

.gitignore          - v repe, ktorý sme inicializovali ako .git môžeme vytvoriť súbor .gitinit (bez prípony),
                        ktorý nám hovorí, ktoré súbory sa majú ignorovať pri commite
                    - keď vytvoríme .gitignore musíme ho commitnuť  git commit -m "Vytvorenie .gitignore"
                    - do .gitignore môžeme písať súbory a zložky, ktoré chceme aby boli ignorované, napr.
                          1. secrets.txt
                          2. myFolder/
                    

git status          - zobrazí čo všetky som zmenili v rámci repozitára
                    - keď sa dačo zmení dostaneme v termináli správu "modified"
                    - keď pridáme file v termináli sa vypíše "untracked" to znamená, že .git nepozná
                        a nepozná tento file (je netrekovaný). Pridáme ho pomocou git add

git add .           - bodka znamená pridaj všetko
                    
git add $filename   - pridanie súboru, ktorý sa nachádza v danom repo (/gitNotes/index.html)
 
git commit -m ""    - vždy keď commitujeme repo musíme zadať -m "" čo predstavuje správu
                    - vždy keď commitneme tak sa commitne celý repo
                    - správou môže byť napr. -m "pridaný index.html"
  

git commit -m "" -m ""      - prvé -m "" predstavuje správu
                            - druhé -m "" predstavuje description

git commit          - otvorí defaultne nastavený textový editor (na MacOS VIM)
                    - správu môžeme napísať vo vime, v prípade, že sa nám ju nechce písať
                        v do jedného riadku keď používame " git commit -m "" "
                    - podstatná vec, ako sa orientovať vo VIMe 

              VIM
              ┌────────────────────────────────────────────────────────┐
              | h j k l     move LEFT DOWN UP RIGHT                    |
              | w b         move on beggining of RIGHT LEFT _word_     |
              | gg G        move on START END of a _file_              | 
              | 0 $         move on START END of a _current line_      |
              | i a         goto insert BEFORE AFTER _cursor_          |
              | o O         goto instert _one line_ UNDER ABOVE        |
              | x X         delete one character AFTER BEFORE _cursor_ |
              | dd          delete _current line_                      |
              | yy p        COPY PASTE _current line_                  |
              | v V         goto visual SELECT CHARACTERS SELECT LINES |
              | / ?         SEARCH FORWARD BACKWARD                    |
              | n N         show NEXT PREVIOUS _result_ from search    |
              └────────────────────────────────────────────────────────┘ 
                      
git commit --amend  - pridanie nových zmien (nového - tohto commitu) ku poslednému commitu
                    - pridá zmeny ale vždy iba k POSLEDNÉMU commitu
                    - predstavme si to na príklade: 
                          1. vytvoríme dva súbory (a.txt, b.txt) 
                          2. súbor a.txt pošleme do staging area pomocou git add a.txt (nepoužijeme git add .)
                          3. myslíme si, že v staging area sú oba súbory (a.txt aj b.txt), ale my sme addli len súbor a.txt
                          4. commitneme:  git commit -m "Vytvorenie nových súborov a.txt a b.txt"   (!b.txt tam nie je!)
                          5. neskôr si všimeneme, že v commite je len a.txt, ale my sme vytvorili commit, do ktorého sme napísali,
                                že sme pridali oba súbory
                          6. do staging area pošleme súbor b.txt:  git add b.txt
                          7. pomocou  git commit --amend  pridáme súbor b.txt do main commitu (najskôr sa otvorí textový editor
                                v ktorom môžeme zmeniť message pre commit a po zavretí súboru máme updatenutý main commit)

git log             - vidíme všetky naše commity (najstarší na najnižšie)
                    - vypísanie dlhého hashu pre commit

git log --oneline   - všetky commity sa vypíšu každý na jeden riadok
                    - vypísanie krátkeho hashu pre commit
                    - prehliadnejší kód (--oneline sa nazýva OPTION)

git log -n $num     - $num je premenná, ktorá predstavuje naturálne číslo, ktoré nám hovorí koľko záznamov sa má vypísať
                    - keď bude $num = 3, tak sa vypíšu 3 najnovšie commity (master a dva za ním)

git log --all --graph --oneline --decorate
                    - grafické zobrazenie celého .git stromu

git show $hash      - $hash je premenná
                    - keď vypíšeme záznam commitov (log alebo log --oneline) tak sa nám označí hash pre daný commit
                    - v show vidíme čo sa v danom commite zmenili (porovnáme aktuálne verziu a verziu pred aktuálnou)

git checkout $hash  - $hash je premenná
                    - môžme použiť buď krátky alebo dlhý hash, funguju oba
                    - vrátime sa k danej verzii (záleží aký hash sme použili) repa
                    - !POZOR! teraz keď napíšeme "git log" vypíšu sa iba staršie commity ako je tento aktuálny,
                        vnímajme to tak, že sme sa vrátili v čase
                    
git checkout master - preto keď sa chceme vratiť k poslednému commitu (master/main/default/...) tak použijeme tento príkaz
                    - teraz keď napíšeme "git log" tak uvidíme COMPLET všetky commity (od najstaršieho po najnovší->master)

git branch          - vypísanie všetkych branchov

git branch $name    - vytvorenie branche s názvom $name

git branch -d $name - vymazanie brenchu s názvom $name

git branch -D $name - vymazanie branchu s názvom $name, ktorý ešte nebol mergenutý

git branch -m "$newName"
                    - '-m' znamená move
                    - týmto príkazom zmeníme názov branche, na ktorej sa práve nachádzame

git switch $branchName    
                    - prenínanie sa medzi brenchmi, $branchName predstavuje názov branchu, do ktorého sa chceme prepnúť


git switch -c $branchName  
                    - $name je premenná pre názov branche, ktorú chceme vytvoriť
                    - '-c' znamená create
                    - takže celý príkaz znamená vytvor branch s názvom $branchName a rovno nás tam prepni

git checkout $branchName  
                    - prepne nás na branch s názvom $branchName
                    - ekvivalent  git switch $name
                    - switch je novší

git merge $branchName
                    - tento typ mergeu sa nazýva fast-forward merge
                    - vyzerá takto:ä
                    
                  ┏                                                                     ┐
                    MB -> Master Branch
                    FB -> Feature Branch
                    .num -> číslo commitu 
                             ( .1 -> prvý commit
                               .n -> najnovší commit )

                    pred mergeom
                    existuje 2 HEADs:
                                  MB.4 je master HEAD
                                  FB.2 je feature HEAD
                                  
                    MB.1 ---- MB.2 ---- MB.3 ---- MB.4 
                                                    \ 
                                                      \____ FB.1 _____ FB.2
                                                      
                    -------------------------------------------------------------------
                    
                    po merge
                    MB.1 ---- MB.2 ---- MB.3 ---- MB.4 ---- newMB.1 ---- newMB.2

                    Feature Branche (FB.1 a FB.2) sa stali nové master branche
                    newMB.1 = FB.1
                    newMB.2 = FB.2

                    takže teraz existuje iba jeden HEAD a tým je newMB.2 (master HEAD)
                  └                                                                     ┛

git push            - pošleme repo na github kde je hostovaný remotne
                    - je presne to isté ako "git push origin master"
                    - kde origin predstavuje lokáciu git repa 
                    - master predstavuje branch, na ktorú pushujeme





---vytváranie lokálneho repa, pridanie referencie na github repo, commitnutie repa na LM, pushnutie LM repa---
vytvoríme si repo na local machine, otvoríme terminál a píšeme:

1.) git init                - inicializácia gitovského repa

2.) git commit -m ""        - pripravíme repo na push tým, že ho commitneme
    
3.) git push origin master  - teraz to nebude fungovať, pretože na githube, nie je vytvorený repo
                            - chyba je kvoli origin (predstavuje lokáciu git repa)
                            - takže .git teraz nevie kam má pushnuť repo => vyhodí chybu 

kvôli tomu, že .git nevie kam má pushnuť repo, najjednodujhší spôsob je ísť na github a vytvoriť tam repo manuálne

po vytvorení repa na githube sa vrátime na local machine (LM) a pokračujeme

1.) git remote add origin "git@github.com:sknefi/gitNotes.git"
                            - na náš lokálny repo pridáme referenciu na github repozitár
                            - git@github.com:sknefi/gitNotes.git

2.) git remote -v           - overenie referencie LM na github

3.) git push --set-upstream origin main
    git push -u origin main         
                            - tieto dva príkazy robia to isté
                            - u znamená upstream => tu na toto miesto chcem pushovať defaultne

---tips & tricks---
git diff                    - rozdiel medzi pôvodným súborom (ten čo je pushnutý/po prípade
                                stiahnutý z githubu na našej LM) a upraveným súborom (ak sme do   
                                pôvodného súboru niečo napísali)

git commit -a -m ""         - je to skrátená verzia pre: git commid addAll -m ""
                            - kde m predstavuje message: git commit addAll message ""
                            - takže keď napíšeme tento príkaz tak ako prvé sa vykoná:
                                - 1.) git add .         => git add all
                                - 2.) git commit -m ""  => zaznamenajú sa zmeny so správou "..."


GIT BRANCHING

MasterBranch = MB (tiež nazývana ako Master, Main, Default, ...)
FeatureBranch = FB


číslo za bodkou predstavuje číslo commitu


    MB.1 ------- MB.2 ------- MB.3 ------- MB.4 ------- MB.MERGE
                               \                         /
                                \____ FB.1 _____ FB.2 __/ 












