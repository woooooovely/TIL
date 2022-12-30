# Webpack

# 📌 Webpack?

웹팩은 **번들링 작업을 수행해주는 번들러(Bundler)**이다. 

우리가 정한 시작점(entry point)으로부터 **의존적인 모듈을 찾아내서 하나의 결과물을 만들어준다.**

# ✅ Webpack의 주요 기능

1. Entry
    
    웹팩에서 **웹 자원을 번들링하기 위해** 필요한 최초 진입점이자 자바스크립트 파일 경로
    

![Untitled](Webpack%2072937f68642c4cc28c323010d3fc3e61/Untitled.png)

```json
// webpack.config.json
module.exports = {
	entry: './src/main.js';
}
```

쉽게 말하면 webpack에게 **‘이 파일부터 빌드를 시작해줘!’**라고 경로를 명시적으로 알려주는 과정이다.

1. Output
    
    빌드 후 웹팩을 돌리고 난 후 결과물의 파일 경로를 의미
    

```json
module.exports = {
	output: {
		filename: 'bundle.js'
	}
}
```

이와 같이 설정하면 웹팩은 빌드한 파일을 `bundle.js` 에 담게 된다.