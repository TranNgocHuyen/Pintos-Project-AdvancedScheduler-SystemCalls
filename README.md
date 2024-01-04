# Pintos-Project-AdvancedScheduler-SystemCalls
Pintos OS with Project 1: Threads - Advanced Scheduler and Project 2: User Programs - System Calls
===================
# 1. INSTALL PINTOS OS
1. Download Qemu Emulator :
sudo apt-get install qemu-system
2. Download latest Pintos source code from:
https://github.com/WyldeCat/pintos-anon

3. Unzip Pintos .tar.gz

4. Open file **/utils/pintos-gdb**. 
Edit **GDBMACROS** = <path_to>/src/misc/gdb-macros.

5.In **/utils/**, open the **Makefile** and edit LOADLIBES -> LDLIBS.

6. Open **terminal** in **/src/utils** and type **“make”** to compile utils.

For error **"stropts.h not found"**

$ patch **src/utils/squish-pty.c**
```diff
/*
 #include <stropts.h>
*/

   /* System V implementations need STREAMS configuration for the
      slave. */
/*
   if (isastream (slave))
     {
       if (ioctl (slave, I_PUSH, "ptem") < 0
           || ioctl (slave, I_PUSH, "ldterm") < 0)
         fail_io ("ioctl");
     }
*/
```  
$ patch **src/utils/squish-unix.c**
```diff
+/*
 #include <stropts.h>
+*/
```
7. Edit **/src/threads/Make.vars**
Line 7 : change **bochs** for **qemu.**

8. In **/src/threads**, type **“make”** in terminal to compile the thread
directory.

9. Edit **/utils/pintos**

Line 103: Replace **bochs** with **qemu**.

Line 257: Replace **kernel.bin** with the full path (...src/threads/build/kernel.bin).

Line 621: Replace **qemu-system-i386** with **qemu-system-x86_64**

10. Edit **/utils/Pintos.pm**

Line 362: Replace **loader.bin** for the full path (...src/threads/build/loader.bin)

11. Edit **~/.bashrc** in **/home/** directory

Add “**export PATH=/home/…/pintos/src/utils:$PATH**” at the last line.

12. Type “**source ~/.bashrc**” in the terminal.
    
13. Run “**pintos run alarm-multiple**”

===================
# 2. PROJECT 1: THREADS - ADVANCED SCHEDULER
1. cd ../src/threads
2. make
3. cd build
4. make check
   
===================
# 3. PROJECT 2: USER PROGRAMS

1. Edit **pintos** and **pintos.pm** in **src/utils** : /threads/ -> /userprog/
2. **cd ../src/userprog** ,run **'make'**
3. **cd build** and run 4 line code:
- **pintos-mkdisk filesys.dsk --filesys-size=2**
- **pintos -f -q**.

 (run **'make'** in **src/example**)
 
- **pintos -p /home/tranngochuyen/He_dieu_anh/pintos-anon-master-syscall/src/examples/echo -a echo -- -q** ( replace by link of echo.c)
- **pintos -q run 'echo x'**
4. run **' make check '** and waiting for this process,get the result of test cases

//NOTE: 
before 'make', should 'make clean'
should make utils and source ~/.bashrc

lỗi ERROR 126 thì cd home chmod -R 755 ./* 

https://velog.io/@jing93/PintOS-Error-code-%EC%99%9C-%EB%82%A8%EC%9D%98-%EC%BB%B4%ED%93%A8%ED%84%B0%EC%97%90%EC%84%9C%EB%8A%94-error%EA%B0%80-%EC%95%88%EB%82%98%EB%8A%94%EB%8D%B0-%EB%82%B4%EA%BA%BC%EC%97%90%EC%84%9C%EB%8A%94-%EB%82%98%EB%8A%94%EA%B1%B4%EC%A7%80 
