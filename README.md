

---

### ## Project #1: MyLib

[cite_start]**MyLib**는 커널 라이브러리에서 사용되는 핵심 데이터 구조를 직접 구현해보는 프로젝트입니다. [cite: 9] [cite_start]이를 통해 C 프로그래밍 기술을 향상시키고, 리스트(list), 해시 테이블(hash table), 비트맵(bitmap)의 내부 동작 원리를 이해하는 것을 목표로 합니다. [cite: 10]

**주요 구현 내용:**
* **자료구조 함수 구현:**
    * [cite_start]**List:** 두 리스트 요소를 교환하는 `list_swap`과 리스트 전체를 무작위로 섞는 `list_shuffle` 함수를 구현합니다. [cite: 54, 55, 61]
    * [cite_start]**Hash Table:** 정수 값을 해시 값으로 변환하는 `hash_int_2` 함수를 직접 설계하고 구현합니다. [cite: 69, 70]
    * [cite_start]**Bitmap:** 기존 비트맵을 주어진 크기만큼 확장하는 `bitmap_expand` 함수를 구현합니다. [cite: 78, 80]
* [cite_start]**대화형 테스트 프로그램:** `create`, `delete`, `dumpdata`와 같은 명령어를 인식하여 위에서 구현한 자료구조들을 생성, 삭제, 출력하는 프로그램을 작성합니다. [cite: 11, 22, 23, 24, 25, 26, 27]

---

### ## Project #2: MyShell

[cite_start]**MyShell**은 리눅스 셸(Shell)의 핵심 기능을 단계적으로 구현하며 프로세스 제어, 시그널, 파이프 등 시스템 프로그래밍의 중요 개념을 익히는 프로젝트입니다. [cite: 388, 389]

**주요 구현 내용:**
* **Phase 1: 기본 셸 구현**
    * [cite_start]`fork()`와 `exec()` 시스템 콜을 사용하여 `ls`, `mkdir` 등 기본 명령어를 실행하는 셸을 만듭니다. [cite: 396, 398, 404, 435] [cite_start]`cd`와 `exit`는 부모 프로세스에서 직접 처리합니다. [cite: 404]
* **Phase 2: 파이프와 리다이렉션**
    * [cite_start]두 개 이상의 명령어를 파이프(`|`)로 연결하여, 한 프로세스의 출력이 다음 프로세스의 입력으로 전달되도록 구현합니다. [cite: 452, 456] [cite_start]예를 들어, `ls -al | grep myshell`과 같은 명령어를 처리할 수 있게 됩니다. [cite: 455]
* **Phase 3: 백그라운드 실행 및 작업 제어**
    * [cite_start]명령어 끝에 `&`를 붙이면 해당 작업을 백그라운드에서 실행하도록 구현합니다. [cite: 484, 486] [cite_start]또한 `jobs`, `fg`, `bg`, `kill`과 같은 내장 명령어를 만들어 백그라운드 작업을 제어하는 기능을 추가합니다. [cite: 487, 489, 490, 491, 492]

---

### ## Project #3: Concurrent Stock Server

[cite_start]**Concurrent Stock Server**는 여러 클라이언트의 동시 접속을 처리할 수 있는 주식 거래 서버를 두 가지 다른 동시성 모델로 구현하는 프로젝트입니다. [cite: 571, 581] [cite_start]클라이언트는 서버에 접속하여 주식 정보를 보거나(`show`), 주식을 사고(`buy`), 파는(`sell`) 요청을 보냅니다. [cite: 584, 672] 서버는 이 요청들을 동시에 처리해야 합니다.

**주요 구현 내용:**
* [cite_start]**주식 데이터 관리:** `stock.txt` 파일의 주식 정보를 서버 메모리의 **바이너리 트리(Binary Tree)** 자료구조에 저장하고 관리합니다. [cite: 772, 778, 810] [cite_start]여러 요청이 동시에 주식 수량을 변경할 때 발생할 수 있는 문제를 해결하기 위해 **Readers-Writers Problem**을 고려한 잠금(lock) 기법을 적용해야 합니다. [cite: 822]
* **Task 1: 이벤트 기반(Event-Driven) 동시성 서버**
    * [cite_start]`select()` 함수를 사용하여 다수의 클라이언트 요청을 **하나의 프로세스** 내에서 비동기적으로 처리하는 서버를 구현합니다. [cite: 572, 759]
* **Task 2: 스레드 기반(Thread-Based) 동시성 서버**
    * [cite_start]`pthread` 라이브러리를 사용하여 클라이언트 요청이 들어올 때마다 새로운 스레드를 생성하여 처리하는 다중 스레드 서버를 구현합니다. [cite: 573, 760]
* **Task 3: 성능 비교 분석**
    * [cite_start]두 가지 방식으로 구현된 서버의 성능(처리율)을 클라이언트 수와 요청 유형에 따라 측정하고 비교 분석합니다. [cite: 574, 829]

---

### ## Project #4: Mallocator

[cite_start]**Mallocator**는 C 프로그램의 표준 라이브러리 함수인 `malloc`, `free`, `realloc`을 직접 구현해보는 동적 메모리 할당자 프로젝트입니다. [cite: 197, 198] [cite_start]목표는 정확하고, 빠르며, 메모리 공간을 효율적으로 사용하는 할당자를 만드는 것입니다. [cite: 199]

**주요 구현 내용:**
* [cite_start]**`mm_init()`:** 할당자 사용 전 힙(heap) 영역을 초기화하는 함수입니다. [cite: 208, 214]
* [cite_start]**`mm_malloc(size_t size)`:** 요청된 `size` 만큼의 메모리 블록을 힙 영역 내에서 찾아 할당하고, **8바이트로 정렬된** 포인터를 반환합니다. [cite: 209, 216, 219]
* [cite_start]**`mm_free(void *ptr)`:** 이전에 할당된 메모리 블록을 해제하여 다시 사용할 수 있도록 만듭니다. [cite: 210, 223]
* [cite_start]**`mm_realloc(void *ptr, size_t size)`:** 이미 할당된 메모리 블록의 크기를 변경합니다. [cite: 211, 229]
* [cite_start]**힙 검사기(Heap Checker):** 개발 과정에서 힙의 일관성을 검사하여 버그를 찾는 `mm_check()` 함수를 선택적으로 구현할 수 있습니다. [cite: 239, 247]
