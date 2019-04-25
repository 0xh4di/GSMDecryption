# GSMDecryption
A5/1 Decryption

### Overview
This open source software allows the 'cracking' of A5/1 keys used to encrypt GSM 2G calls and SMS.
The cracking utility Kraken, developed by Frank A. Stevenson, is written in C++/python and runs on AMD GPUs or CPUs.
Kraken leverages rainbow tables that were computed as a community effort.


### Code
The Kraken git can be fetched with
```bash
git clone https://github.com/0xh4di/kraken.git
```

### Rainbow tables
1. Through [BitTorrent](https://github.com/0xh4di/GSMDecryption/tree/master/files)
2. From [Google Drive](https://drive.google.com/drive/folders/0B-8F5I-fE6lFQk1HY1pTWGJyM3M)


### Decrypting GSM phone calls
![A5/1 Decryption](https://srlabs.de/wp-content/uploads/2010/07/img_8872-low-rise_gr%C3%B6%C3%9Fe_bearbeitet.jpg)
#### Motivation
GSM telephony is the world’s most popular communication technology spanning most countries and connecting over four billion devices. The security standards for voice and text messaging date back to 1990 and have never been overhauled. Our GSM Security Project creates tools to test and document vulnerabilities in GSM networks around the world so to ignite the discussion over whether GSM calls can and should be secured. The project is summarized in this [Black Hat 2010 presentation](https://srlabs.de/wp-content/uploads/2010/07/100729.Breaking.GSM_.Privacy.BlackHat1-1.pdf).

#### Recording calls
GSM data can be recorded off the air using, for example, a programmable radio such as the USRP. GnuRadio provides the tools to record channels while Airprobe’s gsm-receiver decodes the control traffic and—in scenarios where no encryption is used or where the encryption key is known—also decodes voice traffic.

#### Cracking A5/1
When GSM uses A5/1 encryption, the secret key can be extracted from recorded traffic. Given two encrypted known plaintext messages, the Kraken utility that runs on a PC finds the secret key with around 90% probability within seconds in a set of rainbow tables. Our current table set took 2 months to compute and contains 40 tables for a total of 2TB. Further details on cracking A5/1 using rainbow tables are provided in this white paper: [Attacking Phone Privacy](https://srlabs.de/wp-content/uploads/2010/07/Attacking.Phone_.Privacy_Karsten.Nohl_1-1.pdf).

#### Defenses
Short term protocol patches already exists that make cracking much harder by not disclosing known plaintext unnecessarily ([3GPP TS44.006](http://www.3gpp.org/DynaReport/44006.htm), Section 5.2). These patched should be deployed with high priority. In the long term, GSM (2G) will not provide sufficient security and stronger alternatives such as UMTS (3G) and LTE (4G) should be preferred.

#### Tools
The following tools are used to analyze voice calls:

![Tools](https://srlabs.de/wp-content/uploads/2016/04/tools-500x88.png)
* [GnuRadio](http://gnuradio.org/) is included in recent Linux distributions
Recording data requires a programmable radio receiver such as the [USRP](https://www.ettus.com/product)
* Airprobe is available through: git clone https://github.com/0xh4di/airprobe
* Kraken is available through: git clone https://github.com/0xh4di/kraken
Kraken uses rainbow tables that are available through [files](https://github.com/0xh4di/GSMDecryption/tree/master/files).

Please use these tools carefully and never intentionally record other people’s conversations. 
