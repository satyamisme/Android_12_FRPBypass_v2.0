 <p align="center">
 
<img width="200px" src="https://user-images.githubusercontent.com/26827453/176991950-163cb923-25b2-411d-b570-37aea163692a.png" />
  <h3 align="center">(Works for Motorola devices with Android 12 and GBoard installed as default)</i></h3>
</p>

# Motorola

Here is another way how you can get benefits to bypass factory reset 
protection for any `Motorola` device that comes with GBoard from Google 
installed as default.

I have been using a Motorola G50 under all my tests and this repo will 
have  a lot of info for Motorola's devices so I keep everything in this README that I think is worth to share 
for anyone that is interested in this topic.

I was asked by a friend to help his girlfriend to unlock her device since she
forgot wich mail that was used and it seems they gave up and asked me instead.

So as usual when friends asking I am willing to help as long as their are the
owner of the device and that's never a problem of course but before I will help
anyone IRL i have one thing I always do and that is to factory reset the device 
in recovery mode before I going home and start working on the devices for not only mine
but also their privacy, I really have no interest in other people's privacy and I know
that they eat up a sensitive area with these kinds of questions and because many people 
who are not aware of the area can become suspicious IF something were to happen to them, 
it has happened that I was accused of having planted back doors and all that kind of thing 
at one time or another, but of course it has never happened, but I also understand that 
,you can think like that if you don't have 100% control. But no matter what, 
I want to start this wiki for those who want to follow it step by step to show how 
I wiped the phone in fastboot before I started to yes, explore fastboot of course but a
lso so that I am clear about how I went about the exact steps for steps as
I found quite a lot in the week I got to have the phone and explore.

So.. During this week I will now show you everything that I have found on Motorola's 
latest system and also how to oem unlocking key is generated and much more this.

Will I ssucceed or fail? I never using google and looking for other users way to bypass 
because my goal is not to manage to get past the protection and then it's good, no no.. 

Everything for me is about developing myself and finding my own paths so that's why 
all my wikis are always unique from others, when I'm done I usually take some time to 
browse around how other people have done things and what they missed and then I will create
new ways that will help others since it helped me, for example how to enter `engineering mode` 
by clicking an url, there is some sites that offering to open "settings" by clicking via an intent url
but I tried some important features that have been added to my documentation for android 
so we can just get to the right sections by clicking on the urls..

I have added following on application launcher section my documentation for adb shell and you will find them on the url below:

[Motorola - UUSD Secrets - Click to open](https://android.nr1.nu/applicationLauncher.html#motorola)

Following click to open has been added, all works to access when we are behind FRP lock, i have confirmed this ofc but
remember you must browse to the website to be able to click the urls, it wont be able to click them here this is just to show you what was added:

* Click to Open - Radio Info
* Click to Open - FCM Diagnostics
* Click to Open - Engineering Mode
* Click to Open - IMEI window
* Click to Open - Regulator information
* Click to Open - Calendar Debugging

***

## Android 12 - Motorola

Alright, before I booted to system I was exploring Fastboot and Fastbootd since this is new 
features that has been added since Android 10 from Google but  all about this will be found below the FRP Part 

## Before I booted up device for the first time, i wiped **all** partitions by following code

``` bash
#!/bin/bash
#############################################################################
# Author: wuseman
# Date: 2023-01-31
#############################################################################
# 
# - Wipe all partitions from fastboot, 
# - Built for Motorola G50, Android 12
#
#############################################################################

( fastboot oem partition 2>&1 )  \
	|awk -F' ' '{print $2}'   \
	|sed 's/://' \
	|sort > partitions.txt; 

while read line; do 
	fastboot erase ${line}; 
done < partitions.txt

read -p "Reboot to system (y): " reboot2system

if [[ ${reboot2system} = "y" ]]; then 
	fastboot reboot
else
	echo "We are still in fastboot, run your commands: fastboot <command>"
fi
```

# Partitions for Mototorla G50:

Not all these will be wiped and it will give you a permission denied reply. Instead of the code above it is also possible to use a much simpler command as:

```bash
fastboot erase all
```

```
abl_a
abl_b
apdp
bluetooth_a
bluetooth_b
boot_a
boot_b
carrier
cid
ddr
devcfg_a
devcfg_b
devinfo
dhob
dsp_a
dsp_b
dtbo_a
dtbo_b
frp
fsc
fsg_a
fsg_b
hw
hyp_a
hyp_b
keymaster_a
keymaster_b
kpan
last_parti0
last_parti2
last_parti3
last_parti4
last_parti5
logfs
logo_a
logo_b
metadata
misc
modem_a
modem_b
modemst1
modemst2
padA
persist
prodpersist
product_a
product_b
prov_a
prov_b
qupfw_a
qupfw_b
rpm_a
rpm_b
secdata
ssd
storsec_a
storsec_b
super
system_a
system_b
system_ext_a
system_ext_b
tz_a
tz_b
uefisecapp_a
uefisecapp_b
uefivarstore
userdata
utags
utagsBackup
vbmeta_a
vbmeta_b
vbmeta_system_a
vbmeta_system_b
vendor_a
vendor_b
vendor_boot_a
vendor_boot_b
vm-data
vm-keystore
xbl_a
xbl_b
xbl_config_a
xbl_config_b
```

## FRP Bypassing

After the full wipe of device from fastboot, i have just done a normal reboot and we are now in Intro page from Setup Wizard. 

And now, follow the steps below for this rae bypass I have found. I have verified this
four times so it was not just a simple crash by random, this is for sure working for your motorola device with the same version installed.

Now, follow this steps, if you followed my unique way to get into settings on Samsung 10, 
Android 11 you will see this is the same and we are using the permissions to succeed again. 
This is really something I have found myself and the first time it was all just a destiny 
really because I was tired that day few years ago and I have done so many bypasses
because this, this is so funny because all this hacks because a simple mistake when I was 
pressing 1mm below the "ALLOW copy" and this phenomenon you will follow now have 
just been the way I doing my personal bypasses edverytime now in one way or another that 
based on DENY permissions to ALLOW us to bypass ;) Funny! However. Lets move on.

## Android 12 - v2: Crashing GBoard, bypass 

* Screen: That is what is on current window
* Task: What you should do in the current window


| Screen                         | Task                                           |
|--------------------------------|------------------------------------------------| 
| `Hi There`                     | Press `start`                                  |
| `Connect to Mobile Network`    | Press `skip`                                                                                      |
| `Connect to Wifi`              | Connect to your wifi as usual to get online, you will be redirected to next page when connected   | 
| `Privacy & Software Updates`   | `Accept` & `Continue` - Wait for next screen it will search for updates                            | | 
| `Copy apps and data`           | Press `don't copy` | 
| `Verify pin`                   | Press: `Use my Google account instead`   | 
| `Verify your Account (locked)` | Press: `Forgot email?`
| `Find your email`              | Type: `admin` and hit `next`  | 
| `What's your name?`            | Press inside the `First Name` input box, gboard will now popping up | 

Now when  you have gboard open, follow these 3 steps:

* Press Microphone icon in upper right of gboard. 
* Allow Gboard to record audio: Press: `Dont allow` you will now see a little notification at bottom that `no permission to allow microphone` and we doing the task again to permanent deny microphone
* Allow board to record audio: Press `Dont allow`

Now, the third time we gonna press microphone button it will be available to 
press on the icon it wont ask you as before it will just block our request and we gonna see:

No permission to enable: Voice typing.


Now, we gonna crash the gboard. Click the microphone button quickly several 
times until gboard will freeze and you notice this when you can't press anything 
and there are reactions.

Gboard disappears and restarts, it will pop up automatically after 1-2-3 seconds 
we crashed GBoard.. Screen will be dimmed and we gonna do  the same thing again and now, 
press the microphone icon until screen gets dimmed and gboard freezes and 
continue press anywhere on the goard window and the magic happens you will see: 
"Gboard Keeps stopping" and now, press `app info` on the crash notification
and now you will be redirected to settings for gboard.

Now you can FRP bypass and move further to do much you are me have bypassed the factory protection screen to continue 
which should not be possible, therefore it is a protection, but what is the protection worth? 

Nothing basically it's extremely bad that it's this easy every time.

No worries, I wont leave you here.

Let me show you how to continue form here to bypass the Motorola G50 
if you have no idea how to move further. Let's keep hacking this device.


You should now be in the Gboard Setting Menu after we crashed goard and wanted to get more info about this from above step.

| Current Screen                       | Task                                           |
|------------------------------|------------------------------------------------| 
| `App Info`    | Press: `Screen Time`| 
| `Screen Time`    | Press upper right corner menu: `Manage Data` | 
| `Manage Your Data`  | Press: `Clock options` |
| `Set a consistent bedtime for better sleep`  | Press: `Get Started` |
| `Set a regular wake-up alarm`  | Press: `Sound` |
| `Alarm Sound`  | Press: `Youtube Music` |
| `Alarm Sound`  | Press: `Press login` |
| `Music - Open the world of music`  | Press: `Press device files only` |
| `Music`  | Press: `face icon at upper right corner` |
| `Account`  | Press: `Privacy Policy - Terms of Service` |
| `Welcome to Chrome`  | Press: `Acceot & continue`|
| `Turn on sync?`  | Press: `No thanks` |
| `Youtube - Terms of service`  | Enter url to Application Launcher Press: `https://android.nr1.nu/applicationLauncher.html` |
| `Android Application launcher`  | Press: `Click to Open - Settings` |
| `Settings`  | Press: `System navigation` |
| `System navigation`  | Enable (change to): `Gesture navigation` |
| `Gesture navigation`  | Enable (change to): `Gesture navigation` |
| `Gesture navigation`  | Press: `Settings` |
| `Gesture settings`  | Set: `Left/Right` to highest value |
| `Gesture settings`  | Press: `arrow left (go back)` |
| `Apps`  | Press: `See all XX apps` |
| `All apps`  | Press: `Android Setup` |
| `App info`  | Press: `Force stop ` -> `ok` |
| `App info`  | Press: `arrow left (go back)` |
| `All apps`  | Press: `Google play services` |
| `All info`  | Press: `Disable` -> `Disable app` |
| `All info`  | Press: `arrow left (go back)` |
| `All apps`  | Press: `arrow left (go back)` |
| `Apps`  | Press: `arrow left (go back)` |
| `Settings`  | Press: `Accessibility` |
| `Accessibility`  | Press: `Accessibility Menu` |
| `Accessibility Menu`  | Enable: `Accessibility Menu shortcut` |
| `Allow Accessibility menu to....`  | Press: `Allow` |
| `Use Accessibility button to open`  | Press: `Got it` |
| `Accessibility Menu`  | Draw finger from bottom and up: `Visit home screen` |
| `Motorola Android 12 GUI Home Screen`  | Draw finger from bottom and up: `Visit home screen` |
| `Manage Your Data`  | Press: `Daily device Usage` |
| `Turn off usage access?`  | Press: `Turn off in Settings` | 
| `Usage acces`  | Press 3 dots in upper right corner menu: `Show all system` | 
| `Usage access` | Press `Google Play Services` (this app is choosed so don't just press a random one, ive already checked so keep following this step by step)
| `Usage access` | Press twice on google play services icon at top
| `App Info`  | Press: `App Permission ` | 
| `App permissions`  | Press: `on (I` on any options in the right side of any permission in this window | 
| `Help`  | Press: `sharing icon` | 
| `Sharing popupo`  | Press: `Launch messages` | 
| `Select convertation`   | Press: `New message` | 
| `Select convertation`   | Press: `New message` | 
| `New converstation`   | Press: `Create group` |
| `New group converstation`   | Click on nummerpad at end of type a name input to get numeric keyboard` |  
| `New converstation`   | Press: `any number` and then yuou will see send to, press the send to option | 
| `Messages`   | click on `Text message` input |
browsing around.

If you prefer t follow this by pictures instead, I spent my time for sharing this with you as well of course and hopefully I will help some guys hopefully

## Press START

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707225-94e6f6d5-5441-4c55-a7ca-d3e229c45708.png" />

## Press Skip

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707165-62246830-8100-4b0a-a9af-55f228d6597a.png" />

## Choose your wifi network and enter your password and connect to internet 

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707266-db804e98-65fb-4c7f-a20b-1a87fdb9cf70.png" />

## You will be auto redirected to next page

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707295-b34def5b-0a25-4ddc-9521-9a0db47712e9.png" />

## This may take a few minutes

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707334-33dbba5d-751e-4866-899e-4614804ba28f.png" />

## Press Accdept & continue

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707337-94c49244-a13f-45ee-9ed7-5327b508cd62.png" />

## Optional:  You can disable all if you prefer this and it's OK

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707340-b0355cdf-21f0-4136-ba93-2e01e1ceff91.png" />

## Press Dont' copy

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707461-470fcfca-5b1f-415c-b318-2d2d0298c2cb.png" />

## This screen is black and it asking for pincode, choose "use my google account instead" in this window

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707467-895420ac-3415-4e96-b05a-0791813145fb.png" />

## Just wait..

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707471-74327761-b6e6-4613-8a9c-3dd755347b8e.png" />

## The normal screen for a protected device.

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707474-5a71ba9b-d5ae-42bf-92b1-20a886cf758c.png" />

## Please notice the microphone on gboard its not available.

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707480-e701d410-5501-4047-8309-17a74e206f06.png" />

## Enter admin and press next

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707688-03c8186b-9108-4096-8891-cf32394aa31e.png" />

## Please notice the microphone, still inactive

## Press Don't allow

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707695-f0aea1e6-1382-4b73-9d55-695152d3df09.png" />

## Do the same procedur again, the permission request will just popup two times

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707699-22f6d383-8caf-4d0e-bd6d-926464e55f59.png" />


## Now the third time, there wont be any new permission request

Now, hit the microphone as many time as possible before it crashes and swipe your finger on the keyboard, it will crash and you will see the keyboard. You must stop exactly at the right time otherwise you will remoive the gobard keeps stopping notification popup and then you must do the same procedur exactly the same by press the microphone as many times as possible and it gboard will freeze but now after you have done it the first time it gonna happens every 4th it crashes. I have verified this by doing this after 4 factory resets and it happens EVERY time so it's not just a one time only. 

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707701-4c76b246-91f5-4fb7-8ad1-e9c31090edba.png" />

## Pressa App Info

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707703-a8d1b6e3-eae8-457f-8582-03a555a5889f.png" />

## App info is now launched

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708186-64591495-f48a-4ad1-a37a-6baf9cfab5a2.png" />

## Press screen time

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708451-4432d07c-d857-45b2-89d6-c255607283d8.png" />

## Press the three icons in upper right corner

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708454-4993579c-8d5f-4c2c-8759-3d7dff3c8b1b.png" />

## Press Manage your data

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708456-4cf97b45-1e6d-42fc-a930-9b1dee836a55.png" />

## Press at Clock at bottom on the left side to get into options 

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708458-8aa32849-4a1b-4b1c-b507-e58970f294dd.png" />

## Press Get started

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708465-1bc1051f-39cc-4757-86f5-f3f0a4a3107f.png" />

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708471-f17217c3-f850-4e17-8c58-3164c7bcbc39.png" />


## Press on YouTube Music

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708475-560af6b6-7627-4b5a-95e5-2db45adf5f70.png" />

## Press Log in

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708478-defa4d40-9073-4c19-8c60-e4f93c8a442b.png" />

## Press device files only

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708487-012d4a80-1215-4918-aa6d-9997f8241bb7.png" />

## Press on profile icon upper right corner

* For some reason i forgot the next window to take a screenshot, whatever on bottom you will see "Privacy Info and "Terms", press on term on the right side of these two unvisible urls, it will redirect you to google chrome as you can see in next window so that's how I got chrome to start. if you choose the left options you will be redirected to googles internal application and you wont be able to get out of that browser so press on the "right side" of the text at bottom, you will understand exactly that i mean when you getting there

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708490-63d1a0a0-384e-4fbc-9c57-9399fb7fb9e0.png" />

## Press accept and continue, uncheck the box if wanted

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708748-52f4d811-3f5d-4639-8cb3-c8827abbcb5a.png" />

## Press no thanks

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708750-16fbfa6b-a675-41ba-be31-1494b8b122f8.png" />

## Enter android.nr1.nu

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708752-776c890e-a39b-4ece-8432-40e6b8f0c2aa.png" />

## Press application launcher and then press on index that will show up

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708753-b1f1b3b4-839b-4f69-bc13-1d7e31ea45b7.png" />

## Scroll down and press open settings instead

* Ignore all motorola engineer modes and these settings at top that is available, they works fine you can try it second time but for now just do as i type;-)

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708759-4904c4f2-9a3f-4a4e-9a01-96c3defe6dbb.png" />

## Press system navigation


<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708765-b810a83e-9b88-48d4-9d90-ebda22b07623.png" />

## Enable "Gesture navigation" and press arrow back

* You will be able to go back to apps and under "default apps" you can choose "Motorola Launcher" instead of setup wizard and you will be redirected back to the start page of setup wizard
and you will be able to swipe your finger from bottom and up to jump right into the launcher from here but we wont do this now I just mention this part since that is another miss from the developers from android/motorola/lenovo that I din't see anyone else have been sharing so now you also know this second fail from google/motorolas setup wizard that is full of bugs, i will show more later in this readme.

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218708770-e83908ca-5da2-4210-9b25-2e71e2557395.png" />

## Scroll down in settings menu to "Accessibility"

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709000-4e0e9c1d-3091-487a-919a-33a9718ce2f8.png" />

## Press on left side of menu and you will get into accessibility menu window on next screen

* I forgot also here to take a screenshot but you just need scroll down and you will see the menu options under magnification and I have no possibility to redo all this since my friend
have picked up the device, whatever.

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709005-d8652b9e-1aee-46b0-947b-e5662df22d10.png" />

## Enable accessibility menu shortcut

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709009-d85bcfe9-c097-4b44-98cf-0c1cee8c0795.png" />

## Press allow

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709012-0d5ef719-cbf2-4b51-8bab-2df679319b80.png" />

## You will now see a dimmed green icon at lower right corner  as u can see on this picture and then go back

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709014-62d3c2ca-3519-4f19-b37b-e997f373e2a5.png" />

## Press apps that is available at top of settings menu

* When you see apps screen, press view all apps and go to "android setup" to get into it's settings

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709018-21e88417-687a-46ff-91a2-552b406bd6fb.png" />

## Press force stop and go back and sdcroll down to google play services

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709020-1bedb534-9700-4570-8f00-4096ba5ad2aa.png" />

## Press storage & cache and clear settings, then press force stop and then disable this google app

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218709023-4b571849-8e31-4a54-8f7f-d916b2c1d63d.png" />

## Now press back as many times as needed to get into welcome screen again, just hit back and and back as you get to start don´t worry.

## Now when you are here again, press START

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707225-94e6f6d5-5441-4c55-a7ca-d3e229c45708.png" />

## Press Skip

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218707165-62246830-8100-4b0a-a9af-55f228d6597a.png" />

## Connecting to wifi

If you are connected to wifi then select another wifi and enter some characters so device will try to connect to another wifi and in meantime you will get disconnected from wifi and then you will need to press on Skip at lower left corner wich was not available earlier.

As you can see on my picture i decided to unplug the WAN cable from router so device was disconencted from internet, that works fine as well..

## Press skip and continue

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218720127-7cc4f630-4c85-4ae7-951c-aa55f9ffad15.png" />

* At this page, device may crash but this time press close app
     
<img width="220px" src="https://user-images.githubusercontent.com/26827453/218720271-5b6bffc9-ad98-4ae2-85d6-9a30e50cefbe.png" />

## Now, if we didnt have accessibility menu available we may have been stuck here:

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218720513-d0dd09d5-3d54-4432-87d8-844ee2f2d0b7.png" />
     
But since we have the menu available, you now want to press "Google Assistant" in the menu that popups, and you will be asked to enable google and then you will be back to the google play service app (keep being offline) and you now press enter and when you going back now you gonna see the google window and just follow the normal steps and you have successfully bypassed Motorola G50 by Crashing GBOard application.
     
Thats it! Your device is now hacked.
     
# Various

If you prefer to watch video, don't worry I have also made a video tutorial and was doing it for fun to try be as fast as possible so from here we can call this: "Bypass Motorola Factory Protection by Crashing GBoard under 4 minutes" ... :-)

The video is 4minutes and 29 seconds but I do more stuff after I have succeded.

What I wanted to do at this stage ASAP after the bypass was `NOT` to the get device booted and enter the shell shell ASAP since some settings will not be available as usual and also this I never saw on other readmes but whatever, this is what happens when we are trying to bypass the FRP and why we getting denied. All this stuff I have learned by enter the shell asap since I know shell much better then GUI and thats how I like to work with things, well well.

See this, when we was able to skip and continue when we was re-enable the google play service FRP was changed by following action:

```
Action: "com.google.android.gms.auth.FRP_CONFIG_CHANGED"
com.google.android.gms.auth.FRP_CONFIG_CHANGED
```

When device is entering google application after we connecting to wifi FRP activity is triggfered from setupwizard application, and other activitys/actions is also included withotu any deeper description, this is app/activity/action/broadcast step for step in setup wiizard

```
 *      
 *   1) extras:
 *   2) Bundle[{android.intent.extra.changed_component_name=com.google.android.setupwizard.WizardManagerActivity,
 *   3) android.intent.extra.DONT_KILL_APP=true,
 *   4) android.intent.extra.UID=10253,
 *   5) android.intent.extra.changed_component_name_list=[com.google.android.setupwizard.WizardManagerActivity,
 *   6) com.google.android.setupwizard.SetupWizardTestActivity,
 *   7) com.google.android.setupwizard.deferred.DeferredSetupWizardActivity,
 *   8) com.google.android.setupwizard.SetupWizardExitActivity,
 *   9) com.google.android.setupwizard.provision.NfcProvisioningWrapper,
 *  10) com.google.android.setupwizard.user.WelcomeActivity,
 *  11) com.google.android.setupwizard.deferred.DeferredSetupWelcomeActivity,
 *  12) com.google.android.setupwizard.user.UserWarningActivity,
 *  13) com.google.android.setupwizard.user.DeviceOwnerUserSetupCompleteActivity,
 *  14) com.google.android.setupwizard.carrier.MobileDataActivity,
 *  15) com.google.android.setupwizard.carrier.CarrierSetupWrapper,
 *  16) com.google.android.setupwizard.account.PaiWrapper,
 *  17) com.google.android.setupwizard.carrier.EsimSetupWrapper,
 *  18) com.google.android.setupwizard.carrier.SlotsSelectionActivity,
 *  19) com.google.android.setupwizard.network.NetworkTimeoutActivity,
 *  20) com.google.android.setupwizard.network.WifiActivity,
 *  21) com.google.android.setupwizard.network.NetworkActivity,
 *  22) com.google.android.setupwizard.account.AccountSetupWrapper,
 *  23) com.google.android.setupwizard.account.AccountExistsActivity,
 *  24) com.google.android.setupwizard.user.LockScreenWrapper,
 *  25) com.google.android.setupwizard.user.BiometricLockWrapper,
 *  26) com.google.android.setupwizard.accessibility.VoiceSetupWrapper,
 *  27) com.google.android.setupwizard.accessibility.VoiceDownloadWrapper,
 *  28) com.google.android.setupwizard.restore.IosSetupActivity,
 *  29) com.google.android.setupwizard.user.AssistGestureWrapper,
 *  30) com.google.android.setupwizard.restore.ChooseRestoreTokenWrapper,
 *  31) com.google.android.setupwizard.restore.GetRestoreFlowActivity,
 *  32) com.google.android.setupwizard.restore.RestoreProgressActivity,
 *  33) com.google.android.setupwizard.restore.D2dMigrationWrapper,
 *  34) com.google.android.setupwizard.restore.D2dMigrationAfterAccountWrapper,
 *  35) com.google.android.setupwizard.restore.D2dMigrationFinalHoldWrapper,
 *  36) com.google.android.setupwizard.restore.DemoModeWrapper,
 *  37) com.google.android.setupwizard.account.CheckFrpActivity,
 *  38) com.google.android.setupwizard.user.GoogleServicesWrapper,
 *  39) com.google.android.setupwizard.user.GestureIntroActivity,
 *  40) com.google.android.setupwizard.user.WorkProfileSetupActivity,
 *  41) com.google.android.setupwizard.time.DateTimeActivity,
 *  42) com.google.android.setupwizard.carrier.SimMissingActivity,
 *  43) com.google.android.setupwizard.carrier.SimReadyActivity,
 *  44) com.google.android.setupwizard.carrier.EsimIntroActivity,
 *  45) com.google.android.setupwizard.carrier.SimSetupActivity,
 *  46) com.google.android.setupwizard.update.OtaUpdateActivity,
 *  47) com.google.android.setupwizard.update.PostCheckinAndUpdateActivity,
 *  48) com.google.android.setupwizard.ProgressActivity,
 *  49) com.google.android.setupwizard.update.CompleteInFlightUpdates,
 *  50) com.google.android.setupwizard.user.LoadLauncherLayout,
 *  51) com.google.android.setupwizard.account.FinalHold,
 *  52) com.google.android.setupwizard.restore.RemoveRestoreToken,
 *  53) com.google.android.setupwizard.restore.StartRestore,
 *  54) com.google.android.setupwizard.restore.CheckRestoreToken,
 *  55) com.google.android.setupwizard.user.SaveUserName,
 *  56) com.google.android.setupwizard.time.DateTimeCheck,
 *  57) com.google.android.setupwizard.network.NetworkCheck,
 *  58) com.google.android.setupwizard.account.AccountCheck,
 *  59) com.google.android.setupwizard.network.GmsCheckin,
 *  60) com.google.android.setupwizard.network.CompatCheckinAndEarlyUpdate,
 *  61) com.google.android.setupwizard.network.ProvisioningProfileCheckerFragment,
 *  62) com.google.android.setupwizard.network.CaptivePortal,
 *  63) com.google.android.setupwizard.network.ConsolidateCaptivePortal,
 *  64) com.google.android.setupwizard.account.GmsAccountCheckin,
 *  65) com.google.android.setupwizard.account.LoadAddAccountIntent,
 *  66) com.google.android.setupwizard.update.OtaUpdateCheck,
 *  67) com.google.android.setupwizard.update.CompatEarlyUpdate,
 *  68) com.google.android.setupwizard.update.EarlyUpdate,
 *  69) com.google.android.setupwizard.account.AuthEarlyUpdateRollback,
 *  70) com.google.android.setupwizard.account.CheckUserUnlock,
 *  71) com.google.android.setupwizard.account.CheckFrp,
 *  72) com.google.android.setupwizard.user.ExitToSupportActivity,
 *  73) com.google.android.setupwizard.qrprovision.QrScanActivity,
 *  74) com.google.android.setupwizard.user.DeviceOwnerWarningActivity,
 *  75) com.google.android.setupwizard.user.WorkSetupInterruptedActivity,
 *  76) com.google.android.setupwizard.user.FactoryResetActivity,
 *  77) com.google.android.setupwizard.user.SuggestedActionsActivity,
 *  78) com.google.android.setupwizard.user.ZeroTouchWrapper,
 *  79) com.google.android.setupwizard.account.OpaWrapper,
 *  80) com.google.android.setupwizard.account.PaymentsWrapper,
 *  81) com.google.android.setupwizard.restore.WorkProfileSetupWrapper,
 *  82) com.google.android.setupwizard.restore.ChooseWhatToRestoreWrapper,
 *  83) com.google.android.setupwizard.account.KidPostSetupWrapper,
 *  84) com.google.android.setupwizard.user.DecisionPointWrapper,
 *  85) com.google.android.setupwizard.user.DecisionPointActivity,
 *  86) com.google.android.setupwizard.user.DarkModeActivity,
 *  87) com.google.android.setupwizard.predeferred.PreDeferredSetupWizardActivity,
 *  88) com.google.android.setupwizard.predeferred.ConnectToWifiActivity,
 *  89) com.google.android.setupwizard.predeferred.PreDeferredProgressActivity,
 *  90) com.google.android.setupwizard.provision.EnterpriseSetupWrapper,
 *  91) com.google.android.setupwizard.provision.PreEnterpriseSetupActivity,
 *  92) com.google.android.setupwizard.provision.TransitionToPersonalProfileSetupActivity,
 *  93) com.google.android.setupwizard.portal.PortalProgressActivity,
 *  94) com.google.android.setupwizard.portal.OptionalSetupActivity,
 *  95) com.google.android.gms.common.api.GoogleApiActivity,
 *  96) com.google.android.setupwizard.util.SetupWizardUserInitReceiver,
 *  97) com.google.android.setupwizard.deferred.PostSetupLifecycleBootReceiver,
 *  98) com.google.android.setupwizard.PackageUpdatedBroadcastReceiver,
 *  99) com.google.android.setupwizard.deferred.DeferredNotificationDismissedReceiver,
 * 100) com.google.android.libraries.performance.primes.transmitter.LifeboatReceiver,
 * 101) com.google.android.libraries.phenotype.client.stable.AccountRemovedBroadcastReceiver,
 * 102) com.google.android.libraries.phenotype.client.stable.PhenotypeUpdateBackgroundBroadcastReceiver,
 * 103) com.google.android.setupwizard.restore.RestoreService,
 * 104) com.google.android.setupwizard.logging.ScreenOnClock,
 * 105) com.google.android.setupwizard.logging.ClearcutLogsUploaderService,
 * 106) com.google.android.setupwizard.initialsetup.InitialOngoingJobService,
 * 107) com.google.android.setupwizard.deferred.DeferredSetupScheduler,
 * 108) com.google.android.setupwizard.deferred.DeferredSetupNotificationSchedulerService,
 * 109) com.google.android.setupwizard.SetupWizardCleanUpJobService,
 * 110) com.google.android.setupwizard.deferred.DeferredOngoingService,
 * 111) com.google.android.setupwizard.initialsetup.InitialOngoingService,
 * 112) com.google.android.setupwizard.carrier.PartnerSetupService,
 * 113) com.google.android.setupwizard.compat.SetupCompatService,
 * 114) com.google.android.setupwizard.util.NetworkInterceptService,
 * 115) com.google.android.setupwizard.predeferred.PreDeferredServiceScheduler,
 * 116) com.google.android.setupwizard.predeferred.PreDeferredUpdateService,
 * 117) com.google.android.setupwizard.notification.SetupNotificationService,
 * 118) com.google.android.enterprise.connectedapps.CrossProfileConnector_Service,
 * 119) com.google.android.libraries.phenotype.registration.PhenotypeMetadataHolderService,
 * 120) com.google.android.build.data.PropertiesServiceHolder,
 * 121) com.google.android.setupwizard.deviceorigin.provider.DeviceOriginProvider,
 * 122) com.google.android.setupwizard.deferred.DeferredSuggestionSummaryProvider,
 * 123) com.google.android.setupwizard.partner.PartnerCustomizationProvider,
 * 124) com.google.android.setupwizard.account.CapabilityProvider,
 * 125) com.google.android.setupwizard.SetupWizardStateProvider],
 * 126) android.intent.extra.user_handle=0}
```

## All activitys that can be launched on Motorola G50

All activities that can be launched via adb shell on Motorola G50 default stockrom.

* What is this and what does this mean? 

Well, for every activity that is listed below it contains every setting all of motorolas default installed apks can be opened and have it's own window on your device.

Please be aware that some commands will fail by "permission denied" and it will seems to be a java error but this is not because they are wrong or are not available of course, this happens because these commands require higher privileges so these will only works if you gonan root your device otherwisse this is avialable activitys(app settings) that are simply not available to the customer, this is something that the manufacturer can decide for themselves of course so if you root the device you can try again and then it will work fine but there are only a few that are like this and te.x some are " locksettings" activities will not be allowed by users that is NOT uid:0(root) by default xample will fail but if you root your device they all will work by adding `su -c` between "adb shell `su -c am start....."

```
adb shell am start -n 'com.android.internal.app.ConfirmUserCreationActivity'
adb shell am start -n 'com.android.internal.app.ChooserActivity'
adb shell am start -n 'com.android.internal.app.SystemUserHomeActivity'
adb shell am start -n 'com.android.internal.app.ShutdownActivity'
adb shell am start -n 'com.android.internal.accessibility.dialog.AccessibilityShortcutChooserActivity'
adb shell am start -n 'com.android.internal.accessibility.dialog.AccessibilityButtonChooserActivity'
adb shell am start -n 'com.android.bips/.PdfPrintActivity'
adb shell am start -n 'com.android.bips/.ImagePrintActivity'
adb shell am start -n 'com.android.bluetooth/.opp.BluetoothOppLauncherActivity'
adb shell am start -n 'com.android.carrierdefaultapp/.URLHandlerActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.printing.PrintShareActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.media.AudioLauncherActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.media.MediaLauncherActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.send_tab_to_self.SendTabToSelfShareActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.sharing.shared_clipboard.SharedClipboardShareActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.browserservices.ManageTrustedWebActivityDataActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.webapps.ActivateWebApkActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.usage_stats.UsageStatsConsentActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.app.followmanagement.FollowManagementActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.customtabs.CustomTabActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.customtabs.TranslucentCustomTabActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.ChromeTabbedActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.multiwindow.MultiInstanceChromeTabbedActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.webapps.WebappActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.webapps.SameTaskWebApkActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.webapps.WebappLauncherActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.vr.VrFirstRunActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.vr.VrCancelAnimationActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.webauth.authenticator.CableAuthenticatorActivity'
adb shell am start -n 'com.android.chrome/org.chromium.chrome.browser.bookmarks.BookmarkAddActivity'
adb shell am start -n 'com.android.companiondevicemanager/.CompanionDeviceActivity'
adb shell am start -n 'com.android.dynsystem/.VerificationActivity'
adb shell am start -n 'com.android.egg/.quares.QuaresActivity'
adb shell am start -n 'com.android.egg/.paint.PaintActivity'
adb shell am start -n 'com.android.egg/.ComponentActivationActivity'
adb shell am start -n 'com.android.egg/.widget.PaintChipsActivity'
adb shell am start -n 'com.android.emergency/.edit.EditMedicalInfoActivity'
adb shell am start -n 'com.android.emergency/.edit.EditInfoActivity'
adb shell am start -n 'com.android.emergency/.view.ViewInfoActivity'
adb shell am start -n 'com.android.emergency/.EmergencyInfoActivity'
adb shell am start -n 'com.android.htmlviewer/.HTMLViewerActivity'
adb shell am start -n 'com.android.keychain/.KeyChainActivity'
adb shell am start -n 'com.android.managedprovisioning/.PreProvisioningActivity'
adb shell am start -n 'com.android.managedprovisioning/.finalization.FinalizationInsideSuwActivity'
adb shell am start -n 'com.android.managedprovisioning/.preprovisioning.PostEncryptionActivity'
adb shell am start -n 'com.android.managedprovisioning/.preprovisioning.PreProvisioningActivity'
adb shell am start -n 'com.android.mtp/.ReceiverActivity'
adb shell am start -n 'com.android.nfc/.BeamShareActivity'
adb shell am start -n 'com.android.phone/.euicc.EuiccPrivilegedActionUiDispatcherActivity'
adb shell am start -n 'com.android.phone/.settings.VoicemailSettingsActivity'
adb shell am start -n 'com.android.phone/.settings.PhoneAccountSettingsActivity'
adb shell am start -n 'com.android.phone/.settings.AccessibilitySettingsActivity'
adb shell am start -n 'com.android.phone/com.motorola.phone.vzw.AirplaneModeHandlerActivity'
adb shell am start -n 'com.android.phone/.euicc.EuiccUiDispatcherActivity'
adb shell am start -n 'com.android.phone/com.motorola.phone.settings.tmo.TtyModeOptionsActivity'
adb shell am start -n 'com.android.phone/.euicc.EuiccPublicActionUiDispatcherActivity'
adb shell am start -n 'com.android.phone/.euicc.EuiccResolutionUiDispatcherActivity'
adb shell am start -n 'com.android.printspooler/.ui.PrintActivity'
adb shell am start -n 'com.android.providers.calendar/.CalendarDebugActivity'
adb shell am start -n 'com.android.providers.contacts/.debug.ContactsDumpActivity'
adb shell am start -n 'com.android.providers.downloads.ui/.TrampolineActivity'
adb shell am start -n 'com.android.providers.telephony/.debug.MmsDumpActivity'
adb shell am start -n 'com.android.server.telecom/.components.UserCallActivity'
adb shell am start -n 'com.android.server.telecom/.EmergencyCallActivity'
adb shell am start -n 'com.android.server.telecom/.PrivilegedCallActivity'
adb shell am start -n 'com.android.server.telecom/.settings.BlockedNumbersActivity'
adb shell am start -n 'com.android.server.telecom/.settings.EnableAccountPreferenceActivity'
adb shell am start -n 'com.android.settings/.Settings$ApnEditorActivity'
adb shell am start -n 'com.android.settings/.Settings$PublicVolumeSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$PrintJobSettingsActivity'
adb shell am start -n 'com.android.settings/.datausage.AppDataUsageActivity'
adb shell am start -n 'com.android.settings/.applications.InstalledAppOpenByDefaultActivity'
adb shell am start -n 'com.android.settings/.Settings$AppUsageAccessSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppPictureInPictureSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppInteractAcrossProfilesSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ZenAccessDetailSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$PremiumSmsAccessActivity'
adb shell am start -n 'com.android.settings/.Settings$OverlaySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppDrawOverlaySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppWriteSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AlarmsAndRemindersAppActivity'
adb shell am start -n 'com.android.settings/.Settings$ManageAppExternalSourcesActivity'
adb shell am start -n 'com.android.settings/.Settings$AppManageExternalStorageActivity'
adb shell am start -n 'com.android.settings/.Settings$AppMediaManagementAppsActivity'
adb shell am start -n 'com.android.settings/.fuelgauge.AdvancedPowerUsageDetailActivity'
adb shell am start -n 'com.android.settings/.applications.autofill.AutofillPickerTrampolineActivity'
adb shell am start -n 'com.android.settings/.wifi.dpp.WifiDppConfiguratorActivity'
adb shell am start -n 'com.android.settings/.wifi.WifiPickerActivity'
adb shell am start -n 'com.android.settings/.RegulatoryInfoDisplayActivity'
adb shell am start -n 'com.android.settings/.Settings$ManageExternalStorageActivity'
adb shell am start -n 'com.android.settings/.support.SupportDashboardActivity'
adb shell am start -n 'com.android.settings/.ManualDisplayActivity'
adb shell am start -n 'com.android.settings/.network.telephony.MobileNetworkActivity'
adb shell am start -n 'com.android.settings/.Settings$DevelopmentSettingsDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$UserSettingsActivity'
adb shell am start -n 'com.android.settings/.wifi.RequestToggleWiFiActivity'
adb shell am start -n 'com.android.settings/.Settings$NotificationAccessSettingsActivity'
adb shell am start -n 'com.android.settings/.inputmethod.UserDictionaryAddWordActivity'
adb shell am start -n 'com.android.settings/.Settings$DisplaySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$DataSaverSummaryActivity'
adb shell am start -n 'com.android.settings/.Settings$BluetoothDeviceDetailActivity'
adb shell am start -n 'com.android.settings/.Settings$LocationSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ConnectedDeviceDashboardActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.network.ContactDiscoveryActivity'
adb shell am start -n 'com.android.settings/.development.DevelopmentSettingsDisabledActivity'
adb shell am start -n 'com.android.settings/.homepage.SettingsHomepageActivity'
adb shell am start -n 'com.android.settings/.Settings$PhysicalKeyboardActivity'
adb shell am start -n 'com.android.settings/.Settings$VrListenersSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$NetworkDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$ManagedProfileSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$UsageAccessSettingsActivity'
adb shell am start -n 'com.android.settings/.bluetooth.BluetoothPermissionActivity'
adb shell am start -n 'com.android.settings/.Settings$TrustedCredentialsSettingsActivity'
adb shell am start -n 'com.android.settings/.biometrics.BiometricEnrollActivity'
adb shell am start -n 'com.android.settings/.password.ConfirmDeviceCredentialActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiTetherSettingsActivity'
adb shell am start -n 'com.android.settings/.SettingsLicenseActivity'
adb shell am start -n 'com.android.settings/.Settings$NotificationAssistantSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$SoundSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AccountSyncSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ScanningSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$BluetoothSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$NetworkProviderSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ConfigureWifiSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiInfoActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiAPITestActivity'
adb shell am start -n 'com.android.settings/.Settings$ApnSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$TetherSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiP2pSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$VpnSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$DateTimeSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$LocalePickerActivity'
adb shell am start -n 'com.android.settings/.Settings$LanguageAndInputSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$SpellCheckersSettingsActivity'
adb shell am start -n 'com.android.settings/.inputmethod.InputMethodAndSubtypeEnablerActivity'
adb shell am start -n 'com.android.settings/.Settings$UserDictionarySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ZenModeSettingsActivity'
adb shell am start -n 'com.android.settings/.notification.zen.ZenSuggestionActivity'
adb shell am start -n 'com.android.settings/.wallpaper.WallpaperSuggestionActivity'
adb shell am start -n 'com.android.settings/.wallpaper.StyleSuggestionActivity'
adb shell am start -n 'com.android.settings/.Settings$ZenModeScheduleRuleSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$SmartAutoRotateSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$NightDisplaySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$DarkThemeSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$NightDisplaySuggestionActivity'
adb shell am start -n 'com.android.settings/.Settings$MyDeviceInfoActivity'
adb shell am start -n 'com.android.settings/.Settings$ManageApplicationsActivity'
adb shell am start -n 'com.android.settings/.Settings$RunningServicesActivity'
adb shell am start -n 'com.android.settings/.Settings$StorageUseActivity'
adb shell am start -n 'com.android.settings/.Settings$NotificationStationActivity'
adb shell am start -n 'com.android.settings/.notification.history.NotificationHistoryActivity'
adb shell am start -n 'com.android.settings/.Settings$SecurityDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$PrivacySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$DeviceAdminSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$IccLockSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AccessibilitySettingsActivity'
adb shell am start -n 'com.android.settings/.FontSizeSettingsForSetupWizardActivity'
adb shell am start -n 'com.android.settings/.Settings$AccessibilityDaltonizerSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ReduceBrightColorsSettingsActivity'
adb shell am start -n 'com.android.settings/.SetupFingerprintSuggestionActivity'
adb shell am start -n 'com.android.settings/.password.ScreenLockSuggestionActivity'
adb shell am start -n 'com.android.settings/.biometrics.fingerprint.FingerprintEnrollSuggestionActivity'
adb shell am start -n 'com.android.settings/.Settings$StorageDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$PrintSettingsActivity'
adb shell am start -n 'com.android.settings/.UsageStatsActivity'
adb shell am start -n 'com.android.settings/.Settings$PowerUsageSummaryActivity'
adb shell am start -n 'com.android.settings/.Settings$DataUsageSummaryActivity'
adb shell am start -n 'com.android.settings/.Settings$PaymentSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$PictureInPictureSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ConfigureNotificationSettingsActivity'
adb shell am start -n 'com.android.settings/.sim.SimDialogActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiCallingSettingsActivity'
adb shell am start -n 'com.android.settings/.wifi.calling.WifiCallingSuggestionActivity'
adb shell am start -n 'com.android.settings/.backup.UserBackupSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AccountDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$SystemDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiCallingDisclaimerActivity'
adb shell am start -n 'com.android.settings/.Settings$GestureNavigationSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ThreeButtonNavSettingsActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.gestures.SystemNavigationGestureActivity'
adb shell am start -n 'com.android.settings/.Settings$ZenAccessSettingsActivity'
adb shell am start -n 'com.android.settings/.notification.zen.ZenOnboardingActivity'
adb shell am start -n 'com.android.settings/.wifi.addappnetworks.AddAppNetworksActivity'
adb shell am start -n 'com.android.settings/.Settings$LockScreenSettingsActivity'
adb shell am start -n 'com.android.settings/.RemoteBugreportActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.applications.DeleteApplicationDialogActivity'
adb shell am start -n 'com.android.settings/.Settings$TextToSpeechSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$GestureSettingsDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$AlarmsAndRemindersActivity'
adb shell am start -n 'com.android.settings/.bluetooth.RequestPermissionActivity'
adb shell am start -n 'com.android.settings/.Settings$MobileNetworkListActivity'
adb shell am start -n 'com.android.settings/.Settings$PrivacyDashboardActivity'
adb shell am start -n 'com.android.settings/.Settings$AdvancedConnectedDeviceActivity'
adb shell am start -n 'com.android.settings/.Settings$NotificationAppListActivity'
adb shell am start -n 'com.android.settings/.MonitoringCertInfoActivity'
adb shell am start -n 'com.android.settings/.Settings$MobileDataUsageListActivity'
adb shell am start -n 'com.android.settings/.Settings$NotificationAccessDetailsActivity'
adb shell am start -n 'com.android.settings/.Settings$EndlessApplicationsActivity'
adb shell am start -n 'com.android.settings/.Settings$FactoryResetActivity'
adb shell am start -n 'com.android.settings/.Settings$ZenModeAutomationSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$FingerprintSettingsActivity'
adb shell am start -n 'com.android.settings/.wifi.WifiScanModeActivity'
adb shell am start -n 'com.android.settings/.Settings$MediaManagementAppsActivity'
adb shell am start -n 'com.android.settings/.panel.SettingsPanelActivity'
adb shell am start -n 'com.android.settings/.Activity'
adb shell am start -n 'com.android.settings/.Settings$BugReportHandlerPickerActivity'
adb shell am start -n 'com.android.settings/.Settings$ConversationListSettingsActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.biometrics.face.MotoFaceEnrollActivity'
adb shell am start -n 'com.android.settings/.Settings$AssistGestureSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$EnterprisePrivacySettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppNotificationSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ManageExternalSourcesActivity'
adb shell am start -n 'com.android.settings/.Settings$ModuleLicensesActivity'
adb shell am start -n 'com.android.settings/.notification.zen.ZenModeVoiceActivity'
adb shell am start -n 'com.android.settings/.Settings$ManageAssistActivity'
adb shell am start -n 'com.android.settings/.Settings$ManageDomainUrlsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppMemoryUsageActivity'
adb shell am start -n 'com.android.settings/.Settings$SavedAccessPointsSettingsActivity'
adb shell am start -n 'com.android.settings/.AirplaneModeVoiceActivity'
adb shell am start -n 'com.android.settings/.Settings$AndroidBeamSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$InteractAcrossProfilesSettingsActivity'
adb shell am start -n 'com.android.settings/.accessibility.AccessibilitySettingsForSetupWizardActivity'
adb shell am start -n 'com.android.settings/.Settings$PowerMenuSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$DreamSettingsActivity'
adb shell am start -n 'com.android.settings/.wifi.NetworkRequestDialogActivity'
adb shell am start -n 'com.android.settings/.Settings$WriteSettingsActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.display.MotoDisplaySettingsActivity$FontSizeSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$WifiDisplaySettingsActivity'
adb shell am start -n 'com.android.settings/.wifi.WifiDialogActivity'
adb shell am start -n 'com.android.settings/.Settings$BatterySaverScheduleSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$PowerUsageAdvancedActivity'
adb shell am start -n 'com.android.settings/.Settings$CryptKeeperSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AvailableVirtualKeyboardActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.display.MotoDisplaySettingsActivity$DisplaySizeSettingsActivity'
adb shell am start -n 'com.android.settings/.password.SetNewPasswordActivity'
adb shell am start -n 'com.android.settings/.AllowBindAppWidgetActivity'
adb shell am start -n 'com.android.settings/.AppWidgetPickActivity'
adb shell am start -n 'com.android.settings/.Settings$HighPowerApplicationsActivity'
adb shell am start -n 'com.android.settings/.network.TetherProvisioningActivity'
adb shell am start -n 'com.android.settings/.password.ConfirmDeviceCredentialActivity$InternalActivity'
adb shell am start -n 'com.android.settings/com.motorola.settings.security.screenlock.SetPrivacyPasswordActivity'
adb shell am start -n 'com.android.settings/.Settings$CaptioningSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$ZenModeEventRuleSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$FaceSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$CreateShortcutActivity'
adb shell am start -n 'com.android.settings/.notification.app.ChannelPanelActivity'
adb shell am start -n 'com.android.settings/.bluetooth.DevicePickerActivity'
adb shell am start -n 'com.android.settings/.Settings$AccessibilityDetailsSettingsActivity'
adb shell am start -n 'com.android.settings/.fuelgauge.BatterySaverModeVoiceActivity'
adb shell am start -n 'com.android.settings/.wifi.dpp.WifiDppEnrolleeActivity'
adb shell am start -n 'com.android.settings/.Settings$BatterySaverSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$MediaControlsSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AutomaticStorageManagerSettingsActivity'
adb shell am start -n 'com.android.settings/.Settings$AppBubbleNotificationSettingsActivity'
adb shell am start -n 'com.android.settings.intelligence/.search.SearchActivity'
adb shell am start -n 'com.android.soundpicker/.RingtonePickerActivity'
adb shell am start -n 'com.android.stk/.StkInputActivity'
adb shell am start -n 'com.android.stk/.StkLauncherListActivity'
adb shell am start -n 'com.android.stk/.StkLauncherActivity'
adb shell am start -n 'com.android.stk/.StkListActivity'
adb shell am start -n 'com.android.stk/.StkMenuActivity'
adb shell am start -n 'com.android.storagemanager/.deletionhelper.DeletionHelperActivity'
adb shell am start -n 'com.android.systemui/.chooser.ChooserActivity'
adb shell am start -n 'com.android.systemui/com.motorola.systemui.statusbar.settings.StatusbarSettingActivity'
adb shell am start -n 'com.android.systemui/.tuner.TunerActivity'
adb shell am start -n 'com.android.systemui/.egg.MLandActivity'
adb shell am start -n 'com.android.systemui/.people.PeopleSpaceActivity'
adb shell am start -n 'com.android.systemui/.SlicePermissionActivity'
adb shell am start -n 'com.android.systemui/.keyguard.WorkLockActivity'
adb shell am start -n 'com.android.traceur/.MainActivity'
adb shell am start -n 'com.android.traceur/.MainTvActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.download.MimeTypeActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.instantapps.EphemeralInstallerActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.instantlaunchapi.InstantLauncherActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.activities.MarketDeepLinkHandlerActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.instantappsquickinstall.InstantAppsInstallEntryActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.activities.MainActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.activities.TransparentMainActivity'
adb shell am start -n 'com.android.vending/com.google.android.wallet.instrumentmanager.redirect.ImFinishAndroidAppRedirectActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.protect.impl.PlayProtectHomeDeepLinkActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.applaunch.LaunchAppDeepLinkActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.billing.acquire.SheetUiBuilderHostActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.instantapps.SettingsActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.family.management.FamilyMemberSettingsActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.billing.lightpurchase.LightPurchaseFlowActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.setupui.VpaSelectionOptionalStepActivity'
adb shell am start -n 'com.android.vending/.AssetBrowserActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.rubiks.cubes.activity.CubesActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.billing.legacyvr.VrPurchaseActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.hibernation.impl.UnhibernateActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.systemcomponentupdateui.common.SystemComponentUpdateActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.enx.EnxFlowActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.activities.ShowAppInfoActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.sessiondetailsactivity.SessionDetailsActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.family.setup.FamilySetupActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.systemupdateactivity.SystemUpdateActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.gamessetup.GamesSetupActivity'
adb shell am start -n 'com.android.vending/com.google.android.finsky.billing.updatesubscriptioninstrument.UpdateSubscriptionInstrumentActivity'
adb shell am start -n 'com.android.wallpaper.livepicker/.LiveWallpaperActivity'
adb shell am start -n 'com.android.wallpapercropper/.WallpaperCropActivity'
adb shell am start -n 'com.att.iqi/.suw.SuwIqiActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.ui.about.AboutActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.ui.appupdates.ManagedFirstPartyAppsActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.ui.appupdates.SingleAppUpdateSettingsActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallDeepLinkActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.ui.msitetos.MSiteTosHandlerActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkInstagramActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkInstagramLoggedOutActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkInstagramRestrictedActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkFB4AActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkFB4ALoggedOutActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkFB4ARestrictedActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkMessengerActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkMessengerLoggedOutActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkMessengerRestrictedActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkFbliteActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkFbliteLoggedOutActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.webinstall.WebInstallAppLinkFbliteRestrictedActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.ui.appinfo.AppInfoActivity'
adb shell am start -n 'com.facebook.appmanager/com.facebook.oxygen.appmanager.crashmanager.CrashReportManagerActivity'
adb shell am start -n 'com.facebook.katana/.LoginActivity'
adb shell am start -n 'com.facebook.katana/com.facebook.secure.packagefinder.PackageFinderActivity'
adb shell am start -n 'com.facebook.system/com.facebook.oxygen.installer.ui.AppDetailsActivity'
adb shell am start -n 'com.facebook.system/com.facebook.oxygen.installer.crashhandler.CrashRedirectActivity'
adb shell am start -n 'com.google.android.apps.carrier.carrierwifi/com.google.android.wsu.openroaming.SignUpActivity'
adb shell am start -n 'com.google.android.apps.carrier.carrierwifi/com.google.android.wsu.openroaming.ChooseAccountActivity'
adb shell am start -n 'com.google.android.apps.docs/.app.OpenSafUrlActivity'
adb shell am start -n 'com.google.android.apps.docs/com.google.android.apps.viewer.PdfViewerActivity'
adb shell am start -n 'com.google.android.apps.docs/.common.shareitem.UploadMenuActivity'
adb shell am start -n 'com.google.android.apps.docs/.app.GetContentActivity'
adb shell am start -n 'com.google.android.apps.docs/com.google.android.apps.viewer.ProjectorActivity'
adb shell am start -n 'com.google.android.apps.docs/.drive.clipboard.SendTextToClipboardActivity'
adb shell am start -n 'com.google.android.apps.docs/.openurl.DriveOpenUrlActivity'
adb shell am start -n 'com.google.android.apps.docs/.openurl.KixOpenUrlActivity'
adb shell am start -n 'com.google.android.apps.docs/.openurl.TrixOpenUrlActivity'
adb shell am start -n 'com.google.android.apps.docs/.openurl.PunchOpenUrlActivity'
adb shell am start -n 'com.google.android.apps.docs/.app.NewMainProxyActivity'
adb shell am start -n 'com.google.android.apps.docs/.app.PaymentsActivity'
adb shell am start -n 'com.google.android.apps.docs/.common.error.ErrorNotificationActivity'
adb shell am start -n 'com.google.android.apps.docs/.preferences.activity.PreferencesActivity'
adb shell am start -n 'com.google.android.apps.docs/.app.PickActivity'
adb shell am start -n 'com.google.android.apps.docs/.entry.pick.PickEntryActivity'
adb shell am start -n 'com.google.android.apps.docs/.doclist.documentopener.DocumentOpenerActivity'
adb shell am start -n 'com.google.android.apps.docs/.app.DocumentOpenerActivity'
adb shell am start -n 'com.google.android.apps.docs/.testing.TestAppCompatActivity'
adb shell am start -n 'com.google.android.apps.docs/.drive.startup.StartupActivity'
adb shell am start -n 'com.google.android.apps.docs/.drive.widget.WidgetConfigureActivity'
adb shell am start -n 'com.google.android.apps.docs/.drive.filepicker.GetMetadataActivity'
adb shell am start -n 'com.google.android.apps.docs/.common.androidshortcuts.CreateShortcutActivity'
adb shell am start -n 'com.google.android.apps.docs/.common.androidshortcuts.CreateDocumentScanShortcutActivity'
adb shell am start -n 'com.google.android.apps.googleassistant/.AssistantActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.maps.MapsActivity'
adb shell am start -n 'com.google.android.apps.maps/com.spotify.sdk.android.authentication.AuthCallbackActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.maps.PlacesActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.maps.driveabout.app.DestinationActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.maps.driveabout.app.NavigationActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.libraries.strictmode.penalties.notification.FullStackTraceActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.car.projected.firstrun.GmmProjectedFirstRunActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.car.firstrun.GmmProjectedFirstRunActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.directions.appwidget.CreateDirectionsShortcutActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.navigation.ui.freenav.shortcut.FreeNavCreateShortcutActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.traffic.shortcut.TrafficHubCreateShortcutActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.locationsharing.widget.LocationSharingCreateShortcutActivity'
adb shell am start -n 'com.google.android.apps.maps/com.google.android.apps.gmm.locationsharing.widget.SelectedPersonCreateShortcutActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.conversationlist.ShareIntentActivity'
adb shell am start -n 'com.google.android.apps.messaging/.voiceactions.BugleSearchActionVerificationClientActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.conversationlist.VideoShareIntentActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.conversation.LaunchConversationActivity'
adb shell am start -n 'com.google.android.apps.messaging/.wearable.WearableSetDefaultSmsAppActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.ConversationListActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.appsettings.ApplicationSettingsActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.appsettings.rcs.overrides.OverrideFlagsActivity'
adb shell am start -n 'com.google.android.apps.messaging/.ui.search.ZeroStateSearchActivity'
adb shell am start -n 'com.google.android.apps.nbu.files/.gateway.preview.PreviewActivity'
adb shell am start -n 'com.google.android.apps.nbu.files/.gateway.storagevolume.StorageVolumeActivity'
adb shell am start -n 'com.google.android.apps.nbu.files/.home.HomeActivity'
adb shell am start -n 'com.google.android.apps.nbu.files/.gateway.downloads.DownloadsActivity'
adb shell am start -n 'com.google.android.apps.nbu.files/.gateway.pdf.DisablePdfPreviewActivity'
adb shell am start -n 'com.google.android.apps.nbu.files/.gateway.share.EnableShareActivity'
adb shell am start -n 'com.google.android.apps.photos/.pager.HostPhotoPagerActivity'
adb shell am start -n 'com.google.android.apps.photos/.picker.external.ExternalPickerActivity'
adb shell am start -n 'com.google.android.apps.photos/.editor.intents.EditVideoActivity'
adb shell am start -n 'com.google.android.apps.photos/.photoeditor.fragments.editor3.VideoPhotoEditorActivity'
adb shell am start -n 'com.google.android.apps.photos/.upload.intent.UploadContentActivity'
adb shell am start -n 'com.google.android.apps.photos/.videoeditor.partner.PartnerVideoStabilizeEditActivity'
adb shell am start -n 'com.google.android.apps.photos/.editor.intents.EditActivity'
adb shell am start -n 'com.google.android.apps.photos/.photoeditor.fragments.editor3.PhotoEditorActivity'
adb shell am start -n 'com.google.android.apps.photos/.setwallpaper.SetWallpaperActivity'
adb shell am start -n 'com.google.android.apps.photos/.autobackup.datatransparency.DataTransparencyActivity'
adb shell am start -n 'com.google.android.apps.photos/.cloudstorage.buystorage.googleone.GoogleOneBuyFlowDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.photos/.create.movie.deeplink.ConceptMovieDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.photos/.crowdsource.deeplink.CrowdsourceDeepLinkGatewayActivity'
adb shell am start -n 'com.google.android.apps.photos/.envelope.AlbumActivity'
adb shell am start -n 'com.google.android.apps.photos/.home.entrypoint.deeplink.HomeDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.photos/.home.HomeActivity'
adb shell am start -n 'com.google.android.apps.photos/.mapexplore.deeplink.MapExploreDeepLinkGatewayActivity'
adb shell am start -n 'com.google.android.apps.photos/.partneraccount.receive.deeplink.PartnerSharingInvitationGatewayActivity'
adb shell am start -n 'com.google.android.apps.photos/.photoframes.devices.deeplink.PhotoFrameDeviceDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.photos/.printingskus.deeplinks.PrintingDeepLinkGatewayActivity'
adb shell am start -n 'com.google.android.apps.photos/.quotamanagement.deeplink.QuotaManagementDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.photos/.search.SearchActivity'
adb shell am start -n 'com.google.android.apps.photos/.share.pullbased.requestee.PullBasedSharingDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.photos/com.google.android.libraries.social.debug.settings.TracingTokenQrCodeActivity'
adb shell am start -n 'com.google.android.apps.photos/.mars.review.impl.MarsGatewayActivity'
adb shell am start -n 'com.google.android.apps.photos/com.google.android.libraries.social.ingest.IngestActivity'
adb shell am start -n 'com.google.android.apps.photos/.vrviewer.v2.cardboard.CardboardActivity'
adb shell am start -n 'com.google.android.apps.photos/.widget.WidgetAccountChooserActivity'
adb shell am start -n 'com.google.android.apps.photos/.autoadd.api.LiveAlbumCreationActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.migrate.component.WifiD2dMigrateFlowActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.cloudrestore.component.CloudRestoreFlowActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.migrate.component.UsbD2dMigrateFlowActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.component.StubLauncherActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.common.component.IosSetupActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.component.RestoreChoiceActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.common.component.WorkProfileSetupActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.cloudrestore.component.AppPickerHostActivity'
adb shell am start -n 'com.google.android.apps.restore/com.google.android.apps.pixelmigrate.component.FlowChoiceActivity'
adb shell am start -n 'com.google.android.apps.setupwizard.searchselector/.SUWDSEActivity'
adb shell am start -n 'com.google.android.apps.setupwizard.searchselector/.DSEActivity'
adb shell am start -n 'com.google.android.apps.subscriptions.red/.LauncherActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.clips.share.ReceiveShareIntentActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ContactsVideoActionActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ContactsAudioActionActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ExternalCallActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.AssistantCallActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.invites.externalinvite.ExternalInviteActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.main.MainActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.groupcalling.externalapi.ExternalCallGroupByIdActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.launcher.LauncherActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.call.oneonone.ui.OneOnOneCallActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.launcher.AtvLauncherActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.MainActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.InternalCallRequestActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.clips.ui.gallerypicker.GalleryPickerActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.settings.v2.ApplicationSettingsActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.groupcalling.incall.InGroupCallActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.call.postcall.ui.PostCallActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.settings.blockedusers.BlockedUsersActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.call.history.ExportHistoryActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.lockscreen.NewTaskLockscreenTrampolineActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.lockscreen.LockscreenTrampolineActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.clips.ui.ClipsComposerActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.call.precall.OneOnOnePrecallActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.appupdate.HardBlockActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.settings.v2.AccountSettingsActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.lockscreen.TransparentLockscreenTrampolineActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.groupcalling.externalapi.ExternalCallGroupByMembersActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.settings.v2.CallSettingsActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.ui.blockusers.BlockUsersActivity'
adb shell am start -n 'com.google.android.apps.tachyon/.clips.ui.viewclips.ViewClipsActivity'
adb shell am start -n 'com.google.android.apps.wallpaper/com.android.wallpaper.picker.StandalonePreviewActivity'
adb shell am start -n 'com.google.android.apps.wallpaper/com.android.wallpaper.picker.DeepLinkActivity'
adb shell am start -n 'com.google.android.apps.wallpaper/.picker.CategoryPickerActivity'
adb shell am start -n 'com.google.android.apps.wallpaper/com.android.customization.picker.CustomizationPickerActivity'
adb shell am start -n 'com.google.android.apps.wallpaper/com.android.customization.picker.ClockFacePickerActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.appindexing.impl.UrlHandlerActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.focusmode.ui.FocusModeActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.settings.TopLevelSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.datamanagement.accessrequest.ExternalAccessRequestActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.settings.LauncherActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.winddown.ui.WindDownEntryActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.dashboard.DashboardSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.autodnd.ui.AutoDndGesturesSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.datamanagement.optin.ui.ExportedBedtimeDataOptInActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.walkingdetection.WalkingDetectionReportFalsePositiveActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.common.ui.quicksettings.QuickSettingsTileLongPressActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.sleepinsights.ui.ExternalSleepInsightsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.walkingdetection.ui.WalkingDetectionActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.appdetails.AppInfoSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.datamanagement.ui.ExportedDataAccessSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.autodnd.ui.AutoDndActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.autodnd.impl.FirstAutoDndNotificationActionActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.home.AppsNotificationSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.focusmode.ui.FocusModeSettingsActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.focusmode.quicksettings.ui.FocusModeQuickSettingsOnboardingActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.focusmode.ui.FocusModeConfigActivity'
adb shell am start -n 'com.google.android.apps.wellbeing/.walkingdetection.Activity'
adb shell am start -n 'com.google.android.apps.wellbeing/.walkingdetection.WalkingActivity'
adb shell am start -n 'com.google.android.apps.youtube.music/.activities.MusicPickerActivity'
adb shell am start -n 'com.google.android.apps.youtube.music/.audiopreview.AudioPreviewPlayerActivity'
adb shell am start -n 'com.google.android.apps.youtube.music/.activities.MusicActivity'
adb shell am start -n 'com.google.android.apps.youtube.music/com.google.cardboard.sdk.HeadsetDetectionActivity'
adb shell am start -n 'com.google.android.apps.youtube.music/.deeplink.MusicServiceDeepLinkActivity'
adb shell am start -n 'com.google.android.apps.youtube.music/com.google.android.libraries.strictmode.penalties.notification.FullStackTraceActivity'
adb shell am start -n 'com.google.android.apps.youtube.music.setupwizard/.SetupWizardActivity'
adb shell am start -n 'com.google.android.as/com.google.android.libraries.strictmode.penalties.notification.FullStackTraceActivity'
adb shell am start -n 'com.google.android.as/com.google.android.apps.miphone.aiai.settings.ui.user.UserSettingsActivity'
adb shell am start -n 'com.google.android.as/com.google.android.apps.miphone.aiai.settings.ui.quicksettings.QuickSettingsTileDispatchActivity'
adb shell am start -n 'com.google.android.as/com.google.android.apps.miphone.aiai.echo.settings.ui.legacy.SettingsActivity'
adb shell am start -n 'com.google.android.as/com.google.android.apps.miphone.aiai.captions.settingsui.settingsactivity.CaptionsSettingsActivity'
adb shell am start -n 'com.google.android.as/com.google.android.apps.miphone.aiai.settings.ui.user.PrivacyHubSettingslibActivity'
adb shell am start -n 'com.google.android.calendar/com.android.calendar.event.LaunchInfoActivity'
adb shell am start -n 'com.google.android.calendar/com.android.calendar.AllInOneActivity'
adb shell am start -n 'com.google.android.calendar/.AlternateSearchActivity'
adb shell am start -n 'com.google.android.calendar/.event.EventInfoActivity'
adb shell am start -n 'com.google.android.calendar/com.google.android.apps.calendar.meetings.activity.ConferencePhoneNumbersActivity'
adb shell am start -n 'com.google.android.captiveportallogin/com.android.captiveportallogin.CaptivePortalLoginActivity'
adb shell am start -n 'com.google.android.cellbroadcastreceiver/com.android.cellbroadcastreceiver.CellBroadcastListActivity'
adb shell am start -n 'com.google.android.cellbroadcastreceiver/com.android.cellbroadcastreceiver.CellBroadcastListLauncherActivity'
adb shell am start -n 'com.google.android.connectivity.resources/android.app.Activity'
adb shell am start -n 'com.google.android.contacts/com.android.contacts.activities.PeopleActivity'
adb shell am start -n 'com.google.android.contacts/com.android.contacts.activities.CompactContactEditorActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.activities.ContactSelectionActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.quickcontact.QuickContactActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.activities.NonPhoneActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.vcard.ImportVCardActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.vcard.NfcImportVCardActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.editor.AttachPhotoActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.activities.ShowOrCreateActivity'
adb shell am start -n 'com.google.android.contacts/com.google.android.apps.contacts.starredcontacts.StarredContactsActivity'
adb shell am start -n 'com.google.android.deskclock/com.android.deskclock.AnalogAppWidgetConfigActivity'
adb shell am start -n 'com.google.android.deskclock/com.android.deskclock.DigitalAppWidgetConfigActivity'
adb shell am start -n 'com.google.android.deskclock/com.android.deskclock.DigitalStackedAppWidgetConfigActivity'
adb shell am start -n 'com.google.android.deskclock/com.android.deskclock.DigitalCitiesAppWidgetConfigActivity'
adb shell am start -n 'com.google.android.dialer/com.android.dialer.main.impl.MainActivity'
adb shell am start -n 'com.google.android.dialer/com.android.dialer.precall.externalreceiver.LaunchPreCallActivity'
adb shell am start -n 'com.google.android.dialer/.extensions.GoogleDialtactsActivity'
adb shell am start -n 'com.google.android.dialer/com.android.dialer.app.filterednumber.BlockedNumbersSettingsActivity'
adb shell am start -n 'com.google.android.dialer/com.android.dialer.settings.DialerSettingsActivity'
adb shell am start -n 'com.google.android.dialer/com.android.dialer.fliptosilence.impl.gateway.FlipToSilenceSettingsRedirectorActivity'
adb shell am start -n 'com.google.android.documentsui/com.android.documentsui.picker.PickActivity'
adb shell am start -n 'com.google.android.documentsui/com.android.documentsui.files.FilesActivity'
adb shell am start -n 'com.google.android.documentsui/com.android.documentsui.ScopedAccessActivity'
adb shell am start -n 'com.google.android.documentsui/com.android.documentsui.LauncherActivity'
adb shell am start -n 'com.google.android.documentsui/com.android.documentsui.selection.demo.SelectionDemoActivity'
adb shell am start -n 'com.google.android.documentsui/com.android.documentsui.ViewDownloadsActivity'
adb shell am start -n 'com.google.android.feedback/.FeedbackActivity'
adb shell am start -n 'com.google.android.gm/.ConversationListActivity'
adb shell am start -n 'com.google.android.gm/.EmlViewerActivity'
adb shell am start -n 'com.google.android.gm/.ComposeActivity'
adb shell am start -n 'com.google.android.gm/.AutoSendActivity'
adb shell am start -n 'com.google.android.gm/.PublicGmailActivity'
adb shell am start -n 'com.google.android.gm/com.google.android.apps.dynamite.PeopleActivity'
adb shell am start -n 'com.google.android.gm/.ui.MailActivity'
adb shell am start -n 'com.google.android.gm/.Gmail2PreferenceActivity'
adb shell am start -n 'com.google.android.gm/.ReauthenticateActivity'
adb shell am start -n 'com.google.android.gm/com.google.android.libraries.eas.onboarding.OnboardingActivity'
adb shell am start -n 'com.google.android.gm/.browse.SearchDeepLinkTrampolineActivity'
adb shell am start -n 'com.google.android.gm/com.google.android.libraries.communications.conference.ui.intents.ConferenceUrlHandlerActivity'
adb shell am start -n 'com.google.android.gm/com.google.android.libraries.eas.oauth.RedirectUriReceiverActivity'
adb shell am start -n 'com.google.android.gm/.browse.TrampolineActivity'
adb shell am start -n 'com.google.android.gm/com.android.mail.ui.settings.PublicPreferenceActivity'
adb shell am start -n 'com.google.android.gm/.GmailActivity'
adb shell am start -n 'com.google.android.gm/.ui.MailboxSelectionActivity'
adb shell am start -n 'com.google.android.gm/com.android.mail.ui.MailboxSelectionActivity'
adb shell am start -n 'com.google.android.gm/com.google.android.apps.dynamite.features.hub.navigation.PeopleActivity'
adb shell am start -n 'com.google.android.gm/.CreateShortcutActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.call.ContactsVideoActionActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.call.ContactsPrivilegedVideoActionActivity'
adb shell am start -n 'com.google.android.gms/.nearby.sharing.ShareSheetActivity'
adb shell am start -n 'com.google.android.gms/.nearby.sharing.ReceiveSurfaceActivity'
adb shell am start -n 'com.google.android.gms/.plus.sharebox.ShareBoxActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.call.ContactsAudioActionActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.call.ContactsPrivilegedAudioActionActivity'
adb shell am start -n 'com.google.android.gms/.mobiledataplan.ui.MobileDataPlanSettingsActivity'
adb shell am start -n 'com.google.android.gms/.wallet.redirect.FinishAndroidAppRedirectProxyActivity'
adb shell am start -n 'com.google.android.gms/.auth.authzen.AuthzenDeeplinkHandlerActivity'
adb shell am start -n 'com.google.android.gms/.auth.uiflows.common.UnpackingRedirectActivity'
adb shell am start -n 'com.google.android.gms/.trustagent.discovery.WebpageOnbodyPromotionActivity'
adb shell am start -n 'com.google.android.gms/.dck.main.DckActivity'
adb shell am start -n 'com.google.android.gms/.findmydevice.spot.deeplinks.DeepLinkActivity'
adb shell am start -n 'com.google.android.gms/.pay.main.PayActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.settings.TapAndPaySettingsActivity'
adb shell am start -n 'com.google.android.gms/.appinvite.AppInviteActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.tokenization.AddNewCardThroughBrowserActivity'
adb shell am start -n 'com.google.android.gms/.smartdevice.magicwand.MagicWandActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.call.CallEntryActivity'
adb shell am start -n 'com.google.android.gms/.fido.authenticator.ui.QRBounceActivity'
adb shell am start -n 'com.google.android.gms/.appinvite.AppInviteAcceptInvitationActivity'
adb shell am start -n 'com.google.android.gms/.auth.managed.ui.SetupWorkProfileActivity'
adb shell am start -n 'com.google.android.gms/com.google.firebase.auth.api.gms.ui.BrowserSignInResponseHandlerActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.ui.EntryActivity'
adb shell am start -n 'com.google.android.gms/.matchstick.ui.LighterMessageIntentActivity'
adb shell am start -n 'com.google.android.gms/.nearby.discovery.devices.DevicesListActivity'
adb shell am start -n 'com.google.android.gms/.backup.g1.interstitial.GoogleOneInterstitialActivity'
adb shell am start -n 'com.google.android.gms/.backup.component.BackupSettingsCollapsingActivity'
adb shell am start -n 'com.google.android.gms/.backup.component.BackupSettingsActivity'
adb shell am start -n 'com.google.android.gms/.dck.entrypoint.EntryPointDckActivity'
adb shell am start -n 'com.google.android.gms/.growth.ui.webview.GrowthWebViewActivity'
adb shell am start -n 'com.google.android.gms/.pay.deeplink.DeepLinkActivity'
adb shell am start -n 'com.google.android.gms/.pay.deeplink.AliasAddSignUpValuablesDeepLinkActivity'
adb shell am start -n 'com.google.android.gms/.pay.deeplink.AliasViewValuablesDetailsDeepLinkActivity'
adb shell am start -n 'com.google.android.gms/.pay.deeplink.AliasSaveValuablesDeepLinkActivity'
adb shell am start -n 'com.google.android.gms/.wallet.bender3.Bender3FinishRedirectProxyActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.upsell.InGameUiProxyActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.ingame.FeatureNotAvailableActivity'
adb shell am start -n 'com.google.android.gms/.smartdevice.setup.ui.DiscoveryActivity'
adb shell am start -n 'com.google.android.gms/.auth.setup.d2d.SourceNfcHandlerActivity'
adb shell am start -n 'com.google.android.gms/.smartdevice.setup.ui.D2DSourceNfcHandlerActivity'
adb shell am start -n 'com.google.android.gms/.trustagent.TrustAgentOnboardingActivity'
adb shell am start -n 'com.google.android.gms/.nearby.exposurenotification.settings.SettingsActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.ui.CredentialsSettingsActivity'
adb shell am start -n 'com.google.android.gms/.autofill.ui.AutofillSettingsPrivacyHubActivity'
adb shell am start -n 'com.google.android.gms/.family.v2.create.FamilyCreationActivity'
adb shell am start -n 'com.google.android.gms/.plus.activity.AccountSignUpActivity'
adb shell am start -n 'com.google.android.gms/.family.manage.FamilyManagementActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.drivingmode.DrivingModeSettingsActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.drivingmode.DrivingModeSettingsNoSummaryActivity'
adb shell am start -n 'com.google.android.gms/.plus.audience.UpdateCirclesActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.LocationHistorySettingsActivity'
adb shell am start -n 'com.google.android.gms/.wallet.pm.PmRootActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.ui.CredentialPickerActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.places.ui.placepicker.PlacePickerActivity'
adb shell am start -n 'com.google.android.gms/.signin.activity.SignInActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.credentialsaving.ui.SaveAccountLinkingTokenActivity'
adb shell am start -n 'com.google.android.gms/.plus.apps.ManageAppActivity'
adb shell am start -n 'com.google.android.gms/.app.settings.RecoverPermissionActivity'
adb shell am start -n 'com.google.android.gms/.appinvite.ui.context.ContextualPeopleSelectionActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.upsell.InstallPlayGamesActivity'
adb shell am start -n 'com.google.android.gms/.auth.uiflows.addaccount.AccountIntroActivity'
adb shell am start -n 'com.google.android.gms/.instantapps.settings.SettingsActivity'
adb shell am start -n 'com.google.android.gms/.udc.ui.UdcSettingsListActivity'
adb shell am start -n 'com.google.android.gms/.usagereporting.ui.UsageReportingDebugActivity'
adb shell am start -n 'com.google.android.gms/.auth.uiflows.consent.GrantCredentialsWithAclActivity'
adb shell am start -n 'com.google.android.gms/.permissions.debug.ManagePermissionUsageActivity'
adb shell am start -n 'com.google.android.gms/.family.v2.manage.FamilyManagementActivity'
adb shell am start -n 'com.google.android.gms/.wallet.im.ImRootActivity'
adb shell am start -n 'com.google.android.gms/.family.v2.invites.SendInvitationsActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.tokenization.TokenizePanActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.LocationSettingsCheckerActivity'
adb shell am start -n 'com.google.android.gms/.plus.apps.ListAppsActivity'
adb shell am start -n 'com.google.android.gms/.backup.component.D2dSourceActivity'
adb shell am start -n 'com.google.android.gms/.kids.TransparencyActivity'
adb shell am start -n 'com.google.android.gms/.auth.uiflows.addaccount.GoogleServicesActivity'
adb shell am start -n 'com.google.android.gms/.setupservices.GoogleServicesActivity'
adb shell am start -n 'com.google.android.gms/.ocr.SecuredCreditCardOcrActivity'
adb shell am start -n 'com.google.android.gms/.people.settings.PeopleInternalSettingsActivity'
adb shell am start -n 'com.google.android.gms/.accountsettings.mg.ui.main.MainActivity'
adb shell am start -n 'com.google.android.gms/.wallet.ow.ChooseAccountShimActivity'
adb shell am start -n 'com.google.android.gms/.trustagent.ConfirmUserCredentialAndStartActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.signin.ui.SignInActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.phone.ui.AutofillSettingsActivity'
adb shell am start -n 'com.google.android.gms/.nearby.discovery.devices.FindDeviceActivity'
adb shell am start -n 'com.google.android.gms/.icing.ui.SettingsContainerActivity'
adb shell am start -n 'com.google.android.gms/.auth.managed.ui.PhoneskyDpcInstallActivity'
adb shell am start -n 'com.google.android.gms/.autofill.ui.settings.AutofillModernSettingsActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.settingsv2.GamesSettingsActivity'
adb shell am start -n 'com.google.android.gms/.growth.upgradeparty.activity.DebugActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.profile.CreateProfileActivity'
adb shell am start -n 'com.google.android.gms/.auth.login.LoginActivity'
adb shell am start -n 'com.google.android.gms/.smartdevice.setup.ui.D2DSetupActivity'
adb shell am start -n 'com.google.android.gms/.wearable.consent.TermsOfServiceActivity'
adb shell am start -n 'com.google.android.gms/.plus.sharebox.ReplyBoxActivity'
adb shell am start -n 'com.google.android.gms/.smart_profile.SmartProfileActivity'
adb shell am start -n 'com.google.android.gms/.wallet.common.ui.UpdateCallingAppActivity'
adb shell am start -n 'com.google.android.gms/.family.manage.DeleteMemberActivity'
adb shell am start -n 'com.google.android.gms/.feedback.IntentListenerFeedbackActivity'
adb shell am start -n 'com.google.android.gms/.wallet.timelineview.TimeLineViewActivity'
adb shell am start -n 'com.google.android.gms/.plus.audience.CircleSelectionActivity'
adb shell am start -n 'com.google.android.gms/.romanesco.settings.ContactsRestoreSettingsActivity'
adb shell am start -n 'com.google.android.gms/.enterprise.zerotouch.ui.FactoryResetActivity'
adb shell am start -n 'com.google.android.gms/.bugreport.BugreportActivity'
adb shell am start -n 'com.google.android.gms/.app.settings.GoogleSettingsActivity'
adb shell am start -n 'com.google.android.gms/.easysignin.EasySignInActivity'
adb shell am start -n 'com.google.android.gms/.kids.SyncTailTrapperActivity'
adb shell am start -n 'com.google.android.gms/.kids.LockscreenActivity'
adb shell am start -n 'com.google.android.gms/.kids.settings.KidsSettingsActivity'
adb shell am start -n 'com.google.android.gms/.update.OtaSuggestionActivity'
adb shell am start -n 'com.google.android.gms/.trustagent.discovery.OnbodyPromotionActivity'
adb shell am start -n 'com.google.android.gms/.wallet.setupwizard.PaymentsSetupWizardPortalActivity'
adb shell am start -n 'com.google.android.gms/.wallet.setupwizard.PaymentsSetupWizardActivity'
adb shell am start -n 'com.google.android.gms/.wallet.setupwizard.PaymentsSetupWizardTokenEligibleActivity'
adb shell am start -n 'com.google.android.gms/.wallet.setupwizard.PaymentsSetupWizardReactivationActivity'
adb shell am start -n 'com.google.android.gms/.adsidentity.settings.AdsIdentitySettingsActivity'
adb shell am start -n 'com.google.android.gms/.growth.featuredrops.activity.FeatureDropsActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.phone.ui.UserConsentPromptActivity'
adb shell am start -n 'com.google.android.gms/.update.SystemUpdateActivity'
adb shell am start -n 'com.google.android.gms/.wallet.ow.ChooseAccountShimInternalActivity'
adb shell am start -n 'com.google.android.gms/.ocr.GiftCardOcrActivity'
adb shell am start -n 'com.google.android.gms/.common.account.AccountChipAccountPickerActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.yolo.ui.CredentialsSnackbarActivity'
adb shell am start -n 'com.google.android.gms/.permissions.debug.PermissionsDebugActivity'
adb shell am start -n 'com.google.android.gms/.security.settings.SecuritySettingsActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.transaction.WalletTransactionDetailsActivity'
adb shell am start -n 'com.google.android.gms/.usagereporting.settings.UsageReportingActivity'
adb shell am start -n 'com.google.android.gms/.mdm.MdmSettingsActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.DrivingBehaviorSettingActivity'
adb shell am start -n 'com.google.android.gms/.constellation.ui.ApiConsentActivity'
adb shell am start -n 'com.google.android.gms/.locationsharing.activity.LocationSharingRedirectActivity'
adb shell am start -n 'com.google.android.gms/.ocr.CardCaptureActivity'
adb shell am start -n 'com.google.android.gms/.wallet.selector.InitializeGenericSelectorRootActivity'
adb shell am start -n 'com.google.android.gms/.accountsettings.ui.SettingsLoaderActivity'
adb shell am start -n 'com.google.android.gms/.octarine.ui.OctarineWebviewActivity'
adb shell am start -n 'com.google.android.gms/.people.consentprimitive.ContactsConsentPrimitiveActivity'
adb shell am start -n 'com.google.android.gms/.backup.component.BackupOptInActivity'
adb shell am start -n 'com.google.android.gms/.fitness.settings.FitnessSettingsActivity'
adb shell am start -n 'com.google.android.gms/.common.account.SimpleAccountPickerActivity'
adb shell am start -n 'com.google.android.gms/.icing.ui.IcingManageSpaceActivity'
adb shell am start -n 'com.google.android.gms/.permissions.debug.AllConsumerServicesActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.assistedsignin.ui.PhoneNumberHintActivity'
adb shell am start -n 'com.google.android.gms/.netrec.scoring.client.wfa.WfaOptInActivity'
adb shell am start -n 'com.google.android.gms/.common.download.DownloadServiceSettingsActivity'
adb shell am start -n 'com.google.android.gms/.auth.uiflows.factoryreset.PreFactoryResetActivity'
adb shell am start -n 'com.google.android.gms/.family.v2.invites.contactpicker.ContactPickerActivity'
adb shell am start -n 'com.google.android.gms/.mlkit.barcode.ui.BarcodeScanningActivity'
adb shell am start -n 'com.google.android.gms/.people.sync.coreui.ContactsSyncCoreActivity'
adb shell am start -n 'com.google.android.gms/.app.net.NetworkUsageActivity'
adb shell am start -n 'com.google.android.gms/.auth.managed.ui.EmmActivity'
adb shell am start -n 'com.google.android.gms/.kids.KidSetupActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.authorization.ui.AuthorizationActivity'
adb shell am start -n 'com.google.android.gms/.wallet.idcredit.IdCreditActivity'
adb shell am start -n 'com.google.android.gms/.walletp2p.feature.transfer.TransferMoneyActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.signinflow.SignInActivity'
adb shell am start -n 'com.google.android.gms/.plus.oob.PlusActivity'
adb shell am start -n 'com.google.android.gms/.wallet.activity.OrchestrationDelegatorActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.assistedsignin.ui.GoogleSignInActivity'
adb shell am start -n 'com.google.android.gms/.nearby.exposurenotification.settings.SettingsCheckerActivity'
adb shell am start -n 'com.google.android.gms/.smartdevice.setup.ui.AccountChallengeActivity'
adb shell am start -n 'com.google.android.gms/.wallet.activity.GenericDelegatorActivity'
adb shell am start -n 'com.google.android.gms/.constellation.ui.ConstellationOnDemandConsentActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.settings.GamesSettingsActivity'
adb shell am start -n 'com.google.android.gms/.nearby.sharing.SettingsActivity'
adb shell am start -n 'com.google.android.gms/.nearby.sharing.SettingsPreferenceActivity'
adb shell am start -n 'com.google.android.gms/.nearby.sharing.SettingsCollapsingToolbarActivity'
adb shell am start -n 'com.google.android.gms/.ads.settings.AdsSettingsActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.assistedsignin.ui.AssistedSignInActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.ActivityRecognitionPermissionActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.GoogleLocationSettingsActivity'
adb shell am start -n 'com.google.android.gms/.location.settings.LocationAccuracyActivity'
adb shell am start -n 'com.google.android.gms/.location.settings.LocationAccuracyV31Activity'
adb shell am start -n 'com.google.android.gms/.kids.SettingsActivity'
adb shell am start -n 'com.google.android.gms/.chimera.container.ui.ModuleExtractionActivity'
adb shell am start -n 'com.google.android.gms/.walletp2p.feature.completion.CompleteMoneyTransferActivity'
adb shell am start -n 'com.google.android.gms/.family.v2.manage.DeleteMemberActivity'
adb shell am start -n 'com.google.android.gms/.wearable.playsetup.ui.AppInstallActivity'
adb shell am start -n 'com.google.android.gms/.presencemanager.communal.activity.ConsentActivity'
adb shell am start -n 'com.google.android.gms/.autofill.ui.AutofillManagePasswordsActivity'
adb shell am start -n 'com.google.android.gms/.accountsettings.ui.ZeroPartyEntryPointActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.assistedsignin.ui.PhoneNumberHintSettingsActivity'
adb shell am start -n 'com.google.android.gms/.app.settings.licenses.LicensesActivity'
adb shell am start -n 'com.google.android.gms/.plus.audience.FaclSelectionActivity'
adb shell am start -n 'com.google.android.gms/.kids.chimera.RegisterProfileOwnerActivity'
adb shell am start -n 'com.google.android.gms/com.google.firebase.auth.api.gms.ui.BrowserSignInStarterActivity'
adb shell am start -n 'com.google.android.gms/.plus.audience.CircleCreationActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.ui.TokenizationSuccessActivity'
adb shell am start -n 'com.google.android.gms/.mdi.download.ui.DebugUiActivity'
adb shell am start -n 'com.google.android.gms/.cast.activity.CastPopupActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.credentialsaving.ui.PasswordSavingActivity'
adb shell am start -n 'com.google.android.gms/.accountsettings.ui.SearchEntryPointActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.places.ui.autocomplete.AutocompleteActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.EAlertGoogleSettingDebugActivity'
adb shell am start -n 'com.google.android.gms/.permissions.ViewPermissionUsageActivity'
adb shell am start -n 'com.google.android.gms/.pay.main.PayOptionalActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.phone.ui.BrowserConsentActivity'
adb shell am start -n 'com.google.android.gms/.googlehelp.helpactivities.HelpActivity'
adb shell am start -n 'com.google.android.gms/.mlkit.barcode.ui.PlatformBarcodeScanningActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.EAlertSettingsActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.EAlertSettingsV31Activity'
adb shell am start -n 'com.google.android.gms/.tapandpay.ui.ShowSecurityPromptActivity'
adb shell am start -n 'com.google.android.gms/.games.PlayGamesUpgradeActivity'
adb shell am start -n 'com.google.android.gms/.update.UpdateFromSdCardActivity'
adb shell am start -n 'com.google.android.gms/.plus.audience.AclSelectionActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.phone.ui.AutofillConsentActivity'
adb shell am start -n 'com.google.android.gms/.chimera.container.ui.ModuleDownloadActivity'
adb shell am start -n 'com.google.android.gms/.wallet.paymentmethods.PaymentMethodsActivity'
adb shell am start -n 'com.google.android.gms/.plus.circles.AddToCircleConsentActivity'
adb shell am start -n 'com.google.android.gms/.romanesco.restore.settings.ContactsRestoreSettingsActivity'
adb shell am start -n 'com.google.android.gms/.signin.activity.ConsentActivity'
adb shell am start -n 'com.google.android.gms/.chimera.debug.ChimeraDebugActivity'
adb shell am start -n 'com.google.android.gms/.feedback.FeedbackActivity'
adb shell am start -n 'com.google.android.gms/.wearable.consent.PrivacySettingsActivity'
adb shell am start -n 'com.google.android.gms/.auth.login.BrowserActivity'
adb shell am start -n 'com.google.android.gms/.romanesco.settings.ContactsRestoreDialogActivity'
adb shell am start -n 'com.google.android.gms/.usagereporting.ui.UsageReportingDialogActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.diagnostics.TapDiagnosticsActivity'
adb shell am start -n 'com.google.android.gms/.people.profile.AvatarActivity'
adb shell am start -n 'com.google.android.gms/.security.settings.VerifyAppsSettingsActivity'
adb shell am start -n 'com.google.android.gms/.romanesco.restore.ContactsRestoreActivity'
adb shell am start -n 'com.google.android.gms/.locationsharing.activity.OnboardingActivity'
adb shell am start -n 'com.google.android.gms/.trustlet.place.ui.TrustedPlacesSettingsActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.ealert.ux.EAlertSafetyInfoActivity'
adb shell am start -n 'com.google.android.gms/.smartdevice.d2d.ui.AtvSetupActivity'
adb shell am start -n 'com.google.android.gms/.games.ui.video.ScreenCaptureRequestActivity'
adb shell am start -n 'com.google.android.gms/.mdm.settings.AdmSettingsActivity'
adb shell am start -n 'com.google.android.gms/.mdm.settings.FindMyDeviceSettingsActivity'
adb shell am start -n 'com.google.android.gms/.googlehelp.helpactivities.SystemAppTrampolineActivity'
adb shell am start -n 'com.google.android.gms/.auth.uiflows.addaccount.PreAddAccountActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.ui.EnableSecureKeyguardActivity'
adb shell am start -n 'com.google.android.gms/.plus.audience.UpdateActionOnlyActivity'
adb shell am start -n 'com.google.android.gms/.constellation.ui.ConstellationOnDemandConsentV2Activity'
adb shell am start -n 'com.google.android.gms/.wallet.setupwizard.PaymentsSetupWizardMainActivity'
adb shell am start -n 'com.google.android.gms/.plus.plusone.PlusOneActivity'
adb shell am start -n 'com.google.android.gms/.mdm.LockscreenActivity'
adb shell am start -n 'com.google.android.gms/.thunderbird.settings.ThunderbirdSettingsActivity'
adb shell am start -n 'com.google.android.gms/.thunderbird.settings.ThunderbirdSettingsV31Activity'
adb shell am start -n 'com.google.android.gms/.accountsettings.ui.PrivacyHubActivityControlsActivity'
adb shell am start -n 'com.google.android.gms/.auth.managed.ui.SettingsSecurityDeviceOwnerActivity'
adb shell am start -n 'com.google.android.gms/.auth.proximity.multidevice.SettingsActivity'
adb shell am start -n 'com.google.android.gms/.location.settings.EAlertPlatformSettingsActivity'
adb shell am start -n 'com.google.android.gms/.family.webview.FamilyWebViewActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.places.ui.aliaseditor.AliasEditorActivity'
adb shell am start -n 'com.google.android.gms/.mobiledataplan.ui.MobileDataPlanDetailActivity'
adb shell am start -n 'com.google.android.gms/.wearable.ui.WearableManageSpaceActivity'
adb shell am start -n 'com.google.android.gms/.kids.LockscreenUnlockActivity'
adb shell am start -n 'com.google.android.gms/.backup.component.EnhancedBackupOptInActivity'
adb shell am start -n 'com.google.android.gms/.plus.ui.DpadNavigableWebViewActivity'
adb shell am start -n 'com.google.android.gms/.family.v2.tos.TosActivity'
adb shell am start -n 'com.google.android.gms/.permissions.ViewPermissionUsageForPeriodActivity'
adb shell am start -n 'com.google.android.gms/.family.create.FamilyCreationActivity'
adb shell am start -n 'com.google.android.gms/.auth.api.credentials.credentialsaving.ui.SaveAccountLinkingTokenInternalConsentActivity'
adb shell am start -n 'com.google.android.gms/com.google.android.location.settings.ActivityRecognitionModeActivity'
adb shell am start -n 'com.google.android.gms/.nearby.sharing.DeviceVisibilityActivity'
adb shell am start -n 'com.google.android.gms/.auth.managed.ui.SetNewPasswordActivity'
adb shell am start -n 'com.google.android.gms/.tapandpay.ui.WarmWelcomeActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.lens.LensShareEntryPointActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.verticals.memory.framework.selection.MemorySelectionActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/.RecordedVoiceSearchActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.EnterOpaActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.verticals.familyshare.FamilyShareActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.verticals.memory.entity.imagegallery.ImageGalleryViewerActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.android.launcher3.WallpaperCropActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.assistant.handoff.BrowserReturnActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.assistant.handoff.AssistantHandoffActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/.SearchActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.opa.VoiceMatchEnrollmentActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.velour.DynamicActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.lens.MainActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.assistant.settings.hq.agentdirectory.AgentDirectoryActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.deeplink.DeeplinkActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.opa.HotwordMigrationActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.hq.OpaHqActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.googleapp.stampviewer.share.StampViewerShareActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.promo.UpgradePromoTooltipActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.verticals.family.custodio.CustodioGatewayActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.search.calypso.AppIndexingActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.verticals.memory.framework.home.StashHomeActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.libraries.accountlinking.activity.AccountLinkingActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.morris2.drivingscreen.DrivingScreenActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.assistant.settings.AssistantSettingsActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.velvet.ui.settings.PublicSettingsActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.queryentry.QueryEntryActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.surfaces.onboarding.setupwizard.SetupWizardActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.sidekick.main.optin.OptInActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.voicesearch.greco3.languagepack.InstallActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/.VoiceSearchActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.setupwizard.SetupWizardActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.velvet.ui.settings.SettingsActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.surfaces.roti.home.HomeActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.hq.ResizableOpaHqActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.android.launcher3.AddItemActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.voicesearch.handsfree.HandsFreeActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/.DspHotwordVoiceSearchActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.surfaces.common.shortcut.ShortcutActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.launcher.GelWallpaperPickerActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.morris2.onboarding.OpaOnboardingActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.search_gesture.GestureActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.languagepack.DownloadActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.voicesearch.intentapi.IntentApiActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.opa.AssistantOnboardingActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.sidekick.main.optin.NowOptInFirstPartyActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.surfaces.voice.ui.input.settings.MyActionsActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.search.assistant.verticals.snapshot.widgets.weather.ConfigurationActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.sidekick.main.remoteservice.CurrentAccountActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.projection.OpaAutoOptInActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.errorui.UdcPuntCardActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.settings.AssistantAndroidSettingsActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.soundsearchwidget.AliasAddShortcutActivity'
adb shell am start -n 'com.google.android.googlequicksearchbox/com.google.android.apps.gsa.staticplugins.opa.zerostate.widget.SnapshotAddShortcutActivity'
adb shell am start -n 'com.google.android.gsf/.settings.ConfirmLgaaylActivity'
adb shell am start -n 'com.google.android.gsf/.settings.SettingsTosActivity'
adb shell am start -n 'com.google.android.gsf/.settings.common.AutomotiveWebViewActivity'
adb shell am start -n 'com.google.android.gsf/.settings.UseLocationForServicesActivity'
adb shell am start -n 'com.google.android.hotspot2.osulogin/com.android.hotspot2.osulogin.OsuLoginActivity'
adb shell am start -n 'com.google.android.inputmethod.latin/com.google.android.apps.inputmethod.latin.sharing.LinkReceivingLauncherActivity'
adb shell am start -n 'com.google.android.inputmethod.latin/com.google.android.apps.inputmethod.libs.framework.core.LauncherActivity'
adb shell am start -n 'com.google.android.inputmethod.latin/com.google.android.apps.inputmethod.latin.spelling.LatinSpellCheckerSettingsActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackSelectorMenuPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackVerbosityPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackKeyboardShortcutPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackFocusIndicatorPreferenceActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.android.talkback.TalkBackPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.GestureChangeNotificationActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.NotificationActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.accessibilitymenu.activity.A11yMenuSettingsActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.selecttospeak.activities.SelectToSpeakPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackDeveloperPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackContextMenuPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackSoundAndVibrationPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.brailleime.settings.BrailleImePreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.labeling.LabelManagerSummaryActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackDumpAccessibilityEventActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackAdvancedPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackCustomizeMenusPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackHelpPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackShortcutPreferencesActivity'
adb shell am start -n 'com.google.android.marvin.talkback/com.google.android.accessibility.talkback.preference.TalkBackNavigationMenuPreferencesActivity'
adb shell am start -n 'com.google.android.packageinstaller/com.android.packageinstaller.UninstallerActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.role.ui.HomeSettingsActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.role.ui.RequestRoleActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.permission.ui.ManagePermissionsActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.role.ui.SpecialAppAccessListActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.permission.ui.GrantPermissionsActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.role.ui.RoleSearchTrampolineActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.role.ui.DefaultAppActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.permission.ui.ReviewOngoingUsageActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.role.ui.DefaultAppListActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.permission.ui.ReviewAccessibilityServicesActivity'
adb shell am start -n 'com.google.android.permissioncontroller/com.android.permissioncontroller.permission.ui.ReviewPermissionsActivity'
adb shell am start -n 'com.google.android.projection.gearhead/com.google.android.apps.auto.components.app.stubapp.StubSettingsActivity'
adb shell am start -n 'com.google.android.projection.gearhead/com.google.android.gearhead.vanagon.VnLaunchPadActivity'
adb shell am start -n 'com.google.android.projection.gearhead/com.google.android.apps.auto.carservice.gmscorecompatstub.StubFirstActivity'
adb shell am start -n 'com.google.android.providers.media.module/com.android.providers.media.CacheClearingActivity'
adb shell am start -n 'com.google.android.setupwizard/.util.WebDialogActivity'
adb shell am start -n 'com.google.android.setupwizard/.network.WifiActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.WorkSetupInterruptedActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.DecisionPointActivity'
adb shell am start -n 'com.google.android.setupwizard/.util.SecureInterceptActivity'
adb shell am start -n 'com.google.android.setupwizard/.update.PostCheckinAndUpdateActivity'
adb shell am start -n 'com.google.android.setupwizard/.portal.PortalProgressActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.DarkModeActivity'
adb shell am start -n 'com.google.android.setupwizard/.SetupWizardActivity'
adb shell am start -n 'com.google.android.setupwizard/.deferred.DeferredTrampolineActivity'
adb shell am start -n 'com.google.android.setupwizard/.deferred.DeferredSettingsSuggestionActivity'
adb shell am start -n 'com.google.android.setupwizard/.carrier.SimReadyActivity'
adb shell am start -n 'com.google.android.setupwizard/.carrier.SimSetupActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.UserWarningActivity'
adb shell am start -n 'com.google.android.setupwizard/.qrprovision.QrScanActivity'
adb shell am start -n 'com.google.android.setupwizard/.restore.RestoreProgressActivity'
adb shell am start -n 'com.google.android.setupwizard/.network.NetworkTimeoutActivity'
adb shell am start -n 'com.google.android.setupwizard/.SetupWizardExitActivity'
adb shell am start -n 'com.google.android.setupwizard/.portal.OptionalSetupActivity'
adb shell am start -n 'com.google.android.setupwizard/.predeferred.PreDeferredProgressActivity'
adb shell am start -n 'com.google.android.setupwizard/.provision.PreEnterpriseSetupActivity'
adb shell am start -n 'com.google.android.setupwizard/.restore.IosSetupActivity'
adb shell am start -n 'com.google.android.setupwizard/.carrier.SimMissingActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.DeviceOwnerWarningActivity'
adb shell am start -n 'com.google.android.setupwizard/.update.OtaUpdateActivity'
adb shell am start -n 'com.google.android.setupwizard/.carrier.SlotsSelectionActivity'
adb shell am start -n 'com.google.android.setupwizard/.predeferred.ConnectToWifiActivity'
adb shell am start -n 'com.google.android.setupwizard/.time.DateTimeActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.SuggestedActionsActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.WelcomeActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.WorkProfileSetupActivity'
adb shell am start -n 'com.google.android.setupwizard/.network.NetworkActivity'
adb shell am start -n 'com.google.android.setupwizard/.WizardManagerActivity'
adb shell am start -n 'com.google.android.setupwizard/.carrier.EsimIntroActivity'
adb shell am start -n 'com.google.android.setupwizard/.provision.TransitionToPersonalProfileSetupActivity'
adb shell am start -n 'com.google.android.setupwizard/.restore.GetRestoreFlowActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.ExitToSupportActivity'
adb shell am start -n 'com.google.android.setupwizard/.carrier.MobileDataActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.FactoryResetActivity'
adb shell am start -n 'com.google.android.setupwizard/.deferred.DeferredSetupWelcomeActivity'
adb shell am start -n 'com.google.android.setupwizard/.user.DeviceOwnerUserSetupCompleteActivity'
adb shell am start -n 'com.google.android.tts/com.google.android.apps.speech.tts.googletts.local.voicepack.ui.VoiceDataInstallActivity'
adb shell am start -n 'com.google.android.tts/com.google.android.libraries.speech.modelmanager.languagepack.DownloadActivity'
adb shell am start -n 'com.google.android.tts/com.google.android.apps.speech.tts.googletts.service.GoogleTTSActivity'
adb shell am start -n 'com.google.android.tts/com.google.android.apps.speech.tts.googletts.settings.asr.AddLanguagesActivity'
adb shell am start -n 'com.google.android.tts/com.google.android.apps.speech.tts.googletts.settings.asr.SettingsActivity'
adb shell am start -n 'com.google.android.videos/.activity.LauncherActivity'
adb shell am start -n 'com.google.android.videos/.activity.GoogleTvLauncherActivity'
adb shell am start -n 'com.google.android.videos/com.google.android.apps.play.movies.common.presenter.activity.TrailerLauncherActivity'
adb shell am start -n 'com.google.android.videos/com.google.android.apps.play.movies.common.presenter.activity.ApiActivity'
adb shell am start -n 'com.google.android.videos/.mobile.usecase.settings.SettingsActivity'
adb shell am start -n 'com.google.android.videos/.ManageNetworkUsageActivity'
adb shell am start -n 'com.google.android.videos/.mobile.service.remote.cast.LogCollectorActivity'
adb shell am start -n 'com.google.android.videos/.mobile.presenter.activity.SearchActivity'
adb shell am start -n 'com.google.android.videos/com.google.android.apps.play.movies.mobile.presenter.activity.RestrictionsActivity'
adb shell am start -n 'com.google.android.webview/org.chromium.android_webview.devui.MainActivity'
adb shell am start -n 'com.google.android.webview/org.chromium.android_webview.nonembedded.LicenseActivity'
adb shell am start -n 'com.google.android.wfcactivation/.WfcActivationActivity'
adb shell am start -n 'com.google.android.wfcactivation/.can.WfcActivationCanadaActivity'
adb shell am start -n 'com.google.android.wfcactivation/.WfcActivationCanadaActivity'
adb shell am start -n 'com.google.android.wfcactivation/.vzw.VzwEmergencyAddressActivity'
adb shell am start -n 'com.google.android.wfcactivation/.VzwEmergencyAddressActivity'
adb shell am start -n 'com.google.android.wifi.resources/android.app.Activity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.application.Shell_UploadActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.extensions.upload.UploadActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.extensions.accountlinking.UriFlowActivity'
adb shell am start -n 'com.google.android.youtube/com.google.cardboard.sdk.HeadsetDetectionActivity'
adb shell am start -n 'com.google.android.youtube/.UrlActivity'
adb shell am start -n 'com.google.android.youtube/net.openid.appauth.RedirectUriReceiverActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.libraries.accountlinking.activity.AccountLinkingActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.application.Shell$ResultsActivity'
adb shell am start -n 'com.google.android.youtube/.api.StandalonePlayerActivity'
adb shell am start -n 'com.google.android.youtube/.app.honeycomb.Shell$HomeActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.application.Shell_SettingsActivity'
adb shell am start -n 'com.google.android.youtube/.ManageNetworkUsageActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.application.Shell_LiveCreationActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.application.Shell_MediaSearchActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.watchwhile.WatchWhileActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.settings.videoquality.VideoQualitySettingsActivity'
adb shell am start -n 'com.google.android.youtube/com.google.android.apps.youtube.app.settings.datasaving.DataSavingSettingsActivity'
adb shell am start -n 'com.lenovo.lsf.user/com.lenovo.lsf.lenovoid.ui.PsLoginFirstActivity'
adb shell am start -n 'com.lenovo.lsf.user/com.facebook.CustomTabActivity'
adb shell am start -n 'com.lenovo.lsf.user/com.lenovo.lsf.lenovoid.ui.PsLoginFirstGmailActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.sound.AndroidSettingsActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.security.AndroidSettingsActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.gestures.AndroidSettingsActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.battery.optimizedcharging.SmartBatteryOptimizedChargingActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.battery.overchargeprotection.SmartBatteryOverchargeProtectionActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.display.AndroidSettingsActivity'
adb shell am start -n 'com.motorola.actions/.ui.androidsettings.battery.suggestion.SettingsSuggestionActivity'
adb shell am start -n 'com.motorola.actions/.ui.settings.SettingsDetailActivity'
adb shell am start -n 'com.motorola.actions/.ui.settings.SettingsActivity'
adb shell am start -n 'com.motorola.appforecast/.ui.activity.AppForecastSettingsActivity'
adb shell am start -n 'com.motorola.appforecast/.ui.activity.ZRamSettingsActivity'
adb shell am start -n 'com.motorola.appforecast/.ui.activity.QuickLaunchSettingsActivity'
adb shell am start -n 'com.motorola.att.phone.extensions/.unlock.UnlockDialogActivity'
adb shell am start -n 'com.motorola.attvowifi/.ui.WfcSecondMainActivity'
adb shell am start -n 'com.motorola.attvowifi/.ui.WfcToggleActivity'
adb shell am start -n 'com.motorola.attvowifi/.ui.WfcQuickSettingsLaunchActivity'
adb shell am start -n 'com.motorola.attvowifi/.ui.WfcSecondToggleActivity'
adb shell am start -n 'com.motorola.attvowifi/.ui.WfcMainActivity'
adb shell am start -n 'com.motorola.audiofx/com.motorola.motoaudio.ui.introduction.IntroductionActivity'
adb shell am start -n 'com.motorola.audiofx/com.motorola.motoaudio.ui.LauncherActivity'
adb shell am start -n 'com.motorola.brapps/.ui.BrAppsActivity'
adb shell am start -n 'com.motorola.brapps/.ui.RetBrActivity'
adb shell am start -n 'com.motorola.brapps/.MainActivity'
adb shell am start -n 'com.motorola.brapps/.ui.CarrierActivity'
adb shell am start -n 'com.motorola.brapps/.ui.TimBrActivity'
adb shell am start -n 'com.motorola.brapps/.ui.MovistarMxActivity'
adb shell am start -n 'com.motorola.brapps/.ui.MovistarCoActivity'
adb shell am start -n 'com.motorola.brapps/.ui.ClaroBrActivity'
adb shell am start -n 'com.motorola.brapps/.ui.VivoBrActivity'
adb shell am start -n 'com.motorola.brapps/.ui.TigoCoActivity'
adb shell am start -n 'com.motorola.brapps/.ui.MovistarPeActivity'
adb shell am start -n 'com.motorola.brapps/.ui.EntelPeActivity'
adb shell am start -n 'com.motorola.brapps/.ui.AttMxActivity'
adb shell am start -n 'com.motorola.brapps/.ui.AttMxUnefonActivity'
adb shell am start -n 'com.motorola.brapps/.ui.TelcelMxActivity'
adb shell am start -n 'com.motorola.brapps/.ui.OpenMxActivity'
adb shell am start -n 'com.motorola.brapps/.ui.ClaroCoActivity'
adb shell am start -n 'com.motorola.camera3/com.motorola.camera.editor.DocEditorActivity'
adb shell am start -n 'com.motorola.camera3/com.motorola.camera.cli.camera.CliCameraActivity'
adb shell am start -n 'com.motorola.camera3/com.motorola.camera.voice.CameraVoiceActivity'
adb shell am start -n 'com.motorola.carrierconfig/.activity.ManualSyncConfigActivity'
adb shell am start -n 'com.motorola.carrierconfig/.activity.ConfigFileInfoActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.wfc.help.MotoSettingsHelpActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.wfc.WFCSettingsSecondActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.vzwguti.ResetActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.wfc.WFCQuickSettingsLaunchActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.wfc.emara.tile.service.WFCDummySettingsActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.wfc.WFCSettingsActivity'
adb shell am start -n 'com.motorola.carriersettingsext/.unlock.NetworkUnlockActivity'
adb shell am start -n 'com.motorola.ccc.devicemanagement/com.motorola.ccc.sso.ui.CreateAccountActivity'
adb shell am start -n 'com.motorola.ccc.devicemanagement/com.motorola.ccc.sso.ui.MainSettingsActivity'
adb shell am start -n 'com.motorola.ccc.notification/.ui.SubscriptionByQRActivity'
adb shell am start -n 'com.motorola.ccc.notification/com.motorola.engageapp.ui.EngageActivity'
adb shell am start -n 'com.motorola.ccc.notification/com.motorola.engageapp.ui.MotoplaceActivity'
adb shell am start -n 'com.motorola.ccc.notification/com.motorola.engageapp.ui.WebviewActivity'
adb shell am start -n 'com.motorola.ccc.ota/.ui.SettingsActivity'
adb shell am start -n 'com.motorola.ccc.ota/.ui.BaseActivity'
adb shell am start -n 'com.motorola.coresettingsext/.DeepLinkLandingActivity'
adb shell am start -n 'com.motorola.coresettingsext/.charging.wireless.PSSettingsActivity'
adb shell am start -n 'com.motorola.coresettingsext/.screenrecord.ScreenRecordActivity'
adb shell am start -n 'com.motorola.coresettingsext/.setup.DeviceSetupRouterActivity'
adb shell am start -n 'com.motorola.coresettingsext/.BuildFingerprintActivity'
adb shell am start -n 'com.motorola.coresettingsext/.setup.apn.SelectAPNActivity'
adb shell am start -n 'com.motorola.coresettingsext/.QsTilePreferenceRouterActivity'
adb shell am start -n 'com.motorola.demo/.admin.ProvisioningActivity'
adb shell am start -n 'com.motorola.demo/.activity.HomeScreenIconActivity'
adb shell am start -n 'com.motorola.dynamicvolume/.ui.SettingsRouterActivity'
adb shell am start -n 'com.motorola.dynamicvolume/.ui.automute.AutoMuteActivity'
adb shell am start -n 'com.motorola.easyprefix/.SingleSimSettingsActivity'
adb shell am start -n 'com.motorola.easyprefix/.WizardActivity'
adb shell am start -n 'com.motorola.faceunlock/.ConfirmLockScreenActivity'
adb shell am start -n 'com.motorola.faceunlock/.LicencesActivity'
adb shell am start -n 'com.motorola.fmplayer/.assistantactions.AssistantActionsActivity'
adb shell am start -n 'com.motorola.fmplayer/.ChangeThemeActivity'
adb shell am start -n 'com.motorola.fmplayer/.FMMainActivity'
adb shell am start -n 'com.motorola.gamemode/.ui.PreferenceSettingsActivity'
adb shell am start -n 'com.motorola.gamemode/.ui.launcher.main.GameCenterActivity'
adb shell am start -n 'com.motorola.gamemode/.ui.launcher.GameCenterActivity'
adb shell am start -n 'com.motorola.genie/.main.start.LaunchActivity'
adb shell am start -n 'com.motorola.genie/com.lenovo.lsf.lenovoid.ui.PsLoginFirstActivity'
adb shell am start -n 'com.motorola.genie/.devicediagnosis.hardwaretest.activity.HardwareTestActivity'
adb shell am start -n 'com.motorola.genie/.main.notification.NotificationActivity'
adb shell am start -n 'com.motorola.genie/.contactus.moli.MoliChatWebViewActivity'
adb shell am start -n 'com.motorola.genie/.contactus.ContactUsActivity'
adb shell am start -n 'com.motorola.genie/.common.CommonWebViewActivity'
adb shell am start -n 'com.motorola.gesture/.hint.GestureTutorialHintActivity'
adb shell am start -n 'com.motorola.help/com.motorola.feedback.ui.QuickSettingsLPActivity'
adb shell am start -n 'com.motorola.help/com.google.firebase.auth.internal.GenericIdpActivity'
adb shell am start -n 'com.motorola.help/com.google.firebase.auth.internal.RecaptchaActivity'
adb shell am start -n 'com.motorola.help/com.motorola.feedback.ui.RateAndFBSettingsLPActivity'
adb shell am start -n 'com.motorola.help/com.motorola.feedback.ui.FeedbackActivity'
adb shell am start -n 'com.motorola.help/com.motorola.feedback.inappfeedback.uiapi.ContextualInvitationActivity'
adb shell am start -n 'com.motorola.hiddenmenuapp/.mobilenetworkdebuginfo.MobileNetworkDebugInfoActivity'
adb shell am start -n 'com.motorola.hiddenmenuapp/com.sprint.ms.smf.activities.CallingPlusQuickStartActivity'
adb shell am start -n 'com.motorola.hiddenmenuapp/com.sprint.ms.smf.activities.PermissionsActivity'
adb shell am start -n 'com.motorola.hiddenmenuapp/com.sprint.ms.smf.activities.VolteHelpActivity'
adb shell am start -n 'com.motorola.hiddenmenuapp/com.sprint.ms.smf.activities.CallingPlusHelpActivity'
adb shell am start -n 'com.motorola.hiddenmenuapp/.main.HiddenMenuMainActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.hybridhotseat.HotseatEduActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.dragndrop.AddItemActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.settings.SettingsActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.discovery.DiscoveryPrivacyActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.settings.SingleLayerStyleSettingsActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.settings.HomeScreenStyleSettingsActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.settings.IconPersonalizedActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.quickstep.interaction.GestureSandboxActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.quickstep.interaction.AllSetActivity'
adb shell am start -n 'com.motorola.launcher3/com.android.launcher3.discovery.DiscoverySettingActivity'
adb shell am start -n 'com.motorola.lifetimedata/.ui.TmoCallTimerActivity'
adb shell am start -n 'com.motorola.lifetimedata/.ui.UscCallTimerActivity'
adb shell am start -n 'com.motorola.lifetimedata/.ui.TmoDataCounterActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.desktop.AboutActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.MainActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.DesktopActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.audio.MediaOutputRouteActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.desktop.tile.TileActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.desktop.RequestPermissionActivity'
adb shell am start -n 'com.motorola.mobiledesktop.core/.desktop.tutorial.TutorialActivity'
adb shell am start -n 'com.motorola.motcameradesktop/.SettingsActivity'
adb shell am start -n 'com.motorola.motcameradesktop/.webcam.WebcamActivity'
adb shell am start -n 'com.motorola.motcameradesktop/.PhoneTutorialActivity'
adb shell am start -n 'com.motorola.motcameradesktop/.webcam.WebcamTutorialActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.assist.ui.screens.MainActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motorefresh.feature.herocontent.MotoHeroActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motorefresh.feature.bubblehint.ui.BubbleHintActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motorefresh.feature.settings.SettingsCardActivity'
adb shell am start -n 'com.motorola.moto/.mototips.features.settingscard.card.RazrCardActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motolove.settingscard.SettingsCardActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.family.presentation.FamilyActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motolove.wallpaperhub.presentation.WallpaperHubActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.mototips.showtips.presentation.ShowTipsActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motolove.wallpaperhub.presentation.MyPhotosActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.ttm.PermissionActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.styletransfer.ui.download.DownloadDialogActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.family.presentation.PersonalizeFamilyActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.motoegg.presentation.CreditsActivity'
adb shell am start -n 'com.motorola.moto/com.motorola.mototips.widget.WidgetNotificationContainerActivity'
adb shell am start -n 'com.motorola.motocit/.AppMainActivity'
adb shell am start -n 'com.motorola.motocit/.EarpieceActivity'
adb shell am start -n 'com.motorola.motocit/.LDAActivity'
adb shell am start -n 'com.motorola.motocit/.MTFActivity'
adb shell am start -n 'com.motorola.motocit/.desense.OffenderActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.AutoCalibrationActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.DualRubberTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.PerformanceTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.SelfTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.SPMTActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g5.G5DualRubberSPMTActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g5.G5PerformanceTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g5.G5SelfTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g5.G5SPMTActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g6x.G6XPerformanceTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g6x.G6XSelfTestActivity'
adb shell am start -n 'com.motorola.motocit/.goodix.g6x.G6XSPMTActivity'
adb shell am start -n 'com.motorola.motodisplay/.moto.learnmore.view.LearnMoreActivity'
adb shell am start -n 'com.motorola.motodisplay/.moto.homesettings.view.SettingsRouterActivity'
adb shell am start -n 'com.motorola.motodisplay/.moto.homesettings.view.HomeSettingsActivity'
adb shell am start -n 'com.motorola.motodisplay/.folio.moto.settings.view.FolioSettingsActivity'
adb shell am start -n 'com.motorola.mototour/.presentation.main.TourMainActivity'
adb shell am start -n 'com.motorola.mototour/.bubblehint.BubbleHintActivity'
adb shell am start -n 'com.motorola.msimsettings/.MainActivity'
adb shell am start -n 'com.motorola.msimsettings/.activities.DefaultDataSimActivity'
adb shell am start -n 'com.motorola.msimsettings/.activities.SimDialogActivity'
adb shell am start -n 'com.motorola.msimsettings/.activities.SimCustomizationActivity'
adb shell am start -n 'com.motorola.msimsettings/.assistant.dds.dialogs.DdsAssistantDialogActivity'
adb shell am start -n 'com.motorola.msimsettings/.assistant.dds.dialogs.CustomizeTimeActivity'
adb shell am start -n 'com.motorola.nfc/.setup.NfcSetupActivity'
adb shell am start -n 'com.motorola.nfwlocationattribution/.MotoLocationAccessActivity'
adb shell am start -n 'com.motorola.personalize/.app.sound.SoundActivity'
adb shell am start -n 'com.motorola.personalize/.app.StylesActivity'
adb shell am start -n 'com.motorola.personalize/com.android.wallpaper.ThemesMainActivity'
adb shell am start -n 'com.motorola.personalize/.app.sound.RingtonePickerActivity'
adb shell am start -n 'com.motorola.personalize/com.android.wallpaper.ThemeEditActivity'
adb shell am start -n 'com.motorola.personalize/.app.IconPacksActivity'
adb shell am start -n 'com.motorola.photoeditor/com.android.gallery3d.filtershow.FilterShowActivity'
adb shell am start -n 'com.motorola.photoeditor/com.android.gallery3d.filtershow.FilterShowLayerActivity'
adb shell am start -n 'com.motorola.photoeditor/com.android.gallery3d.filtershow.FilterShowPortraitActivity'
adb shell am start -n 'com.motorola.screenshoteditor/.MainActivity'
adb shell am start -n 'com.motorola.settings/.UpdatePreferencesActivity'
adb shell am start -n 'com.motorola.settings/.CarrierLegalActivity'
adb shell am start -n 'com.motorola.setup/.MotoCRMOptInActivity'
adb shell am start -n 'com.motorola.setup/.DummyFrpCheckActivity'
adb shell am start -n 'com.motorola.setup/.MotoNavIntroActivity'
adb shell am start -n 'com.motorola.setup/.MotoNavGoBackActivity'
adb shell am start -n 'com.motorola.setup/.MotoNavGoHomeActivity'
adb shell am start -n 'com.motorola.setup/.MotoOptInActivity'
adb shell am start -n 'com.motorola.setup/.AmxDeviceProvisioningActivity'
adb shell am start -n 'com.motorola.setup/.MotoCPFActivity'
adb shell am start -n 'com.motorola.setup/.VzwMotoOptInActivity'
adb shell am start -n 'com.motorola.setup/.MotoEmailOptinActivity'
adb shell am start -n 'com.motorola.setup/.MotoNewCRMOptInActivity'
adb shell am start -n 'com.motorola.setup/.startup.CpuIdleWaitActivity'
adb shell am start -n 'com.motorola.setup/.MotoSimCheckActivity'
adb shell am start -n 'com.motorola.setup/.MotoNavSwitchAppsActivity'
adb shell am start -n 'com.motorola.setup/.MotoDataEnrichActivity'
adb shell am start -n 'com.motorola.setup/.AmxOptInActivity'
adb shell am start -n 'com.motorola.setup/.MotoDTWelcomeActivity'
adb shell am start -n 'com.motorola.setup/.VFDummySetupActivity'
adb shell am start -n 'com.motorola.setup/.MotoPushOptinActivity'
adb shell am start -n 'com.motorola.setup/.DummySearchActivity'
adb shell am start -n 'com.motorola.spectrum.setup.extensions/.SpectrumConnectionActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.trackpad.TrackpadActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.taskbar.bar.ExternalModeChooserActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.taskbar.onboard.OnBoardActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.taskbar.recent.RecentsActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.taskbar.settings.SettingsActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.taskbar.settings.MobileUiSettingsActivity'
adb shell am start -n 'com.motorola.systemui.desk/com.motorola.taskbar.ModeChooserActivity'
adb shell am start -n 'com.motorola.timeweatherwidget/com.motorola.commandcenter.weather.WeatherActivity'
adb shell am start -n 'com.motorola.timeweatherwidget/com.motorola.commandcenter.weather.settings.ClockSettingActivity'
adb shell am start -n 'com.motorola.timeweatherwidget/com.motorola.commandcenter.weather.settings.WeatherSettingActivity'
adb shell am start -n 'com.motorola.timeweatherwidget/com.motorola.commandcenter.weather.settings.WidgetSettingsActivity'
adb shell am start -n 'com.orange.aura.oobe/com.ironsource.aura.ams.PreInstallDialogActivity'
adb shell am start -n 'com.orange.aura.oobe/com.ironsource.aura.ams.EndCardDialogActivity'
adb shell am start -n 'com.orange.aura.oobe/com.ironsource.appmanager.ui.activities.LauncherPostOOBEActivity'
adb shell am start -n 'com.orange.aura.oobe/com.ironsource.appmanager.app_launcher.AppLauncherActivity'
adb shell am start -n 'com.orange.aura.oobe/com.ironsource.appmanager.application_settings.ApplicationSettingsActivity'
adb shell am start -n 'com.orange.aura.oobe/com.ironsource.appmanager.application_settings.app_details_screen.view.ApplicationDetailsActivity'
adb shell am start -n 'com.orange.update/.DashboardActivity'
adb shell am start -n 'com.orange.update/com.google.android.gms.tagmanager.TagManagerPreviewActivity'
```

## Important developer messages is under systemapps, app info and notifications settings

## Pull all default ringtones and wallpapers

```bash
adb pull /system/product/media
```

## Pull all pre-configured settings for device

```bash
adb  pull /system/product
```

## Pull all default installed system apps

```bash
pullapks() {
	mustbeinnormalmode
	line='..............................................'
	printf "Please enter path to store the apk files in, path: "
	read storagepath
	echo ""
	mkdir -p $storagepath
	cd $storagepath
	printf "%61s\n" | tr ' ' '='
	printf "Pulling applications installed from playstore..........[\e[0;33mWAIT\e[0m]\n"
	printf "%61s\n" | tr ' ' '='

	for package in $(adb shell pm list packages | tr -d '\r' | sed 's/package://g'); do
		apk=$(adb shell pm path $package | tr -d '\r' | sed 's/package://g' | cut -d\/ -f4 | cut -d- -f1)
		apk_real=$(adb shell pm path $package | tr -d '\r' | sed 's/package://g')
		printf "Pulling: $apk"
		adb pull -p $apk_real "$package".apk &>/dev/null
		printf "%s%s[\e[1;32mDONE\e[0m]\n" "${line:${#apk}}"
	done
	PCKS="$(adb shell pm list packages | tr -d '\r' | sed 's/package://g' | wc -l)"
	printf "%61s\n" | tr ' ' '='
	printf "Pulled $PCKS apk packages from your device................[\e[1;32mDONE\e[0m]\n"
	printf "%61s\n" | tr ' ' '='
	exit
}
```

## Backup getprop 

```bash
adb shell getprop > ~/motorola/getprop
```

## Backup settings from global, secure and system

```bash
#!/bin/bash
20230213_114801.png
mkdir -p ~/motorola/settings/
for settings in global secure system; do
  adb shell settings list ${settings} > ~/motorola/settings/${settings}.log
done
```



## Backup dumpsys

```bash
adb shell dumpsys > ~/motorola/dumpsys.log
```

## Backup all available cmd commands on device

```bash
mkdir -p ~/motorola/cmd/valid-commmands
adb shell 'mkdir -p /sdcard/motorola/cmd/valid-commmands'
adb shell 'cmd -l > /sdcard/motorola/cmd/cmd-output.log'

adb shell '
    cmd -l |sed 's/^  //g' > /sdcard/cmd-output.log
	while read commands; do 
		cmd -w ${commands} 
	done < /sdcard/cmd-output.log > /sdcard/motorola/cmd/valid-commmands/${commands}.txt'
adb pull  /sdcard/motorola/cmd/valid-commmands ~/motorola/cmd/valid-commmands
```

## Backup all available activitys we can launch from commandline

```bash
#!/bin/bash
# Author: wuseman

adb shell
for packages in $(cmd package list packages|awk -F':' '{print $2}'|sort); do
    	dumpsys package ${packages} \
    	|grep -Eo "^[[:space:]]+[0-9a-f]+[[:space:]]+${packages}/[^[:space:]]+Activity" \
    	|grep -io com.* \
    	|sed "s/^/adb shell am start -n '/g" \
    	|sed "s/$/'/g" \
    	|awk '!seen[$0]++'
done >  ~/sdcard/all-available-activity.log
exit
adb shell 'cat /sdcard/all-available-activity.log' > ~/motorola/all-available-activity.log
adb shell rm /sdcard/all-available-activity.log
```



## Set pin entry

```bash
com.android.settings/com.android.settings.password.SetupChooseLockPassword
```




## Unlock with your fingerprint activity

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218433868-0e0c5e43-7f45-4e68-b784-1692b089d720.png" />

```bash
com.android.settings/com.android.settings.biometrics.fingerprint.SetupFingerprintEnrollIntroduction
```

## Find the sensor window

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218434214-a319849b-d8cc-4fa5-9021-da495b626ef5.png" />

```bash
com.android.settings/com.android.settings.biometrics.fingerprint.SetupFingerprintEnrollFindSensor
```


## Touch and Fit window

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218435042-58ce3053-63bf-4042-8f38-c9f5f6769ee1.png" />

```bash
com.android.settings/com.android.settings.biometrics.fingerprint.SetupFingerprintEnrollEnrolling
```



## Fingerprint added window

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218435117-8e7df3ed-0eaf-4e8d-b16a-5294bd57dfe2.png" />


```bash
com.android.settings/com.android.settings.biometrics.fingerprint.SetupFingerprintEnrollFinish
```

## Continue setup window? 

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218435250-8e04d061-76aa-4e9b-b6f9-bb021c8be099.png" />


## Allow wireless debbuging on this network window

```bash
adb shell am start com.android.systemui/com.android.systemui.wifi.WifiDebuggingActivity
```



## Android intelligence search window

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218437959-cab85ba5-b094-4649-a04f-bac2d3f536ca.png" />

```bash
com.android.settings.intelligence/com.android.settings.intelligence.search.SearchActivity
```



## Confirm lockscreen password for OEM unlock

* Allowed to take screenshot here but the screenshot will be all black

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218437839-26268872-9427-4491-87eb-719514ab52e4.png" />

```bash
com.android.settings/com.android.settings.password.ConfirmLockPassword
```

## Security settings and manually pressing passlock

* Allowed to take screenshot here but the screenshot will be all black

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218437839-26268872-9427-4491-87eb-719514ab52e4.png" />


```bash
com.android.settings/com.android.settings.password.ConfirmLockPassword$InternalActivity
```

## Fingerprint settings

<img width="220px" src="https://user-images.githubusercontent.com/26827453/218437714-622b5008-c38b-4dfa-8068-b28cd72e28cf.png" />


```bash
com.android.settings/com.android.settings.biometrics.fingerprint.FingerprintSettings
```


## Systme update from Motorola OTA Windwo

```bash
com.motorola.ccc.ota/com.motorola.ccc.ota.ui.SettingsActivity

```



## Erase all data (factory reset) window

```bash
com.android.settings/com.android.settings.Settings$FactoryResetActivity
```



##

```bash
com.android.settings/com.android.settings.development.AppPicker
```



## WHen trying to launch developmentsettings dashboard following message appear

```bash
adb shell am start -n 'com.android.settings/.Settings$DevelopmentSettingsDashboardActivity'
Starting: Intent { cmp=com.android.settings/.Settings }
Warning: Activity not started, intent has been delivered to currently running top-most instance.
```

And if we trying again

```bash
adb shell am start -n 'com.android.settings/.Settings$DevelopmentSettingsDashboardActivity'
Starting: Intent { cmp=com.android.settings/.Settings }
Warning: Activity not started, its current task has been brought to the front
```



## Another thing that is not giving us properly access to developer console, when we trying to launch with the command below we gonna get message that we must enable developer mode before we can launch it, as you see developer mode has been enabled

```bash
adb shell am start -n 'com.android.settings/.development.DevelopmentSettingsDisabledActivity'
```



## Launch screen recordin dialog

```bash
com.android.systemui/com.android.systemui.screenrecord.ScreenRecordDialog
```


## Launch fingerprint activity (works on samsung as well) you can type:

am start -n 'com.android.settings/.biometrics.fingerprint.FingerprintEnrollSuggestionActivity'

and you will be able to enter fingerprint directly









# I learned this during this week

1) New ways from commandline to set FPR enable/disable by read the source code from android developers which I have never seen before in the source code.

```bash

```

2) To learn how to bypass motorola but also samsung because of this and how entire internet is using old methods that is not available anymore. You all probably that is interested of adb have seen all websites (all?) that is writing about this using the same methods, for example this is for samsung that people still writing about I have seen few weeks ago like it works but it does NOT:

This is just a random picked source that is providing this info, even XDA developers on the forum typing about this it is not possible anymore:

https://drfone.wondershare.com/bypass-google-lock/adb-frp.html

```bash
adb shell am start -n com.google.android.gsf.login/
adb shell am start -n com.google.android.gsf.login.LoginActivity
adb shell content insert --uri content://settings/secure --bind name:s:user_setup_complete --bind value:s:1
```

Crazy, they also doing this as a buisness and this is simply wrong and RLY old, I already know these are not working since many years but I never get deeper into this part earlier but during this week I figure out how this can be done instead and this is not included in this readme it will be added to my docu instead im just mentioning it for myself what this device was my reward for spend my time on this device

![](https://i.imgur.com/4UpNPCF.png)

The third command works and is still an option:

```bash
adb shell content read –uri content://settings/secure/ –bind name:s:user_setup_complete –bind value:s:1

```

We can confirm this by using content and query the setting as

![20230214_131522](https://user-images.githubusercontent.com/26827453/218736043-15deb55c-d00a-40bf-8fb9-f2e23964383b.png)

Alright, but how do we set FRP enable or disable? That´s what ive learned.. And you can do this by set a secure seting that is not visible/avasilable in the source where the old way is below the way i found as can be seen here:

```
        /**
         * Indicates whether the device is under restricted secure FRP mode.
         * Secure FRP mode is enabled when the device is under FRP. On solving of FRP challenge,
         * device is removed from this mode.
         * <p>
         * Type: int (0 for false, 1 for true)
         */
        @Readable
        public static final String SECURE_FRP_MODE = "secure_frp_mode";

        /**
         * Indicates whether the current user has completed setup via the setup wizard.
         * <p>
         * Type: int (0 for false, 1 for true)
         *
         * @hide
         */
        @SystemApi
        @Readable
        public static final String USER_SETUP_COMPLETE = "user_setup_complete"
```

And if we look at source code for locksettings, we can read this:

```bash
    private void enforceFrpResolved() {
        final ContentResolver cr = mContext.getContentResolver();
        final boolean inSetupWizard = mInjector.settingsSecureGetInt(cr,
                Settings.Secure.USER_SETUP_COMPLETE, 0, UserHandle.USER_SYSTEM) == 0;
        final boolean secureFrp = mInjector.settingsSecureGetInt(cr,
                Settings.Secure.SECURE_FRP_MODE, 0, UserHandle.USER_SYSTEM) == 1;
        if (inSetupWizard && secureFrp) {
            throw new SecurityException("Cannot change credential in SUW while factory reset"
                    + " protection is not resolved yet");
        }
    }

```

So no matter if it would be possible to run that adb command or not when we are in SUW it will reply with: Cannot change credential in SUW while factory reset"

And I can confirm this after going deeper in this topic by trying this when I figure out how to get the adb shell access in this picture by trying the old method and the encforceFrpResolved will not allow this :

![20230214_135041](https://user-images.githubusercontent.com/26827453/218744360-5354bc04-dff7-40c6-8980-2ec89e8d4ca1.png)

![](https://i.imgur.com/emL5gIv.png)


