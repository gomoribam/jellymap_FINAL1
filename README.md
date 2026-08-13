# JellyMap (젤리맵)

부산 바다 중심의 해파리 관측·위험도·안전정보 모바일 웹 프로토타입입니다.

## 실행

`index.html.html`을 브라우저에서 열거나 GitHub Pages에 업로드합니다.

현재 프로토타입은 별도 빌드 과정 없이 실행되는 단일 HTML 구조이며, 지도는 Leaflet과 OpenStreetMap 타일을 사용합니다.

## 주요 기능

- 부산 해운대·광안리, 송정, 다대포, 태종대·영도, 오륙도·이기대, 기장·일광 등 부산 해역 위험도 표시
- 안전(🟢)·주의(🟡)·위험(🔴) 마커
- 점선과 화살표를 이용한 예시 이동경로
- 마커 선택 후 지도 대신 지역 상세 화면 표시
- 응급처치 단계, 금지 행동, 119 긴급 안내
- 해파리·피부 사진 업로드 분석 시뮬레이션
- 해파리 종류·최근 관측·이용자 행동 권고 안내

## 데이터 안내

현재 지도와 상세 화면에 표시되는 관측값은 프로토타입 검증을 위한 `isSample` 성격의 예시 데이터입니다. 실제 관측 사실로 해석하면 안 됩니다.

공식 자료 연동 시 국립수산과학원 해파리속보 자료를 우선 사용합니다.

- [국립수산과학원 해파리속보](https://www.nifs.go.kr/board/actionBoard0022List.do)

실제 데이터가 연결되면 다음 항목을 데이터 모델로 교체할 수 있습니다.

```ts
interface JellyfishObservation {
  id: string;
  area: string;
  latitude: number;
  longitude: number;
  riskLevel: 'safe' | 'caution' | 'danger';
  species?: string[];
  observedAt?: string;
  observation?: string;
  density?: string;
  movementDirection?: string;
  source?: string;
  isSample?: boolean;
}
```

## 주의

응급처치 정보는 일반적인 안전 안내이며 의료 진단이나 치료를 대신하지 않습니다. 심한 통증, 호흡곤란, 의식저하 등 긴급 증상이 있으면 즉시 119 또는 의료기관의 도움을 받아야 합니다.
