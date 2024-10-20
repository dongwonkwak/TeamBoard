# 로그인

## 1. 목적

사용자가 OAuth2를 통해 안전하고 편리하게 시스템에 로그인할 수 있도록 한다.

## 2. 주요 참여자

* 사용자
* 시스템

## 3. 선행 조건

* 사용자가 인터넷에 접속해 있어야 한다.
* 사용자가 유효한 계정을 가지고 있어야 한다.
* 시스템이 OAuth2 제공자와 연동 설정을 완료한 상태이어야 한다.

## 4. 후행 조건

* 사용자가 성공적으로 로그인하여 시스템에 접근할 수 있게 된다.

## 5. 기본 흐름

1. 사용자는 웹사이트에서 "로그인" 버튼을 클릭한다.
2. 시스템은 OAuth2 제공자의 인증 페이지로 리디렉션한다.
3. 사용자는 자신의 계정으로 로그인한다.
4. OAuth2 제공자는 인증이 완료되면 시스템에 인증 코드를 반환한다.
5. 시스템은 인증 코드를 사용하여 OAuth2 제공자에게 엑세스 토큰을 요청한다.
6. OAuth2 제공자는 액세스 토큰을 시스템에 반환한다.
7. 시스템은 액세스 토큰을 사용하여 사용자의 프로필 정보(이메일, 이름, id)등을 OAuth2 제공자로부터 조회한다.
8. 시스템은 사용자의 로그인 세션을 생성하고, 대시보드로 리디렉션한다.
9. 사용자는 성공적으로 로그인하여 시스템의 서비스를 이용할 수 있게 된다.

## 6. 대안 흐름

A1: OAuth2 제공자 로그인 실패

1. 사용자가 OAuth2 제공자의 로그인 페이지에서 잘못된 자격을 입력하거나 로그인을 취소 한다.
2. OAuth2 제공자는 시스템에 인증 실패 응답을 반환한다.
3. 시스템은 "로그인에 실패했습니다. 다시 시도해주세요"라는 오류 메시지를 사용자에게 표시한다.
4. 사용자는 로그인 과정을 다시 시도한다.

A2: 인증 코드 만료

1. 시스템이 인증 코드를 액세스 토큰으로 교환하는 과정에서 인증 코드가 만료되었음을 감지한다.
2. 시스템은 "인증 코드가 만료되었습니다. 다시 로그인해주세요." 라는 오류 메시지를 사용자에게 표시한다.
3. 사용자는 로그인 과정을 다시 시작한다.

A3: 사용자 정보 조회 실패

1. 시스템이 액세스 토큰을 사용하여 OAuth2 제공자로부터 사용자 정보를 조회하는 과정에서 실패한다.
2. 시스템은 "사용자 정보 조회에 실패했습니다. 다시 시도해주세요."라는 오류 메시지를 사용자에게 표시한다.
3. 사용자는 로그인 과정을 다시 시도하거나 지원 팀에 문의할 수 있다.

## 7. 예외 흐름

E1: 네트워크 오류

1. 사용자가 로그인 과정 중 네트워크 오류로 인해 요청이 중단된다.
2. 시스템은 "네트워크 오류가 발생했습니다. 인터넷 연결을 확인하고 다시 시도해주세요"라는 오류 메시지를 사용자에게 표시한다.
3. 사용자는 인터넷 연결을 확인하고 로그인 과정을 다시 시도한다.

E2: OAuth2 제공자 서비스 중단

1. OAuth2 제공자가 서비스 중단 상태이거나 응답하지 않는다.
2. 시스템은 "현재 로그인 서비스가 이용 불가능합니다. 나중에 다시 시도해주세요."라는 오류 메시지를 사용자에게 표시한다.
3. 사용자는 나중에 다시 시도하거나 지원 팀에 문의할 수 있다.
