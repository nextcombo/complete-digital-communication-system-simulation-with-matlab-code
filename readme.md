# Complete Digital Communication System Simulation [with MATLAB Code]

Simulation Technology:  
Source Coding: Huffman encoding  
Channel Coding: Convolutional encoding  
Modulation: Amplitude Shift Keying (ASK), and Phase Shift Keying (PSK) modulation  
Channel: Additive White Gaussian Noise Channel  
Demodulation: ASK and PSK demodulation  
Channel Decoding: Viterbi decoding  
Source Decoding: Huffman decoding  
Simulation Parameters:  
Simulation Results:  
Code Exhibition:
clc, clear, close all; \nstart = tic; \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                         "System Properties"                         %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\nmodulation_name = 'BPSK'; \nsamples_per_bit = 40; \nRb = 1000; \namp = [1 0];\nfreq = 1000;                         \nsnr = 10; \nGenerator = [1 1 1; 1 0 1]; \nshift = 1; \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                      "Reading Text Data File"                       %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Reading data: '); \nfile = fopen('Data/source_data.txt');\ntext = fread(file, '*char')';\nfclose(file);\ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                         "Source Statistics"                         %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\nfprintf('Source statistics: '); \ntic\n[unique_symbol, probability] = source_statistics(text); \ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                         "Huffman Encoding"                          %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\nfprintf('Huffman encoding: '); \ntic \ncode_word = huffman_encoding(probability); \ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                         "Stream Generator"                          %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Stream generator: '); \nbit_stream = stream_generator(unique_symbol, code_word, text);\ninput = bit_stream;\ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                          "Channel Coding"                           %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Channel coding: '); \n\nchannel_coded = convolutional_coding(bit_stream, Generator);\ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                            "Modulation"                             %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Modulation: ');\nmodulated = modulation(modulation_name, channel_coded, Rb, samples_per_bit, amp, freq); \ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                              "Channel"                              %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Channel: ');\nreceived = awgn_channel(modulated, snr); \ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                           "Demodulation"                            %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Demodulation: ');\nbit_stream = demodulation(modulation_name, received, Rb, samples_per_bit, amp, freq);\ntoc\n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                         "Channel Decoding"                          %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Channel decoding: ');\nbit_stream = viterbi_decoder(bit_stream, Generator, shift); \noutput = bit_stream; \ntoc\n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                         "Huffman Decoding"                          %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Huffman decoding: ');\ndecoded_msg = huffman_decoding(unique_symbol, code_word, bit_stream); \ntoc \n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                    "Writting the Received Data"                     %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\ntic\nfprintf('Writing data: ');\nf = fopen('Data/received.txt','w+');\nfprintf(f, decoded_msg);\nfclose(f);\ntoc\n\n\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\n%%%                     "Time & Error Calculation"                      %%%\n%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%\nfprintf('Total execution time: ');\ntoc(start); \n\nError = sum(abs(input - output)); \ndisp(['Total Bit Error: ' num2str(Error)]);\n  

## Images

![(Digital Communication)Complete Digital Communication System Simulation [with MATLAB Code]](01.jpg)
![(Digital Communication)Complete Digital Communication System Simulation [with MATLAB Code]](02.jpg)
![(Digital Communication)Complete Digital Communication System Simulation [with MATLAB Code]](03.jpg)
![(Digital Communication)Complete Digital Communication System Simulation [with MATLAB Code]](04.jpg)
![(Digital Communication)Complete Digital Communication System Simulation [with MATLAB Code]](05.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
