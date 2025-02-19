# Gallant Lab headcase production pipeline
This doc contains instructions on how to generate a headcase using the Gallant Lab materials and pipeline [Last updated 10012021].<br><br>There are three main steps outlined in this tutorial. First, scan the subject's head with a 3D structure scanner. Second, use the caseforge-pipeline code to generate the headcase model. Finally, print the headcase with the 3D printer.

## Materials
1. 5th generation, 2017 iPad
2. 3D scanner ([Structure Sensor PRO and iPad bracket](https://store.structure.io/buy/structure-sensor-pro#bundle-selector)), swim cap, and hood
3. 3D printer ([Ultimaker S5](https://ultimaker.com/3d-printers/ultimaker-s5)) and filaments ([white PLA](https://www.dynamism.com/material/filament/ultimaker-nfc-pla-white.html))
4. Optional tools: flat-head screwdriver, [dremel](https://www.amazon.com/Dremel-Cordless-Variable-Multi-Purpose-Accessory/dp/B07R9PNRBD/ref=sr_1_1?dchild=1&keywords=dremel&qid=1625796956&sr=8-1&srs=5538998011)

## How to use the Structure Sensor to scan the subject's head
Make sure the [Scanner app](https://apps.apple.com/us/app/scanner-structure-sdk/id891169722) and the [Calibration app](https://apps.apple.com/us/app/structure-sensor-calibrator/id914275485) have been downloaded. The scanner app is used to scan the subject's head, and the calibration app is used to calibrate the distance between the structure scanner's camera and the iPad's camera. 

### Prepare the subject.
Have the subject put on both the swim cap and the hood. The swim cap should be rotated 90 degrees, such that the seam goes from ear to ear. Instruct the subject to pull the cap down, past their ears, to eliminate wrinkles. The hood should also be smoothed to remove wrinkles and pulled down and forward to reveal the back of their neck. They should hold the hood down and forward during the scan. See the image below as a reference.
![alt text](https://github.com/gallantlab/caseforge-pipeline/blob/master/docs/explanatory_ims/pipeline_preparethesubject.png)

### Scan the subject's head.
Connect the scanner to the iPad and open the Scanner app. Before starting the scan, adjust the settings to match the options below:
<img src="https://github.com/gallantlab/caseforge-pipeline/blob/master/docs/explanatory_ims/pipeline_scansettings.png" width="200"/>


NOTE: Sometimes, changing all the settings above causes the app to crash. If so, the most important settings to change are switching "High Resolution Color" to "off", "Depth Stream Preset" to "Body", and "Tracker Type" to "Depth Only".

Stand about 3ft (1m) away from the subject, so the scanning window captures the subject's head + neck and not their shoulders. Start the scan and slowly walk around the subject. Occasionally angle the scanner up and down, to make sure to capture the tip of the subject's nose and the top of their head. After making two full rotations around the subject, stop the scan. If the scan is not smooth and continuous, restart the process. See the image below as an example.<br><br>
<img src="https://github.com/gallantlab/caseforge-pipeline/blob/master/docs/explanatory_ims/pipeline_exampleheadscan.png" width="200"/>

Once you have a good scan, send the file to an email you can access.

## How to create the headcase from the head scan.
1. Download and unzip the Model.zip file received from the Scanner app.
2. Open the Model.obj in [Meshlab](https://www.meshlab.net/). Visually check the model for any discontinuities or noisy patches. Manually remove extraneous portions of shoulder or other floating bits that aren't head/neck/face. 
3. Follow the instructions in the case-forge [readme](https://github.com/gallantlab/caseforge-pipeline) to automatically generate the headcase. Make sure the requirements are installed and run the following command<br>
`python make_headcase.py Model.zip Headcase.zip --headcoil s32 --nparts 2`

## How to print the headcase.
1. Create an [Ultimaker account](https://ultimaker.com/software/ultimaker-cura) and ask a senior lab member to add you to the Gallant Lab group. 
2. Download the [Ultimaker Cura software](https://ultimaker.com/software/ultimaker-cura) and sign in to your account.
3. Upload both the front and back headcase stl files. Rotate and set the front to x=70mm. Set the back to x=-70mm. The two should be touching.
4. In the `PREPARE` page, select the correct filament type and set the folloing print settings:
    - Profiles
      - Default = 0.2
      - Visual = 0.15
      - Engineering = 0.1-0.15
      - Draft = 0.2
    - Infill = 15%
      - Can use 5% for tests.
    - Support = Extruder 1
      - This indicates we're using the same filament for creation and structural support of the headcase. To use a different material, load it into Extruder 2 and select Extruder 2 here.
    - Adhesion = select
6. Download the [custom support plugin](https://marketplace.ultimaker.com/app/cura/plugins/lokster/CustomSupports) and use it to add supports to the headcase.
7. In the `PREVIEW` page, make sure there is enough filament loaded to print the headcase.
8. Print the headcase! This should take about 24 hours.
9. Once the printing is complete and the printer bed has fully cooled, remove the headcase from the printer and indicate on the printer that the object has been removed from the bed.
10. (Optional) Use a flat head screw driver to chip away the supporting material. Use the dremel to smooth any rough portions.

All that's left is to test the headcase in the scanner! First make sure the headcase fits in the head coil without the subject. Then check that the subject is comfortable with the headcase and head coil. 
