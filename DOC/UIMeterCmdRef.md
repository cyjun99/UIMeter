# UIMeter�������ֲ�

UIMeter����һ�����������������ͨ�������նˣ�����Putty��SecrueCRT������������ӡ�
�����Ժ����ͨ������ʹ��UIMeterȫ�����ܡ�ʹ�ô�������֮ǰ����Ҫ�л�ͨѶЭ�鵽
TERMЭ�飬�л�������ο�UIMeter�û��ֲᡣ

���ڲ���������ʾ��

![MODBUS���ڲ���](image/51-MODBUS���ڲ���.png "MODBUS���ڲ���")

������115200��8λ���ݡ�1λֹͣ����У�顢�����ء�
 
���ĵ�����UIMeter�̼�v17.7.1������̼��汾�����ο���

�����¹̼����������������ܻ��е�����ˡ������֪ͨ��

## getui
��ȡ��ǰ��ѹ��������ʱ�䡢���ʡ���������Ϣ��

�����ʽ��`getui`

�������������ʾ��
```
getui
 U: PGA=8 AD=0x000003  0.0000V 0.0000W      1uV
 I: PGA=8 AD=0x000000  0.0000A 9999.9R      0uV
 T: RAW=0x1600  22.0C   22.0C
 P: 0.0000Ah  0.0000Wh     32s
```
���������߿���ʹ�ø�����ɼ���ǰ���ݡ�

�������������ͨ��ִ�и������ѯ�豸ʵʱ���ݣ����Թر�������ԣ����͵����������д�Ѷȡ�

## clear
����豸��ǰʱ��͵�����Ϣ��

�����ʽ��`clear`��

�豸�ϵ��Ժ�����ʱ���Ah������Wh������һֱ�ۼƣ�ִ�и������Ժ�����ʱ�䡢Ah������Wh����ȫ�����㡣
��������Ϊʵʱ���£���������Ӱ�졣

## log
�����������ݡ�

�����ʽ��`log [dump|max|int|ring|auto|uh|ul|ih|il] Operate data logs.`

����������log���������ǰ���ã�������ʾ��������¼��������¼�����RINGģʽ���ء�
AUTOģʽ���أ�UH��UL��IH��IL�ĸ��������������������������˵����
```
log
log [dump|max|int|ring|auto|uh|ul|ih|il] Operate data logs.
 log data length is  4096
 log interval is   1
 ring mode is Off
 auto start log mode is Off
 UH= 0.0000V UL= 0.0000V
 IH= 0.0000A IL= 0.0000A
```

### log dump
log dump���������������������ݡ�

�����ʽ��`log dump [��������]`��

��������Ӧ��С���豸����¼����������10���������£�
```
log dump 10
    i,    t(s),    U(V),    I(A), Tself, Tprob
    0,      11,  0.0001,  0.0000,  26.5,  26.5
    1,      12,  0.0000,  0.0000,  26.5,  26.5
    2,      13,  0.0001,  0.0000,  26.5,  26.5
    3,      14,  0.0000,  0.0000,  26.5,  26.5
    4,      15,  0.0000,  0.0000,  26.5,  26.5
    5,      16,  0.0000,  0.0000,  26.5,  26.5
    6,      17,  0.0000,  0.0000,  26.5,  26.5
    7,      18,  0.0000,  0.0000,  26.5,  26.5
    8,      19,  0.0000,  0.0000,  26.5,  26.5
    9,      20,  0.0000,  0.0000,  26.5,  26.5
```

��һ��Ϊ����������
�ڶ���Ϊ�豸��¼����ʱ�����ʱ�䣨��λ�룩��
������Ϊ��ѹ�����÷��������������Ժ�Ϊ��������������
������Ϊ������
������Ϊ����¶ȣ����£���
������Ϊ̽ͷ�¶ȣ�K���ȵ�ż����ʱ�����壩
 
���Խ��������ն˲������ֹ��ܱ����������ݡ��˵�������(T)->��������(C)��
�򿪳����ն˵Ĳ������ֹ��ܣ������������֣�ִ����log dump���Ȼ��ֹͣ��
�������߼�¼���ݡ�
 
![�����ն˲�������](image/55-�����ն˲�������.png "�����ն˲�������")

�������ݸ�ʽΪCSV�ļ�������ʹ��Excel��������һ���ı��༭���༭��

v17.5.11�̼����ӷ����������������ܣ����÷������������������Ժ�ԭ��ѹ����¼����Ϊ������������

### log max
��������¼������

UIMeter�߱�2048��4096�������߼�¼����������ʹ��log max������������¼���ݡ�
```
log max 2
 Set Max data log to  2048
log max 4
 Set Max data log to  4096
```
����¼������Ҫ��ʵ���豸���õ�EEPROM����ƥ�䣬32kB��Ӧ2048����64kB��Ӧ4096����

��������¼����Ϊ2048��`log max 2`

��������¼����Ϊ4096��`log max 4`

�����Ժ�������Ч�����������Ҫִ��`param save`���

### log int
�������߼�¼�������λ�룬�磺`log int 10`���������߼�¼���Ϊ10��ÿ�Ρ������65535�롣

�����Ժ�������Ч�����������Ҫִ��`param save`���

### log ring
�򿪻��߹ر�RINGģʽ��

Ĭ��ģʽ�£���¼���ݴﵽ����Ժ�ֹͣ��¼��ͨ����RINGģʽ������ʹ���ݴﵽ���
�Ժ��Զ���0��ʼ��¼�����Ǿ����ݡ��÷�����������ѭ����¼���������µĲ������ݡ�

ʹ��`log ring 1`�����RINGģʽ��ʹ��`log ring 0`����ر�RINGģʽ��

�����Ժ�������Ч�����������Ҫִ��`param save`���

### log auto
�򿪻��߹ر�AUTOģʽ��

Ĭ������£��������߼�¼������Ҫ�û����ֶ�����������û���Ҫͬ���ɼ�ĳЩ����
��̨UIMeter֮��������ͬ�������ɼ��� ��˿��Դ�AUTOģʽ��UIMeter�ϵ��Ժ�
�Զ���ʼ��¼���ݡ�ͨ������̨UIMeterͬʱ�ϵ����������ͬ���ɼ���

ʹ��`log auto 1`������Զ���¼���ܣ�ʹ��`log auto 0`����ر��Զ���¼���ܡ�

�����Ժ�������Ч�����������Ҫִ��`param save`���

### log [uh|ul|ih|il]
�趨UH��UL��IH��IL�ĸ�������

�ĸ������������߼�¼��������UH��UL�趨��ѹ���޺����ޣ�IH��IL�趨�������޺����ޡ�

��¼�������£�

 1. UH>UL����ѹ���޸��ڵ�ѹ���ޣ�ʵ�ʵ�ѹ�������޲��ҵ�������ʱ��¼���ݡ�
 2. UH<UL����ѹ���޵��ڵ�ѹ���ޣ�ʵ�ʵ�ѹ�������޻��ߵ�������ʱ��¼���ݡ�
 3. UH=UL����ѹ���޵��ڵ�ѹ���ޣ����߼�¼���ݺ͵�ѹ�޹أ�ֻ������йء�
 4. IH>IL���������޸��ڵ������ޣ�ʵ�ʵ����������޲��ҵ�������ʱ��¼���ݡ�
 5. IH<IL���������޵��ڵ������ޣ�ʵ�ʵ����������޻��ߵ�������ʱ��¼���ݡ�
 6. IH=IL���������޵��ڵ������ޣ����߼�¼���ݺ͵�ѹ�������޹أ���ȫ����¼��

ע�⣬UH��UL��IH��ILΪ��ԭ���ֶ���¼���������ӵ��ĸ������������Ժ���Ȼ��Ҫ�ֶ�
��ͣ��¼�������ʹ����Ҫȫ������Ϊ0.

������������ο����£�
```
log uh 0
 set UH= 0.0000V
log ul 0
 set UL= 0.0000V
log ih 20000
 set IH= 2.0000A
log il 10000
 set IL= 1.0000A
log
log [dump|max|int|ring|auto|uh|ul|ih|il] Operate data logs.
 log data length is  4096
 log interval is   1
 ring mode is Off
 auto start log mode is Off
 UH= 0.0000V UL= 0.0000V
 IH= 2.0000A IL= 1.0000A
```
��������1AС��2Aʱ��¼�������ݣ�UH=UL=0V��IH=2A��IL=1A��

��ѹ����10Vʱ��¼�������ݣ�UH=0V��UL=10V��IH=0A��IL=0A��

�����Ժ�������Ч�����������Ҫִ�С�param save�����

## info
�鿴���������豸������

�����ʽ��`info [dev|lcd|probe|addr|alarm|baud] Display/Set system Info.`

����������info�����ȡ�豸������
```
info
 info [dev|lcd|probe|addr|alarm|baud] Display/Set system Info.
 DeviceType: STD_V20
 LcdType: LCD1602
 ProbeType: TYPEK
 ModbusAddr:   1 Baud: 115200
 ALARM: 1
 UART: TERM
 ECHO:1
 BackLight: 0x8
```
���ò����������ʽΪ��`info [������] [����]`

���������±���ʾ��

| ������ | ����                 | ȡֵ                          |
|:------:|:--------------------:|:-----------------------------:|
| dev    | �����豸����         | 1:��׼�� 2:�߷ֱ��ʰ汾       |
| lcd    | ������Ļ����         | 0:1602�� 1:LCD����            |
| probe  | �����¶�̽ͷ����     | 0:K���ȵ�ż 1:PT100 2:5kŷNTC |
| addr   | ���ô��ڵ�ַ         | 1-247                         |
| alarm  | ����ALARM����        | 0:�ر� 1:����                 |
| baud   | ����MODBUSЭ�鲨���� | 115200bps-2400bps             |

### info dev
UIMeter���а汾ʹ����ͬ�Ĺ̼�����info dev�������������֡�
- ʹ��`info dev 2`��������Ϊ�߷ֱ��ʰ汾�����1uA�����ֱ��ʡ�
- �����汾ʹ��`info dev 1`�������ã����0.1mA�����ֱ��ʡ�

�����Ժ�������Ч�����������Ҫִ��`param save`���

### info lcd
UIMeter����1602��Ļ��TFT������
- `info lcd 0`����Ϊ1602��Ļ��
- `info lcd 1`����ΪTFT������

�����Ժ�ִ��`param save`����������������Ч��

### info probe
UIMeter���������¶�̽ͷ��
- `info probe 0`����ΪK���ȵ�ż��
- `info probe 1`����ΪPT100��
- `info probe 2`����Ϊ5kŷNTC���衣

�����Ժ�������Ч�����������Ҫִ��`param save`���

### info addr
���ô��ڵ�ַ����ַ��Χ1-247.
- `info addr 2`���ô��ڵ�ַΪ2���õ�ַ��MODBUSЭ���ַ��ͬ��

�����Ժ�������Ч�����������Ҫִ��`param save`���

### info alarm
UIMeter��ALARM���ܰ���һ�����MOS�ܺ�һ��LEDָʾ�ƣ��ϵ�Ĭ����UIMeter���ơ�
����û���Ҫ�ֶ�����MOS�ܺ�LEDָʾ�ƣ���Ҫ���ȹر�ALARM���ܡ�
- `info alarm 0`�ر�ALARM���ܡ�
- `info alarm 1`��ALARM���ܡ�

�����Ժ�������Ч�����粻���档

### info baud
����MODBUSЭ�鴮�ڲ����ʣ�֧�ֲ����ʣ�115200��57600��38400��19200��9600��4800��2400��
- `info baud 9600`���ò�����Ϊ9600bps��
�����Ժ�ִ��`param save`����棬Ȼ���л�ΪMODBUSЭ����Ч��

**�����������MODBUSЭ����Ч��TERMЭ����Ȼʹ��115200�̶�������**��

## param
�����û�������

�����ʽ��`param [load|save|restore] Operate parameters.`

param��������������load��save��restore��
- `param load`���������EEPROM���ر���Ĳ�����
- `param save`����������浽����EEPROM��
- `param restore`����ָ�Ĭ�ϲ�����ͬʱ��ס���Ҽ��ϵ�Ҳ���Իָ�Ĭ�ϲ�����

## uset
��ѹͨ���������á�

�����ʽ��`uset [adj|zero|max|min|cali] [adj 100000x|U 10000x] set U param.`

����������uset���������ǰ��ѹͨ���͵���ͨ�������в�����
```
uset
uset [adj|zero|max|min|cali] [adj 100000x|U 10000x] set U param.
 U Adj:  0.99597   U Zero:       2
 I Adj:  0.99602   I Zero:       0
 U Max: 20.0000V   U Min:  0.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:     0A Gain:  1.00000
```

### uset adj
���õ�ѹ����У��ϵ����

��ѹ����У��ϵ����һ��1��������ֵ������У����ѹ���衢��׼��ʼֵ�ȴ�������
��Χ0-100�����UIMeter��ʾ��ѹ��ֵС��ʵ�ʵ�ѹֵ����Ҫ�����ѹ����У��ϵ����
��֮��С��ѹ����У��ϵ����

ʹ��uset adj�����ѹ����У��ϵ������Ϊ1.00234��������ʾ���趨��ֵ��Ҫ����100000��ȥ��С���㡣
```
uset adj 100234
uset
uset [adj|zero|max|min|cali] [adj 100000x|U 10000x] set U param.
 U Adj:  1.00234   U Zero:       2
 I Adj:  0.99602   I Zero:       0
 U Max: 20.0000V   U Min:  0.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:     0A Gain:  1.00000
```
 
### uset zero
���õ�ѹ��ƫУ��ϵ����

�����ѹͨ���ڶ̽Ӳ�����ʱ��Ϊ0����ҪУ����ѹ��ƫ����λΪһ����ѹ�ֱ��ʡ�

�����ѹ��ʾ0.0003V��ʹ��`uset zero 3`����У����

�����ѹ��ʾ-0.0002V��ʹ��`uset zero -2`����У����

### uset [max|min]
���õ�ѹ���ޡ���ѹ���ޡ�

UIMeterʹ�õ�ѹ���ޡ���ѹ���޿������MOS�ܺ�LED��������ѹ�������޲��ҵ�������
ʱ�����MOS��Ϩ��LED��������ѹ�������޻��ߵ������޹ر����MOS�ܵ���LED��

���÷����������£�
```
uset max 100000
uset min 20000
uset
uset [adj|zero|max|min|cali] [adj 100000x|U 10000x] set U param.
 U Adj:  0.99597   U Zero:       2
 I Adj:  0.99602   I Zero:       0
 U Max: 10.0000V   U Min:  2.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:     0A Gain:  1.00000
```
��ѹ��ֵ��Ҫ����10000��ȥ��С����

### uset cali
��ѹ����У׼��

����ʹ��`uset adj 100000`�����ѹ����ϵ������Ϊ1.
��UIMeter��ѹͨ�����׼��ѹԴ��������ȡ��׼Դ��ѹֵ��ִ������ `uset cali [��׼��ѹֵ]` 
UIMeter�Զ�����У׼ϵ������֤��ѹ��ʾֵ���׼��ѹֵ��ȣ���׼��ѹֵ��Ҫ����10000��ȥ��С����

�����Ժ�������Ч�����������Ҫִ��`param save`���

## iset
����ͨ���������á�

�����ʽ��`iset [adj|zero|cali] [adj 100000x|I 10000x] set I param.`

����������iset���������ǰ��ѹͨ���͵���ͨ�������в�����
```
iset
iset [adj|zero|cali|shunt|gain] [adj 100000x|I 10000x] set I param.
 U Adj:  0.99597   U Zero:       2
 I Adj:  0.99602   I Zero:       0
 U Max: 10.0000V   U Min:  2.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:     0A Gain:  1.00000
```

### iset adj
���õ�������У��ϵ����

��������У��ϵ����һ��1��������ֵ������У���������衢��׼��ʼֵ�ȴ�������
��Χ0-100�����UIMeter��ʾ������ֵС��ʵ�ʵ���ֵ����Ҫ�����������У��ϵ����
��֮��С��������У��ϵ����

ʹ��iset adj�����������У��ϵ������Ϊ1.00234���趨��ֵ��Ҫ����100000��ȥ��С���㡣
```
iset adj 100234
iset
iset [adj|zero|cali|shunt|gain] [adj 100000x|I 10000x] set I param.
 U Adj:  0.99597   U Zero:       2
 I Adj:  1.00234   I Zero:       0
 U Max: 10.0000V   U Min:  2.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:     0A Gain:  1.00000
```

### iset zero
���õ�����ƫУ��ϵ����

�������ͨ���ڲ���������ʱ��Ϊ0����ҪУ��������ƫ����λΪһ�������ֱ��ʡ�

���������ʾ0.0003A��ʹ��`iset zero 3`����У����

���������ʾ-0.0002A��ʹ��`iset zero -2`����У����

### iset cali
��������У׼��

����ʹ��`iset adj 100000`�����������У��ϵ������Ϊ1.
��UIMeter����ͨ�����׼����Դ��������ȡ��׼Դ����ֵ��ִ������ `iset cali [��׼����ֵ]`
UIMeter�Զ�����У׼ϵ������֤������ʾֵ���׼����ֵ��ȣ���׼����ֵ��Ҫ����10000��ȥ��С����

�����Ժ�������Ч�����������Ҫִ��`param save`���

### iset [shunt|gain]
���÷��������̺�����У��ϵ�����������v17.5.11�̼���ʼ֧�֡�

UIMeter��v17.5.11�̼���ʼ֧��ʹ�õ�ѹ���������������̽�J4�����Ҳ���λ��
Ȼ�����÷����������Ժ󼴿�ʹ�õ�ѹ�����Է�����������

һ���������������̵�ѹ��Ϊ75mV��75mV��ѹ�������̼�Ϊ���������衣
��75mV 150A������������Ϊ`75mV/150A=0.5mR`��

UIMeter����������΢С�����ϵ�ѹ����Ȼ������û����õķ���������
����������������ϵĵ�����

�����ʽ��`iset shunt [����������]`

�����ʽ��`iset gain [����100000���������У��ϵ��]`

��������������Ϊ100AУ��ϵ������Ϊ1.00111���������£�
```
iset shunt 100
iset gain 100111
iset
iset [adj|zero|cali|shunt|gain] [adj 100000x|I 10000x] set I param.
 U Adj:  0.99597   U Zero:       2
 I Adj:  0.99602   I Zero:       0
 U Max: 20.0000V   U Min:  0.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:   100A Gain:  1.00111
```
��������������Ϊ0AУ��ϵ������Ϊ1���������£�
```
iset shunt 0
iset gain 100000
iset
iset [adj|zero|cali|shunt|gain] [adj 100000x|I 10000x] set I param.
 U Adj:  0.99597   U Zero:       2
 I Adj:  0.99602   I Zero:       0
 U Max: 20.0000V   U Min:  0.0000V
 U Hys:  0.5000V   ChkNum:       4
 75mV SHUNT Range:     0A Gain:  1.00000
```
�������������÷�Χ1A-65534A���ɼ��������Ͼ��������������

��������������Ϊ0A����65535Aʱ���رշ����������������ܡ�
  
һ���û����÷����������Ժ󼴿�׼ȷ���������������û��߱������У׼������
����ʹ��iset gain�����һ����߲������ȡ�

�����Ժ�������Ч�����������Ҫִ��`param save`���

## ctrl
�豸�������

�����ʽ��`ctrl [echo|bklt|led|mos|time] [param] Device Control.`

ͨ���豸����������Կ����豸�����в�����

### ctrl echo
���������л��ԡ�
- �ر������л��ԣ�`ctrl echo 0`��
- �������л��ԣ�`ctrl echo 1`��

UIMeterĬ�ϻ����û�������ַ������Թر������л��ԡ�
```
version
 UIMeter v17.12.6 SN:FF56066E7875524828586719
 ECHO Studio <echo.xjtu@gmail.com>. All Rights Reserved.
ctrl echo 0
 ECHO=0
 UIMeter v17.12.6 SN:FF56066E7875524828586719
 ECHO Studio <echo.xjtu@gmail.com>. All Rights Reserved.
 ECHO=1
version
 UIMeter v17.12.6 SN:FF56066E7875524828586719
 ECHO Studio <echo.xjtu@gmail.com>. All Rights Reserved.
```
 �����Ժ�������Ч�����������Ҫִ��`param save`���

### ctrl bklt
���ñ������ȡ�

�����ʽ��`ctrl bklt [00-FF]`

����Ϊʮ�����ƣ�0x00��0xFF��0x00������0xFF��رձ��⡣
����ͨ��info����鿴��ǰ�������ȡ�����������£�
- ���ñ���������`ctrl bklt 00`
- ��ȫ�رձ��⣺`ctrl bklt FF`
- ���ñ���һ�����ȣ�`ctrl bklt 80`

�����Ժ�������Ч�����������Ҫִ��`param save`���

### ctrl led
����ָʾLED��
- �ر�ָʾLED��`ctrl led 0`��
- ��ָʾLED��`ctrl led 1`��

UIMeterָʾLEDĬ��������Զ����ƣ��û�Ҳ�����ֶ����ơ�
�û�ʹ��`info alarm 0`����ر��������LED������ʹ��`ctrl led`�������LED��
```
ctrl led 0
 set ALARM to 0 first, aborting...
info alarm 0
 ALARM: 0
ctrl led 0
ctrl led 1
```

### ctrl mos
�������MOS�ܡ�
- �ر����MOS�ܣ�`ctrl mos 0`��
- �����MOS�ܣ�`ctrl mos 1`��

UIMeter���MOS��Ĭ��������Զ����ƣ��û�Ҳ�����ֶ����ơ��û�ʹ��`info alarm 0`
����ر�����������MOS�ܣ�����ʹ��`ctrl mos`����������MOS�ܡ�
```
ctrl mos 0
 set ALARM=0 first, aborting...
info alarm 0
 ALARM: 0
ctrl mos 0
ctrl mos 1
```

### ctrl time
�����豸����ʱ�䡣

�����ʽ��`ctrl time [�豸��������]`

����������£�
- ��λ�豸����ʱ�䣺`ctrl time 0`
- �����豸����ʱ��Ϊ1Сʱ��`ctrl time 3600`
- �����豸����ʱ��Ϊ1�죺`ctrl time 86400`

UIMeter�ϵ��Ժ�����ʱ���0��ʼ�Զ����ӣ��û���ͨ��ctrl time�����ֶ���������ʱ�䡣

### ctrl dir
����TFT��Ļ��ʾ����

�����ʽ��`ctrl dir [0|1|2|3]`

��TFT��Ļ��4����ʾ����0��1��2��3��Ĭ����ʾ����Ϊ0��

��ΪĬ����ʾ����`ctrl dir 0`

������ֻ��TFT��Ļ�豸��Ч�������Ժ���Ҫ�������������Ч��

### ctrl menu
�����豸�ϵ��ʼ�˵���

�����ʽ��`ctrl menu [0|1|2|3|4|5|6|7]`

�˵����������±�

| ��� | �˵�       | ��Ļ | ��ע |
|:----:|:----------:|:----:|:----:|
| 0    | ��ѹ����   | 1602 | Ĭ�� |
| 1    | ����ʱ��   | 1602 |      |
| 2    | �¶Ȳ���   | 1602 |      |
| 3    | ���߼�¼   | 1602 |      |
| 4    | ������Ϣ   | 1602 |      |
| 5    | ������     | TFT  | Ĭ�� |
| 6    | ��������� | TFT  |      |
| 7    | �豸��Ϣ   | TFT��|      |

������TFT��Ļ�����ϵ��ʼ�˵�Ϊ��������棺`ctrl menu 6`

�����Ժ���Ҫ�������������Ч��

## sethys
���õ�ѹ����ͻ����������

�����ʽ��`sethys  [dec hys 10000x] [dec chkNum] set Hysteresis.`

UIMeterĬ��ͨ���û����õ���ߵ�ѹ��͵�ѹ�������MOS�ܺ�ָʾLED��
��⵽ʵ�ʵ�ѹ������ߵ�ѹ���ߵ�����͵�ѹʱ�Ͽ����MOS�ܣ�����ָʾLED��

﮵�طŵ�Ϊ�������÷ŵ��ֹ��ѹ3V���ŵ絽3Vʱ�Ͽ����MOS�ܣ����ڵ�������
��·����Ĵ��ڣ���ص�ѹ�����ߵ�3.3V���ϣ��������´����MOS���ٴηŵ硣
��������3Vʱ�Ͽ�MOS�ܣ�3.5V��MOS�ܣ�0.5V��ѹ���Ϊ����ͻ���

ͬ����﮵�طŵ�Ϊ�������÷ŵ��ֹ��ѹ3V��UIMeter�������N�ε�ѹ����3V�Ժ�
�Ͽ����MOS�ܣ�N����Ϊ��������

ע�⣺���û��������Ҫ����ʹ��Ĭ��ֵ��

## reboot
����ϵͳ��

���Դ�һ����ʱ��������λms�����`reboot 900`��ʱ900ms�Ժ�������

����������£�
```
reboot
 rebooting...
 UIMeter v17.12.6 SN:FF56066E7875524828586719
 ECHO Studio <echo.xjtu@gmail.com>. All Rights Reserved.
reboot 900
 rebooting...
 UIMeter v17.12.6 SN:FF56066E7875524828586719
 ECHO Studio <echo.xjtu@gmail.com>. All Rights Reserved.
```

## help
��ȡ���߰�����

����������£�
```
help
 getui -> get U I P R Info.
 clear -> clear power and time Info.
 log -> log [dump|max|int|ring|auto|uh|ul|ih|il] Operate data logs.
 info -> info [dev|lcd|probe|addr|alarm|baud] Display/Set system Info.
 param -> param [load|save|restore] Operate parameters.
 uset -> uset [adj|zero|max|min|cali] [adj 100000x|U 10000x] set U param.
 iset -> iset [adj|zero|cali|shunt|gain] [adj 100000x|I 10000x] set I param.
 ctrl -> ctrl [echo|bklt|led|mos|time|dir|menu] [param] Device Control.
 reboot -> reboot [delay ms] Restart system.
 help -> help Info.
 version -> display SW version and SN.
```

## version
��ȡ�̼����豸���кŵ���Ϣ��

����������£�
```
version
 UIMeter v17.12.6 SN:FF56066E7875524828586719
 ECHO Studio <echo.xjtu@gmail.com>. All Rights Reserved.
```