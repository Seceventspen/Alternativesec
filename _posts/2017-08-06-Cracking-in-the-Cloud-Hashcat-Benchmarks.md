---
layout:     post
title:      Cracking in the Cloud - Hashcat Benchmarks
date:       2017-08-04
author:     SecEventsPen & NR
summary:    Cloud Cracking
categories: Tools
thumbnail:  wrench
tags:
 - 2017
 - Cracking
 - Hashcat
 - Cloud
 - EC2
 - New
 - Benchmarks
 - Nvidia
 - Cuda
 - Tesla K80 GPUs
---

This post is going to be more results/statistics based, providing context to the benchmark tests myself and Nick carried out! It will cover the Benchmarks that we obtained from Hashcat, once we had completed the EC2 Kali instance set-up. The original post covering this can be found here, [Cracking in the Cloud with Hashcat](https://www.alternativesec.xyz/tools/2017/08/04/Cracking-In-The-Cloud-With-Hashcat/)

Here's a quick review of what was used for our Cloud Cracking Instance:

```nohighlight
AMI: Offensive Security Kali Instance
EC2 Instance Type: p2.8xlarge
GPU: 8 x Tesla K80
```

![GPU](/images/AWS/teslak801.jpg)

The benchmark we initiated ran through pretty much everything that Hashcat is able to handle, so this took a while! It is worth keeping in mind the following when trying to make sense of the benchmark output:

```nohiglight
H/s == Hashes per second
KH/s == Kilohashes per second (Thousands of hashes per second)
MH/s == Megahashes per second (Millions of hashes per second)
```

***Note: When running the Benchmark test, we did encounter a ‘Cuda Compatibility’ error which outputted on the terminal screen; however, the benchmark completed successfully. We are still looking into what the exact compatibility error is. Though as previously mentioned this did not seem to adversely affect Hashcats operation and Benchmarking using the Tesla K80 GPUs***

Here's a full list and breakdown of the individual Hash formats that Hashcat can handle and the results produced by each of the eight (8) Tesla K80 GPUs we had at our disposal and an overall total for each hash. We'd love to hear any feedback regarding the cracking speeds or how to fine tune our set-up to improve performance.

Enjoy!

```nohighlight
OpenCL Platform #1: NVIDIA Corporation
======================================
* Device #1: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #2: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #3: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #4: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #5: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #6: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #7: Tesla K80, 2859/11439 MB allocatable, 13MCU
* Device #8: Tesla K80, 2859/11439 MB allocatable, 13MCU

Hashtype: MD4

Speed.Dev.#1.....:  7995.3 MH/s (54.51ms)
Speed.Dev.#2.....:  8390.4 MH/s (51.95ms)
Speed.Dev.#3.....:  7680.7 MH/s (56.75ms)
Speed.Dev.#4.....:  8190.8 MH/s (53.22ms)
Speed.Dev.#5.....:  7738.2 MH/s (56.33ms)
Speed.Dev.#6.....:  8568.4 MH/s (50.86ms)
Speed.Dev.#7.....:  8023.7 MH/s (54.31ms)
Speed.Dev.#8.....:  8443.0 MH/s (51.62ms)
Speed.Dev.#*.....: 65030.3 MH/s

Hashtype: MD5

Speed.Dev.#1.....:  4258.3 MH/s (51.18ms)
Speed.Dev.#2.....:  4423.5 MH/s (49.26ms)
Speed.Dev.#3.....:  4080.2 MH/s (53.41ms)
Speed.Dev.#4.....:  4457.6 MH/s (48.89ms)
Speed.Dev.#5.....:  4110.2 MH/s (53.03ms)
Speed.Dev.#6.....:  4414.8 MH/s (49.35ms)
Speed.Dev.#7.....:  4244.8 MH/s (51.34ms)
Speed.Dev.#8.....:  4471.4 MH/s (48.74ms)
Speed.Dev.#*.....: 34460.8 MH/s

Hashtype: Half MD5

Speed.Dev.#1.....:  3049.9 MH/s (71.47ms)
Speed.Dev.#2.....:  3091.3 MH/s (70.51ms)
Speed.Dev.#3.....:  2938.3 MH/s (74.19ms)
Speed.Dev.#4.....:  3173.7 MH/s (68.68ms)
Speed.Dev.#5.....:  2918.6 MH/s (74.69ms)
Speed.Dev.#6.....:  3138.9 MH/s (69.44ms)
Speed.Dev.#7.....:  3064.1 MH/s (71.14ms)
Speed.Dev.#8.....:  3125.5 MH/s (69.72ms)
Speed.Dev.#*.....: 24500.2 MH/s

Hashtype: SHA1

Speed.Dev.#1.....:  1948.3 MH/s (55.68ms)
Speed.Dev.#2.....:  1939.9 MH/s (55.96ms)
Speed.Dev.#3.....:  1794.3 MH/s (60.48ms)
Speed.Dev.#4.....:  1933.2 MH/s (56.13ms)
Speed.Dev.#5.....:  1841.9 MH/s (58.93ms)
Speed.Dev.#6.....:  2000.0 MH/s (54.26ms)
Speed.Dev.#7.....:  1932.3 MH/s (56.17ms)
Speed.Dev.#8.....:  2009.2 MH/s (54.02ms)
Speed.Dev.#*.....: 15399.0 MH/s

Hashtype: SHA-256

Speed.Dev.#1.....:   823.2 MH/s (66.20ms)
Speed.Dev.#2.....:   835.1 MH/s (65.25ms)
Speed.Dev.#3.....:   799.5 MH/s (68.15ms)
Speed.Dev.#4.....:   800.2 MH/s (68.10ms)
Speed.Dev.#5.....:   788.1 MH/s (69.14ms)
Speed.Dev.#6.....:   837.5 MH/s (65.07ms)
Speed.Dev.#7.....:   819.2 MH/s (66.52ms)
Speed.Dev.#8.....:   841.1 MH/s (64.79ms)
Speed.Dev.#*.....:  6544.0 MH/s

Hashtype: SHA-384

Speed.Dev.#1.....:   211.0 MH/s (64.55ms)
Speed.Dev.#2.....:   205.0 MH/s (66.47ms)
Speed.Dev.#3.....:   208.3 MH/s (65.41ms)
Speed.Dev.#4.....:   208.5 MH/s (65.34ms)
Speed.Dev.#5.....:   208.9 MH/s (65.21ms)
Speed.Dev.#6.....:   208.1 MH/s (65.46ms)
Speed.Dev.#7.....:   209.3 MH/s (65.08ms)
Speed.Dev.#8.....:   206.6 MH/s (65.94ms)
Speed.Dev.#*.....:  1665.7 MH/s

Hashtype: SHA-512

Speed.Dev.#1.....:   214.8 MH/s (63.42ms)
Speed.Dev.#2.....:   212.9 MH/s (64.00ms)
Speed.Dev.#3.....:   213.5 MH/s (63.80ms)
Speed.Dev.#4.....:   211.4 MH/s (64.43ms)
Speed.Dev.#5.....:   215.2 MH/s (63.31ms)
Speed.Dev.#6.....:   212.0 MH/s (64.26ms)
Speed.Dev.#7.....:   213.8 MH/s (63.73ms)
Speed.Dev.#8.....:   209.9 MH/s (64.91ms)
Speed.Dev.#*.....:  1703.4 MH/s

Hashtype: SHA-3 (Keccak)

Speed.Dev.#1.....:   187.2 MH/s (72.80ms)
Speed.Dev.#2.....:   181.2 MH/s (75.19ms)
Speed.Dev.#3.....:   178.4 MH/s (76.38ms)
Speed.Dev.#4.....:   176.1 MH/s (77.36ms)
Speed.Dev.#5.....:   178.6 MH/s (76.29ms)
Speed.Dev.#6.....:   181.6 MH/s (75.02ms)
Speed.Dev.#7.....:   181.2 MH/s (75.17ms)
Speed.Dev.#8.....:   180.0 MH/s (75.70ms)
Speed.Dev.#*.....:  1444.2 MH/s

Hashtype: SipHash

Speed.Dev.#1.....:  7895.9 MH/s (55.20ms)
Speed.Dev.#2.....:  8110.7 MH/s (53.74ms)
Speed.Dev.#3.....:  7562.8 MH/s (57.64ms)
Speed.Dev.#4.....:  7945.1 MH/s (54.86ms)
Speed.Dev.#5.....:  7669.2 MH/s (56.83ms)
Speed.Dev.#6.....:  8248.9 MH/s (52.84ms)
Speed.Dev.#7.....:  7755.6 MH/s (56.17ms)
Speed.Dev.#8.....:  8231.3 MH/s (52.95ms)
Speed.Dev.#*.....: 63419.3 MH/s

Hashtype: Skip32 (PT = $salt, key = $pass)

Speed.Dev.#1.....:  1325.6 MH/s (1.53ms)
Speed.Dev.#2.....:  1312.4 MH/s (1.55ms)
Speed.Dev.#3.....:  1334.9 MH/s (1.53ms)
Speed.Dev.#4.....:  1302.6 MH/s (1.54ms)
Speed.Dev.#5.....:  1330.7 MH/s (1.53ms)
Speed.Dev.#6.....:  1309.9 MH/s (1.54ms)
Speed.Dev.#7.....:  1322.3 MH/s (1.53ms)
Speed.Dev.#8.....:  1285.8 MH/s (1.58ms)
Speed.Dev.#*.....: 10524.2 MH/s

Hashtype: RIPEMD-160

Speed.Dev.#1.....:  1296.8 MH/s (83.72ms)
Speed.Dev.#2.....:  1213.5 MH/s (89.47ms)
Speed.Dev.#3.....:  1184.3 MH/s (91.68ms)
Speed.Dev.#4.....:  1181.8 MH/s (91.88ms)
Speed.Dev.#5.....:  1171.7 MH/s (92.67ms)
Speed.Dev.#6.....:  1284.0 MH/s (84.56ms)
Speed.Dev.#7.....:  1207.6 MH/s (89.91ms)
Speed.Dev.#8.....:  1217.8 MH/s (89.16ms)
Speed.Dev.#*.....:  9757.5 MH/s

Hashtype: Whirlpool

Speed.Dev.#1.....: 80044.1 kH/s (84.09ms)
Speed.Dev.#2.....: 78841.1 kH/s (85.39ms)
Speed.Dev.#3.....: 79700.3 kH/s (84.47ms)
Speed.Dev.#4.....: 79093.0 kH/s (85.10ms)
Speed.Dev.#5.....: 80016.5 kH/s (84.14ms)
Speed.Dev.#6.....: 79158.9 kH/s (85.04ms)
Speed.Dev.#7.....: 79131.0 kH/s (85.08ms)
Speed.Dev.#8.....: 78046.4 kH/s (86.27ms)
Speed.Dev.#*.....:   634.0 MH/s

Hashtype: GOST R 34.11-94

Speed.Dev.#1.....: 67243.1 kH/s (100.12ms)
Speed.Dev.#2.....: 66509.4 kH/s (101.22ms)
Speed.Dev.#3.....: 67103.1 kH/s (100.33ms)
Speed.Dev.#4.....: 67283.4 kH/s (100.06ms)
Speed.Dev.#5.....: 67354.7 kH/s (99.96ms)
Speed.Dev.#6.....: 66746.7 kH/s (100.88ms)
Speed.Dev.#7.....: 67547.2 kH/s (99.68ms)
Speed.Dev.#8.....: 65256.2 kH/s (103.17ms)
Speed.Dev.#*.....:   535.0 MH/s

Hashtype: GOST R 34.11-2012 (Streebog) 256-bit

Speed.Dev.#1.....: 20096.0 kH/s (169.54ms)
Speed.Dev.#2.....: 19611.2 kH/s (173.74ms)
Speed.Dev.#3.....: 19525.0 kH/s (174.50ms)
Speed.Dev.#4.....: 19155.8 kH/s (177.87ms)
Speed.Dev.#5.....: 19534.4 kH/s (174.42ms)
Speed.Dev.#6.....: 20090.4 kH/s (169.57ms)
Speed.Dev.#7.....: 20165.4 kH/s (168.96ms)
Speed.Dev.#8.....: 19499.2 kH/s (174.73ms)
Speed.Dev.#*.....:   157.7 MH/s

Hashtype: GOST R 34.11-2012 (Streebog) 512-bit

Speed.Dev.#1.....: 19741.0 kH/s (172.59ms)
Speed.Dev.#2.....: 19712.2 kH/s (172.84ms)
Speed.Dev.#3.....: 19608.6 kH/s (173.76ms)
Speed.Dev.#4.....: 19690.9 kH/s (173.03ms)
Speed.Dev.#5.....: 19667.1 kH/s (173.24ms)
Speed.Dev.#6.....: 20094.1 kH/s (169.55ms)
Speed.Dev.#7.....: 19754.2 kH/s (172.48ms)
Speed.Dev.#8.....: 19582.8 kH/s (173.98ms)
Speed.Dev.#*.....:   157.9 MH/s

Hashtype: DES (PT = $salt, key = $pass)

Speed.Dev.#1.....:  3835.5 MH/s (56.63ms)
Speed.Dev.#2.....:  3797.9 MH/s (57.25ms)
Speed.Dev.#3.....:  3737.0 MH/s (58.17ms)
Speed.Dev.#4.....:  3796.4 MH/s (57.30ms)
Speed.Dev.#5.....:  3755.1 MH/s (57.90ms)
Speed.Dev.#6.....:  3810.9 MH/s (57.06ms)
Speed.Dev.#7.....:  3835.1 MH/s (56.70ms)
Speed.Dev.#8.....:  3776.0 MH/s (57.60ms)
Speed.Dev.#*.....: 30343.9 MH/s

Hashtype: 3DES (PT = $salt, key = $pass)

Speed.Dev.#1.....:   255.4 MH/s (53.33ms)
Speed.Dev.#2.....:   250.0 MH/s (54.49ms)
Speed.Dev.#3.....:   258.9 MH/s (52.62ms)
Speed.Dev.#4.....:   261.9 MH/s (52.00ms)
Speed.Dev.#5.....:   258.5 MH/s (52.70ms)
Speed.Dev.#6.....:   251.0 MH/s (54.25ms)
Speed.Dev.#7.....:   253.6 MH/s (53.71ms)
Speed.Dev.#8.....:   239.7 MH/s (56.83ms)
Speed.Dev.#*.....:  2028.8 MH/s

Hashtype: phpass, WordPress (MD5), phpBB3 (MD5), Joomla (MD5)

Speed.Dev.#1.....:  1398.4 kH/s (75.47ms)
Speed.Dev.#2.....:  1414.4 kH/s (74.62ms)
Speed.Dev.#3.....:  1360.6 kH/s (77.61ms)
Speed.Dev.#4.....:  1353.2 kH/s (78.04ms)
Speed.Dev.#5.....:  1329.9 kH/s (79.38ms)
Speed.Dev.#6.....:  1422.1 kH/s (74.22ms)
Speed.Dev.#7.....:  1374.7 kH/s (76.78ms)
Speed.Dev.#8.....:  1384.6 kH/s (76.24ms)
Speed.Dev.#*.....: 11037.9 kH/s

Hashtype: scrypt

Speed.Dev.#1.....:   145.9 kH/s (336.37ms)
Speed.Dev.#2.....:   155.2 kH/s (314.15ms)
Speed.Dev.#3.....:   146.9 kH/s (333.22ms)
Speed.Dev.#4.....:   144.4 kH/s (339.18ms)
Speed.Dev.#5.....:   149.0 kH/s (327.62ms)
Speed.Dev.#6.....:   147.9 kH/s (329.75ms)
Speed.Dev.#7.....:   143.3 kH/s (341.56ms)
Speed.Dev.#8.....:   143.1 kH/s (341.49ms)
Speed.Dev.#*.....:  1175.7 kH/s

Hashtype: PBKDF2-HMAC-MD5

Speed.Dev.#1.....:  1470.2 kH/s (58.86ms)
Speed.Dev.#2.....:  1451.2 kH/s (59.49ms)
Speed.Dev.#3.....:  1366.1 kH/s (63.55ms)
Speed.Dev.#4.....:  1468.2 kH/s (59.05ms)
Speed.Dev.#5.....:  1382.7 kH/s (62.58ms)
Speed.Dev.#6.....:  1474.9 kH/s (58.59ms)
Speed.Dev.#7.....:  1440.2 kH/s (60.03ms)
Speed.Dev.#8.....:  1467.3 kH/s (58.90ms)
Speed.Dev.#*.....: 11520.8 kH/s

Hashtype: PBKDF2-HMAC-SHA1

Speed.Dev.#1.....:   762.1 kH/s (60.14ms)
Speed.Dev.#2.....:   770.8 kH/s (59.42ms)
Speed.Dev.#3.....:   721.7 kH/s (63.69ms)
Speed.Dev.#4.....:   750.2 kH/s (61.23ms)
Speed.Dev.#5.....:   718.8 kH/s (63.84ms)
Speed.Dev.#6.....:   781.1 kH/s (58.63ms)
Speed.Dev.#7.....:   768.1 kH/s (59.67ms)
Speed.Dev.#8.....:   747.2 kH/s (61.36ms)
Speed.Dev.#*.....:  6020.0 kH/s

Hashtype: PBKDF2-HMAC-SHA256

Speed.Dev.#1.....:   290.5 kH/s (85.48ms)
Speed.Dev.#2.....:   291.9 kH/s (85.05ms)
Speed.Dev.#3.....:   284.9 kH/s (87.17ms)
Speed.Dev.#4.....:   283.2 kH/s (87.70ms)
Speed.Dev.#5.....:   282.8 kH/s (87.80ms)
Speed.Dev.#6.....:   295.5 kH/s (83.98ms)
Speed.Dev.#7.....:   290.3 kH/s (85.52ms)
Speed.Dev.#8.....:   292.0 kH/s (84.99ms)
Speed.Dev.#*.....:  2310.9 kH/s

Hashtype: PBKDF2-HMAC-SHA512
Speed.Dev.#1.....:    94566 H/s (67.09ms)
Speed.Dev.#2.....:    94087 H/s (67.44ms)
Speed.Dev.#3.....:    92737 H/s (68.42ms)
Speed.Dev.#4.....:    92734 H/s (68.43ms)
Speed.Dev.#5.....:    91743 H/s (69.17ms)
Speed.Dev.#6.....:    95343 H/s (66.55ms)
Speed.Dev.#7.....:    92985 H/s (68.25ms)
Speed.Dev.#8.....:    93837 H/s (67.61ms)
Speed.Dev.#*.....:   748.0 kH/s

Hashtype: Skype

Speed.Dev.#1.....:  2830.8 MH/s (77.01ms)
Speed.Dev.#2.....:  2958.6 MH/s (73.66ms)
Speed.Dev.#3.....:  2750.9 MH/s (79.24ms)
Speed.Dev.#4.....:  2892.3 MH/s (75.37ms)
Speed.Dev.#5.....:  2780.1 MH/s (78.40ms)
Speed.Dev.#6.....:  3074.6 MH/s (70.90ms)
Speed.Dev.#7.....:  2823.0 MH/s (77.22ms)
Speed.Dev.#8.....:  2959.2 MH/s (73.67ms)
Speed.Dev.#*.....: 23069.4 MH/s

Hashtype: WPA/WPA2

Speed.Dev.#1.....:    92251 H/s (70.35ms)
Speed.Dev.#2.....:    93328 H/s (69.54ms)
Speed.Dev.#3.....:    89635 H/s (72.42ms)
Speed.Dev.#4.....:    91501 H/s (70.94ms)
Speed.Dev.#5.....:    89356 H/s (72.64ms)
Speed.Dev.#6.....:    93818 H/s (69.18ms)
Speed.Dev.#7.....:    91415 H/s (71.00ms)
Speed.Dev.#8.....:    91367 H/s (71.04ms)
Speed.Dev.#*.....:   732.7 kH/s

Hashtype: IKE-PSK MD5

Speed.Dev.#1.....:   322.9 MH/s (84.38ms)
Speed.Dev.#2.....:   322.4 MH/s (84.52ms)
Speed.Dev.#3.....:   315.6 MH/s (86.35ms)
Speed.Dev.#4.....:   318.7 MH/s (85.51ms)
Speed.Dev.#5.....:   315.7 MH/s (86.31ms)
Speed.Dev.#6.....:   322.9 MH/s (84.38ms)
Speed.Dev.#7.....:   323.5 MH/s (84.23ms)
Speed.Dev.#8.....:   320.7 MH/s (84.96ms)
Speed.Dev.#*.....:  2562.5 MH/s

Hashtype: IKE-PSK SHA1

Speed.Dev.#1.....:   167.5 MH/s (81.36ms)
Speed.Dev.#2.....:   168.3 MH/s (80.94ms)
Speed.Dev.#3.....:   165.3 MH/s (82.44ms)
Speed.Dev.#4.....:   165.7 MH/s (82.21ms)
Speed.Dev.#5.....:   163.8 MH/s (83.15ms)
Speed.Dev.#6.....:   167.6 MH/s (81.27ms)
Speed.Dev.#7.....:   166.2 MH/s (81.99ms)
Speed.Dev.#8.....:   168.4 MH/s (80.91ms)
Speed.Dev.#*.....:  1332.8 MH/s

Hashtype: NetNTLMv1 / NetNTLMv1+ESS

Speed.Dev.#1.....:  4558.2 MH/s (95.64ms)
Speed.Dev.#2.....:  4747.1 MH/s (91.85ms)
Speed.Dev.#3.....:  4358.1 MH/s (100.05ms)
Speed.Dev.#4.....:  4695.8 MH/s (92.85ms)
Speed.Dev.#5.....:  4433.2 MH/s (98.35ms)
Speed.Dev.#6.....:  4765.8 MH/s (91.49ms)
Speed.Dev.#7.....:  4599.7 MH/s (94.79ms)
Speed.Dev.#8.....:  4736.3 MH/s (92.06ms)
Speed.Dev.#*.....: 36894.4 MH/s

Hashtype: NetNTLMv2

Speed.Dev.#1.....:   298.4 MH/s (91.33ms)
Speed.Dev.#2.....:   294.6 MH/s (92.51ms)
Speed.Dev.#3.....:   291.3 MH/s (93.55ms)
Speed.Dev.#4.....:   294.6 MH/s (92.52ms)
Speed.Dev.#5.....:   293.5 MH/s (92.83ms)
Speed.Dev.#6.....:   294.8 MH/s (92.43ms)
Speed.Dev.#7.....:   297.5 MH/s (91.59ms)
Speed.Dev.#8.....:   295.4 MH/s (92.24ms)
Speed.Dev.#*.....:  2360.2 MH/s

Hashtype: IPMI2 RAKP HMAC-SHA1

Speed.Dev.#1.....:   344.4 MH/s (79.11ms)
Speed.Dev.#2.....:   350.9 MH/s (77.66ms)
Speed.Dev.#3.....:   328.6 MH/s (82.94ms)
Speed.Dev.#4.....:   357.5 MH/s (76.23ms)
Speed.Dev.#5.....:   333.2 MH/s (81.79ms)
Speed.Dev.#6.....:   359.1 MH/s (75.87ms)
Speed.Dev.#7.....:   341.2 MH/s (79.86ms)
Speed.Dev.#8.....:   360.1 MH/s (75.66ms)
Speed.Dev.#*.....:  2775.0 MH/s

Hashtype: Kerberos 5 AS-REQ Pre-Auth etype 23

Speed.Dev.#1.....: 47353.3 kH/s (71.91ms)
Speed.Dev.#2.....: 47154.1 kH/s (72.21ms)
Speed.Dev.#3.....: 47373.7 kH/s (71.88ms)
Speed.Dev.#4.....: 46959.8 kH/s (72.51ms)
Speed.Dev.#5.....: 47553.8 kH/s (143.27ms)
Speed.Dev.#6.....: 46983.7 kH/s (72.48ms)
Speed.Dev.#7.....: 47942.5 kH/s (142.11ms)
Speed.Dev.#8.....: 47183.5 kH/s (72.17ms)
Speed.Dev.#*.....:   378.5 MH/s

Hashtype: Kerberos 5 TGS-REP etype 23

Speed.Dev.#1.....: 48248.3 kH/s (141.19ms)
Speed.Dev.#2.....: 47441.9 kH/s (143.62ms)
Speed.Dev.#3.....: 47836.2 kH/s (142.43ms)
Speed.Dev.#4.....: 47577.4 kH/s (143.19ms)
Speed.Dev.#5.....: 47790.9 kH/s (142.57ms)
Speed.Dev.#6.....: 47851.3 kH/s (142.39ms)
Speed.Dev.#7.....: 48198.8 kH/s (141.36ms)
Speed.Dev.#8.....: 47656.9 kH/s (142.98ms)
Speed.Dev.#*.....:   382.6 MH/s

Hashtype: DNSSEC (NSEC3)

Speed.Dev.#1.....:   760.2 MH/s (71.68ms)
Speed.Dev.#2.....:   756.6 MH/s (72.03ms)
Speed.Dev.#3.....:   735.7 MH/s (74.08ms)
Speed.Dev.#4.....:   738.7 MH/s (73.77ms)
Speed.Dev.#5.....:   732.9 MH/s (74.36ms)
Speed.Dev.#6.....:   770.9 MH/s (70.69ms)
Speed.Dev.#7.....:   765.9 MH/s (71.15ms)
Speed.Dev.#8.....:   761.4 MH/s (71.57ms)
Speed.Dev.#*.....:  6022.4 MH/s

Hashtype: PostgreSQL CRAM (MD5)

Speed.Dev.#1.....:  1338.9 MH/s (81.09ms)
Speed.Dev.#2.....:  1414.9 MH/s (76.73ms)
Speed.Dev.#3.....:  1331.1 MH/s (81.57ms)
Speed.Dev.#4.....:  1393.5 MH/s (77.91ms)
Speed.Dev.#5.....:  1352.1 MH/s (80.29ms)
Speed.Dev.#6.....:  1476.5 MH/s (73.53ms)
Speed.Dev.#7.....:  1364.5 MH/s (79.56ms)
Speed.Dev.#8.....:  1428.7 MH/s (75.99ms)
Speed.Dev.#*.....: 11100.1 MH/s

Hashtype: MySQL CRAM (SHA1)

Speed.Dev.#1.....:   512.3 MH/s (53.10ms)
Speed.Dev.#2.....:   505.0 MH/s (53.88ms)
Speed.Dev.#3.....:   493.1 MH/s (55.18ms)
Speed.Dev.#4.....:   495.4 MH/s (54.92ms)
Speed.Dev.#5.....:   475.0 MH/s (86.03ms)
Speed.Dev.#6.....:   511.5 MH/s (53.19ms)
Speed.Dev.#7.....:   500.8 MH/s (54.33ms)
Speed.Dev.#8.....:   525.3 MH/s (51.80ms)
Speed.Dev.#*.....:  4018.3 MH/s

Hashtype: SIP digest authentication (MD5)

Speed.Dev.#1.....:   521.3 MH/s (52.20ms)
Speed.Dev.#2.....:   513.7 MH/s (52.98ms)
Speed.Dev.#3.....:   521.3 MH/s (52.20ms)
Speed.Dev.#4.....:   518.4 MH/s (52.50ms)
Speed.Dev.#5.....:   521.4 MH/s (52.17ms)
Speed.Dev.#6.....:   516.6 MH/s (52.68ms)
Speed.Dev.#7.....:   520.6 MH/s (52.28ms)
Speed.Dev.#8.....:   514.5 MH/s (52.90ms)
Speed.Dev.#*.....:  4147.8 MH/s

Hashtype: SMF (Simple Machines Forum) > v1.1

Speed.Dev.#1.....:  1641.2 MH/s (66.15ms)
Speed.Dev.#2.....:  1682.5 MH/s (64.52ms)
Speed.Dev.#3.....:  1574.9 MH/s (68.93ms)
Speed.Dev.#4.....:  1581.2 MH/s (68.66ms)
Speed.Dev.#5.....:  1576.0 MH/s (68.89ms)
Speed.Dev.#6.....:  1655.1 MH/s (65.59ms)
Speed.Dev.#7.....:  1571.8 MH/s (69.05ms)
Speed.Dev.#8.....:  1627.6 MH/s (66.69ms)
Speed.Dev.#*.....: 12910.3 MH/s

Hashtype: vBulletin < v3.8.5

Speed.Dev.#1.....:  1303.4 MH/s (83.29ms)
Speed.Dev.#2.....:  1319.1 MH/s (82.29ms)
Speed.Dev.#3.....:  1279.0 MH/s (84.87ms)
Speed.Dev.#4.....:  1301.9 MH/s (83.38ms)
Speed.Dev.#5.....:  1227.7 MH/s (88.77ms)
Speed.Dev.#6.....:  1327.9 MH/s (81.75ms)
Speed.Dev.#7.....:  1304.3 MH/s (83.23ms)
Speed.Dev.#8.....:  1319.3 MH/s (82.60ms)
Speed.Dev.#*.....: 10382.5 MH/s

Hashtype: vBulletin >= v3.8.5

Speed.Dev.#1.....:   842.0 MH/s (64.70ms)
Speed.Dev.#2.....:   846.9 MH/s (64.35ms)
Speed.Dev.#3.....:   782.5 MH/s (69.58ms)
Speed.Dev.#4.....:   812.8 MH/s (66.98ms)
Speed.Dev.#5.....:   841.4 MH/s (64.77ms)
Speed.Dev.#6.....:   848.4 MH/s (64.23ms)
Speed.Dev.#7.....:   836.0 MH/s (65.18ms)
Speed.Dev.#8.....:   818.9 MH/s (66.48ms)
Speed.Dev.#*.....:  6628.9 MH/s

Hashtype: IPB2+ (Invision Power Board), MyBB 1.2+

Speed.Dev.#1.....:   937.1 MH/s (58.15ms)
Speed.Dev.#2.....:   923.6 MH/s (58.99ms)
Speed.Dev.#3.....:   897.1 MH/s (60.74ms)
Speed.Dev.#4.....:   917.3 MH/s (59.40ms)
Speed.Dev.#5.....:   860.6 MH/s (63.32ms)
Speed.Dev.#6.....:   929.3 MH/s (58.63ms)
Speed.Dev.#7.....:   911.2 MH/s (59.80ms)
Speed.Dev.#8.....:   925.4 MH/s (58.88ms)
Speed.Dev.#*.....:  7301.5 MH/s

Hashtype: WBB3 (Woltlab Burning Board)

Speed.Dev.#1.....:   270.9 MH/s (50.28ms)
Speed.Dev.#2.....:   273.3 MH/s (49.84ms)
Speed.Dev.#3.....:   266.3 MH/s (51.15ms)
Speed.Dev.#4.....:   271.6 MH/s (50.14ms)
Speed.Dev.#5.....:   268.3 MH/s (50.77ms)
Speed.Dev.#6.....:   282.3 MH/s (96.55ms)
Speed.Dev.#7.....:   270.1 MH/s (50.42ms)
Speed.Dev.#8.....:   277.1 MH/s (49.15ms)
Speed.Dev.#*.....:  2179.9 MH/s

Hashtype: OpenCart

Speed.Dev.#1.....:   452.4 MH/s (60.17ms)
Speed.Dev.#2.....:   452.5 MH/s (60.15ms)
Speed.Dev.#3.....:   445.6 MH/s (61.08ms)
Speed.Dev.#4.....:   444.2 MH/s (61.27ms)
Speed.Dev.#5.....:   437.5 MH/s (62.20ms)
Speed.Dev.#6.....:   455.8 MH/s (59.72ms)
Speed.Dev.#7.....:   447.3 MH/s (60.85ms)
Speed.Dev.#8.....:   451.1 MH/s (60.34ms)
Speed.Dev.#*.....:  3586.4 MH/s

Hashtype: Joomla < 2.5.18

Speed.Dev.#1.....:  4205.1 MH/s (51.82ms)
Speed.Dev.#2.....:  4398.5 MH/s (49.54ms)
Speed.Dev.#3.....:  4028.0 MH/s (54.10ms)
Speed.Dev.#4.....:  4395.0 MH/s (49.58ms)
Speed.Dev.#5.....:  4198.7 MH/s (51.90ms)
Speed.Dev.#6.....:  4500.1 MH/s (48.41ms)
Speed.Dev.#7.....:  4130.9 MH/s (52.76ms)
Speed.Dev.#8.....:  4390.3 MH/s (49.64ms)
Speed.Dev.#*.....: 34246.6 MH/s

Hashtype: PHPS

Speed.Dev.#1.....:  1303.9 MH/s (83.27ms)
Speed.Dev.#2.....:  1323.3 MH/s (82.05ms)
Speed.Dev.#3.....:  1259.1 MH/s (86.24ms)
Speed.Dev.#4.....:  1307.7 MH/s (83.02ms)
Speed.Dev.#5.....:  1213.7 MH/s (89.81ms)
Speed.Dev.#6.....:  1323.9 MH/s (82.01ms)
Speed.Dev.#7.....:  1315.4 MH/s (82.54ms)
Speed.Dev.#8.....:  1313.9 MH/s (82.62ms)
Speed.Dev.#*.....: 10360.9 MH/s

Hashtype: Drupal7

Speed.Dev.#1.....:    13333 H/s (62.33ms)
Speed.Dev.#2.....:    13433 H/s (61.80ms)
Speed.Dev.#3.....:    13000 H/s (63.85ms)
Speed.Dev.#4.....:    13010 H/s (63.81ms)
Speed.Dev.#5.....:    13032 H/s (63.70ms)
Speed.Dev.#6.....:    13625 H/s (61.00ms)
Speed.Dev.#7.....:    13091 H/s (63.41ms)
Speed.Dev.#8.....:    13270 H/s (62.63ms)
Speed.Dev.#*.....:   105.8 kH/s

Hashtype: osCommerce, xt:Commerce

Speed.Dev.#1.....:  2911.6 MH/s (74.87ms)
Speed.Dev.#2.....:  2942.1 MH/s (74.10ms)
Speed.Dev.#3.....:  2811.3 MH/s (77.54ms)
Speed.Dev.#4.....:  2886.0 MH/s (75.53ms)
Speed.Dev.#5.....:  2739.3 MH/s (79.58ms)
Speed.Dev.#6.....:  2989.4 MH/s (72.91ms)
Speed.Dev.#7.....:  2881.4 MH/s (75.65ms)
Speed.Dev.#8.....:  2956.5 MH/s (73.73ms)
Speed.Dev.#*.....: 23117.6 MH/s

Hashtype: PrestaShop

Speed.Dev.#1.....:  1544.3 MH/s (70.30ms)
Speed.Dev.#2.....:  1606.5 MH/s (67.58ms)
Speed.Dev.#3.....:  1491.5 MH/s (72.79ms)
Speed.Dev.#4.....:  1550.0 MH/s (70.04ms)
Speed.Dev.#5.....:  1601.9 MH/s (67.76ms)
Speed.Dev.#6.....:  1626.5 MH/s (66.75ms)
Speed.Dev.#7.....:  1534.1 MH/s (70.76ms)
Speed.Dev.#8.....:  1604.7 MH/s (67.65ms)
Speed.Dev.#*.....: 12559.4 MH/s

Hashtype: Django (SHA-1)

Speed.Dev.#1.....:  1574.7 MH/s (68.94ms)
Speed.Dev.#2.....:  1628.5 MH/s (66.66ms)
Speed.Dev.#3.....:  1541.6 MH/s (70.42ms)
Speed.Dev.#4.....:  1579.7 MH/s (68.72ms)
Speed.Dev.#5.....:  1505.6 MH/s (72.11ms)
Speed.Dev.#6.....:  1656.5 MH/s (65.54ms)
Speed.Dev.#7.....:  1602.5 MH/s (67.74ms)
Speed.Dev.#8.....:  1621.1 MH/s (66.97ms)
Speed.Dev.#*.....: 12710.4 MH/s

Hashtype: Django (PBKDF2-SHA256)

Speed.Dev.#1.....:    14536 H/s (93.47ms)
Speed.Dev.#2.....:    14487 H/s (93.79ms)
Speed.Dev.#3.....:    14034 H/s (96.74ms)
Speed.Dev.#4.....:    13965 H/s (97.23ms)
Speed.Dev.#5.....:    13966 H/s (97.21ms)
Speed.Dev.#6.....:    14730 H/s (92.31ms)
Speed.Dev.#7.....:    14151 H/s (95.94ms)
Speed.Dev.#8.....:    14553 H/s (93.36ms)
Speed.Dev.#*.....:   114.4 kH/s

Hashtype: MediaWiki B type

Speed.Dev.#1.....:  1284.8 MH/s (84.84ms)
Speed.Dev.#2.....:  1343.2 MH/s (81.15ms)
Speed.Dev.#3.....:  1239.8 MH/s (87.92ms)
Speed.Dev.#4.....:  1351.3 MH/s (80.67ms)
Speed.Dev.#5.....:  1244.4 MH/s (87.60ms)
Speed.Dev.#6.....:  1367.4 MH/s (79.70ms)
Speed.Dev.#7.....:  1284.0 MH/s (84.89ms)
Speed.Dev.#8.....:  1367.5 MH/s (79.71ms)
Speed.Dev.#*.....: 10482.3 MH/s

Hashtype: Redmine

Speed.Dev.#1.....:   682.6 MH/s (79.83ms)
Speed.Dev.#2.....:   691.4 MH/s (78.82ms)
Speed.Dev.#3.....:   621.0 MH/s (87.68ms)
Speed.Dev.#4.....:   635.5 MH/s (85.76ms)
Speed.Dev.#5.....:   633.3 MH/s (86.06ms)
Speed.Dev.#6.....:   690.4 MH/s (78.93ms)
Speed.Dev.#7.....:   657.4 MH/s (82.90ms)
Speed.Dev.#8.....:   664.5 MH/s (82.01ms)
Speed.Dev.#*.....:  5276.2 MH/s

Hashtype: PunBB

Speed.Dev.#1.....:   644.3 MH/s (84.50ms)
Speed.Dev.#2.....:   663.2 MH/s (82.09ms)
Speed.Dev.#3.....:   622.4 MH/s (87.48ms)
Speed.Dev.#4.....:   656.4 MH/s (82.95ms)
Speed.Dev.#5.....:   626.9 MH/s (86.84ms)
Speed.Dev.#6.....:   676.9 MH/s (80.43ms)
Speed.Dev.#7.....:   635.3 MH/s (85.71ms)
Speed.Dev.#8.....:   667.5 MH/s (81.57ms)
Speed.Dev.#*.....:  5192.9 MH/s

Hashtype: PostgreSQL

Speed.Dev.#1.....:  4206.4 MH/s (51.81ms)
Speed.Dev.#2.....:  4487.5 MH/s (48.56ms)
Speed.Dev.#3.....:  4052.5 MH/s (53.77ms)
Speed.Dev.#4.....:  4217.3 MH/s (51.67ms)
Speed.Dev.#5.....:  4081.8 MH/s (53.39ms)
Speed.Dev.#6.....:  4412.4 MH/s (49.39ms)
Speed.Dev.#7.....:  4227.1 MH/s (51.56ms)
Speed.Dev.#8.....:  4387.7 MH/s (49.65ms)
Speed.Dev.#*.....: 34072.8 MH/s

Hashtype: MSSQL (2000)

Speed.Dev.#1.....:  1769.7 MH/s (61.34ms)
Speed.Dev.#2.....:  1860.8 MH/s (58.34ms)
Speed.Dev.#3.....:  1694.4 MH/s (64.07ms)
Speed.Dev.#4.....:  1762.6 MH/s (61.59ms)
Speed.Dev.#5.....:  1716.0 MH/s (63.26ms)
Speed.Dev.#6.....:  1862.6 MH/s (58.27ms)
Speed.Dev.#7.....:  1756.0 MH/s (61.82ms)
Speed.Dev.#8.....:  1828.6 MH/s (59.36ms)
Speed.Dev.#*.....: 14250.8 MH/s

Hashtype: MSSQL (2005)

Speed.Dev.#1.....:  1778.3 MH/s (61.04ms)
Speed.Dev.#2.....:  1810.5 MH/s (59.96ms)
Speed.Dev.#3.....:  1714.9 MH/s (63.30ms)
Speed.Dev.#4.....:  1784.9 MH/s (60.82ms)
Speed.Dev.#5.....:  1712.4 MH/s (63.40ms)
Speed.Dev.#6.....:  1865.8 MH/s (58.18ms)
Speed.Dev.#7.....:  1759.1 MH/s (61.71ms)
Speed.Dev.#8.....:  1883.1 MH/s (57.64ms)
Speed.Dev.#*.....: 14308.9 MH/s

Hashtype: MSSQL (2012, 2014)

Speed.Dev.#1.....:   210.4 MH/s (64.75ms)
Speed.Dev.#2.....:   206.9 MH/s (65.84ms)
Speed.Dev.#3.....:   207.5 MH/s (65.67ms)
Speed.Dev.#4.....:   208.0 MH/s (65.48ms)
Speed.Dev.#5.....:   206.7 MH/s (65.89ms)
Speed.Dev.#6.....:   209.0 MH/s (65.18ms)
Speed.Dev.#7.....:   208.3 MH/s (65.42ms)
Speed.Dev.#8.....:   206.1 MH/s (66.09ms)
Speed.Dev.#*.....:  1662.9 MH/s

Hashtype: MySQL323

Speed.Dev.#1.....: 17852.5 MH/s (48.82ms)
Speed.Dev.#2.....: 19055.9 MH/s (91.52ms)
Speed.Dev.#3.....: 17153.6 MH/s (50.82ms)
Speed.Dev.#4.....: 17896.4 MH/s (48.71ms)
Speed.Dev.#5.....: 18352.3 MH/s (47.49ms)
Speed.Dev.#6.....: 18738.2 MH/s (93.07ms)
Speed.Dev.#7.....: 17858.3 MH/s (48.81ms)
Speed.Dev.#8.....: 18895.5 MH/s (92.29ms)
Speed.Dev.#*.....:   145.8 GH/s

Hashtype: MySQL4.1/MySQL5

Speed.Dev.#1.....:   890.4 MH/s (61.19ms)
Speed.Dev.#2.....:   864.6 MH/s (63.03ms)
Speed.Dev.#3.....:   821.3 MH/s (66.35ms)
Speed.Dev.#4.....:   844.0 MH/s (64.56ms)
Speed.Dev.#5.....:   830.5 MH/s (65.62ms)
Speed.Dev.#6.....:   879.6 MH/s (61.94ms)
Speed.Dev.#7.....:   839.0 MH/s (64.94ms)
Speed.Dev.#8.....:   867.8 MH/s (62.79ms)
Speed.Dev.#*.....:  6837.2 MH/s

Hashtype: Oracle H: Type (Oracle 7+)

Speed.Dev.#1.....:   296.0 MH/s (91.71ms)
Speed.Dev.#2.....:   291.5 MH/s (93.14ms)
Speed.Dev.#3.....:   286.8 MH/s (95.00ms)
Speed.Dev.#4.....:   293.2 MH/s (92.58ms)
Speed.Dev.#5.....:   295.6 MH/s (91.83ms)
Speed.Dev.#6.....:   292.4 MH/s (92.83ms)
Speed.Dev.#7.....:   295.1 MH/s (91.98ms)
Speed.Dev.#8.....:   287.6 MH/s (94.38ms)
Speed.Dev.#*.....:  2338.2 MH/s

Hashtype: Oracle S: Type (Oracle 11+)

Speed.Dev.#1.....:  1922.8 MH/s (56.45ms)
Speed.Dev.#2.....:  1956.8 MH/s (55.47ms)
Speed.Dev.#3.....:  1878.8 MH/s (57.77ms)
Speed.Dev.#4.....:  1897.7 MH/s (57.16ms)
Speed.Dev.#5.....:  1825.6 MH/s (59.42ms)
Speed.Dev.#6.....:  1961.9 MH/s (55.33ms)
Speed.Dev.#7.....:  1848.3 MH/s (58.73ms)
Speed.Dev.#8.....:  1990.9 MH/s (54.52ms)
Speed.Dev.#*.....: 15282.8 MH/s

Hashtype: Oracle T: Type (Oracle 12+)

Speed.Dev.#1.....:    23275 H/s (70.53ms)
Speed.Dev.#2.....:    23264 H/s (70.56ms)
Speed.Dev.#3.....:    22809 H/s (71.95ms)
Speed.Dev.#4.....:    22844 H/s (71.85ms)
Speed.Dev.#5.....:    22539 H/s (72.82ms)
Speed.Dev.#6.....:    23601 H/s (69.57ms)
Speed.Dev.#7.....:    22944 H/s (71.55ms)
Speed.Dev.#8.....:    23203 H/s (70.75ms)
Speed.Dev.#*.....:   184.5 kH/s

Hashtype: Sybase ASE

Speed.Dev.#1.....: 67253.1 kH/s (100.11ms)
Speed.Dev.#2.....: 68150.6 kH/s (98.79ms)
Speed.Dev.#3.....: 67477.5 kH/s (99.78ms)
Speed.Dev.#4.....: 65211.9 kH/s (103.23ms)
Speed.Dev.#5.....: 66111.9 kH/s (101.84ms)
Speed.Dev.#6.....: 66037.3 kH/s (101.95ms)
Speed.Dev.#7.....: 69038.4 kH/s (97.53ms)
Speed.Dev.#8.....: 66721.5 kH/s (100.91ms)
Speed.Dev.#*.....:   536.0 MH/s

Hashtype: Episerver 6.x < .NET 4

Speed.Dev.#1.....:  1560.6 MH/s (69.56ms)
Speed.Dev.#2.....:  1667.7 MH/s (65.09ms)
Speed.Dev.#3.....:  1507.1 MH/s (72.03ms)
Speed.Dev.#4.....:  1581.5 MH/s (68.64ms)
Speed.Dev.#5.....:  1508.3 MH/s (71.98ms)
Speed.Dev.#6.....:  1683.5 MH/s (64.48ms)
Speed.Dev.#7.....:  1575.8 MH/s (68.89ms)
Speed.Dev.#8.....:  1724.3 MH/s (62.96ms)
Speed.Dev.#*.....: 12808.8 MH/s

Hashtype: Episerver 6.x >= .NET 4

Speed.Dev.#1.....:   747.5 MH/s (72.90ms)
Speed.Dev.#2.....:   754.2 MH/s (72.26ms)
Speed.Dev.#3.....:   720.5 MH/s (75.62ms)
Speed.Dev.#4.....:   728.9 MH/s (74.76ms)
Speed.Dev.#5.....:   713.4 MH/s (76.39ms)
Speed.Dev.#6.....:   764.9 MH/s (71.24ms)
Speed.Dev.#7.....:   733.3 MH/s (74.32ms)
Speed.Dev.#8.....:   756.2 MH/s (72.06ms)
Speed.Dev.#*.....:  5918.9 MH/s

Hashtype: Apache $apr1$ MD5, md5apr1, MD5 (APR)

Speed.Dev.#1.....:  2436.6 kH/s (86.20ms)
Speed.Dev.#2.....:  2589.9 kH/s (81.07ms)
Speed.Dev.#3.....:  2365.7 kH/s (88.84ms)
Speed.Dev.#4.....:  2513.5 kH/s (83.61ms)
Speed.Dev.#5.....:  2385.0 kH/s (88.09ms)
Speed.Dev.#6.....:  2629.5 kH/s (79.86ms)
Speed.Dev.#7.....:  2472.0 kH/s (84.97ms)
Speed.Dev.#8.....:  2610.1 kH/s (80.45ms)
Speed.Dev.#*.....: 20002.4 kH/s

Hashtype: ColdFusion 10+

Speed.Dev.#1.....:   440.0 MH/s (61.86ms)
Speed.Dev.#2.....:   456.5 MH/s (59.62ms)
Speed.Dev.#3.....:   426.3 MH/s (63.85ms)
Speed.Dev.#4.....:   431.1 MH/s (63.14ms)
Speed.Dev.#5.....:   419.0 MH/s (64.96ms)
Speed.Dev.#6.....:   444.8 MH/s (61.20ms)
Speed.Dev.#7.....:   435.1 MH/s (62.56ms)
Speed.Dev.#8.....:   444.2 MH/s (61.28ms)
Speed.Dev.#*.....:  3496.9 MH/s

Hashtype: hMailServer

Speed.Dev.#1.....:   762.2 MH/s (71.41ms)
Speed.Dev.#2.....:   760.8 MH/s (71.55ms)
Speed.Dev.#3.....:   693.6 MH/s (78.50ms)
Speed.Dev.#4.....:   728.8 MH/s (74.70ms)
Speed.Dev.#5.....:   706.9 MH/s (77.03ms)
Speed.Dev.#6.....:   776.2 MH/s (70.14ms)
Speed.Dev.#7.....:   745.0 MH/s (73.08ms)
Speed.Dev.#8.....:   779.2 MH/s (69.87ms)
Speed.Dev.#*.....:  5952.6 MH/s

Hashtype: nsldap, SHA-1(Base64), Netscape LDAP SHA

Speed.Dev.#1.....:  1910.6 MH/s (56.81ms)
Speed.Dev.#2.....:  1934.4 MH/s (56.12ms)
Speed.Dev.#3.....:  1817.8 MH/s (59.71ms)
Speed.Dev.#4.....:  1888.6 MH/s (57.48ms)
Speed.Dev.#5.....:  1819.0 MH/s (59.68ms)
Speed.Dev.#6.....:  1964.5 MH/s (55.25ms)
Speed.Dev.#7.....:  1896.5 MH/s (57.24ms)
Speed.Dev.#8.....:  1954.3 MH/s (55.54ms)
Speed.Dev.#*.....: 15185.7 MH/s

Hashtype: nsldaps, SSHA-1(Base64), Netscape LDAP SSHA

Speed.Dev.#1.....:  1877.0 MH/s (57.83ms)
Speed.Dev.#2.....:  1928.5 MH/s (56.29ms)
Speed.Dev.#3.....:  1795.6 MH/s (60.46ms)
Speed.Dev.#4.....:  1894.3 MH/s (57.30ms)
Speed.Dev.#5.....:  1824.4 MH/s (59.50ms)
Speed.Dev.#6.....:  2018.7 MH/s (53.68ms)
Speed.Dev.#7.....:  1839.5 MH/s (59.01ms)
Speed.Dev.#8.....:  1948.7 MH/s (55.70ms)
Speed.Dev.#*.....: 15126.5 MH/s

Hashtype: SSHA-256(Base64), LDAP {SSHA256}

Speed.Dev.#1.....:   810.1 MH/s (67.26ms)
Speed.Dev.#2.....:   816.0 MH/s (66.78ms)
Speed.Dev.#3.....:   773.8 MH/s (70.42ms)
Speed.Dev.#4.....:   800.0 MH/s (68.11ms)
Speed.Dev.#5.....:   785.7 MH/s (69.35ms)
Speed.Dev.#6.....:   836.5 MH/s (65.14ms)
Speed.Dev.#7.....:   804.7 MH/s (67.72ms)
Speed.Dev.#8.....:   805.8 MH/s (67.63ms)
Speed.Dev.#*.....:  6432.5 MH/s

Hashtype: SSHA-512(Base64), LDAP {SSHA512}

Speed.Dev.#1.....:   215.8 MH/s (63.12ms)
Speed.Dev.#2.....:   210.8 MH/s (64.62ms)
Speed.Dev.#3.....:   212.2 MH/s (64.20ms)
Speed.Dev.#4.....:   212.8 MH/s (64.01ms)
Speed.Dev.#5.....:   214.9 MH/s (63.38ms)
Speed.Dev.#6.....:   211.7 MH/s (64.35ms)
Speed.Dev.#7.....:   213.2 MH/s (63.90ms)
Speed.Dev.#8.....:   210.5 MH/s (64.71ms)
Speed.Dev.#*.....:  1702.0 MH/s

Hashtype: LM

Speed.Dev.#1.....:  3823.7 MH/s (56.88ms)
Speed.Dev.#2.....:  3786.1 MH/s (57.45ms)
Speed.Dev.#3.....:  3733.8 MH/s (58.26ms)
Speed.Dev.#4.....:  3754.3 MH/s (57.95ms)
Speed.Dev.#5.....:  3726.1 MH/s (58.36ms)
Speed.Dev.#6.....:  3807.0 MH/s (57.14ms)
Speed.Dev.#7.....:  3803.1 MH/s (57.19ms)
Speed.Dev.#8.....:  3752.2 MH/s (57.98ms)
Speed.Dev.#*.....: 30186.4 MH/s

Hashtype: NTLM

Speed.Dev.#1.....:  8195.2 MH/s (53.19ms)
Speed.Dev.#2.....:  8397.3 MH/s (51.90ms)
Speed.Dev.#3.....:  7930.3 MH/s (54.96ms)
Speed.Dev.#4.....:  8268.1 MH/s (52.72ms)
Speed.Dev.#5.....:  7688.1 MH/s (56.68ms)
Speed.Dev.#6.....:  8515.2 MH/s (51.18ms)
Speed.Dev.#7.....:  8073.4 MH/s (53.99ms)
Speed.Dev.#8.....:  8756.9 MH/s (49.77ms)
Speed.Dev.#*.....: 65824.6 MH/s

Hashtype: Domain Cached Credentials (DCC), MS Cache

Speed.Dev.#1.....:  2337.4 MH/s (93.27ms)
Speed.Dev.#2.....:  2412.7 MH/s (90.36ms)
Speed.Dev.#3.....:  2151.5 MH/s (50.45ms)
Speed.Dev.#4.....:  2323.1 MH/s (93.85ms)
Speed.Dev.#5.....:  2234.4 MH/s (48.57ms)
Speed.Dev.#6.....:  2417.3 MH/s (89.83ms)
Speed.Dev.#7.....:  2269.9 MH/s (95.66ms)
Speed.Dev.#8.....:  2358.8 MH/s (92.06ms)
Speed.Dev.#*.....: 18505.2 MH/s

Hashtype: Domain Cached Credentials 2 (DCC2), MS Cache 2

Speed.Dev.#1.....:    73920 H/s (71.92ms)
Speed.Dev.#2.....:    74979 H/s (70.89ms)
Speed.Dev.#3.....:    71845 H/s (73.99ms)
Speed.Dev.#4.....:    73854 H/s (71.99ms)
Speed.Dev.#5.....:    71719 H/s (74.12ms)
Speed.Dev.#6.....:    75270 H/s (70.62ms)
Speed.Dev.#7.....:    73362 H/s (72.47ms)
Speed.Dev.#8.....:    73970 H/s (71.88ms)
Speed.Dev.#*.....:   588.9 kH/s

Hashtype: DPAPI masterkey file v1 and v2

Speed.Dev.#1.....:    15757 H/s (71.77ms)
Speed.Dev.#2.....:    15921 H/s (71.05ms)
Speed.Dev.#3.....:    15651 H/s (72.27ms)
Speed.Dev.#4.....:    15298 H/s (73.93ms)
Speed.Dev.#5.....:    15364 H/s (73.59ms)
Speed.Dev.#6.....:    16192 H/s (69.88ms)
Speed.Dev.#7.....:    15863 H/s (71.32ms)
Speed.Dev.#8.....:    15694 H/s (72.06ms)
Speed.Dev.#*.....:   125.7 kH/s

Hashtype: MS-AzureSync PBKDF2-HMAC-SHA256

Speed.Dev.#1.....:  2734.0 kH/s (73.90ms)
Speed.Dev.#2.....:  2861.8 kH/s (70.51ms)
Speed.Dev.#3.....:  2654.4 kH/s (76.45ms)
Speed.Dev.#4.....:  2854.1 kH/s (71.07ms)
Speed.Dev.#5.....:  2622.3 kH/s (77.31ms)
Speed.Dev.#6.....:  2882.7 kH/s (70.02ms)
Speed.Dev.#7.....:  2760.5 kH/s (73.14ms)
Speed.Dev.#8.....:  2861.5 kH/s (70.58ms)
Speed.Dev.#*.....: 22231.3 kH/s

Hashtype: descrypt, DES (Unix), Traditional DES

Speed.Dev.#1.....:   155.4 MH/s (87.57ms)
Speed.Dev.#2.....:   153.6 MH/s (88.59ms)
Speed.Dev.#3.....:   174.6 MH/s (77.92ms)
Speed.Dev.#4.....:   173.4 MH/s (78.42ms)
Speed.Dev.#5.....:   148.8 MH/s (91.43ms)
Speed.Dev.#6.....:   174.5 MH/s (77.95ms)
Speed.Dev.#7.....:   155.7 MH/s (87.37ms)
Speed.Dev.#8.....:   143.5 MH/s (94.85ms)
Speed.Dev.#*.....:  1279.5 MH/s

Hashtype: BSDi Crypt, Extended DES

Speed.Dev.#1.....:   582.1 kH/s (60.53ms)
Speed.Dev.#2.....:   582.1 kH/s (60.55ms)
Speed.Dev.#3.....:   550.8 kH/s (64.02ms)
Speed.Dev.#4.....:   571.3 kH/s (61.72ms)
Speed.Dev.#5.....:   564.7 kH/s (62.40ms)
Speed.Dev.#6.....:   590.0 kH/s (59.73ms)
Speed.Dev.#7.....:   574.9 kH/s (61.30ms)
Speed.Dev.#8.....:   580.9 kH/s (60.67ms)
Speed.Dev.#*.....:  4596.8 kH/s

Hashtype: md5crypt, MD5 (Unix), Cisco-IOS $1$ (MD5)

Speed.Dev.#1.....:  2644.6 kH/s (59.50ms)
Speed.Dev.#2.....:  2562.6 kH/s (61.44ms)
Speed.Dev.#3.....:  2476.6 kH/s (63.61ms)
Speed.Dev.#4.....:  2513.3 kH/s (62.68ms)
Speed.Dev.#5.....:  2434.8 kH/s (64.69ms)
Speed.Dev.#6.....:  2632.2 kH/s (59.80ms)
Speed.Dev.#7.....:  2515.1 kH/s (62.61ms)
Speed.Dev.#8.....:  2595.2 kH/s (60.66ms)
Speed.Dev.#*.....: 20374.3 kH/s

Hashtype: bcrypt $2*$, Blowfish (Unix)

Speed.Dev.#1.....:     1920 H/s (48.71ms)
Speed.Dev.#2.....:     1868 H/s (25.02ms)
Speed.Dev.#3.....:     1913 H/s (48.88ms)
Speed.Dev.#4.....:     1912 H/s (48.94ms)
Speed.Dev.#5.....:     1916 H/s (48.83ms)
Speed.Dev.#6.....:     1926 H/s (48.58ms)
Speed.Dev.#7.....:     1932 H/s (48.43ms)
Speed.Dev.#8.....:     1909 H/s (49.02ms)
Speed.Dev.#*.....:    15296 H/s

Hashtype: sha256crypt $5$, SHA256 (Unix)

Speed.Dev.#1.....:   106.7 kH/s (50.32ms)
Speed.Dev.#2.....:   107.1 kH/s (50.12ms)
Speed.Dev.#3.....:   103.0 kH/s (52.10ms)
Speed.Dev.#4.....:   103.2 kH/s (52.03ms)
Speed.Dev.#5.....:   103.5 kH/s (51.85ms)
Speed.Dev.#6.....:   108.4 kH/s (49.52ms)
Speed.Dev.#7.....:   105.8 kH/s (50.72ms)
Speed.Dev.#8.....:   103.4 kH/s (51.91ms)
Speed.Dev.#*.....:   841.1 kH/s

Hashtype: sha512crypt $6$, SHA512 (Unix)

Speed.Dev.#1.....:    35083 H/s (76.92ms)
Speed.Dev.#2.....:    34725 H/s (77.72ms)
Speed.Dev.#3.....:    34015 H/s (79.34ms)
Speed.Dev.#4.....:    34094 H/s (79.16ms)
Speed.Dev.#5.....:    34284 H/s (78.72ms)
Speed.Dev.#6.....:    35178 H/s (76.72ms)
Speed.Dev.#7.....:    34679 H/s (77.82ms)
Speed.Dev.#8.....:    34905 H/s (77.30ms)
Speed.Dev.#*.....:   277.0 kH/s

Hashtype: OSX v10.4, OSX v10.5, OSX v10.6

Speed.Dev.#1.....:  1620.2 MH/s (67.00ms)
Speed.Dev.#2.....:  1626.6 MH/s (66.74ms)
Speed.Dev.#3.....:  1541.4 MH/s (70.43ms)
Speed.Dev.#4.....:  1579.7 MH/s (68.73ms)
Speed.Dev.#5.....:  1509.9 MH/s (71.90ms)
Speed.Dev.#6.....:  1655.3 MH/s (65.57ms)
Speed.Dev.#7.....:  1659.2 MH/s (65.41ms)
Speed.Dev.#8.....:  1698.0 MH/s (63.93ms)
Speed.Dev.#*.....: 12890.3 MH/s

Hashtype: OSX v10.7

Speed.Dev.#1.....:   221.3 MH/s (61.55ms)
Speed.Dev.#2.....:   219.8 MH/s (61.99ms)
Speed.Dev.#3.....:   214.7 MH/s (63.44ms)
Speed.Dev.#4.....:   215.5 MH/s (63.21ms)
Speed.Dev.#5.....:   213.2 MH/s (63.89ms)
Speed.Dev.#6.....:   224.4 MH/s (60.70ms)
Speed.Dev.#7.....:   217.7 MH/s (62.56ms)
Speed.Dev.#8.....:   222.4 MH/s (61.24ms)
Speed.Dev.#*.....:  1749.1 MH/s

Hashtype: OSX v10.8+ (PBKDF2-SHA512)

Speed.Dev.#1.....:     2681 H/s (71.49ms)
Speed.Dev.#2.....:     2675 H/s (71.66ms)
Speed.Dev.#3.....:     2617 H/s (72.84ms)
Speed.Dev.#4.....:     2614 H/s (72.90ms)
Speed.Dev.#5.....:     2616 H/s (73.29ms)
Speed.Dev.#6.....:     2704 H/s (70.49ms)
Speed.Dev.#7.....:     2618 H/s (72.80ms)
Speed.Dev.#8.....:     2672 H/s (71.74ms)
Speed.Dev.#*.....:    21198 H/s

Hashtype: AIX {smd5}

Speed.Dev.#1.....:  2498.6 kH/s (84.05ms)
Speed.Dev.#2.....:  2621.0 kH/s (80.12ms)
Speed.Dev.#3.....:  2382.9 kH/s (88.20ms)
Speed.Dev.#4.....:  2544.2 kH/s (82.59ms)
Speed.Dev.#5.....:  2471.8 kH/s (84.95ms)
Speed.Dev.#6.....:  2622.5 kH/s (80.07ms)
Speed.Dev.#7.....:  2453.2 kH/s (64.21ms)
Speed.Dev.#8.....:  2668.3 kH/s (78.69ms)
Speed.Dev.#*.....: 20262.6 kH/s

Hashtype: AIX {ssha1}

Speed.Dev.#1.....: 10674.8 kH/s (71.39ms)
Speed.Dev.#2.....: 10952.0 kH/s (69.53ms)
Speed.Dev.#3.....:  9788.3 kH/s (78.44ms)
Speed.Dev.#4.....: 10443.0 kH/s (73.34ms)
Speed.Dev.#5.....:  9660.3 kH/s (79.24ms)
Speed.Dev.#6.....: 10816.2 kH/s (70.53ms)
Speed.Dev.#7.....: 10363.8 kH/s (73.77ms)
Speed.Dev.#8.....: 10440.7 kH/s (73.24ms)
Speed.Dev.#*.....: 83139.0 kH/s

Hashtype: AIX {ssha256}

Speed.Dev.#1.....:  4142.2 kH/s (96.44ms)
Speed.Dev.#2.....:  4123.3 kH/s (96.95ms)
Speed.Dev.#3.....:  3964.8 kH/s (100.90ms)
Speed.Dev.#4.....:  3988.8 kH/s (100.40ms)
Speed.Dev.#5.....:  3944.4 kH/s (101.35ms)
Speed.Dev.#6.....:  4160.3 kH/s (96.05ms)
Speed.Dev.#7.....:  4055.0 kH/s (98.53ms)
Speed.Dev.#8.....:  4085.2 kH/s (97.83ms)
Speed.Dev.#*.....: 32464.0 kH/s

Hashtype: AIX {ssha512}

Speed.Dev.#1.....:  1400.2 kH/s (72.70ms)
Speed.Dev.#2.....:  1443.3 kH/s (70.47ms)
Speed.Dev.#3.....:  1358.8 kH/s (74.90ms)
Speed.Dev.#4.....:  1434.0 kH/s (71.02ms)
Speed.Dev.#5.....:  1347.6 kH/s (75.54ms)
Speed.Dev.#6.....:  1445.9 kH/s (70.33ms)
Speed.Dev.#7.....:  1405.1 kH/s (72.42ms)
Speed.Dev.#8.....:  1439.3 kH/s (70.62ms)
Speed.Dev.#*.....: 11274.2 kH/s

Hashtype: Cisco-PIX MD5

Speed.Dev.#1.....:  3297.9 MH/s (66.09ms)
Speed.Dev.#2.....:  3359.8 MH/s (64.87ms)
Speed.Dev.#3.....:  3197.7 MH/s (68.17ms)
Speed.Dev.#4.....:  3268.7 MH/s (66.68ms)
Speed.Dev.#5.....:  3159.9 MH/s (68.98ms)
Speed.Dev.#6.....:  3491.3 MH/s (62.43ms)
Speed.Dev.#7.....:  3324.4 MH/s (65.57ms)
Speed.Dev.#8.....:  3401.8 MH/s (64.07ms)
Speed.Dev.#*.....: 26501.7 MH/s

Hashtype: Cisco-ASA MD5

Speed.Dev.#1.....:  3399.2 MH/s (64.12ms)
Speed.Dev.#2.....:  3410.3 MH/s (63.89ms)
Speed.Dev.#3.....:  3223.8 MH/s (67.61ms)
Speed.Dev.#4.....:  3289.7 MH/s (66.26ms)
Speed.Dev.#5.....:  3170.3 MH/s (68.74ms)
Speed.Dev.#6.....:  3464.9 MH/s (62.88ms)
Speed.Dev.#7.....:  3388.5 MH/s (64.32ms)
Speed.Dev.#8.....:  3432.2 MH/s (63.50ms)
Speed.Dev.#*.....: 26778.9 MH/s

Hashtype: Cisco-IOS type 4 (SHA256)

Speed.Dev.#1.....:   786.1 MH/s (69.23ms)
Speed.Dev.#2.....:   839.7 MH/s (64.83ms)
Speed.Dev.#3.....:   757.2 MH/s (71.88ms)
Speed.Dev.#4.....:   792.1 MH/s (68.72ms)
Speed.Dev.#5.....:   754.7 MH/s (72.11ms)
Speed.Dev.#6.....:   833.7 MH/s (65.36ms)
Speed.Dev.#7.....:   784.6 MH/s (69.37ms)
Speed.Dev.#8.....:   832.8 MH/s (65.36ms)
Speed.Dev.#*.....:  6381.0 MH/s

Hashtype: Cisco-IOS $8$ (PBKDF2-SHA256)

Speed.Dev.#1.....:    14531 H/s (93.50ms)
Speed.Dev.#2.....:    14499 H/s (93.71ms)
Speed.Dev.#3.....:    14092 H/s (96.35ms)
Speed.Dev.#4.....:    13985 H/s (97.09ms)
Speed.Dev.#5.....:    13857 H/s (49.07ms)
Speed.Dev.#6.....:    14718 H/s (92.38ms)
Speed.Dev.#7.....:    14151 H/s (95.94ms)
Speed.Dev.#8.....:    14546 H/s (93.40ms)
Speed.Dev.#*.....:   114.4 kH/s

Hashtype: Cisco-IOS $9$ (scrypt)

Speed.Dev.#1.....:     4940 H/s (10724.57ms)
Speed.Dev.#2.....:     5016 H/s (10563.57ms)
Speed.Dev.#3.....:     4830 H/s (10971.78ms)
Speed.Dev.#4.....:     4860 H/s (10900.44ms)
Speed.Dev.#5.....:     4848 H/s (10928.33ms)
Speed.Dev.#6.....:     5037 H/s (10514.92ms)
Speed.Dev.#7.....:     4906 H/s (10797.20ms)
Speed.Dev.#8.....:     4997 H/s (10598.92ms)
Speed.Dev.#*.....:    39435 H/s

Hashtype: Juniper NetScreen/SSG (ScreenOS)

Speed.Dev.#1.....:  2949.8 MH/s (73.89ms)
Speed.Dev.#2.....:  2890.0 MH/s (75.43ms)
Speed.Dev.#3.....:  2794.8 MH/s (78.00ms)
Speed.Dev.#4.....:  2853.6 MH/s (76.39ms)
Speed.Dev.#5.....:  2791.9 MH/s (78.07ms)
Speed.Dev.#6.....:  2943.4 MH/s (74.06ms)
Speed.Dev.#7.....:  2850.4 MH/s (76.46ms)
Speed.Dev.#8.....:  2969.3 MH/s (73.41ms)
Speed.Dev.#*.....: 23043.1 MH/s

Hashtype: Juniper IVE

Speed.Dev.#1.....:  2422.5 kH/s (86.72ms)
Speed.Dev.#2.....:  2576.8 kH/s (81.51ms)
Speed.Dev.#3.....:  2407.0 kH/s (87.29ms)
Speed.Dev.#4.....:  2533.3 kH/s (82.94ms)
Speed.Dev.#5.....:  2403.3 kH/s (87.41ms)
Speed.Dev.#6.....:  2644.6 kH/s (79.39ms)
Speed.Dev.#7.....:  2432.6 kH/s (86.35ms)
Speed.Dev.#8.....:  2586.5 kH/s (81.20ms)
Speed.Dev.#*.....: 20006.6 kH/s

Hashtype: Samsung Android Password/PIN

Speed.Dev.#1.....:  1356.6 kH/s (64.88ms)
Speed.Dev.#2.....:  1372.6 kH/s (64.13ms)
Speed.Dev.#3.....:  1303.2 kH/s (67.57ms)
Speed.Dev.#4.....:  1332.4 kH/s (66.09ms)
Speed.Dev.#5.....:  1264.5 kH/s (69.64ms)
Speed.Dev.#6.....:  1394.5 kH/s (63.12ms)
Speed.Dev.#7.....:  1318.4 kH/s (66.78ms)
Speed.Dev.#8.....:  1392.3 kH/s (63.22ms)
Speed.Dev.#*.....: 10734.3 kH/s

Hashtype: Citrix NetScaler

Speed.Dev.#1.....:  1745.0 MH/s (62.21ms)
Speed.Dev.#2.....:  1893.1 MH/s (57.34ms)
Speed.Dev.#3.....:  1670.6 MH/s (64.99ms)
Speed.Dev.#4.....:  1745.9 MH/s (62.18ms)
Speed.Dev.#5.....:  1671.1 MH/s (64.96ms)
Speed.Dev.#6.....:  1833.8 MH/s (59.19ms)
Speed.Dev.#7.....:  1738.8 MH/s (62.43ms)
Speed.Dev.#8.....:  1755.8 MH/s (61.82ms)
Speed.Dev.#*.....: 14054.1 MH/s

Hashtype: RACF

Speed.Dev.#1.....:   707.0 MH/s (76.78ms)
Speed.Dev.#2.....:   696.1 MH/s (77.97ms)
Speed.Dev.#3.....:   690.1 MH/s (78.98ms)
Speed.Dev.#4.....:   703.2 MH/s (77.50ms)
Speed.Dev.#5.....:   693.8 MH/s (78.54ms)
Speed.Dev.#6.....:   702.0 MH/s (77.63ms)
Speed.Dev.#7.....:   699.3 MH/s (77.93ms)
Speed.Dev.#8.....:   697.0 MH/s (77.88ms)
Speed.Dev.#*.....:  5588.5 MH/s

Hashtype: GRUB 2

Speed.Dev.#1.....:     9490 H/s (70.82ms)
Speed.Dev.#2.....:     9382 H/s (71.63ms)
Speed.Dev.#3.....:     9183 H/s (73.01ms)
Speed.Dev.#4.....:     9182 H/s (73.02ms)
Speed.Dev.#5.....:     9133 H/s (73.47ms)
Speed.Dev.#6.....:     9527 H/s (70.55ms)
Speed.Dev.#7.....:     9224 H/s (72.68ms)
Speed.Dev.#8.....:     9340 H/s (71.78ms)
Speed.Dev.#*.....:    74461 H/s

Hashtype: Radmin2

Speed.Dev.#1.....:  1610.1 MH/s (67.42ms)
Speed.Dev.#2.....:  1671.3 MH/s (64.95ms)
Speed.Dev.#3.....:  1526.4 MH/s (71.13ms)
Speed.Dev.#4.....:  1635.9 MH/s (66.36ms)
Speed.Dev.#5.....:  1541.9 MH/s (70.41ms)
Speed.Dev.#6.....:  1662.2 MH/s (65.30ms)
Speed.Dev.#7.....:  1523.1 MH/s (71.28ms)
Speed.Dev.#8.....:  1656.7 MH/s (65.53ms)
Speed.Dev.#*.....: 12827.6 MH/s

Hashtype: SAP CODVN B (BCODE)

Speed.Dev.#1.....:   494.5 MH/s (55.03ms)
Speed.Dev.#2.....:   490.9 MH/s (55.45ms)
Speed.Dev.#3.....:   534.0 MH/s (101.96ms)
Speed.Dev.#4.....:   560.6 MH/s (97.12ms)
Speed.Dev.#5.....:   493.1 MH/s (55.18ms)
Speed.Dev.#6.....:   492.8 MH/s (55.23ms)
Speed.Dev.#7.....:   491.7 MH/s (55.34ms)
Speed.Dev.#8.....:   490.2 MH/s (55.49ms)
Speed.Dev.#*.....:  4047.7 MH/s

Hashtype: SAP CODVN F/G (PASSCODE)

Speed.Dev.#1.....:   233.7 MH/s (116.49ms)
Speed.Dev.#2.....:   231.2 MH/s (117.78ms)
Speed.Dev.#3.....:   229.2 MH/s (118.80ms)
Speed.Dev.#4.....:   227.2 MH/s (119.81ms)
Speed.Dev.#5.....:   231.2 MH/s (117.74ms)
Speed.Dev.#6.....:   236.2 MH/s (115.28ms)
Speed.Dev.#7.....:   229.4 MH/s (118.70ms)
Speed.Dev.#8.....:   231.4 MH/s (117.68ms)
Speed.Dev.#*.....:  1849.5 MH/s

Hashtype: SAP CODVN H (PWDSALTEDHASH) iSSHA-1

Speed.Dev.#1.....:  1369.9 kH/s (64.15ms)
Speed.Dev.#2.....:  1513.5 kH/s (58.05ms)
Speed.Dev.#3.....:  1366.9 kH/s (64.30ms)
Speed.Dev.#4.....:  1401.1 kH/s (62.75ms)
Speed.Dev.#5.....:  1334.5 kH/s (65.86ms)
Speed.Dev.#6.....:  1507.2 kH/s (58.28ms)
Speed.Dev.#7.....:  1413.9 kH/s (62.14ms)
Speed.Dev.#8.....:  1455.3 kH/s (60.37ms)
Speed.Dev.#*.....: 11362.3 kH/s

Hashtype: Lotus Notes/Domino 5

Speed.Dev.#1.....: 59472.1 kH/s (113.22ms)
Speed.Dev.#2.....: 59433.3 kH/s (113.30ms)
Speed.Dev.#3.....: 59443.3 kH/s (113.28ms)
Speed.Dev.#4.....: 58856.8 kH/s (114.41ms)
Speed.Dev.#5.....: 59455.3 kH/s (113.24ms)
Speed.Dev.#6.....: 59477.9 kH/s (113.20ms)
Speed.Dev.#7.....: 59532.6 kH/s (113.09ms)
Speed.Dev.#8.....: 59219.1 kH/s (113.71ms)
Speed.Dev.#*.....:   474.9 MH/s

Hashtype: Lotus Notes/Domino 6

Speed.Dev.#1.....: 12993.3 kH/s (65.53ms)
Speed.Dev.#2.....: 12976.6 kH/s (65.60ms)
Speed.Dev.#3.....: 14300.5 kH/s (59.53ms)
Speed.Dev.#4.....: 14168.3 kH/s (60.09ms)
Speed.Dev.#5.....: 12996.8 kH/s (65.51ms)
Speed.Dev.#6.....: 13039.4 kH/s (65.29ms)
Speed.Dev.#7.....: 12977.0 kH/s (65.59ms)
Speed.Dev.#8.....: 12958.5 kH/s (65.70ms)
Speed.Dev.#*.....:   106.4 MH/s

Hashtype: Lotus Notes/Domino 8

Speed.Dev.#1.....:   151.1 kH/s (70.08ms)
Speed.Dev.#2.....:   153.1 kH/s (69.15ms)
Speed.Dev.#3.....:   147.2 kH/s (71.93ms)
Speed.Dev.#4.....:   150.2 kH/s (70.52ms)
Speed.Dev.#5.....:   146.6 kH/s (72.22ms)
Speed.Dev.#6.....:   153.9 kH/s (68.78ms)
Speed.Dev.#7.....:   146.0 kH/s (72.53ms)
Speed.Dev.#8.....:   150.5 kH/s (70.33ms)
Speed.Dev.#*.....:  1198.6 kH/s

Hashtype: PeopleSoft

Speed.Dev.#1.....:  1718.5 MH/s (63.16ms)
Speed.Dev.#2.....:  1799.2 MH/s (60.33ms)
Speed.Dev.#3.....:  1693.5 MH/s (64.10ms)
Speed.Dev.#4.....:  1818.3 MH/s (59.70ms)
Speed.Dev.#5.....:  1713.9 MH/s (63.32ms)
Speed.Dev.#6.....:  1852.9 MH/s (58.58ms)
Speed.Dev.#7.....:  1834.0 MH/s (59.19ms)
Speed.Dev.#8.....:  1818.3 MH/s (59.69ms)
Speed.Dev.#*.....: 14248.6 MH/s

Hashtype: PeopleSoft PS_TOKEN

Speed.Dev.#1.....:   713.2 MH/s (76.41ms)
Speed.Dev.#2.....:   713.7 MH/s (76.35ms)
Speed.Dev.#3.....:   691.7 MH/s (78.78ms)
Speed.Dev.#4.....:   699.7 MH/s (77.89ms)
Speed.Dev.#5.....:   706.7 MH/s (77.12ms)
Speed.Dev.#6.....:   726.5 MH/s (74.94ms)
Speed.Dev.#7.....:   715.1 MH/s (76.21ms)
Speed.Dev.#8.....:   718.8 MH/s (75.75ms)
Speed.Dev.#*.....:  5685.5 MH/s

Hashtype: 7-Zip

Speed.Dev.#1.....:     2390 H/s (85.63ms)
Speed.Dev.#2.....:     2368 H/s (86.43ms)
Speed.Dev.#3.....:     2360 H/s (87.46ms)
Speed.Dev.#4.....:     2344 H/s (88.06ms)
Speed.Dev.#5.....:     2352 H/s (87.74ms)
Speed.Dev.#6.....:     2375 H/s (86.18ms)
Speed.Dev.#7.....:     2357 H/s (87.54ms)
Speed.Dev.#8.....:     2363 H/s (86.62ms)
Speed.Dev.#*.....:    18909 H/s

Hashtype: WinZip

Speed.Dev.#1.....:   241.2 kH/s (51.18ms)
Speed.Dev.#2.....:   248.1 kH/s (49.75ms)
Speed.Dev.#3.....:   236.8 kH/s (52.21ms)
Speed.Dev.#4.....:   240.0 kH/s (51.52ms)
Speed.Dev.#5.....:   231.1 kH/s (53.47ms)
Speed.Dev.#6.....:   248.7 kH/s (49.62ms)
Speed.Dev.#7.....:   234.7 kH/s (52.61ms)
Speed.Dev.#8.....:   241.7 kH/s (51.08ms)
Speed.Dev.#*.....:  1922.3 kH/s

Hashtype: RAR3-hp

Speed.Dev.#1.....:    11501 H/s (72.25ms)
Speed.Dev.#2.....:    11621 H/s (71.50ms)
Speed.Dev.#3.....:    11415 H/s (72.80ms)
Speed.Dev.#4.....:    11399 H/s (72.90ms)
Speed.Dev.#5.....:    11036 H/s (75.30ms)
Speed.Dev.#6.....:    11717 H/s (70.92ms)
Speed.Dev.#7.....:    11429 H/s (72.71ms)
Speed.Dev.#8.....:    11487 H/s (72.34ms)
Speed.Dev.#*.....:    91604 H/s

Hashtype: RAR5

Speed.Dev.#1.....:     8767 H/s (94.70ms)
Speed.Dev.#2.....:     8855 H/s (93.76ms)
Speed.Dev.#3.....:     8643 H/s (47.96ms)
Speed.Dev.#4.....:     8520 H/s (97.29ms)
Speed.Dev.#5.....:     8450 H/s (49.15ms)
Speed.Dev.#6.....:     8964 H/s (92.46ms)
Speed.Dev.#7.....:     8635 H/s (95.98ms)
Speed.Dev.#8.....:     8891 H/s (93.39ms)
Speed.Dev.#*.....:    69726 H/s

Hashtype: AxCrypt

Speed.Dev.#1.....:    36087 H/s (150.85ms)
Speed.Dev.#2.....:    35809 H/s (152.10ms)
Speed.Dev.#3.....:    35925 H/s (151.61ms)
Speed.Dev.#4.....:    35524 H/s (153.33ms)
Speed.Dev.#5.....:    36284 H/s (150.04ms)
Speed.Dev.#6.....:    36119 H/s (150.72ms)
Speed.Dev.#7.....:    36178 H/s (150.48ms)
Speed.Dev.#8.....:    36133 H/s (150.67ms)
Speed.Dev.#*.....:   288.1 kH/s

Hashtype: AxCrypt in-memory SHA1

Speed.Dev.#1.....:  1702.2 MH/s (63.77ms)
Speed.Dev.#2.....:  1755.4 MH/s (61.84ms)
Speed.Dev.#3.....:  1640.2 MH/s (66.19ms)
Speed.Dev.#4.....:  1748.2 MH/s (62.10ms)
Speed.Dev.#5.....:  1649.5 MH/s (65.81ms)
Speed.Dev.#6.....:  1798.4 MH/s (60.36ms)
Speed.Dev.#7.....:  1630.6 MH/s (66.58ms)
Speed.Dev.#8.....:  1782.0 MH/s (60.92ms)
Speed.Dev.#*.....: 13706.4 MH/s

Hashtype: TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit

Speed.Dev.#1.....:    63884 H/s (49.97ms)
Speed.Dev.#2.....:    63877 H/s (49.99ms)
Speed.Dev.#3.....:    61825 H/s (51.72ms)
Speed.Dev.#4.....:    62021 H/s (51.51ms)
Speed.Dev.#5.....:    60831 H/s (52.53ms)
Speed.Dev.#6.....:    65171 H/s (49.00ms)
Speed.Dev.#7.....:    62733 H/s (50.93ms)
Speed.Dev.#8.....:    63570 H/s (50.25ms)
Speed.Dev.#*.....:   503.9 kH/s

Hashtype: TrueCrypt PBKDF2-HMAC-SHA512 + XTS 512 bit

Speed.Dev.#1.....:    90615 H/s (66.52ms)
Speed.Dev.#2.....:    90470 H/s (66.61ms)
Speed.Dev.#3.....:    87097 H/s (69.19ms)
Speed.Dev.#4.....:    88952 H/s (67.73ms)
Speed.Dev.#5.....:    86290 H/s (69.88ms)
Speed.Dev.#6.....:    91569 H/s (65.81ms)
Speed.Dev.#7.....:    88518 H/s (68.05ms)
Speed.Dev.#8.....:    90183 H/s (66.87ms)
Speed.Dev.#*.....:   713.7 kH/s

Hashtype: TrueCrypt PBKDF2-HMAC-Whirlpool + XTS 512 bit

Speed.Dev.#1.....:    11288 H/s (141.95ms)
Speed.Dev.#2.....:    11201 H/s (143.06ms)
Speed.Dev.#3.....:    11227 H/s (142.73ms)
Speed.Dev.#4.....:    11128 H/s (144.00ms)
Speed.Dev.#5.....:    11240 H/s (142.57ms)
Speed.Dev.#6.....:    11236 H/s (142.62ms)
Speed.Dev.#7.....:    11291 H/s (141.92ms)
Speed.Dev.#8.....:    11195 H/s (143.14ms)
Speed.Dev.#*.....:    89806 H/s

Hashtype: TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit + boot-mode

Speed.Dev.#1.....:   121.6 kH/s (48.35ms)
Speed.Dev.#2.....:   126.5 kH/s (90.91ms)
Speed.Dev.#3.....:   122.4 kH/s (94.07ms)
Speed.Dev.#4.....:   121.9 kH/s (94.56ms)
Speed.Dev.#5.....:   117.0 kH/s (98.79ms)
Speed.Dev.#6.....:   130.3 kH/s (89.85ms)
Speed.Dev.#7.....:   120.6 kH/s (48.81ms)
Speed.Dev.#8.....:   123.7 kH/s (47.40ms)
Speed.Dev.#*.....:   984.1 kH/s

Hashtype: VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit

Speed.Dev.#1.....:      186 H/s (50.83ms)
Speed.Dev.#2.....:      187 H/s (50.60ms)
Speed.Dev.#3.....:      186 H/s (52.12ms)
Speed.Dev.#4.....:      185 H/s (52.31ms)
Speed.Dev.#5.....:      187 H/s (52.43ms)
Speed.Dev.#6.....:      186 H/s (49.64ms)
Speed.Dev.#7.....:      187 H/s (51.86ms)
Speed.Dev.#8.....:      186 H/s (50.84ms)
Speed.Dev.#*.....:     1491 H/s

Hashtype: VeraCrypt PBKDF2-HMAC-SHA512 + XTS 512 bit

Speed.Dev.#1.....:      187 H/s (70.57ms)
Speed.Dev.#2.....:      187 H/s (70.71ms)
Speed.Dev.#3.....:      156 H/s (73.35ms)
Speed.Dev.#4.....:      155 H/s (72.12ms)
Speed.Dev.#5.....:      155 H/s (73.78ms)
Speed.Dev.#6.....:      187 H/s (69.62ms)
Speed.Dev.#7.....:      184 H/s (71.68ms)
Speed.Dev.#8.....:      186 H/s (71.27ms)
Speed.Dev.#*.....:     1397 H/s

Hashtype: VeraCrypt PBKDF2-HMAC-Whirlpool + XTS 512 bit

Speed.Dev.#1.....:        0 H/s (148.57ms)
Speed.Dev.#2.....:        0 H/s (149.69ms)
Speed.Dev.#3.....:        0 H/s (149.04ms)
Speed.Dev.#4.....:        0 H/s (150.56ms)
Speed.Dev.#5.....:        0 H/s (149.01ms)
Speed.Dev.#6.....:        0 H/s (149.22ms)
Speed.Dev.#7.....:        0 H/s (148.46ms)
Speed.Dev.#8.....:        0 H/s (149.70ms)
Speed.Dev.#*.....:        0 H/s

Hashtype: VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit + boot-mode

Speed.Dev.#1.....:      403 H/s (50.82ms)
Speed.Dev.#2.....:      406 H/s (50.47ms)
Speed.Dev.#3.....:      372 H/s (52.17ms)
Speed.Dev.#4.....:      371 H/s (52.34ms)
Speed.Dev.#5.....:      373 H/s (52.71ms)
Speed.Dev.#6.....:      403 H/s (49.61ms)
Speed.Dev.#7.....:      374 H/s (51.84ms)
Speed.Dev.#8.....:      402 H/s (51.01ms)
Speed.Dev.#*.....:     3103 H/s

Hashtype: VeraCrypt PBKDF2-HMAC-SHA256 + XTS 512 bit

Speed.Dev.#1.....:      277 H/s (92.26ms)
Speed.Dev.#2.....:      279 H/s (91.58ms)
Speed.Dev.#3.....:      247 H/s (49.21ms)
Speed.Dev.#4.....:      250 H/s (49.35ms)
Speed.Dev.#5.....:      249 H/s (49.46ms)
Speed.Dev.#6.....:      280 H/s (91.13ms)
Speed.Dev.#7.....:      278 H/s (93.93ms)
Speed.Dev.#8.....:      277 H/s (92.25ms)
Speed.Dev.#*.....:     2137 H/s

Hashtype: VeraCrypt PBKDF2-HMAC-SHA256 + XTS 512 bit + boot-mode

Speed.Dev.#1.....:      682 H/s (95.89ms)
Speed.Dev.#2.....:      715 H/s (91.33ms)
Speed.Dev.#3.....:      680 H/s (49.24ms)
Speed.Dev.#4.....:      655 H/s (49.38ms)
Speed.Dev.#5.....:      652 H/s (50.19ms)
Speed.Dev.#6.....:      716 H/s (93.28ms)
Speed.Dev.#7.....:      687 H/s (97.48ms)
Speed.Dev.#8.....:      685 H/s (95.44ms)
Speed.Dev.#*.....:     5470 H/s

Hashtype: Android FDE <= 4.3

Speed.Dev.#1.....:   184.6 kH/s (71.57ms)
Speed.Dev.#2.....:   191.3 kH/s (69.08ms)
Speed.Dev.#3.....:   182.6 kH/s (72.39ms)
Speed.Dev.#4.....:   185.7 kH/s (71.17ms)
Speed.Dev.#5.....:   182.5 kH/s (72.38ms)
Speed.Dev.#6.....:   192.4 kH/s (68.63ms)
Speed.Dev.#7.....:   182.1 kH/s (72.54ms)
Speed.Dev.#8.....:   186.9 kH/s (70.70ms)
Speed.Dev.#*.....:  1488.0 kH/s

Hashtype: Android FDE (Samsung DEK)

Speed.Dev.#1.....:    70213 H/s (94.60ms)
Speed.Dev.#2.....:    70719 H/s (93.93ms)
Speed.Dev.#3.....:    67787 H/s (48.97ms)
Speed.Dev.#4.....:    68385 H/s (97.15ms)
Speed.Dev.#5.....:    67787 H/s (97.99ms)
Speed.Dev.#6.....:    71802 H/s (92.50ms)
Speed.Dev.#7.....:    69147 H/s (96.06ms)
Speed.Dev.#8.....:    71175 H/s (93.32ms)
Speed.Dev.#*.....:   557.0 kH/s

Hashtype: eCryptfs

Speed.Dev.#1.....:     2595 H/s (79.59ms)
Speed.Dev.#2.....:     2552 H/s (80.57ms)
Speed.Dev.#3.....:     2545 H/s (80.79ms)
Speed.Dev.#4.....:     2557 H/s (80.42ms)
Speed.Dev.#5.....:     2583 H/s (79.96ms)
Speed.Dev.#6.....:     2554 H/s (80.51ms)
Speed.Dev.#7.....:     2591 H/s (79.72ms)
Speed.Dev.#8.....:     2551 H/s (80.60ms)
Speed.Dev.#*.....:    20528 H/s

Hashtype: MS Office <= 2003 $0/$1, MD5 + RC4

Speed.Dev.#1.....: 42914.4 kH/s (79.36ms)
Speed.Dev.#2.....: 42563.3 kH/s (80.03ms)
Speed.Dev.#3.....: 42926.8 kH/s (79.35ms)
Speed.Dev.#4.....: 42493.2 kH/s (80.14ms)
Speed.Dev.#5.....: 42882.5 kH/s (79.42ms)
Speed.Dev.#6.....: 42524.0 kH/s (80.10ms)
Speed.Dev.#7.....: 42851.8 kH/s (79.49ms)
Speed.Dev.#8.....: 42440.3 kH/s (80.26ms)
Speed.Dev.#*.....:   341.6 MH/s

Hashtype: MS Office <= 2003 $0/$1, MD5 + RC4, collider #1

Speed.Dev.#1.....: 56552.8 kH/s (120.47ms)
Speed.Dev.#2.....: 55998.9 kH/s (121.67ms)
Speed.Dev.#3.....: 56431.5 kH/s (120.72ms)
Speed.Dev.#4.....: 55838.4 kH/s (122.02ms)
Speed.Dev.#5.....: 56393.7 kH/s (120.82ms)
Speed.Dev.#6.....: 55951.6 kH/s (121.77ms)
Speed.Dev.#7.....: 56450.7 kH/s (120.70ms)
Speed.Dev.#8.....: 56253.1 kH/s (121.12ms)
Speed.Dev.#*.....:   449.9 MH/s

Hashtype: MS Office <= 2003 $3/$4, SHA1 + RC4

Speed.Dev.#1.....: 53798.6 kH/s (126.65ms)
Speed.Dev.#2.....: 52909.9 kH/s (128.78ms)
Speed.Dev.#3.....: 53322.2 kH/s (127.78ms)
Speed.Dev.#4.....: 53018.5 kH/s (128.49ms)
Speed.Dev.#5.....: 53232.2 kH/s (128.00ms)
Speed.Dev.#6.....: 53301.3 kH/s (127.83ms)
Speed.Dev.#7.....: 53741.3 kH/s (126.79ms)
Speed.Dev.#8.....: 53154.1 kH/s (128.18ms)
Speed.Dev.#*.....:   426.5 MH/s

Hashtype: MS Office <= 2003 $3, SHA1 + RC4, collider #1

Speed.Dev.#1.....: 58753.4 kH/s (115.96ms)
Speed.Dev.#2.....: 58279.6 kH/s (116.91ms)
Speed.Dev.#3.....: 58649.7 kH/s (116.16ms)
Speed.Dev.#4.....: 58119.1 kH/s (117.23ms)
Speed.Dev.#5.....: 58653.3 kH/s (116.16ms)
Speed.Dev.#6.....: 58135.5 kH/s (117.19ms)
Speed.Dev.#7.....: 58690.6 kH/s (116.08ms)
Speed.Dev.#8.....: 58373.5 kH/s (116.71ms)
Speed.Dev.#*.....:   467.7 MH/s

Hashtype: MS Office 2007

Speed.Dev.#1.....:    31012 H/s (69.94ms)
Speed.Dev.#2.....:    31137 H/s (69.66ms)
Speed.Dev.#3.....:    29857 H/s (72.64ms)
Speed.Dev.#4.....:    30200 H/s (71.82ms)
Speed.Dev.#5.....:    29889 H/s (72.56ms)
Speed.Dev.#6.....:    31621 H/s (68.60ms)
Speed.Dev.#7.....:    30043 H/s (72.19ms)
Speed.Dev.#8.....:    30409 H/s (71.33ms)
Speed.Dev.#*.....:   244.2 kH/s

Hashtype: MS Office 2010

Speed.Dev.#1.....:    15360 H/s (70.60ms)
Speed.Dev.#2.....:    15544 H/s (69.70ms)
Speed.Dev.#3.....:    15038 H/s (72.04ms)
Speed.Dev.#4.....:    15066 H/s (71.91ms)
Speed.Dev.#5.....:    15083 H/s (71.82ms)
Speed.Dev.#6.....:    15822 H/s (68.55ms)
Speed.Dev.#7.....:    15010 H/s (72.17ms)
Speed.Dev.#8.....:    15249 H/s (71.12ms)
Speed.Dev.#*.....:   122.2 kH/s

Hashtype: MS Office 2013

Speed.Dev.#1.....:     1812 H/s (74.33ms)
Speed.Dev.#2.....:     1796 H/s (75.09ms)
Speed.Dev.#3.....:     1777 H/s (75.97ms)
Speed.Dev.#4.....:     1766 H/s (76.44ms)
Speed.Dev.#5.....:     1771 H/s (76.21ms)
Speed.Dev.#6.....:     1799 H/s (74.96ms)
Speed.Dev.#7.....:     1781 H/s (75.73ms)
Speed.Dev.#8.....:     1788 H/s (75.40ms)
Speed.Dev.#*.....:    14290 H/s

Hashtype: PDF 1.1 - 1.3 (Acrobat 2 - 4)

Speed.Dev.#1.....: 58809.1 kH/s (115.85ms)
Speed.Dev.#2.....: 57914.2 kH/s (117.65ms)
Speed.Dev.#3.....: 58281.6 kH/s (116.90ms)
Speed.Dev.#4.....: 58118.6 kH/s (117.23ms)
Speed.Dev.#5.....: 58257.7 kH/s (116.95ms)
Speed.Dev.#6.....: 57973.9 kH/s (117.40ms)
Speed.Dev.#7.....: 58621.2 kH/s (116.12ms)
Speed.Dev.#8.....: 58170.2 kH/s (117.13ms)
Speed.Dev.#*.....:   466.1 MH/s

Hashtype: PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #1

Speed.Dev.#1.....: 64752.7 kH/s (105.22ms)
Speed.Dev.#2.....: 64048.1 kH/s (106.35ms)
Speed.Dev.#3.....: 64661.8 kH/s (105.36ms)
Speed.Dev.#4.....: 64057.7 kH/s (106.36ms)
Speed.Dev.#5.....: 64508.2 kH/s (105.61ms)
Speed.Dev.#6.....: 64025.3 kH/s (106.41ms)
Speed.Dev.#7.....: 64775.5 kH/s (105.18ms)
Speed.Dev.#8.....: 64418.6 kH/s (105.76ms)
Speed.Dev.#*.....:   515.2 MH/s

Hashtype: PDF 1.4 - 1.6 (Acrobat 5 - 8)

Speed.Dev.#1.....:  2852.5 kH/s (58.67ms)
Speed.Dev.#2.....:  2812.1 kH/s (59.52ms)
Speed.Dev.#3.....:  2863.2 kH/s (58.47ms)
Speed.Dev.#4.....:  2835.8 kH/s (59.05ms)
Speed.Dev.#5.....:  2839.6 kH/s (58.95ms)
Speed.Dev.#6.....:  2869.2 kH/s (145.90ms)
Speed.Dev.#7.....:  2891.8 kH/s (144.46ms)
Speed.Dev.#8.....:  2830.5 kH/s (59.14ms)
Speed.Dev.#*.....: 22794.7 kH/s

Hashtype: PDF 1.7 Level 3 (Acrobat 9)

Speed.Dev.#1.....:   827.1 MH/s (65.88ms)
Speed.Dev.#2.....:   815.4 MH/s (66.83ms)
Speed.Dev.#3.....:   797.8 MH/s (68.30ms)
Speed.Dev.#4.....:   804.3 MH/s (67.75ms)
Speed.Dev.#5.....:   796.8 MH/s (68.39ms)
Speed.Dev.#6.....:   834.1 MH/s (65.33ms)
Speed.Dev.#7.....:   766.0 MH/s (71.07ms)
Speed.Dev.#8.....:   810.3 MH/s (67.24ms)
Speed.Dev.#*.....:  6451.9 MH/s

Hashtype: PDF 1.7 Level 8 (Acrobat 10 - 11)

Speed.Dev.#1.....:     8201 H/s (368.84ms)
Speed.Dev.#2.....:     8130 H/s (372.05ms)
Speed.Dev.#3.....:     8237 H/s (367.22ms)
Speed.Dev.#4.....:     8207 H/s (368.55ms)
Speed.Dev.#5.....:     8272 H/s (365.67ms)
Speed.Dev.#6.....:     8126 H/s (372.25ms)
Speed.Dev.#7.....:     8264 H/s (366.04ms)
Speed.Dev.#8.....:     8115 H/s (372.77ms)
Speed.Dev.#*.....:    65552 H/s

Hashtype: Password Safe v2

Speed.Dev.#1.....:    54309 H/s (41.26ms)
Speed.Dev.#2.....:    53759 H/s (41.68ms)
Speed.Dev.#3.....:    54340 H/s (41.23ms)
Speed.Dev.#4.....:    54039 H/s (41.46ms)
Speed.Dev.#5.....:    54147 H/s (41.40ms)
Speed.Dev.#6.....:    54215 H/s (41.35ms)
Speed.Dev.#7.....:    54536 H/s (41.09ms)
Speed.Dev.#8.....:    53836 H/s (41.63ms)
Speed.Dev.#*.....:   433.2 kH/s

Hashtype: Password Safe v3

Speed.Dev.#1.....:   318.2 kH/s (83.45ms)
Speed.Dev.#2.....:   321.0 kH/s (82.71ms)
Speed.Dev.#3.....:   314.7 kH/s (84.40ms)
Speed.Dev.#4.....:   312.5 kH/s (84.97ms)
Speed.Dev.#5.....:   310.4 kH/s (85.54ms)
Speed.Dev.#6.....:   326.8 kH/s (81.27ms)
Speed.Dev.#7.....:   310.7 kH/s (85.48ms)
Speed.Dev.#8.....:   321.1 kH/s (79.12ms)
Speed.Dev.#*.....:  2535.4 kH/s

Hashtype: LastPass + LastPass sniffed

Speed.Dev.#1.....:   603.3 kH/s (75.97ms)
Speed.Dev.#2.....:   596.2 kH/s (76.91ms)
Speed.Dev.#3.....:   556.0 kH/s (82.49ms)
Speed.Dev.#4.....:   583.7 kH/s (78.57ms)
Speed.Dev.#5.....:   557.6 kH/s (82.26ms)
Speed.Dev.#6.....:   607.5 kH/s (75.47ms)
Speed.Dev.#7.....:   566.2 kH/s (80.99ms)
Speed.Dev.#8.....:   602.1 kH/s (76.14ms)
Speed.Dev.#*.....:  4672.5 kH/s

Hashtype: 1Password, agilekeychain

Speed.Dev.#1.....:   767.9 kH/s (59.96ms)
Speed.Dev.#2.....:   776.8 kH/s (59.30ms)
Speed.Dev.#3.....:   740.0 kH/s (62.26ms)
Speed.Dev.#4.....:   761.9 kH/s (60.47ms)
Speed.Dev.#5.....:   726.6 kH/s (63.42ms)
Speed.Dev.#6.....:   781.6 kH/s (58.94ms)
Speed.Dev.#7.....:   758.8 kH/s (60.70ms)
Speed.Dev.#8.....:   760.5 kH/s (60.58ms)
Speed.Dev.#*.....:  6074.0 kH/s

Hashtype: 1Password, cloudkeychain

Speed.Dev.#1.....:     2360 H/s (70.95ms)
Speed.Dev.#2.....:     2373 H/s (70.56ms)
Speed.Dev.#3.....:     2305 H/s (72.00ms)
Speed.Dev.#4.....:     2305 H/s (71.97ms)
Speed.Dev.#5.....:     2265 H/s (73.55ms)
Speed.Dev.#6.....:     2396 H/s (69.61ms)
Speed.Dev.#7.....:     2312 H/s (71.75ms)
Speed.Dev.#8.....:     2364 H/s (70.86ms)
Speed.Dev.#*.....:    18680 H/s

Hashtype: Bitcoin/Litecoin wallet.dat

Speed.Dev.#1.....:      834 H/s (79.60ms)
Speed.Dev.#2.....:      838 H/s (80.79ms)
Speed.Dev.#3.....:      842 H/s (80.38ms)
Speed.Dev.#4.....:      839 H/s (80.70ms)
Speed.Dev.#5.....:      829 H/s (80.13ms)
Speed.Dev.#6.....:      839 H/s (80.65ms)
Speed.Dev.#7.....:      832 H/s (79.80ms)
Speed.Dev.#8.....:      839 H/s (80.72ms)
Speed.Dev.#*.....:     6692 H/s

Hashtype: Blockchain, My Wallet

Speed.Dev.#1.....: 17286.4 kH/s (60.77ms)
Speed.Dev.#2.....: 18413.8 kH/s (56.75ms)
Speed.Dev.#3.....: 16909.4 kH/s (62.71ms)
Speed.Dev.#4.....: 18194.5 kH/s (58.13ms)
Speed.Dev.#5.....: 16810.2 kH/s (62.60ms)
Speed.Dev.#6.....: 18488.2 kH/s (56.80ms)
Speed.Dev.#7.....: 17670.2 kH/s (59.92ms)
Speed.Dev.#8.....: 18344.4 kH/s (56.99ms)
Speed.Dev.#*.....:   142.1 MH/s

Hashtype: Blockchain, My Wallet, V2

Speed.Dev.#1.....:    72873 H/s (74.26ms)
Speed.Dev.#2.....:    73039 H/s (74.09ms)
Speed.Dev.#3.....:    70921 H/s (76.37ms)
Speed.Dev.#4.....:    71484 H/s (75.77ms)
Speed.Dev.#5.....:    71231 H/s (76.03ms)
Speed.Dev.#6.....:    74242 H/s (72.89ms)
Speed.Dev.#7.....:    70760 H/s (76.54ms)
Speed.Dev.#8.....:    72024 H/s (75.14ms)
Speed.Dev.#*.....:   576.6 kH/s

Hashtype: KeePass 1 (AES/Twofish) and KeePass 2 (AES)

Speed.Dev.#1.....:    43945 H/s (206.23ms)
Speed.Dev.#2.....:    43490 H/s (208.40ms)
Speed.Dev.#3.....:    43557 H/s (208.07ms)
Speed.Dev.#4.....:    43230 H/s (209.66ms)
Speed.Dev.#5.....:    43954 H/s (206.18ms)
Speed.Dev.#6.....:    43745 H/s (207.18ms)
Speed.Dev.#7.....:    43751 H/s (207.15ms)
Speed.Dev.#8.....:    43343 H/s (209.10ms)
Speed.Dev.#*.....:   349.0 kH/s

Hashtype: JKS Java Key Store Private Keys (SHA1)

Speed.Dev.#1.....:  1803.2 MH/s (60.17ms)
Speed.Dev.#2.....:  1920.9 MH/s (56.48ms)
Speed.Dev.#3.....:  1730.9 MH/s (62.70ms)
Speed.Dev.#4.....:  1871.1 MH/s (58.00ms)
Speed.Dev.#5.....:  1730.6 MH/s (62.71ms)
Speed.Dev.#6.....:  1903.5 MH/s (57.00ms)
Speed.Dev.#7.....:  1859.5 MH/s (58.35ms)
Speed.Dev.#8.....:  1907.1 MH/s (56.90ms)
Speed.Dev.#*.....: 14727.0 MH/s

Hashtype: Ethereum Wallet, PBKDF2-HMAC-SHA256

Speed.Dev.#1.....:     1077 H/s (94.34ms)
Speed.Dev.#2.....:     1084 H/s (93.73ms)
Speed.Dev.#3.....:     1048 H/s (96.36ms)
Speed.Dev.#4.....:     1054 H/s (95.81ms)
Speed.Dev.#5.....:     1047 H/s (96.51ms)
Speed.Dev.#6.....:     1106 H/s (92.42ms)
Speed.Dev.#7.....:     1052 H/s (48.02ms)
Speed.Dev.#8.....:     1089 H/s (93.27ms)
Speed.Dev.#*.....:     8557 H/s

Hashtype: ArubaOS

Speed.Dev.#1.....:  1559.5 MH/s (69.59ms)
Speed.Dev.#2.....:  1651.2 MH/s (65.73ms)
Speed.Dev.#3.....:  1569.5 MH/s (69.16ms)
Speed.Dev.#4.....:  1580.2 MH/s (68.68ms)
Speed.Dev.#5.....:  1575.6 MH/s (68.88ms)
Speed.Dev.#6.....:  1656.5 MH/s (65.51ms)
Speed.Dev.#7.....:  1601.6 MH/s (67.76ms)
Speed.Dev.#8.....:  1612.0 MH/s (67.33ms)
Speed.Dev.#*.....: 12806.1 MH/s

Hashtype: ChaCha20

Speed.Dev.#1.....:  1300.2 MH/s (83.50ms)
Speed.Dev.#2.....:  1296.7 MH/s (83.72ms)
Speed.Dev.#3.....:  1178.6 MH/s (92.48ms)
Speed.Dev.#4.....:  1262.7 MH/s (85.99ms)
Speed.Dev.#5.....:  1233.6 MH/s (88.02ms)
Speed.Dev.#6.....:  1297.2 MH/s (84.03ms)
Speed.Dev.#7.....:  1306.5 MH/s (83.10ms)
Speed.Dev.#8.....:  1261.9 MH/s (86.04ms)
Speed.Dev.#*.....: 10137.6 MH/s

Started: Fri Aug  4 11:00:40 2017
Stopped: Fri Aug  4 12:07:48 2017
```
