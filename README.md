# wsl 신규 설치시 ubuntu setup

## oh-my-zsh pyenv 설치로 초기 설정

### oh-my-zsh 설치 및 플러그인, 테마 설치

- 첫번째, apt 업데이트 & 업그레이드

```bash
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get autoremove
&& sudo apt-get autoclean
```

- 두번째, zsh 설치

```bash
sudo apt update && sudo apt install -y zsh
```

- 세번째, oh-my-zsh 설치

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- 네번째, oh-my-zsh 플러그인 설치

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
```bash
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
```
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-syntax-highlighting
```bash
vi ~/.zshrc
```
zshrc에 플러그인 추가
``` bash
plugins=(
        git
        zsh-autosuggestions
        zsh-completions
        zsh-syntax-highlighting
)
```
플러그인 적용
```bash
source ~/.zshrc
```

- powerlevel10k 테마 설치 및 적용
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```
```bash
vi ~/.zshrc
```
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```
```bash
source ~/.zshrc
```
### pyenv 설치 및 python, virtualenv 설치

- 첫번째, pyenv 설치

```bash
curl https://pyenv.run | bash
```

- pyenv 환경변수 추가 및 적용용

```bash
vi ~/.zshrc
```
```bash
export PYENV_ROOT="$HOME/.pyenv"
command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```
```bash
source ~/.zshrc
```

- 에러 발생시 디펜던시 설치 (높은 확률로 필수)

```bash
sudo apt-get update && sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git
```

- 파이선 버전 설치

```bash
pyenv install 3.13.3
```

- 파이선 버전 전역 설정정

```bash
pyenv global 3.13.3
```

- 가상화화 python 설치
pyenv virtualenv 3.13.3 myenv
```bash
pyenv virtualenv 3.13.3 myenv
```

- 가상화 파이선 지역 설정(폴더 내에서 실행 시 해당 폴더 및 하위 폴더)

```bash
pyenv local myenv
```