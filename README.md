# 6-Weekly-Report

## 주제 선정

### <모바일 키오스크앱>

#### 1. 선정이유
매장에서 주문시 자사앱을 설치해야지 주문이 가능하다는 점에 불편함이 많다. 이 앱은 큐알코드인식만으로도 매장의 키오스크역할을 해주기 때문에 매장별 자사앱을 설치하지 않아도 각 매장의 음료나 음식 등을 주문할 수 있다는 편리함이 있어서 선정하게 되었다. 

#### 2. 기능 설명

 (1) 이 앱을 이용하는 매장에 들어가면 각 매장의 정보(체인점이라면 지점명)을 담고 있는 큐알코드가 존재
 
#####  QR코드 생성 :
       createQRCode() 메소드의 파라미터로 들어가는 context가 내용이 되며
       multiFormatWriter.encode()의 파라미터로 들어가는 두 개의 숫자가 QR코드 이미지의 크기가 된다.
       

 (2) 큐알코드를 찍으면 주문서(키오스크)가 등장 (※ 체인점이어도 각 매장마다 다른 품절메뉴가 있을 수 있고 제주도의 스타벅스처럼  시그니처 메뉴가 다를 수 있기 때문에 매장마다 주문서(키오스크)를 따로 만들어야 함)
 
 ##### QR코드 스캔 :
       액티비티를 생성하고, onCreate()로 스캔 뒤 결과를 가져온다. 
       이 액티비티에 진입하면 곧바로 스캔모드가 활성화되게 된다.
       QR코드 화면을 커스텀하고 싶다면 액티비티를 생성하고 원하는 위치에 TextView따위를 넣은 다음
       initiateScan()전에 
       /* qrScan = new IntentIntegrator(this);
        qrScan.setPrompt("아래 띄울 문구");
        qrScan.initiateScan();*/
        다음과 같이 설정한다. 
        QR코드를 인식하면 오버라이드한 onActivityResult() 메소드에서 처리한다. 
        얻은 내용을 갖고 다음 액티비티로 이동하든지, 내용이 url이면 해당 주소로 이동하든지 하면 된다.


 (3) 주문서 작성을 완료하면 포스기로 주문서 정보가 넘어감 (굳이 전화번호가 아니라도 랜덤변수나 숫자(1,2,3,4...)로 각 주문서를 구별함)

 (4) 제품이 완성되면 주문서 정보를 통해 알림을 넣어줌 (전화번호를 넘겨주면 문자로 넣어주고 아니라면 푸시알람으로 대체)

 (5) 손님이 제품을 픽업해가면 포스기에서 픽업버튼을 눌러 주문서 정보를 삭제할 수 있음 



#### 3. 기대효과

(1) 요즘 코로나19가 유행인만큼 접촉을 최소화하는 것이 중요하다. 진동벨을 주고받는 상황에서의 위험요인도 이 앱을 통해 해결할 수 있다.

(2) 바쁜 매장은 하나의 키오스크와 직원과의 주문만으로는 대기시간이 길어질 수 있다. 이 앱은 개인 핸드폰속에 개개인의 키오스크가 존재하는 기능을 가지고 있기 때문에 
    대기 시간을 최소화 할 수 있다는 장점이 있다.
