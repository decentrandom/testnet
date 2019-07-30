# 검증 노드 실행

    randd unsafe-reset-all
    rm -rf ~/.randd/config
    rannd init --chain-id randtest_0001 <moniker>
    randd add-genesis-account $(./randcli keys show <account> -a) 1000000000000000urand
    randcli config chain-id randtest_0001
    randcli config output json
    randcli config indent true
    randcli config trust-node true
    randd gentx --name <account>
    randd collect-gentxs
    randd validate-genesis
    randd start

