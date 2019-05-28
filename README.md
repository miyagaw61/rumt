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

Now `find -maxdepth 1 -name 'hoge_*'` output:

```
hoge_exgdb
hoge_lf
hoge_chikuwansible
```

If you want to run this command:

```
mkdir hoge
mv hoge_exgdb hoge/exgdb
mv hoge_lf hoge/lf
mv hoge_chikuwansible hoge/chikuwansible
```

In this case, You can prepare this `Rumtfile`:

```
find -maxdepth 1 -name 'hoge_*'
hoge_(.*)
mv hoge_{{1}} hoge/{{1}}
```

And run `rumt`:

```
mkdir hoge
rumt
```

Then `find hoge/ -maxdepth 1` output:

```
hoge/exgdb
hoge/lf
hoge/chikuwansible
```

You can this test in test directory:

```
cd test
ls
mkdir hoge
rumt
ls
ls hoge/
rumt Rumtfile2
ls
ls hoge/
```
