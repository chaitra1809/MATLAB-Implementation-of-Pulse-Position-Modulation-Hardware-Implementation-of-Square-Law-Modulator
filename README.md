# MATLAB-Implementation-of-Pulse-Position-Modulation-Hardware-Implementation-of-Square-Law-Modulator


# Introduction:

	Pulse Modulation:
•	Transmits analog information by sampling continuous waveforms at regular intervals.
•	Information transmitted only at sampling times with synchronizing signals.
•	Original waveforms can be reconstituted from sample information at receiving end.

	Pulse Modulation types:
•	Analog: sample amplitude is the variable.
•	Digital: information is a code.

	Pulse Position Modulation (PPM): A method of Pulse Time Modulation
	PPM: 
•	Generated by changing pulse position in a fixed time slot.
•	Amplitude and width of pulses kept constant, position varies.

	PPM advantages:
•	Constant transmitter power output.
•	Bandwidth efficiency.

	PPM disadvantage: requires transmitter-receiver synchronization.

	PPM obtained from Pulse Width Modulation (PWM).

	PPM used in:
•	Wireless communication systems. 
•	Optical communication systems. 
•	Efficient data transmission over RF channels and fiber optic cables. 
•	High-speed data transmission with noise tolerance.

# Mathlab code:

fc = 4000; 

fm = 200;

Ac = 1;

Am=1;

t_end = 0.01; 

fs = 10*fc;

t = 0:1/fs:t_end;

V_carrier = Ac* sawtooth(2*pi*fc*t);

V_mod = Am * sin(2*pi*fm*t);

V_pwm = (V_mod > V_carrier);

figure; 

subplot(3,1,1); 

plot(t, V_carrier); 

xlabel('Time (s)');

ylabel('Amplitude (V)'); 

title('Carrier Signal');

subplot(3,1,2);

plot(t, V_mod); 

xlabel('Time (s)');

ylabel('Amplitude (V)');

title(' Modulated Signal'); 

subplot(3,1,3);

plot(t, V_pwm); 

xlabel('Time (s)');

ylabel('Amplitude (V)'); 

title('PWM Signal');

ylim([-0.1 1.1]);

pulse_width = 0.0001;

pwm_edges = find(diff(V_pwm) == 1);

ppm_positions = t(pwm_edges);

V_ppm=zeros(size(t));

for i = 1:length(ppm_positions)

start_idx = round(ppm_positions(i)*fs) + 1;

end_idx = round((ppm_positions(i) + pulse_width)*fs);

end_idx = min(end_idx, length(V_ppm)); 

V_ppm(start_idx:end_idx)=1;

end

figure;

subplot(3,1,1);

plot(t, V_ppm); 

xlabel('Time (s)');

ylabel('Amplitude (V)'); 

title('PPM Signal');


![image](https://github.com/user-attachments/assets/4931f591-2533-43b8-b3c3-203f728a3130)


# Result:
The experiment on Pulse Position Modulation (PPM) achieved successful generation and transmission of PPM signals. 
The signals were transmitted over a wireless communication channel and received with minimal distortion, demonstrating the technique's potential for reliable communication. 


# Hardware Implementation

# Square Law Modulator:

# Introduction:

Modulation is a fundamental technique in communication systems that involves altering a carrier signal's properties to encode information for transmission. It allows data to be transmitted efficiently over different media, such as radio waves, by varying one or more of the carrier signal's attributes, including amplitude, frequency, and phase. Modulation enables the transmission of digital or analog information over long distances while mitigating issues like interference and signal degradation.

A Square Law Modulator is a type of modulator used in analog communication systems to generate amplitude modulation (AM) signals. It operates based on the non-linear relationship between the input signal's amplitude and the output signal's power. In a square law modulator, the input signal is multiplied by itself, resulting in an output signal that contains both the original signal's frequency components and additional frequency components due to the nonlinear multiplication.

 The key characteristics of a Square Law Modulator include:
 
 1. Nonlinear Operation: The multiplication process introduces nonlinearity, causing the output to contain sum and difference frequency components. 

2. AM Signal Generation: The modulator inherently generates amplitude modulation (AM) signals. The added frequency components carry the amplitude-modulated information.

3. Efficiency: Square law modulators are efficient in generating AM signals since the modulation process doesn't involve complex mathematical operations. 

4. Non-Idealities: While useful for generating AM signals, square law modulators can introduce unwanted distortion and harmonics due to their nonlinear behavior. 

5. Envelope Detection: Square law modulators are also utilized in envelope detection circuits, where the nonlinear operation is exploited to recover the envelope of an amplitude-modulated signal

# Circuit Diagram:
![image](https://github.com/user-attachments/assets/4371d5b1-142b-43d5-8794-399fc6d59853)

# Design:

Designing a complete modulation and demodulation system using a Square Law Modulator and an Envelope Detector involves integrating both components to transmit and recover a modulated signal. Here's a simplified description of the process:

 Modulation using Square Law Modulator:
 
 1. Message Signal Source (Vin): Generate or provide the message signal that you want to modulate. This could be an audio signal or any analog signal you want to transmit.

2. Carrier Signal Source (Vc): Generate a high-frequency carrier signal that will be modulated with the message signal. This could be a sinusoidal waveform.

3. Square Law Modulator Circuit: Construct the Square Law Modulator circuit, as described previously, to mix the message signal with the carrier signal using the nonlinearity of the diode. 

4. Output (Vmod): The output of the Square Law Modulator is the modulated signal (AM signal). It carries the information from the message signal within the variations of its amplitude.

# Result:
![image](https://github.com/user-attachments/assets/ae6d3a85-e41e-4e15-a1a9-ea92d038518f)

![image](https://github.com/user-attachments/assets/cf1dde2b-96ac-4d32-afa8-d66fce033d7d)
