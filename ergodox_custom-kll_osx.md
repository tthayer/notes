How to flash the ergodox using your own kll files
* With help from http://input.club/forums/topic/compiling-from-kll
  
1. `brew install dfu-util`
2. `git clone https://github.com/kiibohd/controller.git`
3. `cd controller`
4. `git submodule add -f https://github.com/kiibohd/kll.git`
5. `cp ~/Downloads/MDErgo1-Default-7cf3dec5b2d47f11e838c3f5be45e2f9/MDErgo1-Default* kll/layouts`
6. edit Keyboards/ergodox.bash
7. Change the DefaultMap line to read "MDErgo-Default-0 lcdFuncMap"
8. Add a PartialMaps value for every map under the base that you have defined in the configurator.
    eg. `PartialMaps[1]="MDErgo1-Default-1"`, `PartialMaps[2]="MDErgo1-Default-2"`
9. Save your changes to ergodox.bash and then run it: `./ergodox.bash`
10. This will create a build folder for each side of the keyboard, Keyboards/ICED-L and Keyboards/ICED-R.
11. Put your keyboard into programming mode and run `dfu-util -D Keyboards/ICED-L/kiibohd.dfu.bin` 
12. Unplug and replug in the main cable to the left side and enjoy your new layout.
