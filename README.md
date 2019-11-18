# TileCalPhaseIIGUI
Development of a GUI for the ATLAS phase-II TileCal testbench for the electronics demonstarator. This is under development at Stockholm University. The GUI will be python-based, allowing the user to interact with the different tests one can perform with the combined Mother/DaughterBoard configuration in the ATLAS TileCal firmware. The testing procedure is based on the Prometeo testbench. Prometeo is the full certification testbench for the TileCal demonstrator and includes software for tests using a lightweight version of the IPbus protocol which allows communication with the FPGAs on the demonstrator boards. The demonstrator itself is an implementation to the phase-II digital calorimeter readout system which is integrated into the full "mini-drawer + PMT" mechanics of the upgraded TileCal. The basic readout workflow can be summarised:

1) The 3-in-1 front-end board which delivers analogue signals from the PMTs with two different gains for later digitization, integrated current output, and an analogue trigger output compatible with the Level 1 trigger output.

2) The MainBoard (MB) which collects data from the front-end board, with discrete analogue-to-digital (ADC) converters for the each PMT signal.

3) The DaughterBoard (DB) collects the digital readout from the MB. Tbe DB consists of GBTx chips and FPGAs for logic processing. 

Prometeo can now be thought off as a testbench designed to provide all of the functionality to access the certification procedure of the 3-in-1 --> MB --> DB processing in one mini-drawer for the phase-II TileCal. The software for performing such standalone functionality tests is available but requies some updates and cleaning (this is an ongoing project). This code, which is to be made configurable with this GUI, is currently internal to ATLAS and can be found here: https://gitlab.cern.ch/fcarrio/prometeogui. The latest version, using separate configuration files, is under the "dev_MikeUpdates" branch and is still in the development phase. 

The current Prometeo testbench setup produces the following tests of the MB/DB configuration:

-- ADC Linearity: This test checks the linarity of the response in the analogue-to-digital conversion on the MB+DB setup.
-- CIS Linearity: This test checks the linearity of the response for a simulated charge injection in the demonstrator.
-- CIS Shape: This test checks the shape of the response for a simulated charge injection in the demonstrator.
-- Pedestal noise: This test checks the noise and determindes the pedestal for the demonstrator system under some response test. A pedestal can be thought off as the offset one must calculated and subtract, due to the presence of (typically) some form of fixed pattern noise in e.g. the detector readout electronics. 

These tests are currently carried out using the python scripts and configuration files found in https://gitlab.cern.ch/fcarrio/prometeogui/tree/dev_MikeUpdates/GUI/scripts. The final GUI produced here will allow the user to fully implement these tests without relying on the python wrapper itself, for ease of use. 

This work forms part of the larger project developing the demonstrator for the phase-II TileCal upgrade, documented in full here (note, internal to ATLAS): https://twiki.cern.ch/twiki/bin/view/Atlas/TileCalDemonstrator.
