# Vashtastic: A Simple and Cool Meshtastic Node

## 10-July-2026

### The Start:

Vashtastic is a Meshtastic Node which you can carry in your Pocket. For those who Don't know what a Meshtastic Node is, It's a Device which has the ability to Talk to other devices without using Internet, it does this by Blasting Radio Waves in the Sky so other Devices can hear it and connect to it. This Device would help you connect and talk with your Friends without Internet (Both Should have this device). and now for the Nerds. I'm using an **ESP32-S3-WROOM-1 Micro-controller** which is wired to multiple Components such as:

- A GPS (Quectel L76K)
- RF Transciever-LoRa (E22-900M22S)
- E-ink Display (Waveshare 2.9In)
- An LDO (ME6211C33M5G)
- Battery Charger (TP4056)
- USB-C
- MOSFET (for GPS, so it doesn't always be ON)

These Components will be connected to the ESP32. I have also Added Capacitors and Resistors to every Components which require it. Vashtastic will be a Compact and Small Device, so a 2.9In Screen is Perfect for that. One more Thing I'm going to add is a Map, which points the Location of other Nodes in the area. This way You can Track Where your Friends are. The Reason I have Chosen E-Ink Display is because It takes Almost no Power After it has Drawn the Picture/Map etc. and Also because it Looks cool. I have Only done Research as of Now and will start working on the Project from tomorrow.

## 11-July-2026

### Starting the Schematic:

- **ESP32-S3-WROOM-1:** 

The First I had to Find was the Strapping pins of the ESP32 from the datasheet, and to research what each Pin Does. I looked up the Datasheet and Looked through it and Found what i was looking for. the Strapping Pins of ESP32 are GPIO-0, GPIO-3, GPIO-45 and GPIO-46. Since I'm using EasyEDA so it was easy to find the Component in the library. now i had to find all the other components and place those.

- **E22-900M22S:**

This is one of the Main Core Components of this device, it is the Module which sends Radio Waves into the Sky, it has pretty Long Range (LoRa). About 7-8 Km. its a Module which connects to the ESP32 and sends Radio data via the SPI pins. It was Pretty Easy to wire because I had already Used a Similar Module in my previous PCB (Bebop). The one I used before was called LoRa-RFM95W, which is also pretty good. Well I placed the component and wired the SPI pins to the GPIO pins of ESP32.

- **Quectel L76K:**

This is the GPS module so that the Map works flawlessly, it will get the Coordinates and send them to the ESP32, which would then be sent to the E-ink display to Point the Coordingates on the Map. I would have to use the Open-Source Meshtastic Firmware. But thats for Later.

- **ME6211C33M5G:**

This is an LDO, which gets the current from the Battery and Converts it to a Smooth 3.3V for all the Components. Without this, the Device wouldn't work.

- **TP4056:**

This is the Li-ION Battery Charger, without this, if a person would try to charge the battery through the USB-C port, the Battery would either catch fire or Explode, or Both. This Battery Charger takes the Current and Charges the Battery so it doesn't explode or stuff. 

- **USB-C:**

Not much to say about this tbh, its a USB-C port. it connects to the Battery Charger.

- **E-Ink Display:**

This is the Cool Display, the module I used has 8 pins and the entire pre-soldered board connects to the pins easily.

I placed all the components and wired the power system first. the power works like this. you plug in the USB-C and the Power goes through the Battery charger first which makes the Voltage good for the battery, the battery charges and then the battery is connected to the LDO, which regulates the battery voltage to a smooth 3.3V for all the components, and then finally all the components are wired to the LDO.

![Power-System](assets/Power-Schematic.png)

 After the Power systerm, i worked on the ESP32 and the Radio Module. Like i said before that it was pretty easy because you just have to match the pins and wire each on of them, the DIO1 pin can be wired to any GPIO pin i think, and you leave the DIO2 pin floating or put a No connect flag on it.

![ESP32 and LoRa](assets/ESP-LoRa-Schematic.png)

 After the wiring is complete for the Radio modulle and ESP32, then you can work on wiring the GPS and E-ink display to the Micro-controller. For the GPS, I added a MOSFET so that GPS is not always turned ON and sips power, so i connected the mosfet to the 3.3V and then the drain is connected to the GPS, i also added a 100K ohm resistor so the GPS doesn't take any power. The wiring for the GPS was easy because you only have to wire 6-7 (no please) pins. i should probably give space between things mb.Oh yeah i also made a silly mistake of connecting the TXD and RXD pins to the TXD and RXD pins of the ESP-32, i basically matched and wired it too but they have to be connected to each other for example, TXD should connect to RXD and vice versa.

![GPS](assets/GPS-Schematic.png)

 Now it was time to wire up the E-ink display. the first problem i had was that i couldn't find the module in the library, but i found out that it was in the user contributed tab. people had made the mmodule available. good people. Since the module only has 8 pins, i connected each pin to the micro-controller's gpio pins and it was done. 

![E-ink](assets/E-ink-Schematic.png)

 I also added alot of capacitors and resistors according to the datasheet of each component.

 After this I was finished with the Schematic. now the hard part is the PCB layout, which i will do tomorrow or after 5 minutes (its 11:55PM rn). After wiring everything up, here's the Schematic:

 ![Schematic Vashtastic](assets/Schematic-1.png)

 I also added a no connect flag on everything which was not connected. I have a headache right now but i have to complete 84 hours. and i only have 20 days left. I'm so cooked man. I did 5 hours today which is not bad but i need to do 10 hours tomorrow.