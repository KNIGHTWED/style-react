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
`.sass`와 `.scss` 확장자를 사용

`yarn eject`
실행 후 `webpack.config.js` 파일에서
'sassRegex' 검색


```javascript
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
      sassOptions: {
        includePaths: [paths.appSrc + '/styles'],
        sourceMap: isEnvProduction && shouldUseSourceMap,
        additionalData: "@import 'utils';"
    }
  }
}),
```

**options** 안에 **sasOptions**로 한번 더 감싸줘야 failed to compile 안나오고 실행됨.
(출처 https://jsdev.kr/t/topic/5334)

data -> prependData -> **additionalData** 
(출처 https://teserre.tistory.com/11)


styled-components
props 값으로 전달해 주는 값을 쉽게 스타일에 적용 가능

```javascript
const Button = styled.button`
  background: ${props => props.color || 'blue'};
  color: black;
  border-radius: 4px;
  font-size: 1rem;
`;
```

예시로 위와 같은 코드를 작성할 수 있다.

스타일 속성은 `**&#96;** **&#96;**` 으로 감싸줘야 한다.

VS Code 마켓플레이스에서 vscode-styled-components를 설치하면

스타일 속성 부분에 에디터 폰트 색상이 입혀진다.

<br/>
<br/>
스타일도 .js파일 안에서 선언해서 사용가능
따라서 동일 .js파일이 아닌 다른 .js파일에 모듈로 만들어서 사용해도 된다.