
Command based.

Usage:
```shell
"init"
dbctl init

"config"
dbctl config set contexts.<context_name>.<attributes> value
dbctl config get-contexts <context_name>
dbctl config use-context <context_name>

"install"
dbctl install
dbctl install -f
dbctl uninstall

"apply"
dbctl apply -f <file_path>
dbctl apply -d <dir>

"get"
dbctl get tables
dbctl get table <table_name>
dbctl get views
dbctl get view <view_name>

"diff"
dbctl diff -d <dir>

"export"
dbctl export -o <json|yaml|html>
dbctl backup -d <dir> 
```