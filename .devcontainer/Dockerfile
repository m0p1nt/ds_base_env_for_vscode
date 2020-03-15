FROM python:3.7.5

# "debconf: delaying package configuration, since apt-utils is not installed"
# の警告メッセージを表示させなくするための環境変数設定
# 表示されても特に問題はないが、不必要な警告メッセージは誤解を招くため表示させない
ENV DEBCONF_NOWARNINGS yes

RUN apt-get update && apt-get install -y unzip sudo

# Python関連環境変数を設定
ENV LANG ja_JP.UTF-8
ENV PYTHONIOENCODIND utf_8

# 開発用sudo権限ユーザ作成・切り替え
RUN groupadd -g 1000 developer && \
    useradd  -g      developer -G sudo -m -s /bin/bash devusr && \
    echo 'devusr:devusr1' | chpasswd

RUN echo 'Defaults visiblepw'             >> /etc/sudoers
RUN echo 'devusr ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER devusr

CMD ["bin/bash"]