# STYLE

## CSS

css 작성 주의사항
+ css클래스를 중복되지 않게 만든다.

App.js에 사용될 App.css

```css
.App{
  ...
}
```
App 전체 스타일

```css
.App .logo{
  ...
}
```
App 안의 logo 스타일

```css
.App header{
  ...
}
```
App 안의 header 스타일
header는 클래스가 아닌 태그이기 때문에 .header라고 쓰지 않는다.


## Sass
.sass와 .scss 확장자를 사용

yarn eject
실행 후 webpack.config.js 파일에서
'sassRegex' 검색


'''javascript
test: sassRegex,
exclude: sassModuleRegex,
use: getStyleLoaders(
  {
    importLoaders: 3,
    sourceMap: isEnvProduction ? shouldUseSourceMap : isEnvDevelopment,
    modules: {
      mode: 'icss',
    },
  }).concat({
    loader: require.resolve('sass-loader'),
    options: {
      sassOptions: { // 원래는 options로만 감싸져 있었지만 sassOptions로 한번 더 감싸줘야 에러 안나옴.
      includePaths: [paths.appSrc + '/styles'],
      sourceMap: isEnvProduction && shouldUseSourceMap,
      data: "@import 'utils';"
    }
  }
}),
'''

**options** 안에 **sasOptions**로 한번 더 감싸줘야 failed to compile 안나오고 실행됨.
