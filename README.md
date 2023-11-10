# Lab 6

## Introduction
Noise is an unvoidable part of the signal processing chain that must be accounted for. This lab explores the effects of that noise including how to measure it and how it affects our 
signals. A large part of a communication engineer's job is how to reduce that noise and how to minimize the effects it has on our signal.

## Hardware
1. Emona TIMS Online Freeware (https://www.emona-tims.com/emona-product/nettims-freewire/)

## SNR and Eye Diagrams
### Questions
The below questions are posed by the Emona Instruments labs. Answer correspond to the related question.

#### Question 1
Looking at the below image of the max noise scenerio we can make an educated guess on the noise type. It appears that the noise evenly distributed across frequencies therefore, it is white noise. We can further take note that the amplitudes of the noise appear to have variance but remain around a center amplitude. Therefore, this is white gaussian noise

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/SNR_Eye/Part1_0db_fft.png)

#### Question 2
Looking at the three plots below, we can determine which of the generators outputs creates the most noise. The first plot is the -20dB case. The second plot is the -6dB case. Finally, the third plot is the 0dB case. From this, we can infer that the 0dB case outputs the most noise.

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/SNR_Eye/Part1_0db.png)

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/SNR_Eye/Part1_6db.png)

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/SNR_Eye/Part1.png)

#### Question 3
To understand why we aren't as noisy, it is helpful to look at the FFT plot of the 0db case. The below image shows the FFT plot. If we compare it to the graph in Question1, we notice that the out-of-band noise is extremely attenuated. In the time domain, all of this noise is added together. Therefore, by filtering we removed much of this out-of-band noise

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/SNR_Eye/Part2_BPF_0db_fft.png)

#### Question 4
Without an RMS voltage measurement device, I was forced to use the Vpp for this part. We assume that Vrms is equivalent to $Vpp/(2 \sqrt{2})$

Source (https://3roam.com/vpp-to-vrms-calculator/)

| Measurement            | Vpp          | Vrms           |
| ----------             |:------------:| :------------: |
| Signal Voltage         | 4.22         | 1.49           |
| Noise Voltage          | 3.18e-3      | 1.10e-3        |
| Signal to Noise Ratio  | N/A          | 1355           |
| SNR (in decibels)      | N/A          | 62.6           |
| Signal + Noise Voltage | N/A          | 1.49           |
| Alternate SNR          | N/A          | 1356           |
| Alternate SNR (in db)  | N/A          | 62.6           |

Note, we round to 3 sigfigs which results in some values appearing unchanged.

The SNR is telling us how many times higher our signal voltage level is to our noise voltage level.

#### Question 5
The SNR in both instances is almost identical because the noise power is so insignificant compared to the signal power. At this amplitude, our signal's power makes the voltage from the noise essentially a rounding error.

#### Question 6
We expect that the SNR in dB will decrease by a relative amount to the amount described by the noise power. As such going from -20dB to -6dB should translate to a decrease of 14dB in our SNR. This should give us a value of about 48.6. Similarly, going to 0dB should give us a value of 42.6dB.

#### Question 7
As stated in Question 6 we expect the table to look as follows if we use 0dB or -6dB.

| Measurement            | Vrms (-6dB)  | Vrms (0dB)     |
| ----------             |:------------:| :------------: |
| Signal Voltage         | 1.49         | 1.49           |
| Noise Voltage          | 5.55e-3      | .011           |
| Signal to Noise Ratio  | 270.9        | 135.5          |
| SNR (in decibels)      | 48.6         | 42.6           |
| Signal + Noise Voltage | 1.49         | 1.50           |
| Alternate SNR          | 270.9        | 136.4          |
| Alternate SNR (in db)  | 48.6         | 42.7           |

Actual measurements for the 0dB case are listed below

| Measurement            | Vpp          | Vrms           |
| ----------             |:------------:| :------------: |
| Signal Voltage         | 4.22         | 1.49           |
| Noise Voltage          | 6.51e-3      | 2.40e-3        |
| Signal to Noise Ratio  | N/A          | 647.8          |
| SNR (in decibels)      | N/A          | 56.2           |
| Signal + Noise Voltage | 4.75         | 1.68           |
| Alternate SNR          | N/A          | 730.4          |
| Alternate SNR (in db)  | N/A          | 57.3           |

#### Question 8
The trigger for the online TimLabs is not reliable enough to form an eye diagram. However, we know from class that noise will significantly degrade the eye.

#### Question 9
As the frequency increases the spacing between the eyes decreases.

## Bit Error Rates

### LPF Response
The below table is the measurements for the LPF characterization
| Freq(Hz)   | Input Voltage  (Vpp) | LPF Voltage (Vpp)    | Gain (dB)      |
| ---------- |:------------: | :------------: | :------------: |
| 10         | 4.00          |   3.52         | -1.11          |
| 50         | 4.00          |   3.52         | -1.11          |
| 100        | 4.00          |   3.52         | -1.11          |
| 500        | 3.99          |   3.46         | -1.24          |
| 1000       | 3.98          |   3.28         | -1.68          |
| 1500       | 3.95          |   2.90         | -2.68          |
| 2000       | 3.78          |   1.99         | -5.57          |
| 2500       | 3.86          |   1.07         | -11.14         |
| 3000       | 3.81          |   0.50         | -17.64         |
| 3500       | 3.73          |   0.24         | -23.83         |


The filter Response can be seen here
![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/BER/LPF_Char/Plot.PNG)

### Questions

#### Question 1
Typically, the 3dB attenuation point is the cutoff frequency for a filter. Therefore, this filter's cutoff frequency can be defined at around 1.6-1.7kHz

#### Question 2
The Pattern can be found below. This shows a 31 bit pattern lasting 14.89ms.

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/BER/pattern_length.PNG)

The lab manual states that the actual bit period length is 15.5ms

#### Question 3
The average is not exactly 0 because there is an odd number of bits (31). This inherently means there will be more of either 1's or 0's. In this case, we can count our bits and see 15 1's and 17 0's resulting in a non-zero voltage.

#### SNR Measurement for 3.5 kHz
| NRZ Voltage   | Noise Voltage | SNR (dB)   |
| ---------- |:------------: | :------------: |
| 1.97         | 1.87          |   0.423         | 

#### Question 4
The reason for the distortion can be seen below in our FFT plot. The signal's side lobes are filtered out resulting in a disruption to our expected sinc function.

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/BER/Question4.PNG)


#### Question 5
We expect the attenuation to exceed 3dB at 1.6kHz. This is because of the work we did previously to tune our LPF. Indeed, this is almost exactly 3dB

![Image](https://github.com/Ryankearns9/DigComm_Lab6/blob/main/imgs/BER/3dB_Point.PNG)

| Ch A Gain   | Ch B Gain | SNR (dB)   |
| ---------- |:------------: | :------------: |
| -13.6         | -16.8          |   3.2         | 

#### Question 6
There are still errors at this point because our filtering is causing significant issues for our amplitudes

#### Question 7
The sample counter is giving roughly the same error every time because it is about a 50% error rate. The error counter is counting for a fixed period of time and outputting roughly 50% error.

#### Question 8
This is creating no errors because we are resetting the sequence generator every time there would be an error. This ultimately results in a synchronized system

#### Question 9
This process of aligning the sequences is known as a phased locked loop. It corrects the phase until the two sequences are aligned

#### Signal Table

| Vrms   | Noise (Vrms) | SNR (dB) |Average Errors    | Error Rate      |
| ---------- |:------------: | :------------: | :------------: | :------------: |
| .58        | .461          | 2.00 | 366          | 43.9e-3         |
| .58         | .245          | 7.50 | 318         | 38.2e-3          |
| .58        | .172          |  10.55 |5         | 6.00e-4          |

#### Signal Table New Eye
| Vrms   | Noise (Vrms) | SNR (dB) |Average Errors    | Error Rate      |
| ---------- |:------------: | :------------: | :------------: | :------------: |
| .58        | .321          | 5.14 | 336          | 40.3e-3         |
| .58         | .114          | 14.13 | 136         | 16.3e-3          |
| .58        | .051          |  21.1 |8         | 9.6e-4          |
'

#### Question 10
As can be seen from the graphs, we need a much better SNR for a good bit error rate if our decision point is not aligned with the eye.

#### Question 11
This occured because the center of the eye is the optimal location to take the measurements. We are at the edge of a bit when taking at a location off from the eye. The bit amplitude is falling as a result of our LPF. This combined with the noise results in a much worse bit error rate