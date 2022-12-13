
* Node 확인
```shell
$ kubectl get node -o wide
```


* Pod 생성 및 실행
```shell
-- 하나만
$ kubectl run nginx-pod --image=ngnix

-- 여러 개
$ kubectl create deployment dpy-nginx1 --image=nginx
$ kubectl run my-first-nginx --image=nginx --replicas=2
```

* Pod 확인
```shell
$ kubectl get pods
$ kubectl get pods -o wide
$ kubectl get deployment
$ kubectl get pod,deploy
```

* Yaml 파일 실행
```shell
$ kubectl create -f dpy-nginx2.yaml
$ kubectl apply -f dpy-nginx.yaml
$ kubectl edit deploy dpy-nginx2
```

* Pod 삭제
```shell
$ kubectl delete pod --all
$ kubectl delete deployment --all
$ kubectl delete svc --all
$ kubectl delete deployment,pod,svc --all
```

* 모니터링
```shell
$ watch kubectl get pods -o wide
```