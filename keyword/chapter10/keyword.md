- **Spring Security**
    
    애플리케이션의 보안(인증 및 인가)을 담당하는 프레임워크. 복잡한 보안 로직을 간편하게 구현할 수 있도록 돕는다.
    
- **인증(Authentication)과 인가(Authorization)**
    
    인증 : 누가 누구인지 확인하는 절차
    
    인가 : 인증된 사용자가 특정 리소스나 기능에 접근할 권한이 있는지 확인하는 절차
    
- **세션과 토큰**
    
    세션 : 클라이언트와 서버 간의 연결이 지속되는 동안 상태를 유지하는 방법, 주로 서버의 메모리에 저장된다
    
    토큰 : 사용자의 인증 정보를 담고 있는 문자열. 세션 방식과 달리 서버가 상태를 저장하지 않는(Stateless) 방식
    
- **액세스 토큰(Access Token)과 리프레시 토큰(Refresh Token)**
    
    액세스 토큰 : 리소스에 접근하기 위한 권한을 부여하는 토큰. 만료 기간을 짧게 설정하여 탈취 시의 위험을 줄이는 것이 일반적이다.
    
    리프레시 토큰 : 액세스 토큰이 만료되었을 때 새로운 액세스 토큰을 발급받기 위해 사용되는 토큰. 액세스 토큰보다 만료 기간을 길게 설정한다.
