# HARQ-Soft-Combining-Using-BiLSTMs

[Adithya S Ubaradka](https://github.com/AdiPadi2703)&nbsp;&nbsp;&nbsp;&nbsp;[Hemang J Jamadagni](https://github.com/Kazedaa)&nbsp;&nbsp;&nbsp;&nbsp;[Rohit Sunil](https://github.com/rohitsunil1102)<br>


## Abstract

Hybrid Automatic Repeat reQuest (HARQ) is used in modern wireless data communication to integrate both Automatic Repeat reQuest (ARQ) and high-rate Forward Error
Correction (FEC) mechanisms to enhance the reliability of data transmission. Unlike traditional ARQ, where an error-ridden frame is discarded upon reception, HARQ temporarily
stores the erroneous frame in a buffer. When the re-transmission of the same frame occurs,
these two frames are combined to generate a new frame, trying to minimize errors. This is
HARQ with Soft Combining. Existing methods like Chase Combining (Type-I) and Incremental Redundancy (Type-II and Type-III) implement log-likelihood Ratio and Maximum
Ratio Combining (MRC) to combine two erroneous frames. This project uses a Bidirectional
Long Short-Term Memory (BiLSTM) model to combine two frames with high channel noise
errors. This project aims to introduce the BiLSTM model, which aims to reduce the Bit Error
Rate (BER) and provide an approach for integrating this model into the existing HARQ
structure.

## Overview of the Proposed Methodology

We use a BiLSTM-based model because of its ability to preserve information over extended temporal context and its ability to handle dynamic fluctuations.  Furthermore, the bidirectional feature of the BiLSTM allows for the utilization of both past and future information.<br><br>

The integration of this model with the existing HARQ architecture has also been considered in our work, by simply adding the model to the Soft Combining step of the process.  In the case where errors in a packet are detected (using Checksum or Cyclic Redundancy Check), the request for a second transmission is made.  Upon receiving the second packet, two packets are passed into the model, thus performing the Soft Combining step.

![ProposedArchitecture](https://github.com/AdiPadi2703/HARQ-Soft-Combining-Using-BiLSTMs/assets/120291477/4f3e122a-9aa5-4b8a-87d0-9f7bdb0f4821)


## Dataset Used

We used a custom dataset consisting of messages, each of 4 bytes consisting of randomly generated integers between 0 and 255 (inclusive).  Four instances of the model were taken to train on four different high-order modulation techniques (QAM-16, PAM-16, PSK-16, and ASK-16).  These modulation techniques were implemented using the <a href="https://github.com/rwnobrega/komm">komm</a> library.  The modulated signal goes through an Additive White Gaussian Noise (AWGN) channel, which is then demodulated back to a digital signal. This is done twice to get two noised frames of the same data for Soft Combining.

## Analysis of Results

For the analysis of the model's performance, we used the Bit Error Rate (BER) and its variation with the SNR.  The training was done on an SNR of 2dB.


## Note from the Authors
The paper has been accepted for oral presentation at the SSWC2024 which is scheduled towards the end of November. Therefore, we have not included the model architecture and other novel ideas discussed in the paper. For further clarification, please raise an issue or contact any of the authors.

Link to the Conference: [International Conference on Smart Systems and Wireless Communication(SSWC2024)](https://www.jiscollege.ac.in/sswc2024/)
