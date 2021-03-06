# WMO-WLS: Windowed Multiscan Optimization using Weighted Least Squares

For scan-matching code in this repository uses
[CSM](https://github.com/AndreaCensi/csm). Precompiled `libcsm.so` and `sm2` for
64-bit Linux located inside `csm` folder. We are using slightly modified version
of the CSM, so if you want to compile it yourself it's recommended to apply
patch `csm.patch` first.

## Dependencies installation
For modern Debian based distribution you can execute the following command:
```sh
sudo apt-get install libgsl2 python3 python3-numpy python3-scipy python3-matplotlib python3-cffi texlive texlive-latex-extra dvipng
```

Additionally you'll need progressbar2 Python library, you can install it
using `pip3`:
```sh
sudo pip3 install progressbar2
```


## Usage
Download datasets archive:
```sh
wget https://github.com/SkRobo/wmo-wls/releases/download/0.1/datasets.tar.bz2
```

And unpack it:
```sh
bzip2 -dc datasets.tar.bz2 | tar xv
```

Next perform matching:
```sh
./match.py
```
Results will be saved in the `./results/match/` folder.

Finally perform optimization:
```sh
./wls.py
```
Results in the form of trajectories will be saved in the
`./results/wls/` folder.

To calculate trajectories using keyframe apporach run:
```sh
./keyframes.py
```

To perfrom nonlinear optimization for set of alphas run:
```sh
./nonlinear.py
```
Here argument is the index of dataset to be optimized for.
Results in the form of trajectories will be saved in the
`./results/nonlinear/` folder.

If you don't want to wait for nonlinear optimization to end you can download
precomputed results:
```sh
wget https://github.com/SkRobo/wmo-wls/releases/download/0.2/nonlinear.tar.bz2
```

To unpack them run:
```sh
bzip2 -dc nonlinear.tar.bz2 | tar xv -C results/
```

To plot figures used in the paper run:
```sh
./plot_figures.py
```
Figures will be saved in the `./figures/` folder.

## Performance
This code is created for scientific purposes only. It is not intended for
uses in practical applications. Thus various optimizations are applicable
which can significantly boost up computational and memory efficiency.
