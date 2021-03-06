附录1 下传数据文件
===================

科学数据
----------

  科学数据包依次由包头、事件1（通道号、us Count时间戳、ADC值、UTC、PPS Count）、事 件2-44（通道号、us Count时间戳、ADC值）、有效计数、丢失计数、包尾、校验组成。

+---------+----------+----------+-----------+-----------+
|  字节号 | 包内编号 |   内容   |     值    |    备注   |
+=========+==========+==========+===========+===========+
|    1    |          |          |    0xAA   |           |
+---------+          |          +-----------+           |
|    2    |     /    |   包头   |    0xBB   |   固定值  |
+---------+          |          +-----------+           |
|    3    |          |          |    0xCC   |           |
+---------+----------+----------+-----------+-----------+
|    4    |          |          |  Channel  |           |
+---------+          |          +-----------+           |
|   5-12  |          |          |  us Count |           |
+---------+          |          +-----------+           |
|  13-14  |     1    |   事件1  |    ADC    |           |
+---------+          |          +-----------+           |
|  15-18  |          |          |    UTC    |           |
+---------+          |          +-----------+           |
|  19-26  |          |          | PPS Count |           |
+---------+----------+----------+-----------+-----------+
|    27   |          |          |  Channel  |           |
+---------+          |          +-----------+           |
|  28-35  |     2    |   事件2  |  us Count |           |
+---------+          |          +-----------+           |
|  36-37  |          |          |    ADC    |           |
+---------+----------+----------+-----------+-----------+
|    38   |          |          |  Channel  |           |
+---------+          |          +-----------+           |
|  39-46  |     3    |   事件3  |  us Count |           |
+---------+          |          +-----------+           |
|  47-48  |          |          |    ADC    |           |
+---------+----------+----------+-----------+-----------+
|   (略)  |          |          |           |           |
+---------+----------+----------+-----------+-----------+
|   478   |          |          |  Channel  |           |
+---------+          |          +-----------+           |
| 479-486 |    43    |  事件43  |  us Count |           |
+---------+          |          +-----------+           |
| 487-488 |          |          |    ADC    |           |
+---------+----------+----------+-----------+-----------+
|   489   |          |          |  Channel  |           |
+---------+          |          +-----------+           |
| 490-497 |    44    |  事件44  |  us Count |           |
+---------+          |          +-----------+           |
| 498-499 |          |          |    ADC    |           |
+---------+----------+----------+-----------+-----------+
| 500-503 |     /    | 有效计数 |     /     |           |
+---------+----------+----------+-----------+-----------+
| 504-507 |     /    | 丢失计数 |     /     |           |
+---------+----------+----------+-----------+-----------+
|   508   |          |          |    0xDD   |           |
+---------+          |          +-----------+           |
|   509   |     /    |   包尾   |    0xEE   |   固定值  |
+---------+          |          +-----------+           |
|   510   |          |          |    0xFF   |           |
+---------+----------+----------+-----------+-----------+
| 511-512 |     /    |   校验   |     /     | CRC16校验 |
+---------+----------+----------+-----------+-----------+

内务数据
----------

  内务数据包依次由包头、子包1-7（UTC、PPS Count、us Count、SiPM温度、ADC温度、SiPM偏压、SiPM电流、MCU温度、UTC对应的PPS Count、PPS Count对应的us Count）、包尾、校验、保留字段组成。

+---------+----------+-------+-------------------------+-----------+
|  字节号 | 包内编号 |  内容 |            值           |    备注   |
+=========+==========+=======+=========================+===========+
|    1    |          |       |           0x12          |           |
+---------+          |       +-------------------------+           |
|    2    |     /    |  包头 |           0x34          |   固定值  |
+---------+          |       +-------------------------+           |
|    3    |          |       |           0x56          |           |
+---------+----------+-------+-------------------------+-----------+
|   4-7   |          |       |           UTC           |           |
+---------+          |       +-------------------------+           |
|   8-15  |          |       |        PPS Count        |           |
+---------+          |       +-------------------------+           |
|  16-23  |          |       |         us Count        |           |
+---------+          |       +-------------------------+           |
|  24-25  |          |       |       CH0 SiPM温度      |           |
+---------+          |       +-------------------------+           |
|  26-27  |          |       |       CH1 SiPM温度      |           |
+---------+          |       +-------------------------+           |
|  28-29  |          |       |       CH2 SiPM温度      |           |
+---------+          |       +-------------------------+           |
|  30-31  |          |       |       CH3 SiPM温度      |           |
+---------+          |       +-------------------------+           |
|  32-33  |          |       |       CH0 ADC温度       |           |
+---------+          |       +-------------------------+           |
|  34-35  |          |       |       CH1 ADC温度       |           |
+---------+          |       +-------------------------+           |
|  36-37  |          |       |       CH2 ADC温度       |           |
+---------+          |       +-------------------------+           |
|  38-39  |          |       |       CH3 ADC温度       |           |
+---------+     1    | 子包1 +-------------------------+           |
|  40-41  |          |       |       CH0 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
|  42-43  |          |       |       CH1 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
|  44-45  |          |       |       CH2 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
|  46-47  |          |       |       CH3 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
|  48-49  |          |       |       CH0 SiPM电流      |           |
+---------+          |       +-------------------------+           |
|  50-51  |          |       |       CH1 SiPM电流      |           |
+---------+          |       +-------------------------+           |
|  52-53  |          |       |       CH2 SiPM电流      |           |
+---------+          |       +-------------------------+           |
|  54-55  |          |       |       CH3 SiPM电流      |           |
+---------+          |       +-------------------------+           |
|  56-57  |          |       |         MCU温度         |           |
+---------+          |       +-------------------------+           |
|  58-65  |          |       |    UTC对应的PPS Count   |           |
+---------+          |       +-------------------------+           |
|  66-73  |          |       | PPS Count对应的us Count |           |
+---------+----------+-------+-------------------------+-----------+
|   (略)  |          |       |                         |           |
+---------+----------+-------+-------------------------+-----------+
| 424-427 |          |       |           UTC           |           |
+---------+          |       +-------------------------+           |
| 428-435 |          |       |        PPS Count        |           |
+---------+          |       +-------------------------+           |
| 436-443 |          |       |         us Count        |           |
+---------+          |       +-------------------------+           |
| 444-445 |          |       |       CH0 SiPM温度      |           |
+---------+          |       +-------------------------+           |
| 446-447 |          |       |       CH1 SiPM温度      |           |
+---------+          |       +-------------------------+           |
| 448-449 |          |       |       CH2 SiPM温度      |           |
+---------+          |       +-------------------------+           |
| 450-451 |          |       |       CH3 SiPM温度      |           |
+---------+          |       +-------------------------+           |
| 452-453 |          |       |       CH0 ADC温度       |           |
+---------+          |       +-------------------------+           |
| 454-455 |          |       |       CH1 ADC温度       |           |
+---------+          |       +-------------------------+           |
| 456-457 |          |       |       CH2 ADC温度       |           |
+---------+          |       +-------------------------+           |
| 458-459 |          |       |       CH3 ADC温度       |           |
+---------+     7    | 子包7 +-------------------------+           |
| 460-461 |          |       |       CH0 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
| 462-463 |          |       |       CH1 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
| 464-465 |          |       |       CH2 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
| 466-467 |          |       |       CH3 SiPM偏压      |           |
+---------+          |       +-------------------------+           |
| 468-469 |          |       |       CH0 SiPM电流      |           |
+---------+          |       +-------------------------+           |
| 470-471 |          |       |       CH1 SiPM电流      |           |
+---------+          |       +-------------------------+           |
| 472-473 |          |       |       CH2 SiPM电流      |           |
+---------+          |       +-------------------------+           |
| 474-475 |          |       |       CH3 SiPM电流      |           |
+---------+          |       +-------------------------+           |
| 476-477 |          |       |         MCU温度         |           |
+---------+          |       +-------------------------+           |
| 478-485 |          |       |    UTC对应的PPS Count   |           |
+---------+          |       +-------------------------+           |
| 486-493 |          |       | PPS Count对应的us Count |           |
+---------+----------+-------+-------------------------+-----------+
|   494   |          |       |           0x78          |           |
+---------+          |       +-------------------------+           |
|   495   |     /    |  包尾 |           0x9A          |   固定值  |
+---------+          |       +-------------------------+           |
|   496   |          |       |           0xBC          |           |
+---------+----------+-------+-------------------------+-----------+
| 497-498 |     /    |  校验 |            /            | CRC16校验 |
+---------+----------+-------+-------------------------+-----------+
| 499-512 |     /    |  保留 |            /            |           |
+---------+----------+-------+-------------------------+-----------+