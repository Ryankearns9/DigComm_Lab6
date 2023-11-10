# Lab 6

## Introduction
TODO

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

