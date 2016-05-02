aseom.dotfiles
==============

### MacBook Pro

> 잠자기 시 암호 요구 끔  
> 보안 설정에서 자동 로그인 활성화 (사용자 설정 아님!)  
> 입력 메뉴에서 다음 소스 선택에 `Cmd` + `Space` 할당  
> XCode, Homebrew 설치

### Bootstrap
```Shell
cd ~
mkdir .ssh && chmod 700 .ssh
chmod 600 .ssh/*.pem  # After copy ssh keys

# Git SSH Clone without ~/.ssh/config
GIT_SSH_COMMAND="ssh -i [ssh_key_file]" \
    git clone --recursive git@github.com:aseom/dotfiles.git

ln -sf ~/dotfiles/.gitconfig
ln -sf ~/dotfiles/.gitignore_global
ln -sf ~/dotfiles/.ssh/config .ssh
ln -sf ~/dotfiles/bin
```

### Zsh
```Shell
brew install zsh
ln -sf ~/dotfiles/.zsh ~ && ln -sf ~/dotfiles/.zshrc ~

# Manually install
git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
git clone https://github.com/junegunn/fzf.git ~/.fzf

# As default shell
sudo cp -p /etc/shells /etc/shells.backup_
echo $(which zsh) | sudo tee -a /etc/shells
chpass -s $(which zsh)
```

### Vim
```Shell
brew install vim --with-lua  # neocomplete requires lua
ln -sf ~/dotfiles/.vim ~ && ln -sf ~/dotfiles/.vimrc ~

# Plugin reqirements
cd ~/.vim/bundle/tern_for_vim && npm install
pip install grip
```
