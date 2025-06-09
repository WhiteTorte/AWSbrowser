ASUS WebStorage 폴더/파일 목록 조회 GUI 도구
개요
이 프로젝트는 ASUS WebStorage 클라우드의 내부 API를 활용하여,
특정 폴더의 파일/폴더 목록을 쉽게 조회할 수 있는 Python GUI 툴입니다.
사용자는 v, foid, ow 값을 입력해 버튼 한 번으로 결과를 확인하고, 결과는 JSON 파일로 자동 저장됩니다.

주요 기능
GUI에서 v, foid, ow 값 입력 후, 폴더/파일 목록 조회 가능

목록 결과를 보기 좋게 텍스트 형태로 바로 출력

결과를 JSON 파일(parsed_response.json)로 저장

응답이 JSON이 아닐 경우, 텍스트로 저장(response.txt)

준비물
Python 3.8 이상

주요 라이브러리:

bash
복사
편집
pip install requests
실행 방법
필수 값 준비하기

v: 인증 쿠키의 v 값(로그인 후 F12 Network에서 확인)

foid: 조회할 폴더의 ID(최상위 폴더는 0, 하위 폴더는 Fiddler, Burp Suite 등으로 추출)

ow: 사용자 계정명(필요 시 Network 요청에서 확인)

코드 실행

bash
복사
편집
python main.py
GUI 창이 실행됩니다.

값 입력 및 결과 확인

각 입력란에 v, foid, ow 값을 입력

Send Request 버튼 클릭

하단 스크롤 영역에서 폴더/파일 목록 바로 확인

결과는 parsed_response.json로 저장(텍스트 응답은 response.txt)

예시 입력
v Value: v=kdsf3... (예시)

foid Value: 0 (최상위 폴더) 또는 폴더ID

ow Value: 사용자계정 (예: your@email.com)

출력 예시
yaml
복사
편집
📂 FolderList :
Folder name : Documents | ID: 123456789 | Created Time : 2024-01-01 12:34:56

📄 FileList :
File name : report.pdf | Last ModifyTime : 2024-03-22 15:44:13
File name : photo.jpg | Last ModifyTime : 2024-03-20 12:00:00
위 내용은 parsed_response.json에도 저장됩니다.

참고
SSL 인증서 경고 무시: 테스트 및 리버스 엔지니어링 환경용(실 운영환경 사용 비추천)

내부 API 구조, 파라미터 종류, 값 추출 방법 등은 [Burp Suite, Fiddler] 같은 툴 활용

민감한 인증정보는 외부 공유 주의

문의 및 기여
이 도구 개선/확장에 대한 제안은 이슈로 남겨주세요.










ASUS WebStorage Folder/File Listing GUI Tool
Overview
This project is a Python GUI tool that utilizes the internal ASUS WebStorage API
to easily retrieve and display the file/folder listing of any specified folder.
Simply enter your v, foid, and ow values, and with one click, the tool fetches the results and saves them as a JSON file.

Features
Enter v, foid, and ow values via GUI and fetch the folder/file list instantly

Results are displayed in a user-friendly text format within the app

Results are automatically saved as parsed_response.json

If the response is not JSON, it is saved as plain text (response.txt)

Requirements
Python 3.8 or higher

Required library:

bash
복사
편집
pip install requests
How to Use
Prepare required values

v: The v value from your authentication cookie (check via F12 Network tab after logging in)

foid: The folder ID to browse (top-level folder is 0; subfolders can be found using tools like Fiddler or Burp Suite)

ow: Your account name (find in network requests if necessary)

Run the script

bash
복사
편집
python main.py
The GUI window will launch.

Input values and check results

Enter your v, foid, and ow values into each field

Click the Send Request button

The bottom scrollable area will immediately show the folder/file list

The result will also be saved as parsed_response.json (if plain text, as response.txt)

Example Input
v Value: v=kdsf3... (example)

foid Value: 0 (top-level folder) or your specific folder ID

ow Value: your@email.com

Example Output
yaml
복사
편집
📂 FolderList :
Folder name : Documents | ID: 123456789 | Created Time : 2024-01-01 12:34:56

📄 FileList :
File name : report.pdf | Last ModifyTime : 2024-03-22 15:44:13
File name : photo.jpg | Last ModifyTime : 2024-03-20 12:00:00
The content above is also saved to parsed_response.json.

Notes
SSL certificate warnings are disabled: For testing and reverse engineering only (not recommended for production use)

To extract internal API structure and required parameters, use tools like Burp Suite or Fiddler

Do not share sensitive authentication data with others

Contact / Contributing
Suggestions for improvement or expansion are welcome—please open an issue.

If you need more detailed parameter extraction guidance, screenshots, or further explanations, let me know!

