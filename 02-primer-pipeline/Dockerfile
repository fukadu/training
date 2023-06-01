FROM ubuntu:22.04

#ポートを開ける
EXPOSE 9864:9864
EXPOSE 8888:8888
EXPOSE 8080:8080

RUN apt update
RUN apt-get update
RUN apt -y upgrade
RUN apt install -y python3-pip
RUN apt-get install -y python3
RUN apt-get update -y

RUN apt install -y curl
RUN curl -o get-pip.py https://bootstrap.pypa.io/get-pip.py
RUN python3 get-pip.py
RUN pip3 install -U pip
RUN pip3 install jupyterlab
RUN export PATH="$HOME/.local/bin:$PATH"
RUN pip3 install numpy==1.19.1
RUN pip3 install pandas==1.1.1
RUN pip3 install python-dateutil==2.8.1
RUN pip3 install pytz==2020.1
RUN pip3 install scipy==1.5.2
RUN pip3 install six==1.15.0
RUN pip3 install xgboost==0.90
RUN pip3 install coverage==5.3.1


RUN apt update
#JAVAをインストールする
RUN apt install default-jdk -y
RUN java --version
#2023jenkinsの鍵をダウンロードする
RUN apt-get install -y wget
RUN wget -qO - https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | apt-key add -
#パッケージ管理コマンドをインストールする
RUN apt-get install -y rpm
#2023jenkinsの鍵をインストールする
RUN rpm --import https://pkg.jenkins.io/redhat/jenkins.io-2023.key
#リポジトリに格納されているjenkins-keyringのアスキーモードのdebフィルをバイナリ―にアップデートする
RUN /usr/share/keyrings/jenkins-keyring.asc and updated /etc/apt/sources.list.d/jenkins.list with:deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/
#URLにアクセスして、Jenkinsのofficial ioキーを現在の場所に追加し、標準入力で　tee \ .のパスを渡す
RUN curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | tee \ .
#RUN /usr/share/keyrings/jenkins-keyring.asc > /dev/null
#ubuntuがコマンドを使うためのJenkinsのリポジトリを追加する
RUN echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
#シェルを起動し、指定したＵＲＬのバイナリのdebファイルへURLパスに格納されたjenkins.listを送り表示する
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
#jenkinsをインストールする
RUN apt install jenkins -y
#サーバーステータス確認用のコマンドをインストールする
RUN apt-get install -y systemctl enable
#jenkinsサーバーの状態を確認
RUN systemctl enable jenkins
#jenkinsサーバーを再起動する
RUN systemctl start jenkins
RUN service jenkins restart
#設定ファイルを開きパスワードをコピーする
RUN apt-get install -y vim
RUN vim /var/lib/jenkins/secrets/initialAdminPassword