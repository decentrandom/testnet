# Mississippi

DecentRandom의 테스트넷, 미시시피에 필요한 Genesis 관련 파일입니다.
이름에 큰 의미는 없습니다. Blues 음악을 좋아해서 즉흥적으로 정했을 뿐.

### Warnings

- TerraFrom에서 '-' 기호를 제대로 인식하지 못하는 문제가 발생하여 '_' 기호로 대체하였습니다.

### <TESTNET_ID>/genesis.json 파일

미시시피 테스트넷의 초기 상태를 규정하는 파일입니다. Cosmos SDK의 그것과 같습니다.

##### 기본 정보

- genesis_time : UTC 타임으로 블록체인 시작 시간을 의미합니다. 이 시간에 맞춰 제네시스 검증인은 온라인 상태에서 블록 협의 절차에 참여해야 합니다. 2/3(보팅 파워 기준)에 해당하는 제네시스 검증인이 온라인 참여해야 합니다.
- chain_id : 현재 테스트넷 정보는 mssp_0001 입니다.

##### 협의 파라메터

- block
  - max_bytes : 블록 크기의 최대값
  - max_gas : 블록 당 가스 제한
- evidence
  - max_age : 증거가 유요하지 않을 때(double signing 등으로) 이어지는 최대 블록 수
- validator
  - pub_key_types : Cosmos SDK의 정책에 따라 현재는 ed25519로 통일합니다.

##### 어플리케이션 상태

- accounts
  - sequence_number : 리플레이 어택 방지용
  - account_number : 고유 ID
  - original_vesting : DecentRandom은 별도의 vesting 기간을 두지 않을 예정입니다.
  - delegated_free : 초기에는 null입니다.
  - delegated_vesting : 초기에는 null입니다.
  - start_time : 0
  - end_time : 0
- Bank
  - send_enabled : vesting 기간이 없으므로 true

