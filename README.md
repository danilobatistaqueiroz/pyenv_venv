### configurando para rodar o GTK:  

apt download python3-gi python3-gi-cairo gir1.2-gtk-3.0 libcairo2-dev pkg-config libgirepository1.0-dev libglib2.0-dev libffi-dev

dpkg -x python3-gi_3.36.0-1_amd64.deb python3-gi
dpkg -x python3-gi-cairo_3.36.0-1_amd64.deb python3-gi-cairo
dpkg -x libcairo2-dev_1.16.0-4ubuntu1_amd64.deb libcairo2
dpkg -x libglib2.0-dev_2.64.6-1\~ubuntu20.04.4_amd64.deb libglib2
dpkg -x libffi-dev_3.3-4_amd64.deb libffi
dpkg -x libgirepository1.0-dev_1.64.1-1\~ubuntu20.04.1_amd64.deb libgirepository
dpkg -x pkg-config_0.29.1-0ubuntu4_amd64.deb pkg-config
dpkg -x gir1.2-gtk-3.0_3.24.20-0ubuntu1.1_amd64.deb gir1

cp -r libs/gir1/usr/lib/* venv/lib/
cp -r libs/libcairo2/usr/lib/* venv/lib/
cp -r libs/libffi/usr/lib/* venv/lib/
cp -r libs/libgirepository/usr/lib/* venv/lib/
cp -r libs/libglib2/usr/lib/* venv/lib/
cp -r libs/pkg-config/usr/lib/* venv/lib/
cp -r libs/python3-gi/usr/lib/python3/dist-packages/* venv/lib/python3.8/site-packages
cp -r libs/python3-gi-cairo/usr/lib/python3/dist-packages/* venv/lib/python3.8/site-packages

export PROJECT=/home/element/labs/python/gtk/with_pyinstaller
export SITEPACKAGES=$PROJECT/venv/lib/python3.8/site-packages
export PYTHONPATH=$PROJECT/venv/lib:$PROJECT/venv/lib/python3.8:$SITEPACKAGES

também é possível fazer um link:  
ln -s venv/bin/python3 venv/bin/python3.8.10

### configurando para o Tkinter funcionar:  
apt download python3-tk
dpkg -x python3-tk_3.8.10-0ubuntu1\~20.04_amd64.deb python3-tk
cp -r libs/python3-tk/usr/lib/python3.8/tkinter venv/lib/python3.8/tkinter
cp /usr/lib/python3.8/lib-dynload/_tkinter.cpython-38-x86_64-linux-gnu.so venv/lib/python3.8/lib-dynload/
cp /usr/share/lintian/overrides/python3-tk venv/share/lintian/overrides/

para que o tkinter funcione:  
export PROJECT=/home/element/labs/python/gtk/with_pyinstaller
export PYTHONPATH=$PROJECT/venv/lib/python3.8:$PROJECT/libs/tcl8.6:$PROJECT/libs/tk8.6:$PROJECT/venv/lib/python3.8/lib-dynload:$PROJECT/libs/python3-tk/usr/lib/python3.8/tkinter

