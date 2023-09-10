# Kendryte K210 standalone SDK


LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/kendryte-toolchain/bin

export LD_LIBRARY_PATH



mkdir build
cd build/
cmake .. -DPROJ=lcd -DTOOLCHAIN=/opt/kendryte-toolchain 
cmake .. -DPROJ=lcd -DTOOLCHAIN=/opt/kendryte-toolchain/bin 
make -j4
../../../kflash.py/kflash.py -p /dev/ttyUSB0 -t lcd.bin 
pyserial-miniterm /dev/ttyUSB0 115200  --rts 0 --dtr 0

