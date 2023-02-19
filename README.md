# redump2x
`redump2x` is a script to "extract" the original Xbox's redump archives.

I was using redump archives to test xiso boot feature from NKPatcher and Cerbios. \
This script was created mainly to automate the processes needed, such as:
- convert redump iso or archive to regular xiso format;
- copy `default.xbe`'s certificate to `attach.xbe` ;
- sanitize the filename (to conform FATX limitations);
- split the xiso if its size is bigger than (approx) 4 GB (also, FATX limitation);
- add game cover to be displayed on UnleashX dashboard.

## How to

### Install

- Install dependendies

  ```bash
  sudo apt install p7zip-full dd grep xxd
  ```

- Clone this repo

  ```bash
  git clone https://github.com/rizaumami/redump2x
  ```

### Use

- Go to redump2x folder an then execute `redump2x` script.

  ```bash
  cd redump2x
  ./redump2x -h
  ```

  ```
  redump2x is a script to convert ogxbox redump archive into reguler xiso.

  Usage: redump2x OPTION

  OPTION:
    -a    Install artworks (game cover) from Rocky5's Xbox Artwork Installer.
    -b    Create xiso folder to be booted from disk.
          Cerbios and driveimageutils can launch a game stored as an xiso on
          ogxbox's disk.
          Boot xiso from disk used as a solution to FATX limitations such as
          filename length, file/folder structure, etc.
    -D    Delete the input redump archive after processing.
    -d    Use dd instead of extract-xiso.
          This will only remove the redump's video partition, so the output
          will be quite big. Approx ~7 GB.
          Try this if extract-xiso produced unplayable image.
    -h    Print this help text and exit.
    -i    Input file or directory (default to current working directory).
          If input is a directory, the redump archives found inside will be
          batch processed.
    -o    Output directory (default to current working directory).
    -m    Enable .xbe media patching.
    -p    Password to extract encrypted archive.
          Script will exit on wrong password.
          If the archives protected with different passwords, it's better to not
          use this option and input password manually when asked.
    -s    Split output ISO into two equal size ISOs.
          Output will be splitted if its size is bigger than 4294965248 bytes.
    -u    Update attach.xbe with default.xbe or game.xbe's certificate.
    -v    Print version information and exit.

  Example:
    - Install artwork.
      redump2x -a -i 'Xbox Artwork Installer.zip'

    - Convert CoolGame.iso and save it into /tmp/xiso directory.
      redump2x -i /home/iza/CoolGame.iso -o /tmp/xiso

    - Convert game isos in Redump directory and save it into /tmp/xiso.
      redump2x -i /home/iza/Redump -o /tmp/xiso

    - Convert CoolGame.iso to bootable from disk format.
      redump2x -bi /home/iza/CoolGame.iso

    - Convert CoolGame.iso and split the output into two equal size ISOs.
      redump2x -si /home/iza/CoolGame.iso

    - Provide password for password protected archive.
      redump2x -p secretpassword -bi /home/iza/CoolGame.7z

  ```

## Notes
- Wrong password on protected archive will stop the script. \
  Only use `-p` option if the archives using the same password.
- Game cover (artwork) is taken from Rocky5' Xbox Artwork Installer. \
  Get it from [here](https://drive.google.com/file/d/1Y3_21N8yDqYJ1CznaP6ceMM87JHpTHwd/view?usp=sharing) and install it using following command:

  ```bash
  redump2x -a -i 'Xbox Artwork Installer.zip'
  ```

  Now, Icon.jpg will automatically created during xiso preparation.
- Thumbnail only work (and tested) on UnleashX. XBMC only displaying the title name, and probably also another dashboards.

## LICENSE
- `redump2x` script is licensed as stated inside the script and [LICENSE](LICENSE) file.
- The files inside bin folder has their own licenses and are excluded from the scope of this repo's license. \
I have a plan to remove the binaries and replaced it with its submodules in future release.
