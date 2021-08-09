# Java 로 외부 api 호출연습 repository

### localhost:8080/auth/GOOGLE 을 주소창에 입력하였을때

1. OauthController 에 매핑되어 'GOOGLE' 은 query string 에서 소셜 로그인 타입 인자로 받게 된다.
2. 소셜 로그인 타입을 OauthService 의 request 메소드로 넘긴다.
3. OauthService 에서 만들어둔 findSocialOauthByType 메소드에서 받을 수 있는 소셜 로그인 타입인지 확인한다.
   - 예외상황) 존재하지 않는 소셜 로그인 타입일 경우 예외 처리
4. GoogleOauth 클래스 선택하여 반환하고 getOauthRedirectURL 메소드를 통해 URL 을 조립하여 
   SocialLogin 을 할 수 있는 페이지로 이동한다.
5. LoginPage 에서 구글 아이디로 로그인 할 수 있다.
6. 로그인이 성공 했을 때 callback URL 을 통해 구글에서 보내준 데이터를 json 형태로 받을 수 있다.
7. requestAccessToken 메소드를 통해 소셜 로그인 타입과 code 를 인자로 넘긴다.
8. 다시 한 번 GoogleOauth 클래스를 찾아서 requestAccessToken 메소드에 code 인자를 넘긴다.
9. Map 을 만들어 필요한 키, 벨류를 담고 post 로 넘긴다.
10. HttpStatus.OK 이면 정상적인 로그인 완료되어 getBody 를 할 수 있고, 아니라면 에러 발생
11. 최종 화면은 getBody 의 결과 혹은 에러 메세지


### TODO List

   - JWT Token 도입
   - SNS Login 후 Logout 추가
   - Naver Login - NCP 에 아이디만 추가하면 됨