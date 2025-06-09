

https://github.com/nikitabobko/AeroSpace

Usefull zsh script to find & launch requred app from CLI in fuzzy style:
```sh 
aa() {
  aerospace list-windows --all \
    |fzf --bind  'enter:execute(bash -c "aerospace focus --window-id {1}")+abort'
}
```


Window manager workflow:
```sh
1. Launch app using cmd + space
2. Example sublime app is open - launch second app firefox it launheex next to sublime
3. If needed move to its own workspace with ctrl + shift + num
4. To change wihch is active app - option(alt) + ;  (3 dots colorfull - not gray) 
5. If there are multiple apps in the same worspace but you think they are one after anoter 
    alt + E will tile them next to eaxh ather 
6. To resize active app enter in resize mode alt + r (R appears) 
- H reduces size
- L increases size 
esc exits resize mode


If required using ~/.config/skhd and aerospace config file app can be launced with custom shortcut:
- alt + T - terminal and it will go to first workspace
- alt + W - web browser it will go to workspace 2 etc

In airospace.toml config can be enforced that app will go 100% to specified workspace examples: https://github.com/vfedotovs/.config
```

MacOS shortcuts:
```sh
- To close active app:  cmd + Q
- To exits/enter application fullscreen: cmd + ctrl + F
```

Chrome shortcuts:
```sh
- Create new tab: cmd + T 
- Close current tab: comd + W 
- Jump to tab cmd + num
- Jump to enter URL field: cmd + L
```

