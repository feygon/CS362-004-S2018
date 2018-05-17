CFLAGS = -Wall -fpic -coverage -lm

DEFAULT:
	Use cases: rngs.o, dominion.o, playdom, interface.o, player, clean, randomTests, randomTestCard1, randomTestCard2, randomTestAdventurerCard

rngs.o: rngs.h rngs.c
	gcc -c rngs.c -g  $(CFLAGS)

dominion.o: rngs.o
	touch dominion.c
	touch dominion.h
	gcc -c dominion.c dominion.h -g  $(CFLAGS)

playdom: dominion.o playdom.c
	gcc -o playdom playdom.c -g dominion.o rngs.o $(CFLAGS)

#To run playdom you need to enter: ./playdom <any integer number> like ./playdom 10*/
interface.o: interface.h interface.c
	gcc -c interface.c -g  $(CFLAGS)

player: player.c interface.o
	gcc -o player player.c -g  dominion.o rngs.o interface.o $(CFLAGS)

clean:
	rm -f *.gcov *.gcdo *.gcno *.out *.o randomtestadventurer randomtestcard1 randomtestcard2

randomTests: dominion.o rngs.o
	touch dominion.c
	make dominion.o
	gcc -o randomtestcard1 randomtestcard1.c dominion.o rngs.o -g $(CFLAGS)
	gcc -o randomtestcard2 randomtestcard2.c dominion.o rngs.o -g $(CFLAGS)
	gcc -o randomtestadventurer randomtestadventurer.c dominion.o rngs.o -g $(CFLAGS)
	./randomtestcard1 &> randomtestresults.out
	./randomtestcard2 &>> randomtestresults.out
	./randomtestadventurer &>> randomtestresults.out
	gcov dominion.c	>> randomtestresults.out
	cat dominion.c.gcov >> randomtestresults.out

randomTestCard1:
	touch dominion.c
	make dominion.o
	gcc -o randomtestcard1 randomtestcard1.c dominion.o rngs.o -g $(CFLAGS)
	./randomtestcard1 &> randomtestcard1result.out
	gcov dominion.c >> randomtestcard1result.out
	cat dominion.c.gcov >> randomtestcard1result.out

randomTestCard2:
	touch dominion.c
	make dominion.o
	gcc -o randomtestcard2 randomtestcard2.c dominion.o rngs.o -g $(CFLAGS)
	./randomtestcard2 &> randomtestcard2result.out
	gcov dominion.c >> randomtestcard2result.out
	cat dominion.c.gcov >> randomtestcard2result.out

randomTestAdventurerCard:
	touch dominion.c
	make dominion.o
	gcc -o randomtestadventurer randomtestadventurer.c dominion.o rngs.o -g $(CFLAGS)
	./randomtestadventurer &> randomtestadventurerresult.out
	gcov dominion.c >> randomtestadventurerresult.out
	cat dominion.c.gcov >> randomtestadventurerresult.out
	gcov randomtestadventurer.c &> cfile.out
	cat randomtestadventurer.c.gcov &>> cfile.out
