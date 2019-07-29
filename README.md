## rumt - RUn Many Times

You can run same command many times for many files

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

Now `find -name 'hoge_*'` output:

```
./hoge_exgdb
./hoge_lf
./hoge_chikuwansible
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
find -name 'hoge_*'
hoge_(.*)
mv hoge_{{1}} hoge/{{1}}
```

And run `rumt`:

```
mkdir hoge
rumt
```

Then `find hoge/` output:

```
hoge/
hoge/exgdb
hoge/lf
hoge/chikuwansible
```

You can this test in test directory:

```
$ cd test/
$ ls
fizz_buzz  foo_bar  hoge_chikuwansible  hoge_exgdb  hoge_lf  Rumtfile  Rumtfile2
$ find -name 'hoge_*'
./hoge_chikuwansible
./hoge_lf
./hoge_exgdb
$ mkdir hoge
$ cat Rumtfile
find -name 'hoge_*'
hoge_(.*)
mv hoge_{{1}} hoge/{{1}}
$ rumt
$ ls
hoge  fizz_buzz  foo_bar  Rumtfile  Rumtfile2
$ ls hoge/
chikuwansible  exgdb  lf
```

You can revert it back:

```
$ find | grep '^./hoge/.*'
./hoge/lf
./hoge/chikuwansible
./hoge/exgdb
$ cat Rumtfile2
find | grep '^./hoge/.*'
(.*)/(.*)
mv {{1}}/{{2}} hoge_{{2}}
$ rumt Rumtfile2
$ ls
hoge  fizz_buzz  foo_bar  hoge_chikuwansible  hoge_exgdb  hoge_lf  Rumtfile  Rumtfile2
$ ls hoge/
$
```
