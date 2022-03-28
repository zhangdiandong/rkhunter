
 * 1.4.6 (20/02/2018)

 New:
 - Added support for Alpine Linux (busybox).
 - Added the 'Diamorphine LKM' test.
 - Added the ALLOWIPCPID configuration file option. This will allow
   specific PIDs to be whitelisted from the shared memory check.
 - Added the ALLOWIPCUSER configuration file option. This will allow
   specific usernames to be whitelisted from the shared memory check.
 - Added the IPC_SEG_SIZE configuration file option. This can be used
   to set the minimum shared memory segment size to check. The default
   value is 1048576 bytes (1MB).
 - Added the SKIP_INODE_CHECK configuration file option. Setting this
   option will disable the reporting of any changed inode numbers.
   The default is to report inode changes. (This option may be useful
   for filesystems such as Btrfs.)
 - Added Ebury sshd backdoor test.
 - Added a new SSH configuration test to check for various suspicious
   configuration options. Currently there is only one check which
   relates to the Ebury backdoor.
 - Added basic test for Jynx2 rootkit.
 - Added Komplex trojan test.
 - Added basic test for KeRanger running process.
 - Added test for Keydnap backdoor.
 - Added basic test for Eleanor backdoor running process.
 - Added basic tests for Mokes backdoor.
 - Added tests for Proton backdoor.
 - Added the SUSPSCAN_WHITELIST configuration file option. This
   option can be used to whitelist file pathnames from the
   'suspscan' test.

 Changes:
 - The 'ipc_shared_mem' test will now log the minimum segment size
   that will be checked. It will also log the size of any segments
   which appear suspicious (that is, larger than the configured
   allowed maximum size).
 - If verbose logging is disabled, then generally only the test
   name and the final result for the test will now be logged.
 - Kernel symbol checks will now use the 'System.map' file, if it
   exists, and no other kernel symbol file can be found.

 Bugfixes:
 - For prelinked systems ensure that the default hash function is
   SHA1 and not SHA256.
 - The result from the 'hidden_procs' test was not being
   calculated correctly.
 - Checking the O/S version number could be missed in some cases.
 - Minor improvement to the *BSD immutable files check.
 - The 'OS_VERSION_FILE' configuration option pathname cannot be
   a link, but this was not checked.
 - Improved checks for the O/S name on Devuan systems.
 - Handling of the '/etc/issue' file during O/S detection has now
   improved. Escape sequences are either replaced or removed.
 - Not all the linux kernel module names were being checked.
 - The logging of detached memory segments tried to show the
   process pathname. This has now been corrected, and where no
   pathname is available, the segment owner and PID will be logged.
 - It was possible for the return code to be lost when running the
   'ipc_shared_mem' test. This has now been corrected.
 - Some configuration options were still not being handled correctly
   when specified more than once.
 - The 'ipc_shared_mem' test did not correctly handle whitelisting
   when a segment pathname was flagged as deleted. This has now
   been corrected.
 - Commands disabled in the configuration file were being logged
   as not found. They are now logged as having been disabled.
 - Disabling verbose logging could hide some warning messages.
 - The 'shared_libs' test now caters for simple filenames, as well
   as pathnames which contain the '$LIB', '$ORIGIN' or '$PLATFORM'
   variables.

