# Mission 3

## Part 0-2

[Link to video](https://disk.yandex.ru/d/-HoYzIdLXi5f8A)
[2nd part](https://disk.yandex.ru/i/xNlw1_OjiprdpQ) , i had  problems in previous video

## Part3

-- список юзернеймов пользователей
>`select distinct username` <br>
>`from public.users pu`

-- кол-во отправленных сообщений каждым пользователем
>`select pu.username, count(*) as send_messages`<br>
>`from public.messages pm`<br>
>`left join  public.users pu on pm.from = pu.id`<br>
>`group by pu.username`

-- пользователь с самым большим кол-вом полученных сообщений и само количество
>`select pu.username, count(*) as count_messages`<br> 
>`from public.messages pm`<br>
>`left join  public.users pu on pm.to = pu.id`<br>
>`group by pu.username`<br>
>`order by count(*) desc`<br>
>`limit 1`

-- среднее кол-во сообщений, отправленное каждым пользователем
>`select round(count(*)/count(distinct pm.from), 2) as avg_messages`<br>
>`from public.messages pm`
