## JPA repository 사용시 Optional<T> 이슈

* 기본적으로 자바에 맞춰져 있으므로 Optinal로 묶여있음

* Kotlin의 장점을 잘 살리려면 Nullable을 바로 체크할 수 있어야 함.

  * Extension 사용

    1. 함수를 재정의하기

    2. 이미 잘 구현되어있는 built-in extension 사용

       e.g) `findById()` -> `findByIdOrNull()`

       성능 이슈가 있다고 하지만, 무시할 수 있을정도의 미미한 성능차



* @JoinColumn 어노테이션의 옵션 name은 해당 엔티티 테이블에 어떤 컬럼명으로 저장할지를 지정
  * 실제로 FK가 맵핑되는 컬럼은 해당 타입(엔티티)의 PK이니까 자동으로 알아서 맵핑해줌.
