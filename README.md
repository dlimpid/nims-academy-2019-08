# 제5회 국가수리과학연구소 산업수학 아카데미

## 컴퓨터 계산 환경 설정

개인 랩탑(Windows/Mac OS)에 계산 환경을 설정하는 방법 안내입니다.

:warning: Linux 사용자이거나, 이미 본인이 관리하여 사용하고 있는 Python 환경이 있으신 경우 아카데미 진행 중 필요한 패키지만 설치하셔서 사용하셔도 무방합니다.

:warning: Windows의 사용자 이름에 한글이 들어가면 제대로 동작하지 않는 경우가 있습니다.
그럴 경우 **사용자 이름**만 바꿔서는 기존의 **사용자 폴더 이름**은 바뀌지 않으므로 Miniconda를 다른 곳(예: C:\\Miniconda3 혹은 C:\\opt\\Miniconda3 등)에 설치해 보세요.

:warning: 설치할 때 특별한 이유가 없는 한 옵션값을 바꾸지 말고 초기 상태대로 두고 설치하세요.

- :white_check_mark: "Just Me (recommended)" **선택**
- :white_large_square: "Add Anaconda to my PATH environment variable" **선택하지 않기**

:warning: 아래 실행 중 2.i에서 Windows 시작 메뉴에 Anaconda3, Anaconda prompt 등이 생성되지 않는 경우, [아래](#windows에서-anaconda-재설치시-시작-메뉴에-anaconda-prompt가-만들어지지-않는-경우)를 참고해 보세요.

1. Miniconda 설치

    Anaconda나 Miniconda를 이미 설치한 경우에는 이전 버전으로 깔았더라도 재설치할 필요가 없이 "2. Conda 업데이트" 항목부터 하시면 됩니다.

    설치한 적이 없는 경우 <https://docs.conda.io/en/latest/miniconda.html> 페이지에서 Python 3.7 version 중 자신의 운영체제에 맞는 파일을 받아 설치합니다.

2. Conda 업데이트

    1. 터미널(Anaconda prompt) 실행

        - Windows: 시작 -> Anaconda3 (64-bit) -> Anaconda Prompt (Miniconda3)
        - Mac: Launchpad -> 터미널

        Note: 명령줄은 OS나 환경에 따라 `(base) C:\Users\myid>`, `bash3.2$`, `MacBook:~$`, `>` 등 다양한 형식으로 보일 수 있습니다. 아래 입력을 따라할 때에는 `$` 표시 다음 부분만 입력하면 됩니다.

    2. 명령어 실행

        ```sh
        (base) $ conda update -n base -c defaults -y conda
        ```

    3. **터미널을 닫았다가 재실행**

    4. 제대로 업데이트되었는지 확인(4.7 이상)

        ```sh
        (base) $ conda --version
        conda 4.7.11
        ```

3. 자료 다운로드

    1. 현재 디렉터리 확인

        Anaconda/Miniconda가 실행되는 디렉터리를 확인합니다.

        - Windows

            기본값으로 `C:\Users\myid` 이고, 파일 탐색기에서는 `C:\사용자\myid`로 찾아가야 할 수도 있습니다. 확실하지 않은 경우 터미널을 실행하면 볼 수 있습니다.

            ```sh
            (base) C:\Users\myid>
            ```

        - Mac

            기본값으로 `/Users/myid`이고, 확실하지 않은 경우 터미널에서 `pwd` 명령어로 확인할 수 있습니다.

            ```sh
            (base) $ pwd
            /Users/myid
            ```

    2. 자료 다운로드

        다음 링크를 클릭해서 자료를 다운로드하고, 위 디렉터리에 압축을 풉니다.

        <https://github.com/dlimpid/nims-academy-2019-08/archive/master.zip>

4. 아카데미용 환경 만들기

    1. 터미널(Anaconda prompt) 실행(2.i)

    2. (Windows만 해당) JDK 설치

        1. [JDK를 다운로드 페이지](https://www.oracle.com/technetwork/java/javase/downloads/jdk12-downloads-5295953.html)에서 jdk-12.0.2_windows-x64_bin.exe를 받아 설치합니다.
        (현재 버전은 12.0.2인데, 만약 업데이트가 되어 새로운 버전을 받은 경우, 아래 디렉터리 이름을 맞는 버전으로 설정해 주세요.)

        2. 터미널에서 다음을 입력하여 `JAVA_HOME` 환경변수를 설정합니다.

            ```sh
            (base) $ setx JAVA_HOME "C:\Program Files\Java\jdk-12.0.2\bin\server"

            성공: 지정한 값을 저장했습니다.
            ```

        3. **터미널을 닫았다가 재실행**

    3. 환경 만들기

        다음 명령어를 실행해서 nims-academy 이름의 환경을 만듭니다.

        ```sh
        (base) $ conda env create -f nims-academy-2019-08-master/environment.yml
        ```

        마지막에 다음과 비슷한 메시지가 나왔으면 제대로 설치된 것입니다.

        ```plain
        ...
        done
        #
        # To activate this environment, use
        #
        #     $ conda activate nims-academy-2019-08
        #
        # To deactivate an active environment, use
        #
        #     $ conda deactivate
        ```

5. JupyterLab 실행

    터미널(Anaconda prompt)을 연 후 다음을 실행합니다.
    `jupyter lab` 명령어를 입력하기 전 명령줄 앞에 `(nims-academy-2019-08)`이 나오는지 확인해 보세요.

    ```sh
    (base) $ conda activate nims-academy-2019-08
    (nims-academy-2019-08) $ jupyter lab
    ```

6. 설치 확인

    웹 브라우저에서 JupyterLab이 열리면 nims-academy-2019-08-master 디렉터리에 있는 environment-test.ipynb를 열고 Run -> Run All Cells를 실행하여

    - 모든 셀이 문제 없이 실행되는지(첫 번째나 두 번째 셀에서 오류가 나는 경우 5번의 `conda activate nims-academy-2019-08`을 실행했는지 확인)
    - 그림에 한글이 잘 출력되는지(끝까지 실행되지 않고 중간에 에러가 나는 경우 notebook 내의 설명을 참고하여 글꼴 이름 바꾸기)

    확인해 봅니다.

---

## 참고 사항

### 기존 환경 삭제 방법

1. 터미널(Anaconda prompt) 실행

2. 다음 명령어 실행

    ```sh
    (base) $ conda remove -n nims-academy-2019-08 --all
    ```

### 다른 디렉터리에서 JupyterLab 실행하기

기본으로 시작하는 홈 디렉터리가 아닌 다른 디렉터리나 다른 드라이브에서 JupyterLab을 실행하고 싶은 경우 디렉토리를 이동한 후 `jupyter lab`을 실행하거나, 옵션으로 지정해 줄 수 있습니다.

#### 방법 1: 디렉토리 이동

Windows와 Mac 모두 `cd` 명령어로 이동할 수 있습니다.

```sh
(nims-academy-2019-08) C:\Users\myid> cd c:\path\to\go
(nims-academy-2019-08) C:\path\to\go> jupyter lab
```

Windows에서 다른 드라이브로 이동할 때에는 드라이브도 바꿔 주어야 합니다.

```sh
(nims-academy-2019-08) C:\Users\myid> d:
(nims-academy-2019-08) D:\> cd path\to\go
(nims-academy-2019-08) D:\path\to\go> jupyter lab
```

#### 방법 2: 옵션으로 지정하기

`--notebook-dir` 옵션으로 시작 디렉터리를 지정할 수 있습니다.

```sh
(nims-academy-2019-08) jupyter lab --notebook-dir="C:\path\to\go"
```

### Windows에서 Anaconda 재설치시 시작 메뉴에 Anaconda prompt가 만들어지지 않는 경우

1. 제어판에서 "Miniconda3 ?.?.? (Python ...)"이나 "Python ?.?.? (Anaconda3 ...)"을 삭제
2. C:\\Users\\myid\\Anaconda3\\ 혹은 C:\\Users\\myid\\Miniconda3\\가 남아있으면 삭제
3. <kbd>Windows</kbd> + <kbd>r</kbd>을 누르고 "regedit" 실행
4. HKEY_CURRENT_USER\\Software\\Microsoft\\Command Processor를 찾아가서 AutoRun, REG_EXPAND_SZ, "C:\\Users\\myid\\Anaconda3\\condabin\\conda_hook.bat" 항목이 있으면 삭제
5. 재부팅한 후 재설치
