# test_NRF24L01_connection
Código para verificar que existe comunicación entre el Arduino (lo he probado para UNO y para NANO). Se utiliza de manera visual, se carga el programa al Arduino y se chequea en el monitor Serial. En principio debería verse algo así.

CheckConnection Starting

FIRST WITH THE DEFAULT ADDRESSES after power on
  Note that RF24 does NOT reset when Arduino resets - only when power is removed
  If the numbers are mostly 0x00 or 0xff it means that the Arduino is not
     communicating with the nRF24

SPI Speedz	 = 10 Mhz
STATUS		 = 0x0e RX_DR=0 TX_DS=0 MAX_RT=0 RX_P_NO=7 TX_FULL=0
RX_ADDR_P0-1	 = 0x4141417852 0x4141417852
RX_ADDR_P2-5	 = 0xc3 0xc4 0xc5 0xc6
TX_ADDR		 = 0x4141417852
RX_PW_P0-6	 = 0x20 0x20 0x00 0x00 0x00 0x00
EN_AA		 = 0x3f
EN_RXADDR	 = 0x03
RF_CH		 = 0x4c
RF_SETUP	 = 0x07
CONFIG		 = 0x0e
DYNPD/FEATURE	 = 0x00 0x00
Data Rate	 = 1MBPS
Model		 = nRF24L01+
CRC Length	 = 16 bits
PA Power	 = PA_MAX


AND NOW WITH ADDRESS AAAxR  0x41 41 41 78 52   ON P1
 and 250KBPS data rate

SPI Speedz	 = 10 Mhz
STATUS		 = 0x0e RX_DR=0 TX_DS=0 MAX_RT=0 RX_P_NO=7 TX_FULL=0
RX_ADDR_P0-1	 = 0x4141417852 0x4141417852
RX_ADDR_P2-5	 = 0xc3 0xc4 0xc5 0xc6
TX_ADDR		 = 0x4141417852
RX_PW_P0-6	 = 0x20 0x20 0x00 0x00 0x00 0x00
EN_AA		 = 0x3f
EN_RXADDR	 = 0x03
RF_CH		 = 0x4c
RF_SETUP	 = 0x27
CONFIG		 = 0x0e
DYNPD/FEATURE	 = 0x00 0x00
Data Rate	 = 250KBPS
Model		 = nRF24L01+
CRC Length	 = 16 bits
PA Power	 = PA_MAX

Si se ve algo como en el caso siguiente (donde sólo se ven 0x00 o 0xff) esto significa que hay problemas de comunicación entre Arduino y transceptor, bien por problemas en la configuración de los pines bien por la alimentación. (desconectando el pin de CSN se puede generar una situación de fallo de comunicación).

CheckConnection Starting

FIRST WITH THE DEFAULT ADDRESSES after power on
  Note that RF24 does NOT reset when Arduino resets - only when power is removed
  If the numbers are mostly 0x00 or 0xff it means that the Arduino is not
     communicating with the nRF24

SPI Speedz	 = 10 Mhz
STATUS		 = 0x7f RX_DR=1 TX_DS=1 MAX_RT=1 RX_P_NO=7 TX_FULL=1
RX_ADDR_P0-1	 = 0x0000000000 0x0000000000
RX_ADDR_P2-5	 = 0x00 0x00 0x00 0x00
TX_ADDR		 = 0x0000000000
RX_PW_P0-6	 = 0x00 0x00 0x00 0x00 0x00 0x00
EN_AA		 = 0x00
EN_RXADDR	 = 0x00
RF_CH		 = 0x00
RF_SETUP	 = 0x00
CONFIG		 = 0x00
DYNPD/FEATURE	 = 0x00 0x00
Data Rate	 = 1MBPS
Model		 = nRF24L01
CRC Length	 = Disabled
PA Power	 = PA_MIN


AND NOW WITH ADDRESS AAAxR  0x41 41 41 78 52   ON P1
 and 250KBPS data rate

SPI Speedz	 = 10 Mhz
STATUS		 = 0x00 RX_DR=0 TX_DS=0 MAX_RT=0 RX_P_NO=0 TX_FULL=0
RX_ADDR_P0-1	 = 0x0000000000 0x0000000000
RX_ADDR_P2-5	 = 0x00 0x00 0x00 0x00
TX_ADDR		 = 0x0000000000
RX_PW_P0-6	 = 0x00 0x00 0x00 0x00 0x00 0x00
EN_AA		 = 0x00
EN_RXADDR	 = 0x00
RF_CH		 = 0x00
RF_SETUP	 = 0x00
CONFIG		 = 0x00
DYNPD/FEATURE	 = 0x00 0x00
Data Rate	 = 1MBPS
Model		 = nRF24L01
CRC Length	 = Disabled
PA Power	 = PA_MIN




