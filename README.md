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

You want to run this command:

```
mv miyagaw61_exgdb miyagaw61/exgdb
mv miyagaw61_lf miyagaw61/lf
mv miyagaw61_chikuwansible miyagaw61/chikuwansible
```

This case, You can prepare this `Rumtfile`:

```
miyagaw61_(.*)
mv miyagaw61_{{1}} miyagaw61/{{1}}
```

And run `rumt`:

```
rumt
```

Then `find miyagaw61/ -maxdepth 1` output:

```
miyagaw61/exgdb
miyagaw61/lf
miyagaw61/chikuwansible
```
