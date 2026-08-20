> [!warning] Never run bash scripts without reading through them first to make sure there is no malicious code.

DaVinci Resolve comes with older glib files because it's made for RHEL binary distros still on version 8-9 which rely on older glibs. I've written a bash script to archive them.
1. Copy this code into a text file and save it as `resolve_fix.sh`  in `~/Documents`.
	1. You can also just copy this directly into the terminal and hit enter, but it won't stay open to tell you the results.
2. Right click on it and select Properties -> Permissions -> `Enable` Allow executing file as a program.
3. In a terminal, `cd Documents`
4. `./resolve_fix.sh`
5. Close Terminal. You should be able to start Davinci Resolve properly now.

```bash
#!/usr/bin/env bash
set -euo pipefail

LIBDIR="/opt/resolve/libs"

cd "$LIBDIR"

FILES=(
    libglib-2.0.so
    libglib-2.0.so.0
    libglib-2.0.so.0.6800.4

    libgobject-2.0.so
    libgobject-2.0.so.0
    libgobject-2.0.so.0.6800.4

    libgio-2.0.so
    libgio-2.0.so.0
    libgio-2.0.so.0.6800.4

    libgmodule-2.0.so
    libgmodule-2.0.so.0
    libgmodule-2.0.so.0.6800.4
)

for file in "${FILES[@]}"; do
    if [[ -e "$file" && ! -e "$file.bak" ]]; then
        mv "$file" "$file.bak"
        echo "Backed up bundled library: $file -> $file.bak"
    elif [[ -e "$file.bak" ]]; then
        echo "Already backed up: $file.bak"
    else
        echo "Not found: $file"
    fi
done
```

### List of old glibs to be archived
1. libglib-2.0.so
2. libglib-2.0.so.0
3. libglib-2.0.so.0.6800.4
4. libgobject-2.0.so
5. libgobject-2.0.so.0
6. libgobject-2.0.so.0.6800.4
7. libgio-2.0.so
8. libgio-2.0.so.0
9. libgio-2.0.so.0.6800.4
10. libgmodule-2.0.so
11. libgmodule-2.0.so.0
12. libgmodule-2.0.so.0.6800.4