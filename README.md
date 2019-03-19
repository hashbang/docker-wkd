# docker-wkd

A GNUPG WKD (Web Key Directory) generating docker image.

## Usage

| ENV VAR        | Required | Description |
|----------------|:--------:|-------------|
| MAIL_DOMAIN    | *        | The domain you'd like to generate key files for. (ex. drgrovellc.com) |
| DATA_FILE_PATH |          | The path to the datafile |
| HU_FOLDER      |          | The folder you'd like to generate the wkd in |

```bash
# Make your folders
mkdir data hu .gnupg
# Make your keys.txt file
echo "C92FE5A3FBD58DD3EC5AA26BB10116B8193F2DBD # Danny Grove" > data/keys.txt

docker run --rm \
  -v $PWD/data:/data/ -v $PWD/hu:/root/hu -v $PWD/.gnupg:/root/.gnupg \
  -e MAIL_DOMAIN=drgrovellc.com
  drgrove/wkd
```
