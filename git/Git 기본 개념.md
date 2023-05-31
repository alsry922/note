이전 포스팅과 이어집니다.

이전 포스팅에서는 git repo에서 파일을 만들어 작업하고, commit을 해보았습니다.

또 파일을 수정하고 나서 commit도 해보았습니다.

이 과정에서 working tree, untracked files 등등의 용어가 나왔는데 이에 대해 알아보고자 합니다.

# ✔️ 깃이 관리하는 세 공간

![[images/잡학다식IT/Git 기본 개념/1.png]]

Git 은 작업 공간을 세 가지로 분류합니다.

## 📌Working Directory(Working Tree)

말 그대로 작업 공간입니다.

우리가 파일을 생성하고 작업하고 수정하고 하는 작업 디렉토리를 working directory 혹은 working tree 라고 부릅니다.

## 📌Staging area

`git add` 를 통해 다음 버전으로 만들고 싶은 변경 사항 들을 Staging area로 올릴 수 있습니다.

staging area에 올라간 파일은 `.git/index` 에서 파일로 관리합니다.

## 📌repository

버전이 만들어지고 관리되는 공간입니다.

working tree에서 stagin area로 올린 변경 사항을 가지고 `git commit` 을 통해 새로운 버전을 만들고 저장소에 저장합니다.

저장소에 새로운 버전을 만드는 것을 "커밋(commit)한다" 라고 표현하고 git으로 만든 버전을 편의상 커밋이라고 칭합니다.

# ✔️Git이 관리하는 파일

## 📌tracked, untracked 파일

한 번이라도 커밋된 적이 있는 파일은 tracked 파일로 깃이 변경사항을 추적하고 있는 파일입니다.

즉 기존에 깃이 관리하던 파일을 의미합니다.

하지만 untracked 파일은 한 번도 커밋된 적이 없어 기존에 깃이 관리하지 않던 파일을 의미합니다.

tracked 파일을 수정하면 modified 파일이 됩니다.

untracked 파일(즉 새로 만들 파일)을 add 하면 new file 상태가 되고 modifed 파일은 add해도 그대로 modified 파일입니다.

## 📌정리

untracked file(새로 만든 파일) -> add 하면 new file로 기록되며 staging area에 올라감

tracked file(기존에 깃이 관리하던 파일) -> 수정하면 modifed file로 기록됨 -> add 하면 modified file로 staging area에 올라감.