01 - 6 단원 소개
======================

이제 우리는 우리의 응용 프로그램의 UI를 구축 끝난 때문에,
그건 때 동작 할 것인가를 생각하는 시간입니다
하지 전경. 의 가장 강력한 기능 중 하나
Android는에서 실행되는 모든 응용 프로그램을위한 기능입니다
배경. 그러나 위대한 힘으로 큰 책임이 따릅니다. 그래서 당신이 필요
그것은 자원을 소비하는 방법의 매우 의식한다.이 중
단원에서는 당신은 Android 프레임 워크가 배경을 관리하는 방법에 대해 자세히 설명합니다
어플이나 당신이 지원하는 서비스 클래스에 도입됩니다
그것이 실현한다. 또한 효율적인위한 기술을 배웁니다
동기화 어댑터와 Google 클라우드 메시징을 사용하여 데이터 전송. 과
메시지를 보내는 통지 프레임 워크에 도입 된
당신 사용자에게 당신의 앱이 foreground에 없을 때.02 - 배경에서 선샤인
===============================

캐서린가 사용 된 경우 2 단원에는 기억하십시오
AsyncTask는 업데이트하려면 새로 고침 버튼에 매여
우리의 데이터? 라토 그것이 있었는지에 대해 이야기했습니다
나쁜 생각 AsyncTask는 묶여 있지 않기 때문에,
활동의 라이프 사이클.가상 머신이 개최합니다
활동 객체에있는 한,
AsyncTask는 Android가 부른 후에도 실행되어 onDestroy
활동을위한, 그것은 폐기 될 것을 기대하고 있습니다.
귀하의 휴대 전화를 회전시키는 경우, 동작은하고있다
당신의 활동을 파괴하고 새로운 것을 인스턴스화합니다. 더
순진 AsyncTask의 구현은 지금하려고 2 개의 스레드가 있습니다
같은 업데이트를 수행하는 등.포인트는
그것은 잠재적으로 매우 최선의 패턴이 없습니다
그런 웹 서비스에서 인출 한 배경 작업. 만약
응용 프로그램을 떠나, asynctask은하고 있습니다
당신의 프로세스가 계속 살아있는 한을 위해 실행
그러나 낮은 우선 순위로 실행하고 당신의 과정이 될
장치 않았다 경우 죽을 먼저하는 것입니다
더 많은 자원을 필요로합니다. 그리고 큰 문제가 있습니다.안드로이드
인스턴스화하기 위해 전경에 표시하고 실행합니다
처음에 작업. 우리가 시작했기 때문에
우리는 응용 프로그램을 시작하면 일기 예보를 업데이트하는 작업이
날씨가 급격하게 변화하면 바람직하지 않은 행동을 가질 수 있습니다. 이렇게
이제 우리는 업데이트를 실행하기위한 올바른 방법을 배울거야.
응용 프로그램이있는 동안 우리는 프로세스를 자동화하고 싶다
전경.그러나 더 중요한 것은 앱이 싶어
최소한의 배터리 소모를 가진 백그라운드에서 주기적으로 업데이트. 그 의지
나중에이 중에서 특히 중요하다
우리는 날씨의 통지를 소개 학습.


03 - 애플리케이션 라이프 사이클 및 서비스
===============================

백 4 단원에서 우리가 배운
Android 런타임은 눈에 보이는 활동에 애플 리케이션을 죽일거야,
포 그라운드에서 필요한 자원을 확보하기 위해,
응용 프로그램.그러나 안드로이드는 작업이 어떤 경우에
활동이 표시되지 않을 때 계속해야 것들
파일 다운로드 사진을 업로드하거나 음악 재생과 같은? 그런데,
따라서 응용 프로그램 구성 요소가 있습니다. 서비스. 우리는 이미했습니다
도입 된 활동, 컨텐츠 제공 업체,
방송 수신기 및 의도.서비스
Android 앱 구성 요소에 마지막 조각이다
퍼즐. 당신이 활동을 실시하는 것과 거의 마찬가지로 당신이하여 서비스를 시작
시작 서비스 호출에 대한 의도에 전달합니다.
그리고 당신은 호출하여 서비스를 동일하게 정지 할 수 있습니다
서비스를 중지하고 이름을 전달
서비스 중지 싶다.활동과 달리 서비스는 없습니다
사용자 인터페이스와 그들은 더 높은 우선 순위로 실행
배경 활동. 이것은 달리기하면 앱
서비스는 실행에 의해 살해 될 가능성이 낮은
포 그라운드 활동을위한 자원을 확보하기위한 시간.
사실, 기본적으로 시스템이 다시 부팅을 시도합니다
그들은 내부에서 정지되기 전에 종료하는 서비스
응용 프로그램.이것은이 단순화 된 라이프 사이클에 반영된다.
활동과 비교하여 서비스가 더 이상 실행을 실행하도록 설계되어있다
중단해서는 안 작업. 일반적으로, 당신은해야합니다
당신은 배경을 시작하는 장소입니다 onStartCommad 핸들러를 오버라이드 (override)
당신이 실행하려는 작업. 그러나다는 것을주의
상태의 변화를 모니터링하려면 핸들러는 반영하지
앱이 백그라운드로 이동한다.이것은 실행중인 때문입니다
서비스 자체가 프레임 워크를 신호
앱을 함유하는 다른 응용 프로그램보다 높은 우선 고려되어야한다
백그라운드에서 실행중인 서비스를 가지고 있지 않습니다. 일부에서는
당신의 서비스가 잠시 않도록 작업을 수행 할 예
UI가 있고 사용자 경험을 방해하지 않고 중단 할 수 없습니다.
예를 들어, 음악을 재생하거나 차 안에서 지원
탐색.이러한 경우에는 그 당신을 보여줄 수
서버에서 실행되는 것이 고려되어야한다
startForeground를 호출하여 전경. 당신은이 호출이 걸리는 것을 알 수 있습니다
알림. 이것이 나타나고 수없는됩니다
서비스가 중지 될 때까지 거부 또는 당신도
stopForeground를 호출합니다. 당신은 약간의 통지에 대해 자세히 설명합니다
나중에 댄.그러나 지금은 전경임을주의
서비스는 포 그라운드와 동일한 우선 순위로 실행됩니다
활동. 실행 시간은 거의 불가능
자원을 확보하기 위해 죽일 수 있습니다. 그럼 당신
자신에게 생각해도 내가 많이 저장할 수있다
문제 만 작성하면 수명주기를 취급
장기 실행 또는 포 그라운드 서비스.그런데, 내가 자란
호주의 해안을 따라 난 젊은 배운
전류에 대한 그 수영은 지치고 결국 쓸모 없다.
이 경우에는 그것이 더 어려워 의미
시스템 자원을 관리하기 위해 결국 연결
나쁜 사용자 경험. 현재 함께 수영. foreground를 사용하십시오
서비스 경우에만 한하여 절대적으로 필요하기 때문에,
그리고 가능한 한 빨리 모든 서비스를 중지합니다.그것은이다
또한 중요한 활동 및 수신기 서비스 같은 것을주의하는 것이
메인 스레드에서 실행됩니다. 그래서해야합니다
실행하기 위해 백그라운드 스레드 나 생각 태스크를 사용
당신이 원하는 장기 실행 작업
당신의 서비스에. 인생을 더 쉽게하기 위해 다음 수 있습니다
의도 서비스 클래스를 사용합니다.어느 대부분을 구현하고 있습니다
아트 인 텐트를 사용하기위한 일반적인 모범 사례 패턴,
서비스 내에서 실행된다. 그것은 큐를 작성
시작 서비스가 호출 될 때 전달 된 들어오는 의도. 이들은 다음 백그라운드 스레드에서 처리 순차적으로
onHandleIntent 핸들러 당신의 의도 서비스 구현에.
큐가 하늘의 경우 서비스 자체가 종료됩니다
새로운 목표는 수신되어 처리가 개시 될 때까지
다시.서비스는 강력한 도구이며, 그것이 중요하다
당신이 그들이 실제로 사용 방법을 이해하는
자신의 압연하기위한 프레임 워크의 대안이있는 경우가 많습니다
서비스 구현. 그것이 실행하기위한 의도 서비스인지 여부
백그라운드 작업과에 대해 알아 보겠습니다 동기화 어댑터
나중에이 단원.배경 데이터 동기화를 수행하기위한 전체


04 - 응용 프로그램의 우선 순위
=========================

그래서 지금 우리는 서비스가 어떻게 작동 하는지를 이해하고 있는지,
는 Android 애플 리케이션의 우선 순위를 결정하는 방법을 살펴 보자. 앱
우선 순위는 3 개의 일반적인 버킷으로 분할되어있다. 위험,
높다고 낮다. 각 버킷 속의 앱이있다
큐에 우선 순위를.의 App을 사용
가장 긴을 위해 가장 낮은 우선으로되어
먼저 실행된다. 중요한 응용 프로그램이있는 것이다
활성화되고있다. 그들은 사용자 상호 작용 전경에있다.
즉, 전경과 응용 프로그램에서의 활동이 포함
포 그라운드 서비스를 수행하고있다. 우선 순위가 높은 응용 프로그램은 보이는 포함
활동과 실행중인 서비스와 모든 응용 프로그램.전경의 애플 리케이션을 죽일보다 낮은 임팩트 동안 파괴
등의 작업을 수행하고있는 눈에 보이는 활동이나 취소 서비스
배경은, 아직 사용자에게 눈에 띄게 되겠지만 업데이트됩니다.
그래서 시스템은 그들을 죽일 것입니다
극단적 인 자원 위기. 그러나 백그라운드에서 응용 프로그램,
그들은 응용 프로그램의 우선 순위 빨간 셔츠를 입은 소위이다
상륙 파티.백그라운드 앱처럼 살해
필요에 따라 마지막으로 본에 먼저 순서를 죽였다
우선 순위가 높은 애플리케이션을 지원하는 것을 돕기 위하여. 내가 좋아하는
3 법칙 생각하기에
Android 자원 관리. 법 1, Android는 모든 응용 프로그램을 유지합니다
그것이 원활하게 실행하는 사용자와 상호 작용한다. Android의 의지
눈에 보이는 활동 또는 실행중인 실행중인 서비스와 모든 응용 프로그램을 유지한다.이렇게하는 것은 제 1 법칙을 위반하지 않는 한. 그리고 셋째, Android 모두를 유지합니다
백그라운드에서 앱 이것이 없으면 실행되는
첫 번째 또는 두 번째 법률을 위반한다. 이렇게
모든 것을 염두에두고 이러한 4 응용 프로그램을 검토하십시오. 당신은 무엇을
생각 시스템에 의하면, 이러한 응용 프로그램의 각각의 우선 순위이다.


05 - 응용 프로그램의 우선 순위
=========================

그 같다.맵은 눈에 보이거나 실행되지 않은
서비스이기 때문에 죽을 가능성이 가장 높습니다.
G 메일 서비스를 실행하고 있지만, 그것은 상호 작용하지 않는
직접 사용자와 Google의 음악 잠시
카메라 응용 프로그램입니다. 이 두 음악 APP의
오랫동안 전경되어 있어야합니다
카메라. 그래서, 약간 낮은 우선 순위를 가지고,
모두 죽을 중 하나의 위험에 노출되어 있는데.06 - 서비스 사용
===================

그래서 어떻게 우리는 서비스를 사용합니다
우리의 응용 프로그램을 구현? 다행히도, 우리는 이미하고 가장
일. 당사는 콘텐츠 제공자가
통지 된 내용 통지와
콘텐츠 관측. 우리의 FetchWeatherTask은 이미 완전히 독립적으로 작동합니다
우리의 UI의. 우리에 좋다.이제 우리
그 의도 서비스를 이용할 수 있도록
라토는 먼저 말했다. 그냥 몇 가지 작은 부
변화는 우리의 코드가 작동하여 얻을 수 있으며,
텐트 서비스 대신에게
날씨 작업을 가져옵니다. 시작하려면 작성하여 봅시다
우리의 서비스를위한 새로운 패키지. [SOUND] 그럼 우리는 요
서비스에서 연장 같은 패키지에 새 Java 클래스를 추가합니다.우리는 Ctrl 키 + I를 친다
다시 필요한 추상 메소드를 추가합니다.
생성자를 추가하려면 Ctrl + O.
서비스는 Android 구성 요소이기 때문에 그것은 그것이 것이 필요하다고 추측
명단. 그런데이하자. SunshineService을 구현 완료하자
과 ForecastFragment에서 그것을 호출합니다. 당신이 의도를 사용하여 서비스를 시작할 수 있습니다
StartService 방법.이것은 명시 적 인 텐트를 사용하는 방법을 기억하는 데 도움이됩니다.


07 - 서비스 사용
===================

모든 권리는 완료되었습니다. 그럼 내 이야기​​를합시다
이를 해결했다. 첫째로, 모든 코드를하자, 그리고
페치 기상 작업에서 복사합니다. 의도
우리가 실행하는 서비스가 실제로 헬퍼 스레드를 작성
으로. 비동기 작업이 무엇 비슷합니다.그래서 우리는
다만 위에 배경을하고 나서이 같은 것을 복사 할 수 있습니다
의도를 취급한다. 것 같이 몇 가지 유용한 상수를 추가하자
태그와 인 텐트 엑스트라를 기록하기 때문에 전달할 수 있습니다
위치 쿼리에서. 그런데, 우리는거야
를 통과하고 오류의 일부를 정리.
결국 텐트 서비스는 값을 반환하지 않습니다.과
그것은 서비스이기 때문에 자신의 컨텍스트를 가진다.
그리고 그 것이다. 우리는 날씨 작업을 가져가났습니다
의도의 서비스에 매우 편리합니다. 이제 우리 만
그것을 호출 할 필요가 있습니다. 그래서 지금 업데이트 중
예측 조각에 우리가 호출 할 수 있기 때문에 기상 기능
명시적인 의도를 이용한 서비스,
의도 특별히 파라미터를 둔다.
모든 권리는 그 실행 방법을 살펴 보자.그리고 때 우리
업데이트 버튼을 치는 그것이 우리의 새로운 서비스를 사용합니다. 꽤 좋다. 그리고 우리
정말 우리는 상황이있을 것으로 예상하고 싶은 방법입니다 아무런 차이도 말할 수 없습니다.


08 - 알람 사용
=================

그래서 지금 우리는 간단한 서비스를 제공하고 있습니다. 그 쉽지 않았습니다?
하지만 여전히 자신을 깨워하지 않습니다.다행히도 시스템이 있습니다
따라서 서비스. 이것은 소개하는 좋은 기회입니다
AlarmManager. AlarmManager는 해당 시스템에 지시 할 수 있습니다
당신은 당신의 응용 프로그램의 구성 요소를 깨워 원하는
업 기간 후에 어떤 작업을 수행
배경.당신도이 일어나 수 있습니다 당신의
응용 프로그램은 정기적으로 있지만, 우리는 백그라운드에서 무엇을 났나요?
그것은 우리가 가지고 있지 않은 Android의 구성 요소가된다
방송 수신라는 전에 보았다. 방송 수신
하는 데 사용되는 특별한 클래스이며,
다른 응용 프로그램에서 자주 의도 방송을 수신. 일반적으로
방송 수신기를위한 인 텐트 필터를 등록합니다
이러한 방송.또한 응용 프로그램이 의지 한 방법이다
알람에 듣는다. 그럼 몇 가지 알람을 추가하자
것. 첫째, 방송 수신을 추가하는거야
선샤인 서비스의 정적 내부 클래스로.
이것은 Android의 구성 요소입니다, 그래서 등록합니다
매니페스트에서이 방송 수신기. 주의
길의 정적 내부 클래스는 표기되어있다.글쎄했습니다
당신의 방송 수신기의 뼈를주고
그것은 경보를 처리 할 수​​ 있지만, 지금 그건
당신의 차례. 당신은에서 PendingIntent를 만들 수 있습니다
명시적인 의도는 알람 관리자 활성화를 가지고
당신의 방송 수신기. 나는 이야기가되지 않을 정도로 뭔가에 알람을 설정하는 것이 좋습니다
5 초와 같은 짧은, 그래서 당신은 쉽게 작동하는지 테스트 할 수 있습니다.09 - 알람 사용
=================

모든 권리는 완료되었습니다. 그러면 솔루션을 살펴 봅시다.
나는 질문에서 말했듯이, 우리는거야
업데이트의 날씨 기능 예측 조각 내부 작업.
먼저 표준 의도를 만드는 데 필요한 것
우리의 경보 수신기을 위해. 그렇다면 우리의 위치 쿼리를 추가
추가로. 다음 보류에 그것을 포장
의도.보류중인 의도는 객체의 특별한 종류이다
그것은 의도를 설명하고 있습니다. 이것은 다른 응용 프로그램을 구현 할 수 있습니다
사용되고 원래 의도의 특징
보류중인 의도를 만듭니다. 우리는 이것을 사용하는거야
일단 의도를 보류했기 때문에 나는 플래그 1 샷을 설정하십시오.
그럼 우리는 알람 서비스를받을 알람 설정
지금부터 5 초를 트리거한다.그러나 아직도 우리
우리의 알람이 무언가를하기 위하여 필요합니다. 뒤에
방송 수신기, 우리는 표준 의도를 보낼 필요가있다
우리의 서비스를 시작하고 그것이이고 있습니다. 그러면 실행하자
응용 프로그램. 모든 권리이기 때문에 지금 우리가 가지고있는
우리의 서비스 방해가 알람 매니저. 우리
새로 고침을 친다. 그것은 우리에 약 5 초 이상 할게요
우리는 실제로 지금의 데이터를 참조하기 전에.그리고 거기에 우리
그것을 가지고있다. 매우 간단한 알람. 하지만과
이 잠재적으로 백그라운드에서 업데이트 서비스를 사용하여
우리는 여전히 우리의 사용에 더 효율적이다 수
휴대 전화 자원. 라토는 우리에게 그것에 대해 많은 걸 알 수 있습니다.10 - 데이터를 효율적으로 전송하기
==================================

우리는 데이터 전송 효율 대해 이야기 할 때 일반적으로 우리는 말했다
전송되는 데이터의 양을 제한하는 정도. 즉, 절감
대역폭과 비용은 일반적으로 꽤있다
좋은 아이디어. 하지만 모바일에서 추가 요인이 있습니다. 당신과
볼 수 그것은 셀 무선으로 판명
장치에서 최대 배터리 물 1.그래서 만들기
당신의 데이터 전송을보다 효율적으로. 또한 개선 된 것이다
배터리 수명.그런데, 기본적인 수준이 지출보다 효율적인 수단임을
더 적은 시간, 더 적은 데이터를 전송 당신의 페이로드를 줄이고 업데이트
자주 거기에 길의 일부를 취할 수 있으며,
그런데 무엇? 타이밍이 차이를 만들 수 있습니까? 그것은 턴
그것이있다. 그리고 그것은 내가 좋아하는 상황이라는 점에서
쿠키 이드 난제로 생각.우리의 작업을 수행합니다
큰 페이로드와 약간 다운로드를 실행? 아니면 우리가 가고 준다
바로 그 때, 우리를 위해 시간 내에 소규모 전송 많은
그들을 필요로하는? 하나의 큰 쿠키와 작은 쿠키 많은?
그래서, 당신은 어떻게 생각하십니까? 우리는 가지고 있어야합니다
에 의해 나타나는 큰 다운로드 수가 적은
이 큰 쿠키?또는 다수의
작은 다운로드, 조금 쿠키의 많은에서 나타나는 것처럼. 11 - 데이터를 효율적으로 전송하기
==================================

여기서 첫 번째 유리에서 각 전송 페이로드를 줄이고,
이것은 필수입니다 경우에만 데이터를 전송하면 소리 접근처럼 보인다.
당신은 전송되는 데이터의 양을 줄일 수 있기 때문에 그것은 다음
네트워크 데이터입니다.즉, 보존 처리를 실시하고 더 적은 낭비 일이다
장치의 데이터. 그것은 기본적으로 연기 예다
당신이 실제로 알고있을 때까지 모든 작업은 당신이 그것을 할 필요가 있습니다.
그러나이 방법은 비교, 그것은 단점이있을 수 판명
프런트까지 그 작업의 모든 빅 쿠키 모델.
따라서 전반적으로, 이것은 좋은 해결책이다. 그러나 여기에서 큰 자세히 살펴 보자
쿠키의 모델.그리고 우리는 정말 그것을 위해
아래에있는 셀의 무선 상태 기계를 이해할 필요가있다.


12 - 셀 무선
===================

장치의 셀 무선은 대략 다음과 같이 작동합니다.
초기 유휴 상태에서, 그것은 몇 초 정도 걸립니다
그것이 전송을 시작할 수있을 때까지 넣습니다. 그런
지연은 싫은 웹 브라우징 경험 할 수 있습니다.그래서이 아니라
아이돌 다시 상태 머신은 풀 파워로 켜져
일정 시간. 일반적으로 주변의 5 ~ 10
사용하여 중간 저전력 모드로 드롭 할 때까지의 초
전체 전력보다 작은 배터리 및 반환에 낮은 지연을 가지고
대기 모드보다 전력에. 새로운 경우
전송이 시작되고 라디오는 뒷면에 추진
풀 파워 모드.그리고 아무것도 다른 기간에 일어나지 않는 경우
분에 약 30 초의 시간 일반적으로, 그것은 해요
대기에 다시 놓습니다. 꼬리 시간의 정확한 대기 시간
경력 사이, 심지어 국가 간의 경력에​​ 변화
국가들이 길고 낮은 지연 시간의 균형을하려고
배터리 수명 셀의 혼잡과 같은 요인에 따라 전형적인
네트워크 상태 실세. 그래서 정확한 타이밍이 다릅니다.어떻게
우리의 전송 주파수를 최적화합니까? 마지막으로, 그것은 문제가 아니다
구체적인 타이밍이있는 것. 그냥 필요
네트워크는 균형하려고하는지 이해하기
높은 배터리 수명과 낮은 레이턴시. 우리를 위해, 시간
그것은 데이터 전송을 할 예정입니다, 우리는 정말 좋아
어딘가 주위에 여기에.지금 우리가 돌​​아갈 때,
셀 무선 상태 기계에 쉽게 우리가 알고있는
우리는 데이터 전송 무선 의지를 실행할 때마다
전체 꼬리 적어도 다른 5 초 동안 활성 상태
시간 어디서나 30 초에서 낮은이지 분에
그것이 결국 대기로 돌아 가기 전에 전원. 즉 모든 시간을 의미
당신은 당신이 셀 무선을 파워 업하고있는 전송을 시작
적어도 20 초.그럼 어떻게 봐 봅시다
그것은 조금 쿠키 방식을 사용하여 응용 프로그램에 영향을줍니다. 앱
이것도 전송하지 배터리를 소모 할 수 있도록
많은 데이터입니다. 이러한 작은 피크는 각각입니다
응용 프로그램은 서버에 그 분석을 다시 ping ,.
이 경우에는 15 초마다. 이러한 LOGI- 피크 나타내는
간헐적 인 데이터 전송은 사용자 상호 작용에 근거한다.예를 들어,
그들은 상장 레스토랑을보고 찾고 있는지
내일의 일기 예보. 그 밑에, 우리는 어떻게 그래프 화되어왔다
이것은 무선 상태에 영향을 미칩니다. 액티브 블루 쇼
데이터 전송. 빨강, 전력에 라디오.
저전력 모드를 나타내는 노란색. 만약 사이의 간격
거기에 모든 었 라디오가 아이돌 이었다는 것을 보여준다.잠시이라
이 응용 프로그램은 시간의 비율이 것이 무엇인지 실행되는
셀 무선 유휴 상태로 돌아갈 수 있나요?


13 - 셀 무선
===================

이 응용 프로그램이 작동하고있을 때 언제든지 이렇게, 그건
지속적으로 전원이 켜 셀 무선을 유지한다. 로
사실 라디오 업데이트는 혼자하기에 충분하다
지금까지 아이돌에 돌아와서 무선을 방지한다.14 - 빅 쿠키 모델
=====================

이 앱은 예를 참조하십시오.
큰 쿠키 모델을 사용하여 네트워크 트래픽을 조각. 모든
반복 전송이 함께 번들되고, 모든되고 있습니다
간헐적으로 전송되는
대부분은 적극적인 프리 페치 및 교환.물론, 일반적으로 완전히 어떤 데이터 이용자를 예측 할 수 없습니다
필요가 있을지도 모릅니다 또한 클라이언트 또는 서비스 중 하나를 무시할 수 있습니다
사이트는 동기화 필요성을 변화시킨다.당신은 할 수있다
를 통해 무선 상태 전이의 수를 최소화하는 것을 목표로
일괄 처리 이외에 적극적인 프리 페치의 조합
그리고 시간은 중요하지 모든 전송을 대기하고
사용자가 시작한 시간이 중요한 전송 이들을 묶는 또는
서버에서 시작 것.우리는 영향을 비교 한 경우
큰 쿠키 모델의 라디오에서 비교 한
온 디맨드 방식으로 이전에 당신이 한 볼 수 있습니다
지금 시간의 3 분의 2 가까이 아이돌.또한
활성 무선 비율은 개선 된 덕분에 크게 감소하고있다
원샷에 더 많은 데이터를 전송 한 결과적으로 효율성을 다운로드


15 - 데이터 전송 모범 사례
=================================

당신은 기억할 필요가 가장 중요한 것은 것입니다
당신이 아무리 작은 데이터를 전송하지 때마다 라디오
절반 가까이 분에 파워 업 체재 할 수있다.그래서 모든
당신이 만드는 결정은 수를 최소화에 따라 이루어집니다
이것이 발생한 횟수입니다. 물론, 여기에서 균형이 있습니다.
당신은 사용자의 가능성이있는 모든 데이터를 다운로드 할
위의 단일 버스트에서 현재 섹션의 필요성
전체 용량에서 단일 연결.물론, 당신은하지 마십시오
단, 배터리 전력과 대역폭을 낭비 모든 풀다운
사용하려는 결코이다 데이터를 다운로드한다. 지금은 갈 수있다
이 항목의 시간이 댄을 위해 참을성이.과
당신은 각각의 구현 방법에 대한 자세한 배울 수 있습니다
프리 페치를 포함하여 이러한 모범 사례
일괄 처리와 밴드 링, 당신을 포함
주파수를 업데이트하는 일련 것을보고 당신의 페이로드를 최소화
Dev의 Lite의 동영상과 내부에 링크 된 개발자 가이드를 읽고
강사는 다음 주.지금은 댄에게 맡기는 전에
때문에 동기화 어댑터를 구현하는 방법을 보여 드리기 위해
모범 사례를 많이 이용하고 있습니다 선샤인
지금 설명하고 모범 사례가 어떻게 될지 생각해 봅시다
당신이 뉴스 리더 앱 같은 것을 구축하고있는 것.어떻게
앱이 처음 시작할 때 많은 데이터는 당신이 다운로드하십시오?
그냥 헤드 라인의 첫 페이지 모든 스토리와 이미지
그 첫 페이지에서 링크 된? 모든 사용 가능한 이야기​​하지만 아무도
이미지? 모든 스토리와 현재 이용 가능한 모든 이미지 또는?16 - 데이터 전송 모범 사례
=================================

모든 데이터를 풀다운하면 대기 시간을 단축하고 극대화합니다
배터리 효율성. 하지만 사용자가 모든로드하려고하고 있다고한다
기사. 그래서 당신은 더 많은 대역폭을 낭비하는 것입니다.다운로드
사진 없음 모든 기사는 실제로 있으면 우리의 효율을 개선하지
당신은 아직 할 필요가 있으므로 그냥 첫 페이지를 다운로드하는
물품이있을 때에는 언제든지 이러한 사진을 다운로드하기 위해 라디오를 활성화
선택했다.정답은 제목과 얻을 수 있습니다
그들이 가장 가능성이 높은 원인 프론트 페이지에서 링크 기사 "
사용자가 시작하게 읽을
응용 프로그램을 찾아. 당신이 단계적으로 그 캔
더 많은 기사를 매번 다운로드하는 사용자가 이동
지역 당신이 아직을 위해 프리 페치되어 있지 않습니다.


17 - 소개 SyncAdapters
=============================

배경을 만들고 배울 것이 많이 있습니다
효율적인 거래를.그러나 좋은 소식은 그 Android합니다
당신에게 그 구현 싱크 관리자 프레임 워크를 제공합니다
이러한 모범 사례의 많은. 당신은 그 프레임 워크를 사용
동기화 어댑터를 구현함으로써. 프레임 워크 원래
안드로이드 2에서 도입되었다. 0 에클 레어와 Android API 레벨
Google 애플 리케이션은 효율적인 동기화 사용 기본 프레임 워크.결국은 모두 놓는다위한 중앙 위치입니다
한 장소에 장치 데이터 전송.
그들 모두를 지능적으로하여 예약 된 바와 같이,
OS. 즉, 그것은 하나의 큰 쿠키이다.
Android 동기화 관리자는 동기화를 사용하여 동기화 요청을 처리합니다
어댑터.관리자 배치와 시간 변화의 동기
이러한 요구 가능하다면 당신의 데이터를 허용하려면
다른 응용 프로그램에서 전송에 예약 할에 전송
모든 줄이는 목표를 향해 노력
횟수는 시스템이 스위치 온해야
라디오. 장치가 적은 메모리를 가지고있는 경우
그것은 약간 동시 synchs을 예약합니다.의 Synch 매니저
또한 체크하는 것과 돌봐
때 전송 및 재시 다운로드를 시작하기 전에 네트워크 연결
연결이 드롭됩니다. 동기화 프레임 워크는 컨텐츠와 연동
양방향 동기화를위한 공급자와 Android를 활용
있는 동기화 서비스를 제공하기 위해 계정 관리자
계정과 관련된.우리의 응용 프로그램은 모두합니다
이러한 것이 우리는 여전히해야합니다
이러한 기능의 복잡성의 일부를 처리합니다.
이것은 SyncAdapter 처음에는 어려운 것처럼 보일 수 있습니다.SyncManager 당신이 페치 돕기 위해 무엇을 할 것인가
네트워크에서 데이터? 그것은 당신의 예약 있나요
다른 응용 프로그램과의 네트워크 작업은 동기화 프로토콜을 구현하고
스토어 계정 정보 또는 재시도 논리가있다
요청? 일치 이들을 모두 선택합니다. 18 - 소개 SyncAdapters
=============================

SyncManager는 당신의 SyncAdapter을 예약하지
작업.하지만 그들은 아무것도 없어
위 무슨 일을 어떻게 할
철사. 표준 동기화 프로토콜은 없습니다.
그들은 AccountManager는에 묶여있는 동안 그들은 저장과는 아무 관계도 했죠
계정 정보. 그러나 그들은 자동 의지
네트워크 상태가 변화하면 요청을 다시 시도하십시오.


19 - SyncAdapter 구현
===============================

그러면 무엇 그것은 의지를 살펴 보자
아주 기본적인 SyncAdapter을 구현하기 위해 걸린다.우리는 거 다
두 서비스를 씁니다. 각 서비스는 기본 하나를 제공합니다
안드로이드를 나타내는 개체를 제공하는 것을 목적
시스템 프레임 워크의 1에 바인더 인터페이스.
바인더는 실제로 구현 낮은 수준의 접착제이다
Android 크로스 프로세스 간 통신. 당신의 결합제를 사용하여왔다
당신이 Android 시스템 서비스에 이야기를 할 때마다.의도와 콘텐츠 제공자는 위만 높은 수준의 추상화이다
바인더 인터페이스의 상단. 알려진 전체 언어가 있습니다
AIDL로 이러한 인터페이스를 정의하는 데 도움이됩니다. 우리는 아니다
여기 전부를 충당하기 위해 가고, 많이 있습니다
더 당신은 서비스와의 결합 제로 할 수 있습니다.One
우리가 시작하기 전에 더 많은 것은, 우리를 정의하는거야
Authenticator에 서비스와 인증 자. 하지만 유일한 의지
우리를 가능하게하기 위해 Android의 계정 프레임 워크에서 사용되는
계정을 만듭니다. SyncAdaptor은 계정이 필요합니다.
와 계정의 틀은 존재해야합니다
Authenticator에 서비스로 전달 Authenticator에.당신은거야
우리의 Authenticator에 다만 시리즈임을 참조하십시오.
위해 발생의 예외를 제외하고 스텁의
그냥 없다는 것을 증명하기 위해 각 통화
정말 사용. 마지막주의 사항. 이 섹션에서는 약
동기화 어댑터 주위 developer.android.com의 온라인 교육을 따릅니다.
당신이 가지고있는 경우는 거기에보고 부담없이
더 이상 질문. 우리는 새로 만들거야
이 장점을 모두 수용하는 패키지 싱크.
그리고 우리의 Authenticator에 대한 새로운 클래스 파일. 이
우리가 정말 붙여 넣으려고하는 코드
마찬가지로 developer.android.com 웹 사이트에서오고있다, 그리고
위의 이전 그냥 스텁입니다. 당신이 말할 수있는
우리는 중 하나를 호출하기위한 예외를 슬로우하므로,
생성자를 제외하고 작동합니다. 그리고 하나
여러 파일. SunshineAuthenticatorService을 만듭니다. 이것은 더 많은 코드이다
그것은 우리를 위해 쓰여져있다.그것은 가능
빈 오 센티 케이타에 액세스하기위한 계정 관리자
우리 만 부착되어있을 것. 지금 우리는 strings.xml에서 계정 유형을 추가합니다. 더
계정 유형의 문자열은 그것이 특이하다는 것을 시사하고있다
우리의 응용 프로그램에. 우리는 많은 응용 프로그램을 가지고 있었다면
동일한 계정을 사용하여 우리가 좋습니다
다만 example.com 계정을 만듭니다. 우리는 또한 해요
물건을 정리하고 추가를 시작
콘텐츠 권한 문자열. 이것이 일치하는 점에 유의하십시오
우리의 콘텐츠 공급자 문자열. 그들은 모두 사용처럼, 우리는 나중에 XML 파일을 수정합니다
이 같은 문자열입니다. 우리는 새로운 XML 리소스 파일을 만들고 파일 이름
루트 요소 계정 인증 자와 authenticator.xml ,.
그리고 당신은 아마 SunshineAuthenticatorService가있는 것으로 나타났습니다
실제로 등록해야 서비스
의 AndroidManifest.xml 패키지 관리자를 갖는다. 여기에서
바로 그것을 할 몇 가지 더 페이스트의 장점. 현재 매우주의하십시오. 이러한 문자열
모두가 정확하게 일치해야합니다. 오류 메시지
시스템은 잘못된 계정이 있기 위하여주는
반드시 직관적 없습니다. 그리고 그것으로 당신
유효한 계정을 만들 수있을 것입니다.다시 한번,
SyncAdapter있는 모든 단지 있도록합니다
계정과 관련된. 당신이 실제로 이것을 사용하지 않는
전혀. 판권 우리의 공급자 태그를 조정합시다
명단. 우리는 동기화 가능한 속성을 추가 할 생각이다.
이것은 다만 Android는 우리가 동기화하기 위해 계획하고있는 것을 알 수 있습니다
서버와 콘텐츠 제공자.또한 우리는 설정합니다
안드로이드 : 내보내기 가짜 같다. 우리는 기본적으로 그것을 가지고 있었다.
어떤 다른 응용 프로그램은 우리의 콘텐츠를 볼 수있는 것을 의미합니다. 마지막으로,
우리의 새로운 문자열을 사용하는 권한을 변경하여 봅시다. 지금
몇 가지 추가 권한을 위해. 우리는 할 수 있도록해야합니다
읽어 동기화 설정을 설명합니다. 그것은 말이있다.또한 우리
우리가 정말 사용하지 않는 경우에도 계정을 인증해야
무엇을위한 그들. 이러한 권한은 모두 무슨 사용자가 없습니다
걱정할 필요가 있습니다. 하지만 개발자로서 우리는 항상하고 싶은
우리는 새로운 권한을 추가 할 필요가있는 경우에주의한다.
내부 SunshineSyncAdapter 파일 자체를 만들어 보자
추상 스레드 동기화를 확장하고 동기화의
어댑터 클래스입니다.Ctrl 키를 + I로 Ctrl + O 히트
생성자에서 필요한 추상 메소드를 구현한다.
우리는 첫 번째 생성자를 사용합니다. 우리는 묻어
이 중 후. 당신이 기억 수도로
동기화 어댑터 패턴은 또 다른 서비스가 필요합니다. 이렇게
우리는 SunshineSyncService라는 다른 Java 클래스를 작성하자.
이 클래스는 동기화 관리자 동기화 어댑터 바인더를 전달하는 데 사용된다.바인더에 의해 우리를 위해 구현되어 있습니다
추상 동기화 어댑터 클래스를 스레드. 그리고 반환
getSyncAdapterBinder 방법으로. 그리고 지금 우리
1 여러 XML 파일이 필요합니다. 과 syncadapter.xml을 만듭니다.
루트 요소 동기화 어댑터. 다시이 XML
파일에는 우리의 동기화 어댑터에 연결된 설정을 정의합니다.
포함하면 콘텐츠의 권위이다. 계정 유형 그것은 그
동기화. 여부는 그것이 사용자 보입니다. 그것은 여부
도로 컨텐츠 공급자를 변경하고 업로드를 지원합니다
동기화 어댑터와 상호 작용합니다. 병렬 동기화를 가능하게하고,
항상 동기화 가능.이러한 설정이 특정 위해 의미를 가진다
응용 프로그램, 그리고 난 당신이 다음 오는지 알고있을 것임에 틀림 없다. 당신이하고있는
맞아. 당신은 동기화 어댑터 서비스를 등록해야
패키지 관리자에서. 따라서 우리는 만들 필요가 있습니다
몇 가지 중요한 메타 데이터를 포함하여 많은 매니페스트 항목. 가장
중요한 것은 방금 만든 파일에 링크합니다. 모든
바로 지금 가까이 보유하고있다.작업을 시작하자
동기화 어댑터 자체에. 우리는 시작하자
더미 동기화 계정을 취득하기위한 헬퍼 함수
그것이 생성되어 있는지 확인하십시오. 그 후
우리는 우리의 동기화 어댑터에 다른 도우미 함수를 추가합니다
그것은 쉽게 우리의 동기화 어댑터를 테스트하도록합니다.


20 - SyncAdapter를 종료합니다
===========================

판권 여기에서 큰 하나 다.마감
SynchAdapter 그것은 날씨를 얻을 수
하여 데이터베이스에 저장합니다. 변경
ForecastFragment 내 updateWeather 함수
SyncAdapter와 동기화를 시작합니다. 여기에 몇 가지. 위에서 코드를 빼냅​​니다
우리의 SyncAdapter 의도를 취급한다. 핸들
의도는 우리의 선샤인 서비스의 안쪽에있다.좋은 소식은 그 추상적 나사이다
동기화 어댑터는 백그라운드 스레드를 제공
서버가 마찬가지로 위의 페치 실행
의도 서비스를 실시합니다. 또한 단순히 장소를 페치
우리의 유틸리티 클래스에서 쿼리. 결국 우리
어떤 일없이 이러한 동기화를 실행할
사용자의 참여. 마지막으로 만들기
우리는 업데이트 날씨를 호출 동기화 어댑터를 실행합니다.21 - SyncAdapter를 종료합니다
===========================

모든 권리는 완료되었습니다. 를 살펴 보자
솔루션. 우리는 로구타구을 추가하는 것부터 시작합니다
우리의 추상에 SyncAdapter 나사. 이런 것들 때문에,
백그라운드에서 실행되며 그것은 가지고 정말 편리합니다
일부 로깅. 우리는 결국 실행하고 싶기 때문에
검출되지 않는 모드 SyncAdapter.위치를 당겨 보자
우리의 유틸리티 클래스에서 쿼리. 그리고 우리
당사의 기존 일조 서비스에서 코드를 붙여 넣습니다.
우리는 어떤 것을 업 패치를 적용해야합니다. 우리는 니노 getContext를 호출해야합니다
예를 들어, 현재의 문맥을 취득. 내가 광고를 위로 복사 한 점에 유의하십시오
나는 주요 기능에 복사 된 같은 시간.그리고 마지막으로, 우리는 수정합니다
새로운 도우미를 사용하도록 날씨 업데이트
우리의 SyncAdapter 기능. 는 이것을 실행하자.


22 - 예약 된 동기화
==============================

그런데, 우리는 지금 동기화 어댑터를 사용하는, 그리고이 있습니다
예전처럼 대부분의 작업. 우리는이 응용 프로그램을 원하는
이 동기화는 교묘하게, 우리는 제거하고 싶습니다
그 이전 업데이트 메뉴 항목.모든 것을 정리하는 것부터 시작하자
다른 루틴은 우리가 동기화해야합니다. 그래서 우리는 확실히
FetchWeatherTask 같은이 다른 것 중 하나 또는 모두를 필요로하지 않는다
이런 것은 우리는 선샤인 서비스에서 한, 우리는 청소하고 싶다
이에 따라 매니페스트 업. 우리는 확실히 두 가지 중 하나를 필요로하지 않는다
이들은 더 이상.그리고 환경 설정에서 우리 만 변경할 수 있습니다
그것은 바로 동기화한다. 그래서 지금 우리가 정말 이것을 사용하는
어디서나 어댑터를 동기화. 우리는 그러나 문제가있다. 우리는 아니다
매우 똑똑하다는 것을. 사용자는 어떤 종류를 가지고
그들은 하늘의 목록을 참조하십시오 장소. 우리가하고 싶은
더 지능적으로 동기화한다. 안드로이드 2.2 프로즌 요구르트에서는 Android가 추가 된
정기적으로 동기화 어댑터의 동기화를 가지고있는 능력. 우리는 추가 할 수 있습니다
우리의 동기화 어댑터에서 이렇게 헬퍼 메소드.
문제는이 방법으로 스마트가 아닌,이다
우리가하고 싶은데, 아직 모든 것을 할 수는 없습니다
정확한 우리가 원하는 알람을 반복함으로써 그 멋진 일괄 처리
그것을 좋아합니다.다행히도 우리는 무언가를 추가했습니다
그, 그건 API 레벨 19까지 사용할 수 없습니다.
부정확 한 반복의 팔을위한 유연한 시간을 이용하여
우리의 선샤인 동기화 어댑터의 멋진 기본값을 설정하자.
먼저 이러한 상수를 추가합니다.상황이 조금 있도록하려면
우리의 코드에서 명확한 만, 다른 함수를 추가하자
새 계정을 만들 때 우리가 부르는 것을
그리고 여기에서 우리는 몇 가지 중요한 플래그를 설정합니다. 등
configurePeriodicSync 1 우리
방금 만든. 없이 SetSyncAutomatically,
우리의 정기적 인 동기화가 적용되지 않습니다.우리는하고 있기 때문에
그러나 그 후 즉시 동기화를하자에서 시작
우리는 전략적 위치에서 호출 할 수 있으며,
동기화 계정을 받았다. 마지막으로, 인터페이스를 만들 수 있습니다
세계에 조금 청소기 의한
initializeSyncAdapter 기능을 추가한다. 그냥 다 확인합니다
계정이 생성되는 것. 그리고 지금
의 onCreate의 주요 활동 안에 우리
그냥 새에 전화를 걸 수 있습니다
기능.그리고 확인하십시오 이여, 그 매개 변수에 대해
우리의 동기화 어댑터가 올바르게 구성되어있다. 수 있습니다
이것은 우리의 에뮬레이터에 영향을 미칠 수 있는지.
처음부터 선샤인의 새로운 버전은 현재 모두 보여줍니다
날씨입니다.동기화 및 동기화를 위해
정기적으로 성공하여 일어나는 어댑터
백그라운드에서 작업을 수행해야합니다 가지고
의 ContentProvider로 동기화 가능한 표시되며, 자동 동기화를 활성화하려면
SyncAdapter 위해 초기 즉시 할
동기화 또는 밀리 초 단위로 간격을 설정합니다.23 - 예약 된 동기화
==============================

당신은 확실히 콘텐츠 공급자로 동기화 할 수있는뿐만 아니라 표시되어 있어야합니다
동기화 어댑터의 자동 동기화를 활성화합니다.
당신은 즉시 예약 할 필요가 없습니다
우리가 그랬던 것처럼 그것은 사용자를위한 좋지만 동기화한다.그리고 이것은 경미
노트에는 밀리 초 단위로 간격을 설정하는 것이 아니라, 초 단위로 설정하지 마십시오.


24 - Google 클라우드 메시징
===========================

부정확 알람을 반복한다. 정확한 알람을 반복보다 무한히 우수한 있지만,
아직 먼 이상에서. 반복의 모든 종류의 문제점
알람은 아직 확인 폴링 서버입니다
업데이트를 위해.그래서 더 자주 당신은 신선한 폴링
당신이 볼 수있는 데이터가 더 높은 비용
배터리 수명. 당신은 배터리를 절약하기 위해 자주 당길 수 있지만,
그것은 당신의 콘텐츠가 길기 때문에 진부가되는 것을 의미합니다.
그냥 사용자가 업데이트 빈도 자체를 결정 할 수
하지만 당신은 마법을 잃는다. 유일한 있었을 경우
더 좋은 방법입니다.그런 일이 가능합니까? 그것은 예
입니다. Google 클라우드 메시징 서버가 귀하의 응용 프로그램에 통지 할 수 있습니다
다운로드 할 준비가 된 데이터가 있습니다 직접 때. 아니면
하지만 메시지 페이로드의 새로운 데이터를 포함 할 수
자체.Google 클라우드 메시징을 사용하여에서 메시지를 보낼 수 있습니다
당신의 앱을 통해 모든 설치된 인스턴스에 대한 당신의 서버
Google 클라우드. 그 결과, 폴링을 중지 할 수 있으며,
즉시 배터리 수명을 개선하고 또한 개선되어
안드로이드의 신선도. 대신, 당신의 서버에 의존
동기화 할 데이터가있을 때 클라이언트에게 통지한다.이러한 메시지는 캔
당신에게 통지함으로써 동기화 어댑터 트리거 단순 간질 한 것
응용 프로그램은 새로운 데이터 또는 다운로드 할 필요가있는 것을.
또는 메시지 페이로드에 새 데이터를 포함 할 수있다.
햇빛의 예에서는 누군가가 다른 사람의 서버를 사용하고있다.그러나
그 때라도, 그것은 자신의 중간을 만들어도 의미가
원본을 이끌어 설치된 응용 프로그램의 인스턴스를 통지 티아
그것은 변화 알았을 때. 이제 우리는 설치하지 않을
이 단원의 서버가 당신을 위해 전체 내용을 볼 수 있습니다
강사 인터넷에 연결되어 개발자 가이드에서 Google 클라우드 메시징을 사용합니다.25 - 통지
==================

이후 안드로이드의 가장 강력한 기능 중 하나
플랫폼의 시작이 제공하는 능력되는
사용자에게 적시에 통지. 우리는 간단한 추가거야
우리의 날씨 앱 1. 이 간단한 알림이 표시됩니다
예보 날씨 아이콘 예측 텍스트,
일의 고온 및 저온. 키 하나
우리가 지적하고 싶었던 것은 어떻게하지 않는 것입니다
우리의 통지에 스팸이다.우리의 응용 프로그램은 최대 표시됩니다
단일 통지. 이러한 경우, 정말 의미가 없습니다
통지는 어쨌든 더미. 그들은하는 데 충분한 정보가 표시되지 않는
컨텍스트를 제공합니다. 알림 중요한 것은 제공하는 것입니다
표준 방식으로 포맷 된 정보의 편리한 한입 때문에,
그것은 시스템의 나머지 부분과 조화를 이루고있는 것.우리는 요
우선하기 위해 문자열을 추가하는 것부터 시작
마지막으로, 우리는 사용자에게 통지를 보냈다. 로
자주 통지의 몸을위한 형식 문자열로.
우리의 동기화 어댑터의 내부에서 알림을 구현하여 봅시다.
우리의 통지는하고있는 무슨에 따라됩니다
데이터베이스. 그래서 우리는 프로젝션과 열의 인덱스를 만듭니다
날씨 ID의 우리의 동기화 어댑터의 값.설명,
그런 max와 온도​​, 데 함수를 추가하자
날씨를 알림. 우리는 몇 가지 추가를 추가합니다
여기서 상수 업. 밀리에서 하루에 One과
1 우리 같은 알림 ID를 사용하는 것처럼.
알림 ID를 다시 사용하는 우리의 응용 프로그램은 유일한 것을 의미합니다
최대 하나의 통지에 게시합니다. 그리고 마지막으로, 우리는 전화 할게
우리의 위 속에서 합리적인 장소에서이 함수는 실행하기
우리의 동기화 어댑터의 동기화 기능.내부의 날씨를 알려, 우리 'LL
여부를 확인하시기 바랍니다, 우리는 실제로 통지를 나타냈다
그 날. 우리는 가지고 있지 않다면 우리는 데이터베이스에 이야기합시다. 현재 현재 확인자 커서를 가져옵니다
하루 한 데이터를 가져 오는 그러나 한가지가 없습니다
하고 실제로 알림이 표시되어있다. 이제 모든 권리는 가까이되었다
끝. 기상 알림을 구현하고
통지 Compat.builder를 사용하여 우리의 통지를 구축
호환 V4에 의해 만들어진 보류 텐트를 가리킨다. TaskStackBuilder과
NotificationManager로 전송되었다. 팁 :
우리의 주요 활동에 대한 명시적인 의도가있다
여기에서 좋은 아이디어. 당신이 읽고 싶은 책에 문서가 많이 있습니다.


26 - 통지
==================

모든 권리는 완료되었습니다. 당시 새로운 것이 많이있었습니다. 그러나 역시,
당신은 지금은 베테랑 Android 프로그래머 해지고있다.내가 전에 말했듯이 우리는 사용하는거야 NotificationCompat.Builder
우리의 통지를 구축한다. 이것은 구축하는 것은 간단합니다
우리의 아이콘이 표시되는 모양 통지
일기 예보, 우리를 위해 제목을 나타내는
응용 프로그램. 그리고 우리의 컨텐츠 텍스트와 예측
가겠. 우리는 다른 클래스를 사용하는거야
지원 라이브러리에서 작업 스택 빌더를 만들
우리의 보류 의도 때문에.이것은 단순한 사건이다
작업 스택 빌더는 우리가 가지고있는 모든이기 때문에
우리의 스택의 단일 항목. 우리는 다만 추가
다음의 의도와 보류 의도를 구축하기 위해 그것을 사용
우리는 통지 관리자에 합격한다. 마지막으로 호출
우리의 빌더에서 작성된 의도 통지 관리자,
알림 기능을 가진다.알림 관리자의 좋은 점 중 하나는
그것은 UI를 표시하고 있음에도 불구하고, 모든 스레드에서 사용 할 수있다. 27 - 통지의 파워
===============================

백그라운드에서 앱 업데이트가 누구 경우
찾아 그것을 열고 정말 어떻게합니까? 통지
사용자에게 통지하기위한 편리한 방법으로 시작
배경 업데이트.그러나 그들은 강력한 표준화 된 단축키로 성장 해왔다
경량 방법으로 응용 프로그램에서 직접 대화한다.
젤리 이후에서는 알림을 확대 할 수 이었음
그들은 크고 더 많은 정보를 포함한다. 그것은 또한 도입
조치를 포함 할 수 풍부한 알림 개념,
이와 같이 데이터에 대해 수행되는
통지에 포함되어 있습니다.이것은 상호 작용을 가속화하고
사용자가 자신의 알림 심사 경험을 합리화하는 데 도움이됩니다. 로
에서 적시에 정보를 전달하기 위해 특별히 설계된 표준화 된 UI
제한된 화면 공간. 통지는 분명 메커니즘이었다
Android 비둘기 착용에 확장 할 때 사용
안드로이드 소프트웨어. 갑자기 당신은 설계된 것이 풍부 통지
휴대폰과 태블릿 용 앱이 착용 호환성을 갖게하는,
자유를 위해.그러나 그것을 과장하지 말라, 사이에 미세한 차이가 있습니다
편리와 스팸. 그리고위한 클릭 유일한 커플이다
사용자가 앱의 알림을 비활성화하기
영구적으로. 그래서 명령을 체크 아웃
그것은 좋은 알림을 만들 때 디자인 가이드에 대한 링크는 아래와 같습니다.


28 - 날씨 알림 OnOff의 터닝
========================================

괜찮아. 우리는 다만 애플 리케이션에 몇 가지 세부 사항을 추가 할 생각이다.우리는 날씨 알림을 구현하는거야
맛. 우리는 추가하여 이것을 할 것이다
알림을 해제하는 응용 프로그램의 설정에 새로운 설정. 그리고 사용
알림을 해제하는 것을 좋아한다.
팁 당신이 CheckBoxPreference을 사용하는거야


29 - 날씨 알림 OnOff의 터닝
========================================

자, 당신은 완료입니다. 모두를 추가하는 것부터 시작하자
문자열은 우리가 새로운 환경을 위해 필요할 것이다.키 레이블 진정한 가짜 및 기본 같은 것.
그럼 우리는 현의 일반 XNL에 추가 특혜, 체크합니다
우리는 단지 정의 된 이러한 문자열을 사용하여 상자의 맛.
우리의 동기화 어댑터에 오버 갑시다. 통지는
기능, 우리는 특혜를 얻기 위해 코드를 추가
그리고 그것을 이용한다. 그리고 거기에 우리는 그것을 가지고있다.사용자가 우리를 원치 않는 경우, 이제 우리는 알림이 표시되지 않습니다
실행중인 응용 프로그램을위한 훌륭한 곳이다,라고.


30 - 구 기상 데이터 삭제
============================

당신은 발견 할 수 모릅니다 것들 중 하나는 우리의 응용 프로그램 데이터베이스가 계속되고있는 것이다
결국 장치를 채우고 영원히 성장한다. 이것이 좋은 방법입니다
응용 프로그램을 제거를 낸다.그럼이 문제를 해결합시다. 그 기상 데이터를 삭제하는 코드를 추가합니다.
여러 날 연령이다. 데이터 연산을 수행하는 캘린더 기능을 사용하십시오.


31 - 구 기상 데이터 삭제 - 솔루션
=======================================

모든 권리는 완료되었습니다. 그러면 솔루션을 살펴 봅시다.만약 당신
우리는 동기화 어댑터를 햇빛이 코드를 추가하려고 했어요 것을 추측,
당신은 바로 북쪽 것이다. 우리는 실제로 코드를 오른쪽에 배치하는거야
우리는 성공 삽입 짓을 알고있는 것은 여기에서이다.
그래서 우리는 무엇을합니까? 그래서 우리는 시작
당일 일정 개체. 그럼 우리는 부의 1을 추가
그것을 의미 한 날은 어제를 가리킨다. 마지막으로 변환
데이터베이스가 사용하기 쉬운 문자열에 그.그리고 우리는 쿼리를 실행
그날 다음을 모두 삭제합니다.
완료. 그것은 자신의 뒤처리하기 위해 항상 좋은 것이다.


32 - 업데이트지도 텐트
======================

당신 디테일 지향의 사람들 모두가 아마 눈치
우리는 실제로 우리가 얻는 좌표를 사용한 적이없는
위치를위한 서버에서 위의 대신 의지
지도 API 날씨 API 모두
위치 쿼리와 같은 일을한다.불행히도,
그들은 항상 일치하지 않는다. 좌표를 사용하여 맵을 구현
위치 테이블에 저장된다. 당신이 시작하고 싶다
WeatherFragment에 MainActivity에서 메뉴 코드를 이동시킴으로써.


33 - 업데이트지도 텐트 - 솔루션
=================================

괜찮아. 그리고 여기 솔루션입니다. 오프 시작하려면 해 봅시다
우리의 예측 조각의 쿼리를보세요.그것은 그래서 참여
우리가 추가 할 수있는 두 테이블간에 정말 간단합니다
우리의 쿼리에 추가 파라미터. 지금, 우리는 지속적으로 확인하십시오
열은 일관성 지수. 이제 우리는 위도를 잡고 왔고,
경도 동시에 우리는 날씨 항목을 잡았다. 그 다음 함수를 이동하는 것입니다
조각을 예측하는 데지도의 바람직한 위치를 연다.대신
이 값을 얻기 위해 공유 환경 설정을 사용하여 실제로 캔
예측 어댑터에서 커서를 가져옵니다. 우리는 얻을 수 있습니다
우리의 커서가 합리적인 위치로 이동 한 다음 빌드
그냥 위도 콜론 경도 인 우리의 새로운 문자열. 우리는 요
그것이 있었다 우리의 코멘트를 남겨주세요. 마지막으로, 우리는있다
코드에서 몇 가지를 수정하면
그래서 끝.글쎄, 적어도 코드. 아직 우리
XML에서 몇 가지 작업을 수행해야합니다. 그러면이 R.ID.action을 이동하자
지도 지금에 그 안에 조각을 예측하는
옵션 항목은 선택했다. 그리고 지금 우리는 몇 가지를하는거야
XML 일. 우리의 메인 메뉴를 살펴 보자. 우리는 다만 해요
이 작업 맵 항목을 떠나​​고 우리는 그것을 오른쪽에 배치합니다
예측 조각에. 괜찮아. 할 또 다른
우리가 여기있는 동안.Raito는 이야기의 하나였습니다
재생 메뉴 항목을 제거하고 싶다. 그래서,
그냥 주석 처리하자. 우리는 그 액션의 업데이트를 제거하면
항목은 우리는 아마 우리의 소스에서 그것을 주석해야
코드 너무. 당신이하고 싶을 때 결국 당신이 알고하지 않습니다
디버깅을 위해 그것을 사용하고 있습니다.그래서 거기에 우리는 그것을 가지고있다. 우리의
마지막 응용 프로그램. 더 이상 업데이트 버튼을 가지지 않는다. 과 동시에
해제하여 날씨 통지를위한 새롭고 흥미로운 설정.
자세한 내용은 담당하고있다. 난 당신이 건물을 즐기고 있었다 바랍니다
선샤인. 사건의 대부분이 아직있는 것은 동안 미뤘던
선샤인.예를 들어, 우리는 또한 더 지능형 많이 추가 할 수 있습니다
사용자 인터페이스 물건. 물론 우리
데이터 싱크가 약 그것은 많은 영리 만들 수 있습니다. 그리고 나는 당신이 선샤인를 구축 배운 사례를 바랍니다
당신의 미래의 응용 프로그램의 모든 도와드립니다


34 - 6 단원 요약
===================

축하합니다.이제 빌드하는 방법을 알고있다
효율적으로 포 그라운드에서 아름답게 실행 된 응용
백그라운드에서. 이 단원에서는 방법을 배웠습니다
서비스 및 사고 어댑터를 사용뿐만 아니라 위해
제공하는 모든 방법은 풍부한 통지를 작성
당신의 앱이 표시되어 있지 않아도 나은 사용자 경험.
로 최종 이야기의 시간을 위해 지금 가입
나는 Android를위한 가능한 미래에 당신을 가지고 간다.35 - 안드로이드 Storytime 미래
================================

나는 나의 첫번째 모뎀 호환 1200 보 ACE를 받았을 때 나는 12 세였습니다. 내가
시작 온라인이 아닌 인터넷 온라인 검색 로컬
의 BBS. 같은시​​기에 부유 지원했다
첫째로 제 1 벽돌 크기의 휴대폰
GSM 네트워크 배포 시작. 미만 이송
안드로이드 의한 년 미만.그리고 거의 밤새
우리는 세계의 정보를 기대하게되었다
우리의 손바닥. 첫 번째 후 불과 6 년
Android 휴대 전화를 시작하고 그것은 전화의 모든 것에 전력을 공급하다
정제, 시계, TV, 자동차. 그래서 우리는 어디로 가야합니까
다음? 가장 확실한 대답은 같은 일을 가능하게하고
다음의 5 억 컴퓨팅 플랫폼을 연결하는 휴대용 클라우드
사람.하드웨어는 더, 더 싸게, 더 강력 해짐에 따라
세계 인구는 인터넷에 연결된 컴퓨터를 얻을 수 있습니다.
그리고 스마트 폰은 만들 것이다 위하여려고하고있다
그것을 가능. 이를 용이하게하기 위해, 우리는 새로운 접근을보고있다
온라인 얻기에도 네트워크 공백 또는 메쉬
Google의 프로젝트 룬.우리는 잘하면 곧 유비쿼터스 세계적인 인터넷이 나타납니다
연결이 현실이된다. 동시에 스마트 폰
사라져 시작합니다. 같은 방법으로
우리는 그들이 예전 컴퓨터로 컴퓨터가 아니라고 생각
우리의 식기 세척기, 차 또는 TV의 일부가 우리는 중지됩니다
그들은 우리 속에 사라 졌을 때와 같은 휴대 전화의 생각을
시계와 [UNKNOWN].우리는 무엇을 기대하고 오기
무선 인터넷을 통합해서 개선 할 수있는
연결은 단순히 1을 가지게됩니다. 그것이 일어나기 위하여는, 우리는 필요로한다
더 컴퓨터와의 상호 작용을보다 창조적 인 방법을 찾기 위해
마우스, 키보드, 터치 스크린을 사용합니다.나는 모든 준비를 선택할 수 있습니다
내 휴대 전화 또는 자신의 손목을 들어 올려 Google에 대처하고,
검색을 실행 텍스트와 이메일을 보내고 알람을 설정하거나 메모
화면과 키보드를 건드리지 않고. 스크린
그 자체는 픽셀 밀도가 없도록 선명하게되어있다
인간의 눈으로 인식 할 수있다. 그리고 팀
구글 X는 혈액을 측정 할 수있는 콘택트 렌즈를 구축하고있다
혈당.감각이라면 내가 할 수있을뿐만 아니라,
그것을 두 어서 자신의 휴대 전화를 제어하는​​ 하나 얼굴 또는
엎드려 비슷한 센서의 배터리가있다
[UNKNOWN] 클래스의 군함에. 노출계 온도 변화, 기압계,
자이로 스코프에 사용할 수있는 이러한 모든
텍스트 입력을 교체하거나 프로세스를 자동화한다. 착용, 자동차,
와 온도 센서의 더 많은 가능성을 소개한다.클라우드에 모든 것을 연결하고
가능성은 무한합니다. 안드로이드의 미래는 없습니다
더 강력한 전화 운영 체제. 그것은이다
눈에 보이지 않는 유비쿼터스 구름 뒤에 뇌는 컴퓨팅을 연결합니다. 이렇게
우리는 멋진 애플 리케이션을 구축하기 위해 오늘 배우는 기술
우리는 내일 사용합니다 같은 기술이있다
우리 주위의 모든 것을 제어한다. 우리는 촬영 한
그 미래의 첫 걸음.난 당신이 다음에 무엇을보기 위하여 기다릴 수 없다.


36 - 축하 안드로이드 파티
==================================

[SOUND].
>> LAUGH]
>> 컨텐츠 제공자.
>> 축하, 모두 당신 선샤인 응용 프로그램을 구축 완료 한 곳입니다.
>>하지만 더 햇빛의 여지는 항상있다.
>> 있고, 댄하지만 지금은 시간이다
학생을위한 그들의 최종 프로젝트를 빌드 간다.>> 그리고 당신은 자원을 많이 얻을 수 있습니다
Android 개발자 사이트에서 정말 놀라운 모바일 애플 리케이션을 구축해야합니다.
>> 미국과 Udacity에서 더 많은 것을 기대하세요.
>> 지금, 나는 생각
일부 케이크 축하하는 시간.
>> Woohoo.
>> 레몬 타르트.
[음악]