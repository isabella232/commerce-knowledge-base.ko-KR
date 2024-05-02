---
title: 기본 바니시 설정을 변경해야 하는 경우 발생하는 503 오류 문제 해결
description: 이 문서에서는 특정 바니시 캐시 기본값이 저장소에 충분하지 않아 발생한 503 오류를 해결하는 방법에 대해 설명합니다.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 9c5e993b69a98865a1142110625252da848eae04
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 기본 바니시 설정을 변경해야 하는 경우 발생하는 503 오류 문제 해결

이 문서에서는 특정 바니시 캐시 기본값이 저장소에 충분하지 않아 발생한 503 오류를 해결하는 방법에 대해 설명합니다.

## 문제

Adobe Commerce에서 사용하는 캐시 태그의 길이가 Varnish의 기본값인 8192바이트를 초과하는 경우 브라우저에서 HTTP 503(백엔드 가져오기 실패) 오류를 볼 수 있습니다. 오류는 다음과 유사하게 표시될 수 있습니다. *&quot;오류 503 백엔드 가져오기에 실패했습니다. 백엔드 가져오기 실패&quot;*

## 솔루션

이 문제를 해결하려면 의 기본값을 늘립니다 `http_resp_hdr_len` Varnish 구성 파일의 매개 변수. 다음 `http_resp_hdr_len` 매개 변수는 최대 헤더 길이를 지정합니다. *다음 범위 내* 총 기본 응답 크기(32768바이트)입니다.

>[!NOTE]
>
>다음과 같은 경우 `http_resp_hdr_len` 값이 32K를 초과하므로 다음을 사용하여 기본 응답 크기를 늘려야 합니다. `http_resp_size` 매개 변수.

1. 을 사용하는 사용자로서 `root` 권한은 텍스트 편집기에서 Vanish 구성 파일을 엽니다.
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * 데비안: `/etc/default/varnish`
   * 우분투: `/etc/default/varnish`
1. 검색 `http_resp_hdr_len` 매개 변수.
1. 매개 변수가 없으면 뒤에 추가하십시오. `thread_pool_max` .
1. 설정 `http_resp_hdr_len` 최대 카테고리의 제품 수에 21을 곱한 값과 같습니다. (각 제품 태그의 길이는 약 21자입니다.)    예를 들어 가장 큰 카테고리에 3,000개의 제품이 있는 경우 값을 65536바이트로 설정하면 작동합니다.    예:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. 설정 `http_resp_size` (증가된 응답 헤더 길이를 수용하는 값).    예를 들어, 증가된 헤더 길이와 기본 응답 크기의 합을 사용하는 것이 좋은 시작점입니다(예: 65536 + 32768 = 98304). `-p http_resp_size=98304`. 코드 조각은 다음과 같습니다.

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## 상태 검사 시간 초과 {#health-check-timeouts}

Varnish가 캐싱 애플리케이션으로 구성되고 Adobe Commerce이 개발자 모드에 있는 동안 캐시를 비활성화하면 관리자에 로그인할 수 없게 될 수 있습니다.

이 상황은 기본 상태 검사에 `timeout` 값 2 초. 상태 검사에서 모든 상태 검사 요청에 대한 정보를 수집하고 병합하는 데 2초 이상 걸릴 수 있습니다. 상태 검사 10개 중 6개에서 이 문제가 발생하면 Adobe Commerce 서버가 비정상으로 간주됩니다. 서버가 비정상 상태일 때 바니시는 오래된 콘텐츠를 제공합니다.

관리자는 Varnish를 통해 액세스되므로 캐싱을 활성화하기 위해 Admin에 로그인할 수 없습니다(Adobe Commerce이 다시 정상이 되지 않는 한). 그러나 다음 명령을 사용하여 캐시를 활성화할 수 있습니다.

```bash
$ bin/magento cache:enable
```

명령줄 사용에 대한 자세한 내용은 [명령줄 구성 시작](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands.html).
