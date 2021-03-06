Gqrx
====

Gqrx is an experimental software defined radio receiver implemented using GNU Radio and the Qt GUI toolkit. Currently it works on Linux and Mac and supports the following devices:
- Funcube Dongle Pro and Pro+
- RTL2832U-based DVB-T dongles (rtlsdr)
- OsmoSDR
- USRP
- HackRF Jawbreaker
- basically any device supported by gr-osmosdr library

Gqrx can operate as a traditional AM/FM/SSB receiver outputting audio or as an FFT-only instrument.

The following sections are some rather generic instructions for building the latest v2.1-git series.


Dependencies
------------

- GNU Radio 3.7 with the following components:
    - gnuradio-runtime
    - gnuradio-analog
    - gnuradio-blocks
    - gnuradio-filter
    - gnuradio-fft
    - gnuradio-audio
- The gr-iqbalance library (optional)
- At least one of:
    - Funcube Dongle Pro driver via gnuradio-fcd
    - UHD driver via gnuradio-uhd
    - Funcube Dongle Pro+ driver from https://github.com/dl1ksv/gr-fcdproplus
    - RTL-SDR driver from http://cgit.osmocom.org/cgit/rtl-sdr/
    - OsmoSDR driver from http://cgit.osmocom.org/cgit/osmo-sdr/
    - HackRF Jawbreaker driver from http://greatscottgadgets.com/hackrf/
- gnuradio-osmosdr from http://cgit.osmocom.org/cgit/gr-osmosdr/
- pulseaudio (Linux only and optional)
- Qt 4.6 or later and optionally Qt Creator (gqrx works with Qt 5)


Installation
------------

Get the latest code from: https://github.com/csete/gqrx
If you are compiling on Mac open gqrx.pro in Qt Creator and comment out the "AUDIO_BACKEND = pulse" line. You can now build gqrx from within Qt Creator (click build) or in a terminal:
$ qmake gqrx.pro
$ make

To build in debug mode add "CONFIG+=debug" to the qmake step above.

Various snapshot releases (source and binaries) are avaialble from:
http://sourceforge.net/projects/gqrx/

Third party app bundle for Macs can be downloaded here:
http://dekar.wc3edit.net/2012/09/30/osx-port-of-the-awesome-gqrx-sdr-software/

The binary packages are bundles containing the necessary GNU Radio, UHD, rtlsdr and Boost libraries.

Usage
-----

If you have been running pre-2.1, please delete $HOME/.config/gqrx/*
Gqrx will now open a device configuration dialog when you start and it will automatically detect all supported input devices that are plugged in.

If you don't see your device it could be that you forgot to add the udev rule to /etc/udev/rules.d/
You can test your device first with rtl_test, qthid, or uhd_usrp_probe that come with the respective packages.

Gqrx supports multiple configurations and sessions if you have several devices or if you want to use the same device under different configurations. You can load a configuratio from the GUI or using the -c command line argument. See "gqrx --help" for a complete list of command line arguments.


Known problems
--------------

- Reconfiguring a device may lead to application freeze or crash.
- Funcube Dongle may not work well on systems with libusb-1.0.9 (try gqrx-2.0 instead).
- Some settings are not saved between sessions.


Getting help and reporting bugs
-------------------------------

There is now a Google group for discussing anything related to Gqrx: https://groups.google.com/forum/#!forum/gqrx
This includes getting help with installation and troubleshooting. Please remember to provide detailed description of your problem, your setup, what steps you followed, etc.


Credits and License
-------------------

Gqrx is designed and written by Alexandru Csete OZ9AEC, and it is licensed under the GNU General Public License.
Some of the source files were adopted from Cutesdr by Moe Weatley and these come with a BSD license.
Following people and organisations have contributed:

Alex Grinkov:
- FM stereo demodulator.

Anthony Willard:
- Various fixes and improvements

Elias Önal:
- Building Gqrx on Mac OS X.
- Crash recovery dialog.

Frank Brickle, AB2KT:
Bob McGwier, N4HY:
- Noise blanker (from dttsp).

Göran Weinholt, SM6-8239:
- Various GUI improvements.

Jiří Pinkava:
- Port to gnuradio 3.7 API

Moe Weatley:
- FFT plotter and waterfall.
- Frequency selector.
- Signal strength indicator.
- AGC

Nadeem Hasan:
- Bug fixes.

Nokia:
- QtColorPicker widget.

Vesa Solonen:
- DC removal in AM demodulator.

Vincent Pelletier
- Initial work on the horizontal zooming / scrolling.

Also thanks to Volker Schroer and Alexey Bazhin for bringing Funcube Dongle Pro+ support to GNU Radio and Gqrx.
Some icons are from the GNOME and Tango icon themes.
The scope.svg icon is based on the utilities-system-monitor.svg icon from the Mint-X icon theme licensed under GNU GPL.

Let me know if somebody or someting is missing from the list!

Alex OZ9AEC
