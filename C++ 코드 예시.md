
1.**헤더 파일**
 (A)**입출력 및 시스템 관련**
  (1) iostream - cin,cout,endl 등 표준 입출력을 담
  (2) fstream - 파일 읽기/쓰기(ifstream, ofstream)를 할 때 사용. 게임의 세이브 데이터를 만들 때 필수
  
 (B)자료구조 관련
  (1)  vector - 동적 배열, 크기가 자유롭게 변하는 배열로 실무에서 많이 쓰임
  (2)  stack  - LIFO 구조의 스택
  (3)  queue - FIFO 구조의 큐와 우선순위 큐(priority_queue)가 들어있음.
  (4)  deque - 앞뒤 양방향에서 모두 넣고 뺌.
  (5)  list - 연결 리스트(Linked List)
  (6): map / <unordered_map> - 해시테이블과 트리구조. 키-값(Key-Value)형태로 데이터저장.
  
(C)알고리즘 및 수학 관련
 (1) algorithm  - (std::sort),(binarn_search),(max),(min) 등 함수들이 다수 들어있음. 
 (2)  cmath - pow(거듭제곱), sqrt(제곱근), abs(절대값) 등 수학 공식들이 들어있음.
 (3)  ctime - 시간 관련 기능 제공 게임에서 랜덤 시드값 줄 때 자주 사용.

(D)문자열 및 기타
 (1)  string  - std::string 객체를 다룸
 (2)  memory  - 스마트 포인터(unique_ptr, shared_ptr)를 지원. 메모리 누수를 막을때 사용
 
**2. 스택(Stack) - LIFO(후입선출출)**
-가장 나중에 들어온 데이터가 가장 먼저 나간다 
stack\<int> s;'
s.push(10); //
s.push(20); // 데이터 추가
s.top(); // 맨 위 데이터 확인 (출력: 20)
s.pop(); // 맨 위 데이터 삭제 (반환값 없음!)
s.size(); // 데이터 개수 확인
s.empty(); // 비어있는지 확인 (비었으면 1, 아니면 0)

// 주의: 비어있을 때 top()이나 pop()을 호출하면 에러 발생!
'if(!s.empty()) cout << s.top();'

return 0;

**3. 큐(Queue) - FIFO(선입선출)**
-먼저 들어온 데이터가 먼저 나간다
queue\<int> q;
q.push(10); // 데이터 추가 (뒤로 들어감)
q.push(20); 
q.front(); // 맨 앞(제일 먼저 들어온) 데이터 확인 (출력: 10)
q.back(); // 맨 뒤(방금 들어온) 데이터 확인 (출력: 20)
q.pop(); // 맨 앞 데이터 삭제
q.size(); // 개수 확인
q.empty(); // 비었는지 확인

**4.덱(Deque) - 양방향 큐()**
-앞, 뒤 양쪽에서 넣고 뺄 수 있음. std::vector보다 앞쪽 데이터 삭제가 훨씬 빠르다.
deque\<int> dq;
dq.push_front(10); // 앞으로 넣기
dq.push_back(20); // 뒤로 넣기
dq.pop_front(); // 앞에서 빼기
dq.pop_back(); // 뒤에서 빼기
dq.front(); // 맨 앞 확인
dq.back(); // 맨 뒤 확인

**5.우선순위 큐(Priority Queue)**
데이터를 넣으면 자동으로 정렬되어 가장 큰 값or작은 값이 항상 맨 위에 옴. + A 알고리즘의 핵심

// 기본은 내림차순 (큰 값이 위로)
priority_queue\<int> pq;

pq.push(10);
pq.push(30);
pq.push(20);
pq.top() : 가장 우선순위가 높은(큰) 값 확인
cout << pq.top() << endl; // 출력: 30
pq.pop(); // 30 삭제

**6.벡터(vector)**

 (1)선언 및 초기화
 std::vector\<int> v1; // 비어있는 벡터 생성

 std::vector\<int> v2(N); // 크기가 N이고 모든 원소가 0으로 초기화된 벡터
 std::vector\<int> v3(N, 7); // 크기가 N이고 모든 원소가 7로 초기화된 벡터
 std::vector\<int> v4 = {1, 2, 3, 4, 5}; // 값을 직접 넣어서 생성
 
 (2)데이터 넣고 빼기
 
 v.push_back(10); // 맨 뒤에 10 추가
 v.push_back(20); // 맨 뒤에 20 추가
 v.pop_back(); //맨 뒤의 데이터 삭제 (20 삭제)
 v.clear(); // 모든 원소 삭제(크기는 0이 됨)
 
 (3)데이터 접근 및 확인 

 std::vector\<int> v = {10, 20, 30}; // 이름이 v인 vector 생성 (원소는 10, 20, 30)
 v\[0]; //0번 인덱스 접근
 v.at(1); // 1번 인덱스 접근(20, 범위 체크를 해서 v[1]보다 안전)
 v.front(); //맨 앞 원소 반환 (10)
 v.back(); //맨 뒤 원소 반환(30);

 v.size(); //현재 들어있는 원소 개수 반환
 v.empty(); //비어있으면 true, 아니면 false 반환
 
 (4) 정렬 및 탐색
 
 std::vector\<int> v = {3, 1, 4, 1, 5};
 std::sort(v.begin(), v.end()); // 오름차순 정렬
 std::sort(v.rbegin(), v.rend()); // 내림차순 정렬
 std::sort(v.begin(), v.end(), A); // A는 정렬의 룰(어떤식으로 정렬할지 함수 등 사용)
 bool found = std::binary_search(v.begin(), v.end(), 4); // 4를 찾는 이분탐색(반드시 정렬 후 사용)
 auto it = std::find(v.begin(), v.end(), 3); // 특정 값의 위치(Iterator) 찾기

**5. C++ 입출력 가속기**

std::ios::sync_with_stdio(false);
장점:cin과 cout의 속도를 scanf/printf 급으로 향상
단점:이 코드를 쓰면 printf, scanf, getchar, puts 등 C언어 계열 입출력 함수 사용불가.

std::cin.tie(NULL);
입력받기전 매번 출력을 확인하는 과정을 생략해 응답속도가 최적화.

**6.\n과 std::endl의 비교**

\n
-속도가 빠름
-데이터가 버퍼에만 쌓여있어서 갑자기 프로그램이 죽으면 로그가 손실됨
-알고리즘 문제나 대량 데이터 처리할때 좋음

std::endl
-매번 버퍼를 비우기 때문에 속도가 느림
-출력이 즉시 기록되어 안전함
-디버깅이나 실시간 시스템,소량 출력할때 좋음

**7.const 상수**

ex) bool compare(const Point& a, const Point& b) { ... }
const 코드가 있다면 const는 이 함수 내에서 상수기 때문에 절대 변할수없음.
만약 a=10 이런식으로 코드를 짜면 에러가 뜬다.

**8.구조체**

// 1. 점을 나타내는 구조체 정의
struct Point { // (x,y) 좌표를 담는 구조체
    int x;
    int y;
};

// 2. 정렬 기준 함수 (비교 함수)
// a가 b보다 앞에 와야 하면 true를 반환함
bool compare(const Point& a, const Point& b) { //a라는 상자에 x,y가 들어있고 b라는 상자에도 x,y가 들어있다고 생각하자 a(x,y) b(x,y)
    if (a.x == b.x) {      // 1순위: x좌표가 같다면
        return a.y < b.y;  // y좌표가 작은 게 앞으로 (오름차순)
    }
    return a.x < b.x;      // x좌표가 작은 게 앞으로 (오름차순)
}

(1)은 a.x \== b.x라면 a.y와 b.y를 비교해서 더 작은 숫자가 앞으로 가게함(오름차순)
내림차순은 return a.y > b.y;


9. void A(int x) { }

10.컨테이너 생성 및 응용

**11.컨테이너 응용**

(1)완전 전달
 (a)push_back - 삽입 : 이미 만들어진 객체를 벡터 안으로 밀어넣음
 -함수 외부에서 생성된 객체를 매개변수로 받아서 벡터 내부 메모리 공간에 그 값을 복사하거나 이동시켜 저장
 이미 있는 걸 넣을때 사용(가독성 우수)

(b)emplace_back -직접 생성 : 벡터의 메모리 공간 안에서 객체를 직접 만듦.
-객체를 전달하는 것이 아닌, 객체를 만드는데 필요한 **재료(인자)**\만 전달. 벡터는 자신의 빈 공간에서 생성자를 직접 호출해 객체를 완성.
ex)총알이나 몬스터 객체를 수천 개 생성해서 리스트에 담을때 사용하면 메모리 복사비용을 줄임
새로 만들어서 넣을 때 사용(복사 비용 절약)

(c)reserve() - 미리 N개만한 메모리 공간을 한 번에 잡아둠
-N번의 데이터를 넣는동안 공간이 모자랄 일이 없으므로 이사를 가지 않아 성능이 향상됨
push_back이나 emplace_back 전에 사용

**코드 예시**

vector\<Member> members;
int N = 100000;

// 1. reserve(N) : "이사 가기 싫으니까 미리 10만 칸 예약해!" 
members.reserve(N); 

for(int i = 0; i < N; i++) {
	members.emplace_back(age, name, i); // 2. emplace_back : "따로 안 만들 테니까 이 재료들
}거기서 바로 조립해!" 



Member m1(25, "Gemini", 100001);// 3. push_back : "이미 만들어진 데이터(m1)가 있으니까 이
members.push_back(m1); 건 그냥 집어넣어!"

**12.설계 패러다임(Design Paradigm)** 
=>공학이나 프로그래밍에서 **문제를 바라보고 해결하는 근본적인 사고의 틀이나 방식**
구체적인 기술보다는 이런 종류의 문제는 이런 시각으로 접근하는게 정답이다

-알고리즘과의 차이
알고리즘은 *레시피*로 김치찌개를 끓일 때 김치를 먼저 볶고 물을 부어라 같은 구체적인 순서
설계 패러다임은 일식 스타일인가 한식 스타일인가 중식 스타일인가 같은 전체적인 방향성

(1)분할과 정복(Divide and Conquer):문제를 일단 반으로 쪼갠다 (ex)병합 정렬
(2)탐욕법(Greedy):지금 당장 눈앞에 최선인 것만 고른다(ex)거스름돈 줄 때 큰 동전부터


(3)**동적 계획법(DP, Dynamic Programming)**
=>큰 문제를 작은 문제로 쪼개서 했던 답과 계산은 기억해뒀다가 다시 써먹는 것
사용 이유 - 피보나치 수열 등을 일반적인 재귀로 풀면 엄청난 낭비가 발생
why? - f(5)를 구하려면 f(4)와 f(3)가 필요한데 f(4)를 구한 과정에서 또 f(3)이 필요하므로
해결법 - 배열(Table)로 결과를 배열에 저장해서 똑같은 계산이 필요하면 배열에서 꺼내씀

DP를 쓸 수 있는 2가지 조건

(A)**최적 부분 구조(Optimal Substructure)**
=>작은 문제들의 정답을 이어 붙였을 때, 전체 문제의 정답이 되는 구조
ex)서울에서 대전을 거쳐 부산으로 가는 가장 빠른 길 구하기
(서울에서 대전 가는 길) + (대전에서 부산 가는 길) = (서울에서 대전을 거쳐 부산 가는 길)

(B)**중복되는 부분 문제(Overlapping Subproblems)**
=>큰 문제를 풀기 위해 작은 문제들로 쪼갰는데, 그 작은 문제들이 계속 똑같이 반복해서 등장함
ex)피보나치 수열 -> 5번째 숫자를 구하려면 3,4번째 숫자를 알아야하고 4번째 숫자를 구하려면 2,3번째 숫자를 알아야함.

vector<int> dp(100) - 100칸짜리 빈 배열 준비
dp[1] = 1; -> 1번째 칸은 1
dp[2] = 2; -> 2번째 칸은 2
for (int i = 3; i <= 10; i++) {}
	dp[i] = dp[i-1] + dp[i-2];
} -> dp[1]과 dp[2]를 기억해두고 활용함.

13. min과 max 알고리즘.
	두 숫자 중에서 더 작은 숫자를 골라줌
(1) 비교하고 싶은 게 2가지일 때
min(a,b)

(2) 비교하고 싶은 게 여러개 일 때
int x = 50;
int y = 20;

min({x, y, 10, 5}) - 중괄호 {} 로 묶어주기.

