# redump2x
`redump2x` is a script to "extract" the original Xbox's redump archives.

I was using redump archives to test xiso boot feature from NKPatcher and Cerbios. \
This script was created mainly to automate the processes needed, such as:
- convert redump iso or archive to regular xiso format;
- copy `default.xbe`'s certificate to `attach.xbe` ;
- sanitize the filename (to conform FATX limitations);
- split the xiso if its size is bigger than (approx) 4 GB (also, FATX limitation);
- add game cover to be displayed UnleashX dashboard.

## Notes
- Wrong password on protected archive will stop the script. \
  Only use `-p` option if the archives using the same password.
- Game cover (artwork) is taken from Rocky5' Xbox Artwork Installer. \
  Get it from [here](https://drive.google.com/file/d/1Y3_21N8yDqYJ1CznaP6ceMM87JHpTHwd/view?usp=sharing) and install it using following command:

  ```bash
  redump2x -a -i 'Xbox Artwork Installer.zip'
  ```

  Now, Icon.jpg will automatically created during xiso preparation.

## LICENSE
- `redump2x` script is licensed as stated inside the script and [LICENSE](LICENSE) file.
- The files inside bin folder has their own licenses and are excluded from the scope of this repo's license. \
I have a plan to remove the binaries and replaced it with its submodules in future release.
