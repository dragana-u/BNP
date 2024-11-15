2. Најди ги шифрите на сите уметнички дела што биле изложени во музеј на отворено.<br>
`πshifra_d(σtip='otvoreno'((Izlozeni ⨝ Izlozba) ⨝ shifra_muzej=shifra Muzej))` 

3. Најди ги шифрите на сите уметнички дела што не биле изложени во музеј на отворено. <br>
`pom = πshifra_d(σtip='otvoreno'((Izlozeni ⨝ Izlozba) ⨝ shifra_muzej=shifra Muzej))
πshifra(Umetnicko_delo) - pom`

4. Прикажи ги сите информации за сите уметнички дела што не биле изложени во музеј на отворено. <br>
`pom = πshifra_d(σtip='otvoreno'((Izlozeni ⨝ Izlozba) ⨝ shifra_muzej=shifra Muzej))
(πshifra(Umetnicko_delo) - pom) ⨝ Umetnicko_delo`

5. Прикажи ги информациите за изложувањата на уметнички дела од Pablo Picasso. <br>
`pom = σumetnik='Pablo Picasso'(Umetnicko_delo)
Izlozeni ⨝ shifra_d=shifra pom`

6. Изброј колку уметнички дела од Pablo Picasso биле изложени на секоја изложба. <br>
`pom = σumetnik='Pablo Picasso'(Umetnicko_delo)
pom2 = Izlozeni ⨝ shifra_d=shifra pom
ρshifra_d->dela(γime_i;count(shifra_d)->shifra_d(pom2))`

7. Прикажи ги информациите за изложбата на која биле изложени најголем број на уметнички дела од Пикасо. <br>
`pom = σumetnik='Pablo Picasso'(Umetnicko_delo) 
pom2 = Izlozeni ⨝ shifra_d=shifra pom
pom3 = ρshifra_d->dela(γime_i;count(shifra_d)->shifra_d(pom2))
πime_i,opis,sprat,prostorija,datum_od,datum_do,shifra_muzej((γmax(dela)->dela(pom3) ⨝ pom3) ⨝ Izlozba)`