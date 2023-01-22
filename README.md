```ps
# powershell
Remove-Item -Recurse -Force build; cmake -B build -G Ninja ; ninja -C build
```