
## Create a cluster

There are two types of clusters:
- All-Purpose clusters can be shared by multiple users. There are typically used to run notebooks. All-Purpose clusters remain active until you terminate them.
- Job clusters run a job. You create a job cluster when you create a job. Such clusters are terminated automatically after the job is completed.
    - ex) An automated workflow needs to be run every 30 minutes.

## Cluster 상태

### Cluster의 status가 pending
- cluster 생성 
- package 생성
- 에러 발생
    - Spark job의 input parameter 오류

### 라이브러리 설치 시 

library를 uninstall하면
- cluster를 한 번 껐다 켜야 함
- 노트북에서 magic command로 uninstall
    - `%pip uninstall ...`
