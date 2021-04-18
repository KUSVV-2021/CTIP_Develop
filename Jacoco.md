# Jacoco coverage , Jenkins 연동

> 작성자: 김승환(jeffkimsh)

<br />

<br />

## Jacoco , Jenkins 연동 방법

### Jacoco Plugin 설치

#### 1. Jenkins 내에서 plugin을 설치합니다.
```
Dashboard -> Plugin Manager -> 설치 가능 메뉴 -> jacoco plugin 설치
```
#### 2. build.gradle에 plugin id 를 추가합니다.

![image](https://user-images.githubusercontent.com/76956654/115134943-acfc2b80-a04f-11eb-82c1-78b7e5322891.png)

#### 3. 빌드 후 조치를 추가합니다.
```
Dashboard -> project -> 구성 메뉴 -> 빌드 후 조치
```

![image](https://user-images.githubusercontent.com/76956654/115135062-6d820f00-a050-11eb-9cb5-ae4e6ac1c296.png)

![image](https://user-images.githubusercontent.com/76956654/115135104-ac17c980-a050-11eb-883d-96bc510800e9.png)

