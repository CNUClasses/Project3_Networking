**CPEN 475/575**

**Project 3:                 ** A multithreaded networked application

**Deliverables:        ** Please clean your Android Studio project and then zip the containing directory and submit.

**Target SDKs**  I will compile and test it on a Nexus 7 running API 22

**Overview:**

This is just an exercise to familiarize you with network communications, AsyncTask, and JSON.   Please install and run the example app to see behavior.

**Requirements  ** Create app that has/does the following;

- Please create a settings screen with one ListPreference.  It contains a choice of 2 URLs (see 1 in Helpful bits).  These are where both the json list of pet information and individual pet pics are stored
- Please create a listener on this URL setting that is notified when  it changes. The listener then sets the main UI accordingly.
- Please create a mainactivity with an appbar.
- The appbar  should have a spinner and an overflow icon that leads to settings.
- Please make all network calls on a separate thread.  You will have to download both text (JSON) and images.

**App Behaviour**

1. On startup the app checks for network connectivity, if there is none it should alert the user.
2. Next  the app will download the json file pets.json from the site selected in settings.
3. If this site cannot be reached (and the CNU one cannot) the app should tell the user what the server status code is and what link was tried.
4. The spinner is  dynamically  populated from information parsed from pets.json using standard Android JSONObject and JSONArray.  This is a flexible design that allows changes to the pets list.
5. The app downloads whichever pet the user specifies in the spinner and displays it in the background.
6. Any errors should be reported to the user via Toast or Snackbars.



**Helpful bits**

- **Sites where JSON and images are stored**

<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string-array name="JSON_URL_NAME">
        <item>CNU - Defender</item>
        <item>Pair - Teton Software - Pets</item>


    </string-array>
    <string-array name="JSON_URL">
        <item>http://www.pcs.cnu.edu/~kperkins/pets/</item>
        <item>http://www.tetonsoftware.com/pets/</item>

    </string-array>
</resources>

- **Getting the JSON info**

The file containing the json data is named pets.json.  Assumming you are using the tetonsoftware site (since it is the one that works) download pets.json with this URL.

http://www.tetonsoftware.com/pets/pets.json

it will return the following JSON text

http://www.tetonsoftware.com/pets/pets.json
it will return the following JSON text
{
"pets":[
	{	
	"name":"Winston",
	"file":"p0.png"
	},
	{	
	"name":"Higgens",
	"file":"p1.png"
	},
	{	
	"name":"Broccoli",
	"file":"p2.png"
	}
	]
}

Use the info in the name and file fields to populate the spinner.  Please use 1 list only to hold this data, something like List&lt;pet&gt; myList.  It will be part of the adapter associated with the spinner.  The pet object just holds the name and its associated file.

- **Downloading the image associated with the pet the user choose**

Once the user selects a pet by name download its associated image.  For example if the user selected Winston above, you would download p0.png using the following link.

http://www.tetonsoftware.com/pets/p0.png

**Preference listener** – Make sure your preference listener is a member of your main activity (See [http://stackoverflow.com/questions/2542938/sharedpreferences-onsharedpreferencechangelistener-not-being-called-consistently](http://stackoverflow.com/questions/2542938/sharedpreferences-onsharedpreferencechangelistener-not-being-called-consistently) for why).  This means you have something like the following example;

 ![Alt text](./ART/1.png?raw=true "Figure 1")
