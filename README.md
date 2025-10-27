## 🏃‍♂️ 로컬 개발 환경 실행 방법 (필독!)

1.  **환경 변수 파일 생성**

    Next.js는 `.env.local` 파일을 우선적으로 읽습니다. `.env.example` 파일을 복사하여 `.env.local` 파일을 생성하세요.

    ```bash
    cp .env.example .env.local
    ```

2.  **환경 변수 확인**

    방금 생성한 `.env.local` 파일에 `NEXT_PUBLIC_API_URL=http://localhost:3000` 값이 올바르게 입력되어 있는지 확인합니다. (이 주소는 로컬에서 실행 중인 백엔드 API 서버를 가리킵니다.)

3.  **Docker 컨테이너 실행**

    Docker Desktop이 실행 중인지 확인한 후, 상황에 맞는 명령어를 사용하세요.

    ### A. 일반적인 실행 (가장 자주 사용)

    Next.js 소스 코드(`.ts`, `.tsx` 파일)만 수정했을 경우에는 이 명령어를 사용합니다.
    컨테이너가 켜진 후, **핫 리로딩** 기능이 파일 변경을 감지하여 서버를 자동으로 재시작합니다.

    ```bash
    docker compose up
    ```

    (서버를 완전히 끄고 정리할 때는 `docker compose down`을 사용합니다.)

    ### B. 이미지를 새로 빌드하며 실행 (중요!)

    **최초 실행 시** 또는 **프로젝트의 '뼈대'가 변경**되었을 때는 `--build` 옵션으로 이미지를 강제로 새로 만들어야 합니다.

    **'뼈대'가 변경되는 경우:**
    * `package.json`에 새 라이브러리를 추가/삭제한 경우 (예: `npm install axios`)
    * `Dockerfile` 자체를 수정한 경우
    * `docker-compose.yml`의 `build:` 관련 설정을 변경한 경우

    docker compose up --build


4.  **서버 확인**

    서버가 `http://localhost:3001`에서 정상적으로 실행됩니다.

    **[ ⚠️ 주의! ]** 백엔드 서버(`3000`)와의 충돌을 피하기 위해, 프론트엔드 서버는 **3001번 포트**를 사용합니다.
