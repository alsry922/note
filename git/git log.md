
# ✔️git log

`git log` 는 여태까지의 커밋 기록들을 보여줍니다.

![[images/잡학다식IT/git log/1.png]]

git log 를 통해 여태까지의 커밋, 커밋 메세지, 커밋 해시, 누가 작성했는지 등을 볼 수 있습니다.

하지만 커밋 본문에 많은 내용을 적어야 하는 경우, 혹은 이미 너무 많은 커밋이 존재하는 경우 한 번에 보기 힘든 경우가 많습니다.

`git log --oneline` 으로 oneline 옵션을 가지고 실행해보겠습니다.

![[images/잡학다식IT/git log/2.png]]

커밋 해시의 길이도 짧아지고 딱 커밋 메세지 그리고 HEAD까지만 나옵니다.

`--oneline` 옵션은 `--pretty=oneline --abrev-commit` 옵션의 short hand입니다.

추가로 `--graph` 옵션은 현재까지의 커밋 기록을 그래프 형태로 보여줍니다.