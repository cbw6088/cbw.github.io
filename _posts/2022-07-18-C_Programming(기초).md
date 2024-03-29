---
title: "C-Programming(기초)"
categories:
  - 수식과연산자
  - 조건문
  - 배열
  - 함수
---

<details>
<summary> 수식과 연산자 </summary>
<div markdown="1">

# C_Programming 과제.1 (수식과 연산자)

### C_과제 1.c
양의 정수 한 개를 입력 받는다. 입력 받은 수가 3의 배수인 경우에는 3의 배수임을 출력하고 5의 배수인 경우에는 5의 배수임을 출력하고 15의 배수인 경우에는 15의 배수임을 출력 한다. 만약 입력 받은 수가 3, 5, 15의 배수가 아닌 경우에는 입력받은 수를 그대로 출력한다. 출 력문은 아래의 출력 예시와 같은 영어 형식으로 출력한다.
- 힌트: 논리 연산자(&&), 논리 부정 연산자(!), 산술 연산자(곱셈, 덧셈, 나머지), 괄호를 이용하 시오.
- if문 / for문 등 사용하지 않고 푸시오.

<img width="389" alt="스크린샷 2022-06-28 오후 11 03 38" src="https://user-images.githubusercontent.com/99342700/176198776-53c2657b-43fc-4723-8dc5-188f1ba77c46.png">

1. 입력 받을 N값과 출력 할 결과값 result 변수 지정
2. 입력 후 조건에 충족시 1 불충족시 0이 나오는 연산을 이용하여 충족하는 해당 연산에 배수만큼 곱하기.
3. 나와야 할 결과값에 맞춰 출력값 세팅

```c++
#include <stdio.h>

int main(void){
    int N=0; int result=0;
    scanf("%d",&N);

    result = ( (N%15 == 0) && (N%5 == 0) && (N%3 == 0) ) * 15 +
    ( (N%15 != 0) && (N%5 != 0) && (N%3 == 0) ) * 3 +
    ( (N%15 != 0) && (N%3 != 0) && (N%5 == 0) ) * 5 +
    ( (N%15 != 0) && (N%5 != 0) && (N%3) != 0 ) * N;
    
    printf("%d is a multiple od %d.",N,result);
    
    return 0;
}
```


### C_과제 2.c
연도를 입력받고, 해당 연도가 윤년인지 평년인지를 판단하는 프로그램을 작성하시오. 단, 윤년일 경우에는 L을, 평년일 경우에는 C를 출력하며, <u>반드시 조건 연산자</u>를 사용하시오.
- 윤년 = 4로 나누어떨어지는 수는 윤년인데, 그 중에서 100으로 나누어떨어지는 수는 제외한다. - 윤년 = 400 으로 나누어떨어지는 수는 윤년, 예) 400, 800, 2000
- 평년 = 그 외는 평년

<img width="443" alt="스크린샷 2022-06-29 오후 1 33 51" src="https://user-images.githubusercontent.com/99342700/176352582-81a3ca99-c848-4069-b8b2-89d4de14d7db.png">

1. 입력 받을 변수와 결과 값으로 출력 할 변수를 지정.
2. 조건 연산자를 사용하여 윤년일 경우 'L' 평년일 경우 'C'를 결과값에 저장.
3. 결과값 출력

```c++
#include<stdio.h>

int main(void){
	int N=0; char result=0;
	scanf("%d",&N);

	result = ( (N%4==0 || N%400==0) && (N%100!=0) ) ? 'L' : 'C';
	printf("%c",result);

	return 0;
}
```


### C_과제 3.c
세 자리 양의 정수 세 개를 입력 받는다. 각 수의 백의 자리수가 모두 같으면 T를 출 력하고, 두 수의 백의 자리수만 같으면 D를 출력하고, 백의 자리수가 모두 다르면 S를 출력하시 오.
- 힌트: 관계연산자( a==b a!=b )와 논리연산자( && || )와 괄호를 이용하시오.
- if문등 배우지 않은 문법 사용금지

<img width="382" alt="스크린샷 2022-06-29 오후 1 53 55" src="https://user-images.githubusercontent.com/99342700/176354581-5cdb16fb-dc1e-49b3-8f0e-1382ad57ea8f.png">

1. 입력받을 변수와 출력 할 결과값 변수 지정.
2. 입력받은 변수에 100의자리만 따로 저장.
3. 각 100의자리 수 비교 후 결과값 저장.
4. 결과값 출력.

```c++
#include<stdio.h>

int main(void){
	int A=0; int B=0; int C=0; 
	char result;
	scanf("%d %d %d",&A, &B, &C);
	A = (A/100) % 10;
	B = (B/100) % 10;
	C = (C/100) % 10;

	result = (A == B && A == C) * 'T' +
	(A == B && A != C) * 'D' +
	(A != B && A == C) * 'D' +
	(B == C && B != A) * 'D' +
	( (A != B && A != C) && (B != C && B != A) ) * 'S';

	printf("%c",result);
	return 0;
}
```



### C_과제 4.c
4자리 양수를 입력받은 후 그 수를 뒤집은 숫자와의 차의 절대값을 출력하는 프로그램 을 작성하시오.
- 힌트: 절대값을 계산하여 출력할 때 조건 연산자( ? )를 이용하시오.

<img width="302" alt="스크린샷 2022-06-29 오후 2 23 08" src="https://user-images.githubusercontent.com/99342700/176358032-4a85ce7f-6ef0-49fb-8312-12c5a9044a93.png">

1. 입력받을 변수와 각 자릿수를 표현 할 변수, 결과값 변수를 지정.
2. 자릿수를 표현 할 변수에 각 자릿수 저장.
3. 저장한 각 지릿수 변수들을 모두 더하여 뒤집은 값 만들기.
4. 기존의 값과 뒤집은 값을 빼기.
5. 조건 연산자를 이용하여 뺀 값이 양수면 그대로 출력 / 음수면 반대로 계산하여 출력.

```c++
#include <stdio.h>
int main(void)
{
  	int a=0; int b=0; int c=0; int d=0;
  	int n=0; int result=0; int add=0;
	scanf("%d", &n);

	a = n/1000;
	b = ((n/100)%10) * 10;
	c = ((n/10)%10) * 100;
	d = (n%10) * 1000;
	
	add = a+b+c+d;
	result = n - add;

	result > 0 ? printf("%d",n-add) : printf("%d",add-n);

  	return 0;
}
```


### C_과제 5.c
세 자리 양의 정수 한 개를 입력 받아 각 자리수 중에서 최소값을 찾아 출력하시오. 각 자리수는 서로 다르다고 가정한다.
- 힌트: 관계연산자( a>b )와 논리연산자( && )와 괄호를 이용하시오. - if문등 배우지 않은 문법 사용금지

<img width="399" alt="스크린샷 2022-06-29 오후 4 49 31" src="https://user-images.githubusercontent.com/99342700/176381866-6dc59c64-2b82-463b-8bbc-ec0bd45a26c8.png">

1. 입력 받을 변수와 각 자릿수의 변수, 출력 할 결과값 변수를 지정.
2. 각 자릿수를 변수에 저장.
3. 연산을 사용하여 최소값 찾기.
4. 결과값 출력.

```c++
#include <stdio.h>
int main(void){
	int N=0; int a=0,b=0,c=0; int result=0;
	scanf("%d",&N);

	a = (N/100) % 10;
	b = (N/10) % 10;
	c = N % 10;

	result = ( (a < b) && (a < c)) * a +
	( (b < a) && (b < c) ) * b +
	( (c < a) && (c < b) ) * c;

	printf("%d",result);

  	return 0;
}
```



### C_과제 6.c
정수 세 개를 입력 받는다. 세 수 중에서 중앙값을 출력하시오. 같은 수는 입력되지 않 는다고 가정한다.
-힌트: [문제5]번과해결방법이비슷하다. - if문등 배우지 않은 문법 사용금지

<img width="404" alt="스크린샷 2022-06-29 오후 5 03 48" src="https://user-images.githubusercontent.com/99342700/176384753-2e652e4c-a965-4060-8705-60ed846a73cd.png">

1. 5번 문제와 동일한 방식으로 세팅.
2. 각 자릿수 중 중간값인 경우 결과값에 저장.
3. 결과값 출력.

```c++
#include <stdio.h>
int main(void){
	int N=0; int a=0,b=0,c=0; int result=0;
	scanf("%d",&N);

	a = (N/100) % 10;
	b = (N/10) % 10;
	c = N % 10;

	result = ( (a < b && a > c) || (a > b && a < c) ) * a +
	( (b < a && b > c) || (b > a && b < c) ) * b +
	( (c < a && c > b) || (c > a && c < b) ) * c;

	printf("%d",result);

  	return 0;
}
```

</div>
</details>

<details>
<summary> 조건문 </summary>
<div markdown="1">

# C_Programming 과제.2 (조건문)

### C_과제 1.c
세 과목 점수 (0~100점 사이 정수)를 입력받는다. 세 과목 평균점수가 ◌ 90점 이상이면 “A”출력
◌ 80점 이상이면 “B”출력
◌ 70점 이상이면 “C” 출력
◌ 60점 이상이면 “D” 출력
◌ 어느 조건에도 해당되지 않으면 “F”가 출력되도록 작성하시오. – 그다음, 입력된 값들 중 최대값과 최소값을 화면에 출력하시오.

<img width="298" alt="스크린샷 2022-06-29 오후 6 19 13" src="https://user-images.githubusercontent.com/99342700/176401223-471d2e30-7029-4eff-824e-8c52c1421356.png">

1. 입력 받을 세개의 정수와 평균값을 저장 할 변수 지정.
2. 세개의 정수를 모두 더한 후 정수의 갯수 만큼 나눠서 평균값 변수에 저장.
3. 조건문을 사용하여 해당 문제에 명시된 조건에 맞추어 각각 기준 점수를 지정한 후 해당 점수일 시 출력.
4. 조건문을 사용하여 가장 큰 정수를 찾아서 출력.
5. 조건문을 사용하여 가장 작은 정수를 찾아서 출력.

```c++
#include <stdio.h>
int main(void){
	int A=0,B=0,C=0,avg=0;
	scanf("%d %d %d",&A,&B,&C);

    avg = (A+B+C)/3;

    if(avg >= 90){
        printf("A\n");
    }
    else if(avg >= 80){
        printf("B\n");
    }
    else if(avg >= 70){
        printf("C\n");
    }
    else if(avg >= 60){
        printf("D\n");
    }
    else{
        printf("F\n");
    }

    if(A > B && A > C){
        printf("max : %d\n",A);
    }
    else if(B > A && B > C){
        printf("max : %d\n",B);
    }
    else if(C > A && C > B){
        printf("max : %d\n",C);
    }

    if(A < B && A < C){
        printf("min : %d\n",A);
    }
    else if(B < A && B < C){
        printf("min : %d\n",B);
    }
    else if(C < A && C < B){
        printf("min : %d\n",C);
    }
	
  	return 0;
}
```



### C_과제 2.c
변종 분식에는 아래와 같은 메뉴가 있다. 대한이는 민국이와 함께 만 원짜리 지폐 한 장으로 들고 3개의 메뉴를 시켜 먹었다. 총 금액과 잔돈을 계산하여 예시와 같이 출력하는 프로그 램을 작성하시오.
- 음식 값이 예산(만원)을 초과하는 경우에는 잔돈이 아닌 “Insufficient Money”를 출력한다. - 메뉴 중복 선택가능. (예시) 메뉴 입력이 2 2 2처럼 같은 메뉴 주문도 가능하다.
- 메뉴는 무조건 3개를 시킨다.

<img width="490" alt="스크린샷 2022-06-29 오후 6 41 51" src="https://user-images.githubusercontent.com/99342700/176405971-9ecd71c1-6866-4e50-bcfb-7261816aa039.png">
<img width="391" alt="스크린샷 2022-06-29 오후 6 42 16" src="https://user-images.githubusercontent.com/99342700/176406003-a82e316f-9bdf-445d-8835-1d22e09e2890.png">

1. 입력 받을 변수, 각 메뉴, 총 금액, 남은 금액 변수 지정.
2. 입력 받은 변수 별로 각 메뉴를 지정했을 때 값을 총 금액에 더해주고 남은 금액에서는 빼기.
3. 남은 금액이 음수일 시 "Insufficient Money" 출력 양수일 시 총 금액과 남은 금액 출력.

```c++
#include <stdio.h>
int main(void){
	int N=0,M=0,S=0;
	int A=5000,B=2500,C=2000,D=1500,E=1000;
	int total=0;
	int money=10000;

	scanf("%d %d %d",&N,&M,&S);

	if(N == 1){
		total = total + A;
		money = money - A;
	}
	else if(N == 2){
		total = total + B;
		money = money - B;
	}
	else if(N == 3){
		total = total + C;
		money = money - C;
	}
	else if(N == 4){
		total = total + D;
		money = money - D;
	}
	else if(N == 5){
		total = total + E;
		money = money - E;
	}

	if(M == 1){
		total = total + A;
		money = money - A;
	}
	else if(M == 2){
		total = total + B;
		money = money - B;
	}
	else if(M == 3){
		total = total + C;
		money = money - C;
	}
	else if(M == 4){
		total = total + D;
		money = money - D;
	}
	else if(M == 5){
		total = total + E;
		money = money - E;
	}

	if(S == 1){
		total = total + A;
		money = money - A;
	}
	else if(S == 2){
		total = total + B;
		money = money - B;
	}
	else if(S == 3){
		total = total + C;
		money = money - C;
	}
	else if(S == 4){
		total = total + D;
		money = money - D;
	}
	else if(S == 5){
		total = total + E;
		money = money - E;
	}

	if(money < 0){
		printf("Insufficient Money");
	}
	else{
		printf("Total:%d\nChange:%d",total,money);
	}



  	return 0;
}
```



### C_과제 3.c
문자 1개와 숫자 1개를 예시와 같이 입력할 경우, 문자를 입력한 숫자만큼 증가 (예시 1) 시키는 프로그램을 작성하라.
- 조건) 대문자 및 소문자에 대해서 적용되며 숫자 및 특수문자는 입력한 글자를 그대로 출력한 다. 대문자의 끝 'Z'에 도달 한 경우 앞 'A'로 이동한다. 소문자 'z' 다음에는 소문자 'a'로 이동 한다. (힌트: 나머지 연산자 ‘%’ 사용)

<img width="445" alt="스크린샷 2022-06-29 오후 7 06 44" src="https://user-images.githubusercontent.com/99342700/176411114-7ee3c149-5eec-4e7c-8a3d-355f17239327.png">

1. 입력 받을 변수와 연산 할 변수 지정.
2. 소문자 / 대문자 / 그 외 범위 별로 나누어 조건문 사용.
3. 입력 받은 문자의 아스키코드 값에서 해당 범위의 알파벳 만큼 뺀 후 이동 할 값을 더하기.
4. 위에서 계산한 값을 아스키코드 값으로 나누어서 'Z'값이 넘어갈 때 다시 알파벳 맨 처음으로 오도록 세팅.
5. 세팅된 값에서 처음에 뺀 범위 내의 알파벳 더하기.
6. 각각 나온 값을 출력. (알파벳이 아닌경우 그대로 출력)

```c++
#include <stdio.h>
int main(void){
	char ch; int N=0; int M='Z'-'A'+1;
	scanf("%c %d",&ch,&N);

	if(ch >= 'a' && ch <= 'z'){
		ch = (ch - 'a' + N) % M + 'a';
		printf("%c",ch);
	}
	else if(ch >= 'A' && ch <= 'Z'){
		ch = (ch - 'A' + N) % M + 'A';
		printf("%c",ch);
	}
	else{
		printf("%c",ch);
	}
  	return 0;
}
```



### C_과제 4.c
두 자리 10진 정수를 입력 받은 후 영어단어로 변환하는 프로그램을 작성하시오. 예) 45를 입력할 경우 “forty-five”를 출력한다. 단, 입력된 정수가 두 자리 10진 정수가 아닌 경우 "none"을 출력한다.
- 힌트: if문안에 switch문을 사용한다(중첩).

<img width="299" alt="스크린샷 2022-06-29 오후 7 26 50" src="https://user-images.githubusercontent.com/99342700/176415087-f70bace0-003f-47df-a1c4-d770de303898.png">

1. 입력 할 변수와 각 자릿수 별로 출력 할 변수 지정.
2. 10~19까지 스위치문을 입력하여 출력.
3. 20 이상이면 스위치문을 이용하여 10의자리와 1의자리 각각 출력.
4. 범위 내에 해당 안될 시 "none"출력.

```c++
#include <stdio.h>

int main(void){
    int N=0; int max=0; int min=0;
    scanf("%d",&N);
    if(N>=10 && N <100){
        if(N >= 10 && N < 20){
            switch (N)
            {
            case 10 : printf("ten");
                break;
            case 11 : printf("eleven");
                break;
            case 12 : printf("twelve");
                break;
            case 13 : printf("thirteen");
                break;
            case 14 : printf("fourteen");
                break;
            case 15 : printf("fifteen");
                break;
            case 16 : printf("sixteen");
                break;
            case 17 : printf("seventeen");
                break;
            case 18 : printf("eighteen");
                break;
            case 19 : printf("nineteen");
                break;
            }
        }
        else{
            max = N/10; 
            min = N%10; 
            switch (max) 
            {
            case 2 : printf("twenty");
                break;
            case 3 : printf("thirty");
                break;
            case 4 : printf("forty");
                break;
            case 5 : printf("fifty");
                break;
            case 6 : printf("sixty");
                break;
            case 7 : printf("seventy");
                break;
            case 8 : printf("eighty");
                break;
            case 9 : printf("ninety");
                break;
            } 
            switch (min)
            {
            case 1 : printf("-one");
                break;
            case 2 : printf("-two");
                break;
            case 3 : printf("-three");
                break;
            case 4 : printf("-four");
                break;
            case 5 : printf("-five"); 
                break;
            case 6 : printf("-six");
                break;
            case 7 : printf("-seven");
                break;
            case 8 : printf("-eight");
                break;
            case 9 : printf("-nine"); 
                break;
            }
        }
    }
    else{
        printf("none");
    }

    return 0;
}
```



### C_과제 5.c
5자리의 양의 정수를 입력 받아 앞의 세 자리로 지역을 구분하는 프로그램을 if 문(문 제 5)과 switch 문(문제 6)으로 각각 완성하시오. 마지막 두 자리는 00으로 가정한다. 서울은 100, 101, 102로 시작한다. 입력의 오류(20100, 10111, 100123, - 10100, 70000, ... 등 형식에 맞지 않 는 입력값)에 대하여 none을 출력한다.

<img width="439" alt="스크린샷 2022-06-29 오후 7 42 10" src="https://user-images.githubusercontent.com/99342700/176417964-b16dae38-a859-42b4-a4bc-0c10e9304518.png">

1. 입력 받을 변수와 100의자리로 나타낼 변수 지정.
2. 입력 받은 변수를 100으로 너누어 100의자리 정수로 만들기.
3. if문을 이용하여 변수 중 1의자리의 수를 케이스별로 나누어 출력. 
4. 해당 조건에 해당하지 않을 시 "none"출력.

```c++
#include <stdio.h>

int main(void){
    int N=0; int HND=0;
    scanf("%d",&N);
    HND = N/100;
    if(HND==100){
        printf("Seoul");
    }
    else if(HND==101){
        printf("Seoul");
    } 
    else if(HND==102){
        printf("Seoul");
    }
    else if(HND==103){ 
        printf("Busan");
    }
    else if(HND==104){
        printf("Busan");
    }
    else if(HND==105){
        printf("Gwangju");
    }
    else{
        printf("none");
    }

    return 0;
}
```

### C_과제 6.c
5자리의 양의 정수를 입력 받아 앞의 세 자리로 지역을 구분하는 프로그램을 if 문(문 제 5)과 switch 문(문제 6)으로 각각 완성하시오. 마지막 두 자리는 00으로 가정한다. 서울은 100, 101, 102로 시작한다. 입력의 오류(20100, 10111, 100123, - 10100, 70000, ... 등 형식에 맞지 않 는 입력값)에 대하여 none을 출력한다.

<img width="439" alt="스크린샷 2022-06-29 오후 7 42 10" src="https://user-images.githubusercontent.com/99342700/176417964-b16dae38-a859-42b4-a4bc-0c10e9304518.png">

1. 입력 받을 변수와 100의자리로 나타낼 변수 지정.
2. 입력 받은 변수를 100으로 너누어 100의자리 정수로 만들기.
3. switch문을 이용하여 변수 중 1의자리의 수를 케이스별로 나누어 출력. 
4. 해당 조건에 해당하지 않을 시 "none"출력.

```c++
#include <stdio.h>

int main(void){
    int N=0; int HND=0;
    scanf("%d",&N);
    HND = N/100; 
    switch (HND)
    {
    case 100 : printf("Seoul");
        break;
    case 101 : printf("Seoul");
        break;
    case 102 : printf("Seoul");
        break;
    case 103 : printf("Busan");
        break;
    case 104 : printf("Busan");
        break;
    case 105 : printf("Gwangju");
        break;
    
    default: printf("none");
        break;
    }
    return 0;
}
```

</div>
</details>

<details>
<summary> 반복문 </summary>
<div markdown="1">

# C_Programming 과제.3 (반복문)

### C_과제 1-2.c
N개의 정수 M을 입력 받아, M과 M의 약수를 예시와 같이 출력하시오.
(단, N ≥ 3, M의 3자리 이상 정수) - 입력받은 각 정수에 대하여, (1) 입력된 정수를 그대로 출력하고
(2) 입력된 정수의 약수를 출력하고
(3) 각 정수에 대한 약수의 개수를 출력하고
(4) 약수의 개수가 가장 많은 M을 출력
(약수의 개수가 동일한 정수가 있을 경우, 첫 번째 일치하는 정수만 해당함)

<img width="594" alt="스크린샷 2022-06-30 오후 6 07 11" src="https://user-images.githubusercontent.com/99342700/176638774-501729b2-b790-41d7-9623-25906bb17203.png">

1. 각각의 변수 지정.
2. N번 만큼의 반복을 할 for문을 입력.
3. 이중 for문으로 약수를 구하여 약수일 시 출력과 갯수 추가.
4. 갯수 출력 후 줄 바꿈.
5. 카운트값을 비교하여 조건에 맞을 시 새로운 카운트 변수에 기존 카운트값 저장.
6. 카운트값이 가장 높은 값 출력.

```c++
#include <stdio.h>

int main(void){
    int N=0,M=0,cnt=0,ccnt=0,max=0;
	scanf("%d",&N);

	for(int i=0; i<N; i++){
		scanf("%d",&M);
		printf("%d:",M);
		for(int j=1; j<=M; j++){
			if(M%j==0){
				printf(" %d",j);
				cnt++;
			}
		}
		printf(" %d\n",cnt);
		if(ccnt < cnt){
			ccnt = cnt;
			max = M;
		}
		cnt=0;
	}
	printf("%d",max);
    return 0;
}
```



### C_과제 2-2.c
1 이상 1000 이하의 두 개의 양의 정수 N 과 M을 사용자로부터 입력 받아 N부터 M 까지의 각 숫자의 약수의 개수를 계산해서 약수의 개수가 가장 큰 수를 출력하고 그 수 의 약수의 개수도 함께 출력하시오. (만약, 약수의 개수가 가장 많은 수가 지정된 범위 내에서 여 러 개 존재할 때 가장 작은 수를 선택.)
단,각숫자의약수의개수는소인수분해를통해구하시오.숫자 을소인수의지수형태 n=ap xbq xcr 로나타낼수있을때,n의약수의개수는이다.예를들 어, 72 = 23 x 32 의 약수의 개수는  이다. 소인수 분해를 통해 계산했는지 확 인하기 위해 소인수의 지수 합 ()을 추가로 출력하시오.
- 입력: N M
- 출력: (약수의 개수가 가장 큰 수) (약수의 개수) (소인수의 지수 합)

<img width="393" alt="스크린샷 2022-06-30 오후 6 26 36" src="https://user-images.githubusercontent.com/99342700/176642754-0bad9f58-4560-41d4-90ae-3fb1816619b5.png">

1. 각각 변수 지정.
2. for문을 이용하여 N ~ M 까지 약수를 구하고 약수의 개수 1씩 올리기.
3. 갯수가 클 때 마다 i값(현재 N값) 저장.
4. 반복 연산으로 약수의 개수가 가장 큰 수와 그 약수의 개수를 출력.
5. 약수의 개수가 가장 큰 수를 2부터 나누며 다시 약수를 구하기.
6. 가장 큰 수가 0이 될 때 까지 반복 계산.
7. 소인수의 지수 합 출력.

```c++
#include <stdio.h>
int main(void)
{
  int N=0; int M=0; int cnt=0; int max=0; int answer=0;
  scanf("%d %d",&N,&M);
  if( ( N < 1 || N > 1000 ) || ( M < 1 || M > 1000 ) ){return -1;}
      for(int i=N; i<=M; i++){ 
        for(int j=2; j<=i; j++){ 
          if(i%j==0){
           cnt++;
          }
          if(max<cnt){ 
          max=cnt;
          answer=i; 
          }
        } 
         cnt=0;
      }    
       printf("%d %d ",answer,max+1);
      int f=2; int exp=0;
      while(answer>1){
        if(answer%f==0){
          exp++;
          answer=answer/f; 
        } 
        else{ 
          f++;
          if(answer%f==0){
            exp++;
            answer=answer/f;
          }
        } 
      } 
      printf("%d",exp); 
  return 0;
}
```



### C_과제 3.c
<img width="481" alt="스크린샷 2022-06-30 오후 6 37 42" src="https://user-images.githubusercontent.com/99342700/176645175-9c1ee1a6-0335-468e-a16a-6b5cc777110d.png">
<img width="462" alt="스크린샷 2022-06-30 오후 6 38 11" src="https://user-images.githubusercontent.com/99342700/176645183-362e91e2-3650-443e-9553-11cdbff88a3b.png">

1. 각각 변수 지정.
2. 조건을 충족하지 못할 시 주어진 멘트를 출력하며 종료.
3. 조건에 나온대로 순열 / 중복순열 / 조합 / 중복조합 을 계산하여 출력. 

```c++
#include <stdio.h>
int main(void)
{
    int n=0; int r=0; long long s=1; int nt=0; long long js=1;
    int rt=1; long long jj=1; int jt=0; long long j=1;

    scanf("%d %d",&n,&r); 
    if(n < r || r <= 0){ 
        printf("inputs n and r must satisfy '0 < r <= n'.");
        return -1;
    }

    nt = n;
    for(int i=0; i<r; i++){
        s = s * nt;
        nt--;
    }
    printf("%dP%d=%lld\n",n,r,s);

    for(int i=0; i<r; i++){
        js = js * n; 
    }
    printf("%dPI%d=%lld\n",n,r,js);

    for(int i=1; i<=r; i++){
        rt = rt * i;
    }
    j = s/rt;
    printf("%dC%d=%lld\n",n,r,j);

    jt = n + r -1; 
    for(int i=1; i<=r; i++){
        jj = jj * jt;
        jt--;
    }
    jj = jj / rt; 
    printf("%dH%d=%lld",n,r,jj);


  return 0;
}
```



### C_과제4-2.c
찾기 원하는 0이 아닌 한 자리 정수 T를 입력 받는다. 그 후 한 자리 혹은 여러 자리를 갖는 정수를 0이 나오기 전까지 지속적으로 입력 받은 다음 입력 받은 정수들에 T가 등장한 횟수, T 보다 작은 수가 등장한 횟수, T 보다 큰 수가 등장한 횟수를 출력하는 프로그램을 작성하시오. 이 때, 마지막에 입력된 0은 무시되며, 입력되는 수는 모두 양수라고 가정한다.

<img width="483" alt="스크린샷 2022-06-30 오후 6 47 51" src="https://user-images.githubusercontent.com/99342700/176647422-31873ae0-aed8-4be7-9718-27926e3a65a6.png">

1. 각각 변수 지정
2. 이중 반복문을 이용하여 각 자릿수의 값을 입력한 N과 비교하여 큰 값 / 작은 값 / 같은 값 나누어 저장.
3. 각각 나눈 변수 출력. 

```c++
#include <stdio.h>
int main(void)
{
  int N=0; int M=0; int num=0; int cnt=0,min=0,max=0;
  scanf("%d",&N);

  while(1){
	  scanf("%d",&M);
	  if(M == 0){break;}

	  for(int i=M; i>0; i=i/10){
		  num = i%10;
		  if(num == N){
			  cnt++;
		  }
		  else if(num > N){
			  max++;
		  }
		  else{
			  min++;
		  }
	  }	  
  }
  printf("%d %d %d",cnt,min,max);
  return 0;
}
```



### C_과제 5-3.c
정수 N을 입력 받아 (N>0)
- 자리수가 짝수인 수들만 역순으로 만든 수를 출력하시오. 그런 다음, - 자리수가 홀수인 수들만 역순으로 만든 수를 출력하시오.

<img width="381" alt="스크린샷 2022-06-30 오후 7 03 50" src="https://user-images.githubusercontent.com/99342700/176650935-88e380d5-b102-4377-bda6-c4c7a3bd52a0.png">

1. 각각 필요한 변수 지정.
2. 입력받은 N이 0이 될 때 까지 반복.
3. 입력받은 값을 1의자리부터 나누며 각 자릿수가 짝수일 경우와 홀수일 경우 구분.
4. 짝수일 경우 자릿수를 곱하며 뒤집은 값이 나오게 연산.
5. 홀수일 경우 짝수일 경우와 마찬가지로 연산.
6. 짝수인 경우와 홀수인 경우 출력.

```c++
#include <stdio.h>
int main(void)
{
  int N=0; int num=0; int even=0,odd=0;
  scanf("%d",&N);

  for(int i=N; i>0; i=i/10){
	  num = i % 10;
	  if(num%2 == 0){
		  even = even * 10;
		  even = even + num;
	  }
	  else if(num%2 != 0){
		  odd = odd * 10;
		  odd = odd + num;
	  }
  }
  printf("%d %d",even,odd);
  return 0;
}
```



### C_과제 6-2.c
삼각형 높이를 나타내는 N을 종료 조건 시까지 반복해서 입력받고, 앞의 문 제(문제 1-1)와 동일한 사각형 모양을 순서대로 출력하는 프로그램을 작성하시오.
(단, 2 <= N <= 20)
- 종료조건: 0, 1, 음수, 3의 배수 입력

<img width="433" alt="스크린샷 2022-06-30 오후 7 17 46" src="https://user-images.githubusercontent.com/99342700/176653704-a93a459a-1063-4e19-963a-ac579b469ba4.png">

1. 각각 필요한 변수 지정.
2. 반복하여 입력을 받고, 입력 예시와 맞게 가로 세로 인덱스를 구축 할 반복문코드 작성.
3. 각 인덱스 별로 모양에 맞추어 공백 / O / X 지정 후 출력.

```c++
#include <stdio.h>
int main(void){
int N=0;

while(1){
  	scanf("%d",&N);
  	if(N <= 1 || N%3 == 0){return -1;}
  	for(int i=0; i<N; i++){
	  	for(int j=0; j<N*2-1; j++){
		  	if(i+j < N-1){
				  printf(" ");
		  	}
		  	else if(j-i > N-1){
				  printf(" ");
		  	}
		  	else if(i+j == N-1){
				  printf("O");
		  	}
		  	else if(j-i == N-1){
				  printf("O");
		 	}
		  	else if(i == N-1){
				  printf("O");
		  	}
		  	else if(i+j >= N){
				  printf("X");
		  	}
	 	}
	  	printf("\n");
  	}
  }	  
  return 0;
}
```

</div>
</details>

<details>
<summary> 배열 </summary>
<div markdown="1">
# C Programming 4차 과제

### 1. C_과제 1-2.c
회문수는 순서대로 읽은 수와 거꾸로 읽은 수가 일치하는 수를 말한다. 예를 들면
34543은 회문수이고, 34567은 회문수가 아니다. 정수 M1과 M2를 먼저 입력받고, 종료 조건까지 정수
N을 반복해서 입력받는다. (1) 정수 N을 한 자리씩 나누어, 가장 마지막 자릿수부터 순차적으로 배열 Y에 저장한다. (정수 N
의 일의 자릿수가 Y[0]의 원소가, 십의 자릿수가 Y[1]의 원소가 되는 방식이다.) (2) 배열 Y의 원소 중 인덱스 M1과 M2 위치의 원소를 삭제한다. 단, M1 또는 M2가 배열 Y의 원소의 수보다 큰 경우, 해당 위치에서 삭제되는 원소는 없다. (3) 배열 Y의 남은 원소로 만들어지는 정수가 회문수이면, 이때의 정수 N을 배열 X에 저장한다. (4) 배열 X에 저장된 정수를 가장 큰 수부터 내림차순으로 정렬하여 출력한다. (5) 입력된 정수 중 조건을 만족하는 정수가 하나도 없는 경우, “none”을 출력한다.
 - 종료 조건 : 0 또는 음수 입력
 - 입력되는 정수의 최대 개수는 100이다.
 - 입력된 정수 N 중에, Y[M1]과 Y[M2]의 자릿수를 삭제한 후, 남는 자릿수가 없는 정수는 없다고 가정한다.

 <img width="587" alt="스크린샷 2022-07-04 오전 2 48 55" src="https://user-images.githubusercontent.com/99342700/177051448-0efe1d33-5e2e-4431-8e02-d3d82fe6d17b.png">

1. 배열 및 정수 변수 지정.
2. for문을 이용하여 입력받은 정수N을 Y배열에 역순으로 저장.
3. for문을 이용하여 입력받은 M1,M2인덱스를 제외한 값을 Z배열에 저장.
4. for문을 이용하여 Z배열의 첫 번째 인덱스와 마지막 인덱스 부터 안쪽으로 차례대로 비교하며 카운트.
5. 만약 인덱스의 값과 비교한 카운트 값이 같을 경우 회문수이므로 X배열에 회문수 저장.
    - 한번이라도 회문수가 나오면 체크.(체크가 한번도 안되면 "none" 출력)
6. X배열 안에있는 값을 내림차순으로 저장.
7. X배열 순서대로 출력.

```c++
#include <stdio.h>

int main(void){
	int X[100]={0},Y[100]={0},Z[100]={0};
	int M1=0,M2=0,N=0,cnt=0,st=0,temp=0,idx=0,result=0,check=0;;
	scanf("%d %d",&M1,&M2);

	while(1){
		scanf("%d",&N);
		if(N < 1){break;}

		for(int i=N; i>0; i=i/10){
			Y[idx++] = i % 10;
			cnt++;
		}
		idx = 0;

		for(int i=0; i<cnt; i++){
			if(i == M1 || i == M2){
				continue;
			}
			else{
				Z[idx++] = Y[i];
			}
		}

		for(int i=0; i<idx; i++){
			if(Z[i] == Z[idx-1-i]){
				temp++;
			}
		}

		if(idx == temp){
			X[result++] = N;
			check = 1;
		}
		temp = 0;
		idx = 0;
		cnt = 0;
	}

	for(int i=0; i<result; i++){
		for(int j=0; j<result; j++){
			if(X[i] > X[j]){
				st = X[i];
				X[i] = X[j];
				X[j] = st;
			}
		}
	}
	if(check == 1){
		for(int i=0; i<result; i++){
			printf("%d ",X[i]);
		}
	}	
	else{
		printf("none");
	}
    return 0;
}
```



### C_과제 2-2.c
종료 조건까지 문자를 반복해서 입력받아, 배열 X에 저장한다.
 (1) 배열 X에 저장된 문자 중 중복된 문자는 제외하고 배열 Y에 저장한다. 동일한 문자가 여러
번 나오는 경우, 가장 처음에 입력된 문자를 배열 Y에 저장한다.
 (2) 배열 Y에 저장된 문자들을 출력한다.
 (3) 정수 M을 입력받고, M개의 문자를 입력받아 배열 Z에 저장한다. 단, M≤N.
 (4) 배열 Y에 저장된 문자 중에 배열 Z에 저장된 M개의 문자가 연속해서 나타나면, 배열 Y에서 연속된 M개 문자의 시작 위치(배열의 인덱스 값)을 출력한다. (5) 배열 Y에 저장된 문자 중에 배열 Z에 저장된 M개의 문자가 연속해서 나타나지 않으면
“none”을 출력한다.
 - 종료 조건 : 문자 ‘!’ 입력
 - 입력되는 문자의 최대 개수는 100이다. 
 - M 입력 후 배열 Z에 문자들을 입력받아 저장하기 전에  getchar();  문장을 사용해서
  <enter>를 읽어 들여야 함

<img width="622" alt="스크린샷 2022-07-05 오후 12 59 34" src="https://user-images.githubusercontent.com/99342700/177247102-f3fe15b0-1e1c-4c92-99a2-b3ff2f91a300.png">

1. 문제에 맞는 변수 지정.
2. 종료조건 전까지 무한루프를 이용하여 반복 계산.
3. 입력한 X배열에 중복되는 문자가 나오면 카운트를 하여 카운트가 자기자신 외에 더 있으면 Y배열에 저장 안함.
4. 중복되지 않은 문자들로 이루어진 Y배열 출력.
5. M을 입력받고 M크기 만큼의 문자를 새로운 배열 Z에 저장.
6. for문을 이용하여 같은 문자가 나오면 그 다음 문자들도 같은지 확인.
7. 몇번째에서 해당 문자가 시작하는지 카운트 후 출력.
8. 그 외에는 none출력.

```c++
#include <stdio.h>

int main(void){
    char X[100],Y[100],Z[100];
	int idx=0,cnt=0,ccnt=0,temp=0,M=0,a=0,b=0,c=0;

	while(1){
		scanf("%c",&X[idx++]);
		if(X[idx-1] == '!'){break;}
	} 

	for(int i=0; i<idx; i++){
		for(int j=i; j>=0; j--){
			if(X[i] == X[j]){
				cnt++;
			}
		}
		if(cnt == 1){
			Y[temp++] = X[i];
		}
		cnt=0;
	}

	for(int i=0; i<temp-1; i++){
		printf("%c",Y[i]);
	}

	scanf("%d",&M);
	getchar();

	for(int i=0; i<M; i++){
		scanf("%c",&Z[i]);
	}

	for(int i=0; i<temp; i++){
		for(int j=0; j<M; j++){
			if(Y[i] == Z[j]){
				a = i;
				b = j;
				for(int k=0; k<M-1; k++){
					if(Y[++a] == Z[++b]){
						ccnt++;
					}
				}
			}
		}
		if(ccnt == M-1){
			printf("\n%d",i);
			c = 1;
		}
		ccnt=0;
	}
	if(c == 0){
		printf("\nnone");
	}

    return 0;
}
```



### C_과제 3-2.c
1부터 20까지 정수를 배열 A[0]에서 A[19]에 순서대로 저장하고, 양의 정수 F(<20), R(F<R<20), M을 입력받아 A[F]부터 A[R]까지의 정수 중, A[R]부터 M개의 정수를 하나씩 오른쪽으로 이동시키는 프로그램을 작성하시오. M은 R-F+1보다 작은 수이다.

<img width="788" alt="스크린샷 2022-07-06 오후 4 18 26" src="https://user-images.githubusercontent.com/99342700/177492631-bcf822db-61fb-48ea-8d6f-5dee5cabd900.png">

1. 조건에 맞게 변수 지정.
2. 범위 내의 인덱스 크기 구하기.
3. 해당 인덱스 범위 내의 값들을 새로운 배열에 저장.
4. 새롭게 저장한 배열을 기존 배열의 N부터 차례로 저장하고 출력.

```c++
#include <stdio.h>

int main(void){
    int arr[20] = {1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20}; 
	int X[20] = {0};
	int F=0,R=0,M=0,N=0,next=0,idx=0,cnt=0; 
	scanf("%d %d %d",&F,&R,&M); 

	N = R - M + 1;
	next = R;

	for(int i=N; i<=R; i++){
		X[idx++] = arr[i]; 
		cnt++; 
	}
	idx = cnt-1;

	for(int i=N; i<=R; i++){
		arr[i] = X[idx++]; 
		if(idx == cnt){
			idx = 0;
		}
	}

	for(int i=0; i<20; i++){ 
		printf("%d ",arr[i]);
	}

    return 0;
}
```



### C_과제 4-3.c
정수 N을 입력받고, N개의 정수 읽어 들여 1, 2단계 [ 문제 4-1 ] [ 문제 4-2 ]를 수 행한후, 결과로나온배열에다시2단계[문제4-2]를계속적용하여전체N개의정수중가 장 큰 수, 가장 작은 수가 남을 때 까지 반복하는 프로그램을 작성하시오.

<img width="788" alt="스크린샷 2022-07-06 오후 4 18 26" src="https://user-images.githubusercontent.com/99342700/177605977-a841542b-3f49-4c36-8e0b-cc2e2de639ad.png">

1. 각 변수 지정.
2. 입력 받은 크기로 각 배열 변수 지정.
3. 입력 받은 배열을 역순으로 출력.
4. 각 최대/최소 변수에 배열의 첫 번째 인덱스 저장.
5. 반복할 때 i는 3칸씩 이동.
6. max변수에 가장 큰 값 저장.
7. min변수에 가장 작은 값 저장.
8. 배열에 최대/최소값 각각 저장 후 출력.

```c++
#include <stdio.h>

int main(void){
    int N=0,idx=0,cnt=0,M=0,max=0,min=0;
	scanf("%d",&N);
	int arr[N],temp[N],X[N],Y[N],max_cnt[N],min_cnt[N];

	for(int i=0; i<N; i++){
		scanf("%d",&arr[i]);
		temp[i] = arr[i];
	}

	for(int i=N-1; i>=0; i--){
		printf(" %d",arr[i]);
	}
	printf("\n");

	while(1){
		idx=0;
		for(int i=0; i<N; i=i+3){
			max = arr[i];
			min = temp[i];
			for(int j=i; j<i+3 && j<N; j++){
				if(max < arr[j]){
					max = arr[j];
				}
				if(min > temp[j]){
					min = temp[j];
				}
			}
			max_cnt[idx] = max;
			min_cnt[idx] = min;
			idx++;
		}


		for(int i=0; i<idx; i++){
			printf(" %d",max_cnt[i]);
		}
		printf("\n");
		for(int i=0; i<idx; i++){
			printf(" %d",min_cnt[i]);
		}
		printf("\n");
		N = idx;
		if(N == 1){
			break;
		}
		for(int i=0; i<N; i++){
			arr[i] = max_cnt[i];
			temp[i] = min_cnt[i];
		}
	}
	return 0;
}
```



### C_과제 5-2.c
두 집합 A, B 의 원소를 합쳐서 합집합을 만들려고 한다. 두 집합의 원소는 각각 음 수가 입력될 때까지의 원소이다. 문제 5-1처럼 중복된 원소가 입력될 수 있고 이 때는 집합에 추 가되지 않아야 한다. 합집합은 두 집합이 합쳐 진 후 정렬을 하여 오름차순으로 출력한다.
각 줄에서, 음수를 제외하고 최대 100개의 정수가 입력된다.

<img width="697" alt="스크린샷 2022-07-07 오후 7 03 15" src="https://user-images.githubusercontent.com/99342700/177748308-cf2affc1-157a-475d-95c6-e1e23240b4f5.png">

1. 필요한 배열 및 변수 지정.
2. 종료조건 전까지 입력받고 입력받은 값은 A,B배열에 저장.
3. 현재 위치부터 0인덱스까지 비교하며 같은 경우가 자기 자신 밖에 없을 때 새로운 배열에 저장.(반복된 수 제거)
4. 반복 제거한 두 배열을 하나의 배열로 합치기.
5. 합친 배열에 반복값이 있는지 확인하고 반복된 수는 제외하고 새로운 배열에 저장.
6. 가장 작은 수 부터 정렬하며 오름차순으로 저장.
7. 해당 배열 출력.

```c++
#include <stdio.h>

int main(void){
    int A[101],B[101],C[101],D[101],E[202],F[101],G[101];
	int idx=0,idx2=0,idx3=0,idx4=0,idx5=0,cnt=0,num1=0,num2=0,add=0,min=99999999,n=0,temp=0;

	while(1){
		scanf("%d",&temp);
		if(temp < 0){break;}
		A[num1++] = temp;
	} 
	
	while(1){
		scanf("%d",&temp);
		if(temp < 0){break;}
		B[num2++] = temp;
	}

	for(int i=0; i<num1; i++){
		for(int j=i; j>=0; j--){
			if(A[i] == A[j]){
				cnt++;
			}
		}
		if(cnt==1){
			C[idx++] = A[i]; 
		}
		cnt=0;
	}
	cnt=0;
	for(int i=0; i<num2; i++){
		for(int j=i; j>=0; j--){
			if(B[i]==B[j]){
				cnt++;
			}
		}
		if(cnt==1){
			D[idx2++] = B[i];
		}
		cnt=0;
	}
	cnt=0;

	add = idx + idx2;

	for(int i=0; i<idx; i++){
		E[idx3++] = C[i]; 
	}

	for(int i=0; i<idx2; i++){
		E[idx3++] = D[i];
	}

	for(int i=0; i<add; i++){
		for(int j=i; j>=0; j--){
			if(E[i] == E[j]){
				cnt++;
			}
		}
		if(cnt == 1){
			F[idx4++] = E[i];
		}
		cnt=0;
	}

	for(int i=0; i<idx4; i++){
		for(int j=0; j<idx4-1; j++){
			if(F[j] > F[j+1]){
				min = F[j];
				F[j] = F[j+1];
				F[j+1] = min;
			}
		}
	}

	for(int i=0; i<idx4; i++){
		printf("%d ",F[i]);
	}


	return 0;
}
```
</div>
</details>

<details>
<summary> 함수 </summary>
<div markdown="1">

# C_Programming 5차 과제

### 1. C_과제 1-2.c
회문수는 순서대로 읽은 수와 거꾸로 읽은 수가 일치하는 수를 말한다. 예를 들면
34543은 회문수이고, 34567은 회문수가 아니다. 정수 M1과 M2를 먼저 입력받고, 종료 조건까지 정수
N을 반복해서 입력받는다. (1) 정수 N을 한 자리씩 나누어, 가장 마지막 자릿수부터 순차적으로 배열 Y에 저장한다. (정수 N
의 일의 자릿수가 Y[0]의 원소가, 십의 자릿수가 Y[1]의 원소가 되는 방식이다.) (2) 배열 Y의 원소 중 인덱스 M1과 M2 위치의 원소를 삭제한다. 단, M1 또는 M2가 배열 Y의 원소의 수보다 큰 경우, 해당 위치에서 삭제되는 원소는 없다. (3) 배열 Y의 남은 원소로 만들어지는 정수가 회문수이면, 이때의 정수 N을 배열 X에 저장한다. (4) 배열 X에 저장된 정수를 가장 큰 수부터 내림차순으로 정렬하여 출력한다. (5) 입력된 정수 중 조건을 만족하는 정수가 하나도 없는 경우, “none”을 출력한다.
 - 종료 조건 : 0 또는 음수 입력
 - 입력되는 정수의 최대 개수는 100이다.
 - 입력된 정수 N 중에, Y[M1]과 Y[M2]의 자릿수를 삭제한 후, 남는 자릿수가 없는 정수는 없다고 가정한다.

 <img width="587" alt="스크린샷 2022-07-04 오전 2 48 55" src="https://user-images.githubusercontent.com/99342700/177051448-0efe1d33-5e2e-4431-8e02-d3d82fe6d17b.png">

1. 배열 및 정수 변수 지정.
2. for문을 이용하여 입력받은 정수N을 Y배열에 역순으로 저장.
3. for문을 이용하여 입력받은 M1,M2인덱스를 제외한 값을 Z배열에 저장.
4. for문을 이용하여 Z배열의 첫 번째 인덱스와 마지막 인덱스 부터 안쪽으로 차례대로 비교하며 카운트.
5. 만약 인덱스의 값과 비교한 카운트 값이 같을 경우 회문수이므로 X배열에 회문수 저장.
    - 한번이라도 회문수가 나오면 체크.(체크가 한번도 안되면 "none" 출력)
6. X배열 안에있는 값을 내림차순으로 저장.
7. X배열 순서대로 출력.

```c++
#include <stdio.h>

int main(void){
	int X[100]={0},Y[100]={0},Z[100]={0};
	int M1=0,M2=0,N=0,cnt=0,st=0,temp=0,idx=0,result=0,check=0;;
	scanf("%d %d",&M1,&M2);

	while(1){
		scanf("%d",&N);
		if(N < 1){break;}

		for(int i=N; i>0; i=i/10){
			Y[idx++] = i % 10;
			cnt++;
		}
		idx = 0;

		for(int i=0; i<cnt; i++){
			if(i == M1 || i == M2){
				continue;
			}
			else{
				Z[idx++] = Y[i];
			}
		}

		for(int i=0; i<idx; i++){
			if(Z[i] == Z[idx-1-i]){
				temp++;
			}
		}

		if(idx == temp){
			X[result++] = N;
			check = 1;
		}
		temp = 0;
		idx = 0;
		cnt = 0;
	}

	for(int i=0; i<result; i++){
		for(int j=0; j<result; j++){
			if(X[i] > X[j]){
				st = X[i];
				X[i] = X[j];
				X[j] = st;
			}
		}
	}
	if(check == 1){
		for(int i=0; i<result; i++){
			printf("%d ",X[i]);
		}
	}	
	else{
		printf("none");
	}
    return 0;
}
```



### C_과제 2-2.c
종료 조건까지 문자를 반복해서 입력받아, 배열 X에 저장한다.
 (1) 배열 X에 저장된 문자 중 중복된 문자는 제외하고 배열 Y에 저장한다. 동일한 문자가 여러
번 나오는 경우, 가장 처음에 입력된 문자를 배열 Y에 저장한다.
 (2) 배열 Y에 저장된 문자들을 출력한다.
 (3) 정수 M을 입력받고, M개의 문자를 입력받아 배열 Z에 저장한다. 단, M≤N.
 (4) 배열 Y에 저장된 문자 중에 배열 Z에 저장된 M개의 문자가 연속해서 나타나면, 배열 Y에서 연속된 M개 문자의 시작 위치(배열의 인덱스 값)을 출력한다. (5) 배열 Y에 저장된 문자 중에 배열 Z에 저장된 M개의 문자가 연속해서 나타나지 않으면
“none”을 출력한다.
 - 종료 조건 : 문자 ‘!’ 입력
 - 입력되는 문자의 최대 개수는 100이다. 
 - M 입력 후 배열 Z에 문자들을 입력받아 저장하기 전에  getchar();  문장을 사용해서
  <enter>를 읽어 들여야 함

<img width="622" alt="스크린샷 2022-07-05 오후 12 59 34" src="https://user-images.githubusercontent.com/99342700/177247102-f3fe15b0-1e1c-4c92-99a2-b3ff2f91a300.png">

1. 문제에 맞는 변수 지정.
2. 종료조건 전까지 무한루프를 이용하여 반복 계산.
3. 입력한 X배열에 중복되는 문자가 나오면 카운트를 하여 카운트가 자기자신 외에 더 있으면 Y배열에 저장 안함.
4. 중복되지 않은 문자들로 이루어진 Y배열 출력.
5. M을 입력받고 M크기 만큼의 문자를 새로운 배열 Z에 저장.
6. for문을 이용하여 같은 문자가 나오면 그 다음 문자들도 같은지 확인.
7. 몇번째에서 해당 문자가 시작하는지 카운트 후 출력.
8. 그 외에는 none출력.

```c++
#include <stdio.h>

int main(void){
    char X[100],Y[100],Z[100];
	int idx=0,cnt=0,ccnt=0,temp=0,M=0,a=0,b=0,c=0;

	while(1){
		scanf("%c",&X[idx++]);
		if(X[idx-1] == '!'){break;}
	} 

	for(int i=0; i<idx; i++){
		for(int j=i; j>=0; j--){
			if(X[i] == X[j]){
				cnt++;
			}
		}
		if(cnt == 1){
			Y[temp++] = X[i];
		}
		cnt=0;
	}

	for(int i=0; i<temp-1; i++){
		printf("%c",Y[i]);
	}

	scanf("%d",&M);
	getchar();

	for(int i=0; i<M; i++){
		scanf("%c",&Z[i]);
	}

	for(int i=0; i<temp; i++){
		for(int j=0; j<M; j++){
			if(Y[i] == Z[j]){
				a = i;
				b = j;
				for(int k=0; k<M-1; k++){
					if(Y[++a] == Z[++b]){
						ccnt++;
					}
				}
			}
		}
		if(ccnt == M-1){
			printf("\n%d",i);
			c = 1;
		}
		ccnt=0;
	}
	if(c == 0){
		printf("\nnone");
	}

    return 0;
}
```



### C_과제 3-2.c
1부터 20까지 정수를 배열 A[0]에서 A[19]에 순서대로 저장하고, 양의 정수 F(<20), R(F<R<20), M을 입력받아 A[F]부터 A[R]까지의 정수 중, A[R]부터 M개의 정수를 하나씩 오른쪽으로 이동시키는 프로그램을 작성하시오. M은 R-F+1보다 작은 수이다.

<img width="788" alt="스크린샷 2022-07-06 오후 4 18 26" src="https://user-images.githubusercontent.com/99342700/177492631-bcf822db-61fb-48ea-8d6f-5dee5cabd900.png">

1. 조건에 맞게 변수 지정.
2. 범위 내의 인덱스 크기 구하기.
3. 해당 인덱스 범위 내의 값들을 새로운 배열에 저장.
4. 새롭게 저장한 배열을 기존 배열의 N부터 차례로 저장하고 출력.

```c++
#include <stdio.h>

int main(void){
    int arr[20] = {1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20}; 
	int X[20] = {0};
	int F=0,R=0,M=0,N=0,next=0,idx=0,cnt=0; 
	scanf("%d %d %d",&F,&R,&M); 

	N = R - M + 1;
	next = R;

	for(int i=N; i<=R; i++){
		X[idx++] = arr[i]; 
		cnt++; 
	}
	idx = cnt-1;

	for(int i=N; i<=R; i++){
		arr[i] = X[idx++]; 
		if(idx == cnt){
			idx = 0;
		}
	}

	for(int i=0; i<20; i++){ 
		printf("%d ",arr[i]);
	}

    return 0;
}
```



### C_과제 4-3.c
정수 N을 입력받고, N개의 정수 읽어 들여 1, 2단계 [ 문제 4-1 ] [ 문제 4-2 ]를 수 행한후, 결과로나온배열에다시2단계[문제4-2]를계속적용하여전체N개의정수중가 장 큰 수, 가장 작은 수가 남을 때 까지 반복하는 프로그램을 작성하시오.

<img width="788" alt="스크린샷 2022-07-06 오후 4 18 26" src="https://user-images.githubusercontent.com/99342700/177605977-a841542b-3f49-4c36-8e0b-cc2e2de639ad.png">

1. 각 변수 지정.
2. 입력 받은 크기로 각 배열 변수 지정.
3. 입력 받은 배열을 역순으로 출력.
4. 각 최대/최소 변수에 배열의 첫 번째 인덱스 저장.
5. 반복할 때 i는 3칸씩 이동.
6. max변수에 가장 큰 값 저장.
7. min변수에 가장 작은 값 저장.
8. 배열에 최대/최소값 각각 저장 후 출력.

```c++
#include <stdio.h>

int main(void){
    int N=0,idx=0,cnt=0,M=0,max=0,min=0;
	scanf("%d",&N);
	int arr[N],temp[N],X[N],Y[N],max_cnt[N],min_cnt[N];

	for(int i=0; i<N; i++){
		scanf("%d",&arr[i]);
		temp[i] = arr[i];
	}

	for(int i=N-1; i>=0; i--){
		printf(" %d",arr[i]);
	}
	printf("\n");

	while(1){
		idx=0;
		for(int i=0; i<N; i=i+3){
			max = arr[i];
			min = temp[i];
			for(int j=i; j<i+3 && j<N; j++){
				if(max < arr[j]){
					max = arr[j];
				}
				if(min > temp[j]){
					min = temp[j];
				}
			}
			max_cnt[idx] = max;
			min_cnt[idx] = min;
			idx++;
		}


		for(int i=0; i<idx; i++){
			printf(" %d",max_cnt[i]);
		}
		printf("\n");
		for(int i=0; i<idx; i++){
			printf(" %d",min_cnt[i]);
		}
		printf("\n");
		N = idx;
		if(N == 1){
			break;
		}
		for(int i=0; i<N; i++){
			arr[i] = max_cnt[i];
			temp[i] = min_cnt[i];
		}
	}
	return 0;
}
```



### C_과제 5-2.c
두 집합 A, B 의 원소를 합쳐서 합집합을 만들려고 한다. 두 집합의 원소는 각각 음 수가 입력될 때까지의 원소이다. 문제 5-1처럼 중복된 원소가 입력될 수 있고 이 때는 집합에 추 가되지 않아야 한다. 합집합은 두 집합이 합쳐 진 후 정렬을 하여 오름차순으로 출력한다.
각 줄에서, 음수를 제외하고 최대 100개의 정수가 입력된다.

<img width="697" alt="스크린샷 2022-07-07 오후 7 03 15" src="https://user-images.githubusercontent.com/99342700/177748308-cf2affc1-157a-475d-95c6-e1e23240b4f5.png">

1. 필요한 배열 및 변수 지정.
2. 종료조건 전까지 입력받고 입력받은 값은 A,B배열에 저장.
3. 현재 위치부터 0인덱스까지 비교하며 같은 경우가 자기 자신 밖에 없을 때 새로운 배열에 저장.(반복된 수 제거)
4. 반복 제거한 두 배열을 하나의 배열로 합치기.
5. 합친 배열에 반복값이 있는지 확인하고 반복된 수는 제외하고 새로운 배열에 저장.
6. 가장 작은 수 부터 정렬하며 오름차순으로 저장.
7. 해당 배열 출력.

```c++
#include <stdio.h>

int main(void){
    int A[101],B[101],C[101],D[101],E[202],F[101],G[101];
	int idx=0,idx2=0,idx3=0,idx4=0,idx5=0,cnt=0,num1=0,num2=0,add=0,min=99999999,n=0,temp=0;

	while(1){
		scanf("%d",&temp);
		if(temp < 0){break;}
		A[num1++] = temp;
	} 
	
	while(1){
		scanf("%d",&temp);
		if(temp < 0){break;}
		B[num2++] = temp;
	}

	for(int i=0; i<num1; i++){
		for(int j=i; j>=0; j--){
			if(A[i] == A[j]){
				cnt++;
			}
		}
		if(cnt==1){
			C[idx++] = A[i]; 
		}
		cnt=0;
	}
	cnt=0;
	for(int i=0; i<num2; i++){
		for(int j=i; j>=0; j--){
			if(B[i]==B[j]){
				cnt++;
			}
		}
		if(cnt==1){
			D[idx2++] = B[i];
		}
		cnt=0;
	}
	cnt=0;

	add = idx + idx2;

	for(int i=0; i<idx; i++){
		E[idx3++] = C[i]; 
	}

	for(int i=0; i<idx2; i++){
		E[idx3++] = D[i];
	}

	for(int i=0; i<add; i++){
		for(int j=i; j>=0; j--){
			if(E[i] == E[j]){
				cnt++;
			}
		}
		if(cnt == 1){
			F[idx4++] = E[i];
		}
		cnt=0;
	}

	for(int i=0; i<idx4; i++){
		for(int j=0; j<idx4-1; j++){
			if(F[j] > F[j+1]){
				min = F[j];
				F[j] = F[j+1];
				F[j+1] = min;
			}
		}
	}

	for(int i=0; i<idx4; i++){
		printf("%d ",F[i]);
	}


	return 0;
}

```
</div>
</details>

<!--
<details>
<summary>  </summary>
<div markdown="1">

</div>
</details>
----------------------
-->