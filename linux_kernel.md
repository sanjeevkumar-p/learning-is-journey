https://www.linkedin.com/posts/abhinavu_we-know-that-the-linux-kernel-is-preemptive-activity-7249766820130238464-n2kU?utm_source=share&utm_medium=member_android

https://www.linkedin.com/posts/siddharthanand_futex-wikipedia-activity-7248514450763206656-tkXc?utm_source=share&utm_medium=member_android

https://www.linkedin.com/posts/aditya-pratap-singh-412755192_ldd-embeddedsystems-interview-activity-7252970447829389312-IHuX?utm_source=share&utm_medium=member_android

Pstore or ramoops provides a mechanism to persistently store kernel crash logs, such as oops messages, panic logs, or other debug information, in a reserved non-volatile memory region - persistent RAM or flash.
https://embear.ch/blog/using-ramoops

https://www.linkedin.com/pulse/linux-kernel-how-detect-user-space-crashes-log-austin-kim-v3ucc?utm_source=share&utm_medium=member_android&utm_campaign=share_via

https://www.linkedin.com/feed/update/urn:li:activity:7271789562153095169?utm_source=share&utm_medium=member_desktop&rcm=ACoAACiwM6cBP6MTyCRvMwe-eTyBVQleG6Rmc-E

[Arm] Debugging patch for stack corruption
https://www.linkedin.com/pulse/arm-debugging-patch-stack-corruption-austin-kim-spevc?utm_source=share&utm_medium=member_android&utm_campaign=share_via

To increase debug level of kmod in run time,
echo 'module <module_name> +p' > /sys/kernel/debug/dynamic_debug/control
example: 
echo 'module ecm +p' > /sys/kernel/debug/dynamic_debug/control
+p - enables pr_debug level prints ; to disable, -p 
echo 'module ecm -p' > /sys/kernel/debug/dynamic_debug/control
To list all modules which we can enable debug level:
cat /sys/kernel/debug/dynamic_debug/control | awk '{print $5}' | sort | uniq
