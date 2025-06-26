---
layout: post
categories: [blog, jekyll]
title: Jekyll 블로그에 Code Syntaxhighlight 추가하기
---

심플해서 고른 테마지만, Code 문법에 테마가 적용되지 않아 밋밋한 김에 설정을 좀 만진다.

## Gem 설치하기

```bash
gem install kramdown rouge
```
---
## _Config 설정하기
```yaml
markdown: kramdown

kramdown:
  input: GFM
  syntax_highlighter: rouge

```
위 적용이 안될 경우는, 아래와 같이 쓸 수 있다고 한다. 난 위 내용으로 적용됐다.
```yaml
markdown: kramdown
highlighter: rouge
```
---
## Rouge 테마 CSS 만들기
(Rouge Theme Preview Page)[https://spsarolkar.github.io/rouge-theme-preview/] 에 접속하여 원하는 테마를 선택하여 아래와 같이 CSS 파일을 만든다.

```bash
rougify style monokai > assets/css/syntax.css
```
---
## Post Layout 에 CSS 적용하기
만들어둔 파일의 경로를 Post 가 적용되는 레이아웃의 head 태그 내 아래 내용을 추가한다.
```html
<link rel="stylesheet" href="{{ "/assets/css/syntax.css" | relative_url }}" />
```
---
## Post 에 Syntax Highlihght 적용하기
아래 형태로 작성하면, 
````
```java
int total = 0;
for(int i = 0; i < list.length; i++) {	
  total += list[i];
  System.out.println( list[i] );
}
return total;
```
````

다음과 같이 적용된다. 
```java
int total = 0;
for(int i = 0; i < list.length; i++) {	
  total += list[i];
  System.out.println( list[i] );
}
return total;
``` 