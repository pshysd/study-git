> 다루게 될 명령어

- [git merge](#git-merge)
  - [충돌](#충돌)
- [git rebase](#git-rebase)

<hr />

# git merge

이제 *second-branch*에서 작업하던 내용이 완성되었따면 *main*과 합쳐서 실제로 사용할 수 있게 해야한다. 이 때 사용하는 명령어가 `git merge [브랜치명]`이다.

> 여기서의 브랜치명은 합칠 branch이다. 현재 HEAD인 브랜치가 아니다.<br />
> ➡️ 현재 *main* 브랜치(HEAD)에서 second-branch를 병합한다면 `git merge second-branch`

`git merge second-branch`를 입력하고 나면 결과에 *Fast-forward*라고 표시되어 이쓴데 이것은 *main* 브랜치를 앞으로 쭉 당겼다는 뜻이다.

*second-branch*가 *main*보다 한 커밋 앞에 있었기 때문에 *main* 브랜치가 *second-branch*를 **merge**하는 순간 한 커밋 앞으로 당겨지는 것.

## 충돌

항상 모든 **merge**가 순조롭게 되는 것은 아니다.

`git reset HEAD~1`으로 *main* 브랜치를 뒤로 돌려보자. 

그리고 **git.html**을 다음과 같이 수정하고 커밋한다.

```html
<!DOCTYPE html>
<html>
<head>
  <title>깃 연습</title>
  <link rel="stylesheet" href="./git.css" />
</head>
<body>
  <h1>깃 충돌</h1>
  <p><b>깃 충돌</b>의 사용 방법에 대해 알아봅시다</p>
</body>
</html>
```
# git rebase