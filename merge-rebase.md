> 다루게 될 명령어

- [git merge](#git-merge)
  - [충돌](#충돌)
- [git rebase](#git-rebase)

<hr />

# git merge

이제 *second-branch*에서 작업하던 내용이 완성되었따면 *main*과 합쳐서 실제로 사용할 수 있게 해야한다. 이 때 사용하는 명령어가 `git merge [브랜치명]`이다.

> 여기서의 브랜치명은 합칠 branch이다. 현재 HEAD인 브랜치가 아니다.<br />
> ➡️ 현재 *main* 브랜치(HEAD)에서 second-branch를 병합한다면 `git merge second-branch`

`git merge second-branch`를 입력하고 나면 결과에 *Fast-forward*라고 표시되어 있는데 이것은 *main* 브랜치를 앞으로 쭉 당겼다는 뜻이다.

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

![Alt Text](https://cdn.filepicker.io/api/file/wxjeK1jjTXGKamMoMSop)

브랜치 두 개가 각자 다른 갈래로 갈라졌다. 이제 `git merge second-branch`를 하면 충돌이 일어난다.

**git.html**이 다음과 같이 변경된다.

```html
<!DOCTYPE html>
<html>
<head>
  <title>깃 연습</title>
  <link rel="stylesheet" href="./git.css" />
</head>
<body>
<<<<<<< HEAD
  <h1>깃 conflict</h1>
  <p><b>깃 conflict</b>의 해결 방법에 대해 알아봅시다</p>
=======
  <h1>깃 브랜치</h1>
  <p><b>깃 브랜치</b>의 사용 방법에 대해 알아봅시다</p>
>>>>>>> feature
</body>
</html>
```

이 부분을 정상적으로 바꿔준 뒤 **add**, **commit** 해주면 충돌이 해결된다.

# git rebase

위의 구조에서 `git reset HEAD~1`을 해준다. 합쳐졌던 두 개의 브랜치가 다시 갈라졌다.

![Alt Text](https://cdn.filepicker.io/api/file/jJtqqm7HTAaH3poLXk9K)

두 사람이 협업하다가 커밋이 서로 달라진 경우이다. 이제 *main*에서 *second-branch*를 **rebase**한다. 

`git rebase [브랜치명]`

![Alt Text](https://cdn.filepicker.io/api/file/KqzTJprSmaJpoQwFEDCL)

역시나 충돌이 일어나는데 **merge**와는 해결 방법이 살짝 다르다.

일단 **git.html**의 충돌을 해결하고, `git add git.html`로 *staged* 상태로 만들어준다. **merge**는 그 후 커밋을 했지만, **rebase**는 `git rebase --continue`로 중단된 **rebase**를 이어가면 된다.

> 깔끔한 로그를 원하면 **rebase**를 하고, 직관적으로 간단하게 하고 싶으면 **merge**를 사용하면 된다.