#### 动态插入数据库

```sql
<insert id="addUserInfo" parameterType="com.lhyy.sjsgyadminapi.admin.model.UserModel" useGeneratedKeys="true" keyProperty="user_id">
    insert into admin.[user] (
    <trim suffixOverrides=",">
        user_name,
        user_mob,
        user_number,
        user_pw,
        create_date,
        update_date,
        <if test="user_des!=null and user_des!=''">user_des,</if>
        <if test="create_id!=null">create_id,</if>
        <if test="create_id!=null">update_id,</if>
        is_valid,
    </trim>
    ) values (
    <trim suffixOverrides=",">
        #{user_name},
        #{user_mob},
        #{user_number},
        #{user_pw},
        now(),
        now(),
        <if test="user_des!=null and user_des!=''">#{user_des},</if>
        <if test="create_id!=null">#{create_id},</if>
        <if test="create_id!=null">#{create_id},</if>
        1,
    </trim>
    )
</insert>
```

