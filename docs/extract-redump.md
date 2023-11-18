# Converting redump image to XISO

From  [xemu documentation](https://xemu.app/docs/disc-images/):

> "Redump" ISOs are a full dump of the game disc. Xbox game discs contain two partitions, the first is a video partition which you can access from a computer or DVD player. This partition usually contains a short video instructing you to insert the disc into an Xbox. The second partition contains the actual game data. A "redump" ISO contains both of these partitions.

On Linux machine, we can use the following tools to convert redump image to XISO:

1. `dd`

   Use `dd` to remove the video partition. \
   This method will produce slightly smaller XISO file compared to its redump input, approx ~7 GB.

   ```sh
   dd if=game-redump.iso of=game.iso skip=387 bs=1M
   ```

2. `fallocate`

   Similar to `dd`, we can use `fallocate` to remove video partition.

   ```sh
   fallocate -c -o 0 -l 387MiB game.iso
   ```

3. [extract-xiso](https://github.com/XboxDev/extract-xiso)

   ```sh
   extract-xiso -r game-redump.iso
   ```

   Depends on the contents of the game, the output XISO image produced by this method is far smaller than its redump input. \
   The original game-redump.iso will be renamed to `game-redump.iso.old`.

4. `extract-xiso` + [xbfuse](https://github.com/multimediamike/xbfuse) combo.

   - Mount redump archive:

     ```sh
     xbfuse game-redump.iso $HOME/xgame
     ```

   - Create xiso from the mountpoint:

     ```sh
     extract-xiso -c $HOME/xgame game.iso
     ```

5. [xdvdfs](https://github.com/antangelo/xdvdfs)

  ```sh
  xdvdfs pack game-redump.iso
  ```