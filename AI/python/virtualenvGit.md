# gitignore에 가상환경 추가하기


AI-server 작업 후에 git add . 를 하니 엄청나게 많은 파일이 올라갔다. (거의 5분 소요)  

그리고 commit하고, push를 하려하니

```powershell
failed to push some refs to ...
```

이라는 오류 발생!

구글에서는 main에 있는 폴더가 내 브랜치에 없을 때 발생하는 오류라는데, 그 문제는 아니었다.  

  
  
### 1) 해결 시도

전에 branch 병합 후에 기존 branch를 삭제를 안해서 발생하는 문제인가?

⇒ 삭제 후 다시 시도 했지만 아니었음   



### 2) 해결 시도

가상 환경 폴더를 gitignore에 추가하지 않아서 발생하는 문제인가?

⇒ 우선, git commit과 git add를 취소하고, 가상 환경 폴더를 gitignore에 추가했다.

결과는 성공! git add시 오래걸린 이유도 이 문제였던 것 같다.. 



### **<결론>**

가상 환경 설정 후에 gitignore에 가상환경 폴더를 추가해야 한다.

참고로 gitignore 폴더에 등록된 폴더는 노란색으로 표시된다.
