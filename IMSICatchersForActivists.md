
#IMSI Catchers: Practical Knowledge for Activists 


_"Not on the phone"_   --Stringer Bell 
:no_mobile_phones:

## Introduction

Activists on the streets face a multitude of threats of State repression ranging from surveillance, arrest, and physical violence at minimum. Technology tools by themselves will not reduce this State power but tools used as part of a _security culture_ can make an impact.  There already exist a few excellent guides [0] on cell phones knowledge for activists. However this short guide will specifically explore IMSI catchers [1], their capabilities, as well as some practical counter-surveillance measure. Sections that are technical, but not required reading, will be marked with a asterisks at the start of the paragraph for optional reading

### GSM Technology

*****Your phone (MS) connects to a cell phone tower [2]. In order to preserve battery life, it will by design pick the strongest broadcasting tower in your area. When the connection occurs, you connect to a a base transceiver station (BTS) and multiple BTS create a general location area code (LAC).  The BTS your phone connects to determines a large amount of the capabilities of your connection: is it encrypted or not, how is it encrypted, is it 2G/3G etc. So when your phone (MS) makes the _first_ connection to your phone a large amount of information about your phone is handed off.  The information that is handed off could uniquely places activists at demonstrations, which is the _largest_ concern for activists who wish to remain anonymous.

### Phones

_Phones_ _are_ _tracking_ _devices_ (NEVER forget this fact!) Your phone will routinely ping your location to a BTS and records of your physical location will be stored in a database somewhere. (Activists should consider leaving their phones at home if you don't want your location tracked). However to uniquely identify your phone, you need a few key bits of information:
	
	* IMSI    -- International Mobile Subscriber Number
	* IMEI    -- Cellphone hardware's unique identifier
	* MSISDN  -- Phone number 

### IMSI Catchers and their capabilities

When your phone connects to a new BTS for the first time, the IMSI that uniquely identifies your phone is broadcast to the BTS. Because IMSIs so uniquely identify a phone, a temporary id (TMSI) is generated for most actual uses.  The first connection is what gets exploited by IMSI Catchers. IMSI Catchers work by broadcasting as a fake cell tower and tricking your phone into handing your IMSI over to it. [3] There are also two modes that Stingrays (a trademarked type of IMSI Catcher) can operate in; a passive and active mode. In the active mode, a phone is constantly ping'ed and tracked. In an active attack, the phone will broadcast its location at its full power output which will present as very high battery drain. Passive attackers are much harder to detect because they may be present for weeks or months at a time (say outside of a foreign embassy). Passive mode are more interested in profiling information, namely phone routing information or "metadata" about who was dialing who, duration of calls etc.) A passive attacker could survey andarea and dump all phone records in an area into a database. I suspect that IMSI Catchers in passive mode are used at demonstrations to map social networks. That way the police can tell *who* might have been in the area for intelligence gathering. There also exist so called "hybrid" modes which mix these two properties.  

For 2G, IMSI Catchers (depending on the model/manufacturer) can capture your dialed numbers, _content_ of your calls / SMS, metadata, and SMS information can be intercepted and in, some models, content can be modified in real time. PDF pg 7 [4] For 3G and LTE, there is an additional authentication mechanism [5] so content interception isn't possible but IMSI Catching still works. It is also possible to "jam" 3G broadcasting to force your phone to use 2G, so called downgrade attacks. (There are other attacks to break GSM encryption for 3G/LTE [6])

tl;dr IMSI catchers uniquely identify *your* phone number 

### Symptoms of IMSI Catchers

Some symptoms of IMSI Catchers are: 
	
	* Very high battery drain (phone transmits at full power) but see notes below
	* Denial of Service (phone can't connect at all without rebooting)
	* Downgrade attacks (3G goes down with 2G only available
	* Rapidly changing LAC / BTS / Tx & Rx

Note to activists:
	
	* Very high battery drain is expected if you're at a demonstration and tweeting / taking pictures etc. 
	* It can also be congestion due to close proximity to each other and hitting the same BTS
	* Every truck parked near a demonstration isn't an IMSI Catcher. 
	* Every time your applications won't open doesn't mean you're being tracked.
	* Be cautious but not paranoid ;-)

### Counter-Surveillance

A small list of counter-surveillance that activists can do on the ground include: 
	
	* Look for amberjack antennas [7][8] 
	* Turn phone off
	* SnoopSnitch (Android)
	* AIMSICD (Android)
	* Firechat or PirateBox (WiFi only communication)
	* End-To-End Encryption

#### Android 

There exist two good projects for detecting IMSI catchers for Android: SnoopSnitch [9] and AIMSICD[10]. Snoop Snitch is particularly promising because many of the low-level GSM controls (like AT commands) are hidden away in the proprietary baseband. Some clever engineering by experts in the field allowed them to pull the information into an easy-to-use application.  The code is open-source and provides a very good look into how IMSI Catchers work in the wild. The application also detects SS7 attacks which are outside the focus this article. Snoop Snitch is available in the Android Store [11] for devices which have Qualcomm basebands.

AIMSICD is another promising application in active development. A coupe of nice features include a local database backup of events that occur in your area for later analysis, an easy to use UI and color coded threat levels. In my own experience, I turn on the application as I walk around town and have passively mapped most of the topography of GSM towers in the city. This baseline is important for when fake towers emerge and disappear quickly. You can download the APK here [12]

#### End-To-End Encryption

"Properly implemented strong crypto systems are one of the few things that you can rely on". While cryptography can be relied upon to protect your content, the GSM model is badly broken in many ways. IMSI catchers can still uniquely identify your phone but to protect from _eavesdropping_ you can use SMS encryption with Signal [13] for Android or iOS [15]. Phone calls can be encrypted using Signal as well for either platform. These are free, open-source applications that allow users to communicate with very user friendly applications. 

### Trade-Offs

The downside to these applications (SnoopSnitch and AIMSICD) is that they require very low-level access to your cellphone. SnoopSnitch also requires a rooted Android phone.  If you're not comfortable with that being the case, you can purchase a low-cost Moto E for $100 USD and use it as a testing device (with the added benefit that your everyday phone number isn't attached to demonstrations). Purchase the Moto E and a pre-paid SIM card with cash and register a new Google Account (not linked to your *real* idenity). 

Another trade-off with Snoop Snitch is that it will send traffic back to SDR Labs to help build a database of SS7/IMSI Catcher attacks. You may not want this.  

Is this all worth it? I'd argue that IMSI Catchers posses a real threat to anonymous political speech. There is evidence of coordinated crackdown on protests in the last few years [16][17] and see a very real need to update our threat models. We know in the past that IMSI Catchers were deployed on US soil [18] against protesters in 2003 and local police are only getting more money from DHS under "counter terrorism" grants. It has also been widely reported that IMSI Catchers have been found at demonstrations in Egypt, Germany, Ukraine, etc.

```
Sources:

[0] https://www.eff.org/deeplinks/2014/08/cell-phone-guide-protesters-updated-2014-edition
[1] https://en.wikipedia.org/wiki/IMSI-catcher
[2] https://imgur.com/YOl0lVj
[3] http://arstechnica.com/tech-policy/2013/09/meet-the-machines-that-steal-your-phones-data/	
[4] http://www.shoc.ch/downloads.html?file=files/shoc/pdf/go2SIGNALS%20Brochures/go2INTERCEPT_V1.0_E_2013-10-31.pdf 
[5] https://imgur.com/ooeS6Lk
[6] https://twitter.com/matthew_d_green/status/533401814696484865
[7] http://cdn.arstechnica.net/wp-content/uploads/2013/09/amberjack_2-300x526.jpg
[8] http://www.austinchronicle.com/binary/1a71/pols_feature31.jpg
[9] https://opensource.srlabs.de/projects/snoopsnitch
[10] https://secupwn.github.io/Android-IMSI-Catcher-Detector/
[11] https://play.google.com/store/apps/details?id=de.srlabs.snoopsnitch
[12] https://github.com/SecUpwN/Android-IMSI-Catcher-Detector/releases
[13] https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms&hl=en
[14] https://play.google.com/store/apps/details?id=org.thoughtcrime.redphone&hl=en
[15] https://itunes.apple.com/us/app/signal-private-messenger/id874139669?mt=8
[16] http://www.theguardian.com/commentisfree/2012/dec/29/fbi-coordinated-crackdown-occupy
[17] http://www.justiceonline.org/fbi_files_ows
[18] http://dbapress.com/wp-content/uploads/2014/10/DBA-Forbidden-Knowledge-Stingray-July-2014.pdf
```
