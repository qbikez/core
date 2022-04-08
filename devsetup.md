# install on Windows (bare metal)

```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```

From scripts/setup:

```
mkdir -p config

python3 -m venv venv
./venv/Scripts/activate.ps1
```

You're now in `(venv)`.

From script/bootsrap:

```bash
python3 -m pip install wheel --constraint homeassistant/package_constraints.txt
python3 -m pip install tox tox-pip-version colorlog pre-commit $(grep mypy requirements_test.txt) $(grep stdlib-list requirements_test.txt) $(grep tqdm requirements_test.txt) $(grep pipdeptree requirements_test.txt) $(grep awesomeversion requirements.txt) --constraint homeassistant/package_constraints.txt --use-deprecated=legacy-resolver
```

```bash
pre-commit install
```

```bash
python3 -m pip install -e . --constraint homeassistant/package_constraints.txt --use-deprecated=legacy-resolver
pip install tzdata
```

install [npcap](https://npcap.com/#download)



```bash
hass --verbose
```

Get HACS:
```bash
wget -O - https://get.hacs.xyz | bash -
```