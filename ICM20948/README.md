# ICM20948

## Initial Steps:

Clone this repo and extract source.zip file

Inside the extracted folder, we have an already compiled and built bin file ready in release/bin/<filename>.bin
  
To start right away, download [ST LINK](http://www.st.com/en/development-tools/stsw-link004.html) and open the installed software.

After opening ST LINK, click on Target -> Connect.

Then, Click on Target -> Program and select the bin file in release/bin folder and Click program.

Once the programming is done, the flash memory restarts and is ready to use.

## Get Sensor data

We have setup two UARTs, one for logging and one for getting the sensor data. The configuration of both UARTs are as follows:

#### LOG UART
```
  uart_config.uart_num = LOG_UART_ID;
	uart_config.irqs_on = 1;
	uart_config.use_for_printf = 1;
	uart_config.use_dma_for_tx = 0;
	uart_config.use_dma_for_rx = 0;
	uart_config.tx_buffer = uart_logTx_buffer;
	uart_config.rx_buffer = NULL;
	uart_config.tx_size = UART_LOG_TX_FIFO_SIZE;
	uart_config.rx_size = 0;
	uart_config.baudrate = 921600;
	uart_config.rx_interrupt_cb = NULL;
	uart_config.tx_interrupt_cb = NULL;
	uart_config.rx_context = NULL;    
	uart_config.tx_context = NULL;
	uart_init(&uart_config);
```

### Main UART
```
  uart_config.uart_num = MAIN_UART_ID;
	uart_config.irqs_on = 1;
	uart_config.use_for_printf = 0;
	uart_config.use_dma_for_tx = 1;
	uart_config.use_dma_for_rx = 0;
	uart_config.tx_buffer = NULL;
	uart_config.rx_buffer = uart_mainRx_buffer;
	uart_config.tx_size = 0;
	uart_config.rx_size = UART_MAIN_RX_FIFO_SIZE;
	uart_config.baudrate = 2000000;
	uart_config.rx_interrupt_cb = NULL;
	uart_config.tx_interrupt_cb = NULL;
	uart_config.rx_context = NULL;    
	uart_config.tx_context = NULL;
	uart_init(&uart_config);  
```

We can connect to these UART's using putty or hyper terminal or even python using pyserial.

## Sensor-cli

To implement the cube program, we use sensor-cli. It is located in the extracted folder tools/sensor-cli.exe

Navigate to the above specified folder through command prompt and type the following command:
``` sensor-cli --target=emdwrapicm20x48,port=\\.\COMxx --adapter=dummy ```  COMXX being the comport of daughter board

If the device is correctly connected and flashed, this will display ```sensor-cli>``` prompt waiting for user input.

help command provides list of commands available.

type ```cube on grv``` and then ```en grv 20``` to start the cube program. 

To stop the sensor output, type ```dis grv```

## To make changes to the code

To modify the existing code, open the project in IAR Embedded workbech and open [example.c](https://github.com/prasanthnarasimha/COMP-7060-731-/blob/master/ICM20948/example.c)

Make the necessary changes and then click on Project->build all.

Once the build is completed, go to Project->Download and Debug. The modified code is compiled and downloaded to the flash memory. Once you're certain that the code is running as expected, click on run.

