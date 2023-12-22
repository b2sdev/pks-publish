---
id: dbzdjnctsucmkxrt9h5zpce
title: How to fix pip path?
desc: ''
updated: 1703227582177
created: 1703226872473
---

## 문제
`pip`로 패키지를 설치 후 실행 시 패키지를 찾지 못함

## 관찰
`pip install`로 패키지 설치 시 아래와 같은 로그 확인
```
Installing collected packages: pakage-abc
  WARNING: The script package-abt is installed in '/home/ubuntu/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
Successfully installed package-abc-1.2.3
```

## 해결
```bash
echo "export PATH=\"/home/ubuntu/.local/bin:\$PATH\"" >> ~/.bashrc && source ~/.bashrc
```

## References
- https://askubuntu.com/questions/1242234/in-ubuntu-20-04-how-to-fix-pip-pat