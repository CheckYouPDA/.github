# ✅ Check You

금융사기피해 에방을 위한 신원 및 데이터 인증 서비스 Check You를 소개합니다.

### 서비스 배포 주소는 [링크](https://shinhansec.checkyou.net/)를 확인해주세요.

<br>

## 👋 About
- 주제: 
- 일정: 
- 인원: 5명

<br>

## 🌟 Main function

- 금융투자협회, 금융소비자 정보 포털 등의 데이터를 바탕으로 투자자문사/유사투자자문사/미신고개인인지에 대해 사용자가 바로 알 수 있습니다.
- 금융기관으로부터 실제 데이터를 수신하여 진위여부를 판별하고 데이터의 출처를 확보 및 위/변조를 방지합니다.

<br>

## 📝 IA

<img width="80%" alt="image" src="https://github.com/check-you/.github/assets/67499154/7ba8a565-d02a-4bd0-a944-22a33f3ada2e">

<br>

- 일반 사용자
  - 이름, 금융기관, 계좌정보, 소속, 사업자번호를 통해 알아보려는 사람이 실제로 투자자문사, 유사투자자문사 혹은 개인인지에 대한 여부를 조회할 수 있습니다.

- 계좌를 인증하려는 사용자
  - 본인의 정보를 등록하고, 등록된 정보에 대해 공개될 수 있음을 동의하여 신원을 등록할 수 있습니다.
  - 사업자번호를 입력함으로써 금융투자협회의 데이터를 활용해 이 사람이 전문가인지에 대한 신원 정보를 가져옵니다.
  - 실계좌에 대해 역이체 인증방식을 활용해서 금융기관으로부터 계좌 정보와 내역을 모두 가져올 수 있습니다.

<br>

## 📤 Data Flow

<img width="80%" alt="image" src="https://github.com/check-you/.github/assets/67499154/e2e7e39a-cd2a-4b58-a218-76f9a4cf0256">

<br>

[**공개키와 비밀키, 대칭키, 전자서명**을 사용한 암호화 파이프라인]

- 클라이언트가 서버에 요청을 보내고, 서버는 사용자의 요청에 맞게 각 증권사에 요청을 보냅니다.
- 클라이언트와 서버가 통신하는 과정에서는 SSL 인증서를 통한 HTTPS 통신을 하여 데이터의 위변조를 방지하고 제3자가 열람을 할 수 없습니다.

Check You → 증권사

1. 요청을 받은 증권사는 데이터의 해시 값을 계산해 다이제스트를 구하고 이를 증권사의 비밀키로 암호화해 전자 서명합니다.
2. 데이터를 대칭키로 암호화하고 사용된 대칭키를 체크유의 공개 키로 암호화합니다.
3. 그 결과 전자 서명과 암호화된 데이터, 암호화된 대칭 키를 체크유 서버로 보냅니다.

Check You ← 증권사

1. 체크유 서버는 전자 서명, 암호화된 데이터, 암호화된 대칭 키를 받습니다.
2. 암호화된 대칭키를 체크유의 비밀키로 복호화해 대칭키를 추출하고, 이 대칭키로 암호화된 데이터를 복호화해 다이제스트를 산출합니다. 
3. 전자 서명을 증권사의 공개키로 복호화하는 과정에서 데이터의 출처가 증권사임을 증명함과 동시에 다이제스트를 산출합니다.
4. 둘을 비교해 값이 같다면 데이터의 흐름에서 위변조가 발생하지 않았다고 판단하고 이를 클라이언트에게 내려 줍니다.

<br>

## 🏛️ Infra Architecture

<img width="80%" alt="image" src="https://github.com/check-you/.github/assets/67499154/c5aa4bd0-1096-446b-9fe4-c5cc86f3f036">

<!-- - **AWS Tools**: EKS(Ingress, Service, Deployment, Pod), EC2, S3, Route53, ACM, Cloud Watch -->

<br>

## 🛠️ Application Develop Skills and Tools

- **Presentation Tier**: JavaScript, React, Recoil
- **Application Tier**: Java, Spring Boot, Gradle, Lombok, JWT, Spring Security
- **Data Tier**: MariaDB

<br>

## 👥 Member

|이름|역할|Github|
|:--:|:--:|:--:|
|서준원|인프라|[wnsdnjs70](https://github.com/wnsdnjs70)|
|유오준|백엔드|[yoj9168](https://github.com/orgs/check-you/people/yoj9168)|
|정채윤|프론트엔드|[kkkwp](https://github.com/kkkwp)|
|조하영|프론트엔드|[chososo](https://github.com/chososo)|
|조현진|프론트엔드|[Hyunjin02](https://github.com/Hyunjin02)|
