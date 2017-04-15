<img src="ASSETS/electron.png" alt="JavaScript">

# Electron 첫번째 어플리케이션 만들기.

## 1. Project폴더 생성 후 package.json 작성하기

앞서 Node.js를 설치 하였기 때문에 **npm init** 명령어가 가능합니다.
커맨드 창에서 프로젝트 경로로 진입 한 후 **npm init -y** 명령어로 기본 package.json 파일을 생성합니다. -y 옵션은 기본값으로 package.json을 생성하는 옵션입니다.

package.json을 생성한 후 아래와 같이 수정합니다(주석 제외, 주석 포함시 에러발생).

**package.json**
```
     {
        "name": "Electron-HelloWorld",
        "version": "1.0.0",
        "description": "",
        "main": "index.js", //엔트리 포인트
        "scripts": {
            "start": "electron ."  // 실행 스크립트
        },
        "author": "suwoni <topspin1278@naver.com>", //리눅스 빌드시 필요함
        "license": "ISC"
    }
```
## 2. Electron 설치

Electron을 아래와 같이 설치합니다.

**Electron 설치**
```
     npm install --save-dev electron
```

## 3. index.js 작성

index.js 파일을 package.json파일과 같은 경로에 아래와 같이 작성합니다.

```
// app모듈과, BrowserWindow 모듈 할당
const {app, BrowserWindow} = require('electron');
let win;

app.on('ready', () =>{
    win = new BrowserWindow(
        {
            width : 800
            , minWidth:330
            , height :500
            , minHeight: 450
            , show: false
            , icon: __dirname + '/resources/installer/Icon.ico'
            , webPreferences :{ defaultFontSize : 14}
        }
    );
    // 창이 ready 상태가되면 보여주기
    win.once('ready-to-show', function(){
        win.show();
    });

    // 윈도우 창에 로드 할 html 페이지
    win.loadURL(`file://${__dirname}/index.html`); //작은 따옴표가 아닌  back stick 기호(tab키 위)
    //__dirname : node.js 전역변수이며, 현재 실행중인 코드의 파일 경로를 나타냄

    //개발자 도구 오픈
   win.webContents.openDevTools();
});
```
## 4. index.html 작성

index.html은 자유롭게 작성합니다.

## 5. 실행
커맨드 창에서 아래의 명령어를 실행합니다.
```
     npm start
```
<img src="ASSETS/screenshot.png">
    
## [Electron 배포 ➤](https://github.com/cionman/03_Electron_Distribution) 


 



