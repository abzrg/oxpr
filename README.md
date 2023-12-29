# Oxford Pronunciation Downloader

This simple utility downloads the files from oxford online dictionary.

## Usage

```sh
# To see all the features
oxpr --help

oxpr <word>  # us (default), cwd=./

oxpr <word> -l gb  # gb, cwd=./

oxpr <word> -o my_fav_word_output_name.mp3 # specify the output name, otherwise the remote name

oxpr <word> -d /path/to/dir/  # us, cwd=/path/to/dir
```

To download and play a list of words:

```sh
<words.txt | xargs -I{} oxpr -d prons/ -l gb {}

ls prons/*_gb_* | xargs -I {} bash -c 'play {} && sleep 0.5 && play {} && sleep 0.5'
```

## Install

Download the script (`oxpr`) and put it file somewhere in path.

```sh
git clone https://github.com/abzrg/oxpr /tmp/oxpr
cd $_

cp oxpr ~/.local/bin/   # if ~/.local/bin is in path
# or
sudo cp oxpr /usr/local/bin/   # otherwise
```


## Todo

- [ ] cache

  ```sh
  [ -d ~/.cache/oxpr/{us,gb} ] || mkdir ...{us,uk}
  # if file_present(file); -> echo file already downloaded and { 1. only play it 2. copy it from cache }
  ```

- [ ] `-p|only-play`

  ```sh
  play() {
      mpv --no-config --really-quiet --keep-open=no --force-window=no --no-resume-playback "$1"
  }
  ```

- [ ] read from files using `-f <filename>`/ `-f - (stdin)`

- [ ] config: either from a environment variable or from a file (if both, priority with environment?)
