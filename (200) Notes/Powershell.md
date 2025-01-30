Reference of commands:
```powershell
# Move all .zip files to desktop
Get-ChildItem "*.zip" | Move-Item -Path "C:\Users\lain\Desktop"

# check PATH 
$env:PATH -split ';'

# check aliases
Get-Alias aliasname

# PWD
Get-Location
```