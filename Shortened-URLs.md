This is a list of shortened Git URLs to make linking to common Cesium and CZML pages easier.

* **Cesium main page** http://git.io/cesium
* **Cesium Wiki** http://git.io/cesium-wiki
* **czml-writer main page** http://git.io/czml-writer
* **CZML Specification** http://git.io/czml

## Creating Shortened URLs

To create `http://git.io/cesium` from `http://github.com/AnalyticalGraphicsInc/cesium`, open bash and run:
```
curl -i http://git.io -F "url=http://github.com/AnalyticalGraphicsInc/cesium" -F "code=cesium"
```
See [Git.io: GitHub URL Shortener](https://github.com/blog/985-git-io-github-url-shortener).