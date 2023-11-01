### How to uncomment line in a text file ...

```
# comment1
#comment2
#   comment3
```

```
 comment1
comment2
   comment3
```

```shell
sed '/comment/s/^#//g' filename
```

### How to comment line in a text file

```
 comment1
comment2
   comment3
```

```
# comment1
#comment2
#   comment3
```

```shell
sed '/comment/s/^#*/#/g' filename
```

### You can use this sed command to remove leading whitespace (spaces or tabs)

```
      aaaaa
      bbbbb
      ccccc
```
```
aaaaa
bbbbb
ccccc
```


```shell
sed 's/^[ \t]*//' filename
```
source: https://stackoverflow.com/questions/34322188/removing-all-spaces-from-the-beginning-of-lines

### How would I go about inserting a choice line of text after the first line matching a specific string

```
CLIENTSCRIPT="foo"
CLIENTFILE="bar"

CLIENTSCRIPT="foo"
CLIENTSCRIPT2="hello"
CLIENTFILE="bar"
```

```shell
sed '/CLIENTSCRIPT="foo"/a CLIENTSCRIPT2="hello"' file
```
source: https://stackoverflow.com/questions/15559359/insert-line-after-match-using-sed
