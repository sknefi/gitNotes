https://www.youtube.com/watch?v=RGOj5yH7evk&t
https://www.youtube.com/watch?v=_qSB6jN4A3s&list=PLQ8x_VWW6AkuVs1oyWth3lXA4D4jxD_7F


funguje???

#HELLO THEEERE

čím lepšie si spíšeš ťahák, tým je menšia šanca, že ho použiješ

---vytvorenie repozitára na gite, naklonovanie ho na local machine, upravenie repa, pushnutie ho späť na github---
git clone git@github.com:sknefi/$name.git
ls -la              (zobrazí všetky súbory v danom súbere, -la zobrazí aj hidden súbory)

git status          (zobrazí čo všetky som zmenili v rámci repozitára)
                    - keď sa dačo zmení dostaneme v termináli správu "modified"
                    - keď pridáme file v termináli sa vypíše "untracked" to znamená, že .git nepozná
                    a nepozná tento file (je netrekovaný). Pridáme ho pomocou git add

git add $p          - $p vnímajme ako premenu/parameter
                    - $p = cesta od hlavného repozitára (ten, ktorý sme naklonovali)
                    - $p = .    => pridaj všetko čo je v repozitári (bodka predstavuju current folder)
                    - $p = index.html    => file, ktorý obsahuje clonenutý repo (/gitNotes/index.html)
 
git commit -m ""    - vždy keď commitujeme repo musíme zadať -m "" čo predstavuje správu
                    - správou môže byť napr. -m "pridaný index.html"
  

git commit -m "" -m ""      - prvé -m "" predstavuje správu
                            - druhé -m "" predstavuje description

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












