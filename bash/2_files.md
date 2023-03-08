# Bash #


## Files ##

### Loading Order ###

1.  `/etc/profile`
2.  `~/.bash_profile` (if it exists)
3.  `~/.bash_login` (if it exists)
4.  `~/.profile`
5.  `~/.bashrc`

---

### What do the files do ###

<dl>
   <dt>/bin/bash
          <dd>The bash executable
   <dt>/etc/profile
          <dd>The systemwide initialization file, executed for login shells
   <dt>/etc/bash.bashrc
          <dd>The systemwide per-interactive-shell startup file
   <dt>/etc/bash.bash.logout
          <dd>The systemwide login shell cleanup file, executed when a login shell exits
   <dt>~/.bash_profile
          <dd>The personal initialization file, executed for login shells
   <dt>~/.bashrc
          <dd>The individual per-interactive-shell startup file
   <dt>~/.bash_logout
          <dd>The individual login shell cleanup file, executed when a login shell exits
   <dt>~/.inputrc
          <dd>Individual readline initialization file


---

### /etc/profile ###

System-wide startup file for a login shell

