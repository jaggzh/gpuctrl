# gpuctrl - RISKY GPU power and fan management

<div align="center">
  <em>Quick Status</em><br>
  <img src="i/ss-status.png"><br>
</div>

<div align="center">
  <em>Set Watts Limit</em><br>
  <img src="i/ss-watts-limit.png"><br>
</div>

## The Requisite WARNING:

*Manipulating your fans, and maybe your power, **might** be risky. If you're overriding the GPU fan speed, YOU ARE PREVENTING NVidia from deciding on its [imo] way-too-relaxed fan.

## Dear Google, Can a gpu overheating (by fixing your fan speed to 0%) cause a fire?

>Strictly speaking, yes, a GPU overheating can theoretically cause a fire. However, it is highly unlikely. Modern graphics cards are specifically designed with safeguards to prevent catastrophic heat-related failures. [1, 2, 3, 4]  

>Built-in Safeguards 

>• Thermal Throttling: If a GPU gets too hot (usually around 80°C to 85°C), it will automatically slow itself down to reduce heat. 
>• Emergency Shutdown: If the temperature reaches dangerous, critical levels (often around 100°C+), the PC will hard-lock or shut down entirely to protect itself. [1, 3, 5, 6, 7]  

>What Happens When Fans Are Fixed at 0% 

>Fixing your fan speed to 0% while running heavy tasks or playing games will lead to rapid thermal throttling and system crashes. Over time, prolonged exposure to extreme heat can degrade the card's components, including its thermal pads and paste. [1, 3, 5, 6, 8]  

>The Real Fire Hazards 

>When a GPU-related fire does occur, it is rarely caused by the silicon chip itself. Instead, it is usually caused by: 

>1. Faulty Connectors: Melted or poorly seated power cables (like the 12VHPWR connectors) causing an electrical arc. 
>2. Short Circuits: Defective power delivery components (VRMs or MOSFETs) failing under load. 
>3. Power Supply Issues: A low-quality power supply (PSU) failing to cut power during a hardware short. [9, 10, 11]  

>How to Stay Safe 

>• Manage Fan Curves: Use trusted software like MSI Afterburner to set a safe, automatic fan curve rather than a fixed 0%. 
>• Check Cables: Ensure all power cables are firmly pushed all the way into the GPU so no pins are exposed or loose. 
>• Monitor Temps: Keep an eye on your hardware temperatures using monitoring tools like  HWiNFO . [8, 11, 12, 13]  

>...

>AI can make mistakes, so double-check responses

[1] https://www.youtube.com/shorts/NZTva-MWrKw
[2] https://www.reddit.com/r/EtherMining/comments/6k2sgq/when_will_my_fan_break_will_my_gpu_catch_fire/
[3] https://www.reddit.com/r/pcgaming/comments/2stlbt/why_is_overheating_bad_for_a_gpuwhat_does_it_do/
[4] https://www.quora.com/Can-overheating-your-GPU-cause-shutdown
[5] https://www.instagram.com/reel/DQVoPRkERJb/
[6] https://www.quora.com/Can-overheating-damage-GPU
[7] https://www.quora.com/Can-gaming-at-high-settings-make-a-GPU-overheat
[8] https://www.facebook.com/groups/pcbuilderandsetups/posts/1038240971309276/
[9] https://www.facebook.com/groups/PcBuildersCommunity/posts/3346846875598670/
[10] https://forums.anandtech.com/threads/we-all-know-a-video-card-can-catch-fire-but-can-it.2491237/
[11] https://www.youtube.com/shorts/Gpg8hIg-85A
[12] https://www.quora.com/Will-Running-My-Graphics-Card-At-100-Fan-Speed-Damage-It
[13] https://www.youtube.com/shorts/FLsj1009Q2o


***SET A FIXED FAN SPEED AT YOUR OWN RISK.***

***Using this software is dangerous and, by using this, you are accepting all liability, and you release me of all liability, up to and including damage to your hardware, starting a fire.*** **And starting a fire could kill someone, so do not  and that may obviously ruining your relationship, etc.***

## **Supports symlinks:** gpufans, gpustop

## sudo / root / x11

I don't have a Wayland system to work with. But controlling the GPU settings requires both *root* AND *X11 access*. Thus, we go through some elaborate detection of your X11 session information needed so, when we sudo, we'll "just work". Hopefully.

My GPU was *hot*, but I'd have wanted my fan on higher. However, with my miscellaneous electronics work I.. I don't know. I just like keeping them below "burn my fingers". (I think that's about  ~44°C / 112°F).

I'd be okay with my fan kicking in and speeding up faster. Unfortunately, there apparently isn't a way to just increase the eagerness of the GPU's fan use.

Controlling this through software is *not* ideal. Now, perhaps I'm naive, but I *have* had my system lock up and my GPU continuing. I'd like it if the hardware were not relying on software for this.

Nevertheless, I wanted to set my *max GPU power (watts)*.

<div align="center">
  <em>Overkill convenient CLI controls</em><br>
  <img src="i/ss-help.png"><br>
</div>

## Not intended as a replacement / Alternatives:

*It didn't mean anything!*

Okay, this is **not intended** as a replacement for these scripts/daemons that I have no experience with. *[Summaries from Google AI]*:

- [**coolgpus:**](https://github.com/andyljones/coolgpus) A specialized Python tool built specifically for headless Linux servers. It continuously reads your GPU core temperature and applies a linear or piecewise-linear fan curve. You can launch it via a simple terminal command like: `sudo coolgpus --temp 20 55 80 --speed 5 30 99`
- [**gpufanctl:**](https://github.com/gmbeard/gpufanctl) A lightweight background service (daemon) written for Linux. It monitors temperature thresholds in the background and scales fan percentages up or down automatically.
- (**nvfancontrol:**](https://github.com/foucault/nvfancontrol) A high-performance utility written in Rust. It hooks directly into the NVIDIA driver to adjust individual fans dynamically based on precise temperature response curves.

## Emergency Safety Mode

Running `gpuctrl` without args will go into an "emergency" low-power high-fan mode.

<div align="center">
  <em>Set Watts Limit</em><br>
  <img src="i/ss-stop.png"><br>
</div>

## Switch to NVidia's Auto / Defaults:

<div align="center">
  <em>Go back to GPU's defaults</em><br>
  <img src="i/ss-auto.png"><br>
</div>
