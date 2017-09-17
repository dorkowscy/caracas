# Caracas

The [original Caracas](https://github.com/ambientsound/caracas) was an open source DIY car stereo system, running on a Raspberry Pi with custom hardware modifications. [See pictures](http://imgur.com/a/6FCoq) of Caracas in action!

This fork's `minimal` branch strips Caracas of car-specific components to change it into a more general Raspberry Pi-compatible music player. Caracas Minimal works well with a touch screen.

## Components

Caracas is a Qt application. It uses a customizable CSS file for styling. MPD is used to fetch music.

As a bonus, the creator also provided Ansible role files and systemd service files.

## Setting up

1. Install and configure MPD.

2. Install Qt and supporting packages:

  ```
  $ sudo apt install build-essential libgl1-mesa-dev qt5-qmake qt5-default qt5-dev
  ```

  ```
  $ sudo apt install ibmpdclient-dev libtag1-dev libqt5svg5-dev libid3-3.8.3-dev libid3tag0-dev libtag1-dev
  ```

3. After installing all of the above using `apt`, make sure you are in the repository's `gui` directory, and run the following commands:

  ```
  $ qmake .
  $ sudo make install
  ```
4. Without changing directories, launch Caracas from the command line using:

  ```
  $ ./caracas-gui -stylesheet style.css
  ```

### Notes

If you want to launch Caracas on a touchscreen from an SSH session, it's enough to type:

```
DISPLAY=:0.0 ./caracas-gui -stylesheet style.css
```

If you don't prepend the line with `DISPLAY`, the command will try to open the player in your current SSH session.
