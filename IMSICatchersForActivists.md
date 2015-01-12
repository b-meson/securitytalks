
IMSI Catchers: Practical Knowledge for Activists 
=====

_"Not on the phone"_ --Stringer Bell

Introduction
	Activists on the streets face threats of State repression ranging from surveillance, arrest, physical violence to start. Technology tools by themselves will not reduce this State power but tools used as part of a _security culture_ can make an impact.  There are already a few excellent guides [0] so this short guide will explore IMSI catchers [1], their capabilities, as well as some practical counter surveillance on the streets. Sections that are technical will be marked with a asterisk for optional reading

GSM Technology
	*****Your phone (MS) connects to a cell phone tower [2]. In order to preserve battery life, it will by design pick the strongest broadcasting tower in your area. When the connection occurs, you connect to a a base transceiver station (BTS) and multiple BTS create a general location area code (LAC).  The BTS your phone connects to determines a large amount of the capabilities of your connection: is it encrypted or not, how is it encrypted, is it 2G/3G etc. So when your phone (MS) makes the _first_ connection to your phone a large amount of information about your phone is handed off 
is also uniquely places activists at demonstrations, which is the _largest_ concern for activists who wish tto remain anonymous.

Phones
	_Phone_are_tracking_devices (NEVER forget this fact!) Your phone will routinely ping your location to a BTS and records of your physical location will be stored in a database somewhere. (Activists should consider leaving their phones at home if you don't want your location tracked). However to uniquely identify your phone, you need a few key bits of information:
	
	* IMSI    -- International Mobile Subscriber Number
	* IMEI    -- Cellphone hardware's unique identifier
	* MSISDN  -- Phone number 

IMSI Catchers and their capabilities
	When your phone connects to a new base station (BTS), the IMSI that uniquely identifies your phone is broadcast to the BTS. Because IMSIs so uniquely identify a phone, a temporary id is generated for most actual use (TMSI).  But the first connection is what gets exploited by IMSI Catchers. IMSI Catchers work by broadcasting as a cell tower and tricking your phone into handing your IMSI over to it. [3] There are also two modes that Stingrays (a trademarked type of IMSI Catcher) can operate in; a passive and active mode. In the active mode, a phone is constantly ping'ed and tracked. A passive mode will just survey the area and could dump all phone records in the area into a database. The author suspects that IMSI Catchers in passive mode are used at demonstrations. That way the police can tell *who* might have been in the area for intelligence gathering. This is a cause for immediate concern. 
	For 2G, IMSI Catchers can capture your dialed numbers, _content_ of your calls / SMS, metadata, and SMS information can be intercepted and in, some models, content can be modified in real time. PDF pg 7 [4] For 3G and LTE, there is an additional authentication mechanism [5] so content interception isn't possible but IMSI Catching still works. It is also possible to "jam" 3G broadcasting to force your phone to use 2G. (There are other attacks to break GSM encryption for 3G/LTE [6])

tl;dr IMSI catchers uniquely identify *your* phone 

Symptoms of IMSI Catchers
	* Very high battery drain (phone transmits at full power) {see note 1 below}
	* Denial of Service (phone can't connect at all without rebooting)
	* Downgrade attacks (3G goes down with 2G only available
	* Rapidly changing LAC / BTS / Tx & Rx
	* Note to activists	
		1. Very high battery drain is expected if you're at a demonstration and tweeting / taking pictures etc. It's can also be explained when hundreds of people congregate in close proximity to each other and hit the same BTS
		2. Every truck parked near a demonstration isn't an IMSI Catcher. Every time your applications won't open doesn't mean you're being tracked.
		3. Be cautious but no paranoid ;-)

Counter-Surveillance
	* Look for amberjack antennas [7][8] 
	* Turn phone off
	* SnoopSnitch (Android)
	* AIMSICD (Android)
	* End-To-End Encryption

Android 
	There exist two good projects for detecting IMSI catchers for Android: SnoopSnitch [9] and AIMSICD[10]. Snoop Snitch is particularly promising because many of the low-level GSM controls (like AT commands) are hidden away in the proprietary baseband. Some clever engineering by experts in the field allowed them to pull the information into an easy-to-use application.  The code is open-source and provides a very good look into how IMSI Catchers work in the wild. The application also detects SS7 attacks which are outside the focus this article. Snoop Snitch is available in the Android Store [11] for devices which have Qualcomm basebands.
	AIMSICD is another promising application in active development. A coupe of nice features include a local database backup of events that occur in your area for later analysis, an easy to use UI and color coded threat levels. In my own experience, I turn on the application as I walk around town and have passively mapped most of the topography of GSM towers in the city. This baseline is important for when fake towers emerge and disappear quickly. You can download the APK here [12]

End-To-End Encryption
	"Encryption works. Properly implemented strong crypto systems are one of the few things that you can rely on" Unfortunately the GSM model is badly broken in many ways. IMSI catchers can uniquely identify your phone but to protect from _eavesdropping_ you can use SMS encryption using TextSecure [13] for Android and RedPhone [14] for Android and Signal for iOS [15]. These are  

Trade-Offs
	The downside to these applications is that they require very low-level access to your cellphone. SnoopSnitch also requires a rooted Android phone.  If you're not comfortable with that being the case, you can purchase a Moto E for $100 USD and use it as a testing device (with the added benefit that your everyday phone number isn't attached to demonstrations). Purchase the Moto E and a pre-paid SIM card with cash and register a new Google Account (not linked to your *real* idenity).
Another tradeoff is that Snoop Snitch will send traffic back to SDR Labs to help build a database of SS7/IMSI Catcher attacks. You may not want to be included in this.  
	Is this all worth it? I'd argue that IMSI Catchers posses a real threat to anonymous political speech. There is evidence of coordinated crackdown on protests in the last few years [16][17] and see a very real need to update our threat models. We know in the past that IMSI Catchers were deployed on US soil [18] against protesters (this was in 2003) and of local police are only getting more money from DHS under "counter terrorism" grants.

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
