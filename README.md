
# Operating Systems Project (Cache Cleaner)
|Name|Id|
|-|-|
|Muhammad Zain|k21-4729|
|Faisal Khan|k21-4727|


## Intro
The system can access frequently used data more quickly thanks to temporary data storage known as cache memory. Cache memory can fill up over time and affect system performance. . Users of Linux-based operating systems can clean various types of caches using the cache cleaner , a C program. Users can choose from a variety of cache types on a menu provided by the programme, and the cleaning operation is then applied to the selected cache type. The following cache cleaning operations are included in the programm:

<li>System cache memory</li>
<li>Swap cache memory</li>
<li>DNS cache memory</li>
<li>Temporary files</li>
<li>RAM cache memory</li>
<li>ARP cache memory</li>
<li>Other caches on Ubuntu</li>


## Approach
The program uses C standard libraries like stdio.h, stdlib.h, stdbool.h, sys/wait.h, and unistd.h. It defines several functions, including:
<li>SystemCacheMemory() to clear the system cache memory</li>
<li>ClearOutSwap() to clear the swap cache memory</li>
<li>DNSCscheMemory() to clear the DNS cache memory</li>
<li>TemporaryFile() to clear the temporary files</li>
<li>RAMCacheMemory() to clear the RAM cache memory</li>
<li>ARPCacheMemory() to clear the ARP cache memory</li>
<li>OtherCache() to clear other caches on Ubuntu</li>
<li>DoAll() to clear all caches at once</li>


## Working
The main() function presents a menu of cache types to the user. The user selects the desired cache type to clean by entering the corresponding number. If the user selects the "Clean All" option, the DoAll() function is called, which sequentially executes all the cache clearing functions one by one.
<h2>1.System Cache Memory</h2>
This option clears out the system cache memory by dropping cached data from memory by executing this command “echo 1 > /proc/sys/vm/drop_caches”. Before and after running this option, the program displays the status of the system cache memory using the "free -m -h" command


<h2>2.Clear Out Swap</h2>
This option clears out the swap memory by turning swap off and then on again. Before and after running this option, the program displays the status of the swap memory using the "free -m -h" command.

<h2>3.DNS Cache Memory</h2>
This option clears out the DNS cache memory by flushing the system's DNS cache using the "systemd-resolve --flush-caches" command. Before and after running this option, the program displays the status of the system cache memory using the "free -m -h" command and the statistics of the DNS cache memory using the "systemd-resolve --statistics" command.
<h2>4.Temporary Files</h2>
This option clears out temporary files by listing the files in the "/var/tmp" directory, deleting all directories in that directory using the "find /var/tmp/* -type d -delete" command, and then listing the files in the directory again.

<h2>5.RAM Cache Memory</h2>
This option clears out the RAM cache memory by dropping the cache using the "echo 1 > /proc/sys/vm/drop_caches", "echo 2 > /proc/sys/vm/drop_caches", and "echo 3 > /proc/sys/vm/drop_caches" commands. Before and after running this option, the program displays the status of the RAM cache memory using the "free -h" command.

<h2>6.ARP Cache Memory</h2>
This option clears out the ARP cache memory by flushing all entries in the ARP cache using the "ip -s -s neigh flush all" command.

<h2>7.Miscellaneous Caches</h2>
This option installs the "bleachbit" package using the "sudo apt install bleachbit" command and then uses the "bleachbit" command with the "--preview system.tmp" option to preview the system cache memory cleaning. After previewing, the program uses the "bleachbit" command with the "--clean cleaner-name.name" option to clean the system cache memory.
<h2>8.Clean All</h2>
This option runs all of the above options one by one. The program waits for 5 seconds after each option before proceeding to the next.

After executing the command to clear the cache type, the function displays the status of the cache type before and after clearing using the system command free -m -h for memory-based caches and ls for file-based caches.

## Conclusion
  The cache cleaner program provides a convenient way for Linux users to clean various types of caches on their system. It uses system commands to clear the caches and presents a menu-based interface to the user. By running the program, users can quickly free up valuable system resources and improve the performance of their system.

