# stdinfo v0.1

Disclaimer: This is in active beta and has not yet been verified to be cryptographically secure. Use at your own risk.
This program serves as the foundation and API core for ONITO's 'STDinfo' that uses secure multiparty computation to allow users to know if they can have safe sex with each other without sharing their STD (sexually transmitted disease) medical reports with each other or a 3rd party.

Dependencies:
MPyC

To run main.py, open 3 command terminals in the directory where elderly.py is stored. 
In terminal 1, run 'python main.py -M3 -I0 00010'. Terminal 1 is operated by user 1. '00010' is a distilled STD panel report where 0 denotes negative test result, 1 denotes positive test result, and the index in this bit string denotes a specific sexually transmitted disease on the panel. 
In terminal 2, run 'python main.py -M3 -I1 00000'. Terminal 2 is operated by user 2. '00000' is the distilled STD panel data (all STDs tested for were negative).
In terminal 3, run 'python main.py -M3 -I2'. Terminal 3 is an oblivious matchmaker needed for secure computation. It receives no data from both parties and transmits no data.

STD panel reports are converted to bit strings. This is referred to as distilled STD panel data. Indexes are specific for each disease, 0 denotes negative result (no infection), and 1 denotes positive result (infected).


Index 0 is chlamydia


Index 1 is HIV


Index 2 is gonorrhea


Index 3 is syphilis


Index 4 is hepatitis B


Index 5 is hepatitis C

Current strategy is to simply perform bitwise XOR on both bit strings. If both partners have a disease (1 in same index) or both don't have a disease (0 in same index), then XOR returns 0, else XOR returns 1 if one partner has a disease and the other doesn't. All XORs must return 0 to return an output of 0 denoting safe sex is possible, else 1 is returned denoting unsafe sex.

Next steps:


Performing this secure multiparty computation on Android and iOS apps natively without Internet access


Incorporating a safety feature to warn about pregnancy for partners who both test positive for an STD because STDs can transfer through childbirth


Incorporating document parsing to convert STD panel reports in PDF form to distilled STD panel bit strings, done natively on device without transferring medical data to a 
third party
