# getops

## ex
```
function usage(){
  echo -e "$0:\n"
  echo -e "Manage the vault\n\n"
  echo "$0 <--app appname> [--env env] <--role-type role-type>"
  echo -e "\n
  ex: $0 --app myappdemo --env tst --role-type read
  ex: $0 --app myappdemo --env tst --role-type readwrite

  role-type: read | readwrite
  "
}

ARGUMENT_LIST=(
  "app"
  "env"
  "role-type"
)


# read arguments
opts=$(getopt \
  --longoptions "$(printf "%s:," "${ARGUMENT_LIST[@]}")" \
  --name "$(basename "$0")" \
  --options "" \
  -- "$@"
)

eval set --$opts
echo $@

while [[ $# -gt 0 ]]; do
  case "$1" in
    --app)
      APP=$2
      shift 2
      ;;

    --env)
      ENV=$2
      shift 2
      ;;

    --role-type)
      # read, readwrite
      ROLE_TYPE=$2
      shift 2
      ;;

    *) echo "else=$1"
       break
      ;;
  esac
done

echo "APP=$APP"
echo "ENV=$ENV"
echo "ROLE_TYPE=$ROLE_TYPE"


```


## Learn by the example

* mandatory arguments followed by ':'
* optional arguments not followed by ':'

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
