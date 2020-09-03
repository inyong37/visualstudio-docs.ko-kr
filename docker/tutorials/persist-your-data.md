---
title: 'Docker 자습서-4 부: 데이터 유지'
description: 볼륨을 탑재 하 여 데이터베이스에 데이터를 저장 하 고 컨테이너에 디렉터리를 공유 하는 방법을 알아봅니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 34b3cb9465c1efb946260917d755729e25c4e259
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176792"
---
# <a name="persist-your-data"></a> 데이터 유지

확인 하지 못한 경우에는 컨테이너를 시작할 때마다 할 일 목록이 정리 됩니다. 그 이유는 무엇입니까? 컨테이너가 어떻게 작동 하는지 살펴보겠습니다.

## <a name="the-containers-filesystem"></a>컨테이너의 파일 시스템

컨테이너는 실행 될 때 해당 파일 시스템에 대 한 이미지의 다양 한 계층을 사용 합니다. 또한 각 컨테이너는 파일을 만들거나 업데이트 하거나 제거 하기 위한 자체 "스크래치 공간"을 가져옵니다. 동일한 이미지를 사용 하는 *경우에도* 다른 컨테이너에는 변경 내용이 표시 되지 않습니다.

### <a name="see-this-in-practice"></a>실제로이 항목을 참조 하세요.

이 작업을 수행 하려면 두 개의 컨테이너를 시작 하 고 각각에 파일을 만듭니다. 한 컨테이너에서 만든 파일은 다른 컨테이너에서 사용할 수 없다는 것을 알 수 있습니다.

1. `ubuntu` `/data.txt` 1에서 1만 사이의 임의 숫자로 이름이 지정 된 파일을 만들 컨테이너를 시작 합니다.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    명령에 대 한 자세한 내용은 bash 셸을 시작 하 고 두 개의 명령을 호출 하는 것입니다 (의 경우 `&&` ). 첫 번째 부분은 단일 난수를 선택 하 여에 씁니다 `/data.txt` . 두 번째 명령은 단순히 파일을 감시 하 여 컨테이너를 계속 실행 합니다.

1. 유효성 검사를 사용 하 여 컨테이너에 가져오는 출력을 볼 수 있습니다 `exec` . 이렇게 하려면 VS Code 확장을 열고 **셸 연결** 옵션을 클릭 합니다. 이는 `exec` 를 사용 하 여 VS Code 터미널 내의 컨테이너에서 셸을 엽니다.

    ![Ubuntu 컨테이너에 CLI를 열 VS Code](media/attach_shell.png)

    Ubuntu 컨테이너에서 셸을 실행 하는 터미널이 표시 됩니다. 다음 명령을 실행 하 여 파일의 내용을 확인 `/data.txt` 합니다. 나중에이 터미널을 닫습니다.

    ```bash
    cat /data.txt
    ```

    명령줄을 선호 하는 경우 `docker exec` 명령을 사용 하 여 동일한 작업을 수행할 수 있습니다. 컨테이너의 ID를 가져와서 (를 사용 하 여 `docker ps` ) 다음 명령을 사용 하 여 콘텐츠를 가져와야 합니다.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    난수를 확인할 수 있습니다.

1. 이제 다른 `ubuntu` 컨테이너 (동일한 이미지)를 시작 하면 동일한 파일이 없다는 것을 볼 수 있습니다.

    ```bash
    docker run -it ubuntu ls /
    ```

    확인 하세요. `data.txt`파일이 없습니다. 첫 번째 컨테이너에 대해서만 스크래치 공간에 기록 되었기 때문입니다.

1. 계속 해 서 명령을 사용 하 여 첫 번째 컨테이너를 제거 `docker rm -f` 합니다.

## <a name="container-volumes"></a>컨테이너 볼륨

이전 실험을 사용 하 여 각 컨테이너가 시작 될 때마다 이미지 정의에서 시작 되는 것을 확인 했습니다. 컨테이너는 파일을 생성, 업데이트 및 삭제할 수 있지만 컨테이너를 제거 하 고 모든 변경 내용이 해당 컨테이너에 격리 되 면 해당 변경 내용이 손실 됩니다. 볼륨을 사용 하면이 모든 것을 변경할 수 있습니다.

[볼륨](https://docs.docker.com/storage/volumes/) 은 컨테이너의 특정 파일 시스템 경로를 호스트 컴퓨터에 다시 연결 하는 기능을 제공 합니다. 컨테이너의 디렉터리가 탑재 된 경우 해당 디렉터리의 변경 내용이 호스트 컴퓨터에도 표시 됩니다. 컨테이너를 다시 시작 하는 동안 동일한 디렉터리를 탑재 하면 동일한 파일이 표시 됩니다.

볼륨에는 두 가지 주요 유형이 있습니다. 궁극적으로는 두 가지를 모두 사용 하지만 **명명 된 볼륨**으로 시작 합니다.

## <a name="persist-your-todo-data"></a>Todo 데이터 유지

기본적으로 todo 앱은의 [SQLite 데이터베이스](https://www.sqlite.org/index.html) 에 해당 데이터를 저장 `/etc/todos/todo.db` 합니다. SQLite를 잘 모르는 경우 신경 쓰지! 단지 모든 데이터가 단일 파일에 저장 되는 관계형 데이터베이스입니다. 이는 대규모 응용 프로그램에는 적합 하지 않지만 작은 데모에서는 작동 합니다. 나중에이를 실제 데이터베이스 엔진으로 전환 하는 방법에 대해 설명 합니다.

데이터베이스가 단일 파일이 면 해당 파일을 호스트에 보관 하 고 다음 컨테이너에서 사용할 수 있도록 하는 경우 마지막으로 남은 위치를 선택할 수 있어야 합니다. 볼륨을 만들고 (종종 "탑재 중" 이라고 함) 데이터가 저장 된 디렉터리에 연결 하 여 데이터를 유지할 수 있습니다. 컨테이너는 파일에 쓸 때 `todo.db` 볼륨의 호스트에 저장 됩니다.

앞에서 설명한 것 처럼 **명명 된 볼륨**을 사용 합니다. 명명 된 볼륨은 단순히 데이터 버킷 이라고 생각 하면 됩니다. Docker는 디스크의 물리적 위치를 유지 관리 하며 볼륨의 이름을 명심 해야 합니다. 이 볼륨을 사용할 때마다 Docker는 올바른 데이터가 제공 되는지 확인 합니다.

1. 명령을 사용 하 여 볼륨을 만듭니다 `docker volume create` .

    ```bash
    docker volume create todo-db
    ```

1. `docker rm -f <id>`영구적 볼륨을 사용 하지 않고 계속 실행 되 고 있으므로 대시보드 (또는)에서 todo 앱 컨테이너를 다시 한 번 중지 합니다.

1. Todo 앱 컨테이너를 시작 하지만 `-v` 볼륨 탑재를 지정 하는 플래그를 추가 합니다. 명명 된 볼륨을 사용 하 여에 탑재 합니다 `/etc/todos` . 그러면 경로에 생성 된 모든 파일이 캡처됩니다.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. 컨테이너가 시작 되 면 앱을 열고 할 일 목록에 몇 개의 항목을 추가 합니다.

    ![할 일 목록에 추가 된 항목](media/items-added.png)

1. Todo 앱에 대 한 컨테이너를 제거 합니다. 대시보드 또는를 사용 `docker ps` 하 여 ID를 가져온 다음 `docker rm -f <id>` 제거 합니다.

1. 위의 동일한 명령을 사용 하 여 새 컨테이너를 시작 합니다.

1. 앱을 엽니다. 항목이 목록에 계속 표시 됩니다.

1. 목록 체크 아웃을 완료 하면 계속 해 서 컨테이너를 제거 합니다.

만 세! 이제 데이터를 유지 하는 방법을 배웠습니다.

> [!TIP]
> 명명 된 볼륨 및 바인드 탑재는 기본 Docker 엔진 설치에서 지원 되는 두 가지 주요 유형의 볼륨 이지만, NFS, SFTP, NetApp 등을 지 원하는 데 사용할 수 있는 많은 볼륨 드라이버 플러그 인이 있습니다. Swarm, Kubernetes 등을 사용 하 여 클러스터 된 환경의 여러 호스트에서 컨테이너를 실행 하기 시작 하는 경우 특히 중요 합니다.

## <a name="dive-into-your-volume"></a>볼륨에 대 한 자세한 내용을 알아봅니다.

많은 사람들이 "명명 된 볼륨을 사용 하는 경우 일반적으로 데이터 *를 저장 하* 는 위치는 어디 인가요?" 라고 질문 합니다. 알고 싶으면 명령을 사용할 수 있습니다 `docker volume inspect` .

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

는 `Mountpoint` 데이터가 저장 되는 디스크의 실제 위치입니다. 대부분의 컴퓨터에서는 호스트에서이 디렉터리에 액세스할 수 있는 루트 액세스 권한이 있어야 합니다. 하지만 이것이 여기에 해당 합니다.

> [!NOTE]
> **Docker Desktop에서 직접 볼륨 데이터 액세스** Docker Desktop에서 실행 하는 동안 컴퓨터의 작은 VM 내에서 Docker 명령이 실제로 실행 되 고 있습니다. *탑재* 지점 디렉터리의 실제 콘텐츠를 확인 하려는 경우 먼저 VM 내부에서 가져와야 합니다. WSL 2에서이는 WSL 2 배포판 내에 있으며 파일 탐색기를 통해 액세스할 수 있습니다.

## <a name="recap"></a>요약

이 시점에서 계속 해 서 다시 시작할 수 있는 작동 중인 응용 프로그램이 있습니다. 투자자에 표시 하 여 비전을 파악할 수 있습니다.

그러나 앞에서 설명한 대로 모든 변경에 대 한 이미지를 다시 작성 하는 데 시간이 많이 걸립니다. 신속 하 게 변경 하는 방법이 있나요? 이전에 언급 한 바인드 탑재를 사용 하면 더 나은 방법이 있습니다. 이제 살펴보겠습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [바인드 탑재 사용](use-bind-mounts.md)