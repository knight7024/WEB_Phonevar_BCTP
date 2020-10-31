## 로고
<img src = "./IMG/logo2.png" width="">

 <p align = "center"><a href="https://github.com/osamhack2020/WEB_Phonevar_BCTP/raw/master/PPT/PhoneVar_PPT.pdf"><img src="https://www.flaticon.com/svg/static/icons/svg/337/337949.svg" width="50"></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://drive.google.com/file/d/1-sjLwo3VrR89QWUArvEd-nJdfJbxaQRy/view"><img src="https://www.flaticon.com/svg/static/icons/svg/3074/3074767.svg" width="50"></a>
</p>

# 프로젝트 개요📖

## 개발과제
생활관 병사 스마트폰 비대면 반납 앱 [제안처 : 군수전산소]

## 기획의도
* 기존 스마트폰 제출방식의 __문제점__
   * 동시에 여러명이 반납하는 쏠림 현상으로 인한  __제출시간 지연__
   * 반납과 반출을 눈으로 하나하나 확인해야하는 __인력적인 수요__
<p align = "center">“수동”적인 제출 시스템  ➔ “능동”적인 제출 시스템</p>

## Phonevar란?
장병들의 주도적인 스마트폰 사용 및 관리를 자동으로 도와주는 서비스 앱입니다.

## 해결방안

>사이버지식정보방 사용일지처럼
“스마트폰의 사용일지”를 남겨
관리자가 확인하면 되지 않을까?

**스마트폰 사용시간 외 폰이 켜지거나 꺼지는 기록을 모두 남기고 관리자에게 비정상 사용 기록을 알려주자!**<br>
스마트폰의 끄고 켜짐을 기준으로 사용기록을 기록해 사용자가 정상적인 사용을 하고 있는지 비정상적인 사용을 하고 있는지 관리자가 기록을 확인하여 비정상이용 사용자를 식별하는 아이디어입니다.

## 폰바의 방향성
* __최소한의 데이터를 이용__<br>
  사용자가 정상적인 사용을 한다면 스마트폰에 기록이 남지 않아 기록 전송을 위한 데이터가 사용되지 않는다. 하지만 이상사용이 있다면 서버로 바로 데이터 전송이 일어납니다.
* __전원종료 제출방식을 이용__<br>
  직접 만지지 않아도 스마트폰을 사용할 수 있는 원격 장치의 이용을 막고자 전원종료 제출 방식을 필수로 합니다. ex)블루투스 이어폰을 이용한 음성제어 명령

## 개념도
![Alt text](/IMG/개념도.png)
- 스마트폰 사용시간 외 이상사용이 감지 될 경우 이를 기록하고 그 기록을 서버에 전송하여 관리자가 이상사용을 확인할 수 있도록 합니다.
- 스마트폰에서는 지속적으로 이상사용을 감지하고, 서버에 기록을 전송하기 전까지는 폰에 계속해서 기록이 쌓입니다.
- 기록된 내용들은 모두 이상사용들만 나타내고 과거의 모든 기록은 관리자 페이지를 통해 열람 할 수 있습니다.
- 서버에서는 이상사용이 감지가 되면 관리자 앱에 푸시알림으로 알려 즉각조치가 가능하도록 합니다.

# 프로젝트 기능설계

프로젝트는 크게 __앱/서버/웹__ 으로 개발 되었고, 각 파트는 다음과 같은 기능이 있습니다.
* __사용자 앱 / 관리자 앱__
	* 사용자 등록<br>
  <table>
		  <tr>  
				  <td><img src = "./IMG/app_user.png" width="400"></td>  
				  <td>데이터 위조를 방지하기 위해 서버 데이터베이스에 입력된 사용자만 스마트폰 등록을 할 수 있도록 했습니다. 기본적인 인적사항은 국방부 데이터와 연계한다고 가정했습니다.</td>  
		  </tr>
  </table>	
  
  * __사용기록 작성__<br>
	  다음아래의 기준에 따라 이상사용기록이 작성됩니다.
	  * __기준 1__
	  ![Alt text](/IMG/1.png)
	  * __기준 2__
	  ![Alt text](/IMG/2.png)
	  * __기준 3__
	  ![Alt text](/IMG/3.png)
  * __스마트폰 푸시 알림__
  <table>
		  <tr>  
				  <td><img src = "./IMG/app_user_push.png" width="500"></td>  
				  <td>제출시간 10분 전 병사들은 앱을 통해 스마트폰 제출 알림을 받습니다.(사용자앱) </td> 
				  <td><img src = "./IMG/app_admin_push.png" width="500"></td>  
				  <td>비정상적인 사용이 감지될 경우 앱을 통해 이상사용 알림을 받습니다.(관리자앱) 
		  </tr>
  </table>	

	* __현재 상황 확인 __
  <table>
		  <tr>  
				  <td><img src = "./IMG/app_user_list.png" width="250"></td>  
				  <td>관리자 앱을 통해 병사들의 이상 여부를 확인 할 수 있습니다.</td>  
		  </tr>
  </table>
  * __사용기록 서버 전송__

* __서버__
  * __API문서 제공__<br>
	  API DOC: [https://bctp.koreacentral.cloudapp.azure.com/phonevar/swagger-ui.html](https://bctp.koreacentral.cloudapp.azure.com/phonevar/swagger-ui.html)<br>
API EXAMPLE: [https://bctp.koreacentral.cloudapp.azure.com/phonevar/api/unit/list](https://bctp.koreacentral.cloudapp.azure.com/phonevar/api/unit/list) 
  * __관리자 푸시알림전송__
  * __사용기록 검증__

* __웹페이지__(관리자용)
  * __부대 로그인__
    <img src = "./IMG/web_login.png" width="">  
  * __현재 상황 확인__
    <img src = "./IMG/web_main.png" width="">
  * __사용기록 열람 / 사용자상태 변경(정상/비정상)__
    <img src = "./IMG/web_log.png" width="">
  * __스마트폰 사용시간 수정__(미구현)
   <img src = "./IMG/web_log.png" width="">
## 프로젝트 사용법 (Getting Started)
* __사용자 앱 / 관리자 앱__
  * 사용자 등록


  * 스마트폰 제출 푸시 알림
  * 사용기록 서버 전송

* __서버__
  * 사용기록 검증
  * 관리자 푸시알림
![Alt text](/IMG/web_login.png)
![Alt text](/IMG/web_main.png)
![Alt text](/IMG/web_log.png)

* __웹페이지__
  * 사용기록 열람
  * 스마트폰 사용시간 수정
  * 사용자상태 변경(정상/비정상)
MAIN PAGE: [https://bctp.koreacentral.cloudapp.azure.com/](https://bctp.koreacentral.cloudapp.azure.com/)

| 계정 | ID              | P/W |
|-----|-----------------|-----|
| 1   | 전투지휘훈련단    |  a  |
| 2   | 제9보병사단       | aa  |
| 3   | 수도기계화보병사단 | aaa |
    


### [기술 스택 (Technique Used)](/techstack.md)

# 프로젝트 전망
## 장점
 * 경제성<br>
반납을 하기위해 앱만 설치하면되고, 부가적인 반납시스템 구축 비용도 없다. 인원추가에 대한 물리적제한과 비용도 없다. 또한 유지보수 수요가 적으며, 이에 대한 부가적인 비용도 없습니다.   

 * 즉각성<br>
 사용자에게 사용시간 준수를 위해 푸시알림을 통해 미리방지하며,만약 서버에서 비정상적인 사용이 감지 될 경우, 즉시 관리자앱이 설치된 스마트폰으로 알림이 가기 때문에 빠른조치를 취할 수 있습니다.
 
 * 보완성<br>
 스마트폰에 직접 설치되는 앱서비스이기 때문에 다른 스마트폰을 이용해 반납하는 반납위조의 행위를 막을 수 있다. 자동으로 스마트폰의 끄고 켜짐이 기록되기 때문에 기록위조도 불가능합니다.

## 개선 방향
* 데이터가 없는 사용자 확인 : <br>
앱과 서버 간 통신이 가능한지 확인하기 위해서 하루에 한번씩 송수신 상태를 확인하여 실행현황을 최신화합니다.

* 출타자 관련 사용시간 관리 : <br>
출타 시 관리자 웹을 통해서 사용시간 제한이 해제되거나 수정 될 수 있도록 개선합니다.

* 강제종료 방지 : <br>
국방부 모바일앱처럼 사용자가 끄지 못하도록 해당 앱과 연계합니다.

* 시간조작 방지 : <br>
사용자가 시간조작을 하지 못하도록 서버시간으로 동기화합니다.

* 아이폰 사용자 : <br>
아이폰용도 BackgroundTasks Framework(App Refresh Task)를 이용해 추후 개발 가능합니다.

* 데이터 위조 방지 : <br>
JWT에 Access Token과 Refresh Token 방식을 적용하여 보안성 강화

## 발전 가능성
 * 1차적 시장 <br>
 지정과제를 낸 군수전산소를 주 타겟으로 하여 해당 서비스의 보안성과 보편성을 더욱 높이기 위해 기술개선을 합니다.
 * 2차적 시장 <br>
해당 서비스의 기록작성 기준을 스마트폰 전원 on/off가 아닌 블루투스 비콘의 신호여부로 전환하여 기숙사, 도서관의 인원출입 관리나 대중교통의 승하차 승객 관리서비스 앱으로 발전할 수 있다고 전망하고 있습니다.

# 프로젝트 관리
## 흐름도
![Alt text](/IMG/흐름도.png)
## 개발일정
![Alt text](/IMG/일정.png)

## 컴퓨터 구성 / 필수 조건 안내 (Prerequisites)
* ECMAScript 6 지원 브라우저 사용
* 권장: Google Chrome 버젼 77 이상

## 프로젝트 동영상
[![Alt text](/IMG/video.png)](https://drive.google.com/file/d/1-sjLwo3VrR89QWUArvEd-nJdfJbxaQRy/view)


## 팀 정보 (Team Information)
- kim dae yu (dea0323@gmail.com), Github Id: kimdaeyu
- jeong jong woo (knight7024@naver.com), Github Id: knight7024
- lee dong june (yhs06280@gmail.com), Github Id: JunBeul


## 저작권 및 사용권 정보 (Copyleft / End User License)
 * [MIT](https://github.com/osam2020-WEB/Sample-ProjectName-TeamName/blob/master/license.md)
 

<img src = "./IMG/logo.png" width="100px">

더 자세한 개발현황은
<https://www.notion.so/inhaunivkdy/2020-bctp-668f236ca2b142698428b55c9dd8812e>
에서 확인하시면 됩니다.
