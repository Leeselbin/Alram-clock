Atmega128 을 이용한 알람시계 만들기


## 사용 기술 및 라이브러리

- C
- AVR Atmega128 (마이크로 컨트롤러 모듈)
- ***Codevision*** AVR 이용하여 코드 빌드 → 타겟보드에 라이팅


채터링(chattering) : 전자회로 내의 스위치 접점이 닫히거나 열리는 순간에 기계적인 진동에 의해 매우 짧은 시간안에 스위치가 붙었다가
                   떨어지는 것을 반복하는 현상(바운스 현상이라고도함)
                 
디바운스(debounce)  : 채터링 현상을 방지하기 위해 짧은 시간에 여러 번 스위치의 상태 혹은 이전상태를 확인하여 바운싱을 억제하기 위한것



ex) 해결법 

key = digitalRead(BUTTON);     //버튼값 key 변수에저장 

if(key == LOW){                //버튼 눌러짐
 if(keyState == HOGH){         //이전 버튼의 상태가 떨어져있다면 
     Serial.pritln(" 눌러짐 ");  
     keyState = key;           //버튼상태 저장
 }
 esle{
  if(keyState != HIGH){
      Serial.println(" 떨어짐 ");
      keyState = key;
   }
 }
   
