# SSH - 인증키 생성

## Info

위의 문서는 `Ubuntu` 환경을 기준으로 작성 되었습니다.

대표적인 비대칭 공개키 암호화 방식인
`RSA(Rivest-Shamir-Adleman)`을 기준으로 설명합니다.

RSA 기반의 인증키를 생성 시, 2개의 파일이 생성되며
각각의 용도는 아래와 같습니다.

- `*._rsa`
	
	비공개 키: **(절대로 외부에 공유하지 않습니다.)**
	

- `*.rsa.pub`
	
	공개 키: **(서버나 Git 서비스에 등록합니다.)**
	

---

### Create Key

- ***Base***
```bash
ssh-keygen -t rsa -b 4096 -C $USER_EMAIL
```

| ***option***      | ***info***                               | ***Ex***                   |
| ----------------- | ---------------------------------------- | -------------------------- |
| `-t <type>`       | 키 타입을 지정                                 | `rsa`, `ecdsa`, `ed25519`  |
| `-b <bits>`       | 키 길이를 지정                                 | **PSA**는 2048 또는, 4096을 추천 |
| `-f <filename>`   | 키 파일을 저장할 경로와 이름을 지정                     | `-f ~/.ssh/keystore`       |
| `-C <comment>`    | 키에 주석 삽입.                                | **GitHub** 식별용으로 유용        |
| `-N <passphrase>` | 패스프레이즈(암호) 지정.<br>자동화 작업에선 빈 문자열로도 설정 가능 |                            |
| `-q`              | 생성 과정에서 터미널<br>출력문 생략 (간략히 표현)           |                            |
| `-m PEM`          | 출력 format을 PEM으로 설정합니다.                  | 구버전 호환성용                   |

<br>

- ***Ex***
```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/keystore -C atng02_019@nhnacademy.com
```

---

### Folder path

#### Local Location

```bash
cd .ssh/keystore
```

#### Remote Location

```bash
cd .ssh/authorized_keys
```

---

## Move

| prev | curr | next |
| ---- | ---- | ---- |

---

## Reference

- [wikipedia - 공개 키 암호화 방식](https://ko.wikipedia.org/wiki/%EA%B3%B5%EA%B0%9C_%ED%82%A4_%EC%95%94%ED%98%B8_%EB%B0%A9%EC%8B%9D) 
	
- [wikipedia - RSA 암호](https://ko.wikipedia.org/wiki/RSA_%EC%95%94%ED%98%B8)
	
- [GitHub Docs - Authentication: 새 SSH 키 생성](https://docs.github.com/ko/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

---
