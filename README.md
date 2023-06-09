# 마크다운 사용템플릿 #

이 페이지는 깃허브 마크다운으로 문서작성샘플을 기록합니다.

https://kiss7001.github.io/test0518/ 로 접속이 가능합니다.

Advantages:
- 하하하
- Works on any markdown file (doesn't need to be on a public GitHub repo)
- Fast

Disadvantages:
- Uses my best guess at GitHub's algorithm to determine anchor names for header strings. Works for my use cases, but may not cover all cases. If it doesn't work for you, please let me know!


## 사용방법 ##

- Install Python 2.7 (haven't tested with other versions)
- Run ```md-to-toc <markdown_file>```
- Copy output to your markdown file


## 예시 ##

Given test.md:

```
# Header1
Some text

## Header2
Some more text

## Header2 again
Even more text

### Header3

#### Header4

##### Header5

###### Header6

# Header1

## Header2

## Header2 again
```

Run md-to-toc:

```bash
$ python md-to-toc.py test.md
- [Header1](#header1)
  - [Header2](#header2)
  - [Header2 again](#header2-again)
    - [Header3](#header3)
      - [Header4](#header4)
        - [Header5](#header5)
          - [Header6](#header6)
- [Header1](#header1-1)
  - [Header2](#header2-1)
  - [Header2 again](#header2-again-1)
```

One cute feature is that if your file doesn't start with header level 1, leading spaces will be removed so that the output is flush with the left edge:

test2.md:

```
### Header3

#### Header4

##### Header5

###### Header6
```


| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |


```
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

```bash
$ python md-to-toc.py test2.md
- [Header3](#header3)
  - [Header4](#header4)
    - [Header5](#header5)
      - [Header6](#header6)
```


## 대안 ##

[github-markdown-toc](https://github.com/ekalinin/github-markdown-toc) is a bash script that uses GitHub's API to convert a markdown file to HTML, then parses the HTML to produce the table of contents. This script is more robust than md-to-toc because it parses out the anchors directly from HTML, while md-to-toc converts the header titles to anchors using my best guess at GitHub's algorithm. On the other hand, github-markdown-toc requires an internet connection.
