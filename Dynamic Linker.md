How the dynamically linked libraries are loaded in the confines of a process?

    - Initially there is no process or page of a process installed in the memory even if there is enough memory to store the process. Now, as the program is executed it's process with its PCB is loaded and not all the pages. As the CPU asks for certain bytes for the execution to continue, the dynamic linker finds the byte through file system and loads the corresponding page of that process containing the byte into the memory and maps it's address into the table.
      So, if the process again asks for that byte or a byte in that page its loaded through the address table created earlier and thus no extra memory is wasted.


Are the portions of the library (functions or classes that you are using from that library) loaded in the same process's address space or the Operating System loads the library as a separate process?

     - All the portions of the library that are asked by the CPU for further execution is loaded into the same address space as, if the libraries are stored in different memory locations and spaces than a large process will use a big portion of the memory and several small processes may have to wait indefinitely (starvation), so only a confined space is allocated to a process depending upon its size and all the bytes the CPU asks for is loaded within the process's address space itself.


What if the same Dynamically Linked Library is being used by multiple processes? How will the OS manage then?

      - When a process wants to access a dynamic linked library it makes a copy of it and the data in it and makes the necessary changes (modularity) and thus no change is there in original library and so several processes can use a single Dynamically linked library.
      - In case when Dynamically Linked Library is used by different processes, OS maintains a counter for reference. So, when a process starts using the Dynamically linked library the counter increase and when it stops using it the counter decreases. Also, if the counter reaches zero, the dynamically linked library is unloaded from the memory thus memory efficiency is also increased and only the process using it will have access to it.
