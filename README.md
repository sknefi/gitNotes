https://www.youtube.com/watch?v=RGOj5yH7evk&t
https://www.youtube.com/watch?v=_qSB6jN4A3s&list=PLQ8x_VWW6AkuVs1oyWth3lXA4D4jxD_7F

čím lepšie si spíšeš ťahák, tým je menšia šanca, že ho použiješ

Git
  - beží na našej lokálnej mašine (LM)
  - nemusíme mať internet
  - zaznamenáva zmeny kódu lokálne
GitHub
  - cloud, na kotrý umiestňujeme repozitáre, ktoré obsahujú postupne vyvýjanie nášho projektu
  - použijeme ho v tedy keď chceme mať zálohované súbory / pracujeme v tíme a potrebujeme medzi sebou zdielať kód
  - môžme to považovať ako sociálnu sieť

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



---vytvorenie repozitára na gite, naklonovanie ho na local machine, upravenie repa, pushnutie ho späť na github---

git clone git@github.com:sknefi/$name.git
                    - z ssh linku si naklonujeme repo na LM

ls -la              - zobrazí všetky súbory v danom súbere, -la zobrazí aj hidden súbory

rm -rf              - vynútené zmazanie (používa sa na mazanie folderov)

rm -rf .git         - vymaže git z repa v LM

git status          - zobrazí čo všetky som zmenili v rámci repozitára
                    - keď sa dačo zmení dostaneme v termináli správu "modified"
                    - keď pridáme file v termináli sa vypíše "untracked" to znamená, že .git nepozná
                    a nepozná tento file (je netrekovaný). Pridáme ho pomocou git add

git add .
                    - bodka znamená pridaj všetko
                    
git add $filename
                    - pridanie súboru, ktorý sa nachádza v danom repo (/gitNotes/index.html)
 
git commit -m ""    - vždy keď commitujeme repo musíme zadať -m "" čo predstavuje správu
                    - vždy keď commitneme tak sa commitne celý repo
                    - správou môže byť napr. -m "pridaný index.html"
  

git commit -m "" -m ""      - prvé -m "" predstavuje správu
                            - druhé -m "" predstavuje description

git log             - vidíme všetky naše commity (najstarší na najnižšie)
                    - vypísanie dlhého hashu pre commit

git log --oneline   - všetky commity sa vypíšu každý na jeden riadok
                    - vypísanie krátkeho hashu pre commit
                    - prehliadnejší kód (--oneline sa nazýva OPTION)

git show $hash      - $hash je premenná
                    - keď vypíšeme záznam commitov (log alebo log --oneline) tak sa nám označí hash pre daný commit
                    - v show vidíme čo sa v danom commite zmenili (porovnáme aktuálne verziu a verziu pred aktuálnou)

git checkout $hash  - $hash je premenná
                    - môžme použiť buď krátky alebo dlhý hash, funguju oba
                    - vrátime sa k danej verzii (záleží aký hash sme použili) repa
                    - !POZOR! teraz keď napíšeme "git log" vypíšu sa iba staršie commity ako je tento aktuálny
                    
git checkout master - preto keď sa chceme vratiť k poslednému commitu (master/main/default/...) tak použijeme tento príkaz
                    - teraz keď napíšeme "git log" tak uvidíme COMPLET všetky commity (od najstaršieho po najnovší->master)


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












