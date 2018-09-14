# Docker PyCon JP issue receipt

## Usage

- Edit GIT_BRANCH and YEAR parameters in docker-compose.yml file.
- Put attendee master DB into ./issue_receipt/db directory.
- Clone issue_receipt.git repository on pycon.jp server then copy "static" to somewhere you want.
- Edit pycon.jp's nginx config to refer this host and static directory in pycon.jp.
- `docker-compose up -d`

## ToDo

- Integrate nginx for static contents.
