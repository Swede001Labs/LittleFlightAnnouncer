# LittleFlightAnnouncer
Freeware add-on utility for MSFS 2024.

## About
LittleFlightAnnouncer plays announcements from the flight crew when various
events occur during a flight, such as reading safety instructions or announcing
seat belt status. The application includes several predefined announcements in
English, and you can edit or add your own announcements in a few other languages.

## Installation Instructions

Unzip the archive. You will find two folders:

- **LittleFlightAnnouncer**  
  This folder can be placed anywhere. The EXE file is the main application.

- **routeadapter-wasm-misc**  
  Copy this entire folder into your MSFS Community folder. This WASM module 
  reads the flight plan whenever it changes and sends it to the main application.

Restart MSFS if it’s already running to activate the WASM module.

## Usage Instructions
	
### Start a new flight in MSFS 2024.

When the application is running, it will automatically connect to
MSFS using SimConnect.

When you start a new free flight, create a flight plan using the
in sim EFB and send it to the avionics using the EFB menu. The
application will read the flight plan and show basic information
about the flight in the main window.

If you are using SimBrief, make sure you load or create the flight
plan in the SimBrief EFB app and click *Import into sim*. The
flightplan will then be sent to the avionics as if you had created
it using the default planner. When you do this, the flight plan is
also copied into the sims own planning tool.

Details in the flight plan are used to calculate the flight time and
distance which are used when playing different announcements during the
flight to inform the passengers.

If you change SID, STAR or approach, update the flight plan in the
default EFB planner and click *Send to avionics* again to update
the flight plan in the simulator if you want the time estimates to
be as good as possible.

As the flight continues, announcements will be played automatically when
certain events occur.

### The main menu

The application has a main menu with several options:

#### **Flight**
Shows the current flight information and also a log of all events
that have occurred and also all announcements that have been played. The
data on the page is updated automatically as the flight continues.

#### **Crew**
It is possible to change members in the flight crew. Currently
there are two roles which both can read announcements:
  - **Captain**
  - **Purser**

For each role, you can select a voice and a language. The
application comes with several voices and languages to choose from.
Note the difference between language and country, for example if
the language is English, you can choose country between GB or US.

It is also possible to have the application choose a random voice
for each flight. In that case, if 'Any' is selected in any
drop-down menu, all options are available to the random picker.

#### **Announcements**
This is where you can view or edit all of your various announcements. By
default, several built-in announcements are displayed, but it's easy to
edit them or add new ones.

Each announcement is governed by rules that determine when it should
be played. There can be several rules for each announcement, but the
announcement will be played if any of the rules are fulfilled. All
options for a specific rule must match for it to be considered as
fulfilled. When that happens, the announcement is played.

Some aircraft use SimConnect variables differently, and sometimes the
values are incorrect. For example, the default Asobo 737-8 Max has,
for unknown reasons, switched the values for the seat belt sign on and
off.

To fix this, create a new rule for the seat belt sign on announcement
and another rule for the seat belt sign off announcement. For these
new rules, select the specific aircraft type and choose the opposite
action.

When a rule specifies an aircraft type, it is always prioritized, so
all other rules that are not specific to that aircraft type will be
ignored. This ensures that the announcement will be played correctly
for that aircraft.

The announcement itself can be edited below the rules. Note that the
language of the announcement is dictated by the crew member's language
which is going to play the announcement. Please make sure the languages
for the selected role and the announcement itself match so that the
announcement read out can be understood.

It is possible to exclude certain aircraft from the announcement
playing. There are also restore buttons which will show up here and
there if something has changed. By restoring you can revert to
factory settings.

#### **Settings**
There are a few options that can be changed to suit you the best.

## Technical details
For those of you who are curious, it might be interesting to get an
insight into how the application works.

The main driver is a speech engine built upon an open source TTS
(Text To Speech) engine named Piper. Language models are downloaded
and cached as needed, and all text-to-speech conversions happen
locally on your computer. No need for any online AI engines!
Please note that each voice used requires a certain amount of local
storage space. The more voices you try, the more space will be used.

Flight plans are fetched from the sim using the *Planned Route API*
built into the sim. To use this API, a WASM module is needed. All the
other sim data used by the application is fetched using SimConnect.


## License
This software is released under an MIT-style license with the following restriction:
- **Commercial use is not permitted** without written permission from the author.
