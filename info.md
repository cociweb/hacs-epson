# **Epson Printer**
The `epsonprinter` platform allows you to monitor the ink levels of a Epson Workforce/EcoTank(ET) printers from Home
Assistant.

## Installation
### Manual installation
1) Download the component
2) Place the folder custom_components/switch_manager into the config/custom_components/ path of your home assistant installation
3) Restart Home Assistant
4) add configuration to your `configuration.yaml`

### HACS Insallation
1) 
[![Open HACS Dashboard and add the following repository at custom repository submenu in the 3-dotted menu on top right corner:](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/) [https://github.com/cociweb/hacs-epson](https://github.com/cociweb/hacs-epson)
2) Search and Download Epson Printer component with HACS
3) Restart Home Assistant
4) add configuration to your `configuration.yaml`

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


host:
  description: The host name or address of the Epson workforce printer
  required: true
  type: string
monitored_conditions:
  description: The cartridge colours to monitor.
  required: true
  type: list
  keys:
    black:
      description: The black ink cartridge
    photoblack:
      description: The photo black ink cartridge (not supported by all printers).
    yellow:
      description: The yellow ink cartridge.
    magenta:
      description: The magenta (=red) ink cartridge.
    cyan:
      description: The cyan (=blue) ink cartridge.
    clean:
      description: The cleaning cartridge.
protocol:
  description: The type of the protocol: `HTTP` or `HTTPS`
  required: false
  type: string
  default: http
verify_ssl:
  description: Verify the SSL chain or not.
  required: false
  type: boolean
  default: false


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
