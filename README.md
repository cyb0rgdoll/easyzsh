


## Install Zsh</a></h2>
<p>Depending on your platform, I use Termux for Android, Debian for Raspberry Pi and Kali on Windows Subsystem for Linux - WSL).. you can install Zsh with the following:</p>
<pre class="language-bash"><!-- HTML_TAG_START --><code class="language-bash"><span class="token function">sudo</span> <span class="token function">apt</span> <span class="token function">install</span> <span class="token function">zsh</span></code><!-- HTML_TAG_END --></pre>


<p> If you're on Android using Termux, install by typing:</p>pkg install zsh

<p>If you’re on macOS and use Brew you can install Zsh with the
following:</p>
<pre class="language-bash"><!-- HTML_TAG_START --><code class="language-bash">brew <span class="token function">install</span> <span class="token function">zsh</span></code><!-- HTML_TAG_END --></pre>

<h2 id="install-oh-my-zsh"><a href="#install-oh-my-zsh">Install Oh My Zsh</a></h2>
<p>Zsh has a framework that you can use with it called <a href="https://ohmyz.sh/" rel="noopener noreferrer" target="_blank">Oh My Zsh</a> this
adds a lot of functionality to the shell, more on this in the guide.</p>
<p>Installing Oh My Zsh is as simple as:</p>
<pre class="language-bash"><!-- HTML_TAG_START --><code class="language-bash"><span class="token function">sh</span> <span class="token parameter variable">-c</span> <span class="token string">"<span class="token variable"><span class="token variable">$(</span><span class="token function">curl</span> <span class="token parameter variable">-fsSL</span> https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh<span class="token variable">)</span></span>"</span></code><!-- HTML_TAG_END --></pre>
<p>Once installed you will have a <code>~/.zshrc</code> file that you can edit to
add additional functionality to the shell.</p>
<p>The <code>~</code> here represents the home directory of your current logged in
user. So if you were to do <code>cd ~</code> you would be in your home directory.</p>
<p>One of the joys of Zsh is that many commands are contextual so the
<code>cd ~</code> can be shortened to <code>~</code>.</p>
<p>Another nice one is changing directories, in bash you’d need to
<code>cd ..</code> to go back a directory. In Zsh you can use <code>..</code> to go back a
directory. To go back three directories you can use <code>...</code>.</p>
<p>Anyway, the <a href="https://github.com/ohmyzsh/ohmyzsh/blob/master/templates/zshrc.zsh-template" rel="noopener noreferrer" target="_blank">default <code>.zshrc</code> file</a> is filled with helpful comments to
guide you through its usage.</p>
<p>If you <code>cat</code> out the contents of the <code>.zshrc</code> (with <code>cat ~/.zshrc</code>)
file you’ll see something similar to what I just linked.</p>
<p>You can edit the <code>.zshrc</code> file with your text editor of choice, I use
<code>nano</code> but you can use any text editor, VS Code even, use
<code>code ~/.zshrc</code> from the terminal to start editing with VS Code.</p>

## [Install Powerlevel10k](https://github.com/romkatv/powerlevel10k) 

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

>>> Basic quick zsh install instructions 

## Install with curl

```sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"```

## Enabling Plugins (zsh-autosuggestions & zsh-syntax-highlighting)

Install git first

apt install git [Linux; Ubuntu, Kali]
pkg install git [Termux and others]
brew install git [MacOS]

Download zsh-autosuggestions by typing:

```git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions```

Download zsh-syntax-highlighting by typing:

```git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting```

```nano ~/.zshrc find plugins=(git)``` 

(this is to edit your zsh configuration profile that's in your current root/home directory)

>>> Add zsh-autosuggestions & zsh-syntax-highlighting to plugins() like this

```plugins=(git zsh-autosuggestions zsh-syntax-highlighting)```


<h2 id="oh-my-zsh-configuration"><a href="#oh-my-zsh-configuration">Oh My Zsh configuration</a></h2>
<p>So if we take a look at my current configuration (modify or add as much you like that suits you and your terminal) ```.zshrc```

```

# -- [ Basic WSL2 Detection ] --
is_wsl() {
  grep -qiE "(microsoft|wsl)" /proc/version
}

# -- [ Gitstatus crash fix ] --
export GITSTATUS_LOG_LEVEL=OFF
export POWERLEVEL9K_DISABLE_CONFIGURATION_WIZARD=true
export POWERLEVEL9K_INSTANT_PROMPT=quiet

# -- [ Theme / Oh My Zsh ] --
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="powerlevel10k/powerlevel10k"

plugins=(
  git
  z
  zsh-autosuggestions
  zsh-syntax-highlighting
  docker
  command-not-found
  history-substring-search
  sudo
  extract
  man
)

source $ZSH/oh-my-zsh.sh

# -- [ Instant prompt cache ] --
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# -- [ Language + Editor ] --
export LANG=en_US.UTF-8
export EDITOR='nano'

# -- [ LS Color scheme ] --
export LS_COLORS="rs=0:no=00:di=01;34:ln=01;36:so=01;33:pi=01;33:ex=01;32"

# -- [ Default directory on launch ] --
cd ~/panda

# -- [ PATH Purification for WSL2 ] --
if is_wsl; then
  export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:$HOME/.local/bin:$HOME/bin"
fi

# -- [ PYENV Setup ] --
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# -- [ Conda Setup (WSL-compatible)] --
if [[ -f "$HOME/miniconda3/etc/profile.d/conda.sh" ]]; then
  source "$HOME/miniconda3/etc/profile.d/conda.sh"
  conda activate base
fi

# -- [ Golang Setup ] --
export GOROOT="/usr/local/go"
export GOPATH="$HOME/go"
export PATH="$GOPATH/bin:$GOROOT/bin:$PATH"

# -- [ Neofetch on start ] --
neofetch

# -- [ Syntax Highlighting + Completion ] --
autoload -U compinit && compinit

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

source ~/powerlevel10k/powerlevel10k.zsh-theme
source "$ZSH/oh-my-zsh.sh"

# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
```

**Change your default shell**

```
chsh -s $(which zsh)
```

You must log out from your user session and log back in to see this change.

Initialize your new zsh configuration

Once you open up a new terminal window, it should load zsh with your editted Oh My Zsh's configuration.
