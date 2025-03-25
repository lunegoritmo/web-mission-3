# Mission 3

## Part 0-2

[Link to video](https://disk.yandex.ru/i/Xlu2JbJy0JiVmA)

## Part3

-- список юзернеймов пользователей
'''select distinct username
'''from public.users pu

--кол-во отправленных сообщений каждым пользователем
select pu.username, count(*) as send_messages
from public.messages pm
left join  public.users pu on pm.from = pu.id
group by pu.username

--пользователь с самым большим кол-вом полученных сообщений и само количество
select pu.username, count(*) as count_messages 
from public.messages pm
left join  public.users pu on pm.to = pu.id
group by pu.username 
order by count(*) desc
limit 1

--среднее кол-во сообщений, отправленное каждым пользователем
select round(count(*)/count(distinct pm.from), 2) as avg_messages
from public.messages pm
