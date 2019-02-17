# Testing SD Cards and I/O Speed
These are the results from SD card speed tests. We also apply overclocking and measure test results with them.

## Overclocking
To overclock the SD card reader, add the line
```
dtoverlay=sdhost,overclock_50=100
```
to the file `/boot/config.txt`, followed with a re-boot.

## Test methods
We just test a sequential read to have a hint how different cards compare to each other. To make a write test, we call
```
dd if=/dev/zero of=~/test.tmp bs=500K count=1024
```
and to make a read test, we call
```
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
dd if=~/test.tmp of=/dev/null bs=500K count=1024
```

## Test results
|SD Card|Write Speed<br/>Factory Declaration<br/>MB/s|Read Speed<br/>Factory Declaration<br/>MB/s|Sequential Write Test<br/>MB/s|Sequential Read Test<br/>MB/s|Sequential Write Test<br/>(Overclocked)<br/>MB/s|Sequential Read Test<br/>(Overclocked)<br/>MB/s|
|---|---|---|---|---|---|---|
|SanDisk Extreme 128GB UHS-I U3 A1 V30|90|100|22.5|23.4|26.5|38.3|
|SanDisk Ultra 32GB C10 U1 A1|?|98|20.3|23.6|17.4|38.8|
|Transcend Premium 32GB C10 U1|?|90|18.5|23.4|13.4|37.4|
|SanDisk Extreme 32GB V30 U3 A1|40|90|31.1|23.7|27.9|39.0|
|Transcend Premium 16GB C10 U1|?|90|9.8|23.4|11.3|38.0|
|SanDisk Extreme Pro 64GB UHS-I U3 A2 V30|90|170|26.6|23.6|25.9|38.5|
|SanDisk 16GB C2|?|?|6.5|18.2|7.5|30.3|
