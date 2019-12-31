# myled
# 2019年：ロボットシステム学課題１
## 目的
ubuntuイメージのRaspberry Pi 3 Model B で２つのLEDの操作を行う
## プログラムの内容
0. 両方のLEDの消灯
1. 片方のLEDの点灯
2. もう片方のLEDの点灯
3. 両方のLEDの点灯
4. 片方が点灯し、もう一方が消灯する点滅を100回行う
5. 三三七拍子の点滅
6. 交互に点滅、最初は遅くだんだん早くなり、最後に消灯
7. 片方が１秒だけ点灯、その後もう片方も１秒だけ点灯
   これまでの遅延はdelay関数を使っていたが、これはsleep関数を使用
## 手順
1. LEDの接続先のピンを22と24に繋げる
2. my_deviceディレクトリに入り、makeを実行する
3. sudo insmod myled.koを実行し、インストールする
4. ls /devでmyled0があれば手順６にとぶ
5. tail /var/log/messagesでmajor番号を確認(私はmajor:391だった)
6. sudo mknod　/dev/myled0 c 391 cと実行する
   391の部分は先に確認したmajor番号に変える
7. sudo chmod 666 /dev/myled0を実行する
8. echo 0 > /dev/myled0でプログラムを実行する
   0の部分を上の「プログラムの内容」の数字にすることで、その部分のプログラムを実行できる
   例）echo 3 > /dev/myled0　…両方のLEDが点灯
9. 終える際にはsudo rmmod myledを実行し、アンインストールする
