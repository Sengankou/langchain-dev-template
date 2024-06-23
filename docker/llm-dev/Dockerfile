FROM python:3.11

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Asia/Tokyo

EXPOSE 8000
EXPOSE 8080

# 作業ディレクトリの作成
RUN mkdir -p /workspace
# 作業ディレクトリを設定
WORKDIR /workspace


RUN pip install \
    langchain \
    langchain-community \
    langchain-core \
    langsmith \
    langchain-cli \
    "langserve[all]" \
    openai \
    anthropic \
    python-dotenv

RUN pip install jupyter_contrib_nbextensions jupyterlab_code_formatter

# jupyter labの表示バグ対策
RUN pip install ipywidgets==8.0.4

RUN mkdir -p $HOME/.jupyter/lab/user-settings/@jupyterlab/notebook-extension/ \
    && mkdir -p $HOME/.jupyter/lab/user-settings/@jupyterlab/terminal-extension \
    && mkdir -p $HOME/.local/share/code-server/User

# set jupyterlab config  
RUN echo '\n\
{ \n\
    "codeCellConfig": { \n\
        "autoClosingBrackets": true, \n\
        "lineNumbers": true \n\
    } \n\
} \n\
' > $HOME/.jupyter/lab/user-settings/@jupyterlab/notebook-extension/tracker.jupyterlab-settings