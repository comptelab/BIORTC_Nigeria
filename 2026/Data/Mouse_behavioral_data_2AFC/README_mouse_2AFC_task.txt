2AFC Behavioral Dataset

Overview
This file contains behavioral data from an auditory two-alternative forced-choice (2AFC) task performed by multiple mice across multiple experimental sessions.
Each row corresponds to a single trial. The dataset includes stimulus information, the animal's choice and outcome, reaction time, and the timing of all left and right licking events recorded during the trial.
 
Data organization
Each row represents one behavioral trial.
Trials from different mice and sessions are concatenated into a single table. The combination of Subject, SessionIndex, and Trial uniquely identifies each trial.
 
Variables
Trial
Sequential trial number within the session.
Side
Correct stimulus side.
•	0: Left
•	1: Right
Hit
Behavioral outcome.
•	1: Correct response
•	0: Incorrect response
•	NaN (if present): no valid choice or omitted trial
Choice
Animal's reported choice.
•	0: Left
•	1: Right
ILD
Interaural Level Difference (dB) used as the auditory stimulus.
Negative values favor the left side, whereas positive values favor the right side. Larger absolute values correspond to easier discriminations.
Subject
Unique identifier for the mouse.
SessionIndex
Session number for the corresponding subject.
 
Licking behavior
LicksLeft
List containing the timestamps (in seconds) of all left-port licks detected during the trial.
LicksRight
List containing the timestamps (in seconds) of all right-port licks detected during the trial.
The timestamps are stored as Python-style lists.
 
Lick count variables
nLicksLeft
Total number of left licks during the trial.
nLicksRight
Total number of right licks during the trial.
nLicks
Total number of licks during the trial:
nLicks = nLicksLeft + nLicksRight
 
Inter-lick intervals
leftILI
Mean inter-lick interval (seconds) computed from left licks only.
Undefined (NaN) when fewer than two left licks occur.
rightILI
Mean inter-lick interval (seconds) computed from right licks only.
Undefined (NaN) when fewer than two right licks occur.
ILI
Mean inter-lick interval across all consecutive licks during the trial.
 
Reaction time
RT
Reaction time (seconds), measured from Go cue onset to the animal's first lick.


