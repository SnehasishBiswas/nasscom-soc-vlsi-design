# nasscom-soc-vlsi-design
## Day1 lab 
 1. Run 'picorv32a' design synthesis using Openlane flow and generate necessary outputs. Screenshots of running each commands:
 cd Desktop/work/tools/openlane_working-die/openlane

  ## docker

 ## ./flow.tcl -interactive
 
 ## package require openlane

 ## prep -design picorv32a
![openlane start](https://github.com/user-attachments/assets/ec9a304d-e6a8-4e25-bf4a-bc78c9a2c244)


## run_synthesis
![run](https://github.com/user-attachments/assets/d520d62e-40e3-4f0c-b14d-4c2bbb350c1d)

2. Calculate the flip-flop ratio.
![Screenshot from 2024-12-01 22-32-09](https://github.com/user-attachments/assets/20600fe4-b15d-49d0-81d8-442a979ed995)
![Screenshot from 2024-12-01 22-31-34](https://github.com/user-attachments/assets/0bd629c8-dd21-4af2-bb20-b4bfc5d379a5)

Calculation of Flip Flop ratio : 

number of D flip Flop = 1613 total number of cells = 14876

Calculating  Flop ratio = no. of D-ff / total cells 

flop ratio = 1613/14876 = 0.108429685

# #How we can run floorplan 
 run_floorplan

2. Calculate the die area in microns from the values in floorplan def
   //Screenshot of contents of floorplan def
   
![def](https://github.com/user-attachments/assets/2f06d706-ded0-42d4-9a01-d299676ee7be)

> According to floorplan def
                                       1000 unit distance = 1 micron
                               Die width in unit distance= 660685-0=66085
                               Die height in unit distance = 671405-0=671405
                             Distance in microns = Values in Unit distance/1000
                             Die width in microns = 66085/1000 = 660.685 microns
                             Die height in microns = 671405/1000 = 671.408 microns
              Area f the die in micron is = 660.685 *671.408 = 443587.212425 square micron
3. Load Generated floorplan def in magic tool and explore the floor plan
# command for load the floorplan def in magic tool in another command
// cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/11-12-24/results/floorplan/
# Change directory to path containing generated floorplan def

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

Screenshot of floorplan def in magic 
                               
![WhatsApp Image 2024-12-11 at 17 22 23_3bfb461d](https://github.com/user-attachments/assets/9614e250-b7af-47a3-9d07-eb6afdeb0a45)

4. Run 'picorv32a' design congestion aware placement using Openlane flow and generate necessary outputs.
   Command to run placement
   run_placement

5. Load generated placement def in magic tool and explore the placement
   # Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-12-24/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![WhatsApp Image 2024-12-11 at 17 22 23_9880f15e](https://github.com/user-attachments/assets/56c69d94-5784-4195-a418-c36ff3135429)
Command run to exit from the current terminal 
>> exit
>> exit

## Section 3 - Design libary cell usign Magic Layout and ngspice 

Theory
Implementation
Section 3 tasks:-
Clone custom inverter standard cell design from github repository: Standard cell design and characterization using OpenLANE flow.
Load the custom inverter layout in magic and explore.
Spice extraction of inverter in magic.
Editing the spice model file for analysis through simulation.
Post-layout ngspice simulations.
Find problem in the DRC section of the old magic tech file for the skywater process and fix them.
Section 3 - Tasks 1 to 5 files, reports and logs can be found in the following folder:
Section 3 - Tasks 1 to 5 (vsdstdcelldesign)

Section 3 - Task 6 files, reports and logs can be found in the following folder:
Section 3 - Task 6 (drc_tests)

1. Clone custom inverter standard cell design from github repository
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &



