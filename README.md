# Yo-Kai Watch 2 Infinite Tunnel
This text aims to explain the mechanics behind the Infinite Tunnel in Yo-Kai Watch 2.

## General
The infinite tunnel in Yo-Kai Watch 2 is split into sections.
These sections are exactly 50m long and each section contains one emergency exit door at the end.
The number of the section the player is currently in is equal to the current escape door number.
The goal is always at the end of a section.
So that the distance at the end isn't always ending in 00 or 50, the first section is randomly up to 49m longer.

## Maximum and Minimum Tunnel Length
The maximum and minimum tunnel lengths determine how much the tunnel length can shrink or grow. These values are stored in the `yw2_a.fa` in `/data/res/enen_tunnel/enen_tunnel_event.cfg.bin`
under `ENEN_TUNNEL_LENGTH_PARAM_X` with `X` being the number of times the tunnel has been cleared. On three days the end distance is fixed and minimum and maximum lengths are the same. 

These are the values:

| Inf. Tunnel Clear Count | Min. Sections | Max. Sections | Fixed End Distance (m) |
| ----------------------- | ------------- | ------------- | ---------------------- |
| 0                       | -             | -             | 749                    |
| 1                       | 20            | 40            | -                      |
| 2                       | 20            | 60            | -                      |
| 3                       | -             | -             | 4949                   |
| 4                       | 20            | 120           | -                      |
| 5                       | 20            | 140           | -                      |
| 6                       | -             | -             | 7979                   |
| 7                       | 2             | 160           | -                      |
| 8                       | 2             | 180           | -                      |
| 9                       | 2             | 200           | -                      |
| 10                      | 2             | 220           | -                      |
| 11                      | 2             | 240           | -                      |
| 12                      | 2             | 260           | -                      |
| 13                      | 2             | 280           | -                      |
| 14                      | 2             | 300           | -                      |
| 15                      | 2             | 320           | -                      |
| 16                      | 2             | 340           | -                      |
| 17                      | 2             | 360           | -                      |
| 18                      | 2             | 380           | -                      |
| 19                      | 2             | 400           | -                      |
| >19                     | 2             | 20000         | -                      |


## Goal Location at the Beginning
The initial goal position is determined randomly and depends on the clear count of the infinite tunnel.
The lower bound is 21 sections and the upper bound is (20 * clearCount + 21) sections with a maximum of 401 sections.

> The goal position cannot exceed the maximum tunnel length or go lower than the minimum tunnel length.

## Manipulating the Tunnel Goal Location
The tunnel length cannot be lowered more than the minimum mentioned above and not more than the section the player is in plus one. The tunnel length cannot grow further than the maximum mentioned above.
If the player is already in the last or second to last section, the tunnel length can no longer be manipulated.
The end location of the goal can be manipulated the following ways:
* Talking to NPCs:
    * "The exit got a bit farther": +10 sections (+500m)
    * "The exit got a bit closer": -10 sections (-500m)
    * *Exception*: Saying to the Tunnel Guy, "Make it shorter": -20000 sections (-1000000m)
* Dangerous Switch:
    * "The exit got really close": -40 sections (-2000m)
    * "The exit got a bit closer": -20 sections (-1000m)
    * "The exit got a bit farther": +30 sections (+1500m)
    * "The exit got extremely far away": +60 sections (+3000m)
* Fighting a Yo-Kai that blocks the way or walks through the tunnel (NOT a battle after talking to an NPC): +1 section (+50m)
