## rumt - RUn Many Times

You can run same command many times

### Install

```
cd /path/to/
git clone https://github.com/miyagaw61/rumt
cp -a ./rumt/rumt /usr/local/bin/
pip install --git https://github.com/miyagaw61/enert
```

### Usage

```
vim Rumtfile
rumt
```

### Rumtfile

Now `find -maxdepth 1 -name 'miyagaw61_*'` output:

```
miyagaw61_exgdb
miyagaw61_lf
miyagaw61_chikuwansible
```

If you want to run this command:

```
mkdir miyagaw61
mv miyagaw61_exgdb miyagaw61/exgdb
mv miyagaw61_lf miyagaw61/lf
mv miyagaw61_chikuwansible miyagaw61/chikuwansible
```

In this case, You can prepare this `Rumtfile`:

```
find -maxdepth 1 -name 'miyagaw61_*'
miyagaw61_(.*)
mv miyagaw61_{{1}} miyagaw61/{{1}}
```

And run `rumt`:

```
mkdir miyagaw61
rumt
```

Then `find miyagaw61/ -maxdepth 1` output:

```
miyagaw61/exgdb
miyagaw61/lf
miyagaw61/chikuwansible
```

You can this test in test directory:

```
cd test
ls
mkdir miyagaw61
rumt
ls
ls miyagaw61/
rumt Rumtfile2
ls
ls miyagaw61/
```
