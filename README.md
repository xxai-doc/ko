<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

nodejs, [direnv](https://direnv.net) , [bun을](https://github.com/oven-sh/bun) 먼저 설치하고 디렉토리 진입 후 `direnv allow` 설치하는 것을 권장합니다(디렉토리 진입 후 [.envrc는](https://github.com/xxai-art/doc/blob/main/.envrc) 자동으로 실행됨).

의미는 일본어로 중국어 번역, 한국어, 영어, 다른 모든 언어로 영어 번역입니다. 중국어와 영어만 지원하려면 `zh: en` 입력하면 됩니다.

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

### 문서 번역 자동화 지침

코드 저장소 [xxai-art/doc](https://github.com/xxai-art/doc) 참조

nodejs, [direnv](https://direnv.net) , [bun을](https://github.com/oven-sh/bun) 먼저 설치하고 디렉토리 진입 후 `direnv allow` 설치하는 것을 권장합니다(디렉토리 진입 후 [.envrc는](https://github.com/xxai-art/doc/blob/main/.envrc) 자동으로 실행됨).

수백 개의 언어로 번역된 대규모 코드베이스를 피하기 위해 각 언어별로 별도의 코드베이스를 만들고 코드베이스를 저장할 조직을 만들었습니다.

환경 변수 `GITHUB_ACCESS_TOKEN` 설정하고 [create.github.coffee를](https://github.com/xxai-art/doc/blob/main/create.github.coffee) 실행하면 코드 저장소가 자동으로 생성됩니다.

물론 코드베이스에 넣을 수도 있습니다.

번역 스크립트 참조 [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

스크립트 코드는 다음과 같이 해석됩니다.

[bunx](https://bun.sh/docs/cli/bunx) 는 더 빠른 npx를 대체하는 것으로, 물론 bunx가 설치되어 있지 않다면 `npx` 대신 사용할 수 있습니다.

`bunx mdt zh` zh 디렉토리의 `.mdt` `.md` 로 렌더링합니다. 아래 링크된 파일 2개를 참조하세요.

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` 번역을 위한 핵심 코드입니다( `nodejs` 만 설치되어 있고 `bun` 과 `direnv` 설치되어 있지 않은 경우 `npx i18n` 실행하여 번역할 수도 있습니다).

[i18n.yml 을](https://github.com/xxai-art/doc/blob/main/i18n.yml) 구문 분석합니다. 이 문서의 `i18n.yml` 구성은 다음과 같습니다.

```
en:
zh: ja ko en
```

의미는 일본어로 중국어 번역, 한국어, 영어, 다른 모든 언어로 영어 번역입니다. 중국어와 영어만 지원하려면 `zh: en` 입력하면 됩니다.

마지막은 [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) 로 각 언어의 `README.md` 에서 주 제목과 첫 번째 부제 사이의 콘텐츠를 추출하여 항목 `README.md` 를 생성합니다. 코드는 매우 간단하며 직접 볼 수 있습니다.

Google API는 무료 번역에 사용됩니다. Google에 액세스할 수 없는 경우 다음과 같이 프록시를 구성하고 설정하십시오.

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

번역 스크립트는 `.i18n` 디렉토리에 번역된 캐시를 생성합니다. `git status` 로 확인하고 코드 저장소에 추가하여 번역이 반복되지 않도록 하세요.

번역을 수정할 때마다 `bunx i18n` 실행하여 캐시를 업데이트하십시오.

원문과 번역문을 동시에 수정하면 캐시가 혼란스러워지므로 수정을 원할 경우 하나만 수정하고 `bunx i18n` 실행하여 캐시를 업데이트하면 됩니다.
