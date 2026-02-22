
1.**헤더 파일**
 (A)**입출력 및 시스템 관련**
  (1)<iostream> - cin,cout,endl 등 표준 입출력을 담
  (2)<fstream> - 파일 읽기/쓰기(ifstream, ofstream)를 할 때 사용. 게임의 세이브 데이터를 만들 때 필수
  
 (B)자료구조 관련
  (1) <vector> - 동적 배열, 크기가 자유롭게 변하는 배열로 실무에서 많이 쓰임
  (2) <stack> - LIFO 구조의 스택
  (3) <queue> - FIFO 구조의 큐와 우선순위 큐(priority_queue)가 들어있음.
  (4) <deque> - 앞뒤 양방향에서 모두 넣고 뺌.
  (5) <list> - 연결 리스트(Linked List)
  (6): <map> / <unordered_map> - 해시테이블과 트리구조. 키-값(Key-Value)형태로 데이터저장.
  
(C)알고리즘 및 수학 관련
 (1) <algorithm> - (std::sort),(binarn_search),(max),(min) 등 함수들이 다수 들어있음. 
 (2) <cmath> - pow(거듭제곱), sqrt(제곱근), abs(절대값) 등 수학 공식들이 들어있음.
 (3) <ctime> - 시간 관련 기능 제공 게임에서 랜덤 시드값 줄 때 자주 사용.

(D)문자열 및 기타
 (1) <string> - std::string 객체를 다룸
 (2) <memory> - 스마트 포인터(unique_ptr, shared_ptr)를 지원. 메모리 누수를 막을때 사용
 
2. 스택(Stack) - LIFO(후입선)
-가장 나중에 들어온 데이터가 가장 먼저 나간다
stack<int> s;
s.push(10); // 데이터 추가
s.push(20); // 데이터 추가
s.top(); // 맨 위 데이터 확인 (출력: 20)
s.pop(); // 맨 위 데이터 삭제 (반환값 없음!)
s.size(); // 데이터 개수 확인
s.empty(); // 비어있는지 확인 (비었으면 1, 아니면 0)

// 주의: 비어있을 때 top()이나 pop()을 호출하면 에러 발생!
if(!s.empty()) cout << s.top();

return 0;

3. 큐(Queue) - FIFO(선입선출)
-먼저 들어온 데이터가 먼저 나간다
queue<int> q;
q.push(10); // 데이터 추가 (뒤로 들어감)
q.push(20); 
q.front(); // 맨 앞(제일 먼저 들어온) 데이터 확인 (출력: 10)
q.back(); // 맨 뒤(방금 들어온) 데이터 확인 (출력: 20)
q.pop(); // 맨 앞 데이터 삭제
q.size(); // 개수 확인
q.empty(); // 비었는지 확인

4.덱(Deque) - 양방향 큐()
-앞, 뒤 양쪽에서 넣고 뺄 수 있음. std::vector보다 앞쪽 데이터 삭제가 훨씬 빠르다.
deque<int> dq;
dq.push_front(10); // 앞으로 넣기
dq.push_back(20); // 뒤로 넣기
dq.pop_front(); // 앞에서 빼기
dq.pop_back(); // 뒤에서 빼기
dq.front(); // 맨 앞 확인
dq.back(); // 맨 뒤 확인

5.우선순위 큐(Priority Queue)
데이터를 넣으면 자동으로 정렬되어 가장 큰 값or작은 값이 항상 맨 위에 옴.+A* 알고리즘의 핵심

// 기본은 내림차순 (큰 값이 위로)
priority_queue<int> pq;

pq.push(10);
pq.push(30);
pq.push(20);
pq.top() : 가장 우선순위가 높은(큰) 값 확인
cout << pq.top() << endl; // 출력: 30
pq.pop(); // 30 삭제

6.벡터(vector)

 (1)선언 및 초기화
 std::vector<int> v1; // 비어있는 벡터 생성

 std::vector<int> v2(N); // 크기가 N이고 모든 원소가 0으로 초기화된 벡터
 std::vector<int> v3(N, 7); // 크기가 N이고 모든 원소가 7로 초기화된 벡터
 std::vector<int> v4 = {1, 2, 3, 4, 5}; // 값을 직접 넣어서 생성
 
 (2)데이터 넣고 빼기
 
 v.push_back(10); // 맨 뒤에 10 추가
 v.push_back(20); // 맨 뒤에 20 추가
 v.pop_back(); //맨 뒤의 데이터 삭제 (20 삭제)
 v.clear(); // 모든 원소 삭제(크기는 0이 됨)
 
 (3)데이터 접근 및 확인 

 std::vector<int> v = {10, 20, 30}; // 이름이 v인 vector 생성 (원소는 10, 20, 30)
 v[0]; //0번 인덱스 접근
 v.at(1); // 1번 인덱스 접근(20, 범위 체크를 해서 v[1]보다 안전)
 v.front(); //맨 앞 원소 반환 (10)
 v.back(); //맨 뒤 원소 반환(30);

 v.size(); //현재 들어있는 원소 개수 반환
 v.empty(); //비어있으면 true, 아니면 false 반환
 
 (4) 정렬 및 탐색
 
 std::vector<int> v = {3, 1, 4, 1, 5};
 std::sort(v.begin(), v.end()); // 오름차순 정렬
 std::sort(v.rbegin(), v.rend()); // 내림차순 정렬
 bool found = std::binary_search(v.begin(), v.end(), 4); // 4를 찾는 이분탐색(반드시 정렬 후 사용)
 auto it = std::find(v.begin(), v.end(), 3); // 특정 값의 위치(Iterator) 찾기

(5) C++ 입출력 가속기

std::ios::sync_with_stdio(false);
장점:cin과 cout의 속도를 scanf/printf 급으로 향상
단점:이 코드를 쓰면 printf, scanf, getchar, puts 등 C언어 계열 입출력 함수 사용불가.

std::cin.tie(NULL);
입력받기전 매번 출력을 확인하는 과정을 생략해 응답속도가 최적화.

(6)\n과 std::endl의 비교

\n
-속도가 빠름
-데이터가 버퍼에만 쌓여있어서 갑자기 프로그램이 죽으면 로그가 손실됨
-알고리즘 문제나 대량 데이터 처리할때 좋음

std::endl
-매번 버퍼를 비우기 때문에 속도가 느림
-출력이 즉시 기록되어 안전함
-디버깅이나 실시간 시스템,소량 출력할때 좋음

