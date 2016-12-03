# MindMyMind

## WHO
![image](https://github.com/HackTheBrain/MindMyMind/blob/master/images/MMM1.jpg)

- Boris van Schooten – Developer – Roessingh Research and Development http://www.rrd.nlwww.rrd.nl, Enschede, the Netherlands
- Dennis Hofs - Developer – Roessingh Research and Development http://www.rrd.nl, Enschede, the Netherlands
- Dora Kotsi-Felici – Artist – http://www.theodorakotsi.com/
- Hossein Nassabi – Researcher – University of Twente http:www.utwente.nl, Enschede, the Netherlands
- Wendy Oude Nijeweme – d’Hollosy - University of Twente http://www.utwente.nl, Enschede, the Netherlands

Boris, Dennis, Hossein and Wendy were sent to the HtB2016 to represent the Center for Monitoring and Coaching https://www.utwente.nl/ctit/cmc/. None of the team members had prior experience with EEG signals and BCI technologies. Therefore, this project was started from scratch on the first day, June 24th 2016.

## WHY
Although the team had no experience with BCI, there were certainly some ideas among the team members to work on during the weekend. The main common factor in the ideas was giving people self- reflection on their real mind state. Sometimes people don’t know (or cannot express) their real feelings, or the feelings of the people in their environment. This often leads to miscommunication. MindMyMind can provide a visual, intuitive and easy to interpret picture of a user’s state of mind. It is a very general idea that is applicable to a lot of areas.

Examples are:

Giving persons self-awareness on their real feelings that can lead to a change in perspective.
Coaching programs in eHealth/telemedicine can be extended to incorporate the mind-state of the patient, to tailor-made the coaching strategy based on the patients mood.
Helping the environment of autistic children to show the real emotion of these children, and vice versa, to be able to act on this in the right way.
People with locked-in syndrome can express their feelings.
WHAT
Detection of emotions

EEG signals have been used previously to detect emotions. Different areas of brain can be activated based on the type of the emotion[1]:


Valence: positive emotions result in a higher frontal coherence in alpha, and higher right parietal beta power, compared to negative emotion.
Arousal: excitation presented a higher beta power and coherence in the parietal lobe, plus lower alpha activity.
Dominance: strength of an emotion, which is generally expressed in the EEG as an increase in the beta to alpha activity ratio in the frontal lobe, plus an increase in beta activity at the parietal lobe.

The next model was presented in “Real-Time EEG-Based Human Emotion Recognition and Visualization” in which Valence and Arrousal are presented in a 2D space http://www3.ntu.edu.sg/home/EOSourina/Papers/EmoRecVis2010.pdf

![image](https://github.com/HackTheBrain/MindMyMind/blob/master/images/400px-MMM2.jpg)

In literature there are some discussion on how to divide emotions. For example:

“Firstly, the usefulness of these approaches has been challenged by discrete emotions theorists, such as Silvan Tomkins, Paul Ekman, and Carroll Izard, who argued that the reduction of emotion space to two or three dimensions is extreme and resulting in loss of information. Secondly, while some basic emotions proposed by Ekman, such as happiness or sadness, seem to fit well in the dimensional space, some basic emotions become indistinguishable (e.g., fear and anger), and some emotions may lie outside the space (e.g., surprise). It also remains unclear how to determine the position of other affect-related states such as confusion. Note, however, that arousal and valence are not claimed to be the only dimensions or to be sufficient to differentiate equally between all emotions. Nonetheless, they have proven to be useful in several domains (e.g., affective content analysis as reported by Yang, Lin, Su, & Chen, 2007).”

Regardless of the expressed concerns, the above model still forms the base of our project.

## HOW
Design of the prototype

In our prototype, we would like to map emotions into a valence-arousal plane. Conventionally, the user is exposed to a (visual) stimuli which will lead to voltage changes in the brain. The EEG is recorded from which noise and artifacts are removed. Relevant features are selected from the resulting data based on which a classifier is trained and tested [2].

![image](https://github.com/HackTheBrain/MindMyMind/blob/master/images/500px-MMM3.jpg)

This is where it gets technical. Please describe how you made it (e.g. hardware/software used). Reference to code/patches/data can also be made through linking to github or similar. In the developed prototype, we skip the classifier training step due to time constraints. As such, we detect and visualize changes to brain activities which may imply changes to the state-of-mind of the user. The emotion-detection will be left as future work. We use 10 electrodes to detect the changes in the alpha and beta brain waves. The architecture of the HtB2016 prototype will exist of the following elements:

![image](https://github.com/HackTheBrain/MindMyMind/blob/master/images/700px-MMM4.jpg)


Approach and division of tasks

We used the TMSi Mobita [3]as the equipment for measuring the EEG signals.

![img](https://github.com/HackTheBrain/MindMyMind/blob/master/images/400px-Screenshot_2016-07-13_01.35.34.png)

The following channels were used:

![img](https://github.com/HackTheBrain/MindMyMind/blob/master/images/400px-Screenshot_2016-07-13_01.35.50.png)

The electrodes that were used for Alpha and Beta wavebands are as follows:

Alpha:
Left: F7, F3, and Fp1,
Right: F8, F4, and Fp2
Left Power minus Right Power -> Valence is normalized between [-1, 1]
Beta:
AFZ, Fz, and Cz
Mean power -> Arousal is normalized between [0-1]
The asymmetrical frontal EEG activity may reflect the valence level of emotion experienced. Generally, right hemisphere is more active during the experience of negative emotions while left hemisphere is more active during positive emotions5. Therefore we calculated the power of signals from left hemisphere minus right hemisphere to calculate valence is our prototype.

The tasks in the team were divided as follows:

![imge](https://github.com/HackTheBrain/MindMyMind/blob/master/images/400px-Screenshot 2016-07-13 01.36.13.png)
**Boris**
Has set up the TMSi Mobita and collected data. He installed the software on his computer and did some experiences with it. Unfortunately, installing the software took a lot of time. He coded the signal processing, and this code can be found (later on) on the WIKI-page. Buffer BCI -> raw data out of the Morbita sent to a Java application (Signal Analyzer). This application analysis the signal. See architecture figure. Through a socket this information is send to the MMM webservice.

![imgage45](https://github.com/HackTheBrain/MindMyMind/blob/master/images/400px-Screenshot 2016-07-13 01.36.26.png)
**Dora**
Helped Hossein and Wendy in the research on EEG and BCI and emotion detection. Furthermore, she esigned the MMM avatar in LightWay and made a MP4 movie that could be used by Dennis.


![imgage3](https://github.com/HackTheBrain/MindMyMind/blob/master/images/400px-Screenshot_2016-07-13_01.36.35.png)
**Dennis**
Received data and created the real-time visualization by setting up a web service. He used HTML5 to play the video, Javascript for speeding the animation, and CSS for the color overlay. Also this code can be found (later on) on the WIKI- page.

**Hossein and Wendy**
Worked on the research and documentation, and found many papers usable for this project.
