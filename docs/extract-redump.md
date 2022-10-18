# Converting redump image to XISO

From  [xemu documentation](https://xemu.app/docs/disc-images/):

> "Redump" ISOs are a full dump of the game disc. Xbox game discs contain two partitions, the first is a video partition which you can access from a computer or DVD player. This partition usually contains a short video instructing you to insert the disc into an Xbox. The second partition contains the actual game data. A "redump" ISO contains both of these partitions.

On Linux machine, we can use the following tools to convert redump image to XISO:

1. `dd`

   Use `dd` to remove the video partition.  
   This method will produce slightly smaller XISO file compared to its redump input, approx ~7 GB. 
   
   ```sh
   dd if=game-redump.iso of=game.iso skip=387 bs=1M
   ```

2. [extract-xiso](https://github.com/XboxDev/extract-xiso)

   ```sh
   extract-xiso -r game-redump.iso
   ```
   
   Depends on the contents of the game, the output XISO image produced by this method is far more smaller than its redump input.  
   The original game-redump.iso will be renamed to `game-redump.iso.old`.
