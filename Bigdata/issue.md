정호준[사원] 님의 말 (오후 2:15) :
    차장님 안녕하세요~
오늘 진짜 덥네요.ㅜㅜ 구미도 34도인걸로 보이는데
오석근[차장] 님의 말 (오후 3:04) :
    하이~
정호준[사원] 님의 말 (오후 3:22) :
    차장님께 대전 쪽 hiveserver2 jdbc url을 제가 찾은 결과 검토 받으려고 연락드렸어요~ 그 내용은 카톡으로 보내드리긴했는데
Hive랑 RStudio를 연동하려고 하늗네
R쪽에 jdbc hiveserver2 url 적는 과정에서
남영지 차장님이 대전의 경우 커버로스가 되어있으니 hiveserver2의 값이 심플하고는 다르니 확인이 필요하다고하시네요
정호준[사원] 님의 말 (오후 3:24) :
    제가 찾은 url은
"jdbc:hive2://node1:10000/default;principal=hive/HiveServer2Host@YOUR-REALM.COM"
오석근[차장] 님의 말 (오후 3:24) :
    거기에 hive.server2.proxy.user
정호준[사원] 님의 말 (오후 3:24) :
    이렇게 하라고 하는데 맞는지 차장님께 확인받고싶어서요ㅎㅎ
소윤대리 화학도 커버로스여서 소윤대리한테 물어보려고 했으나 소윤대리쪽에 장애나서 답변 받기 힘들어 바쁘신 차장님께 메신저 드려요 ㅜㅜ
오석근[차장] 님의 말 (오후 3:24) :
    이 옵션까지 주면 될듯
정호준[사원] 님의 말 (오후 3:27) :
    혹시 옵션까지 주면이라는게
hive.server2.proxy.user 이 옵션에 있는 값이 root라고 하면
"jdbc:hive2://node1:10000/default;principal=hive/HiveServer2Host@YOUR-REALM.COM;proxyUser=root"
정호준[사원] 님의 말 (오후 3:28) :
    이걸 의미하시는건가요?
오석근[차장] 님의 말 (오후 3:28) :
    저 옵션을 그대로 붙여야지
정호준[사원] 님의 말 (오후 3:30) :
    "jdbc:hive2://node1:10000/default;principal=hive/HiveServer2Host@YOUR-REALM.COM;hive.server2.proxy.user=root"
    아 넵ㅎㅎ
    감사합니다~~
오석근[차장] 님의 말 (오후 3:46) :
    실제로는 저 옵션 사용자로 로긴되는거삼


---------------  2017년  7월 26일  ---------------
정호준[사원] 님의 말 (오후 3:40) :
    안녕하세요. 차장님.
오석근[차장] 님의 말 (오후 3:40) :
    하이~
정호준[사원] 님의 말 (오후 3:40) :
    죄송한데 부탁드릴게 있어서요ㅜㅜ
오석근[차장] 님의 말 (오후 3:41) :
    어떤...?
정호준[사원] 님의 말 (오후 3:41) :
    내일 대전에 가서 저녁때 MRD랑 hive,tez 업그레이드 진행하거든요
    작업계획서 출력해서 작업할텐데..
    혹시 문제 생기는걸 제가 찾다가 해결 못하게 되면 저녁 때 연락드려도될까요..?
오석근[차장] 님의 말 (오후 3:41) :
    ㅇㅇ
오석근[차장] 님의 말 (오후 3:42) :
    도움이 될지는 모르겠지만 ㅋ
정호준[사원] 님의 말 (오후 3:42) :
    감사합니다 ㅜㅜ
    멀리서 프로젝트하시는데
    죄송해유ㅜㅜ
오석근[차장] 님의 말 (오후 3:42) :
    백업 잘해두고...
    혹시 안되면 롤백해야 하니께
정호준[사원] 님의 말 (오후 3:42) :
    넵넵 알겠습니다.
오석근[차장] 님의 말 (오후 3:44) :
    파일은 어케 하기로 햇어?
    패치파일 반입
정호준[사원] 님의 말 (오후 3:44) :
    파일은 제가 cd로 구웠구요
    내일 대전에 가서 먼저 검사해야될것같아요
정호준[사원] 님의 말 (오후 3:45) :
    송재현수석이 원칙적으로는 cd로 구워오는게 맞다고 회신이 와서요.\
오석근[차장] 님의 말 (오후 3:45) :
    cd로 구워와도 뭐 검사하고 한참 걸리더라고
    그 시간 고려해야 할듯
정호준[사원] 님의 말 (오후 3:45) :
    넵 고려해서 출발할게요!

오석근[차장] 님의 말 (오후 3:46) :
    수고~

정호준[사원] 님의 말 (오후 3:48) :
    감사합니다~


---------------  2017년  7월 31일  ---------------
오석근[차장] 님의 말 (오후 6:03) :
    https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL#LanguageManualDDL-AlterTable/PartitionLocation
정호준[사원] 님의 말 (오후 6:13) :
    파티션은
    없다고하네요ㅜ
    그리고 이상한게
    새로 table을 생성하고
구조랑 데이터는 동일한걸 사용했는데
정호준[사원] 님의 말 (오후 6:14) :
    처음에
    user한테 할당해준 디렉토리명이
    /user/hive/aaa였대요.
    근데 이걸 /user/hive/bbb로
    변경하고 쓰게하고있다고 합니다
오석근[차장] 님의 말 (오후 6:14) :
    디렉토리 퍼미션은?
정호준[사원] 님의 말 (오후 6:16) :
    디렉토리 퍼미션은 user id별로 준걸로 알고 있는데
지금 문자로 정확히 물어볼게요.,
오석근[차장] 님의 말 (오후 6:16) :
    호준씨도 개발기에서 함 해봐
    너무 급하게 응대 안해도 되니
정호준[사원] 님의 말 (오후 6:17) :
    넵 지금
    돌리고있습니당
정호준[사원] 님의 말 (오전 10:39) :
    차장님 안녕하세요.
    여쭤볼게 있는데, 김순호 차장님말로는
유저포탈에서 id를 생성하면 id명.keytab파일이 생성된다는데, 제가 서버에서 찾질 못해서요.\
오석근[차장] 님의 말 (오전 10:47) :
    keytab 파일이 생기는건 아니고
    kerberos KDC에 principal이 생겨요
    keytab이 필요하면 만들어야 해요
정호준[사원] 님의 말 (오전 11:00) :
    제가 hive cli에 붙어서 쿼리를 돌리고 싶어서
어제 유저포탈에서 생성한 user의 keytab을 생성하려고 하는데

xst -k hive.service.keytab theid/sbprnd01.sbp.com
으로 시행하면 될까요?

오석근[차장] 님의 말 (오전 11:00) :
    ㅇㅇ

오석근[차장] 님의 말 (오전 11:01) :
    키탭 파일명을 사용자 명으로 하는게 더 직관적일듯

정호준[사원] 님의 말 (오전 11:02) :
    theid가 사용자명인데, 혹시 파일명이
hive.service.keytab이되는건가요?

오석근[차장] 님의 말 (오전 11:02) :
    ㅇㅇ

정호준[사원] 님의 말 (오전 11:02) :
    넵 감사합니다.


---------------  2017년  8월  3일  ---------------
정호준[사원] 님의 말 (오전 11:03) :
    차장님 안녕하세요.
정호준[사원] 님의 말 (오전 11:04) :
    저 여쭤볼게 있는데,
madmin의 계정의 key
정호준[사원] 님의 말 (오전 11:05) :
    admin.keytab은 커버로스 admin의 키탭이고 madmin은 커버로스 입장에서도그냥 일반 유저인거죠?
오석근[차장] 님의 말 (오전 11:07) :
    SBP에서 쓰는 kerberos principal은 모두 admin
    이고
오석근[차장] 님의 말 (오전 11:08) :
    나머지 사용자는 admin principal을 사용하여 proxy user로
    사용하고 있어요
    keytab은 1개 이상의 principal을 등록해서 내려 둘수 있는 장치구요
    admin.keytab에는 admin principal만 들어 있긴해요
오석근[차장] 님의 말 (오전 11:09) :
    https://hadoop.apache.org/docs/r2.7.1/hadoop-project-dist/hadoop-common/Superusers.html
정호준[사원] 님의 말 (오전 11:10) :
    읽어보도록 하겠습니당
오석근[차장] 님의 말 (오전 11:11) :
    https://www.slideshare.net/gruter/hadoop-security-deview-2014
    요것도 좀 지난 자료지만 하둡 시큐리티 잘 정리된 자료
    추천
정호준[사원] 님의 말 (오전 11:12) :
    감사합니다!
정호준[사원] 님의 말 (오후 3:42) :
    차장님 안녕하세요.
정호준[사원] 님의 말 (오후 3:43) :
    지금 클러스터 환경에서 테스트 중인데,
tez도 기존에 0.7.0 버전에서 0.5.4로 변경하였거든요.
근데 scm에서 tezUI를 눌러서 들어가니 0.7.0 화면으로 연결이 되는데 테즈 버전 패치 작업이 적용이안되서 그런건가요?
오석근[차장] 님의 말 (오후 3:44) :
    그런거 같은데요
정호준[사원] 님의 말 (오후 3:48) :
    scm에서 hive서비스 - tez Library복사 눌러서 임시로 디렉토리 만들고 진행해보니, 제가 패치한 0.5.4의 라이브러리가 복사가 되던데...별도로 잡는 과정이 있나요?
오석근[차장] 님의 말 (오후 3:49) :
    그건 잘 모르겠네요
    SBP 전체를 다 외우고 다니는게 아니라 ㅋ
정호준[사원] 님의 말 (오후 3:50) :
    위키랑 레드마인을 다시한번 찾아보겠습니다.
오석근[차장] 님의 말 (오후 3:57) :
    YARN 통해서 띄우는 것 같은데
    그 서버 포트 확인하고
오석근[차장] 님의 말 (오후 3:58) :
    netstat -nap | grep LISTEN | grep portNum
    으로 프로세스 id 찾은다음에
    ps -ef | grep pid로 프로세스가 뭘 물고 있는지 확인하면 될듯해요
정호준[사원] 님의 말 (오후 3:58) :
    timleIneRestUri에서 YarbCin
정호준[사원] 님의 말 (오후 3:59) :
    YarnConstants까지 따라갔으나 경로를 언급하진 않는것같았는데.
    한번 프로세스 찾아볼게요
오석근[차장] 님의 말 (오후 3:59) :
    네


---------------  2017년  8월  9일  ---------------
정호준[사원] 님의 말 (오후 1:08) :
    차장님 안녕하세요. 제가 대전하고 동일한 환경을 구성해서 테스트 진행하려고하는데,
    scm 설치하는것에서부터..막혀서요...
정호준[사원] 님의 말 (오후 1:10) :
    클라우드에는 scm-dist-xxx.tar.gz 파일이 있는데 가이드 보면 scm-xxx.tar.gz으로 하라고 하기도 하고
scm-dist-2.1.0.tar.gz을 풀어서 하니, /engn001/sbp/scm/systemfile/uploadTemp 경로가 없어서
    설치가 진행이 안되는것 같은데..제가 설치파일을 잘못 알고 있는게 맞나요..?
오석근[차장] 님의 말 (오후 1:54) :
    dist로 하는게 설치마법사 이용하는거 아닌가?

정호준[사원] 님의 말 (오후 2:06) :
    넵..

                   < 여기까지 대화하셨습니다 >

정호준[사원] 님의 말 (오전 9:38) :  
차장님 안녕하세요
오석근[차장] 님의 말 (오전 9:38) :  
하이~
정호준[사원] 님의 말 (오전 9:38) :  
저 장애난거 때문에 여쭤볼게 있어서요ㅜㅜ 차장님에게 조언좀...
오석근[차장] 님의 말 (오전 9:38) :  
ㅇㅇ
정호준[사원] 님의 말 (오전 9:38) :  
U+ 쪽 namenode가 수요일에 메모리 부족으로
HA 구성은되어있었는데 둘다 뻗어가지고
정호준[사원] 님의 말 (오전 9:39) :  
원인은 메모리 부족같아 4G->8G로
올려서 재기동했었거든요.
오석근[차장] 님의 말 (오전 9:39) :  
ㅇㅇ
정호준[사원] 님의 말 (오전 9:39) :  
근데 그 때 오후에 데이터노드3대중 1대가 죽었고
당장 수요일 오후에는 반차라 외부에 있어서 바로 확인못하였고, 데이터노드 재기동 가이드 준다음에 목요일은 예비군 갓다가 이제 로그 파일 받아서 확인해보려는데
데이터노드가 전체가 죽었어요.
정호준[사원] 님의 말 (오전 9:40) :  
한대죽었을때 에러로그는
Caused by : java.net.ConnectException: ... 글자가 깨져서 나와서 알순 없지만
구글링해보니
정호준[사원] 님의 말 (오전 9:41) :  
네임노드가 문제생겨서
재기동햇을 떄에ㅔ
safemode로 실행이
된상태에서
정호준[사원] 님의 말 (오전 9:42) :  
datanode.DataNode : Failed to report bad block BP-....
at org.apache.hadoop.hdfs.server.datanode.ReportBadBlolckAction.reportTo(ReportBadBlockAction.java:67)...등등이
오석근[차장] 님의 말 (오전 9:42) :  
전화 줘삼
정호준[사원] 님의 말 (오전 9:42) :  
보이거든요
넵
오석근[차장] 님의 말 (오전 9:42) :  
010-2534-6795
오석근[차장] 님의 말 (오전 9:54) :  
org.apache.hadoop.util.JvmPauseMonitor: Detected pause in JVM or host machine (eg GC): pause of approximately 3809ms
오석근[차장] 님의 말 (오전 9:55) :  
pause in JVM
오석근[차장] 님의 말 (오전 10:01) :  
https://community.hortonworks.com/questions/39875/datanode-heap-exhaustion.html
근데 데이터노드가 블럭수에 따라 힙을 많이 쓰는지는 좀 찾아봐야 할듯
정호준[사원] 님의 말 (오전 10:09) :  
새로 추가된 데이터가 있냐고 물어보니
로그데이터 새로 수집시작했따고 하는데
hdfs경로상에 그 파일이
정호준[사원] 님의 말 (오전 10:10) :  
hive partition에 daily 기준 230byte의 크기로 4000개씩 나뉘어져 있는걸 확인했는데
오석근[차장] 님의 말 (오전 10:10) :  
230bytes?
헐
정호준[사원] 님의 말 (오전 10:10) :  
차장님께서 말씀하신대로 작은파일이 많아서 기존보다 메모리가 부족했던거같아요..
예전에는 이러지 않았었는데..
오석근[차장] 님의 말 (오전 10:11) :  
콘솔에 가면 디렉토리랑 파일수 나올꺼야
그리고 의심가는 경로 hdfs dfs -ls -R 경로 | wc -l
하면 몇개인지 볼수 잇고
메모리 늘리는 것도 필요하고
오석근[차장] 님의 말 (오전 10:12) :  
데이터를 230byte씩 쌓이게 하지 않는게 더 중요함
정호준[사원] 님의 말 (오전 10:13) :  
194671개로 나오네요.
오석근[차장] 님의 말 (오전 10:13) :  
며칠치야?
정호준[사원] 님의 말 (오전 10:14) :  
50일치도 안됩니당
오석근[차장] 님의 말 (오전 10:14) :  
전체는 몇개고?
대략 나눠보면 48일 정도 되네
네임노드 콘솔에서
9088 files and directories, 4890 blocks = 13978 total filesystem object(s).
Summary 밑에 세번째줄
?
정호준[사원] 님의 말 (오전 10:15) :  
15565993 files and directories, 13264808 blocks = 28830801 total filesystem objects(s)
오석근[차장] 님의 말 (오전 10:16) :  
나머지가 훨 많네
정호준[사원] 님의 말 (오전 10:16) :  
아 잠시만요
오석근[차장] 님의 말 (오전 10:16) :  
https://www.cloudera.com/documentation/enterprise/5-10-x/topics/admin_nn_memory_config.html
오석근[차장] 님의 말 (오전 10:17) :  
여기보면 object 하나당 대략 150byte 잡아서 어림 잡는데
28830801 로 계산하면 4기가 좀 넘네
정호준[사원] 님의 말 (오전 10:17) :  
여기서
오브젝트는
오석근[차장] 님의 말 (오전 10:17) :  
근데 메타만 저 공간이니 부족한게 맞는듯하고
정호준[사원] 님의 말 (오전 10:17) :  
어떤 단위로 봐야되요?
오석근[차장] 님의 말 (오전 10:18) :  
파일이 여러개의 블럭으로도 나눠질수 있자너
정호준[사원] 님의 말 (오전 10:18) :  
네
오석근[차장] 님의 말 (오전 10:18) :  
그 블럭수까지 합한거
링크보면 그래서 object 수로 어림 잡고
정호준[사원] 님의 말 (오전 10:19) :  
아아
저는 다른의미의 object를 말씀하시는줄알았어요
정호준[사원] 님의 말 (오전 10:20) :  
네임노드콘솔에 나와있는 값 말씀하시는거군요
오석근[차장] 님의 말 (오전 10:20) :  
ㅇㅇ
근데 그 디렉토리에 19만건은 전체 file and directory 15565993의 1%도 안되는데
정호준[사원] 님의 말 (오전 10:20) :  
아 그 추가된
디렉토리가
5개가 더 있대요..
정호준[사원] 님의 말 (오전 10:21) :  
다 다른 디렉토리로
구성이되어있는데
오석근[차장] 님의 말 (오전 10:21) :  
아하
전화
오석근[차장] 님의 말 (오전 10:26) :  
네임노드를
http://greatkim91.tistory.com/74
요 유틸로 봐서
Full GC가 계속 일어나고 있으면
메모리가 또 부족한게 맞고
오석근[차장] 님의 말 (오전 10:27) :  
아니고 minor gc만 일어나면
크게 문제 없을듯
정호준[사원] 님의 말 (오전 10:28) :  
오...감사합니당+ㅜ
오석근[차장] 님의 말 (오전 10:28) :  
호준씨 실전으로 무장되어가고 있삼 흐흐~
정호준[사원] 님의 말 (오후 4:46) :  
차장님
정호준[사원] 님의 말 (오후 4:47) :  
저 스쿱관련해서 메일 보내드렸는데요ㅎㅎ
그것과 별개로 오전에 블록 파일 많아서 오류난 곳이요
sbp에서 getmerge 로 blockfile을 줄이는건 불가능한가요?
오석근[차장] 님의 말 (오후 4:49) :  
스쿱은 아직 못봤고
getmerge는 뭔지 첨 듣는데
스쿱은 일단 키 쫑안나게 해서는 문제 없는지 보고... 일단 그렇게 쓰라고 하고
정호준[사원] 님의 말 (오후 4:49) :  
아..
잘못조사했네요.ㅠㅠ로컬파일에
떨구는 명령어래요...
정호준[사원] 님의 말 (오후 4:50) :  
merge해서
오석근[차장] 님의 말 (오후 4:50) :  
에러 나면 왜 행이 걸리는지는 구글링 하던지 oozie 로그를 한땀한땀 살펴봐야 할듯
오석근[차장] 님의 말 (오후 4:51) :  
어떻게 사용하는지 우리는 모르니 그쪽 보고 비즈에 영향 안가게 다시 설계해서 올리라해
정호준[사원] 님의 말 (오후 5:12) :  
넵ㅎㅎ알려주신내용 참고해서 메일 보냈습니다. 감사합니당
정호준[사원] 님의 말 (오후 5:13) :  
금요일 5시네요
오석근[차장] 님의 말 (오후 5:13) :  
ㅇㅇ 주말 잘 보내고~ 11월에 만나자고 ㅋㅋ
정호준[사원] 님의 말 (오후 5:13) :  
얼른 서울 올라오셔서
가족분들하고 좋은 주말되세용
오석근[차장] 님의 말 (오후 5:13) :  
^^