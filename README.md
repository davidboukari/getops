# getops

## Learn by the example

* mandatory arguments followed by ':'
* vV not followed by ':' =>  optionals

```bash
while getopts "a:c:vV" option
do
  case $option in
    c)
      changeLog
      exit 0
      ;;
    a)
      myParam="$OPTARG"
      ;;
    v|V)
      version
      exit 0
    ;;
  esac
done

echo  "-> myParam=$APP"
```
