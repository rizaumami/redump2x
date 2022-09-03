# redump2x
`redump2x` is a script to extract the original Xbox's redump archives.

I was using redump archives to test xiso boot feature from NKPatcher and Cerbios. \
This script was created mainly to automate the processes needed, such as:
- convert redump archive to regular xiso format;
- sanitize the filename (to conform FATX limitations);
- split the xiso if its size is bigger than (approx) 4 GB (also, FATX limitation).

## LICENSE
- `redump2x` script is licensed as stated inside the script and [LICENSE](LICENSE) file. \
- The files inside bin folder has their own licenses and are excluded from the scope of this repo's license.
