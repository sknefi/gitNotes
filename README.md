SKUSKA 1 2 3 



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


---vytváranie lokálneho repa, 
vytvoríme si repo na local machine, otvoríme terminál a píšeme:

git init            - inicializácia gitovského repa