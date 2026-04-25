# Gameboy Go 🎮
<img width="1239" height="673" alt="image" src="https://github.com/user-attachments/assets/ad8a3670-6cc9-48d4-8877-787aa0777b75" />

A handheld console for playing retro games with an interesting sliding mechanism. The console has aspects of a Gameboy and a PSP Go, which led to the name. I made this as a part of [Hackclub's Stasis](https://stasis.hackclub.com) program which funds custom hardware projects. I decided to make a game console because I thought it could teach me a lot of new things and allow me to explore topics I'd been interested in for a long time. It also seemed like it would be very fun, and I could continue using it after I finished the build.

## Setup
### The steps you'll need to get up and running with a Gameboy Go

1. Order all the parts based off the BOM
2. Solder your electrical components onto your PCB based on the models and schematics
3. Download RetroPie using the raspberry pi imager and put it on a SD card into the raspberry pi
4. Use a computer and the command line to get setup and change the configuration files according to the instructions
5. Unplug all components 
6. Assemble the bottom half of the case in this order - Bottom, PCB, Middle, Buttons, Top
7. Assemble the top half of the case containing the screen in this order - Bottom, Display, Top
8. Route the wires to connect the screen to the main case
9. Plug it into a power source
10. You're done!

## Features
### What this console can do and what it's made of

- 2 part sliding black and yellow case
- 3.5 inch screen
- 15 buttons including face buttons, a DPAD, shoulder buttons, menu buttons, and volume controls
- 3.5mm audio jack for headphones

## CAD 
### The 3d model of the case and components

I modeled in fusion 360 but I also got a lot of models for components online. In total, this will require 21 screws and 17 nuts. 7 will be used to hold parts of the case together, 2 will be used for the PCB, and 8 will be used for the hinges. There are 3 separate parts in the main case. The bottom, the middle, and the top. The other portion has 2 parts to sandwich the screen so just a top and bottom. The parts are held together by 4 hinges. The wires for the screen are routed through the back and there is also a hole there for power. 

Images:
<img width="1519" height="996" alt="image" src="https://github.com/user-attachments/assets/def9c7c7-5a06-4624-ad97-e111944a7dd8" />
<img width="1366" height="948" alt="image" src="https://github.com/user-attachments/assets/5284c898-b7bd-493e-9221-a458f6ce8fc6" />
<img width="1467" height="874" alt="image" src="https://github.com/user-attachments/assets/7d454ad3-ae2b-4e1c-ae2d-6074161e417b" />
<img width="1080" height="807" alt="image" src="https://github.com/user-attachments/assets/1431f54b-c0c0-45e3-af72-554b3a8e6b3c" />

## PCB 
### Details about the PCB I made

I made my PCB in KiCad. I used it before for other projects so I already knew the basics. My schematic was pretty simple but included things like a low-pass filter for the audio. The PCB layout was also easy to make but I just had to work around a lot of the constraints with making a PCB of this size with this many components. 

Schematic:

<img width="1039" height="919" alt="image" src="https://github.com/user-attachments/assets/2e1e866a-19bd-4e1e-bacb-bbaf06367f59" />

PCB:

<img width="1353" height="976" alt="image" src="https://github.com/user-attachments/assets/bb0972db-5f60-40d9-bf89-f2dd837a485d" />

3d Renders:

<img width="1595" height="1063" alt="image" src="https://github.com/user-attachments/assets/a11a69a2-2ef7-4dd2-b60a-ee7964903bb2" />
<img width="1622" height="837" alt="image" src="https://github.com/user-attachments/assets/1af4781b-989a-47d9-a50e-4c59421de808" />
<img width="1362" height="979" alt="image" src="https://github.com/user-attachments/assets/0ea85aa3-eab1-4728-ab03-5c5bf2ca229d" />
<img width="1609" height="1149" alt="image" src="https://github.com/user-attachments/assets/6062ad18-defe-4a90-b274-cb66dc858734" />

## Software Configuration
### How to get setup with the software and make RetroPie work with this console

There wasn't much to do on the software/programming side of this project. I had planned from the start to use an emulator called RetroPie for the console. It handles almost everything and you just need to set it up and change some things to match your console. 

<img width="520" height="140" alt="image" src="https://github.com/user-attachments/assets/992be77a-8fa4-4579-9230-18b467f9b3f2" />


In order to get RetroPie working on the Gameboy Go, you have to add audio functionality, configure the WaveShare screen, and use RetroGame for button inputs. 

First, get your screen up and running by accessing the pi from your computer and following [these instructions](https://www.waveshare.com/wiki/3.5inch_RPi_LCD_(G)#Calibrate_Resistive_Touch_Screen) from the official wiki. 

Then, add these lines to your config.txt file to get audio on the headphone jack working:
```
dtparam=audio=on

audio_pwm_mode=2
(This may be on by default but if not add it)
```

Finally, for the buttons, you need to [install RetroGame](https://learn.adafruit.com/retro-gaming-with-raspberry-pi/adding-controls-software) from Adafruit in order to convert button inputs from GPIO pins to key presses. Then, you need to edit the retrogame.cfg file to match the one provided in the configuration folder. 

That should be everything needed to get the console running nicely. 

## BOM
### Bill of materials needed with names, links, and quantities

| Name | Amount | Link |
|---|---|---|
| Raspberry pi Zero 2 w | 1 | [Raspberry pi](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/?variant=raspberry-pi-zero-2-w) |
| 3.5inch RPi LCD (G) | 1 | [WaveShare](https://www.waveshare.com/3.5inch-rpi-lcd-g.htm?srsltid=AfmBOopoyxl4aeTF2s5BtMy4MCuqwqXwdewwnlaeLHAK1Bwd1KD4Ym0p) |
| 6mm Push Buttons | 11 | [Adafruit](https://www.adafruit.com/product/367?srsltid=AfmBOoqAj2fYT_9Y2s0Y7QZpG46cAeABVtzY1UmmWIn-tXu1GYy3M0Tw) |
| 270 ohm resistors | 2 | [MicroCenter](https://www.microcenter.com/product/689184/leo-sales-ltd-resistors-05w-270ohm-metal-oxide-10-pack) |
| 33nF Capacitors  | 2 | [Aliexpress](https://www.aliexpress.us/item/3256806455818371.html?spm=a2g0o.productlist.main.1.157364ba1Yi2YQ&algo_pvid=a6c3f40d-cf68-4b87-af1d-c807c6ebc1ea&algo_exp_id=a6c3f40d-cf68-4b87-af1d-c807c6ebc1ea-0&pdp_ext_f=%7B"order"%3A"526"%2C"eval"%3A"1"%2C"fromPage"%3A"search"%7D&pdp_npi=6%40dis%21USD%212.16%210.99%21%21%2114.67%216.68%21%402101c44517770998316333468e44ca%2112000037902429351%21sea%21US%210%21ABX%211%210%21n_tag%3A-29910%3Bd%3A1deda900%3Bm03_new_user%3A-29895%3BpisId%3A5000000203537349&curPageLogUid=ahvGlUmzWuX5&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005006642133123%7C_p_origin_prod%3A) |
| M3 Hex Nuts | 17 | [Home Depot](https://www.homedepot.com/p/Everbilt-M3-0-5-Zinc-Hex-Nut-5-Pieces-862798/323368368) |
| M3 Screws | 17 | [Home Depot](https://www.homedepot.com/p/M3-0-5-x-25-mm-Phillips-Pan-Head-Stainless-Steel-Machine-Screw-2-Pack-842748/204283766) |
| M2.5 Screws | 4 | [Home Depot](https://www.homedepot.com/p/Prime-Line-M2-5-0-45-x-10-mm-Zinc-Plated-Steel-Phillips-Drive-Pan-Head-Metric-Machine-Screws-25-Pack-9130848/311229794)|
| Sparkfun 5-way Switch | 1 | [Aliexpress](https://www.aliexpress.us/item/2251832459877116.html?src=google&src=google&albch=shopping&acnt=708-803-3821&isdl=y&slnk=&plac=&mtctp=&albbt=Google_7_shopping&aff_platform=google&aff_short_key=UneMJZVf&gclsrc=aw.ds&albagn=888888&ds_e_adid=&ds_e_matchtype=&ds_e_device=c&ds_e_network=x&ds_e_product_group_id=&ds_e_product_id=en2251832459877116&ds_e_product_merchant_id=107407105&ds_e_product_country=US&ds_e_product_language=en&ds_e_product_channel=online&ds_e_product_store_id=&ds_url_v=2&albcp=19558607238&albag=&isSmbAutoCall=false&needSmbHouyi=false&gad_source=1&gad_campaignid=19566915268&gclid=CjwKCAjwqazPBhALEiwAOuXqdOePMoYkzu9AJ8uqxPdbrhwhWEiKvReEP_qOVmW35NRlWhqx1O2liRoCb6cQAvD_BwE&gatewayAdapt=glo2usa) |
| Sparkfun TRRS Breakout | 1 | [Sparkfun](https://www.sparkfun.com/sparkfun-trrs-3-5mm-jack-breakout.html?gad_source=1&gad_campaignid=17479024039&gclid=CjwKCAjwqazPBhALEiwAOuXqdJmdIlovKzbgYQDtQEwtJ_wsp0qeUwmUB5OWLQOMiqpNB_8F0yb3FhoCtgUQAvD_BwE) |
| 40 Pin Header | 1 | [Adafruit](https://www.adafruit.com/product/2822) |
| 12 Pin Header | 1 | [Aliexpress](https://www.aliexpress.us/item/3256808907494688.html?src=google&src=google&albch=shopping&acnt=708-803-3821&isdl=y&slnk=&plac=&mtctp=&albbt=Google_7_shopping&aff_platform=google&aff_short_key=UneMJZVf&gclsrc=aw.ds&albagn=888888&ds_e_adid=&ds_e_matchtype=&ds_e_device=c&ds_e_network=x&ds_e_product_group_id=&ds_e_product_id=en3256808907494688&ds_e_product_merchant_id=5667405338&ds_e_product_country=US&ds_e_product_language=en&ds_e_product_channel=online&ds_e_product_store_id=&ds_url_v=2&albcp=20123152476&albag=&isSmbAutoCall=false&needSmbHouyi=false&gad_source=1&gad_campaignid=20127768206&gclid=CjwKCAjwqazPBhALEiwAOuXqdN9Pz6WZsAVT2R7mCSNVDfhqV7nhC78X3GVik8dpSUpEzkkHtHR5fBoCjmkQAvD_BwE&gatewayAdapt=glo2usa) |
| 3d printed case and components | 1 | N/A |

## Extras
### Random related things

I made the logo with the help of chat gpt and then edited it in Canva.

<img width="2518" height="1283" alt="image" src="https://github.com/user-attachments/assets/bed98c92-bf17-4601-97b1-1c9a93cfda0b" />

These are some photos of my original brainstorming sketches in my notebook:
<img width="499" height="692" alt="image" src="https://github.com/user-attachments/assets/e4778f40-c28e-435a-8679-7194097114b8" />
<img width="554" height="399" alt="image" src="https://github.com/user-attachments/assets/8b27a7e1-2f9e-4560-a2be-c1445c6fea11" />

I think I succesfully made what I originally envisioned in these sketches and I had a lot of fun coming up with them.

This design was inspired a lot by the PSP Go and Gameboy, but also by a build I saw from Marcin Plaza where he made a sliding phone. 
<img width="480" height="360" alt="image" src="https://github.com/user-attachments/assets/5c30268e-f7fd-409a-8508-5c7db813ea2c" />

Some changes I could still make -
- Embedding magnets in the case
- Adding a battery
- Improving the shoulder buttons

# Thank you so much for reading and being interested in my project! If you would like to know more feel free to reach out to me. I hope you enjoy what I've made as much as I have.
