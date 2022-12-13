
```python
import logging

logger = logging.getLogger(__name__)

# 로그 레벨 확인
print(logger.getEffectiveLevel())
print(logger.isEnabledFor(logging.WARNING)) # True
print(logger.isEnabledFor(logging.DEBUG)) # False

# 로그 레벨 변경
logger.setLevel(logging.DEBUG)
print(logger.getEffectiveLevel())
print(logger.isEnabledFor(logging.DEBUG)) # True

# Literal 사용
print(logging.getLevelName("DEBUG"))
logger.setLevel("INFO")

```