# MinecraftJVMArgs
My attempt at organizing java arguments because I always forgot and spend hours Googling...


## Tested with Create: Above & Beyond v1.3 for Minecraft 1.16.5 and Forge 36.2.20

# Client
MultiMC 5
```sh
-XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true
```

# Server
The contents of my run.bat to start the server
https://www.reddit.com/r/feedthebeast/comments/lgfr7m/minecraft_forge_jvm_flags_for_high_performance/
```sh
"C:\Program Files\Eclipse Adoptium\jdk-11.0.17.8-hotspot\bin\java.exe" -XX:+UseG1GC -Xmx8G -Xms8G -Dsun.rmi.dgc.server.gcInterval=600000 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:G1NewSizePercent=20 -XX:G1ReservePercent=20 -XX:MaxGCPauseMillis=50 -XX:G1HeapRegionSize=32 -jar forge-1.16.5-36.2.20.jar --nogui
pause
```
