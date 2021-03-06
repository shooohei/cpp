# xecho

## Description
指定したパターンのバイナリデータを出力します．
基本的には，入力データをコピーして膨らませます．データを膨らませる際に，1バイト単位でのインクリメント／デクリメントが可能です．

## Usage

    $ xecho [OPTION...] [HEX_STRING]

    -l NUM    入力データのサイズをNUM倍にする．
    -m MODE   NUM倍時にMODEに応じた演算を加える（MUST: -l）
              MODE: countup-NUM, countdown-NUM それぞれNUM分インクリメント，デクリメントを行う．
              NUMを省略した場合，1が入力されたとして扱われる．
    -f FILE   入力データにファイルを指定．
    -h        ヘルプを表示．

    [HEX_STRING]の指定が無い場合，標準入力からの入力を受け付ける．
    出力は，標準出力から取得する．

## Example

    xecho -l 16 01 > test1.dat
    [test1.dat]
    00000000  01 01 01 01 01 01 01 01  01 01 01 01 01 01 01 01
    00000010

    xecho -l 16 01 | xecho -l 2 -m countup-1 > test2.dat
    [test2.dat]
    00000000  01 01 01 01 01 01 01 01  01 01 01 01 01 01 01 01
    00000010  02 02 02 02 02 02 02 02  02 02 02 02 02 02 02 02

    xecho -l 16 01 | xecho -l 2 -m countup-1 | xecho -l 4 -m countup-8 > test3.dat
    [test3.dat]
    00000000  01 01 01 01 01 01 01 01  01 01 01 01 01 01 01 01
    00000010  02 02 02 02 02 02 02 02  02 02 02 02 02 02 02 02
    00000020  09 09 09 09 09 09 09 09  09 09 09 09 09 09 09 09
    00000030  0a 0a 0a 0a 0a 0a 0a 0a  0a 0a 0a 0a 0a 0a 0a 0a
    00000040  11 11 11 11 11 11 11 11  11 11 11 11 11 11 11 11
    00000050  12 12 12 12 12 12 12 12  12 12 12 12 12 12 12 12
    00000060  19 19 19 19 19 19 19 19  19 19 19 19 19 19 19 19
    00000070  1a 1a 1a 1a 1a 1a 1a 1a  1a 1a 1a 1a 1a 1a 1a 1a
