# iTerm2 with Oh-My-Zsh
MAC開發必備神器 iTerm2 + Oh My Zsh

iTerm2是一個比mac內建terminal更強大的終端

而Oh My Zsh則是用來管理zsh這個shell的framework

這篇是我看了一些文章之後且實際裝過幾次後的心得與分享(主要是想自己筆記一份)

讓你不用幾分鐘就得到一個漂亮好用的command line環境！

以下是我參考的幾篇文章！大家可以去看看相信也會有不小的收穫！
> * http://www.siguoya.name/pc/home/article/256#%E5%AE%89%E8%A3%85iTerm2
> * https://pjchender.blogspot.tw/2017/02/mac-terminal-iterm-2-oh-my-zsh.html
> * https://medium.com/statementdog-engineering/prettify-your-zsh-command-line-prompt-3ca2acc967f


我把過程分五個步驟！
1. install iterm2
2. install powerline font
3. install zsh
4. install oh my zsh
5. install zsh-completions

***

### 不過首先沒有裝homebrew的話要先去載homebrew...

homebrew有點類似ubuntu的apt，是macOS的package manager

以下都是利用homebrew安裝各式各樣套件

[想了解更多的話官網在這](https://brew.sh/)

或是直接跑這行安裝homebrew...

`$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

***
# 1. install iterm2
 
沒跑過這行要跑一次

`$ brew tap caskroom/cask (下載或更新 <user/repo>)`

安裝iterm2

`$ brew cask install iterm2 (cask 可以直接幫你裝app)`

安裝好以後，打開 iTerm2 檢查 Report Terminal Type 的設定，設定路徑：

Preferences(command+,) -> Profiles -> Terminal -> Report Terminal Type

設為 xterm-256color，才可以看到一堆顏色

![1](https://github.com/htkuan/iTerm2_with_Oh-My-Zsh/blob/master/img/1.png)

再來要修改Color-Schemes(預設很醜，clone下面這包有超多可以選，選幾個喜歡的import到iTerm2裡面，

import之後還要在選import進來的color scheme才算完成!)

https://github.com/mbadolato/iTerm2-Color-Schemes

`$ git clone https://github.com/mbadolato/iTerm2-Color-Schemes`

![2](https://github.com/htkuan/iTerm2_with_Oh-My-Zsh/blob/master/img/2.png)

![3](https://github.com/htkuan/iTerm2_with_Oh-My-Zsh/blob/master/img/3.png)

# 2. install nerd font [https://www.nerdfonts.com/](https://www.nerdfonts.com/)

因為我們要用的Theme會用到很多特殊的icon，所以iTerm2選用的字型必需要支援這種特殊icon字型。

這類型的字體統稱為 [nerd font](https://github.com/ryanoasis/nerd-fonts#option-4-homebrew-fonts)（還有一種叫powerline font也可以,nerd 比較集大成一點)

沒有選用這種字型的話，畫面遇到不支援的icon會變框框問號！

先執行下面這行，才能用 homebrew 安裝字型

`$ brew tap homebrew/cask-fonts`

安裝字型(根據教學後來選用 nerd font)

`$ brew cask install font-jetbrains-mono`

裝完後，記得修改 iTerm2 字型設定否則不會生效。

請改成 JetBrains Mono 或你自己下載的字型，

設定路徑：Preferences -> Profiles -> Text -> Change Font 

![5](https://github.com/htkuan/iTerm2_with_Oh-My-Zsh/blob/master/img/5.png)

![6](https://github.com/htkuan/iTerm2_with_Oh-My-Zsh/blob/master/img/6.png)

# 3. install zsh

安裝 Zsh

`$ brew install zsh`

查看當前系統有哪些shell可以用

`$ cat /etc/shells`

查看當前正在使用的shell

`$ echo $SHELL`

如果當前的shell不是zsh，透過以下指令可以切換shell成zsh

`$ chsh -s /bin/zsh`

重啟後在echo $SHELL 應該就是zsh了，然後就可以來載oh my zsh

# 4. install oh my zsh

[安裝 Oh My Zsh](https://ohmyz.sh/)

`$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

就完成了！ 再來都是多餘的... 看過不少人也喜歡這個預設簡約的 theme

再來可以切換內建的 theme! 很簡單直接修改你的 Zsh 設定檔 ~/.zshrc

把設定檔原本的 ZSH_THEME=”robbyrussell” 改成你想要的：

一般而言很多人會選擇內建的“agnoster”

`ZSH_THEME=”robbyrussell” => ZSH_THEME=”agnoster”`

修改 ZSH_THEME 後，執行以下指令來變更這次改動

`$ exec $SHELL`

### 補:上面文章中推薦的zsh theme “powerlevel9k” (真的很潮)
### powerlevel9k 已經棄用，改由 [powerlevel10k](https://github.com/romkatv/powerlevel10k) 接手

這不是內建的 theme 要去 clone 這一包 theme 下來(在設定到ZSH_THEME)

`$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`

由於 powerlevel10k 推薦用 Meslo Nerd Font(好像有自己的 patch)

`exec $SHELL` or `p10k configure` 他會有完整的提示互動流程幫助你設定，非常猛

結束後以我的觀察是，會輸出 .p10k.zsh 並且在 .zshrc 裡面做引用

.zshrc
```
# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
```

# 5. install zsh-completions

[https://github.com/zsh-users/zsh-completions](https://github.com/zsh-users/zsh-completions)

本人目前覺得這個套件可有可無，所以索性不再更新這個套件
