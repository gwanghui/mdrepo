## HOL (Head of Line) Blocking - 특정 응답의 지연

- Web에서의 HOLB
  - HTTP HOLB
  - TCP HOLB
 
- HTTP/1.1의 connection당 하나의 요청처리를 개선할 수 있는 기법중 pipelining이 존재 
  - 하나의 Connection을 통해서 다수개의 파일을 요청/응답 받을 수 있는 기법 어느 정도의 성능 향상을 꾀 할 수 있으나 큰 문제점이 하나 있다.
 
 - 하나의 TCP연결에서 3개의 이미지(a.png, b.png, c.png)를 얻을려고 하는경우 HTTP의 요청순서는 다음 그림과 같다.

| --- a.png --- |

            | --- b.png --- |


                        | --- c.png --- |

- 순서대로 첫번째 이미지를 요청하고 응답받고 다음 이미지를 요청하게 되는데 만약 첫번째 이미지를 요청하고 응답이 지연되면 아래 그림과 같이 두,세번째 이미지는 당연히 첫번째 이미지의 응답처리가 완료되기 전까지 대기한다.
- 이와 같은 현상을 HTTP의 Head of Line Blocking 이라 부르며 파이프 라이닝의 큰 문제점 중 하나이다.

| ------------------------------- a.png --------------- --- |

                                                       | -b.png- |


                                                               | --c.png-- |
                                                               
출처 : https://www.popit.kr/%EB%82%98%EB%A7%8C-%EB%AA%A8%EB%A5%B4%EA%B3%A0-%EC%9E%88%EB%8D%98-http2/
