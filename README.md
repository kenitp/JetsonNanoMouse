[English](README.en.md) | [日本語](README.md)

# JetsonNanoMouse

Jetson Nano Mouseのデバイスドライバです。

![](https://rt-net.github.io/images/jetson-nano-mouse/Jetson-Nano-Mouse-500x500.png)

## インストール方法

Jetson-IOを実行して`spi1`を有効にします。詳細は[wiki](https://github.com/rt-net/JetsonNanoMouse/wiki/Jetson-IO%E3%82%92%E7%94%A8%E3%81%84%E3%81%A6SPI1%E3%82%92%E6%9C%89%E5%8A%B9%E5%8C%96)を参照してください。

このリポジトリを`git clone`でダウンロードします。

```sh
git clone https://github.com/rt-net/JetsonNanoMouse.git
cd JetsonNanoMouse
```

必要に応じて[`drivers/rtmouse/rtmouse.c`](drivers/rtmouse/rtmouse.c)のオプションを編集します。

ダウンロードしたディレクトリ内で以下のコマンドを実行します。

```sh
make build
sudo make install
```

`/dev/rtlightsensor0`や`/dev/rtled0`などのデバイスファイルが作成されていることを確認します。

## オプション

[`drivers/rtmouse/rtmouse.c`](drivers/rtmouse/rtmouse.c)のオプションは以下の通りです。

| オプション | 有効な場合 | 無効な場合 |
| --- | --- | --- |
| USE_EXTERNAL_CLOCK | モータドライバへの信号出力ICで外部クロックを使用 ※1 | モータドライバへの信号出力ICで内部クロックを使用 |

※1 左右のモータの回転数差の低減が期待できます（[#16](https://github.com/rt-net/JetsonNanoMouse/issues/16)）

## サンプルプログラム

デバイスファイルの使用例は[./samples](./samples)を参考にしてください。

## License

(C) 2019-2020 RT Corporation \<shop@rt-net.jp\>

このリポジトリはGPLv2ライセンス（[GPL-2.0-only](https://spdx.org/licenses/GPL-2.0-only.html)）で公開されています。詳細は[LICENSE](./LICENSE)を確認してください。

`samples`ディレクトリは
[Apache-2.0](https://spdx.org/licenses/Apache-2.0.html)
ライセンスで公開されています。
詳細は[./samples/LICENSE](./samples/LICENSE)を確認してください。

### Acknowledgements

This project includes [rt-net/RaspberryPiMouse](https://github.com/rt-net/RaspberryPiMouse), licensed under the GPLv2 license.
```
 /*
 *
 * rtmouse.c
 * Raspberry Pi Mouse device driver
 *
 * Version: 3.0.0
 *
 * Copyright (C) 2015-2020 RT Corporation <shop@rt-net.jp>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; version 2.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
 * GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 * MA 02110-1301, USA.
 */
```

This project includes the code to control PCA9685([adafruit/Adafruit_Python_PCA9685](https://github.com/adafruit/Adafruit_Python_PCA9685)) licensed under the MIT License.
```
# Copyright (c) 2016 Adafruit Industries
# Author: Tony DiCola
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.
```

This project includes the code to control PCA9685([adafruit/Adafruit-PWM-Servo-Driver-Library](https://github.com/adafruit/Adafruit-PWM-Servo-Driver-Library)) licensed under the 3-clause BSD License.

```
Software License Agreement (BSD License)

Copyright (c) 2012, Adafruit Industries
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
1. Redistributions of source code must retain the above copyright
notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright
notice, this list of conditions and the following disclaimer in the
documentation and/or other materials provided with the distribution.
3. Neither the name of the copyright holders nor the
names of its contributors may be used to endorse or promote products
derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS ''AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```