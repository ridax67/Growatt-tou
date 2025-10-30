# Growatt-tou
Growatt tou display and edit from Home Assistant with the Solax modbus hacs integration

To install this card follow these steps.

1.  This card assumes the Solax modbus integration use growatt_inverter as prefix.  If your configuration yu need to search and replace the card and automation yaml files.
2.  Install the following hacs packages: button-card, state-switch and browser-mod. After having downloaded browser-mod you need to add it as an integration,  After that is done, you need to t go to the left menu and select browser-mod there and enable 'Register' there.
3.  Add the contents of growatt-tou-automation.yaml file to your automations.yaml file (if your configuration file includes it)  or include it directly in the configuration.yaml file with a line 'automation: !include growatt-tou-automation.yaml'
4.  Add the line 'input_select: !include growatt-tou-input-select.yaml'
5.  Activate all tou-related fields in the modbus integration (Time 1-9 Update, Time 1-9 Activate, Time 1-9 Begin, Time 1-9 End, Time 1-9 Mode and Time 1-9 Activate_read, Time 1-9 Begin_read, Time 1-9 End_read, Time 1-9 Mode_read).  The only tou related enntries you won't need are Time 1-9 Clear.
6. This step is not necessary, but I recommend it.  It will let you set your tou starting every 00/15/30/45 minute and end every 14/29/44/59 minute.  Otherwise it will be every 5th minute for both begin and end which is not that practical as the list will be very long and you can't set the same time as end in one entry and begin in another.  Thus you can't swítch directly from battery to grid.  To apply the modification for the Solax modbus integration for growatt you copy the const.py and plugin_growatt.py to homeassistant/custom_components/solax_modbus/ and overwrite the files existing there.
7. Create a manual card in Home Assisstant and empty it and paste the contents of growatt-tou-card.yaml


Once the card is working it will display a list of tou entries numbered 1-9 each with begin/end-time, mode and active.  Below this list is a single row of icons with the corresponding fields.  There are up and down arrows to select which line in the list you work with.  When pressing the send button the line in the list will be updated once the inverter has accepted it.  If it not updated, there could be overlapping active lines that prevent it from being accepted. 

Mikael Wahlgren
