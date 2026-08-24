This firmware is designed for the CYD and uses a SI4732 as receiver chip. 

------------------------------------------------------------------------------------------

Getting Started:
Upload the .bin file to the ESP32.
Configure WiFi:
Menu → More → Config → WiFi Cred.
Receiver works offline, but WiFi needed for features.

------------------------------------------------------------------------------------------
Software hints:

ESP 32 file System (LittleFS)
Several config files are stored on ESP32’s LittleFS. They can be downloaded/modified/re-uploaded via WiFi Sync:

MemoInfo.csv -> memory entries
eibi.lst -> EiBi station list
image.img -> last downloaded image
kiwisdr.url -> KiwiSDR server URLs
iradio.url -> Internet radio server URLs
memory.csv -> station list (PicoRX compatible)
splash.jpg -> boot image
*.raw -> saved SSTV images (raw format)
*.bmp -> saved SSTV images (BMP format)

------------------------------------------------------------------------------------------


Encoder:
Push = fine tune mode.
Push again = exit fine tune.


WiFi Sync: Syncs browser with the ESP32 file system. Download, edit, re‑upload config files, station lists and SSTV images.


WiFi interface: Allows to listen remotely. For best sound:
Adjust receiver volume first (avoid clipping).
Fine‑tune volume then with WiFi interface slider.
This feature requires full ESP32 processing power -> other functions may lag or be unavailable.
Exit via Freq -> Boot button.

Decoders:
CW: Best at 500–800 Hz. Align with waterfall red bars.
RTTY: Align mark/space with waterfall bars. Mark should be set to 500Hz. While decoding use encoder for fine tuning.
SSTV: Supports Martin & Scottie. Autodetect is based on sync interval and may fail.
Weatherfax: Experimental. IOC567 format only. Sync unstable.

SSTV files:
Saves SSTV images to SD card (BMP) or LittleFS (.raw or .bmp).
Limited storage: ~12 raw or 4 BMP files. Oldest file gets overwritten when full.


KiwiSDR: Connects to 1 of 10 selectable KiwiSDR servers using the current frequency/mode. KiwiSDR servers can be changed by modifying the config file kiwisdr.url.
Not all will work since this client uses a rather primitive implementation of the (undisclosed) communication protocol between server and client.
To change a server, check http://rx.linkfanel.net/ and http://kiwisdr.com/public/. Try the new server first in a browser and
use a server that does not use cloudflare or similar bot protector.
For SSB and CW the SI4732 frequency needs to be precisely adjusted (Config -> Crystal Offset), otherwise it will cause a frequency offset with the Kiwi server.
The client can now be tuned with the encoder. The first tuning changes will be slow (several seconds) until the internal audio buffer has been adjusted.
Later changes will take around 1 second. Not all servers allow tuning with the encoder.
DLY- and DLY+ can be used if the audio drops, or the audio pitch is too high/low. The correct value depends on the individual hardware and should be around 70 (indicator
on the top right). The client may not function on every hardware, the streaming and decoding chain pushes the ES32 to it's limits.


Internet radio: Experimental. Servers can be changed by modifying the config file iradio.url. Currently only mp3 encoding is supported. Faster streams (>192Kbit)
will most likely stutter.


User Interface
Indicators: Tap indicators below S‑Meter to change values.

