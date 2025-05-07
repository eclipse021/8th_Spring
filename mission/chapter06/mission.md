- 1번
    
    기존
    
    ```sql
    SELECT 
      m.point, 
      m.name, 
      m.description, 
      um.is_completed,
      um.updated_at
    FROM user_mission AS um
    INNER JOIN mission AS m ON um.mission_id = m.id
    WHERE um.user_id = 1
      AND um.updated_at < (
        SELECT updated_at
        FROM user_mission AS um2
        WHERE um2.id = 30 AND user_id = 1
      )
    ORDER BY um.updated_at DESC
    LIMIT 15;
    ```
    
    수정
    
    ```java
    List<Tuple> result = queryFactory
        .select(
            m.point,
            m.name,
            m.description,
            um.isCompleted,
            um.updatedAt
        )
        .from(um)
        .join(um.mission, m)
        .where(
            um.user.id.eq(1L),
            um.updatedAt.lt(
                JPAExpressions
                    .select(um2.updatedAt)
                    .from(um2)
                    .where(um2.id.eq(30L), um2.user.id.eq(1L))
            )
        )
        .orderBy(um.updatedAt.desc())
        .limit(15)
        .fetch();
    ```
    
- 2번
    
    기존
    
    ```sql
    INSERT INTO review (content, star, restaurant_id, user_id)
    VALUES ('음 너무 맛있어요 포인트도 얻고 맛있는 맛집도 알게 된 것 같아 너무나도 행복한 식사였답니다', 5, 3, 1);
    ```
    
    수정
    
    ```sql
    
    ```
    
- 3번
    
    **3-1.**
    
    기존
    
    ```sql
    SELECT COUNT(*) AS count_mission
    FROM user_mission AS um
    INNER JOIN mission AS m ON um.mission_id = m.id
    INNER JOIN restaurant AS r ON m.restaurant_id = r.id
    INNER JOIN location AS l ON r.address = l.address
    WHERE um.user_id = 1 AND l.address = '안암동'
    ```
    
    수정
    
    ```java
    Long count = queryFactory
        .select(um.count())
        .from(um)
        .join(um.mission, m)
        .join(m.restaurant, r)
        .join(r.location, l)
        .where(
            um.user.id.eq(1L),
            l.address.eq("안암동")
        )
        .fetchOne();
    		
    				
    ```
    
    **3-2.**
    
    기존
    
    ```sql
    SELECT 
        um.mission_complete,
        m.description AS mission_description,
        m.expired_at,
        r.name AS restaurant_name,
        r.cusine_type,
        l.address AS location_address
    FROM user_mission um
    JOIN mission m ON m.id = um.mission_id
    JOIN restaurant r ON r.id = m.restaurant_id
    JOIN location l ON r.address = l.address
    WHERE um.user_id = ?
      AND l.address = ?
      AND um.id > ?
    ORDER BY um.id ASC
    LIMIT ?
    ```
    
    수정
    
    ```java
    List<Tuple> results = queryFactory
        .select(
            um.missionComplete,
            m.description,
            m.expiredAt,
            r.name,
            r.cusineType,
            l.address
        )
        .from(um)
        .join(um.mission, m)
        .join(m.restaurant, r)
        .join(r.location, l)
        .where(
            um.user.id.eq(userId),
            l.address.eq(address),
            um.id.gt(cursorId)
        )
        .orderBy(um.id.asc())
        .limit(limit)
        .fetch();
    		
    ```
    
- 4번
    
    기존
    
    ```sql
    SELECT 
        u.nickname,
        u.email,
        u.is_phone_verified,
        u.point
    FROM user AS u;
    ```
    
    수정

  ```java
    Tuple result = queryFactory
    .select(u.nickname, u.email)
    .from(u)
    .where(u.id.eq(1L)) 
    .fetchOne();
    		
    ```
