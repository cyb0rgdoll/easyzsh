## Install Zsh</a></h2>
<p>Depending on your platform (I use Termux for Android, Debian for Raspberry pi and Kali on Windows Subsystem for
Linux - WSL) you can install Zsh with the following:</p>
<pre class="language-bash"><!-- HTML_TAG_START --><code class="language-bash"><span class="token function">sudo</span> <span class="token function">apt</span> <span class="token function">install</span> <span class="token function">zsh</span></code><!-- HTML_TAG_END --></pre>
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

nano ~/.zshrc
```



<h2 id="oh-my-zsh-configuration"><a href="#oh-my-zsh-configuration">Oh My Zsh configuration</a></h2>
<p>So if we take a look at my current configuration

```

# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.

if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# Set name of the theme to load --- 

ZSH_THEME="powerlevel10k/powerlevel10k" 

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.

plugins=(git thefuck history command-not-found zsh-autosuggestions zsh-syntax-highlighting zsh-completions)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
 export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
   export EDITOR='nano'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.

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
