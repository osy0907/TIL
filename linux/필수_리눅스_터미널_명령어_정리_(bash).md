>[필수 리눅스 터미널 명령어 | Bash]를 핵심만 정리한 내용 입니다.

# 필수 리눅스 터미널 명령어 정리 | Bash

### man : (manual, users manual)

- 명령어는 무엇인지 모르겠다, 어떤 옵션들을 함께 써야하는지 모르겠다. 할 때 사용.

ex) man man : 매뉴얼에 대한 매뉴얼 (설명, 어떤옵션들이 있는지 들어있음.) 나갈 때는 q를 입력하면 됨. 아마quit의 약자인가?

ex) man touch : touch명령어의 매뉴얼을 모르겠다. 할 때 사용

---

### clear

- 터미널에 있는 모든 텍스트를 깔끔하게 청소해주는 명령어

ex) man clear : 클리어에 대한 매뉴얼을 확인

---

## Navigating file system ( 파일 시스템 탐색하기 )

터미널에서 어떻게 폴더와 파일을 탐색할 수 있는지

### pwd : (print working directory)

- 내가 현재 있는 곳의 전체 경로를 프린트 해주는 명령어.
- 서버에서 로그를 남기거나 스크립트를 작성할 때도 자주 사용.

---

### open .

현재 경로에 어떤 폴더와 파일들이 있는지 ui(파일탐색기)로 볼 수 있는 명령어

---

### ls : list

- 현재 디렉토리 안에 들어있는 폴더와 파일들을 확인

### ls 폴더 or 파일이름.

- 특정한 폴더 안에 있는 내용들을 보고 싶을 때. ls +폴더 or 파일이름.

### ls -l : (long format)

- 파일에 대해서 조금 더 자세한 내용들을 보고싶을 때 사용 (파일이름, 사이즈, 언제 수정이 되었는지, 그리고 파일을 소유하고 있는 오너도 확인 가능)

### ls -a : (all)

- ls -a ui상에서는 보여지지 않는 숨겨져있는 파일이나 디렉토리도 보고싶을 때.

### ls -la : (long format + all)

- 이렇게 함께 묶어서 옵션을 줄 수도 있음.

---

### cd : (change directory)

- 현재에 있는 경로의 위치를 변경할 때 사용

### cd .

- .(dot)은 현재 디렉토리를 나타내기 때문에 아무런 디렉토리 체인지 없음.

### cd ..

- 상위 디렉토리로 이동

### cd ~

- 현재 설정된 사용자의 홈 디렉토리로 이동 (최상위 경로로 이동)

### cd -

- 바로 이동 이전 경로로 이동

---

### find

- 파일시스템에서 특정한 파일이나 디렉토리를 찾을 때 사용

ex) 현재에 있는 경로와 하위에 있는 모든 폴더에 한해서 모든 텍스트 파일을 찾고싶다면?

find . -type file -name "*.txt" → find 현재 경로에서 부터 시작해서 type은 file이고 이름은 모든 파일인데 확장자가 txt인 파일을 찾아라.

find . -type file -name "*.json", find . -type directory -name "*2" 등

---

### which

- 내가 지금 실행하고자 하는 프로그램이 어디에 설치되어있는지 어디에 설정되어져있는지 경로를 확인할 때 사용

ex) which node → 노드의 실행경로를 확인해볼 수 있다.

which code → vscode의 경로를 확인해볼 수 있다.

---

### . : (dot)

1.  숨김(히든) 파일을 만들때 사용
    .profile 이러면 ls 에서 안보이고 ls -a 옵션을 줘야 보임
2.  쉘의 환경변수를 바꿀 때 사용
    . ~/.profile 이러면 현재 환경변수를 ~/.profile에 설정된 값으로 변경
    이 때 앞의 . 은 source의 축약된 표시
3. 현재 경로(디렉토리)를 나타냄
   ./configure 이러면 현재 /home/oseb/Packages/ffmpeg이라고 하면
   /home/oseb/Packages/ffmpeg/configure 라고 하는 걸 줄여서 표시하는 겁니다
   부록으로 .. 두 개는 상위 디렉토리를 나타냄

---

### / : (enter)

- It means enter.

---

## 파일 생성 및 관리하기 (create and manage files)

파일을 만들고 경로를 만들고 파일을 복사하고 이동하고 삭제하고, 모든 파일에 한해서 키워드로 검색하는 유용한 명령어

ui탐색기가 아니라 터미널을 사용하는 가장 큰 장점중에 하나가 마우스를 사용하지 않고 빠르게 일들을 처리하고 확인할 수 있는게 아닌가? 터미널을 사용하다보면 파일이나 경로를 만들거나 또는 파일안에 있는 내용들을 빠르게 확인할 필요가 있다.

### touch 원하는 파일명

- touch + 원하는 파일명 새로운 파일을 만들 수 있다.

### cat 파일명

- 파일안에 있는 내용들을 빠르게 확인할 수 있다.

ex) cat new_file1.txt,

cat new_file1.txt new_file2.txt (파일명 연속해서 가능) → 모든파일의 컨텐츠를 한번에 확인

### echo 문자열

- 문자열을 터미널에 메아리 처럼 출력할 수 있다. 메아리 처럼??

ex) echo "hello world"

echo "hello world" > new_file3.txt → ehcho 옆에 있는 문자열을 오른쪽에 있는 새로운 파일을 만들면서 컨텐츠로 직접 넣어준다.

주의할 것이 위의 예시에서 **>** 키워드를 쓰면 문자열을 그대로 새롭게 덮어씌워 주는 그런 기능을 하고 있음.

**>>** 키워드를 쓴다면 덮어쓰지 않고 뒤에 추가하고 싶다. 뒤에다가 붙이고 싶을 때.

---

### mkdir : (make directory)

- 디렉토리를 만들 수 있다.

ex) mkdir dir3 → 새로운 폴더, 음..경로가 만들어 진 것임.

mkdir -p dir4/subdir1/subdir2 → 한 번에 서브 디렉토리 까지 만들고 싶을 때 즉, 중간중간 필요한 디렉토리를 한번에 생성 가능.

---

## 파일관리명령어 3가지

### cp : (copy)

- 파일을 복사

ex) cp file1.txt dir1/ → 파일1.txt를 dir1으로 복사.

### mv : (move)

- 파일을 이동

ex) mv file2.txt dir2/ → 파일2.txt를 dir2로 이동

mv file1.txt file2.txt → (cp 원하는파일 대상파일) cp or mv 모두 경로가 아니라 새로운 파일로 복사, 이동하고 싶다

### rm : (remove)

- 파일을 삭제

ex) rm file2.txt

rm dir2 → 경고 왜? rm -r dir2 이렇게 recursive하게 하위에 있는 것들도 다 삭제하도록 해줘야함.

---

### grep : (global regular expression print)

- 코딩을 할 때 한 파일 안에서 키워드로 검색하거나 프로젝트 전체에 한해서 키워드로 검색할 경우 사용.

ex) grep "world" *.txt → grep 다음 검색하고자 하는 키워드 작성 특정한 파일안에서 or 특정한 확장자를 가진 모든 파일에서

grep -n "world" *.txt → (-n : line number) "world"가 정확히 몇 번째 줄에 있는지 확인하고 싶다면 사용

grep -ni "world" *.txt (-i : insensitive) 대, 소문자 상관없이 검색하고 싶을 때

grep -nir "world" . (-r : recursive) 현재 경로에서 특정 키워드가 포함되어 있는 것을 전부 검색하고 싶을 때

---

## 환경 변수 설정하기 (Work with environment variables)

환경 변수 : 내 컴퓨터에서 키워드가 어떠한 일을 하거나 경로를 저장할 수 있도록 만든다.

### export 환경변수=값

- 내 컴퓨터상에 변수를 설정할 수 있다.
- 환경 변수는 보통 대문자로 단어 사이의 구분자는 밑의 대쉬(_)를 이용. 관례같은 것

ex) export MY_DIR="dir"

---

### unset 환경 변수

- 환경 변수 제거하고 싶을 때

---

### env

- 설정된 모든 환경 변수를 보고 싶을 때 사용

---

### $ + 환경 변수

- 환경 변수 사용 시 $ 이용.

ex) cd $MY_DIR

## 참고

### vi or vim

- terminal에서 이용되는 text editor
- vi, vim은 터미널 뿐만 아니라 vscode or intelliJ 등에서도 자주 사용
  터미널에서 git을 사용하거나 어떤 특정한 파일을 수정할 때 vim 이용

### :w (write changes)

- 저장

### :q (quit)

- 종료

### :q! (!는 강제)

- 저장하지 않고 강제로 종료하겠다.