# Creating Static Libraries:

1. Firstly compile all the source file as -
	# gcc -c abc.c -o abc.o
	# gcc -c xyz.c -o xyz.o

2. Bundle all the object files(.o) into a final static library(.a) using archive cmd:
   	# ar rs <libNAME.a> <.o files> 
   	where, NAME is the name of the library we want eg. library for doubly linked list as "libdll.a"
	# ar rs libdll.a abc.o xyz.o

3. Linking of the static library into your application source file:
	A. You mush have static library(.a) file in PWD or its absolute path if not in PWD.
	B. Now compile the application source file/s and get its object(.o) file/s.
	C. Now link the .o file/s with the static library file(.a) using the cmd:
		# gcc <.o file/s> -o exe -L /absolute/path/of/the/library -l<library_name>
		# gcc application.o -o exe -L . -ldll
		# ./exe (run)
		where, -L is for path to the library &
		       -l is for linking the specified library
		        . for PWD(present working directory)



# Creating Dynamic Libraries:

1. Firstly compile all the source file using -fPIC flag -
   * **PIC - Position Independent Code
	# gcc -c fPIC abc.c -o abc.o
	# gcc -c fPIC xyz.c -o xyz.o

2. Bundle all the object files(.o) into a final 'dynamic library' or shared object(.so) using gcc -shared flag:
   	# gcc abc.o xyz.o -shared -o libdll.so

3. Linking of the dynamic library into your application source file:
	A. Place the "libdll.so" file at the default location(/usr/bin or /usr/local/bin) where all the dynamic libraries are kept & load the configuration file using cmd:
		# sudo ldconfig
		This cmd will tell the OS that we have just added a shared library so please make a note of that.
		
	B. Now compile the application source file/s and get its object(.o) file/s.
	C. Now link the .o file/s with the dynamic library file(.so) using the cmd:
		# gcc application.o -o exe -ldll
		# ./exe (run)
		Note: Here path is not provided as the library is kept at the default location.





## For more info refer to Derek Kwok blog:
https://medium.com/@dkwok94/the-linking-process-exposed-static-vs-dynamic-libraries-977e92139b5f


