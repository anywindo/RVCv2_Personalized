# AICoverGen (modded)
An autonomous pipeline to create covers with any RVC v2 trained AI voice from YouTube videos or a local audio file. For developers who may want to add a singing functionality into their AI assistant/chatbot/vtuber, or for people who want to hear their favourite characters sing their favourite song.

Modded Personalized version is simplified to easy my workflow. It includes GUI and basic CLI or non-UI input for inference.

## Colab notebook

Original AICoverGen:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SociallyIneptWeeb/AICoverGen/blob/main/AICoverGen_colab.ipynb)

Modded AICoverGen:

[![Open In Colab](https://colab.research.google.com/github/anywindo/RVCv2_Personalized/blob/main/RVCv2_Personalized.ipynb)

## Usage with WebUI

To run the AICoverGen WebUI, run the following command.

```
python src/webui.py
```

| Flag                                       | Description |
|--------------------------------------------|-------------|
| `-h`, `--help`                             | Show this help message and exit. |
| `--share`                                  | Create a public URL. This is useful for running the web UI on Google Colab. |
| `--listen`                                 | Make the web UI reachable from your local network. |
| `--listen-host LISTEN_HOST`                | The hostname that the server will use. |
| `--listen-port LISTEN_PORT`                | The listening port that the server will use. |

Once the following output message `Running on local URL:  http://127.0.0.1:7860` appears, you can click on the link to open a tab with the WebUI.

### Running the pipeline

To run the AI cover generation pipeline using the command line, run the following command.

```
python src/main.py [-h] -i SONG_INPUT -dir RVC_DIRNAME -p PITCH_CHANGE [-k | --keep-files | --no-keep-files] [-ir INDEX_RATE] [-fr FILTER_RADIUS] [-rms RMS_MIX_RATE] [-palgo PITCH_DETECTION_ALGO] [-hop CREPE_HOP_LENGTH] [-pro PROTECT] [-mv MAIN_VOL] [-bv BACKUP_VOL] [-iv INST_VOL] [-pall PITCH_CHANGE_ALL] [-rsize REVERB_SIZE] [-rwet REVERB_WETNESS] [-rdry REVERB_DRYNESS] [-rdamp REVERB_DAMPING] [-oformat OUTPUT_FORMAT]
```

| Flag                                       | Description |
|--------------------------------------------|-------------|
| `-h`, `--help`                             | Show this help message and exit. |
| `-i SONG_INPUT`                            | Link to a song on YouTube or path to a local audio file. Should be enclosed in double quotes for Windows and single quotes for Unix-like systems. |
| `-dir MODEL_DIR_NAME`                      | Name of folder in [rvc_models](rvc_models) directory containing your `.pth` and `.index` files for a specific voice. |
| `-p PITCH_CHANGE`                          | Change pitch of AI vocals in octaves. Set to 0 for no change. Generally, use 1 for male to female conversions and -1 for vice-versa. |
| `-k`                                       | Optional. Can be added to keep all intermediate audio files generated. e.g. Isolated AI vocals/instrumentals. Leave out to save space. |
| `-ir INDEX_RATE`                           | Optional. Default 0.5. Control how much of the AI's accent to leave in the vocals. 0 <= INDEX_RATE <= 1. |
| `-fr FILTER_RADIUS`                        | Optional. Default 3. If >=3: apply median filtering median filtering to the harvested pitch results. 0 <= FILTER_RADIUS <= 7. |
| `-rms RMS_MIX_RATE`                        | Optional. Default 0.25. Control how much to use the original vocal's loudness (0) or a fixed loudness (1). 0 <= RMS_MIX_RATE <= 1. |
| `-palgo PITCH_DETECTION_ALGO`              | Optional. Default rmvpe. Best option is rmvpe (clarity in vocals), then mangio-crepe (smoother vocals). |
| `-hop CREPE_HOP_LENGTH`                    | Optional. Default 128. Controls how often it checks for pitch changes in milliseconds when using mangio-crepe algo specifically. Lower values leads to longer conversions and higher risk of voice cracks, but better pitch accuracy. |
| `-pro PROTECT`                             | Optional. Default 0.33. Control how much of the original vocals' breath and voiceless consonants to leave in the AI vocals. Set 0.5 to disable. 0 <= PROTECT <= 0.5. |
| `-mv MAIN_VOCALS_VOLUME_CHANGE`            | Optional. Default 0. Control volume of main AI vocals. Use -3 to decrease the volume by 3 decibels, or 3 to increase the volume by 3 decibels. |
| `-bv BACKUP_VOCALS_VOLUME_CHANGE`          | Optional. Default 0. Control volume of backup AI vocals. |
| `-iv INSTRUMENTAL_VOLUME_CHANGE`           | Optional. Default 0. Control volume of the background music/instrumentals. |
| `-pall PITCH_CHANGE_ALL`                   | Optional. Default 0. Change pitch/key of background music, backup vocals and AI vocals in semitones. Reduces sound quality slightly. |
| `-rsize REVERB_SIZE`                       | Optional. Default 0.15. The larger the room, the longer the reverb time. 0 <= REVERB_SIZE <= 1. |
| `-rwet REVERB_WETNESS`                     | Optional. Default 0.2. Level of AI vocals with reverb. 0 <= REVERB_WETNESS <= 1. |
| `-rdry REVERB_DRYNESS`                     | Optional. Default 0.8. Level of AI vocals without reverb. 0 <= REVERB_DRYNESS <= 1. |
| `-rdamp REVERB_DAMPING`                    | Optional. Default 0.7. Absorption of high frequencies in the reverb. 0 <= REVERB_DAMPING <= 1. |
| `-oformat OUTPUT_FORMAT`                   | Optional. Default mp3. wav for best quality and large file size, mp3 for decent quality and small file size. |


## Terms of Use

The use of the converted voice for the following purposes is prohibited.

* Criticizing or attacking individuals.

* Advocating for or opposing specific political positions, religions, or ideologies.

* Publicly displaying strongly stimulating expressions without proper zoning.

* Selling of voice models and generated voice clips.

* Impersonation of the original owner of the voice with malicious intentions to harm/hurt others.

* Fraudulent purposes that lead to identity theft or fraudulent phone calls.

## Disclaimer

I am not liable for any direct, indirect, consequential, incidental, or special damages arising out of or in any way connected with the use/misuse or inability to use this software.
