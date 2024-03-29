# Kippykip-2009
 Resources typically used for making Kippykip-2009 video effects.
 
 For audio bitcrushing there's a few methods, the easiest is just straight up exporting low HZ audio from movie maker. It'll upscale it in a "nearest neighbour" fashion but for audio.
 You can achieve the same with sndrec32, by opening wav audio and going File>Properties>Convert Now...>Attributes>44.100 kHz, 16 Bit, Stereo
 
 Another method using Audacity is to copy the script contents of audacity_bitcrush_v4.ny.txt into Tools>Nyquist Prompt. Uncomment the ; on the conversion rate you want to use to whatever the sourcerate of your loaded audio is then hit OK.  
 (For example, if you want to upscale audio from 22050 to 44100) then change this line:  
 ;(setq factor 2) ;22050hz -> 44100hz  
 To this:  
 (setq factor 2) ;22050hz -> 44100hz  
 
 Hit ok, then on the top left side of the audio layer, click the dropdown arrow>Rate>44100 Hz.
 Special thanks to SteveDaulton for writing this updated script!
 
 There's also the older version 3 audacity script. It works pretty much the same but instead change the "sourcerate" variable (which is set to 4000 in the file)
 to whatever the sourcerate of your loaded audio is. Tick "Use legacy (version 3) syntax." if you have the option and hit OK.
 
 If successful, your low hz audio should play in a bitcrushed fashion similar to how Windows XP Movie Maker / Sound Recorder handled it.  
 
UPDATE: I have been informed that Windows Movie Maker XP doesn't render the scrolling text on Windows 10 (and any project that uses it can’t be exported). I now have Windows 10 and found that if you right click on Windows Movie Maker 2.6>Properties>Compatibility>Run this program in compatibility mode for>Windows XP (Service Pack 2), it should work fine again. - Tested on Windows 10 Enterprise 2016 LTSB X64
 
[**Download Archive**](https://github.com/Kippykip/Kippykip-2009/archive/master.zip)
