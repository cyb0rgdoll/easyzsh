Install Zsh</a></h2>
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
<h2 id="oh-my-zsh-configuration"><a href="#oh-my-zsh-configuration">Oh My Zsh configuration</a></h2>
<p>So if we take a look at my current configuration, it’s a bit sparse
