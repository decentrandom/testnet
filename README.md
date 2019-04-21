# 미시시피 테스트넷(Mississippi Testnet)

DecentRandom의 테스트넷, 미시시피에 필요한 Genesis 관련 파일입니다.
(이름에 큰 의미는 없습니다. Blues 음악을 좋아해서 즉흥적으로 정했을 뿐.)

## Warnings

- TerraFrom에서 '-' 기호를 제대로 인식하지 못하는 문제가 발생하여 '_' 기호로 대체하였습니다.

## mssp_0001/genesis.json 파일

미시시피 테스트넷의 초기 상태를 규정하는 파일입니다. Cosmos SDK를 사용하므로 구조가 크게 다르지 않습니다.

### 기본 정보

- genesis_time : UTC 타임으로 블록체인 시작 시간을 의미합니다. 이 시간에 맞춰 제네시스 검증인은 온라인 상태에서 블록 협의 절차에 참여해야 합니다. 2/3(보팅 파워 기준)에 해당하는 제네시스 검증인이 온라인 참여해야 합니다.
- chain_id : 현재 테스트넷 정보는 mssp_0001 입니다.

### 협의 파라메터

- block
  - max_bytes : 블록 크기의 최대값
  - max_gas : 블록 당 가스 제한
- evidence
  - max_age : 증거가 유요하지 않을 때(double signing 등으로) 이어지는 최대 블록 수
- validator
  - pub_key_types : Cosmos SDK의 정책에 따라 현재는 ed25519로 통일합니다.

### 어플리케이션 상태

- accounts
  - sequence_number : 리플레이 어택 방지용
  - account_number : 고유 ID
  - original_vesting : DecentRandom은 별도의 vesting 기간을 두지 않을 예정입니다.
  - delegated_free : 초기에는 null입니다.
  - delegated_vesting : 초기에는 null입니다.
  - start_time : 0
  - end_time : 0
- bank
  - send_enabled : vesting 기간이 없으므로 true
- staking
  - pool
    - not_bonded_tokens : 본딩 되지 않은 토큰 수량입니다. (mrand 단위)
    - bonded_tokens : 본딩된 토큰
  - params
    - unbonding_time : 토큰 본딩이 해제되는데 소요되는 시간 (나노 초 단위)
    - max_validators : 최대 활성화 검증인 수
    - max_entries : 7로 고정합니다.
    - bond_denom : mrand 단위를 사용합니다.
  - last_total_power : 보팅 파워의 총 량
  - last_validato_powers : null로 고정합니다.
  - validators : null로 고정합니다.
  - bonds : null로 고정합니다.
  - unbonding_delegations : null로 고정합니다.
  - redelegations : null로 고정합니다.
  - exported : false
- distr
  - fee_pool
    - community_pool : 바운티 등을 위해 사용됩니다. mssp_0001에서는 사용하지 않습니다.
  - **community_tax** : 커뮤니티 풀로 적립되는 tax 입니다. mssp_0001에서는 사용하지 않습니다.
  - base_proposer_reward : 1%
  - bonus_proposer_reward : 4%
  - withdraw_addr_enabled : 위임자가 다른 주소로 인출할 수 있도록 합니다.
  - delegator_withdraw_infos : 제네시스 단계에서는 null
  - previous_proposer : 제네시스 이므로 사용하지 않습니다.
  - outstanding_rewards : 제네시스 단계에서는 null
  - validator_accumulated_commission : null
  - validator_historical_rewards : null
  - validator_current_rewards : null
  - delegator_starting_infos : null
  - validator_slash_events : null
  - slashing
    - params
      - max_evidence_age : 나노 초 단위
      - signed_blocks_window : 100
      - min_signed_per_window : 50%
      - downtime_jail_duration : 나노 초 단위
      - slash_fraction_double_sign : 5%
      - slash_fraction_downtime : 1%
    - siginin_infos : 사용하지 않습니다.
    - missed_blocks : 사용하지 않습니다.
- gentxs

to-do

