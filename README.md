# MinecraftJVMArgs
My attempt at organizing java arguments because I always forget and spend hours Googling...

> Note:
> + These notes are written for myself, sharing if someone else finds it useful.. No guarantees!
> + I don't have a great understanding of these settings, I've copied and pasted them from various places
> + I've tried to reference where I found the settings
> + These settings may or may not work for you, from what I've read, there is no setting that works amazing for every system...

# Download for the JDK
https://adoptium.net/temurin/releases/
+ Sort by system windows/linux/etc
+ Sort by Java version 8/11/17


# Tested with Create: Above & Beyond v1.3
+ Minecraft 1.16.5
+ Forge 36.2.20
+ I added mods rubidium (performance), oculus (shaders), oauth (refresh game session without having to reboot game) 

## Client
MultiMC 5
https://aikar.co/2018/07/02/tuning-the-jvm-g1gc-garbage-collector-flags-for-minecraft/
+ MultiMC handles the Xmx and Xms flags elsewhere, so I dropped some of the flags below, see the url to aikar's website for the full setting
+ The java installation path set in MultiMC: C:/Program Files/Java/jre1.8.0_202/bin/javaw.exe
  +   Adoptium jdk 1.8.0_352 x64 https://adoptium.net/temurin/releases/
+   For the Xmx/Xms I have it set to 10gb for both, from what I've read they should be the same
  + My system is 32GB
```sh
-XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true
```

## Server
The contents of my run.bat to start the server
https://www.reddit.com/r/feedthebeast/comments/lgfr7m/minecraft_forge_jvm_flags_for_high_performance/
+ My "server" is a Windows 10 PC I use as a home media system. It helps a lot running a server on a 2nd machine, even if it's not a great server..
  + Aspire TC-875: i5-10400, 2.9GHz, 16GB
+ For some reason I used Java 11 on the server (Windows x64)
  + https://adoptium.net/temurin/releases/  
+ I have so many java versions installed on the server, instead of calling just "java" in the bat file below, I reference the exact location of the right java.exe version 
```sh
"C:\Program Files\Eclipse Adoptium\jdk-11.0.17.8-hotspot\bin\java.exe" -XX:+UseG1GC -Xmx8G -Xms8G -Dsun.rmi.dgc.server.gcInterval=600000 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:G1NewSizePercent=20 -XX:G1ReservePercent=20 -XX:MaxGCPauseMillis=50 -XX:G1HeapRegionSize=32 -jar forge-1.16.5-36.2.20.jar --nogui
pause
```

# MISC References
+ https://old.reddit.com/r/feedthebeast/comments/5jhuk9/modded_mc_and_memory_usage_a_history_with_a/
+ https://www.reddit.com/r/feedthebeast/comments/r24zg4/upgrade_your_java_to_one_that_has_the_shenandoah/
