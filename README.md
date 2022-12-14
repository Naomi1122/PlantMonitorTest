# PlantMonitorTest




## Construction of the physical prototype sensor

| Hardware | Description |
| --- | --- |
| ESP8266 | For connecting to wifi and publish data to MQTT server |
| DHT22 | Sensor for temperature and humidity |
| ultrasonic rangefinder | detect movement of any approaches within certain distance |
| LED bulb | connect with ultrasonic rangefinder to flash |
| resistor | Limit the voltage to tolerant range |
| nails | measure resistance between for moisture |
| Raspberry Pi | Store and visualise the data |
| board | Extension of pin connection |

### Detailed assembly pictures

![3541668596214_ pic](https://user-images.githubusercontent.com/78373920/202162719-599d699f-2209-420d-8df0-5733a5e260e4.jpg)

The above picture shows the details of the welding of these nails and wires for the first time. Because of the instability of the moisture data measurement, I chose to re-solder the interface with the wires and install a 3D printed plastic holder for the nails showed in the below picture. 3D printing makes it more consistent with the two The distance between nails to ensure that the resistance reads the correct moisture value.

![nail2](https://user-images.githubusercontent.com/78373920/203058742-a16eee42-b3a5-4623-bb26-df1af08f0e87.jpeg)

The resistors and the DHT22 sensor are soldered onto ESP8266 so the kit is fixed in place as showed in the below pictures. The output pin mode and the input pin mode are also showed below. There are two wires reached out for connection of the nails.

![3551668596214_ pic](https://user-images.githubusercontent.com/78373920/202162724-e8dd9d93-cd62-4c75-86ee-1757b02abdde.jpg)
![3561668596215_ pic](https://user-images.githubusercontent.com/78373920/202162726-2f0233d6-f625-4790-80ae-eb88eb3380ab.jpg)

Below, the pictures show how the ultrasonic rangefinder and the bulb are connected to the basic plant monitor showed above. I used a zinc board for extension pins as the breadboard is too large in size so not suitable but the extra equipments require for more pins to connect. The coding for this part is designed as the bulb will begin to flash if the ultrasonic device detect an object within 100cm distance, and the speed of flash bulb will increase as the distance between the object and the ultrasonic device decreases. There are also two resistors connected in series between the output pin of the module and GND for ultrasonic rangefinder to connect with ESP8266 as the voltage has to be limited from 5V of ultrasonic rangefinder to 3.3V of ESP8266.

![360](https://user-images.githubusercontent.com/78373920/203066165-82407671-3038-46b4-8f10-f841197d2930.jpeg)

## Position of the sensor

The figure elow shows the position of basic plant monitor when in use with a plant, the drawback of this prototype is that the distance between the nails are random, all depends on how the users insert them but the users are not suppose to gain the knowledge of the correct distance. Incorrect distance between the nails will result in incorrect values of resistance thus incorrect readings of moisture.
![3501668596212_ pic](https://user-images.githubusercontent.com/78373920/202162893-bd06e456-cbc3-4e50-8142-4d8096cdd395.jpg)

As shown in the graph of data collected on the night of 15th of November which is in the next section. There???s a sudden rise and then drop between half past two and three, then the reading rise back permenantly to 80s after 3. The sudden change might be a leakage of water or a shift of places of the nails.  
Therefore, I???m going to find out the maximum reading that the sensor can take by putting the nails into water and the readings of moisture goes up to 288. The problems occurs here as the maximum reading should be 1024 of maximum testing moisture when the nails are in a place full of water. Apart from the distance between the nails can make a difference on the measurements, I???m try to figure out if the depth of the nails in the soil can make a difference in the measurements as well, so I changed the depth of the nails in water from being completely submerged in water to taking out half its length above the water. However the readings of moisture are not much difference.

![3511668596212_ pic](https://user-images.githubusercontent.com/78373920/202162898-7ffd2496-584c-444c-b806-c02e142b21bc.jpg)

This is the final prototype of my plant monitor and how it is positioned with the plant.

![359](https://user-images.githubusercontent.com/78373920/203066043-0cfcca21-f51c-41e7-a26c-144e2270b3c8.jpeg)


## Data visualisation
The whole data visualised in the graph by telegraf in influxdb for the night of using the basic prototype of plant monitor. The peak value at beginning is when I watering the plant with a whole bottle of water. Then the abnormal values of moisture readings have been discussed in the section above.
<img width="1438" alt="test1" src="https://user-images.githubusercontent.com/78373920/202160364-83393011-c8bf-4ffb-afa5-e3a9cef84639.png">

The moisture data read in the figure below is inaccurate, because the data is very unstable in the same soil without touching the nails and adding water. Therefore, more experiments are required.
<img width="1246" alt="3" src="https://user-images.githubusercontent.com/78373920/202160380-4bbd7756-d25a-41ee-b7b3-b1e80e7fdff6.png">

Data gathered when the nails are submerged in the water, we can see a sudden rise to 288 when the nails are submerged in water.
<img width="1243" alt="4" src="https://user-images.githubusercontent.com/78373920/202160377-6ba85fcb-9b8a-4871-bb25-2d8d9708ef2d.png">


Data gather when the nails are in the correct position since the moisture reading is in between 10-15, this suggests that the other parts of my plant monitor has been built in right place, only the distance needed to be amend to correct position and hold fixed.
<img width="1244" alt="correct1" src="https://user-images.githubusercontent.com/78373920/202163617-aab76db4-cf4a-4596-b7af-ce65cc3f1d95.png">

Below shows the data collected with the final prototype of the plant monitor, the three readings remains constant when the moisture dropped after a period of time, that's when I put the nails from water into soil.
<img width="1245" alt="p3" src="https://user-images.githubusercontent.com/78373920/203049678-a9a4e2ce-4480-410d-8cc1-8d6fe5bfde1a.png">

Another thing I want to specify as the readings changes several minutes after the environment of the sensor changed, therefore, it can be worthy to change the requency of uploading data from one minute to an hour for future long term use.

