<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

웹사이트 코드의 일부는 오픈 소스입니다. 번역 최적화에 도움을 주셔서 감사합니다.

## 프런트엔드 코드

* [프런트엔드 코드](https://github.com/xxai-art/web)
* [사이트 전체를 위한 언어 팩](https://github.com/xxai-art/web/tree/main/i18n)
* [로그인 모듈용 언어 팩](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [웹사이트 다국어 문서](https://github.com/xxai-doc)

프런트엔드 프로그래밍 언어는 [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) 이며 이는 coffeescript 구문을 기반으로 몇 가지 기능을 추가합니다 [( ./coffee_plus.md](./coffee_plus.md) 참조).

## 웹사이트 및 문서의 국제화

다음 3개 프로젝트를 기반으로 구축

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  접미사는 `.mdt` 이며 `<+ ./coffee_plus/import.js>` 유사한 구문을 사용하여 외부 파일을 참조하고 접미사 `.md` 로 마크다운을 생성할 수 있습니다.

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  마크다운 번역은 코드와 링크를 번역하지 않고 번역된 문장을 캐시합니다.번역이 수정되었지만 원본 텍스트가 수정되지 않은 경우 다시 실행해도 번역 수정을 덮어쓰지 않습니다.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  `yaml` 생성 웹사이트를 번역하기 위한 언어 파일.
