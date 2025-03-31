# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To implement Pulse Code Modulation (PCM) for encoding and decoding a sinusoidal signal using quantization and to observe the output waveforms.

# SOFTWARE REQUIRED
1. Python Software
-> Numpy Library

-> Matplotlib Library

-> Scipy Library (for signal processing
# ALGORITHMS
1. Generate a sinusoidal signal.
2. Sample the signal at a fixed rate.
3. Quantize the sampled values to the nearest discrete level.
4. Convert the quantized values into binary (encoding).
5. Decode the binary data back into quantized values.
6. Reconstruct the signal from the quantized values.
7. Plot the original, sampled, quantized, and reconstructed signals.
# PROGRAM
import numpy as np

sampling_rate = 5000  

frequency = 50 

duration = 0.1  

quantization_levels = 16 

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))  

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels

quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step

pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)

plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')

plt.title("Message Signal (Analog)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 2)

plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')

plt.title("Clock Signal (Increased Frequency)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")


plt.grid(True)

plt.subplot(4, 1, 3)

plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')

plt.title("PCM Modulated Signal (Quantized)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 4)

plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')

plt.title("Signal Without Demodulation")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.tight_layout()

plt.show()

# OUTPUT
![Screenshot 2025-03-31 204547](https://github.com/user-attachments/assets/d4be2e28-5878-4104-b5f1-6885de9762ab)
![Screenshot 2025-03-31 204608](https://github.com/user-attachments/assets/8e7b00ce-80fc-4ca6-ba01-b3fec81b1a20)
 
# RESULT / CONCLUSIONS
The PCM encoding process successfully quantized the original sine wave into 16 levels.

The demodulated signal closely resembled the original signal with minor quantization noise.

The output waveforms validated the functioning of PCM in digital communication systems.
