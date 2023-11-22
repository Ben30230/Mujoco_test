1. Try to rebuild the mujoco by myself.

   Discription of folders: 
   - Needed when rebuilding:
        - `include` include dictionary ()
        - `lib` library
        - `model/KUKA` KUKA xml, converted from the urdf ```bin/compile ***.urdf ***.xml ```
        
            (remember add the head in the urdf first, see [mujoco document](https://mujoco.readthedocs.io/en/stable/modeling.html)
        - `simulate` main source files 

            Note that the loadpng.cc and loadpng.h have been added into simulate/
   - Not needed when rebuilding:
        - `bin/` is the well-built excutable file by the official
        - `sample/` constains other example code 

    Run
    ```
    mkdir build
    cd build
    cmake ..
    make 
    ./simulate ***.xml
    ```
    If compiling fails, check for the dependents of mujoco, see [THIRD_PARTY_NOTICES](./THIRD_PARTY_NOTICES)

2. To visualize KUKA iiwa7 for a specific trajecory
    general idea: specific the angles before every simulation step

    - Changes from the original `main.cc`:
        - line- 557 load iiwa7.xml by default
        - around line 445 force the angles to be the interested ones
        - aroubd line 295 read the angles from the txt file and have some initialization for line 445















