# **Epson Printer**
The `epsonprinter` platform allows you to monitor the ink levels of a Epson Workforce/EcoTank(ET) printers from Home
Assistant.

## Installation
### Manual installation
1) Download the component
2) Place the folder custom_components/switch_manager into the config/custom_components/ path of your home assistant installation
3) Restart Home Assistant
4) add configuration to your `configuration.yaml`

### HACS Installation
1) Open HACS Dashboard and add the following repository at custom repository submenu in the 3-dotted menu on top right corner: [https://github.com/cociweb/hacs-epson](https://github.com/cociweb/hacs-epson)
2) Search and Download Epson Printer component with HACS
4) Restart Home Assistant
5) add configuration to your `configuration.yaml`

## Configuration
To add Epson Printer integration to your installation, add the following to your `configuration.yaml` file:

```
sensor:
  - platform: epsonprinter
    host: IP_ADDRESS
    monitored_conditions:
    - black
    - photoblack
    - yellow
    - magenta
    - cyan
    - clean
    verify_ssl: false
    protocol: "https"
```


host:<br>
&ensp; description: The host name or address of the Epson workforce printer<br>
&ensp; required: true<br>
&ensp; type: string <br>
monitored_conditions:<br>
&ensp; description: The cartridge colours to monitor.<br>
&ensp; required: true<br>
&ensp; type: list<br>
&ensp; keys:<br>
&ensp; &ensp; black:<br>
&ensp; &ensp; &ensp; description: The black ink cartridge<br>
&ensp; &ensp; photoblack:<br>
&ensp; &ensp; &ensp; description: The photo black ink cartridge (not supported by all printers).<br>
&ensp; &ensp; yellow:<br>
&ensp; &ensp; &ensp; description: The yellow ink cartridge.<br>
&ensp; &ensp; magenta:<br>
&ensp; &ensp; &ensp; description: The magenta (=red) ink cartridge.<br>
&ensp; &ensp; cyan:<br>
&ensp; &ensp; &ensp; description: The cyan (=blue) ink cartridge.<br>
&ensp; &ensp; clean:<br>
&ensp; &ensp; &ensp; description: The cleaning cartridge.<br>
protocol:<br>
&ensp; description: The type of the protocol: `HTTP` or `HTTPS`<br>
&ensp; required: false<br>
&ensp; type: string<br>
&ensp; default: http<br>
verify_ssl:<br>
&ensp; description: Verify the SSL chain or not.<br>
&ensp; required: false<br>
&ensp; type: boolean<br>
&ensp; default: false<br>


# Supported devices:

Epson Workforce (and some EcoTank) printers who publish a HTTP(S) page containing the ink cartridge levels

Tested devices:
- Epson WF2630
- Epson WF2660
- Epson WF3540
- Epson WF3620
- Epson WF3640
- Epson WF4820
- Epson EcoTank ET-77x0
- Epson ET-2650
- EPSON ET-2750
- Epson ET-4750
- Epson EcoTank ET-5150 (51x0)
- Epson EcoTank L3150
- Epson Expression Home XP-2100
- Epson Expression Home XP-2105

To make this module work you need to connect your printer to your LAN.
The best is to navigate to the status page of the printer to check if it shows the page with the ink levels on the URL `http(s)://<IP_ADDRESS>/PRESENTATION/HTML/TOP/PRTINFO.HTML`

# Links:
 - "https://www.home-assistant.io/integrations/epsonworkforce"
 - "https://pypi.org/project/epsonprinter/"
 - "https://github.com/cociweb/hacs-epson"
