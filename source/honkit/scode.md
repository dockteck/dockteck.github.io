# jsonサンプル

## book.json
```
{
    "root": "./source",
    "title": "Honkit - Github Pages",
    "description": "HonkitをGithub Pagesで公開する",
    "author": "Name",
    "language": "ja",
    "plugins": [
        "theme-default",
        "@dogatana/search-plus", "-lunr", "-search",
        "@dogatana/page-toc-button",
        "@dogatana/back-to-top-button",
        "anchors",
        "copy-code-button",
        "github-issue-feedback",
        "hide-published-with",
        "hints",
        "insert-logo-link-style",
        "toggle-chapters"
    ],

    "pluginsConfig": {
        "toggle-chapters":{},
        "page-toc-button": {
            "maxTocDepth": 2,
            "minTocSize": 2
        },
        "github-issue-feedback": {
            "repo": "user/repo",
            "label": "報告するる"
        },
        "insert-logo-link-style": {
            "src": "/assets/logo.png",
            "style": "background: none;",
            "link": "http://www.google.com",
            "target": "_blank"
        },
        "hints": {
            "info": "fa fa-bullhorn",
            "tip": "fa fa-coffee",
            "danger": "fa fa-check",
            "working": "fa fa-question-circle"
        }
    },

    "styles": {
        "website": "styles/website.css",
        "pdf": "styles/pdf.css"
    }

}
```
## package.json
```
{
  "name": "project",
  "version": "1.0.0",
  "description": "",
  "homepage": "https://user.github.io/",
  "scripts": {
    "init": "npx honkit init",
    "build": "npx honkit build . docs",
    "serve": "npx honkit serve",
    "deploy": "npx honkit build . docs && gh-pages -d docs"
  },
  "keywords": [],
  "author": "Name",
  "license": "ISC",
  "devDependencies": {
    "honkit": "^4.0.0",
    "gh-pages": "^4.0.0",
    "@dogatana/honkit-plugin-back-to-top-button": "^1.0.0",
    "@dogatana/honkit-plugin-page-toc-button": "^1.0.0",
    "@dogatana/honkit-plugin-search-plus": "^1.0.1",
    "gitbook-plugin-anchors": "^0.7.1",
    "gitbook-plugin-copy-code-button": "^0.0.2",
    "gitbook-plugin-github-issue-feedback": "^1.4.0",
    "gitbook-plugin-hide-published-with": "^0.0.1",
    "gitbook-plugin-hints": "^1.0.2",
    "gitbook-plugin-insert-logo-link-style": "^1.0.3",
    "honkit-plugin-toggle-chapters": "^0.0.1"
  }
}
```
## website.css
```
    /* github-issue-feedback */
    .gitbook-plugin-github-issue-feedback {
        background-color: #333;
        color: #fff;
        opacity: 0.8;
        padding: 4px;
        margin-right: 24px;
        margin-bottom: 4px;
        border-radius: 6px;
    }

    .gitbook-plugin-github-issue-feedback:hover {
        opacity: 1;
    }
```
