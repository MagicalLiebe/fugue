[![Crates.io](https://img.shields.io/crates/v/fugue-box)](https://crates.io/crates/fugue-box)
[![Crates.io](https://img.shields.io/crates/l/fugue-box)](https://github.com/MagicalLiebe/fugue/blob/main/LICENSE)
[![CI](https://github.com/MagicalLiebe/fugue/actions/workflows/rust_ci.yml/badge.svg?branch=develop)](https://github.com/MagicalLiebe/fugue/actions/workflows/rust_ci.yml)

# ð¦ FUGUE ð¦

A CLI tool to operate files or directories in 2 steps.

## ð¦ DESCRIPTION

- `fugue`ã¯ãã¡ã¤ã«æä½ã2ã¹ãããã§è¡ãCLIãã¼ã«ã§ãã
- `mv`,`cp`,`ln`ã³ãã³ããªã©ã®ä»£æ¿ã³ãã³ãã¨ãã¦éçºãã¾ããã
- æä½å¯¾è±¡ã®ãã¡ã¤ã«ããã£ã¬ã¯ããªã`fugue mark`ã«ãããã¼ã­ã³ã°ããå¥ã®ãã£ã¬ã¯ããªã«ç§»åããå¾ã«ã³ãã¼ãç§»åãå®è¡ã§ãã¾ãã

## ð¦ INSTALLATION

### ãã«ãæ¸ã¿ãã¤ããª

- ä»¥ä¸ã®ã¢ã¼ã­ãã¯ãã£ç¨ã®ãã¤ããªã[releases](https://github.com/MagicalLiebe/fugue/releases)ã«æºåãã¦ãã¾ãã

  - aarch64-apple-darwin (Mac - Apple Chip)
  - x86_64-apple-darwin (Mac - Intel Chip)
  - x86_64-unknown-linux-gnu (Linux - Intel Chip)

- ãä½¿ãã®PCã«ãã£ããã¤ããªããã¹ã®éã£ããã£ã¬ã¯ããªã«éç½®ãã¦ãã ããã

### Cargoã«ãããã«ã

- `cargo`ã³ãã³ãã«ãããã«ããããã¨ã§ã¤ã³ã¹ãã¼ã«ã§ãã¾ãã

```
$ cargo install fugue-box
```

### ã³ãã³ãã®ç¢ºèª

- ä»¥ä¸ã®ã³ãã³ãã§ãã¼ã¸ã§ã³æå ±ãè¡¨ç¤ºãããã°ã¤ã³ã¹ãã¼ã«å®äºã§ãã

```
$ fugue -V
fugue v0.0.2
```

## ð¦ USAGE

```
USAGE:
    fugue <SUBCOMMAND>

OPTIONS:
    -h, --help       Print help information
    -V, --version    Print version information

SUBCOMMANDS:
    copy       Copy the marked file or directory
    help       Print this message or the help of the given subcommand(s)
    link       Make a symbolic link to the marked file or directory
    mark       Set the path of the target file or directory
    move       Move the marked file or directory
    version    Show the version of the tool
```

### æä½å¯¾è±¡ãã¡ã¤ã«ã®è¨­å®

- `fugue mark <TARGET>`ã§æä½å¯¾è±¡ã¨ãããã¡ã¤ã«ããã£ã¬ã¯ããªããã¼ã­ã³ã°ãã¾ãã

```
$ fugue mark target_file.txt 
â : ð target_file.txt has marked.
```

- ç¾å¨ãã¼ã­ã³ã°ä¸­ã®ãã¡ã¤ã«ããã£ã¬ã¯ããªãç¢ºèªãããã¨ãã¯ã`fugue mark --show`ã§ç¢ºèªã§ãã¾ãã

```
$ fugue mark --show
â¹ï¸ : ð /home/user/path/to/file/target_file.txt
```

- ãã¼ã­ã³ã°ãè§£é¤ãããå ´åã¯ã`fugue mark --reset`ã§è§£é¤ã§ãã¾ãã

```
$ fugue mark --reset
â : The marked path has reset.
```

### ãã¡ã¤ã«æä½

ä»¥ä¸ã®3ã¤ã®ãã¡ã¤ã«æä½ãå¯è½ã§ãã

#### ã³ãã¼

- ã³ãã¼åã®ãã£ã¬ã¯ããªã«ç§»åãã`fugue copy`ã§ãã¼ã­ã³ã°ä¸­ã®ãã¡ã¤ã«ããã£ã¬ã¯ããªãã³ãã¼ã§ãã¾ãã

```
$ cd test_dir_copy

$ fugue copy         
â¹ï¸ : Start copying ð target_file.txt from /home/user/path/to/file/target_file.txt
â : ð target_file.txt has copied.
```

- ã³ãã¼åã®ãã£ã¬ã¯ããªããã¡ã¤ã«åãä¸ãããã¨ãå¯è½ã§ãã

```
$ fugue copy test_dir_copy
â¹ï¸ : Start copying ð test_dir_copy/target_file.txt from /home/user/path/to/file/target_file.txt
â : ð test_dir_copy/target_file.txt has copied.

$ fugue copy copy.txt
â¹ï¸ : Start copying ð copy.txt from /home/user/path/to/file/target_file.txt
â : ð copy.txt has copied.
```

#### ç§»å

- ç§»ååã®ãã£ã¬ã¯ããªã«ç§»åãã`fugue move`ã§ãã¼ã­ã³ã°ä¸­ã®ãã¡ã¤ã«ããã£ã¬ã¯ããªãç§»åã§ãã¾ãã

```
$ cd test_dir_move

$ fugue move                
â¹ï¸ : Start moving ð target_file.txt from /home/user/path/to/file/target_file.txt
â : ð target_file.txt has moved.
```

- ã³ãã¼åæ§ãç§»ååã®ãã£ã¬ã¯ããªããã¡ã¤ã«åãä¸ãããã¨ãå¯è½ã§ãã

```
$ fugue move test_dir_move
â¹ï¸ : Start copying ð test_dir_move/target_file.txt from /home/user/path/to/file/target_file.txt
â : ð test_dir_move/target_file.txt has moved.

$ fugue move move.txt
â¹ï¸ : Start moving ð move.txt from /home/user/path/to/file/target_file.txt
â : ð move.txt has moved.
```

#### ã·ã³ããªãã¯ãªã³ã¯

- ã·ã³ããªãã¯ãªã³ã¯ãä½æããããã£ã¬ã¯ããªã«ç§»åãã`fugue link`ã§ãã¼ã­ã³ã°ä¸­ã®ãã¡ã¤ã«ããã£ã¬ã¯ããªã¸ã®ã·ã³ããªãã¯ãªã³ã¯ãä½æã§ãã¾ãã

```
$ cd test_dir_link

$ fugue link                
â¹ï¸ : Start making symbolic link ð target_file.txt from /home/user/path/to/file/target_file.txt
â : ð target_file.txt has made.
```

- ã·ã³ããªãã¯ãªã³ã¯ä½æåã®ãã£ã¬ã¯ããªããã¡ã¤ã«åãä¸ãããã¨ãå¯è½ã§ãã

```
$ fugue link test_dir_link
â¹ï¸ : Start making symbolic link ð test_dir_link/target_file.txt from /home/user/path/to/file/target_file.txt
â : ð test_dir_link/target_file.txt has made.

$ fugue link link.txt
â¹ï¸ : Start making symbolic link ð link.txt from /home/user/path/to/file/target_file.txt
â : ð link.txt has made.
```
