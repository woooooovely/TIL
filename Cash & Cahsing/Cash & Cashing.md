# Cash & Cashing

# 캐시?

<aside> 💡 자주 액세스하는 데이터의 성능을 향상시키는 데 사용되는 더 빠르고 비싼 소량의 메모리

</aside>

즉, 컴퓨터 성능을 향상시키기 위해 사용되는 메모리다.

디스크에서 불러오는 것이 속도가 느리기 때문에 메모리에서 빠르게 가져와 시간을 줄여주는 것이다.

**사용하면 좋을 때**

- 자주 조회되는 데이터일 때
- 잘 변하지 않는 데이터일 때
- 반복적으로 같은 결과를 반환해줄 때

# 캐싱 전략

캐싱 전략은 애플리케이션에서 데이터를 읽고 쓰는 방법에 따라 달라질 수 있다.

캐싱전략은 총 5가지가 있다.

## 읽기 전략

**Look aside (Lazy Loading)**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6345dbf-39d2-4e90-b7fd-358d249b80af/Untitled.png)

캐시를 먼저 확인한 후에, 캐시에 데이터가 있으면 해당 데이터를 읽어오는 방법

만약, 존재하지 않으면 데이터를 DB에서 가져온 후 캐시에 저장

### Read-Through

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ff009ddf-c50b-43bc-a349-02a2d9e2cf19/Untitled.png)

데이터를 읽을 때 캐시로만 데이터를 읽어오는 방식

만약 데이터가 캐시에 없을 때 DB에서 데이터를 캐시로 저장

### Lazy-Loading과 Read-Through의 차이점

look aside 같은 경우는 애플리케이션이 직접 DB에 데이터를 조회하지만, Read-Through는 캐시가 DB에 데이터를 직접 조회하고 로드하는 방식이다.

## 쓰기 전략

### write-around

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/18f73f56-6036-4304-924b-326ef6ee7138/Untitled.png)

DB에 저장하고 읽은 데이터만 캐시에 저장하는 방식

모든 데이터가 일단 DB에 저장됨

그 후, 캐시에 없어서 캐시미스가 일어날 때만 캐시로 데이터를 끌고오는 방법

- 자주 읽지 않을 데이터가 캐시에 로드되지 않아서 메모리를 아낄 수 있음
- 캐시와 DB사이의 데이터 일관성이 지켜지지 않을 수 있음
- DB에 저장한 후 읽지 않으면 데이터가 캐시되지 않음

### write-through

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/284ff73d-38d5-4220-bee8-77b1a0221f16/Untitled.png)

데이터를 먼저 캐시에 저장한 후 DB에 저장하는 방식

- DB와 캐시의 데이터 일관성을 보장해줄 수 있다.
- 저장할 때마다 캐시와 DB 모두 저장되기 때문에 상대적으로 속도가 느릴 수 있다.
- 데이터가 한번만 사용되는 경우에도 캐시에 넣게 되서 불필요할 수 있다.

### write-back

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0181d686-7e97-49d6-ab82-9482c3991c4f/Untitled.png)

모든 쓰기 작업이 캐시로 전달되고 일정시간에 DB에 데이터가 전달되는 방식

- 캐시에 장애가 발생해 데이터 유실이 생길 수 있는 문제가 있다