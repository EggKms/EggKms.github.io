---
title: github page 를 google 검색에 나타나게 하는법
date: YYYY-MM-DD HH:MM:SS +09:00
categories: [homepage, github, github.io]
tags:
  [
    homepage,
    github,
    github.io,
    jekyll,
    blog,
    search

  ]
---

# github page
=============
---

구글 검색에 노출하기 위해서는 sitemap.xml, robots.txt등이 갖춰져 있어야 합니다.

## 1. sitemap 활성화

jekyll 사이트맵에서 말하는 설치법.
참고 - <https://github.com/jekyll/jekyll-sitemap>

1. Add ```gem 'jekyll-sitemap'``` to your site's Gemfile and run ```bundle```
2. Add the following to your site's ```_config.yml```:

```
url: "https://eggkms.github.io/" # the base hostname & protocol for your site
plugins:
  - jekyll-sitemap
```

* 블로그 소스 ```Gemfile``` 안에 ```gem 'jekyll-sitemap'``` 삽입.
* ```terminal```에 ```bundle install``` 실행
* ```Gemfile.lock``` 파일 안에 DEPENDENCIES -> jekyll-sitemap 추가 확인

참고 -  <https://jekyllrb-ko.github.io/docs/plugins/>

jekyll 에는 많은 플러그인이 있지만 현재는 sitemap 만 다룬다.

* ```_config.yml``` 안에 ```url``` 하단에 ``` plugins: - jekyll-sitemap``` 추가.

```
url: "https://eggkms.github.io/"
plugins:
  - jekyll-sitemap
```

이후 ```bundle exec jekyll serve``` 로 테스트 할 때
```url/sitemap.xml```로 접속 시 xml 설정이 나온다면 정상동작하는것이다.
* ex) https://eggkms.github.io/sitemap.xml

## 2. robots.txt 추가

크롤링 봇에게 내 sitemap 파일과 어디까지 제공하는지에 대한 설정

git repository 최상단에 robots.txt를 추가하고 아래 내용을 입력합니다.
```
User-agent: *
Allow: /

Sitemap: https://eggkms.github.io/sitemap.xml
```

## 3. google search console에 sitemap 등록

<https://www.google.com/webmasters>에서 ‘SEARCH CONSOLE’을 선택합니다.











----------------
미완성 소스

특정 페이지/게시물을 사이트맵에서 제외할 수도 있다.
구성을 추가한 뒤 ```_config.yml``` 파일에
```
defaults:
  - scope:
      path: "assets/**/*.pdf"
    values:
      sitemap: false
```

특정 페이지 / 게시물에서 추가.

```
sitemap: false
```




 



## 참고
- - -
* <https://inasie.github.io/it%EC%9D%BC%EB%B0%98/3/>
* <https://en.wikipedia.org/wiki/Sitemaps>
* <https://github.com/jekyll/jekyll-sitemap>
* <https://jekyllrb-ko.github.io/docs/plugins/>