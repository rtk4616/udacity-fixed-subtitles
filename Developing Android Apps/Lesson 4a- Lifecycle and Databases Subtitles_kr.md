01 - 4 단원 소개
=============================

 목표는 당신의 앱이 원활한 효율적인 환경을 제공하고 보장하는 것이다
네트워크가 느리거나 사용할 수없는 경우에도 사용자





02 - 우리는 활동의 라이프 사이클이 필요한 이유
======================================

예.
댄은 데이터베이스와의 도취되기 전에 그럼보고하자
당신은 활동 사이를 전환하려는 의도를 사용할 때 어떤 일이 일어난다.선샤인 속에서
당신이 주요 활동 목록을 탭하면 그것은 세부 활동을 엽니 다.
그러나 주요 활동은 backstack에 남아 있습니다.
즉시 반격 같이 다시 표시 할 준비가되었습니다.
지금이 예제에서는 두 활동은 같은 앱에서이다.
우리는 3 장에서 배운 것처럼. 하지만 당신은 또한 브라우저를 감상 할 수 있습니다
햇빛에서의지도 응용 프로그램.또는 그 문제에 대해 사용자가 홈을 이길 수 있습니다.
그리고 거기에서 응용 프로그램을 실행 또는 그들이 최근의 키를 사용할 수 있습니까?
통지를 사용하여 다른 응용 프로그램으로 전환합니다.
이 옵션은 모든 당신의 허리 스택 앱의 많은 끝나는 것을 의미합니다.
그런데, 장치의 우리의 자원이 매우 제한되어 있음에 유의하십시오.그래서 백그라운드에서 유휴 앱 수십을 가지고있는 것은 좋은 생각이 아닙니다.
Android는 우리를 위해이 문제를 해결하고
그래서 그 지독한 작업 킬러 응용 프로그램을 사용할 필요가 없습니다.
그래서, 그것을 어떻게해야합니까?
글쎄, 당신이 잠시 사용하지 않지만, 우선 순위가 낮은 애플리케이션을 죽인다.우리는 그것이 죽을 필요가있는 앱을 산출하는 방법을 정확하게 더 갈거야,
레슨 6.
하지만 지금은 당신의 애플 리케이션이되지 않은 것을 인식하는 것이 중요합니다
자신의 운명을 통제한다.
이것은 언제든지 죽을 수있다. 그래서 그것을 해결하는 방법을 알고 있어야합니다.그리고 활동의 라이프 사이클과 신호 우리를 이해하는 것을 의미
평생 동안 진행 상황을 보여주기 위해 프레임 워크에서 가져옵니다.





03 - Android 활동의 라이프 사이클
===================================

직접 응용 프로그램을 종료 함 플랫폼을 위해 가열찬 출발합니다
바탕 화면 WinForms 개발에 자신의 치아를 잘라 나 같은 사람.당신이 같은 배경에서 오는 경우는 아마있다
라이프 사이클 이벤트 핸들의 관점에서 무엇을 기대하는 것은 아주 좋은 아이디어.
당신은 당신의 UI를 구축하고 그물까지 어디 콜백의 OnCreate에서 시작된다.
설정이 완료 당신의 활동이 작성되었습니다. 그것은 이렇게 놀람이 없습니다
당신 활동이 표시 될 때를위한 이벤트 핸들러도 있습니다 것을.그것이 포커스를 취득하여 활성화 될 때를 위해 ONSTART와 다른 어느
onResume에서 전경 애플 리케이션. 그 같은 순서가 다음 반대로 일어난다.
[SOUND]는 onPause는 이어 활동이 포커스를 잃은 것을 보여
를 OnStop 응용 프로그램은 더 이상 표시됩니다. 마지막으로, onDestroy 메소드가 있습니다,
응용 프로그램 라이프 사이클의 종료를 나타낸다. 안드로이드를 처음 시작하면 당신은 요
바로 이러한 상태 사이를 이동합니다.작성 시작, 다시 시작 잇달아
[BLANK_AUDIO]
그러나 전체 응용 프로그램의 유효 기간내에서의 onCreate가 처음 불려 갔을 때부터
응용 프로그램은 결국 종료 될 때까지. 이것은 활성 평생 가서
물리적 수명, 여러 번. 그럼 좀 더 상세하게 그들을보고하자.



04 - 활성 및 가시 존속 기간
=================================

액티브 라이프 사이클은 활동이 포 그라운드에있을 때
포커스를 가지고있다. 여기에서는 적극적으로 사용자 이벤트에서 입력을 수신하는 경우
다른 활동은 그것을 애매하게되어 있지 않습니다. [UNKNOWN]을 켜
활성 수명은 곧 당신의 활동이 부분적으로 숨겨진대로 종료
이 예제처럼.[SOUND] 권한의 대화 여기서 볼 수 있습니다
Google Play 눈앞에 표시되는
저장소에있는 응용 프로그램. 당신이하려고 다른 활동을 가지고 있거나 같은 일이 일어납니다
암시 적 의도를 완수 해, 사용자가 선택을 할 필요가있다. 이렇게
한정된 자원을 효율적으로 활용하기 위해,
당신은 응용 프로그램의 리소스 부담을 조정하기 위해 이러한 신호를 사용하게 될 것입니다.그래서 UI를 통해 가장 업데이트 일시 중지 할 수 때이 수명이 완료되면
이것은 onPause가 발표되고있다. 보시다시피 그러나 응용 프로그램은 이렇게, 아직 표시되어있는
당신은 당신의 UI를 렌더링되는 프로세스를 일시 중지해야하는 것이 아닙니다. 보이는
응용 프로그램은 전혀 나타나지 때 언제든지 반면 수명은 계속하고
곧 그것은 완전히 다른 응용 프로그램에서 숨겨진이다로 종료합니다. 이런.[SOUND]는이 시점에서 우리의 응용 프로그램은 백그라운드로 이동됩니다.
당신이 정지에 나오면 당신은 사용자가 모든 애플 리케이션을 볼 수 없습니다 알고있다. 그래서 잠시
OnCreate 이벤트 및 OnDestroy는 최대 1 회 당신의 앱이 실행될 때마다 호출됩니다,
응용 프로그램을 실행하는 동안이 핸들러는 여러번 호출 될 수있다.
상황이 조금 다르다 가져올 위치 지금이.대부분의 플랫폼에서는
응용 프로그램 라이프 사이클은 확정적이다. 일반적으로 당신이 프로그램을 시작하고,
그것이 완료 중 하나 또는 사용자가 그것을 취소하는 데는 달리기를 두자. 당신이보고
당신의 앱이 당신의까지 계속 실행 의미 전통적인 데스크톱 개발
사용자는 파일 메뉴에서 종료 또는 종료를 선택합니다.그 시점에서, 당신이 숙박을 말할 수 있으며,
여유 자원. 우리는 Android의 라이프 사이클에 알다시피하지만 조금 다릅니다.
그러면 그것이 작동하도록합니다 정확히 어떻게 자세히 살펴 보자.





05 - 라이프 사이클 이벤트
=====================

그래서 지금은 onPause로 이동 추가 로깅 문장을 간다, onresume,를 OnStop,
ONSTART 및 주요 활동에 대한 OnCreate와 ondestroy 수명주기 핸들러.앱을 실행하고 휴대 전화를 회전시켜보십시오. 지금 로그를 관찰한다.
뭐죠 당신의 활동을 통해 이러한 라이프 사이클 이벤트의 시퀀스
단순히 그 방향을 바꿀 수있다.





06 - 라이프 사이클 이벤트 솔루션
==============================

눈물 다운을 시작으로 응용 프로그램은 먼저 일시 정지 정지, 파괴,
그 후, 다시 작성, 다시 시작하고 재개했다.



07 - 활동 종료
=========================

우리가 파악할 수있는 경우 응용 프로그램이 종료 할 때 무슨 일이 일어나는가 살펴 보자
배경. 홈 키를 치고 다시 응용 프로그램을 시작합니다. 현재 몇 가지 다른 시작
우리의 것으로 돌아 오기 전에 응용 프로그램. 시도 큰 메모리 풋 프린트 응용 프로그램을 선택한다.당신이 마지막으로 다음의 라이프 사이클 이벤트 핸들러 어떤 알아낼 수 있습니다
안드로이드는 아마 런타임에 의해 종료 전에 1는라는 보장?





08 - 활동 정지 액
==================================

벌집 때문에 Android 앱은 앱 전에 정지가 불려 가고있는 데다 의지 할 수있는
종료되는 위험이있다.하지만 당신은 이전 허니컴 장치를 지원하는 경우
당신이 이미 후 위의 일시 정지, 종료 준비를해야합니다.
[BLANK_AUDIO]
예를 들어, 당신이 너무 빨리 앱 죽음의 준비를해야하는지 자세히 살펴 보겠습니다.





종료를위한 준비 방법 - 09
===================================

당신은 응용 프로그램 사이를 돌아 다니고대로 당신은 아마도 사용자의 것을 발견
관점은 Android 애플 리케이션 상태의 변화를 발표하지 않습니다.그것은 공표하지
그것은 메모리에 낮은가 리소스를 해제 할 응용 프로그램을 닫도록 사용자에게 요청한다. 로
사실 그것은 장치에 리소스 제한을 위해 그것이있는 모두를 실시해,
사용자는 보이지 않는다. 즉, 원활하게 실행 전경 응용 프로그램을 유지하는 것을 의미하고,
와 원활한 응용 프로그램 전환, 그것이중인 애플 리케이션을 죽일 것을 의미
배경.그리고 만약을 수행합니다
전경 응용 프로그램을 계속 실행 할 수 있는지 확인하기 위해 그들의 자원을 필요로합니다.
그래서 우리는 가능한 한 빨리 귀하의 응용 프로그램이 표시되지 않은로서 그 수명 보이는 것을 알고있다
레드 결혼식 스탁 것과 위험한. 예고없이 죽을 가능성이 높다,
그러나 사자에게서 복귀 할 준비가.그것은 우리에게 몇 가지 매우 중요한 것을 알려줍니다
우리의 응용 프로그램은 선량한 시민임을 행동과 뛰어난 사용자를 제공해야합니다 방법
경험. 시스템의 관점에서, 일시 정지 및 정지에 대한 우리의 신호이며,
응용 프로그램은 우수 살해 될 수 있습니다.그래서 우리는 모든 자원을 정리해야합니다
모든 열려있는 연결이나 소켓 닫기 등의 다운 질서 눈물을 필요로하고 있습니다.





10 - OnPauseOnStop에 무엇을 해야할지
================================

또한 시스템은 지금 경보 우선 믿고 수 있도록 신호입니다. 주어진
한정된 자원, 우리는 시스템의 우리의 사용을 줄임으로써 응답해야합니다
자원.특히 배터리의 소모를 계속할 수있는 것.
즉, UI를 업데이트하는 데에만 사용되는 것이 포함되어 있습니다. 그래서 무엇
일시 정지하거나 절단 할 필요가있는 청취자와 업데이트의 몇 가지 예를 보여줍니다.
때는 onPause 또는를 OnStop 받고 있습니까? 아래의 텍스트 상자에 답변을 넣어주세요.




11 - OnPauseOnStop 솔루션에 무엇을 해야할지
=========================================

답변 좋은 예로는
센서 청취자 위치 정보의 갱신 동적 방송 수신기. 또는
게임의 물리 엔진. 응용 프로그램이 일어나고 유지해야하는 작업
당신의 활동이 일시 중지 된 경우에도. 정말 활동에서 일어나야하지 않습니다
모두. 우리는 6 단원에서 그 문제에 어떤 해결책을보고있는 것입니다.당신이 때 활동이 일시 정지하고있는 점에 유의하십시오,
그것은 아직 눈에 보입니다. 그것은 단지 다른 것이 일반적인 대화 상자에 의하여 숨겨 것이다.
하지만 중지하지 않습니다. 그래서 당신은 일시 정지받은 때 당신의 UI를 그리기 멈추지 않는다





12 - 활동의 라이프 사이클 요약
=============================

선샤인 응용 프로그램의 목적을 위해이 정보는 순수하게 이론적이다.사실, 당신이 정말로 유일한 나중에 이것을 고려해야합니다
당신은 센서와 LocationListeners의 종류를 추가하는 때. 그때까지,
기본 구성 요소는이 동작을 많이 처리합니다
당신. 어쨌든도 이제 라이프 사이클을 이해하고 있는지,
방법은 시스템 리소스를 필요로 할 때 당신의 응용 프로그램을 종료합니다.Android 응용 프로그램 종료 또는 버튼을 종료되지만 서비스를 제공하는 왜 잘하면 이해하고 있어야합니다
실용적인 목적은 없습니다. 대부분의 시간에, 당신은 활동 마무리를 호출 할 수 있으며,
그것은 즉시 철거 버립니다. 즉, 실제로 정확히 언제 무엇이 일어나는가?
당신이 다시 그들의 활동 중에서 간단한 히트를 사용하고 있습니다.당신은 여전히​​ 납득하지 않은 분은 강사 노트에서 동영상을 확인하십시오.
나는 조금 색과 나의 추론을 설명하고 어디에.





13 - 상태 유지
======================

응용 프로그램 개발자로서, 그것은 한 번 시작 착각을 유지하기 위해 우리의 일입니다,
모든 앱이 찾고 그라운드에서 참을성있게 기다리는
위라는 스타에 그 기회.그래서 언제든지 사용자로 전환
당신의 응용 프로그램이 시스템은 그동안 kilted되어 있는지 아닌지,
그들은 떠날 때 그들이 가지고 동일한 UI가 나타날 것입니다. 지원하기 위해,
Android 특히 이러한 상태를 지속하는 한 쌍의 핸들을 가지고있다
상황. 인스턴스 데이터를 저장하려면 일시 정지 직전에 호출됩니다.이렇게
즉시 당신의 응용 프로그램이 켜져 더 이상 활성이다
만든 직후에 호출 된 인스턴스 데이터를 복원하지만,
응용 프로그램은 시스템에 의해 종료 된 후 다시 시작하는 경우에 한합니다.
지난번 당신을 구한 당신이 상태 정보의 무리를 읽을 수 있다는 것을 의미
응용 프로그램은 여기에 포 그라운드로했습니다.다음에
그것은 시스템에 살해당한 경우에도 귀하의 응용 프로그램에 스위치를 사용합니다
평균 시간. 그 번들을 사용하여 동일한 상태로 그것을 당신의 UI를 반환 할 수 있습니다
사용자가 그것을 본 마지막 시간은 그 피부의 원활한 전환을 만든
덮개 아래에 일어나고 자원 관리. 그래서 충분하다,
그럼 댄 다시 실천이 이론을 배치하는 방법을 살펴 보자.




14 - 응용 프로그램 상태를 저장하는 번들
==============================

당신은 라이프 사이클이 정말 중요하고 생각 할 수도있다.
그러나이 섹션에서는 데이터를 유지하고 회복에 있습니다. 날 믿어,
난 그냥 우리가 다시 코딩 싶어. 그러나이 것은 밀접하게 연결되어
당신이 모두를 이해하지 않으면 그들은 오해는 간단하다.Reito 언급했듯이,
Android는 번들 응용 프로그램의 상태를 저장합니다. 당신이 가지고 있을지도 모른다
그냥이 번들의 모든 종류의 정보를 저장하고 싶다는 생각과
지속성의 다른 형태에 대해 걱정할 필요가 없습니다. 그러나 문제는,
이 번들은 즉시 사용자가 뒤로 키를 치는 것을 떠나
당신의 주요 활동. 그것은 그들이 이렇게하는 것은 정말 중요합니다.사용자는 이전 키로 기대를 당신의 활동을 청산하는 것을 선택한 경우
활동이 표시되는 다음 시간은 기본 상태입니다. Home 키 또는 응용 프로그램 전환기를 사용하는 경우, 사용자의 배경 당신의 iPad,
활동이 작성된 다음, 그것은 현재 상태에서 재개 할 필요가있다.




15 - 좋은 안드로이드 시티즌
=========================

우리는 코드에 뛰어 들기 전에 내가 언급하고 싶었던 다른 하나는 그것이 있다는 것입니다
좋은 Android 시민 인 것이 중요하다. 이것은 원칙을 준수 수단
네트워크 활동을 최소화하고 사이를 완벽하게 통합 응용 프로그램을 가지고
오프라인과 온라인 상태입니다. 우리는 캐시를 작성하여 그것을 실현하는거야
선샤인 다양한 활동간에 공유되는 데이터 모델.



16 - Android에서 데이터 저장
============================

우리는 세션 자료에 뛰어 들기 전에, 저장 또는 대해 조금 이야기하자
Android의 데이터를 유지한다. 우선 왜 우리는 물건을 유지하기 위해 일부러 할거야
전혀? 이것은 연결되는 클라우드의 시대입니다.왜 우리는 항상에서 인출하지 마십시오
거기? 그것은 응용 프로그램을 실행하고 표시되지 않습니다처럼 정말 기쁩니다로드 또는 더 나쁜
이러한 빈 화면. 빠른 사람이 응용 프로그램을 사용할 수 있으며, 더 그것은 다음과 같습니다
사용. 물론, 1은 뭔가를 표시하기 위해 취득하려면 새로 고침을 선택해야하는 경우
그것은 특히 나쁜 것이다.우리의 데이터를 유지하는 또 다른 이유는
모든 무선을 사용하면 장치의 배터리 수명에 해로운 것으로,
특히 셀룰러 무선. 많은 사용자는 변수의 데이터 플랜에 포함되어 있지 않거나
그들은 당신의 응용 프로그램을 사용하려는 경우 로밍 할 수도있다. 이러한 모든 불필요한 데이터
페치를 추가 할 수 있습니다. 네트워크를 가지고 있지 않은 많은 장소가 남아 있습니다
사용 가능한 연결.모바일 응용 프로그램을 갖는 주요 장점 중 하나입니다
불량 또는 존재하지 않는 네트워크 상태에 저항성이다. 결국
사용자가 앱을 사용하고 싶을 것입니다 어디에 당신이 알고있는 것은 아닙니다. 당신이 예상 할지도 모르지만,
Android는 파일 시스템에서 영구 데이터를 저장합니다.
이 파일은 당신의 응용 프로그램의 개인 내부 저장 장치에 저장할 수있다.그들은 또한 공유 또는 외부 저장 장치에 저장할 수있다. 오래된 온
Android 장치는이 공유 스토리지는 외부 메모리 카드에 실제로 있었다.
이 같이 오늘날 대부분의 Android 장치는이 카드를 에뮬레이트
공유 외부 스토리지 응용 프로그램은 장치에서 사용할 수 있어야합니다. 일부 안드로이드
장치는 공유 스토리지 및 보조 저장 장치를 에뮬레이트하고있다.
안드로이드 4.4 킷캣은 개발자가 보조에 액세스 할 수 있도록하기위한 API를 추가했습니다
외부 기억 장치. 우리는이 클래스의 내부 스토리지에 집중할 생각이다.
Android의 위치에 대한 자세한 내용은 강사 정보를 확인하십시오.
내가 전에 언급했듯이, Android는 파일 시스템에 데이터를 유지합니다.
이것은 형태의 파일 시스템에 2 개의 기능 계층을 제공하지
공유 취향과 SQLite의.공유 Preferences 클래스는 일반적인를 제공하고 있습니다
당신이 저장하고 영구 키와 값의 쌍을 얻을 수 있습니다 프레임 워크
그런 부울, 부동 소수점, 정수, long과 같은 기본 데이터 형식,
문자열. 공유 설정을 저장하기 위해 Android 좋아하는 활동에 사용됩니다
그런 위치로 설정 데이터. 왜 SQLite 데이터베이스에서 물건을 저장할?
결국, Android는 RAW 파일 공유 환경을 모두 지원합니다.위해
당신을 던질 경우, 그것은 일을 찾는 것은 비효율적이라는 것과 이유
바닥에 말뚝에서 옷. SQLite 데이터베이스에서 물건을 저장할 수 있습니다
당신은 쉽게 테이블의 인덱싱의 파워 덕분에 데이터를 정리하고 찾을 수 있습니다.
SQLite 데이터베이스는 우리의 기상 데이터베이스에서이 조각 수 있습니다.
않은 모든 필드가 표시되어 있는지에주의하십시오.우리는 사용하여 쿼리를 실행할 수 있습니다
그런 여기에서 SELECT 문 반환으로이 데이터베이스에 대해 SQL,
우리가하고 싶은 것이다 것과 비슷 지정한 날, 날씨,
자세히보기. 우리는 범위를 반환하는 데 조금 복잡한 쿼리를 사용할 수 있습니다
우리는 주로 예측 ListView에 무엇을 해야할지에 비슷한 날짜.





17 - SQLite 데이터베이스
=====================

예. 여기에서 조금 복잡한 SQL 쿼리입니다.위한 강사 노트를 참조하십시오
당신은 SQL 문을 분석하는 데 사용할 수있는 몇 가지 리소스. One 노트
맥스는 하루에 고온을 저장하는 열의 이름입니다.





18 - SQLite 데이터베이스 - 솔루션
================================

이것은 실제 최대 고온을 포함한 단일 행을 반환합니다.
우리는 최대의 놓인이 열의 내림차순를 사용하는
쿼리를 시작할 때의 값. 리미트 문장이에 SQLite를 알려줍니다
유일한 단일 행을 반환한다.우리는 최대 값을 가진 행을 반환한다.
우리는 최신 하이 원한다면, 우리는 최대 DESC 날짜 DESC하여 주문할 수 있습니다.





19 - 안드로이드에서 데이터 저장에 대한 자세한
====================================

SQLI을 사용하면 제거 할 쉽게, 업데이트 및 고도로 사용하여 행을 삽입
표정이 풍부한 쿼리. 하나도 당신 개정 데이터베이스로 새 열을 추가 할 수 있습니다.그냥 인기있는 애플 리케이션 정도로 SQLI의 일부를 이용한 놀랄 일이 아닙니다
안드로이드. 그것은 Android 솔루션의 매우 인기와 중요한 구성 요소입니다.
Android는 또한 작업을위한 도우미 함수의 거대한 세트를 제공합니다
쿼리 작성을 자동화하는 기능을 포함 쉽게 데이터베이스.
표시 목록보기 쿼리에 의해 채워, 심지어 문장을 컴파일하고있다.위해
Android에서 데이터베이스에 대한 자세한 내용은 강사 노드를 참조하십시오. 한마디
제가 언급하고 싶은 우리는 당신에게 어떻게 기초를 가르친다는 것입니다
Android에서 콘텐츠 제공자에 데이터베이스를 구축.아이디어는 당신에 한 번하는 것입니다
이 클래스로 진행되며 당신은 어떻게 그것을 모든 작품을 잘 이해하고있는 것입니다
당신의 데이터베이스 구축을 지원하기위한 라이브러리를 사용하여 종료 경우와
당신의 미래의 응용 프로그램에서 콘텐츠 제공자. 그것은을 위해 그 것이다
Android에서 스토리지에 대한 간단한 소개. 당신이 더 많은 것을 배우고 싶은 경우
developer.android.com으로 이동하여 데이터 스토리지를 검색하십시오.





20 - 최종 세부 와이어 프레임
===========================

이것이 우리의 마지막 자세한 와이어 프레임을 다시 방문하는 좋은 시간입니다.
각 일기 예보 위해, 우리는 적어도 날짜를 저장할 필요가 있다고하고,
조건은 고온 및 저온,
습도. 풍속과 방향 및 기압.우리의 데이터베이스는 각 예측 날짜를 표현하기 위해 줄을 사용하기 때문에, 우리는 저장합니다
다른 열에 예상 관련 데이터의 각 부분.





21 - WeatherContract
====================

우리의 데이터 사이에서 데이터베이스의 계약을 정의하는 것부터 시작하자
우리의 모델. 계약은 당사의 데이터 모델과 우리 사이의 합의이다
정보가 저장되어 있는지를 설명하기위한 도면.그것은 모든 필드가 포함됩니다
우리의 사용자 인터페이스가 표시됩니다. 코딩을 시작하려면 Android Studio 가자.
우리는 데이터가 데이터 모델을 캡슐화하는 우리의 프로젝트에 새로운 패키지를 추가합니다.
다음, 우리는 우리의 열 정보를 저장하기 위해 계약 클래스를 만듭니다.
우리의 계약 클래스의 내부 클래스는 테이블을 정의하는 데 사용됩니다.열이 기본으로 표시되기 때문에 각 테이블에는 기본 열을 구현합니다
열이 편리합니다. ID 열은 특히 우리의 테이블의 일부 여야합니다
우리의 콘텐츠 공급자의 통합은이 단원의 뒷부분에서 작동 시키려면





22 - 우리의 첫 번째 표
====================

우리의 데이터베이스는 날씨의 항목이 포함됩니다. 아웃 데이터 모델을 사용합니다
두 테이블.하나의 테이블은 장소에 대한 정보를 포함하기 위하여 사용되는
다른 데이터가 장소를 키 예측이 포함되어 있지만.
이들은 결국 계약을 통해 우리의보기에 다시 연결되어
콘텐츠 공급자. 우리는 내부 조인을 사용하기위한 완전한 데이터를 얻을 수 있습니다
각각이 오늘 예상. 장소에 대한 모든 정보를 포함한다. 이,
큰 계약입니다.우리는 외국되는 것이고, 위치 ID를 저장하는 것에주의하십시오
COLUMN_LOC_KEY의 위치 테이블에서 키. 단위가 포함되지 않은 점에 유의하십시오
데이터베이스. 우리는 모든 날씨 항목이 미터 단위로 저장되는 것을 기대하고
제국 단위에 UI가 필요한 때 변환됩니다.컬럼 이름 때문에,
실제로 데이터 형식이 포함되지 않은, 그것은에서 그 주석 편리합니다
우리의 계약을보다 명확하게하기 위해, 변수 이름 및 / 또는 코멘트.



23 - 칼럼
============

우리는 위치의 항목이 포함되어있는 우리의 다른 테이블에 계약을 작성해야합니다.
위치 항목은 도시의 이름이 포함되어 있어야합니다. 이 innerclass은 다음과 같습니다
weatherentry와 거의 같은 방법으로 만들었습니다. 이것은 기반 열을 구현한다.테이블 이름이 포함되어 있으며 각 열에 이름이 포함되어있다. 주 : 생각을
장소 항목 클래스의 각 행은 WeatherEntry에 저장됩니다.





24 - 열 솔루션
=====================

모든 권리 완료되었습니다! 그럼 내 솔루션을보고 갑시다. 그런데,주의하십시오
당신이 실제로 아직 이러한 솔루션 중 하나를 테스트하려면이 코드를 실행 할 수 없습니다.그러나 우리는 신속하게 테스트하는 것입니다, 걱정하지 마십시오. 여기에 우리의 솔루션입니다.
우리는 독특한 테이블 이름에서 시작됩니다. 내부 클래스의 나머지 부분,
우리는 데이터를 저장하는 데 사용하는거야 열을 나타냅니다.





25 - SQLiteOpenHelper를 사용하여 데이터베이스를 작성
==========================================

지금은 계약이다. 그러나 우리는 아직 데이터베이스를 가지고 있지 않습니다.저희 데이터베이스 클래스는 Android 클래스를 확장합니다. SQLITEOpenHELPER.
SQLITEOpenHELPER 우리는 데이터베이스의 버전 관리를 취급 돕기 위해 멋진 것이 포함되어 있습니다.
우리는 미래에 우리의 데이터베이스를 변경하면 그것은 우리가 해결하는 데 도움이 우리의
테이블. 많은 응용 프로그램에서 데이터 손실없이 새 버전으로 업그레이드 할 수있다
매우 중요합니다.는 데이터 패키지 WeatherDBHelper 클래스를 만들어 봅시다과
그것은 SQLite 오픈 도우미를 확장하고있다. [SOUND] 우리는 추가 할 수 있습니다
Ctrl 키를 + I를 누르면 필요한 메소드.
그리고 우리는 Ctrl 키를 + O를 눌러 생성자를 재정의 할 수 있습니다. 그래서 지금 우리는 하드 코드를 할 수 있습니다
이러한 변수는 생성자에.데이터베이스 이름을 하드 코딩 이름
null에 우리의 공장 및 데이터베이스 버전에 우리의 버전입니다.
글쎄, 당신은 내가 데이터베이스 이름을 공개하고 있습니다주의하십시오, 그리고 있어요
우리는 미래에 우리의 테스트에서 그것을 사용하는거야 때문이다.
이제 우리가 만들고 ONUPGRADE 방법으로 그것을 가지고 참조하십시오.OnCreate 방법은 구축하기 위해 문자열을 작성하는 것으로 시작하는거야
기상 항목 계약에 정의 된 데이터를 사용하여 기상 항목 테이블.
지금은 그냥이 댓글을 추가 할 생각이므로, 다시 어디 당신이 알고
나중에 위치 항목을 추가합니다. 기상 항목이 달라 지므로
장소 항목에는 난 보통 처음 항목을 설명하지만
날씨의 항목은 상당히 복잡합니다.그래서 오히려 우리가 무슨 짓을했는지를 설명하고자
당신까지 장소 항목을 남긴다. 우리는을 위해 원시 SQL을 사용하는거야
우리의 우리의 계약에서 테이블 이름에서 시작하여 테이블 쿼리를 만듭니다.
이 시점에서 그것은 WeatherContract.locationentry을 가져 오면 편리하고
날씨 항목. 그것은 읽기들의 쿼리가 너무 쉽게합니다. 우리는 시작하자
우리는 자동 증가 필드에 우리의 기본 키로 설정됩니다 우리의 ID 필드.
그 정수가 실제로 SQLite에서 긴 8 바이트 부호있는 값임을주의하십시오.
자동 증가 기능을 사용하면 1이 생각할지도 모른다 것을 정확하게하지 않습니다.ID를 설정하면 정수 기본 키가 실제로하게됩니다
고유 값은 삽입을하지만, 그것은 반드시 증가하지 않는 것은 언제든지.
이것은 레코드의 기존 ID 값이 제거 된 재사용 할 수있다.
어떤 자동 증가 정말 편리합니다 당신이 데이터 2를 동기화하는 경우입니다.
서버와 방법.그것은 데이터를 생성하기 때문에, 그러나 우리는 여기에서 그것을 이용합니다
우리는 오른쪽과 같이 연결 때문에 우리 쿼리에서보다 자연스럽게 비트를 정렬
서버에서 순이었다. 일반적으로 우리는 필드상의 제약을 사용하고있다.
이 경우는 null이 아니다. 그것은 데이터베이스를 많이 할 수 있기 때문에, 우리는 이렇게
우리를 위해 우리의 매개 변수 확인.이 방법으로 그것을하고 약 까다로운 부분,
이러한 제약이 실패했을 때 우리는 편리한 오류가 발생하지 않는다는 것입니다,
그것은 디버깅이 어려울 수 있습니다. 우리는 인간이 읽을 수있는 문자열을 사용하는
날짜 또는를위한 강력한 이유는 없습니다
이 선택에 대해. 우리는 쿼리를 단순화하는 날짜를 정상화하고 싶었
그리고 인간의 가독성은 디버깅이 쉬워집니다.날짜에서 열린 날씨에서 유래
우리는 없애 필요가있는 몇 시간 정보를 가진 UNIX 타임 스탬프 형식입니다.
나는 모든 필드를 커버 할 생각은 없습니다. SQL에서 부동 소수점 리얼 의미합니다.
뿐만 아니라 고정 소수점 연산에서 정수를 사용하여 있었기 때문에 괜찮 았어 것이고,
일부는 이것은 빠른 것이라고 주장하는 것이지만,
우리는 부동 소수점 값을 저장하고 있기 때문에 실제는 더 간단합니다.현재
재미있는 것은 우리는 LOC 키를 설정하는거야.
당신이 구축되는 장소 항목 테이블에 외래 키입니다.
이것은 테이블 간의 관계를 강화하기 위해 SQLite됩니다.
해당 위치의 항목이 존재하지 않을 때 우리는 날씨 항목을 삽입 할 수 없습니다.
그 날씨 항목이 아직 존재하는 경우, 우리는 장소 항목을 제거 할 수 없습니다
그것에 의존한다. 멋진 것, 오른쪽? One 마지막 제약.우리 날짜의 텍스트 이외에 장소는 고유해야합니다. 분쟁은 데이터를 교환하십시오.
이것은 우리가 쉽게 열리는 날씨 EPI에서 새로운 데이터를 삽입 할 수 있습니다.
기존의 키를 유지하고 예측의 변화에​​ 따라 값을 업데이트한다.




26 - LocationEntry
==================

위치 항목에서 일치하는 위치 항목 테이블 만들기 쿼리를 만듭니다
계약 모델로 기상 항목 1을 사용합니다. 좋은 소식은이 것입니다.간단한 쿼리가있다. 당신이 정말로 데이터베이스를 싫어한다면 단순히 솔루션으로 전환.





27 - LocationEntry 솔루션
===========================

훨씬 쉽게 테이블. 단지 표준 기본 키 일부 값 및
일부 제약. 우리는 IGNORE 분쟁에 관한 사용하는 것에주의하십시오. 이것은 인서트 의미
같은 키를 사용하여 데이터베이스에 실제 데이터베이스를 업데이트하지 않습니다
모두. 그러기 위해서라도 Android 헬퍼 함수에서 ID를 반환하지 않습니다.



28 - SQLiteOpenHelper ONUPGRADE 방법
======================================

그런데 지금 우리는 어딘가에 있어요. 우리가해야 할 것은 이러한 테이블의 생성을 실행하는
우리에 마지막으로 정확한 속편을 호출하여 쿼리 함수를 만듭니다. 하지만 잠깐
우리의 SQliteOpenHelper, ONUPGRADE의 다른 기능이 있습니다. 당신은 생각할지도 모르지만,
왜 나는 그들을 걱정해야?
나는 아직 아무것도 업그레이드 아니에요.우리의 개발은 우리가하는 것보다 쉽게​​ 사는 있도록하려면
가 ONUPGRADE의 가장 표준적인 형식을 구현 할 예정이다.
당신의 데이터베이스 버전을 변경하는 경우에만 화재를 ONUPGRADE를 참조하십시오.
이제 우리는 SQliteOpenHelper 기반 생성자에 해당 버전을 전달 기억
예전에.우리는 Web 데이터 캐시로 우리의 데이터베이스를 사용하여 시도하고 있기 때문에
사용자를위한 콘텐츠를 생산하지 않는, 우리는 테이블을 삭제합니다. 우리 경우에 유용합니다.
장래 적으로는 데이터베이스를 변경하고 싶습니다. 우리는 사용자 데이터를 사용하지 않으면 우리는 무엇일까
사용 같은 것은 새 열을 추가 할 테이블을 변경합니다. 그래서 지금 우리는 데이터베이스를 가지고있다.



29 - JUnit 테스트
==================

우리는 우리의 코드에서이를 테스트 할 수 있습니다 전에 그러나 그것은 잠시됩니다. 우리는 여전히하려고하고있다
UI 변경의 무리와 함께 그 위에 층 전체를 구현한다.
다행히도, 우리는 돕기 위해 여기에 J 단위 테스트를 구현 할 수 있습니다. 그리고 지금을 위해
어떤 마법.우리는 Android 스튜디오의 소스 디렉토리에 디렉토리를 추가합니다
프로젝트는 Android의 테스트라고. 그리고 그 밑에 다른 1은 Java로 불린다.
이것은 우리가 테스트 대상이 찾고 크래들에 있습니다 Android 스튜디오를 전하는 방법입니다
우리의 응용 프로그램. 이제 우리는 우리의 메인 패키지에 일치하는 테스트 패키지를 만들
마지막으로 추가 테스트 디렉토리. 전체라는 새로운 클래스를 만듭니다.테스트 패키지의 테스트. 이 코드를 추가합니다. 이
우리는 추가 클래스에서 테스트를 추가 할 수있는 몇 가지 보일러 플레이트 코드이다.
그렇다면, 우리는 Android 테스트 케이스 노이즈 및 확장하는 TESTDB 클래스를 만듭니다
우리의 데이터베이스를 만들어 테스트를 추가합니다.이것이 작동하는 방법은 테스트 러너 것입니다
이를 위해 테스트로 시작하는 우리의 클래스의 모든 기능을 수행합니다
그들은 클래스에서 선언되어있다. 각 테스트는 실패 경로를 가지고 있어야합니다
주장을 사용하고 있습니다. 우리는 그것을 테스트하기 전에 데이터베이스를 제거하여 시작한다. 그래서,
우리는 깨끗한 테스트를 가지고있다.그런데,이 응용 프로그램에 우리는 간다 테스트를 실행하기 위해 드롭 다운을 시작했다.
그리고 편집 구성을 선택합니다. 우리는 새로운 설정을 추가하려면 더하기를 선택합니다. 과
모듈의 응용 프로그램에 대한 Android 테스트를 선택합니다. 이제 우리는 테스트에 이름을 붙인다.
지금은 기본적으로 에뮬레이터를 대상으로하는 경향이 있다는 점에 유의하십시오.그래서,
나는 쇼 선택 대화를 선택하는 것입니다 실제 장치를 사용한다.
이제 우리는 우리의 장치에 대한 테스트를 수행 할 수 있습니다. 그리고 그것이 통과한다. 이렇게
는 데이터 기반 인서트를 만들고 테스트를 읽어 보자. 그것의 시작,
우리는 각각의 테이블에 단일 레코드를 삽입합니다. 우리는 몇 가지 더미에서 시작하자
우리의 위치를​​위한 데이터.우리는 쓰기 가능한 데이터베이스를 얻기 위해 dbHelper을 사용합니다.
이것은 우리가 우리의 프로젝트에서 그것을 코딩 할 때 우리는 데이터베이스를 사용합니다 정확히 어떻게있다.
우리는 그 편리한 도우미 개체입니다 ContentValues​​ 객체를 만듭니다
Android 값과 키를 저장하는 데 사용합니다. 우리는 우리의 더미 데이터를 저장합니다
우리의 LocationEntry 계약에서 라인.그것을 만들기 위하여주의
이 생략 구문에서 작업, 여기에 몇 가지 여분의 수입을 추가 할 필요가 없었다.
그렇다면 우리의 데이터베이스에 데이터를 삽입, 우리는 뒷줄을 얻은 것을 확인했다.
지금 나는 내 테스트 케이스에 로그 메시지를두면 유용하다는 것을 발견 할 것이다.
이제 우리는 밖으로 다시 우리의 거짓 데이터를 가져 오는 데이터베이스 읽기 작업을 사용합니다
데이터베이스.우리는 이론적으로는 여기에 사용자 정의 투영을 이용하고있다
우리가 원하는 값을 조회 할 수 있도록 우리의 데이터베이스 커서를 사용하는 것이 쉬울 것이다.
여기에서는 사용자 정의 투영을 사용하고 있습니다. 하지만 그것은 필요하지 않습니다.
사용자 정의 투영이 없었던 경우는 단순히 모든 라인을 돌려줍니다.
데이터베이스 커서는 위의 통과를 허용하는 제어 구조입니다
데이터베이스 레코드.안드로이드에서는이 커서 오브젝트에 의해 표현된다.
커서 오브젝트는 하나가 쿼리에서 레코드 사이 횡단하는 것을 허용하고
쿼리에서 모든 개별 라인의 내용을 받았다.
이제 우리는 데이터의 우리의 행의 커서를 설정하기 위해 cursor.moveToFirst을 사용하고 있습니다.
다음은 인덱스에 의해 우리의 데이터를 활용할 수 있습니다. 마지막으로 주장
그것은 우리의 더미 데이터와 일치하지 않는 경우. 그리고 지금 우리는 다시 우리의 테스트를 실행 해달라고한다.
[BLANK_AUDIO]
그리고 그들은 통과했습니다.



30 - InsertReadDbTest
=====================

의견이 있으시면 다음의 말처럼 모든 권리, 지금 우리는 위치를 가지고있는 몇 가지를 추가하자
날씨입니다.우리의 삽입 redb이 테스트의 날씨 일부를 구현하여 봅시다. 나는거야
당신을 돕기 위해 당신에게 몇 가지 더미 데이터를 제공합니다. 위치 키는 행임을주의하십시오
우리는 단지 삽입 된 데이터의 ID입니다. 또한 나는이 짧은 구문을 사용할 수있는 점에 유의하십시오
기상 항목, 그 파일의 선두에이 수입을 추가했기 때문에.자, 우리는 나는 우리의 데이타베이스에 당신을 준 데이터를 제공 한 것을 넣고
우리는 다시 그것을 읽어 되돌릴 수 있는지 확인합니다.





31 - InsertReadDbTest 솔루션
==============================

모든 권리는 완료되었습니다. 난 당신이 내가 당신을 주었다는 것을 꺼리지 않는다는 것을 희망한다
큰 테이블이 시간.하지만 첫 번째에 의존하기 때문에 그것이 온 것이다
다른 어떤 순서로 당신을주는 것은 어렵다. 난 당신의 콘텐츠 값 구조를 준
그냥 데이터를 삽입하는 것은 매우 간단합니다. 그럼 우리가 다시 데이터를 조회합니다.
[SOUND] 첫째로의 전환에 실패하면 커서가 하늘이며,
쿼리가 실패했습니다. [LAUGH] 여기에 컷 & 페이스트가 많이 있습니다.그것은 DV를 얻기 위해 좋다
그 엄격하게 필요하지 않지만 데이터 형식의 도우미를 사용하여 값
우리가 알고 있기 때문에 우리의 테스트 데이터는 실제로 우리의 제약 조건과 일치하게 일어나고있다. 과
1보다 많은 실패 사례는 우리의 쿼리가 복귀하지 않는 경우, 여기에 추가해야합니다
모든 행. 그리고 그 것이다. 모든 단지 데이터베이스를 검색 할 수 및
그것을 테스트하는 방법.그럼 테스트를 다시 실행하여 보자. 글쎄,
적어도 우리는 모든 기본적인 것들을 작품을 알고, 다만 이러한 테스트하지 않고 기억,
당신은 매우 긴 시간 동안이 코드를 실행할 수 없었을 것입니다.





32 - 테스트를 간소화
===================

괜찮아. 지금 오픈 엔드 형 운동의 조금을 위해.
어떻게 우리는 우리의 테스트 코드를 단순화 할 수 있습니까? 솔루션을 쓴다.힌트는 여기에있다
우리는 콘텐츠의 가치 구조의 읽기 특성을 활용할 수있다.





33 - 테스트를 간소화
===================

여기에서 나는 것들을 단순화하게 방법입니다. 나는 훌륭한 테스트의 아이디어를보고 싶어요.
당신이 창조 한 것이 특정하고있는 경우, 위해 솔루션을 게시
포럼. 나는 물건을 조금 리팩토링 오프 시작했다.나는 지금 어떤
무엇을 할 생각은 내가 위치 내용 값을 검색하는 기능을 추가하는 것입니다.
우리가 실제 위해 이러한 테스트를 사용하려고 할 때 유용합니다
나중에 위의 몇 가지 다른 것. 그리고 거기에 우리가있다. 기능이야
위치 내용 값을 반환합니다. 나는 또한 도시의 이름을 꺼내는거야
우리는 나중에 여러 가지 검증 절차를 위해 그것을 사용할 수 있습니다. 그리고 거기에 우리가있다.그것은 지금이다
함수 내부. 그리고 우리는 단순히 그 함수를 호출하는거야
우리의 위치 내용 값을 가져오고 우리는 코드의 모든 행을 제거 할 수 있습니다.
그런데, 이러한 열 모두, 나는 매우 중요하지 전에도 말했듯이
우리는 그들을 제거 할 수 있습니다. 그리고 우리는 또한 우리의 쿼리에서 값을 0 수 있습니다.
내가하고 싶은 다음 것은 사실이 확인 절차를 수정하고있다.우리는 무엇을 할 수 있습니다
우리는지도를 얻을 수 있다는 사실에 의존하는 함수를 만들 수 있으며,
우리의 콘텐츠 값에서 설정하십시오. 그리고 우리는 단순히 그들을 반복 할 수 있습니다. 그럼 우리가 볼 수 있다면, 우리는 실제로 과거의 기록을 작성하는 데 사용되는 값
반환 된 커서의 값입니다. 자, 다시 우리의 작업.그래서,
불필요한 코드의 대부분은 지금 여기에 있습니다. 우리가해야 할 일은 호출입니다
우리의 가치와 우리의 커서 validateCursor. 괜찮아. 그래서 지금 우리는했습니다
첫 번째 테스트로 변환. 우리뿐만 아니라 두 번째 시험에서 같은 일을 할 수 있습니다.
모든 첫째로, 우리는 이전과 같은 추상화를합시다. 지금 물론,
이러한 값 1은 정적이기 위하여려고하고 있지 않기 때문에, 중간에 추가해야합니다.그래서 지금 우리는 콘텐츠의 값이 getWeatherContentValues​​과 같음 말할 수 있습니다.
우리의 모든 중요한 장소의 행 ID를 가진다. 기억 우리 테이블이 연결되어있다.
그리고 우리는 데이터베이스에 삽입 할 수 있습니다. 그것을 조회한다.
쿼리가 성공하면 우리는 우리의 날씨에 다시 validateCursor를 호출 할 수 있습니다
우리의 기상 커서를 가지는 값. 그렇게 적은 코드.
그리고 그 것이다.우리의 테스트가 단순화되고,
그것은 나중에 우리에게 도움이 될 것이다. 그래서 지금 우리는 다시이 테스트를 실행 해보세요
그것은 여전히​​ 리팩토링 후 작동 여부를 알게된다. 그리고 거기에 우리는 테스트가 전달됩니다. 그런데,
우리는 실제로 그렇게 좀 더 많은 데이터를 출력하는 것은 유용 될 것이다
우리는 테스트되고 있었는지를 볼 수 있습니다.그러나이 단순화 우리에게
테스트는 우리가 전진하도록 우리를 도와 일어나고있다. 우리는 아직 테스트하지 않았습니다.





34 - 테스트를 간소화
===================

여기에서 나는 것들을 단순화하게 방법입니다. 나는 훌륭한 테스트의 아이디어를보고 싶어요.
당신이 창조 한 것이 특정하고있는 경우, 위해 솔루션을 게시
포럼. 나는 물건을 조금 리팩토링 오프 시작했다.나는 지금 어떤
무엇을 할 생각은 내가 위치 내용 값을 검색하는 기능을 추가하는 것입니다. 우리가 실제 위해 이러한 테스트를 사용하려고 할 때 유용합니다
나중에 위의 몇 가지 다른 것. 그리고 거기에 우리가있다. 기능이야
위치 내용 값을 반환합니다. 나는 또한 도시의 이름을 꺼내는거야
우리는 나중에 여러 가지 검증 절차를 위해 그것을 사용할 수 있습니다. 그리고 거기에 우리가있다.그것은 지금이다
함수 내부. 그리고 우리는 단순히 그 함수를 호출하는거야
우리의 위치 내용 값을 가져오고 우리는 코드의 모든 행을 제거 할 수 있습니다.
그런데, 이러한 열 모두, 나는 매우 중요하지 전에도 말했듯이
우리는 그들을 제거 할 수 있습니다. 그리고 우리는 또한 우리의 쿼리에서 값을 0 수 있습니다.
내가하고 싶은 다음 것은 사실이 확인 절차를 수정하고있다.우리는 무엇을 할 수 있습니다
우리는지도를 얻을 수 있다는 사실에 의존하는 함수를 만들 수 있으며,
우리의 콘텐츠 값에서 설정하십시오. 그리고 우리는 단순히 그들을 반복 할 수 있습니다.
그럼 우리가 볼 수 있다면, 우리는 실제로 과거의 기록을 작성하는 데 사용되는 값
반환 된 커서의 값입니다. 자, 다시 우리의 작업.그래서,
불필요한 코드의 대부분은 지금 여기에 있습니다. 우리가해야 할 일은 호출입니다
우리의 가치와 우리의 커서 validateCursor. 괜찮아. 그래서 지금 우리는했습니다
첫 번째 테스트로 변환. 우리뿐만 아니라 두 번째 시험에서 같은 일을 할 수 있습니다.
모든 첫째로, 우리는 이전과 같은 추상화를합시다. 지금 물론,
이러한 값 1은 정적이기 위하여려고하고 있지 않기 때문에, 중간에 추가해야합니다.그래서 지금 우리는 콘텐츠의 값이 getWeatherContentValues​​과 같음 말할 수 있습니다.
우리의 모든 중요한 장소의 행 ID를 가진다. 기억 우리 테이블이 연결되어있다.
그리고 우리는 데이터베이스에 삽입 할 수 있습니다. 그것을 조회한다.
쿼리가 성공하면 우리는 우리의 날씨에 다시 validateCursor를 호출 할 수 있습니다
우리의 기상 커서를 가지는 값. 그렇게 적은 코드.
그리고 그 것이다.우리의 테스트가 단순화되고,
그것은 나중에 우리에게 도움이 될 것이다. 그래서 지금 우리는 다시이 테스트를 실행 해보세요
그것은 여전히​​ 리팩토링 후 작동 여부를 알게된다. 그리고 거기에 우리는 테스트가 전달됩니다. 그런데,
우리는 실제로 그렇게 좀 더 많은 데이터를 출력하는 것은 유용 될 것이다
우리는 테스트되고 있었는지를 볼 수 있습니다.그러나이 단순화 우리에게
테스트는 우리가 전진하도록 우리를 도와 일어나고있다. 우리는 아직 테스트하지 않았습니다.