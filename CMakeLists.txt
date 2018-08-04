cmake_minimum_required(VERSION 3.11)

set(SRCS main.c lex.c subs.c getopt.c) # kparse.key


find_package(BISON)
BISON_TARGET(a56 a56.y ${CMAKE_CURRENT_BINARY_DIR}/a56.c)

add_executable(a56 ${SRCS} ${BISON_a56_OUTPUTS})
#FIXME:	$(CC) $(CFLAGS) -o a56 $(OBJS) -lm

add_executable(keybld keybld.c subs.c)

#lex.o:	lex.c gram.h

#kparse.c:	a56.key keybld
#	$(abspath keybld) < a56.key > kparse.c

#toktab.c:	gram.h
#	awk -f tok.awk < gram.h > toktab.c

add_executable(toomf toomf.c)
add_executable(torom torom.c subs.c)

#main.o gram.o lex.o:	a56.h
