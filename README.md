# docker-oa

## WINDOWS

### 下載 Docker-Windows
---
+ https://www.docker.com/docker-windows

### 安裝方法
---
1. 安裝 docker (完成後內含 docker-compose)
2. docker 請求 Hyper-v 權限 (需重新登入，且其他虛擬機會無法使用)
3. docker 請求個人密碼
4. Settings/Shared Drives/C&D 打勾

### 專案配置
---
1. D:\ 新增 NYD 資料夾
2. D:\NYD> git clone https://github.com/liucjray/docker-oa.git
	
### 專案配置結構
---
1. oaoa.local.conf - OA vhost
2. docker-compose.yaml - docker-compose 配置檔

### 配置專案容器方法
---
1. 修改本地端 hosts 檔案並加入 127.0.0.1 oaoa.local
2. D:\{$GIT CLONE PATH}> git clone https://github.com/liucjray/docker-oa.git
3. 進入 D:\{$GIT CLONE PATH}\docker-oa\webdevops\php-nginx-dev_centos-7-php56
4. 輸入 docker-compose up
5. 瀏覽器輸入 http://oaoa.local

### 移除專案容器方法
---
1. 進入 D:\{$GIT CLONE PATH}\docker-oa\webdevops\php-nginx-dev_centos-7-php56
2. 輸入 docker-compose stop #停止容器
3. 輸入 docker-compose rm -f #移除容器

### 進入專案容器方法
---
1. 開啟 Windows Power Shell
2. docker ps -a
3. docker exec -it {$CONTAINER_ID} bash

### 修改 WINDOWS 環境下 container 80 port 對應至 host 8888
1. 系統管理員身分執行 Windows Power shell
2. 修改 host 偵聽 8888 port 並轉送至 80 port
   > netsh interface portproxy add v4tov4 listenport=80 listenaddress=127.0.0.1 connectport=8888 connectaddress=127.0.0.1

### 查詢 portproxy
---
+ netstat -a -n -p TCP | findstr "LISTENING"

### 加入 portproxy
---
+ netsh interface portproxy add v4tov4 listenport=80 listenaddress=127.0.0.1 connectport=8888 connectaddress=127.0.0.1

### 移除 portproxy
---
+ netsh interface portproxy delete v4tov4 listenport=80 listenaddress=127.0.0.1
