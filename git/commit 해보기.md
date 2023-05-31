이전 포스팅과 이어집니다.

자, 이제 git repo도 만들어 봤으니 git이 어떻게 우리의 작업 내용을 관리해주는지 알아봅시다.

# ✔️git status, git add, git commit

현재 우리의 git repo에 아무것도 없습니다. 오늘 날짜로 일기를 한 번 써보려고 합니다.

```bash
touch diary0531.txt
```

>
>오늘은 git을 공부했습니다.
상당히 재밌더군요.
내 작업 내용들을 관리해준다니 멋집니다.

이 내용을 남기고 해당 파일을 저장했습니다.

그리고 `git status`로 git repo의 상태를 확인해봅시다.

![[images/잡학다식IT/commit 해보기/1.png]]

untracked files로 diaray0531.txt 파일이 있다고 나옵니다.

`git add` 를 실행해주고 다시 `git status` 로 살펴봅시다.

![[images/잡학다식IT/commit 해보기/2.png]]

diary0531.txt 가 new file로 기록되면서 commit될 변경사항이 있다고 나옵니다.

이제 commit을 남겨봅시다.

```bash
git commit -m "wirt diary 0531"
```

![[images/잡학다식IT/commit 해보기/3.png]]

commit 이후 status를 확인해보니 commit할 게 없고 working tree가 clean하다고 나옵니다.

이렇게 우리는 하나의 commit을 남겼습니다.

지금 보니 커밋메세지에 오타가 있었네요 이를 수정하는 방법은 다음 포스팅에서 알아보겠습니다.

자, 이 상태에서 새로운 파일을 한 번 써봅시다. 갈비찜 레시피가 궁금해서 파일이 생성해 갈비찜 레시피를 적어주었습니다.

```bash
touch galbijjim-recipe.txt
```

>
갈비찜은 이렇게 저렇게 삶고 
양념장을 이렇게 저렇게 만들어서
졸여주면 완성됩니다.
짜잔

그리고 아까 쓴 일기에 내용을 좀 추가해주고 싶어졌습니다. 그래서 마지막 줄에 밑에 내용처럼 추가해줬습니다.

>commit 수정도 가능할까요?

작성한 후 git status를 살펴봅시다.

![[images/잡학다식IT/commit 해보기/4.png]]

diary0531은 modified, galbijjim-recipe는 Untracked files로 나옵니다.

각각의 파일을 add해서 commit할 수 있지만 귀찮으니까 일단 한 번에 add해서 commit 해봅시다.

![[images/잡학다식IT/commit 해보기/5.png]]

add, commit 후 status 까지 한 결과입니다.

commit하는 방법은 알겠는데 working tree, untracked file, modifed... 잘 이해되지 않는 말들이 있습니다.

다음 포스팅에서는 다음 내용에 대해 살펴보도록 하겠습니다.