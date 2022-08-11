# ~/tmux.conf

Mi configuración de tmux

# para que funcione el cipiar Pegar
```
brew install reattach-to-user-namespace
```

# Esto va en mi archivo .zshrc 
```
function tat {
  name=$(basename `pwd` | sed -e 's/\.//g')
   if tmux ls 2>&1 | grep "$name"; then
     tmux attach -t "$name"
   elif [ -f .envrc ]; then
     direnv exec / tmux new-session -s "$name"
   else
     tmux new-session -s "$name"
   fi
 }
 ````

#Tmux plugin manager
```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```
### Con el prefijo, en este caso control + x y luego Shift + i se instalan los plugins, con Shift + u Se actualizan
