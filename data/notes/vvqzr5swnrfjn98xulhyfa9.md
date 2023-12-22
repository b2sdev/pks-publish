
## Error occurred during initialization of VM

- 자바가 32비트일 경우 램을 1기가까지만 할당 가능하다!
- https://kin.naver.com/qna/detail.nhn?d1id=2&dirId=20411&docId=344517490


## Determining whether a Java installation is 32 bit or 64 bit

$ java –version
- If 64 bit is running you’ll get a message like:
```
java version "1.6.0_18" 
Java(TM) SE Runtime Environment (build 1.6.0_18-b07) 
Java HotSpot(TM) 64-Bit Server VM (build 16.0-b13, mixed mode)
```
- For 32 bit, the message is:
```
java version "1.6.0_21" 
Java(TM) SE Runtime Environment (build 1.6.0_21-b07) 
Java HotSpot(TM) Client VM (build 17.0-b17, mixed mode, sharing)
```

- https://wiki.scn.sap.com/wiki/display/SCM/Determining+whether+a+Java+installation+is+32+bit+or+64+bit
