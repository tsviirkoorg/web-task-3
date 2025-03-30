# Mission 3

## Part 1,2

[Link to video](https://drive.google.com/file/d/1ipToImjRHgNbLsWd1SsomWODolPhPg2K/view?usp=sharing)

## Part 3
- Вопрос 1	 
> **SELECT** username **FROM** users

- Запрос 2	 
>  **SELECT** 
    u.username **AS** username,
    COUNT(m.id) **AS** "number of sent messages"
**FROM** 
    users u
**LEFT JOIN** 
    messages m **ON** u.id = m.from
**GROUP BY** 
    u.id, u.username

- Вопрос 3	 
>  **SELECT** 
    u.username **AS** username,
    **COUNT**(m.id) **AS** "number of received messages"
**FROM** 
    users u
**JOIN** 
    messages m ON u.id = m.to
**GROUP BY** 
    u.id, u.username
**ORDER BY** 
    **COUNT**(m.id) **DESC**
**LIMIT** 1;

- Вопрос 4	 
> **SELECT** 
    **AVG**(message_count) **AS** "average messages per user"
**FROM** (
    **SELECT** 
        u.id,
        **COUNT**(m.id) **AS** message_count
    **FROM** 
        users u
    **LEFT JOIN** 
        messages m **ON** u.id = m.from
    **GROUP BY** 
        u.id
) **AS** user_message_counts;
