"Removing COVID-19 from the earth is, in principle, quite easy. All we need to do is to have the - still relatively few - people infected, stop infecting new people. The surprise is that achieving this might not require any mass surveillance. Just a free app, with absolutely no impact on most users' life. An app that nobody should be shy to ask their friends to install before visiting. This is the idea of the AVICOT-APP." Sune Mai

# Can we stop COVID-19 using Bluetooth?
Dear reader, please help me evaluate the ideas outlined below. I believe it might be possible to develop these concepts into a GDPR conforming mobile phone app and a WHO organized global data-server solution. And, that the combination of these has the potential to stop both COVID-19, and other deadly virus epidemics in general - without compromising personal data security. 

There are two challenges to face in this plan. One is about technology, and the other is about public awareness, information and education. We shall primarily deal with the technology part here, although the latter challenge is probably going to be the most difficult.

I hereby ask you to link and share this with anybody you think could contribute in evaluating and implementing the idea. We really don’t have a lot of time to get this done.

## Interview-based contact tracking and quarantining 
An important, and very efficient, part of the current intensive effort being made by medical authorities worldwide, is contact tracking: For each known infected person, the task is to identify anybody that may have had exposure to the virus, and to put those in any real risk into quarantine.

In cases where the infected person has mostly been close to well-known contacts like family, friends and colleagues, the tracking is straight forward. In others, e.g. if the infected person has been to a public concert or has spent a long time in public transportation, the task can be almost impossible, because nobody knows the identity of the potentially infected people. 

When identifying and assessing the risk of all contacts is possible, however, the method is extremely effective. But it also requires large resources and qualified medical staff, making global scaling unrealistic. Furthermore, it can easily be to slow, in the sense that the virus infection may already have taken another leap or two, before the quarantining is established.

## Technology and Privacy - the General Data Protection Regulation
Any technological solution that tries to mimic the contact tracking performed by medical authorities will automatically break GDPR. Or will it really? 

What if we turn the contact tracking and quarantining concept upside down, and rephrase it like this: Every responsible human being should be interested in knowing if he or she presents a non-negligible virus threat to family, friends, colleagues and thus – ultimately – society in general. 

With proper advice; self-quarantining, or just infection awareness, would reduce the transmission probability markedly. Thus, nobody needs to be identifiable or trackable in any way for the concept to work. But anyone advised by an app that they are realistically in some danger, would probably choose to seek medical advice in any case – and hopefully by phone.

If we can provide an automatic, app-based solution that gives the relevant info free of cost, free from commercials, using little mobile data bandwidth and battery,  and with full anonymity and control of shared personal data – then why would anybody not want to have this app permanently running? And maybe a valid app-installation with 14 days of contact tracking log-file could even be made mandatory for participating in all large public events, e.g. like the Olympics? 

This is the overall concept and scale of ambition for the AVICOT-APP described below. The exact technology used to get there doesn’t really matter much, as long as it works. But since the time-budget is limited we’d better try to use an existing technology. One option is Bluetooth. 

## Bluetooth scanning
Even without establishing a full connection (or “pairing”) of two Bluetooth devices, one can still probe the Bluetooth addresses of nearby devices. You can easily verify this as follows: If you put your own phone into “visible mode”, and start a Bluetooth scanning app on another, you will, after 12-15 sec scanning, get a list of all nearby Bluetooth devices - including the address of your own. The unique Bluetooth address is the main ID we are interested in, while the Radio Signal Strength Indicator (RSSI) parameter gives an estimate of proximity, which correlates with the infection risk.

The relation between RSSI and distance depends on many factors, including the presence of metal objects nearby and the relative orientation of the two devices – the literature on the subject is large. From a simple electromagnetic radiation perspective, however, it should be clear that the highest values of RSSI correspond well with immediate physical proximity of the devices.

The technology has been used before, e.g. for traffic measurements in Australia, where Bluetooth IDs of car-drivers’ electronic gadgets were logged from roadside scanners in order to determine transit times on a road [1]. 

## Anonymous Virus Contact Tracking – the AVICOT protocol
Consider a mobile phone AVICOT-APP that does the following:
1.	Every 10 minutes, referred to absolute UTC time, it enables Bluetooth and visibility of the phone for 15 sec. 
2.	During these 15 sec, a scan of nearby Bluetooth devices is performed. The result is stored in a timestamped log of (ID, RSSI) pairs locally on the phone. The log is time-limited to cover only entries from the last, say, 20 days. Any ID appearing often, or with high RSSI, represents a likely “contact” in the sense of contact tracking and quarantining. But no sharing or uploading of this data occurs.  
3.	Regularly, e.g. every 6 hours, the AVICOT-APP checks the public “COVID-19 level 0” list on a WHO-organized AVICOT-SERVER. Entries in this are Bluetooth IDs of devices owned/used by officially diagnosed COVID-19 cases, who have given their consent to this publication. The list may be regionally organized, to limit mobile data requirements.
4.	In the rare case that a match is found between an ID in the local log, and the official level 0 list, it most likely means that within the last 20 days, the phone has been in the vicinity of the now diagnosed, and possibly unrelated COVID-19 patient. To assess if this should have consequences in the form of medical advice to the owner, the timestamps, IDs and RSSI values corresponding to the recorded matches is uploaded to the AVICOT-SERVER. Notice that this transfer should be covered by the consent already described in point 3. The server then evaluates the data with an algorithm designed to estimate the infection risk. 
5.	If the AVICOT-SERVER responds to the upload with a message of non-negligible increased infection risk, this information is conveyed to the user of the AVICOT-APP along with suitable explanation of what action to take. 
6.	Step 5 may also prompt the user to give consent to uploading the phones own Bluetooth ID to a “COVID-19 level 1” list, containing IDs of devices belonging to people who might be infected, and thus generalizing the general concept to multiple stages of contact tracking. 

There are many issues to consider in the above, both technical and use related:  

There may be a technical challenge having multiple Bluetooth devices doing a synchronized scan? In this case an alternative scanning protocol should be considered - e.g. based on randomization of scan start time?

Maybe a coarse position should be included when reporting back a match, in order to detect and prevent false input data to the AVICOT-SERVER “COVID-19 level 1” (or higher) lists? 

Is a 6 hour polling interval suitable? Or should the polling be performed more often for the small “COVID-19 level 0” list, while keeping the interval fixed for polling of higher level lists, which will be much larger. 

The battery life of devices should be taken into account – is 10 minute intervals to large or small considering the trade-offs?

To me, the most important aspect is that this concept may be useful in all areas of the world, even where mobile phone bandwidth is limited and unstable.  And if the AVICOT-APP implementation is made completely free, also from adds, and is sufficiently anonymous, I see no reason why this could not become a global solution to both the current COVID-19 outbreak – and also any future epidemic. 

## Roadmap and collaboration
To organize inputs, I’ve setup an initial team and a documentation repository at
 https://github.com/AVICOT-APP

In the Documentation repository, I would like to gather your input for public sharing under creative commons CC0-1.0 license. This will most likely be a quite dynamic and agile roadmap, depending on what issues turn up in the feedback.

If the project does take off on a large scale, I intend to hand-off the organizational responsibility to e.g. the WHO or the national (danish) health authorities, in case it is easier to build a test-case in national scale. Until further notice, however, I will try to organize the input into the Documentation repository.

The following is the initial roadmap suggestion for the first few steps:
1.	Evaluate the technical challenges of the ID logging. Without this, we can’t go further - unless an alternative technological solution, meeting the same overall goals, should come up.
2.	Evaluate the legal details. I’m not an expert on GDPR, or legal issues in general, so we need to check if the local storage of Bluetooth IDs in the log is legal.
3.	Evaluate the licensing terms of the current project. My main concern in releasing the concept at this very early stage is that some patent-troll (individual or company) may solve a really trivial technical challenge in getting the synchronized logging to work – and thus delay the process and limit the scope of the project. 
4.	If the above points are ok, we should immediately start development of an AVICOT-APP, drawing relevant industrial partners into the project. A first issue to consider is whether the log-file can be started by an initial AVICOT-APP v0.1, having only logging capability – and then being continued without any data loss with each subsequent release. 
5.	Finally, we should evaluate if the protocol should stay at “COVID-19 level 0” list, or we should include the higher level into the specification. In this part we should also consider additional privacy issues, since users eligible for being on the COVID-19 level N>0 list, might opt not to if they risk “shaming” issues. I.e., we don’t want any hotels or restaurants to actively check and exclude anybody on the N>0 list.

Further steps are many, of course, but I believe the above is more than enough for now. 

If you are interested in participating, please send me your details and background, and I shall include you into the project. 

Best regards

Sune Mai, March 2nd, 2020 

sunemai@hotmail.com

[1] Jard, Meaad & Shah, H. & Bhaskar, Ashish. (2013). Empirical evaluation of Bluetooth and Wifi scanning for road transport.
