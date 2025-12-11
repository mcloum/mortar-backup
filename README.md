THI IS A BACKUP OF THE LAST VERSION OF MORTAR. NO SUPPORT IS GIVEN, NOR ARE ANY UPDATES BEING DEVELOPED.

---

## How do I setup Mortar?

### NextUI Setup

1. Own a TrimUI Brick or Smart Pro and have a SD Card with NextUI.
2. Connect your device to a Wi-Fi network.
3. Extract the release zip and place the `Mortar.pak` directory into `SD_ROOT/Tools/tg5040`.
4. Follow the "How To Configure Mortar" section below to complete the setup.
5. Launch `Mortar` from the `Tools` menu and enjoy!

---

### muOS Setup

Mortar has only been tested on muOS 2508.1 Canada Goose on an Anbernic RG35XXSP.

Please help by verifying if it works on other devices!

1. Own a supported device running muOS.
2. Download the the zip form this repo.
3. Transfer the `Mortar.muxapp` file to SD1 `(mmc)/ARCHIVE` on your device.
4. Go to Applications and launch Archive Manager.
5. Select [SD1-APP] Mortar from the list and let it extract to your applications directory.
6. Exit Archive Manager.
7. Follow the "How To Configure Mortar" section below to complete the setup.
8. Find an [input mapping config](/.github/resources/input_mappings) for your device.
    - If one does not exist, please try one for a different device.
9. Save the input mapping JSON file as `input_mapping.json` and transfer it to SD1 `(mmc)/Applications/Mortar` on your
   device.
10. Select `Apps` on the Main Menu, launch Mortar and enjoy!

**Note:** Mortar does not support downloading art on muOS.

---

### How To Configure Mortar

1. Connect your handheld to a Wi-Fi network.
2. Launch `Mortar` from the `Tools` menu.
3. On first launch, Mortar will display a QR Code that leads to a configuration editor.
    - For the editor to function, the editing device (phone, laptop, etc.) must be connected to the same Wi-Fi network as your handheld.
4. Follow the Configuration Reference section below.

---

## Configuration Reference

**Note:** Mortar **_will not_** function without a valid `config.json` file.

If Mortar does not find a config.json file or if the provided config file has syntax errors you will see an error screen
with a QR Code that leads to this page. If you arrived at this page for this reason, please continue reading.

Please edit the template 'config.yaml'


These are templates. They **_will not function_** without modification.

---

```json
{
  "hosts": [
    {
      "display_name": "Display Name",
      "root_uri": "https://domain.tld",
      "port": 445,
      "platforms": [
        {
          "platform_name": "Game Boy",
          "system_tag": "GB",
          "local_directory": "/mnt/SDCARD/Roms/Game Boy (GB)/",
          "host_subdirectory": "/files/No-Intro/Nintendo%20-%20Game%20Boy/",
          "skip_inclusive_filters": false,
          "skip_exclusive_filters": false,
          "is_arcade": false
        }
      ],
      "filters": {
        "inclusive_filters": [
          "USA",
          "En,"
        ],
        "exclusive_filters": [
          "(Proto",
          "(Demo)",
          "(Beta)",
          "(Aftermarket",
          "4-in-1",
          "4 in 1",
          "(Europe)",
          "(Japan)"
        ]
      }
    }
  ],
  "download_art": true,
  "art_download_type": "BOX_ART",
  "log_level": "ERROR"
}
```

### Configuration Options Explained

#### Host Configuration

- **root_uri**: This can be the start of a URL with protocol (e.g. https://), a host name or an IP Address
- **port**: Optional otherwise unless using non-standard ports
- **hosts**: Define more hosts if desired

#### Platform Configuration

- **platform_name**: Name it whatever you want
- **system_tag**: Must match the tag in the `SDCARD_ROOT/Roms` directories
- **local_directory**: Explicitly set the path. This will be overwritten if `system_tag` is set
- **host_subdirectory**: The subdirectory on the host
- **skip_inclusive_filters**: If true, everything in the host directory will be included
- **skip_exclusive_filters**: If true, nothing in the host directory will be excluded
- **is_arcade**: If true, Mortar will use an internal mapping file for arcade names
- **platforms**: One or more mappings of the host directory to the local filesystem. Define more sections if desired

#### Filter Configuration

- **inclusive_filters**: These are applied first. If the ROM filename contains any of these, it will be
  included
- **exclusive_filters**: These are applied second. If the ROM filename contains any of these, it will be
  excluded

#### Art Configuration

- **download_art**: If true, Mortar will attempt to find box art. If found, it will display it and let you indicate if
  you want it
- **art_download_type**: Optional, defaults to `BOX_ART`.
    - Valid Choices: `BOX_ART` | `TITLE_SCREEN` | `LOGOS` | `SCREENSHOTS`

#### Logging

- **log_level**: Optional, defaults to error. Handy when shit breaks

Sample configuration files can be in the repo. 

