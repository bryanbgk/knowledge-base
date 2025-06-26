# 🧰 Instalação do Oh My Posh no Windows

- [Site de suporte para instalação](https://rafaelwms.com.br/2024/06/05/oh-my-posh-turbine-seu-powershell/)

## 1. Instalar font

- https://www.nerdfonts.com/font-downloads

- Escolha uma font e baixe

- Descomprima toda a pasta

- Selecione os arquivos de font (ex: .ttf/.otf)

## 2. Instale via Winget (recomendado)

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

## 3. Criar arquivo $profile

```powershell
new-item -type file -path $profile -force
```

```powershell
notepad $PROFILE
```

### Config
```txt
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\free-ukraine.omp.json" | Invoke-Expression
```

## 4 (Opicional). Ajustar Políticas de Execução

```powershell
Set-ExecutionPolicy -ExecutionPolicy Unrestricted
```