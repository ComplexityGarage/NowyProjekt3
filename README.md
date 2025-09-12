# Antenna Prototype
# Authors 
- Magdalena Stępień,
- Wiktoria Pawelczyk,
- Maciej Mędrek 
# Description of the project 
As part of our technical project, we built a VHF antenna designed to receive airband radio communications between pilots and air traffic control. These transmissions typically operate in the frequency range of 118 to 137 MHz. Our goal was to construct a simple, functional, and cost-effective prototype antenna suitable for aviation radio monitoring. This project allowed us to explore basic antenna theory, RF propagation, and practical aspects of antenna construction. 
# Science and tech used 
Material used: 
- Radiating element and ground radials – 5 aluminum rods, each approximately 60 cm in length
- Custom designed mounting block – designed in SolidWorks and 3D printed, used to hold and position the rods
- Coaxial cable – for signal transmission, with a minimum length of 1 meter
- Antenna socket – for connecting the antenna to the receiver
- RTL-SDR receiver (Software Defined Radio) – used to receive and decode VHF airband signals 
# State of the art 
This antenna prototype was used for monitoring pilot communications. To verify its operation we tested the antenna’s performance near the airport. We utilized the SDR Angel application to receive the signals. Although we could clearly hear that a signal was present, it was quite noisy and the sound quality was not as good as we expected.  
# What next?
The next step of this project would be to find a method to reduce the noise in the signal. In the SDR software, noise reduction filters can be applied to improve signal clarity. Another approach is to use a low-noise amplifier to boost the signal strength before processing, which helps increase the signal to noise ratio. An additional goal would be to strengthen the antenna’s construction for improved durability and stability. 
# Operation guide: using SDR Angel with the antenna prototype 
When the antenna is connected, you need to add the device in the SDR Angel application. In the “Add RX Device” tab, search for your device’s name (it should appear as RTL-SDR (serial number). After completing this step, two windows should open: one named after your device (File Input Plugin), which is used for configuring the antenna, and another with the same name (Main Spectrum Window), which is used to monitor the signal from the antenna. 

Next, in the antenna settings window, find the option “Show All Channels,” and within it, open the “AM Demodulator” window. 

Once all the necessary windows are open, set the antenna parameters as follows: 
- Set the received signal frequency to the range where pilots communicate, approximately from 118 MHz to 138 MHz. The optimal value is the frequency used by the control tower at the nearest airport (this information can be found online). For Krakow, this frequency is 123.255 MHz.
- Set the “SR” (Sample Rate) parameter to 2,040,000 S/s or 2,048,000 S/s. This indicates the number of samples per second taken by the RTL-SDR tuner.
- Change the “DC” (Decimation) parameter to 1. This controls the sample rate reduction during subsequent processing stages.
- Adjust the “Gain” parameter to a value between approximately 15 and 40. It is best to test several values to determine which provides the best signal reception. Too low a value will result in a weak signal, while too high a value may overload the tuner, causing no signal to be registered (in my case, the value was around 21).
- In the “AM Demodulator” window, set the “Sq” (Squelch) value so that sound becomes audible. This is a noise gate that mutes audio below a certain dB threshold. The current dB value is displayed in the top right corner in real time. Your squelch value should be slightly lower but as close as possible to this number to prevent noise when no transmission is active.
- Leave all other parameters at their default automatic settings.
Once everything is set up, observe the signal display window for characteristic peaks. If you are tuned to the correct frequency, you should hear conversations between pilots and the control tower. If you notice peaks at frequencies other than the one set, you can adjust for this by using the “Δf” field in the AM Demodulator window, selecting a value that aligns your antenna’s reception with the peak signal. Remember, pilots do not communicate with the tower continuously, so the best chance to capture their conversations is during takeoff or landing. 
# Sources 
- [Writing on GitHub] ( https://docs.github.com/en/get-started/writing-on-github )
- https://www.rtl-sdr.com/rtl-sdr-quick-start-guide/
- https://my.solidworks.com/training
- https://sq9jdo.com.pl/Niezbednik/Bandplan/lotnicze.html 
