# Инструкция по сборке и тестированию
## Компиляция для yocto-18.0.0

```bash
. /opt/poky/2.4.4/environment-setup-armv7ahf-neon-poky-linux-gnueabi
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Debug -DBOARD_REV=0 ..
make
```
Значения `BOARD_REV`:
- `BOARD_REV=0` - PBX-MTV-508
- `BOARD_REV=1` - PN-MTV-581

## Сборка на x86

```bash
mkdir build
cd build
cmake -DCMAKE_PREFIX_PATH=~/Qt5.10.0/5.10.0/gcc_64/lib/cmake/ ..
make
```
## Проверка TSL
В папке `tsl` лежит `tsl_send.py`. Запустить его следующей командой:

```bash
./tsl_send.py -a 1 --txt "Input 1.2(tsl)"  192.168.2.241 15000
./tsl_send.py -r -a 10 --txt "Input 1.2(tsl)"  192.168.2.241 15000
./tsl_send.py -g -a 10 --txt "Input 1.2(tsl)"  192.168.2.241 15000
./tsl_send.py -r -g -a 10 --txt "Input 1.2(tsl)"  192.168.2.241 15000
```
Параметры:
- `-r` - цвет TALLY **красный**
- `-g` - цвет TALLY **зелёный**

### Таймер прямого отсчёта
**Старт:**
```bash
./tsl_send.py -a 50  192.168.2.219 1500
```
**Стоп:**
```bash
./tsl_send.py -r -a 50  192.168.2.219 15000
```
## Переключение раскладки
| Адрес  | № Раскладки |
|--------|-------------|
| 51..60 | 1..10       |

**Включить раскладку №1:**
```bash
./tsl_send.py -a 51 -r 192.168.2.219 15000
```
**Включить раскладку №10:**
```bash
./tsl_send.py -a 60 -r 192.168.2.219 15000
```
## Включение Solo
**Включить Solo для входа 1:**
```bash
./tsl_send.py -a 61 -r 192.168.2.219 15000
```
**Включить Solo для входа 7:**
```bash
./tsl_send.py -a 67 -r 192.168.2.219 15000
```
**Выключить Solo для входа 7:**
```bash
./tsl_send.py -a 67 192.168.2.219 15000
```
|  Каскадов | Входов | Адрес  |
|-----------|--------|--------|
| 1         | 1..8   | 61..68 |
| 2         | 1..15  | 61..75 |
| 3         | 1..24  | 61..84 |
| 4         | 1..29  | 61..89 |
| 5         | 1..36  | 61..96 |
# a-h-pbx-mtv-508-learn
