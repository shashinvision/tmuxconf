# ~/tmux.conf

Mi configuración de tmux

---

## 🚀 Instalación y uso

### 1. Clonar el repositorio

```bash
git clone https://github.com/shashinvision/tmuxconf.git ~/tmuxconf
```

### 2. Crear un enlace simbólico

Esto permite que tmux use directamente el archivo clonado como configuración:

```bash
ln -s ~/tmuxconf/tmux.conf ~/.tmux.conf
```

> ⚠️ Si ya tienes un `.tmux.conf`, respáldalo primero:

```bash
mv ~/.tmux.conf ~/.tmux.conf.backup
ln -s ~/tmuxconf/tmux.conf ~/.tmux.conf
```

### 3. Recargar configuración de `tmux`

```bash
tmux source-file ~/.tmux.conf
```

O reinicia tmux.

---

## 📋 Copiar y pegar en macOS

Para que funcionen correctamente los atajos de copiar y pegar en macOS:

```bash
brew install reattach-to-user-namespace
```

---

## ⚙️ Función útil para `tmux` en `.zshrc`

Agrega esta función a tu archivo `~/.zshrc` para abrir sesiones tmux nombradas automáticamente según la carpeta actual:

```bash
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
```

---

## 🔌 Tmux Plugin Manager (TPM)

Instala TPM para gestionar plugins fácilmente:

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

### 🧠 Uso de TPM

- `Ctrl + b` luego `Shift + i`: Instala los plugins definidos en `.tmux.conf`
- `Ctrl + b` luego `Shift + u`: Actualiza los plugins

---

¡Listo! Con esto tienes tu configuración de `tmux` al día, con gestión de plugins, soporte para copiar/pegar en macOS y una función útil para sesiones personalizadas. 🧑‍💻🔥
