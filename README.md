# Rines PulseMedia

A lightweight audio and video player with playlists, built from a single Windows batch file. No installer, no dependencies. It is the media player for [RinesOS](#rinesos-integration), and it also works on its own.

> **Beta.** PulseMedia is a small hobby project. Expect rough edges, and please report them in the Issues tab.

## Features

- **Audio and video** in one window. Audio files show a Now Playing screen with the track title, folder and an animated visualizer (decorative; it does not react to the actual sound).
- **Playlists and queue**
  - Add files, or whole folders with or without subfolders
  - Reorder with Up / Down, remove tracks, clear the queue, sort A-Z
  - Save and load standard `.m3u` playlists (default folder: `%APPDATA%\RinesPulseMedia\Playlists`)
  - Drag and drop files or folders into the window
- **Playback controls**: play/pause, stop, previous/next, seek bar, +/-10 second skip, volume, mute
- **Shuffle** and **repeat** (off / all / one)
- **Remembers** your last queue, volume, shuffle and repeat settings
- **Full screen** for video
- If Windows cannot play a file, PulseMedia offers to open it in the Windows default player instead

## Requirements

- Windows 10 or 11
- Windows PowerShell 5.1 (built in)

## Getting started

1. Download `PulseMedia.bat` from the [Releases](../../releases) page.
2. Double-click it, then press **+ Files** or drag media into the window.

You can also start it with a file, a folder or a playlist:

```bat
PulseMedia.bat "C:\Music\song.mp3"
PulseMedia.bat "C:\Music"
PulseMedia.bat "C:\Playlists\road-trip.m3u"
```

Opening a single file queues the other media in the same folder and starts at the file you chose.

## Keyboard shortcuts

| Key | Action |
|---|---|
| Space | Play / pause |
| Left / Right | Seek 5 seconds |
| Up / Down | Volume |
| N / P | Next / previous track |
| S | Stop |
| M | Mute |
| F | Full screen |
| Q | Show / hide the queue |
| O or Ctrl+O | Add files |
| Delete | Remove selected track |
| Ctrl+S / Ctrl+L | Save / load playlist |
| Double-click video | Full screen |

## Supported formats

PulseMedia uses the media support built into Windows, so it plays what Windows can play:

- **Audio:** mp3, wav, wma, m4a, aac, flac, ogg, opus, aif, aiff, mid, midi
- **Video:** mp4, m4v, mkv, avi, mov, wmv, webm, mpg, mpeg

Some formats (mkv, flac, ogg, opus, webm) depend on the codecs installed on your PC and may not play everywhere.

## RinesOS integration

[RinesOS](https://github.com/Radinsk-Internet-Electronic-Services/RinesOS) is a pretend operating system written in batch files. Put `PulseMedia.bat` in the same folder as `RinesOS.bat`, then in RinesOS use **Settings > Media player > Rines PulseMedia**, or the terminal command `mediaplayer pulse`. The `pulse [file]` command opens it directly.

## Known limitations

- Windows only.
- The visualizer is decorative and does not analyze the audio.
- A console window may flash briefly when it starts.
- No equalizer, no tag or album-art reading, and no streaming.

## How it works

`PulseMedia.bat` is a batch launcher with a PowerShell + WPF program embedded in it. The batch part starts PowerShell, which reads the rest of the file and runs it, so the whole player is one file you can open and read.
