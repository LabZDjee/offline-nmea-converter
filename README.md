## Welcome to Offline NMEA Converter
ドライブレコーダーが保存したNMEA形式のファイルをGPX、KML、CSVに変換します。HTML5の技術を活用し、サーバにデータを送信せずに動作します。

Convert the NMEA format file saved by the drive recorder to GPX, KML, CSV. Using HTML 5 technology, it works without sending information to any server.

## How to Use
使い方

### STEP1: Move to top page.
下記のURLにアクセスします。
https://labzdjee.github.io/offline-nmea-converter

### STEP2: Drag and drop *.NMEA* file.
.NMEAファイルをドラッグ ＆ ドロップします。

### STEP3: Select the type of file to download.
ダウンロードしたいファイルのを選択します。

<img src="https://tkama.github.io/offline-nmea-converter/img/h1.png" height="320px">

------

Tech notes: 

Reason for forking this interesting [https://github.com/tkama/offline-nmea-converter](https://github.com/tkama/offline-nmea-converter) is mainly because we have *.nmea* files (from an Olympus app) where GPRMC records don't come first and their respective timestamps suffer from a slight offset (less than one second). So GPRMC/GPGGA were not working with this type of files.

Here are the following changes:

- GPGGA records are processed after GPRMC records and GPGGA-GPRMC matches
  are done based on hour-minute-second time stamp to be as
  close as possible to find matches (and to be less than one second to avoid silly matches). This process is much slower than before hence performance penalty on long NMEA files (technically each GPGGA is processed against *all* GPRMC records).
  This is a way to be independent of the order GPRMC/GPGGA like before where GPGGA  could not come first.
- accepts *.nmea* filename extensions (not case sensitive).
- translates some more Japanese texts into English.
- corrects *NEMA* as *NMEA* in some places: *NEMA* renamed *NMEA* wherever found.

