# genius-scrape project readme file
## Requirements
- Python 3.x
- pip packages: install using `pip3 install -r requirements.txt` (may require using `sudo -H` at the beginning)
	- recommend using with virtual environments
- **if using `clip` output**: x11, `xclip`
- Internet connection
	- If no internet connection is had when running the program, it will forever try to parse the Genius website with no result

## Summary
- Search for lyrics on [Genius](http://genius.com), provided an artist, either a song or album name, and that the page exists on Genius

## Instructions
- Clone the repository
- For argument help, run `python3 genius_scrape_cli.py -h`
- Search for an individual song:
	- Run `python3 genius_scrape_cli.py` then enter the artist name, press enter, then enter the item name
	- e.g. `python3 genius_scrape_cli.py` -> `Lefa` `Tournee des bars`
- Search for an album:
	- Run `python3 genius_scrape_cli.py -i ALBUM` then follow the prompts
	- e.g. `python3 genius_scrape_cli.py` -> `Lefa` `Monsieur Fall`
- Notes
	- The names are case insensitive, but may only contain alphanumerics, spaces, and dashes
- This will try to open the Genius page for that artist/song combination and print the lyrics to standard output
	- The song page must exist for it to work. Otherwise, it will throw an exception

- The output method can be changed with command line flag `-o`. This can take either of four values: `STD`, `FILE`, `CLIP`, or `NONE`
	- STD : print lyrics to standard output
	- FILE : write lyrics to a file in the current directory (suffixed `.OUT`)
		- e.g. `python3 genius_scrape_cli.py -i ALBUM -o FILE` -> `Lefa` `Monsieur Fall`
		- this will search all the songs in the album "Monsieur Fall", and save the lyrics of each to separate plaintext files
	- CLIP : writes the lyrics into the clipboard (next paste action will paste lyrics)
		- when used in conjunction with `-i ALBUM`, it will pause between each song, promtping for any key to be pressed before continuing
		- **WARNING**: this will overwrite the existing clipboard entry
	- NONE : do not output lyrics (used for debug purposes)

