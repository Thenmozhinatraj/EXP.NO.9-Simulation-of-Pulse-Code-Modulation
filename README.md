# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To implement Pulse Code Modulation (PCM) using Python to generate, sample, quantize, and visualize an analog signal.

# SOFTWARE REQUIRED
- Python 3.x
- NumPy library
- Matplotlib library

# ALGORITHMS
1. Generate an analog message signal (sine wave) with a specified frequency and duration.
2. Create a clock signal for sampling.
3. Quantize the sampled signal into discrete levels.
4. Perform PCM modulation by encoding the quantized values.
5. Visualize the message signal, clock signal, PCM modulated signal, and demodulated signal.

# PROGRAM
import numpy as np

import matplotlib.pyplot as plt

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

plt.plot(t, message_signal, color='blue')

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 2)

plt.plot(t, clock_signal, color='green')

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 3)

plt.step(t, quantized_signal, color='red')

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 4)

plt.plot(t, quantized_signal, color='purple', linestyle='--')

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.tight_layout()

plt.show()


# OUTPUT
![Screenshot 2025-03-23 142244](https://github.com/user-attachments/assets/939e6780-8703-4f9d-b256-5ae948eb816e)
![Screenshot 2025-03-23 142303](https://github.com/user-attachments/assets/c77ee3c3-cbc6-46e3-b095-bcdc3c9012f8)

 
# RESULT / CONCLUSIONS
The experiment successfully demonstrated PCM (Pulse Code Modulation).

Higher quantization levels improve signal approximation.

Efficient clock synchronization and sufficient sampling rate are essential for accurate signal reconstruction.
