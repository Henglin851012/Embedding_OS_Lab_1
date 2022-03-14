
# create 2 個 task :

## 1.vLedHandler():
```c=
BaseType_t xledtask = xTaskCreate(vLedHandler, "LED", 128,xQueue,  1, NULL);
```
  以mode控制模式, mode 0 -> 綠燈和紅燈交替輛 , mode 1 -> 紅燈閃爍亮
  並判斷如果queue裡有值,就做模式切換

## 2.vButtonHandler():
```c=
BaseType_t xbuttontask = xTaskCreate(vButtonHandler,"BUTTON", 128,xQueue, 1,NULL);

QueueHandle_t xQueue;
```
  用一個queue去判斷是否有收到button的訊息,且設定兩個Pinstate判斷當下(now)和上一次(pre)的pinstate,當now == 1 就send訊息進queue
