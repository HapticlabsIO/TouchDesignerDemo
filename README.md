# TouchDesignerDemo
Simple TouchDesigner demo connected to the Hapticlabs Satellite using a [Chop Execute](https://derivative.ca/UserGuide/CHOP_Execute_DAT) in Combination with the [Serial DAT](https://derivative.ca/UserGuide/Serial_DAT). 

## Getting the Satellite ready
Start of by importing `hapticlabsTouchDesignerDemo.hptl` (File > Export/Import) and uploading the Project to the Satellite (Satellite > Upload Project to Satellite)
<img width="1552" alt="Screenshot 2023-06-10 at 16 27 58" src="https://github.com/HapticlabsIO/TouchDesignerDemo/assets/34678030/4624319b-d955-48ba-8eaf-9ee163b9ccd3">

## TouchDesigner
Inside the Chop Execute is the following code: 
``` python
def onOnToOff(channel, sampleIndex, val, prev):

	# to use Serial
	# op('hapticlabsSerial').module.startTrack("1")
	# op('hapticlabsSerial').module.setAmplitudeScale(0.1)
	
	# to use TCP, make sure to bypass (turn off) the serial block to prevent TouchDesigner from connecting to the Satellite.
	op('hapticlabsTCP').module.startTrack("1")
	op('hapticlabsTCP').module.setAmplitudeScale(0.1)
	return
```

There are two options to control the Satelite, through TCP or Serial.

### 1. TCP 
`op('hapticlabsTCP').module.startTrack("1")` will start the track that is named "1" through TCP. 
> In this case the Satellite is connected to Hapticlabs Studio, and TouchDesigner starts tracks in Studio through TCP. This way you can keep iterating on the tracks without having to upload them to the Satellite all the time. Make sure the "serial" block is turned off to prevent TouchDesigner from trying to connect to the Satellite directly.
<img width="1582" alt="Screenshot 2023-10-11 at 20 05 43" src="https://github.com/HapticlabsIO/TouchDesignerDemo/assets/34678030/a395702a-114b-4ffc-9c30-548452030a79">

### 2. Serial
Alternatively, you can use `op('hapticlabsSerial').module.startTrack("1")`. Make sure the "serial" block is turned on so TouchDesigner is connecting to the Satellite directly, also check that the Baud Rate is set to 115200 and the correct port is selected.
>  If you make changes to the tracks in the Hapticlabs Studio, you need to stop the TouchDesigner project, disconnect the Satellite, connect it in the Studio and upload the Project to the Satellite (Satellite > Upload Project to Satellite).


<img width="1582" alt="Screenshot 2023-10-11 at 20 06 21" src="https://github.com/HapticlabsIO/TouchDesignerDemo/assets/34678030/ca014168-0d70-4e43-9e7b-70e3914e207d">
