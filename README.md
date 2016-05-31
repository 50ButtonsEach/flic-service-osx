# flic-service-osx

This is a Beta release of the Flic TCP socket server program that will later be integrated in the final Flic app for Mac. This server supports a simple, well-documented, API over a TCP socket to allow you to add new clients that can scan and connect Flic buttons and receive their button events. We decided to release a Beta version of this so that application developers can go ahed and start creating their own applications at this time.

**Notice:** If you are running the hax-with-flic-osx application then please uninstall that before installing this. Also, please submit new issues if you find anything that is incorrect or is not working properly.

**Installation and running**

1. Download the repository by pressing the "Download ZIP" button. 
2. Mount the dmg file and drag and drop the FlicServiceBeta.app to your applications folder.

That's it!

By default when running this application it will start the TCP server on port 5551 using the Any-interface (0.0.0.0). If you need to change this for some reason then you can do that by launching the application from the command line instead with the following arguments:

```
-i  --interface     If you leave this option out then it will default to 0.0.0.0. The only configurable option is: localhost
                    
-p  --port          The port that you want to tie the server to. Default is 5551.
```

So, for example, to tie the service to port 5555 on localhost you would run the following:

`open /Applications/FlicServiceBeta.app --args --interface localhost --port 5555`

**Compatibility**

This application requires OSX 10.10 or above operating systems running on a machine that supports Bluetooth Low Energy. It is unclear exactly which machines that have Bluetooth Low Energy support, but Apple supposedly started the transition around 2012. Running the following in a terminal will output the Bluetooth LMP Version:

	system_profiler -detailLevel full SPBluetoothDataType | grep "LMP Version"

Version 0x6 was the first one that supported Low Energy, but we cannot guarantee that this will be correct for all computers. Using a Bluetooth Low Energy compatible USB dongle should also work if it is just configured correctly.

**Documentation**

This application uses the same protocol as first introduced with our fliclib-linux-hci release. The documentation can be found in the [ProtocolDocumentation.md](https://github.com/50ButtonsEach/fliclib-linux-hci/blob/master/ProtocolDocumentation.md) file.

There are however a few thing in that protocol that have not yet been implemented in this application and those are:

The following fields in the EvtGetInfoResponse:

* `max_pending_connections`
* `max_concurrently_connected_buttons`
* `current_pending_connections`
* `currently_no_space_for_new_connection`

For now you can ignore those fields.

**Clients**

A few client libs are available [here](https://github.com/50ButtonsEach/fliclib-linux-hci/tree/master/clientlib).

A simple client implementation can be found [here](https://github.com/50ButtonsEach/fliclib-linux-hci/tree/master/simpleclient).







