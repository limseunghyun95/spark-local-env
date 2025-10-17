## (2025-10-17) 
- 기존에는 docker compose scale 커맨드로 워커를 추가하려고 했으나 web UI에서 확인하기 위해서는 port를 외부에 노출하기 위한 binding을 해줘야하는데 그러면 port를 지정해줘야함. -> 이러면 scale을 통해 워커를 추가할 수 없음.(docker compose의 제약 사항) -> 따라서, 1차적으로 yaml 파일에 port 번호를 지정한 코드를 추가하는 것으로 임시적으로 사용

- hostname이 jupyter로 되어 있어 application detail로 이동시 jupyter:4040으로 넘어감 -> 이는 올바른 접근 방식이 아님. localhost:4040으로 접근해야 함. -> hostname 을 jupyter에서 localhost 로 변경하여 이슈 해결