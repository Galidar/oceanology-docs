# Audio System

Oceanology supports two different modes of Audio: Underwater & Waves. The behavior of underwater and non-underwater detection can be checked via "Debug Enabled" perfectly.

## Underwater Audio
The underwater audio plays when the actual camera is below the waterline of the current overlapping water body.

## Wave Audio
The wave audio plays only when you are NOT underwater and also uses Attenuation.

## Actors
* The **BP_OceanologyLake** itself contains all the necessary audio (underwater & waves), you only need to configure the attenuation settings yourself. Changing the size of the lake also increases the falloff distance.
* The **BP_OceanologyInfiniteOcean** itself contains ONLY the underwater Ocean audio. Wave sounds of the shore should be manually placed.
* The **BP_OceanWaveAudio** is the actor designed for the ocean shore wave audio. You may place multiple actors of this fine-tuning to your own taste the audio settings alongside the Ocean's shore. This behavior guarantees that wave audio only plays near the shores, and not in the middle of the island.