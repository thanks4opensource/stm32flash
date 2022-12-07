stm32flash
==========

December 7, 2022 update:

- Code describe below (moved to branch v0.5_merge_request_15) is
  deprecated.
- Current v0.7 code at 
  <https://sourceforge.net/p/stm32flash/code/ci/master/tree/> supports
  "-b 0" flag with same functionality as branch's "-N".
- This GitHub repo's master branch updated to current v0.7 (commit
  [553016] as of this date/time), but does not have full git commit
  history and may become out-of-date.
- Please instead use most recent v0.7 (or later) from SourceForge
  repo, or equivalent distro binaries.

Fork of <https://sourceforge.net/p/stm32flash/code/ci/master/tree/>

* minor enhancement to upstream code ...
* to add support for opening `/dev/pts/<N>` pty (pseudo-tty) device special files ...
* created by [buck50.py](https://github.com/thanks4opensource/buck50/blob/master/build/buck50.py) ...
* connected to a "Blue Pill" STM32F103 USB device running [buck50](https://github.com/thanks4opensource/buck50) firmware ...
* connected via UART TX/RX to device being flashed ...
* because pty device files do not support changing baud rate, parity, bit size, stop bits, etc. ...
* as commanded by `stm32flash` via `tcsetattr()` library calls ...
* thus `stm32flash` exits with error.

Fork checks for "/dev/pts/" in `stm32flash [tty_device]` commandline argument and bypasses the `tcsetattr()` call. Also adds explicit `-N` commandline to force bypass regardless of `[tty_device]` name.

When used with buck50 firmware, baud rate, etc. must be set via the `buck50.py` user interface prior to invoking `stm32flash`.
