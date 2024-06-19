# simulation


#
# Handover Success Rate: Measures how often handovers are successfully predicted and executed.
# Handover Failure Rate: Measures the rate of incorrect handover predictions.
# Handover Frequency Rate: Measures how often handovers are happening over time.
# Handover Detection Time: Estimates the time required to detect and execute a handover based on UE speed and channel conditions.


Handover Success Rate (HO_Success_Rate):
Definition: The ratio of successful handovers to the total number of handovers attempted.
Calculation:
HO Success Rate
=
Number of successful handovers
Total number of handovers attempted
HO Success Rate= 
Total number of handovers attempted
Number of successful handovers
HO_success_rate = (true & (true == pred)).sum() / len(true) if len(true) > 0 else 0
This calculates the proportion of handovers that were correctly predicted by the model out of all handover attempts.

Handover Failure Rate (HO_Failure_Rate):
Definition: The ratio of failed handovers to the total number of handovers attempted.
Calculation:
HO Failure Rate
=
Number of failed handovers
Total number of handovers attempted
HO Failure Rate= 
Total number of handovers attempted
Number of failed handovers

HO_failure_rate = (true & (true != pred)).sum() / len(true) if len(true) > 0 else 0
This calculates the proportion of handovers that were incorrectly predicted by the model out of all handover attempts.
Handover Frequency Rate (HO_Frequency_Rate):

Definition: The rate at which handovers occur per unit time.
Calculation:
HO Frequency Rate
=
Total number of handovers
Total simulation time
HO Frequency Rate= 
Total simulation time
Total number of handovers
​
 

HO_frequency_rate = UE_i_HO_Executed.sum() / max_sim_time
This calculates how frequently handovers are executed over the total simulation time.
Handover Detection Time (HO_Detection_Time):

Definition: The time taken to detect and execute a handover.
Calculation:
This is represented by N_training in the code, which is calculated based on user equipment (UE) speed and channel coherence time.

HO_detection_time = N_training  # Simplified for this example
This simplifies the detection time as N_training which is determined from:

average_UE_speed = 1000. * simulation_data['Distance'].mean() / max_sim_time
T_coherence = np.ceil(average_UE_speed / c * f_mmWave)
N_training = int(min(T_coherence, r_training * max_sim_time))
