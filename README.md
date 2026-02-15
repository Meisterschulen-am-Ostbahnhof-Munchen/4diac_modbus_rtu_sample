# 4diac_modbus_rtu_sample

Dieses Beispiel zeigt die Ansteuerung eines **Waveshare Industrial 8-Ch Digital Input & Output Modules** über Modbus RTU.

## Hardware-Details
Das Modul bietet 8 digitale Eingänge (isoliert) und 8 digitale Ausgänge (Relais). Standardmäßig kommuniziert es mit 9600 Baud und hat die Slave-ID `1`.

## Modbus RTU Konfiguration
Die Konfiguration ist in `modbus_const.gcf` hinterlegt.

### Verbindungs-String erklärt
`modbus[rtu:/dev/uart/1:9600:N:8:1:delay:1:500:c0..7:c0..7]`

* **rtu**: Modbus RTU Protokoll.
* **/dev/uart/1**: Die serielle Schnittstelle (entspricht `COMx` unter Windows).
* **9600:N:8:1**: Baudrate 9600, No Parity, 8 Databits, 1 Stopbit.
* **delay**: Ein spezieller Parameter für 4diac FORTE, der eine kurze Verzögerung nach dem Öffnen der Schnittstelle einfügt. Dies ist bei vielen RS485-USB-Wandlern für eine stabile Verbindung notwendig.
* **1**: Slave ID des Waveshare Moduls.
* **500**: Polling-Intervall in Millisekunden.
* **c0..7**: Zugriff auf Coils (Bits) 0 bis 7.
    * Im **Read-Bereich**: Liest den aktuellen Status der 8 Relais.
    * Im **Send-Bereich**: Steuert die 8 Relais an.

## Verwandte Projekte
* Gateway RTU to TCP: [4diac_modbus_rtu_tcp_sample](https://github.com/franz-ms-muc/4diac_modbus_rtu_tcp_sample)
* Pure TCP Sample: [4diac_modbus_tcp_sample](https://github.com/Meisterschulen-am-Ostbahnhof-Munchen/4diac_modbus_tcp_sample)

![image](https://github.com/user-attachments/assets/bcbc72dd-bd7d-4ef6-8031-77a32c7c5476)

