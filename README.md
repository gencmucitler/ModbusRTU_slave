# ModbusRTU Slave Kütüphenesi

PIC18F46Q10 için yazıldı. Gerekli değişiklikler ile diğer PIC18F serisinde kullanılabilinir.

EUSART1 modbustan gelen veriler içindir.
EUSART2 debug amaçlı verileri gönderir.

Timer3 iki frame arasındaki süreyi ölçmek için kullanılıyor.
Şuan kod sadece 9600bps için yazıldı, diğer düzenlemeler yapılmadı.

Modbustan gelen tüm verilen önce gelen_veri[] ring buffera yazılıyor.
modbus_progress() fonksiyonu frame_baslangic[] dizisinden modbus frame başlangıç bilgisini alıp gelen_veri[] den mb_frame[] dizisine aktarıyor.
Daha sonrada mb_frame[] dizisinden gerekli modbus komutları işleniyor ve sonuçlar ilgili dizilere aktarılıyor.

Yazılacak projeye göre gerekli düzenlemeler yapılmalı. Modbus Poll programı ile test edildi. Fakat sahada test edilmedi. Eksiklikler hatalar olabilir.

Desteklenen komutlar:
01 (0x01) Read Coils
02 (0x02) Read Discrete Inputs
03 (0x03) Read Holding Registers
04 (0x04) Read Input Registers
05 (0x05) Write Single Coil
06 (0x06) Write Single Register
15 (0x0F) Write Multiple Coils
16 (0x10) Write Multiple Registers


