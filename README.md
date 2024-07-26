### <p align = center>2024 Techeer Summer BootCamp <p>
<div align=center>
<br> <image width=50%, height=50%, src="서비스이미지요">


<br>💫 와라랄 그럴듯한 멘트로 서비스 소개 💫
##### URL : https://person-a.site
</div>

## 🔮 Table of Contents
- [Medium](#-Medium)
- [Demo](#-Demo)
- [System Architechture](#-System-Architechture)
- [Tech stack](#-Tech-stack)
- [ERD](#-Erd)
- [MongoDB](#-MongoDB)
- [API](#-API)
- [Flow Chart](#-Flow-Chart)
- [Sequence Diagram](#-Sequence-Diagram)
- [Monitoring](#-Monitoring)
- [File Directory](#-file-directory)
- [Directory Structure](#-Directory-Structure)
- [How to Start](#-How-to-Start)
- [Member](#-Member)



## 📝 Medium 
https://medium.com/@angal2310/siliconvalley-summer-bootcamp-person-a-e12d2177d349

## ✨ Demo
|로그인 & 회원가입|
|------|
|그림1|
|인격선택|
|그림2|
|채팅|
|그림3|
|상담일지|
|그림4|
|인기순위|
|그림5|

## 🏢 System Architechture
<img src="https://github.com/user-attachments/assets/bc756677-37da-445d-b05b-45952b49ce3d">

## 💻 Tech stack

## 🗺️ ERD
<img src="https://github.com/user-attachments/assets/49ee725f-b121-4827-bd1b-d6fd26de2855">

## 📚 MongoDB
<img src="https://github.com/user-attachments/assets/545875d6-52ea-4609-b267-b2fa180f4064">

## 📄 API 
<img src="https://github.com/user-attachments/assets/84cf1ce4-56bf-4a8a-8b18-889b5434e5e4">
<img src="https://github.com/user-attachments/assets/9d6c0342-4bf0-42b6-876b-71631085afd1">

## 🪐 Flow Chart
<img src="https://github.com/user-attachments/assets/c6590de5-ad2a-461b-a526-ed08689560c8">

## 📊 Sequence Diagram
<img src="https://github.com/user-attachments/assets/f60ba003-ca2b-4e2b-8e64-8b827e32b249">

## 🧑🏻‍💻 Monitoring

## 📂 Directory Structure
<details>
    <summary>Backend</summary>
<pre>
<code>

📦backend
┣📦prometheus
┃┗ 📜metrics.js
┣📦src
┃┣ 📂config
┃┃ ┣ 📜config.js
┃┃ ┣ 📜openAiConfig.js
┃┃ ┣ 📜sequelize.js
┃┃ ┗ 📜sttConfig.js
┣┣ 📂controllers
┃┃ ┣ 📜aiController.js
┃┃ ┣ 📜personController.js
┃┃ ┣ 📜speechController.js
┃┃ ┣ 📜summaryController.js
┃┃ ┣ 📜userController.js
┃┃ ┗ 📜userSelectionController.js
┃┣ 📂migrations
┃┃ ┗ 📜20240709070544-create-user-and-person-tables.js
┃┣ 📂models
┃┃ ┣ 📜chatLogModel.js
┃┃ ┣ 📜index.js
┃┃ ┣ 📜openAiModel.js
┃┃ ┣ 📜person.js
┃┃ ┣ 📜ttsModel.js
┃┃ ┣ 📜user.js
┃┃ ┗ 📜userselection.js
┃┣ 📂prompt
┃┃ ┣ 📜defaultPrompt.json
┃┃ ┣ 📜luckyPrompt.json
┃┃ ┣ 📜mzPrompt.json
┃┃ ┣ 📜picturePrompt.json
┃┃ ┣ 📜simonPrompt.json
┃┃ ┣ 📜solutionPrompt.json
┃┃ ┣ 📜summaryPrompt.json
┃┃ ┗ 📜twentyQPrompt.json
┃┣ 📂routes
┃┃ ┣ 📜aiRoutes.js
┃┃ ┣ 📜personRoutes.js
┃┃ ┣ 📜summaryRoutes.js
┃┃ ┣ 📜userRoutes.js
┃┃ ┗ 📜userSelectionRoutes.js
┃┣ 📂service
┃┃ ┣ 📜imageService.js
┃┃ ┣ 📜openAiService.js
┃┃ ┣ 📜personService.js
┃┃ ┣ 📜summaryService.js
┃┃ ┣ 📜userSelectionService.js
┃┃ ┗ 📜userService.js
┃┣ 📂socket
┃┃ ┗ 📜chat.js
┃┗ 📜.DS_Store
┣📦swagger
┃┣ 📜swagger-output.json
┃┗ 📜swagger.js
┣📜.env
┣📜.gitignore
┣📜.sequelizerc
┣📜app.js
┣📜docker-compose.yml
┣📜Dockerfile
┣📜Jenkinsfile
┣📜package-lock.json
┣📜package.json
┣📜README.md
┣📜start.sh
┗📜wait-for-it.sh

</code>
</pre>
</details>


<details>
    <summary>Frontend</summary>
<pre>
<code>

📦frontend
┣📦dist
┃┣ 📂assets
┃┃ ┣ 📜index-DVoHNO1Y.js
┃┃ ┣ 📜index-DiwrgTda.css
┃┃ ┗ 📜react-CHdo91hT.svg
┃┣ 📜index.html
┃┗ 📜vite.svg
┣📦public
┃┣ 📜persona.png
┃┗ 📜vite.svg
┣📦src
┃┣ 📂assets
┃┃ ┣ 📂png
┃┃ ┃ ┣ 📜backbutton.png
┃┃ ┃ ┣ 📜book.png
┃┃ ┃ ┣ 📜click.png
┃┃ ┃ ┣ 📜download.png
┃┃ ┃ ┣ 📜fact.png
┃┃ ┃ ┣ 📜leemal.png
┃┃ ┃ ┣ 📜leemalback.png
┃┃ ┃ ┣ 📜logo.png
┃┃ ┃ ┣ 📜logpersona.png
┃┃ ┃ ┣ 📜lucky.png
┃┃ ┃ ┣ 📜luckyback.png
┃┃ ┃ ┣ 📜mz.png
┃┃ ┃ ┣ 📜mzback.png
┃┃ ┃ ┣ 📜newcharacter.png
┃┃ ┃ ┣ 📜page.png
┃┃ ┃ ┣ 📜pen.png
┃┃ ┃ ┣ 📜persona.png
┃┃ ┃ ┣ 📜pront.png
┃┃ ┃ ┣ 📜share.png
┃┃ ┃ ┣ 📜uncle.png
┃┃ ┃ ┣ 📜uncleback.png
┃┃ ┃ ┣ 📜upButton.png
┃┃ ┃ ┣ 📜worry1.png
┃┃ ┃ ┣ 📜worry2.png
┃┃ ┃ ┗ 📜worry3.png
┃┃ ┣ 📂svg
┃┃ ┃ ┣ 📜closeIcon.svg
┃┃ ┃ ┣ 📜leftarrow.svg
┃┃ ┃ ┣ 📜mic.svg
┃┃ ┃ ┗ 📜send.svg
┃┃ ┣ 📂tts
┃┃ ┃ ┣ 📜leemalTTS.mp3
┃┃ ┃ ┣ 📜luckyTTS.mp3
┃┃ ┃ ┣ 📜mzTTS.mp3
┃┃ ┃ ┗ 📜uncleTTS.mp3
┃┃ ┣ 📜ShootingStarsComponent.tsx
┃┃ ┣ 📜StarBackground.tsx
┃┃ ┣ 📜initCharacter.ts
┃┃ ┣ 📜react.svg
┃┃ ┗ 📜styles.tsx
┃┣ 📂chating
┃┃ ┣ 📂component
┃┃ ┃ ┣ 📜LoadingModal.tsx
┃┃ ┃ ┣ 📜TypingWaiting.tsx
┃┃ ┃ ┣ 📜chatingStyles.tsx
┃┃ ┃ ┗ 📜logstyles.tsx
┃┃ ┣ 📜Chat.tsx
┃┃ ┣ 📜ChatComponents.tsx
┃┃ ┣ 📜socket.tsx
┃┃ ┗ 📜stt.tsx
┃┣ 📂main
┃┃ ┣ 📜App.tsx
┃┃ ┣ 📜Login.tsx
┃┃ ┣ 📜RotatingCharacters.tsx
┃┃ ┣ 📜StarField.tsx
┃┃ ┣ 📜index.css
┃┃ ┣ 📜index.tsx
┃┃ ┣ 📜loginAPI.tsx
┃┃ ┣ 📜mainstyles.tsx
┃┃ ┗ 📜signupAPI.tsx
┃┣ 📂select
┃┃ ┣ 📜Select.tsx
┃┃ ┣ 📜cardstyles.tsx
┃┃ ┣ 📜selectAPI.tsx
┃┃ ┣ 📜selectmodalAPI.tsx
┃┃ ┗ 📜selectstyles.tsx
┃┣ 📂topselect
┃┃ ┣ 📜BarChart.tsx
┃┃ ┣ 📜TopSelect.tsx
┃┃ ┣ 📜topselectAPI.tsx
┃┃ ┗ 📜topselectstyles.tsx
┃┣ 📜App.css
┃┣ 📜App.tsx
┃┣ 📜index.css
┃┣ 📜main.tsx
┃┗ 📜vite-env.d.ts
┣📜.gitignore
┣📜docker0compose.yml
┣📜Dockerfile
┣📜Jenkiunsfile
┣📜package.json
┣📜README.md
┣📜tsconfig.app.json
┣📜tsconfig.json
┣📜vite.config.json
┗📜yarn.lock

</code>
</pre>
</details>

## 💌 How to Start
### Backend 
```
git clone --recursive https://github.com/2024-SUMMER-BOOTCAMP-TEAM-A/backend.git
```
### env setting in the Backend folder
* backend/.env
```
MYSQL_ROOT_PASSWORD=
MYSQL_ROOT_PASSWORD=
MYSQL_DATABASE=
MYSQL_USER=
MYSQL_PASSWORD=
MYSQL_HOST=
NODE_ENV=
TZ=

OPENAI_API_KEY=
CLOVA_API_KEY=
CLOVA_CLIENT_ID=
JWT_SECRET=
REFRESH_TOKEN_SECRET=

MONGO_INITDB_ROOT_USERNAME=
MONGO_INITDB_ROOT_PASSWORD=
MONGOEXPRESS_LOGIN=
MONGOEXPRESS_PASSWORD=
MONGO_LOCAL_URL=
MONGODB_DOCKER_URL=
ELEVENLABS_API_KEY=

GOOGLE_CLOUD_PROJECT=
GCLOUD_STORAGE_BUCKET=
GCP_TYPE=
GCP_PROJECT_ID=
GCP_PRIVATE_KEY_ID=
GCP_PRIVATE_KEY=
GCP_CLIENT_EMAIL=
GCP_AUTH_URI=
GCP_TOKEN_URI=
GCP_AUTH_PROVIDER_X509_CERT_URL=
GCP_CLIENT_X509_CERT_URL=
GCP_UNIVERSE_DOMAIN=

ELASTIC_PASSWORD=
LOGSTASH_INTERNAL_PASSWORD=
```
### Run Docker
```
docker-compose up -d --build
```
### Frontend
```
git clone --recursive https://github.com/2024-SUMMER-BOOTCAMP-TEAM-A/frontend.git
```
### Install
```
nvm use 20.0.0
yarn add
```

### Run
```
yarn dev
```

## 👪 Member

| Name  | <center>윤정은</center> | <center>김민지</center> | <center>김종연</center> | <center>임승제</center> | 
| :----- | :---------------------------------------: |:----------------------------------:| :---------------------------------------: | :----------------------------------------: | 
| Profile | <center><img width="100px" height="100px" src="https://github.com/2023-Winter-Bootcamp-Team-J/.github/assets/113340283/b07082d0-28f9-442a-9e8d-d46aeed4f9d4" /></center>|<center><img width="100px" height="100px" src="https://github.com/user-attachments/assets/bdb0da06-6ac3-4356-a4bd-482a5375dd54" /></center>|<center><img width="100px" height="100px" src="https://github.com/user-attachments/assets/831ef8d1-0674-42dd-88ac-dd2cb2eb90ae" /></center>|<center><img width="100px" height="100px" src="https://github.com/user-attachments/assets/a663dcf4-e128-4112-a1eb-58d040a1e81f" /></center>| 
| role    | <center> Team Leader <br> Backend <br> Frontend <br> DevOps </center>   | <center> Backend <br> Frontend <br> DevOps </center>  | <center> Backend <br> Frontend <br> DevOps </center>  | <center> Frontend <br> Backend </center> |
| GitHub | <center>&nbsp;&nbsp;&nbsp;[@jungeunyooon](https://github.com/jungeunyooon)&nbsp;&nbsp;&nbsp;</center> | <center>&nbsp;[@songwol38](https://github.com/songwol38)&nbsp;</center>| <center>&nbsp;&nbsp;&nbsp;&nbsp;[@qsc6543](https://github.com/qsc6543)&nbsp;&nbsp;&nbsp;&nbsp;</center>| <center>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[@seungje1217](https://github.com/seungje1217)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</center> |

