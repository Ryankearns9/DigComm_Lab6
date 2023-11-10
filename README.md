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

