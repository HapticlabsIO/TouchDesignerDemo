# TouchDesignerDemo
Simple TouchDesigner demo connected to the Hapticlabs Satellite using a [Chop Execute](https://derivative.ca/UserGuide/CHOP_Execute_DAT) in Combination with the [Serial DAT](https://derivative.ca/UserGuide/Serial_DAT). 

Inside the Chop Execute is the following code: 
``` python
def onOnToOff(channel, sampleIndex, val, prev):
	print(";startTrack(\"0\");")
	op('serial1').send(";startTrack(\"1\");")
	return
```
This will send ";startTrack(\"1\");" on the Serial connection to the Satellite and will start the track that is currently loaded on slot 1. You can also use custom commands or create multiple instances of the Chop Execute to trigger different tracks whenever you want.

Make sure the Baud Rate is set to 115200 and the correct port is selected.

<img width="1440" alt="Screenshot 2023-05-15 at 15 39 46" src="https://github.com/HapticlabsIO/TouchDesignerDemo/assets/34678030/8549cced-f149-4d4a-99ae-c3aa5e897f6c">
