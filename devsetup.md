# install on Windows (bare metal)


You'll need python >=3.10
```powershell
choco upgrade -y python
where python.exe
```

```bash
# curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
# python get-pip.py
python -m pip install virtualenv
```

From scripts/setup:

```bash
mkdir -p config

python -m venv venv
./venv/Scripts/activate.ps1
```

You're now in `(venv)`.

From script/bootsrap:

```bash
python -m pip install wheel --constraint homeassistant/package_constraints.txt
python -m pip install tox tox-pip-version colorlog pre-commit $(grep mypy requirements_test.txt) $(grep stdlib-list requirements_test.txt) $(grep tqdm requirements_test.txt) $(grep pipdeptree requirements_test.txt) $(grep awesomeversion requirements.txt) --constraint homeassistant/package_constraints.txt --use-deprecated=legacy-resolver
```

```bash
# no, thanks
# pre-commit install
```

```bash
python -m pip install -e . --constraint homeassistant/package_constraints.txt --use-deprecated=legacy-resolver
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

Patch satel:

edit `venv\lib\site-packages\satel_integra\satel_integra.py`

Line 175:
```python
-            self._reader, self._writer = await asyncio.open_connection(
-                self._host, self._port, loop=self._loop)
+            self._reader, self._writer = await asyncio.open_connection(
+                self._host, self._port)
```