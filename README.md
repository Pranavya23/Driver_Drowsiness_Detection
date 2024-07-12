# Driver_Drowsiness_Detection
Implemention of drowsiness detection using eye aspect ratio (EAR)

# Motivation
Drowsy drivers are one of the main factors leading to road accidents. According to a report by the Ministry of Road Transport and  Highways Transport Research Wing, road accidents claimed 1,53,972 lives and harmed 3,84,448 people in 2021. NHTSA’s census of fatal crashes and estimate of traffic-related crashes and injuries rely on police and hospital reports to determine the incidence of drowsy-driving crashes. By leveraging the power of computer vision and machine learning, my project aims to provide a real-time alert system to detect early signs of drowsiness in drivers and warn them before it leads to dangerous situations.
Reference:
1. https://timesofindia.indiatimes.com/auto/policy-and-industry/driver-fatigue-led-road-accidents-approaches-india-could-take-to-prevent-these/articleshow/97048300.cms
2. https://www.nhtsa.gov/risky-driving/drowsy-driving
3. https://www.emro.who.int/emhj-volume-28-2022/volume-28-issue-9/risk-assessment-of-road-traffic-accidents-related-to-sleepiness-during-driving-a-systematic-review.html

# Features
1. Real-Time Detection: Monitors driver's eyes in real-time using a webcam.
2. Eye Aspect Ratio (EAR): Calculates the EAR to determine if the driver is alert, drowsy, or asleep.
3. Normalization: Captures initial frames to calculate a baseline EAR for personalized and accurate detection.
4. Auditory Alerts: Plays an alarm sound if the driver is detected as drowsy or asleep.

# Description of the project
  Initially, the system captures the first 20 frames of the video stream to calculate a baseline Eye Aspect Ratio (EAR) for the driver. This normalization process ensures personalized and accurate detection by accounting for individual differences in eye shape and size. The EAR is calculated by measuring the vertical and horizontal distances between specific points around the eyes. This baseline EAR serves as a reference for determining the driver's level of alertness.

  During real-time monitoring, the system continuously captures video frames and converts them to grayscale for efficient processing. It detects faces in the frame using dlib's pre-trained face detector and then identifies facial landmarks to locate the eyes. The EAR is calculated for both eyes, and the system determines whether the eyes are open, drowsy, or closed by comparing the current EAR with the baseline EAR. The system increments counters based on the blink state to track how long the driver has been in each state.

  If the driver is detected as drowsy or asleep for more than a specified number of frames, the system triggers an auditory alarm. This alarm plays a specific sound file up to 30 times to ensure the driver's attention is captured. The alarm mechanism uses a separate thread to play the sound, ensuring that the main video processing loop is not interrupted. The system continues to monitor the driver's state and resets the alarm counter when the driver returns to an active state.
