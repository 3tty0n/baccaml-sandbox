CC := gcc
CFLAGS := -m32
OCAMLOPT := ocamlopt
MINCAML := min-caml

interp.opt: interp.s main.o libmincaml.o interop.o
	$(CC) $(CFLAGS) -lm -I`ocamlc -where` -L`ocamlc -where` $^ -o $@ -lcurses -ldl -lasmrun

clean:
	$(RM) *.opt *.o

%.o: %.S
	$(CC) $(CFLAGS) -lm -c $<

%.s: %.ml
	$(MINCAML) $<

%.so: %.s libmincaml.S
	$(CC) $(CFLAGS) -fPIC -shared -ldl -lm $^ -o lib$(basename $<).so

%.o: %.c
	$(CC) -c $(CFLAGS) -I`ocamlc -where` $^
