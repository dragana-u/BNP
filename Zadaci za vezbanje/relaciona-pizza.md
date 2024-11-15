1. Излистај ги пиците што биле нарачани од најмалку една девојка на возраст над 20 години. <br>
`πpizza(σ age>20 ∧ gender='female' (Person ⨝ Eats))`
2. Најди ги имињата на сите девојки што нарачале најмалку една пица што се служи во Straw Hat. (Забелешка: Пицата не мора да биде нарачана од Straw Hat.) <br>
`π name(σ gender='female' ∧ Serves.pizzeria='Straw Hat'  ((Serves ⨝ Eats)⨝Person))`
3. Најди ги сите пицерии што служат пици што биле нарачани од Amy или од Fay (или од двете), а се поефтини од $10. <br>
`πpizzeria(σ(name='Amy' ∨ name='Fay') ∧ price < 10(Eats ⨝ Serves))`
4. Најди ги сите пицерии што служат пици што биле нарачани од Amy или од Fay (или од двете), а се не поевтини од $10. <br>
`πpizzeria(σ(name='Amy' ∨ name='Fay') ∧ price > 10(Eats ⨝ Serves))`
5. Најди ги сите пицерии што служат пици кои биле нарачани од Amy и од Fay, а се поефтини од $10. <br>
`amy = πpizzeria(σname='Amy' ∧ price<10 (Eats⨝Serves))
fay = πpizzeria(σname='Fay' ∧ price<10(Eats⨝Serves))
amy ∩ fay`
6. Излистај ги имињата на сите луѓе што нарачале барем една пица што се служи во Dominos, но истите не го посетиле Dominos. <br>
`πname(σpizzeria='Dominos'(Eats ⨝ Serves)) - πname(σpizzeria='Dominos'(Frequents))`
7. Најди ги сите пици што биле нарачувани од луѓе помлади од 24 години, или што чинат најмногу $10 без разлика каде се служат. <br>
`πpizza(σage<24 ∨price<=10((Eats ⨝ Person) ⨝ Serves ))`
8. Најди ја возраста на најстарото лице (или лица) што нарачало пица со печурки (mushroom pizza). <br>
`ρage←max(γmax(age)→max(σpizza='mushroom' (Eats ⨝ Person ⨝ Serves)))`
9. Излистај ги сите пицерии што служат пици кои биле нарачувани од луѓе постари од 30 години. <br>
`πpizzeria(σage>30((Person ⨝ Eats) ⨝ Serves))`
10. Излистај ги сите пицерии што служат пици кои биле нарачувани само од луѓе постари од 30 години. <br>
`πpizzeria(Serves) - πpizzeria(σage<30((Person ⨝ Eats) ⨝ Serves))`
11. Најди ги сите пицерии што биле посетени од лица помлади од 18 години. <br>
`πpizzeria(σage<18((Person ⨝ Frequents) ⨝ Serves))`
12. Излистај ги имињата на сите девојки што јадат пица со печурки (mushroom pizza) или пица со кулен (pepperoni pizza) (или двете). <br>
`pom = σpizza='mushroom' ∨ pizza='pepperoni'(Eats ⨝ Person)
πname(σgender='female'(pom))`
13. Излистај ги имињата на сите девојки што јадат и пица со печурки (mushroom pizza) и пица со кулен (pepperoni pizza). <br>
`females = σgender='female'(Person ⨝ Eats )
pecurki = πname(σpizza='mushroom'(females))
kulen = πname(σpizza='pepperoni'(females))
pecurki ∩ kulen`
14. Најди ги сите пицерии што служат барем една пица што е поефтина од $10 и Amy ја јаде. <br>
`πpizzeria(σname='Amy'∧ price<10((Person ⨝ Eats) ⨝ Serves))`
15. Најди ги пицериите што ги посетуваат само девојки или само момчиња. <br>
`maski = πpizzeria(Person ⨝ Frequents) - πpizzeria(σgender='female' (Person ⨝ Frequents))
devojki = πpizzeria(Person ⨝ Frequents) - πpizzeria(σgender='male' (Person ⨝ Frequents))
(devojki ∪ maski)`
16. За секое лице, најди ги пиците што лицето ги јаде, но не се служат во ниедна од пицериите што лицето ги посетува (да се вратат паровите име на лице – име на пица). <br>
`jade = πname,pizza(Eats ⨝ Person)
odi = πname,pizza(Frequents ⨝ Serves)
jade - odi`
17. Најди ги имињата на лицата што посетуваат само пицерии што служат пици кои тие ги јадат (барем една пица). <br>
`(π name(Person)) - (π name(((π name,pizzeria((Person) ⨝ Frequents)) - (π name,pizzeria((Person) ⨝ Eats ⨝ Serves)))))`
